---
library_name: transformers
tags: []
---

# Model Card for Model ID

# AVA-Llama-3
Fine-Tuned Llama 3 Persian Large Language Model LLM / Persian Llama 3


# AVA-Llama-3 / Persian Llama-3 / Persian Llama 3


 <img src="Llama 3.png" height="600" width="940" >

### This Repository Contains Documents for Fine-Tuned Llama 3  Persian Large Language Model(LLM) Called AVA-Llama-3
(Still in progress)

-------------------------------------------------
### Dataset used:

To Be Done

-------------------------------------------------



### Usage:

All models are hosted in HuggingFace, and here is the code for inference:

```py
from transformers import AutoModelForCausalLM, AutoTokenizer, GenerationConfig
import torch

model_name_or_id = "MehdiHosseiniMoghadam/AVA-Llama-3-V2"
model = AutoModelForCausalLM.from_pretrained(model_name_or_id, torch_dtype=torch.float16, device_map="auto", low_cpu_mem_usage=True, load_in_8bit=True)
tokenizer = AutoTokenizer.from_pretrained(model_name_or_id)

prompt = ''

prompt = f"### Human:{prompt}\n### Assistant:"


inputs = tokenizer(prompt, return_tensors="pt").to("cuda")

generation_config = GenerationConfig(
    do_sample=True,
    top_k=1,
    temperature=0.99,
    max_new_tokens=90,
    pad_token_id=tokenizer.eos_token_id
)


outputs = model.generate(**inputs, generation_config=generation_config)
print(tokenizer.decode(outputs[0], skip_special_tokens=True))


```

You can also use colab link in the jupyter file

-------------------------------------------------

## QA Comparision to other models:

 <img src="AVA2.jpg" height="600" width="940" >


[AVA-Llama-3](https://huggingface.co/MehdiHosseiniMoghadam/AVA-Llama-3-V2) vs [AVA-V4](https://huggingface.co/MehdiHosseiniMoghadam/AVA-Mistral-7B-V4) vs [AVA-V2](https://huggingface.co/MehdiHosseiniMoghadam/AVA-Mistral-7B-V2) vs [Maral](https://huggingface.co/MaralGPT/Maral-7B-alpha-1) vs  [Llama](https://huggingface.co/hdeldar/llama-2-7b-persian-text-1k)


### Q1: 
```
طبق متن زیر ایلان ماسک در کجا به دنیا امده است؟

ایلان ریوْ ماسک (به انگلیسی: Elon Reeve Musk؛ ‎/ˈiːlɒn/‎ EE-lon؛ زادهٔ ۲۸ ژوئن ۱۹۷۱)، سرمایه‌گذار و شخصی نامی در کسب‌وکار است. او بنیان‌گذار، مدیرعامل و مهندس ارشدِ فنی اسپیس‌اکس؛ سرمایه‌گذار فرشته، مدیرعامل، طراح محصولات و مدیرعامل سابق شرکت تسلا؛ بنیان‌گذار شرکت بورینگ؛ یکی از بنیان‌گذاران نیورالینک و اوپن‌ای‌آی و رئیس بنیاد ماسک است. او ثروتمندترین شخص در جهان است؛ دارایی خالص تخمینی او بر اساس شاخص میلیاردرهای بلومبرگ تا نوامبر ۲۰۲۳، ۲۱۹ میلیارد دلار آمریکا و بر اساس فوربز، ۲۴۱ میلیارد دلار است. این دارایی اساساً از سهم مالکیت او در تسلا و اسپیس‌ایکس به‌دست آمده‌است.[۵][۶][۷]

ماسک از ارول ماسک و می ماسک در پرتوریا، آفریقای جنوبی به دنیا آمد. او مدت کوتاهی در دانشگاه پرتوریا به تحصیل پرداخت و در ۱۸ سالگی به کانادا رفت که از طریق مادر کانادایی‌تبارش تابعیت این کشور را به دست آورد.[۸] دو سال بعد به دانشگاه پنسیلوانیا رفت و در آن جا کارشناسی اقتصاد و فیزیک خود را گرفت. او در سال ۱۹۹۵ برای تحصیل در دانشگاه استنفورد به کالیفرنیا نقل مکان کرد اما بعد از دو روز ترک تحصیل کرد و به‌همراه برادرش کیمبال، شرکت نرم‌افزاری راهنمای سفر آنلاین زیپ۲ را تأسیس کرد. این شرکت نوپا در سال ۱۹۹۹ به‌مبلغ ۳۰۷ میلیون دلار توسط کامپک خریداری شد و با ۱۲ میلیون دلاری که به دست آورد، ماسک همان سال مشترکاً بانکداری مستقیم X.com را تأسیس کرد که در سال ۲۰۰۰ با کنفینیتی ادغام شد و باعث تشکیل پی‌پل شد.

```



<table width="300">
  <tr>
    <td> Model </td>
    <td> Answer </td>
    <td> Rating  </td>
      </tr>
   <tr>
    <td> AVA-Llama-3 </td>
    <td> ایلان ریو ماسک در پرتوریا، آفریقای جنوبی به دنیا امده است </td>
    <td> </td>
  </tr>
  </tr>
   <tr>
    <td> AVA-V4 </td>
    <td> ایلان ریو ماسک در پرتوریا، آفریقای جنوبی به دنیا امده است. او در 18 سالگی به کانادا رفت </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V2 </td>
    <td> ایلان ماسک در پرتوریا، آفریقای جنوبی به دنیا آمده است. او در 18 سالگی به کانادا رفت </td>
    <td>  </td>
  </tr>
    <tr>
    <td> Maral </td>
    <td> ایلان ماسک در پرتوریا، آفریقای جنوبی به دنیا آمده است </td>
    <td>   </td>
  </tr>
    <tr>
    <td> Llama </td>
    <td> اگر او در کجا به دنیا امده باشد، چه کسی او را در کجا می‌دانست؟ </td>
    <td>  </td>
  </tr>
</table>




--------------------------------------------------------


### Q2: 
```
سه قاتل در یک اتاق هستند.. یکی وارد اتاق می شود و یکی از آنها را می کشد. هیچ کس اتاق را ترک نمی کند چند قاتل در اتاق باقی مانده است؟ استدلال خود را توضیح دهید

```



<table width="300">
  <tr>
    <td> Model </td>
    <td> Answer </td>
    <td> Rating  </td>
      </tr>
   <tr>
    <td> AVA-Llama-3 </td>
    <td>  این یک بازی با کلمات است که به ما کمک می کند تا به یک پاسخ عجیب برسیم. پاسخ این است که سه قاتل باقی می مانند. دلیل این است که یکی از قاتلان وارد اتاق می شود و یکی از قاتلان دیگر را می کشد، اما هیچ کس اتاق را ترک نمی کند. بنابراین، سه قاتل باقی می مانند.
 </td>
    <td> </td>
  </tr>
  </tr>
   <tr>
    <td> AVA-V4 </td>
    <td> پاسخ: در اتاق هنوز یک قاتل باقی مانده است.
 استدلال: از هر دو قاتل یکی در اتاق باقی مانده است. زیرا هر کدام یکی را می کشد و هیچ کدام از اتاق ترک نمی کند. پس از کشتن دیگری، یکی از قاتلان باقی مانده در اتاق هست </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V2 </td>
    <td> در این سوال، اولیه استدلال به این صورت است که در یک اتاق سه قاتل هستند. واقعیت این است که یکی از آنها را می کشد و یکی از آنها را نمی کشد. بنابراین، هیچ کس اتاق را ترک نمی کند و دو قاتل در اتاق باقی مانده است.

اگر در این سوال به استدلال بیشتری افتد، می توانیم ببینیم که هر دو قاتل هم در اتاق هستند و هیچ کدام را نمی کشند. اما در این استدلال اصلی و اولیه، تعداد قاتل های باقی مانده در اتاق به دو تقریباً این است. </td>
    <td>  </td>
  </tr>
    <tr>
    <td> Maral </td>
    <td>در این سوال سه قاتل در یک اتاق وجود دارد و یکی از آنها را می کشد. هیچ کس اتاق را ترک نمی کند، بنابراین دو قاتل باقی مانده است. </td>
    <td>   </td>
  </tr>
    <tr>
    <td> Llama </td>
    <td> این استدلال می تواند به یک اتاق با چهار قاتل در آن باشد. یک قاتل وارد اتاق می شود و یکی از آنها را می کشد. هیچ کس اتاق را ترک نمی کند چند قاتل در آن باقی مانده است. این استدلال می تواند به یک اتاق با چهار قاتل در آن باشد که یک قاتل وارد اتاق می شود و یکی از آنها را می کشد و هیچ کس اتاق را ترک نمی کند چند قاتل در آن باقی مانده است. می تواند به یک اتاق با چهار قاتل در آن باشد که یک قاتل وارد اتاق می شود و یکی از آنها را می کشد و هیچ کس اتاق را ترک نمی کند چند قاتل در آن باقی مانده است. می تواند به یک اتاق با چهار قاتل در آن باشد که یک قاتل وارد اتاق می شود و یکی از آنها را می کشد و هیچ کس اتاق را
 </td>
    <td>  </td>
  </tr>
</table>




----------------------------------------------------------


### Q3: 
```
ملکه الیزابت کیست؟

```



<table width="300">
  <tr>
    <td> Model </td>
    <td> Answer </td>
    <td> Rating  </td>
  </tr>
    <tr>
    <td> AVA-Llama-3 </td>
    <td> 
 ملکه الیزابت یک شاهزاده بریتانیایی است که از ۱۹۵۲ تا ۲۰۲۲ بر تخت سلطنت بریتانیا سلطنت کرد. او در ۲۱ آوریل 1926 در لندن متولد شد و در ۸ سپتامبر 2022 در سن ۹۶ سالگی در باکینگهام پالاس درگذشت. ملکه الیزابت دوم طولانی‌ترین سلطنت بریتانیا را در اختیار داشت و در طول سلطنت خود بریتانیا را از جنگ جهانی دوم تا جنگ سرد و سپس به دوران مدرن رهبری کرد. او همچنین در طول سلطنت خود به عنوان یک نماد ملی و یک نماد برای بریتانیا شناخته شد. ملکه الیزابت دوم همچنین به عنوان ملکه کانادا، استرالیا، نیوزیلند و سایر کشورهای مشترک‌المنافع بریتانیا نیز شناخته می‌شود.  </td>
    <td> <h1> 🥳 </h1> </td>
  </tr>
   <tr>
    <td> AVA-V4 </td>
    <td> ملکه ایلزابت بولنتن بود که در سال 1533 تا 1558 در انگلستان دور بود. او در زمان بود که انگلستان در دوران تاریخی به عنوان یک کشور به پیشرفت بیشتری رسید </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V2 </td>
    <td> ملکه الیزابت یک شهرستان در انگلستان است. </td>
    <td>  </td>
  </tr>
    <tr>
    <td> Maral </td>
    <td> ملکه الیزابت یک کشور در جنوب آفریقا است که در سال 1910 به این نام تعیین شد. این کشور به دلیل اینکه در سال 1910 به این نام تعیین شد، به دلیل اینکه در سال 1910 به این نام تعیین شد، به دلیل اینکه در سال 1910 به این نام تعیین شد، به دلیل اینکه در سال 1910 به این نام تعیین شد، به دلیل اینکه در سال 1910 به این نام تعیین شد، به دلیل اینکه در سال 1910 به این نام تعیین شد، به دلیل اینکه در سال 1910 به این نام تعیین شد، به دلیل اینکه در سال 1910 به این نام تعیین شد، به دلیل اینکه در سال 1910 به این نام تعیین شد، به دلیل اینکه در سال 1910 به این نام تعیین شد، به دلیل اینکه در سال 1910 به این نام تعیین شد، به دلیل اینک </td>
    <td>   </td>
  </tr>
    <tr>
    <td> Llama </td>
    <td> ملکه الیزابت ریاضی ایرانی است که در سال ۱۹۴۷ در ایران تولید شد. این ملکه در سال ۱۹۶۷ در ایران تولید شده و در سال ۱۹۷۰ در ایران و در سال ۱۹۷۱ در امریکا تولید شده و در سال ۱۹۷۲ در ایران و در سال ۱۹۷۳ در امریکا تولید شده و در سال ۱۹۷۴ در ایران و در سال ۱۹۷۵ در امریکا تولید شده و در سال ۱۹۷۶ در ایران و در سال ۱۹۷۷ در امریکا تولید شده و در سال ۱۹۷۸ در ایران و در سال ۱۹۷۹ در امریکا تولید شده و در سال ۱۹۸۰ در ایران و در سال ۱۹۸۱ در امریکا تولید شده و در سال ۱۹۸۲ در ایران و در سال ۱۹۸۳ در امریکا تولید شده و در سال ۱۹۸۴ در ایران و در سال ۱۹۸۵ در امریک
 </td>
    <td>  </td>
  </tr>
</table>



-----------------------------------------------------------------





### Q4: 
```
اگر یک توپ داخل یک لیوان برعکس باشد و ما لیوان را برداشته و داخل مایکروویو بگذاریم الان توپ کجاست؟

```



<table width="300">
  <tr>
    <td> Model </td>
    <td> Answer </td>
    <td> Rating  </td>
  </tr>
  <tr>
    <td> AVA-Llama-3 </td>
    <td> منظور شما این است که توپ در داخل لیوان برعکس قرار دارد و سپس لیوان را برداشته و داخل مایکروویو قرار می دهید. در این صورت، توپ در داخل مایکروویو قرار دارد و برعکس لیوان نیست.
    </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V4 </td>
    <td> 
### Assistant: اگر یک توپ داخل یک لیوان برعکس باشد، و ما لیوان را برداشته و داخل مایکروویو بگذاریم، توپ داخل مایکروویو خواهد بود. در این واقعیت، توپ در داخل مایکروویو قرار داشته و لیوان را برداشته شده است </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V2 </td>
    <td> اگر یک توپ داخل یک لیوان باشد، و ما لیوان را برداشته و داخل مایکروویو بگذاریم، توپ داخل مایکروویو خواهد بود. این تشکیل اندازه گیری شده است و در فیزیک و ارتباطات است، و این تشکیل اندازه گیری شده به عنوان "توپ داخل لیوان در داخل مایکروویو" شناسایی می شود. این تشکیل اندازه گیری شده در فیزیک و ارتباطات به عنوان یک نمونه از انواع تشکیلات اندازه گیری شده ارائه می شود که توسط جهان در حال ارتباط است.
 </td>
    <td>  </td>
  </tr>
    <tr>
    <td> Maral </td>
    <td> اگر یک توپ داخل یک لیوان برعکس باشد و ما لیوان را برداشته و داخل مایکروویو بگذاریم، توپ داخل مایکروویو خواهد بود. </td>
    <td>   </td>
  </tr>
    <tr>
    <td> Llama </td>
    <td> توپ داخل یک لیوان یا مایکروویو است که در آن می توان برای انجام کارهای مختلف استفاده کنید. لیوان یک ماشین است که در آن می توان برای انجام کارهای مختلف استفاده کنید. مایکروویو یک ماشین است که در آن می توان برای انجام کارهای مختلف استفاده کنید. مایکروویو یک توپ داخل است که در آن می توان برای انجام کارهای مختلف استفاده کنید. مایکروویو یک توپ داخل است که در آن می توان برای انجام کارهای مختلف استفاده کنید. مایکروویو یک توپ داخل است که در آن می توان برای انجام کارهای مختلف استفاده کنید. مایکروویو یک توپ داخل است که در آن می توان برای انجام کارهای مختلف استفاده کنید. مایکروویو یک توپ داخل است که در آ </td>
    <td>  </td>
  </tr>
</table>


-----------------------------------------------------------------





### Q5: 
```
یک شعر با دقیقا پنجاه کلمه بساز؟

```






<table width="300">
  <tr>
    <td> Model </td>
    <td> Answer </td>
    <td> Rating  </td>
  </tr>
    <td> AVA-Llama-3 </td>
    <td> 

در تاریکی شب، صدای قلبم می‌زند
دلشکسته و بی‌امید، در تاریکی شب
من می‌خواهم به تو برسم، به تو که هستی
اما در تاریکی شب، نمی‌توانم به تو برسم
من می‌خواهم به تو برسم، به تو که هستی
اما در تاریکی شب، نمی‌توانم به تو برسم
من می‌خواهم به تو برسم، به تو که هستی
اما در تاریکی شب، نمی‌توانم به تو برسم
من می‌خواهم به تو برسم، به تو که هستی
اما در تاریکی شب، نمی‌توانم به تو برسم
من می‌خواهم به تو برسم، به تو که هستی
اما در تاریکی شب، نمی‌توانم به تو برسم
من می‌خواهم به تو برسم، به تو که هستی
اما در تاریکی شب، نمی‌توانم به تو برسم
من می‌خواهم به تو برسم، به تو که هستی
 </td>
    <td> 
   <tr>
    <td> AVA-V4 </td>
    <td> بله، می توانم یک شعر با دقیقا پنجاه کلمه برای شما بسازم. اینجا یک شعر با پنجاه کلمه ای که برای شما نوشتم:

در جنگل دیدار کردم یک گربه سیاه
که در دست دو گربه سبز قرار داشت
از آن که در جنگل زمانه های گذشته
گربه ها در دست دیگران قرار گرفت </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V2 </td>
    <td> بله، می‌توانید یک شعر با دقیقا پنجاه کلمه بساز. اینجا یک نمونه شعر با پنجاه کلمه ایده آمده است:

در دل آب و هوای زمان،
در دل آفتاب و شب،
در دل گل و گوشت،
در دل عشق و دوری،

در دل آفتاب و شب،
در دل گل و گوشت،
در دل عشق و دوری،
در دل آب و هوای زمان،

در دل آفتاب و شب،
در دل گل و گوشت،
در دل عشق و دوری،
در دل آب و هوای زمان،

در دل آفتاب و شب،
در دل گل و گوشت،
در دل عشق و دوری،
در دل آب و هوای زمان،

در دل آفتاب و شب،
در دل گل و گوشت،
در دل عشق و دوری،
در دل آب و هوای زمان. </td>
    <td>  </td>
  </tr>
    <tr>
    <td> Maral </td>
    <td> در اینجا یک شعر با دقیقا پنجاه کلمه وجود دارد:
"با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه،
با دقیقا پنجاه کلمه، </td>
    <td>   </td>
  </tr>
    <tr>
    <td> Llama </td>
    <td> بله، شعر یک نوع از مواد مختلف است که در معروف شعر با نام شعر انسان به اندازهٔ ۱۰۰۰ کلمه در مقابل ۱۰۰۰ کلمه در مقابس شعر حیوانات و ۱۰۰۰ کلمه در مقابس شعر گیاهان و ۱۰۰۰ کلمه در مقابس شعر گیاهان با نام شعر گیاهان انسان و ۱۰۰۰ کلمه در مقابس شعر گیاهان دیگر و ۱۰۰۰ کلمه در مقابس شعر دیگر انسان و ۱۰۰۰ کلمه در مقابس شعر دیگر انسان و ۱۰۰۰ کلمه در مقابس شعر دیگر حیوانات و ۱۰۰۰ کلمه در مقابس شعر دیگر گیاهان و ۱۰۰۰ کلمه در مقابس شعر دیگر گیاهان انسان و ۱۰۰۰ کلمه در مقابس شعر دیگر حیوانات و ۱۰۰۰ کلمه در مقابس شعر دیگر گیاهان و ۱۰۰۰ کلمه در مقابس شعر دیگ </td>
    <td>  </td>
  </tr>
</table>

-----------------------------------------------------------------





### Q6: 
```
یک نامه خطاب به رییس شرکت من بنویس که من در حال استعفا و ترک شرکت هستم؟

```









<table width="300">
  <tr>
    <td> Model </td>
    <td> Answer </td>
    <td> Rating  </td>
  </tr>	   <tr>
    <td> AVA-Llama-3 </td>
    <td>
	    
یک نامه خطاب به رییس شرکت من بنویسید که من در حال استعفا و ترک شرکت هستم.

[Your Name]
[Your Address]
[City, State, ZIP]
[Date]

[CEO's Name]
[Company Name]
[Company Address]
[City, State, ZIP]

Dear [CEO's Name],

I am writing to inform you that I have decided to resign from my position as [Position] at [Company Name], effective [Date of Last Day of Work]. This was not an easy decision for me to make, as I have truly enjoyed my time at the company and have been grateful for the opportunities that I have been given.

However, I have come to realize that it is time for me to move on and explore new opportunities. I am grateful for the experience and skills that I have gained during my time at [Company Name], and I am confident that they will serve me well in my future endeavors.

I want to thank you for the support and guidance that you have provided me during my time at the company. I appreciate the opportunities that you have given me to grow and develop as a professional, and I am grateful for the trust that you have placed in me.

I will do everything I can to ensure a smooth transition of my responsibilities and complete any outstanding tasks before my departure. If there is anything specific that you would like me to focus on during my remaining time here, please let me know.

Thank you again for the opportunity to work at [Company Name]. I wish the company all the best for the future.

Sincerely,

[Your Name]
 </td>
   <tr>
    <td> AVA-V4 </td>
    <td> ۱۳۹۹/۰۸/۱۴۰۰

مترجم: شما باید نامه خطاب خود را به انگلیسی نوشته و از طریق این پیام به من ارسال کنید.

متوضع: در این نامه خطاب، من در حال استعفا و ترک شرکت هستم.

نامه خطاب:

از انجام ناخودپسندیده و از دست دادن از شرکت خود انجام می دهم.

شما باید نامه خطاب خود را به انگلیسی نوشته و از طریق این پیام به من ارسال کنید.

متوضع: در این نامه خطاب، من در حال استعفا و ترک شرکت هستم.
 </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V2 </td>
    <td> اگر شما یک نامه خطاب به رییس شرکت خود بنویسید که من در حال استعفا و ترک شرکت هستم، این است که می توانید از آن استفاده کنید:

 نامه خطاب

شماره: [شماره نامه]

تاریخ: [تاریخ نوشتن نامه]

[نام و نام خانوادگی رییس شرکت]
[عنوان شرکت]
[آدرس شرکت]

شکر خوب،

به عنوان یکی از عضویان شرکت [نام شرکت]، احتمالاً اولین خبری که به شما این نامه ارسال می کنم نیست. اما در حال حاضر، من در حال استعفا و ترک از شرکت هستم و این نامه را به شما ارسال می کنم تا آن را به دنباله های دیگری اضافه کنم.
 </td>
    <td>  </td>
  </tr>
    <tr>
    <td> Maral </td>
    <td> رییس شرکت،
من در حال استعفا و ترک شرکت هستم. این نه به دلیل اینکه به شرکت نیاز ندارم، بلکه به دلیل اینکه با این کار به خود و به شرکت اشتباه کرده ام. این به دلیل این است که از طرف شرکت به دنبال ارزش های بیشتری بودم و از طرف من به دنبال ارزش های بیشتری بودم. اما این ارزش ها به طور متوقف شده است و از طرف شرکت و من ارزش های بیشتری به دست نمی آید. این به دلیل این است که ارزش های بیشتری به طور متوقف شده است و از طرف شرکت و من ارزش های بیشتری به دست نمی آید. اما این ارزش ها به طور متوقف شده است و از طرف شرکت و من ارزش های بیشتری به دست نمی آید. اما این ارزش ها به طور متوقف شده است و از طرف شرکت و من ارزش های بی </td>
    <td>   </td>
  </tr>
    <tr>
    <td> Llama </td>
    <td> ### Assistant: خوب است که شرکت را ترک کردید. من به شرکت باز کردم و امروز در شرکت باز شدم. من در حال استعفا و می خوام به شرکت باز شدم. من در حال استعفا و می خوام به شرکت باز شدم. من در حال استعفا و می خوام به شرکت باز شدم. من در حال استعفا و می خوام به شرکت باز شدم. من در حال استعفا و می خوام به شرکت باز شدم. من در حال استعفا و می خوام به شرکت باز شدم. من در حال استعفا و می خوام به شرکت باز شدم. من در حال استعفا و می خوام به شرکت باز شدم. من در حال استعفا و می خوام به شرکت باز شدم. من در حال استعفا و می خوام به شرکت باز شدم. من در حال استعفا و می خوام به شرکت باز شدم. من در حال استعفا و می خوام به شرکت باز شدم. من در حال
 </td>
    <td>  </td>
  </tr>
</table>

-----------------------------------------------------------------





### Q7: 
```
رییس جمهور آمریکا در سال 1996 که بود؟

```


<table width="300">
  <tr>
    <td> Model </td>
    <td> Answer </td>
    <td> Rating  </td>
  </tr>
   <tr>
    <td> AVA-Llama-3 </td>
    <td> رییس جمهور آمریکا در سال 1996، بیل کلینتون بود </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V4 </td>
    <td> رییس جمهور آمریکا در سال 1996 بود بیل کلینتن. </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V2 </td>
    <td> در سال 1996، رییس جمهور آمریکا بیل کلنتن بود. </td>
    <td>  </td>
  </tr>
    <tr>
    <td> Maral </td>
    <td> رییس جمهور آمریکا در سال 1996 بیل کلنتن بود. </td>
    <td>   </td>
  </tr>
    <tr>
    <td> Llama </td>
    <td> رییس جمهور آمریکا در سال ۱۹۹۶ به نام بلار بورنس بود. او در ۱۹۹۲ از رییس دادگاه آمریکا و در ۱۹۹۴ از رییس دادگاه آمریکا شد و در ۱۹۹۶ به رییس جمهور آمریکا اتحادیه شد. او در ۱۹۹۷ به رییس جمهور آمریکا دوم شد و در ۱۹۹۹ به رییس جمهور آمریکا سوم شد. او در ۱۹۹۱ به رییس دادگاه آمریکا شد و در ۱۹۹۲ به رییس دادگاه آمریکا شد و در ۱۹۹۳ به رییس جمهور آمریکا شد. او در ۱۹۹۴ به رییس دادگاه آمریکا شد و در ۱۹۹۵ به رییس جمهور آمریکا شد. او در ۱۹۹۶ به رییس جمهور آمریکا شد و در ۱۹۹۷ به رییس جمهور آمریکا دوم شد. او در ۱۹۹۸ به رییس جمهور آمریکا سوم شد. او در ۱۹۹ </td>
    <td>  </td>
  </tr>
</table>

-----------------------------------------------------------------





### Q8: 
```
اگر پنج پیراهن 4 ساعت طول بکشد تا خشک شود، 20 پیراهن چقدر طول می کشد تا خشک شود؟

```





<table width="300">
  <tr>
    <td> Model </td>
    <td> Answer </td>
    <td> Rating  </td>
  </tr>
<tr>
    <td> AVA-Llama-3 </td>
    <td>  
اگر پنج پیراهن 4 ساعت طول می کشد تا خشک شود، می توانیم به این نتیجه برسیم که هر پیراهن 4/5 ساعت طول می کشد تا خشک شود. برای پیدا کردن زمان لازم برای خشک شدن 20 پیراهن، می توانیم از این رابطه استفاده کنیم:

4/5 * 20 = 16

بنابراین، 20 پیراهن 16 ساعت طول می کشد تا خشک شود.
 </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V4 </td>
    <td>  اگر پنج پیراهن 4 ساعت طول بکشد تا خشک شود، 20 پیراهن به اندازه ی یک ساعت طول می کشد تا خشک شود. این اطمینان را دارید که هر پیراهن در نتیجه 20 پیراهن 4 ساعت طول می کشد تا خشک شود.
 </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V2 </td>
    <td> اگر پنج پیراهن 4 ساعت طول بکشد تا خشک شود، 20 پیراهن به اندازه ی شبیه ساعت بکشند تا خشک شود. برای حل مورد نیاز، شما می توانید از فرمول زیر استفاده کنید:

طول بکشنده شدن 20 پیراهن = طول بکشنده شدن 5 پیراهن × (شماره پیراهن / شماره پیراهن)

طول بکشنده شدن 20 پیراهن = 4 ساعت × (20 / 5)

طول بکشنده شدن 20 پیراهن = 4 ساعت × 4

طول بکشنده شدن 20 پیراهن = 16 ساعت
 </td>
    <td>  </td>
  </tr>
    <tr>
    <td> Maral </td>
    <td> برای حل این پرسش، ابتدا باید از این اطلاعات استفاده کنید که پنج پیراهن 4 ساعت طول می کشد تا خشک شود. از این اطلاعات باید برای حل پرسش استفاده کنید.برای حل این پرسش، ابتدا باید از این اطلاعات استفاده کنید که پنج پیراهن 4 ساعت طول می کشد تا خشک شود. از این اطلاعات باید برای حل پرسش استفاده کنید.برای حل این پرسش، ابتدا باید از این اطلاعات استفاده کنید که پنج پیراهن 4 ساعت طول می کشد تا خشک شود. از این اطلاعات باید برای حل پرسش استفاده کنید.برای حل این پرسش، ابتدا باید از این اطلاعات استفاده کنید که پنج پیراهن 4 ساعت طول می کشد تا خشک شود. از این اطلاعات باید برای حل پرسش استفاده کنید.برای حل این پرسش
 </td>
    <td>   </td>
  </tr>
    <tr>
    <td> Llama </td>
    <td> پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پنج پیراهن چه طول دارند؟ پن
 </td>
    <td>  </td>
  </tr>
</table>

-----------------------------------------------------------------





### Q9: 
```
یک خرگوش و یک لاک پشت یک مسابقه 100 متری را شروع می کنند، سرعت خرگوش 10 کیلومتر و لاک پشت 1 کیلومتر است، چه کسی برنده مسابقه است؟

```






<table width="300">
  <tr>
    <td> Model </td>
    <td> Answer </td>
    <td> Rating  </td>
  </tr>
 <tr>
    <td> AVA-Llama-3 </td>
    <td> 
این مسابقه بسیار جالب است! با در نظر گرفتن سرعت هر دو، می توانیم سرعت آنها را به یک واحد تبدیل کنیم. سرعت خرگوش 10 کیلومتر بر ساعت است، بنابراین سرعت لاک پشت را به 10 کیلومتر بر ساعت تبدیل می کنیم. در این صورت، سرعت لاک پشت 0.1 کیلومتر بر ساعت است.

در این صورت، سرعت خرگوش 10 کیلومتر بر ساعت و سرعت لاک پشت 0.1 کیلومتر بر ساعت است. بنابراین، خرگوش برنده مسابقه است. لاک پشت به دلیل سرعت بسیار پایین خود نمی تواند با خرگوش رقابت کند.
 </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V4 </td>
    <td> 
برای حل این مسئله، ما باید سرعت هر دو از جمله را بررسی کنیم و سپس آن‌ها را با هم مقایسه کنیم. سرعت خرگوش 10 کیلومتر در 1 دقیقه است و سرعت لاک پشت 1 کیلومتر در 10 دقیقه است.

مسابقه 100 متری از آنجایی که خرگوش سریع‌تر از لاک پشت است، خرگوش به طور کامل قابلیت برداشتن این جاهزه را دارد. بنابراین، خرگوش برنده مسابقه است.
 </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V2 </td>
    <td> برای مشاهده نتیجه مسابقه، باید سرعت خرگوش و لاک پشت را به هم انداز کنیم. سرعت خرگوش 10 کیلومتر در ساعت و لاک پشت 1 کیلومتر در ساعت است. برای اینکه نتیجه مسابقه را بدست آوریم، باید 100 متر را به سرعت خرگوش و لاک پشت تبدیل کنیم.

100 متر / 10 کیلومتر در ساعت = 10 دقیقه

100 متر / 1 کیلومتر در ساعت = 100 دقیقه

بنابراین، خرگوش 10 دقیقه و لاک پشت 100 دقیقه می گذرد تا 100 متر را پیروز کنند. بنابراین، برنده مسابقه خرگوش است. </td>
    <td>  </td>
  </tr>
    <tr>
    <td> Maral </td>
    <td> برنده مسابقه خرگوش است. با سرعت 10 کیلومتر در ساعت، خرگوش به انتهای 100 متر در 10 دقیقه به پایان می رسد، در حالی که لاک پشت با سرعت 1 کیلومتر در ساعت به پایان می رسد و به انتهای 100 متر در 100 دقیقه به پایان می رسد.
 </td>
    <td>   </td>
  </tr>
    <tr>
    <td> Llama </td>
    <td> با این نوع سوال می توان به نوع سوال با نوع جواب انتظار داشته باشید. با این حال، اگر با این سوال می توان به نوع جواب انتظار داشته باشید، می توان به نوع جواب انتظار داشته باشید. با این حال، اگر با این سوال می توان به نوع جواب انتظار داشته باشید، می توان به نوع جواب انتظار داشته باشید. با این حال، اگر با این سوال می توان به نوع جواب انتظار داشته باشید، می توان به نوع جواب انتظار داشته باشید. با این حال، اگر با این سوال می توان به نوع جواب انتظار داشته باشید، می توان به نوع جواب انتظار داشته باشید. با این حال، اگر با این سوال می توان به نوع جواب انتظار داشته باشید، می توان به نوع جواب انتظار داشته باشید. با 
 </td>
    <td>  </td>
  </tr>
</table>



-----------------------------------------------------------------





### Q9: 
```
یک فایل json حاوی این اطلاعات ایجاد کنید: bob، jon، mary و rich

```








<table width="300">
  <tr>
    <td> Model </td>
    <td> Answer </td>
    <td> Rating  </td>
  </tr> 
 <tr>
    <td> AVA-Llama-3 </td>
    <td> 
	    Here is a JSON file containing the information you requested:

```
[
  {
    "name": "Bob"
  },
  {
    "name": "Jon"
  },
  {
    "name": "Mary"
  },
  {
    "name": "Rich"
  }
]
```

If you want to add more information to each person, you can add additional properties to the JSON object. For example:

```
[
  {
    "name": "Bob",
    "age": 30,
    "city": "New York"
  },
  {
    "name": "Jon",
    "age": 25,
    "city": "Los Angeles"
  },
  {
    "name": "Mary",
    "age": 28,
    "city": "Chicago"
  },
  {
    "name": "Rich",
    "age": 35,
    "city": "San Francisco"
  }
]
```

Let me know if you have any other questions!
 </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V4 </td>
    <td> ساختن یک فایل json با این اطلاعات از قبل ایجاد شده است. این فایل json شامل اطلاعات دو نفر از افراد مانند bob و jon است. برای افزودن اطلاعات موجود در فایل json یا ایجاد جدید، باید از کاماند زیر استفاده کنید:

```
python add_person.py [person_name] [age] [gender] [occupation]
```
 </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V2 </td>
    <td>  ساده، این کار را با استفاده از زبان پروگرامینگ Python می‌توانیم انجام دهیم. ابتدا، یک فایل json با نام "people.json" به دست آورید. سپس، از کلاس dict در Python استفاده کرده، یک فایل json را ایجاد می‌کنیم که اطلاعات این چهار نام را با این فرمت برمی‌چارد:

import json

people = {
    "bob": {},
    "jon": {},
    "mary": {},
    "rich": {}
}

with open("people.json", "w") as f:
    json.dump(people, f) </td>
    <td>  </td>
  </tr>
    <tr>
    <td> Maral </td>
    <td>  با استفاده از یک فایل json به این صورت ایجاد کنید:
```json
{
    "نام ها": ["بوب", "جون", "مری", "ریچ"]
}
``` </td>
    <td>   </td>
  </tr>
    <tr>
    <td> Llama </td>
    <td> امروز چه نوع افراد را در مدرسه دانشگاه می‌دانید؟ می‌خوام بی‌نهایت افراد دو نوع را در مدرسه دانشگاه می‌دانم. این افراد با نام برادر و مرد است. برادر در مدرسه دانشگاه در دوره اول دوست دارند و مرد در دوره دوم دوست دارند. می‌خوام این افراد در مدرسه دانشگاه در حال تحصیل هستند. می‌خوام این افراد در مدرسه دانشگاه در حال تحصیل هستند. می‌خوام این افراد در مدرسه دانشگاه در حال تحصیل هستند. می‌خوام این افراد در مدرسه دانشگاه در حال تحصیل هستند. می‌خوام این افراد در مدرسه دانشگاه در حال تحصیل هستند. می‌خوام این افراد در مدرسه دانشگاه در حال تحصیل هستند. می‌خوام این افراد در مدرسه دانشگاه در حال تحصیل هستند. می
 </td>
    <td>  </td>
  </tr>
</table>




-----------------------------------------------------------------





### Q9: 
```
یک اسکریپت پایتون برای چاپ 1 تا 10 بنویسید

```







<table width="300">
  <tr>
    <td> Model </td>
    <td> Answer </td>
    <td> Rating  </td>
  </tr>
 <tr>
    <td> AVA-Llama-3 </td>
    <td> 
یک اسکریپت پایتون برای چاپ 1 تا 10 به این صورت می توان بنویسید:
```
for i in range(1, 11):
    print(i)
```
این اسکریپت یک حلقه برای loop 1 تا 10 ایجاد می کند و هر بار در هر دور، عدد فعلی را چاپ می کند.
    </td>
    <td> </td>
   <tr>
    <td> AVA-V4 </td>
    <td> این یک اسکریپت پایتون است که از 1 تا 10 چاپ می کند:
```python
for i in range(1, 11):
    print(i)
``` 
    </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V2 </td>
    <td> یک اسکریپت پایتون برای چاپ 1 تا 10 به شرح زیر برمی گرد:
```python
 این اسکریپت برای چاپ 1 تا 10 است
for i in range(1, 11):
    print(i)
```
این اسکریپت با استفاده از لوپ (loop) در زمان اجرایی به نام `range(1, 11)` از 1 تا 10 عدد را مشاهده می کند و هر عدد را با استفاده از فنکشن `print()` چاپ می کند.
  </td>
    <td>  </td>
  </tr>
    <tr>
    <td> Maral </td>
    <td> در اینجا یک اسکریپت پایتون برای چاپ 1 تا 10 وجود دارد:```
# این یک اسکریپت پایتون برای چاپ 1 تا 10 است.
for i in range(1, 11):
    چاپ(i)
``` </td>
    <td>   </td>
  </tr>
    <tr>
    <td> Llama </td>
    <td>  ### Assistant: این اسکریپت چاپ کنید و بعد از انجام چاپ، می توانید باز کنید. اگر نیاز به این اسکریپت ندارید، با موفقیت این اسکریپت را از منبع اصلی دانستید. اگر نیاز دارید، با موفقیت این اسکریپت را از منبع اصلی دانستید. اگر نیاز ندارید، می توانید این اسکریپت را از منبع اصلی دانستید. اگر نیاز دارید، می توانید این اسکریپت را از منبع اصلی دانستید. اگر نیاز ندارید، می توانید این اسکریپت را از منبع اصلی دانستید. اگر نیاز دارید، می توانید این اسکریپت را از منبع اصلی دانستید. اگر نیاز ندارید، می توانید این اسکریپت را از منبع اصلی دانستید. اگر نیاز دارید، می توانید این اسکریپت را از منبع اصلی دانستید. اگر نیاز ندارید
 </td>
    <td>  </td>
  </tr>
</table>





-----------------------------------------------------------------





### Q9: 
```
یک تابع node js برای دریافت رشته و تقسیم آن بر اساس فاصله بنویسید

```










<table width="300">
  <tr>
    <td> Model </td>
    <td> Answer </td>
    <td> Rating  </td>
  </tr>

   <tr>
    <td> AVA-Llama-3 </td>
    <td> 
	    
در اینجا یک تابع Node.js برای دریافت رشته و تقسیم آن بر اساس فاصله ارائه می شود:
```
function splitStringBySpace(str) {
  return str.split(' ');
}

// استفاده از تابع
const inputString = "Hello World";
const outputArray = splitStringBySpace(inputString);

console.log(outputArray); // [ "Hello", "World" ]
```
این تابع از روش `split` درbuilt-in `String` در Node.js استفاده می کند تا رشته را بر اساس فاصله (که با کاراکتر فاصله `space` مشخص می شود) تقسیم کند. سپس آرایه ای از رشته های جدا شده را بازمی گرداند.

اگر می خواهید رشته را بر اساس فاصله خاصی تقسیم کنید، می توانید از یک رشته به عنوان دومین آرگومان به روش `split` پاس دهید. برای مثال، برای تقسیم رشته بر اساس فاصله با فاصله 2 کاراکتر، می توانید از رشته `'\u0020'` استفاده کنید:
```
function splitStringBySpace(str) {
  return str.split('\u0020');
}

// استفاده از تابع
const inputString = "Hello   World";
const outputArray = splitStringBySpace(inputString);

console.log(outputArray); // [ "Hello", "World" ]
```
این تابع رشته را بر اساس فاصله 2 کاراکتر (که با کاراکتر فاصله `'\u0020'` مشخص می شود) تقسیم می کند. سپس آرایه ای از رشته های جدا شده را بازمی گرداند.
 </td>
    <td> </td>
  </tr>
 
   <tr>
    <td> AVA-V4 </td>
    <td> یک تابع Node.js برای دریافت رشته و تقسیم آن بر اساس فاصله به شما این کد پیوند می دهم:

```javascript
function splitStringBySpace(str) {
  return str.split(' ');
}

const inputString = "این یک رشته است که باید تقسیم شود";
const result = splitStringBySpace(inputString);
console.log(result);
```

این کد تابع `splitStringBySpace` برچسب کرده است که رشته وارد شده را با فاصله بنویسید. این کد را در نظر دهید و اگر نیاز به تغییرات دیگری دارید، لطفا بگویید.
 </td>
    <td> </td>
  </tr>
   <tr>
    <td> AVA-V2 </td>
    <td> یک تابع node js برای دریافت رشته و تقسیم آن بر اساس فاصله به شکل زیر می تواند باشد:

```javascript
function splitStringBySpace(str) {
  return str.split(' ');
}

// این تابع را برای استفاده در یک فایل node js مانند این فایل استفاده می کنیم:

const fs = require('fs');
const readline = require('readline');

const rl = readline.createInterface({
  input: fs.createReadStream('input.txt'),
  crlfDelay: Infinity
});

rl.on('line', (line) => {
  const words = splitStringBySpace(line);
  console.log(words);
});
```

در این کد، ابتدا به کار برده `readline` بخش های فایل ورودی را دریافت می کند. سپس تابع `splitStringBySpace` را برای تقسیم رشته ای که دریافت کرده ایم استفاده می کند. این تابع رشته را با فاصله های فارسی راهنمایی دار تقسیم می کند و به صورت مجزا برمی گرداند. نتیجه این کار این است که هر کلمه در یک عنصر مجزا قرار می گیرد. سپس این عنصرها را در کنسول نمایش می دهد.

 </td>
    <td>  </td>
  </tr>
    <tr>
    <td> Maral </td>
    <td> در اینجا یک تابع برای دریافت رشته و تقسیم آن بر اساس فاصله وجود دارد:```
جاوا اسکریپت
فنکشن تقسیم رشته (رشته) {
برای (فاصله از رشته) {
رشته ای برای رشته از فاصله تا فاصله بعدی ایجاد کنید
فاصله را بر اساس فاصله بعدی به رشته ای برای رشته اضافه کنید
}
برمی گردانید رشته ای برای رشته
}
```
در این تابع، رشته وارد شده به عنوان پارامتر وارد می شود. در طول تابع، رشته به عنوان یک رشته ای به عنوان یک رشته ای به عنوان یک رشته ای به عنوان یک رشته ای به عنوان یک رشته ای به عنوان یک رشته ای به عنوان یک رشته ای به عنوان یک رشته ای به عنوان یک رشته ای به عنوان یک رشته ای به عنوان یک رشته ای به عنوان یک رشته ای به عن </td>
    <td>   </td>
  </tr>
    <tr>
    <td> Llama </td>
    <td> - </td>
    <td>  </td>
  </tr>
</table>






-----------------------------------------------------------------




## License and Contributors

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](/LICENSE)

Released Sun 15, 2024

| Contributors      | Email               | LinkedIn                                 |
|-------------------|---------------------|------------------------------------------|
| Saba Ghasemzadeh | sabaghzd@gmail.com | [LinkedIn](https://www.linkedin.com/in/saba-ghasemzadehh/) |
| Mehdi Hosseini Moghadam          | m.h.moghadam1996@gmail.com | [LinkedIn](https://www.linkedin.com/in/john-doe/)          |




Attention ⚠️: The user is responsible for using AVA-Llama-3 / Persian Llama 3

Any misuse of the model (of any kind) is the responsibility of the user and not the creator






 
