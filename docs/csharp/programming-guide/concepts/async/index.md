---
title: "C'de asynchronous programlama #"
description: Async, await, Task ve Task kullanarak eşzamanlı programlama için C# dil desteğine genel bakış<T>
ms.date: 03/18/2019
ms.openlocfilehash: 4cbbff0f2c48f0ec2f8befa234ea5023465a1c5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79169915"
---
# <a name="asynchronous-programming-with-async-and-await"></a>Async ve await ile asenkron programlama

Görev asynchronous programlama modeli (TAP) asynchronous kodu üzerinde bir soyutlama sağlar. Her zamanki gibi kod dizilimi olarak yazarsın. Bu kodu, her deyim bir sonraki başlamadan önce tamamlanmış gibi okuyabilirsiniz. Derleyici, bu ifadelerden bazıları çalışmaya başlayıp devam eden <xref:System.Threading.Tasks.Task> çalışmayı temsil eden bir dönüşüm döndürebileceğinden bir dizi dönüşüm gerçekleştirir.

Bu sözdiziminin amacı budur: bir dizi deyim gibi okuyan, ancak dış kaynak tahsisine ve görevler tamamlandığında çok daha karmaşık bir sırada yürüten kodu etkinleştirin. İnsanların eşzamanlı görevleri içeren işlemler için nasıl talimat verdiğine benzer. Bu makale boyunca, bir dizi eşzamanlı yönerge içeren kod hakkında `async` `await` neden oluşturmayı nasıl kolaylaştırdığını görmek için kahvaltı yapmak için bir talimat örneği kullanırsınız. Nasıl bir kahvaltı yapmak açıklamak için aşağıdaki liste gibi talimatlar bir şey yazmak istiyorum:

1. Bir fincan kahve dök.
1. Bir tavayı ısıtın, sonra iki yumurta kızartın.
1. Üç dilim pastırma kızartın.
1. İki parça ekmeği kızartın.
1. Tost tereyağı ve reçel ekleyin.
1. Bir bardak portakal suyu dökün.

Eğer pişirme konusunda deneyime sahipseniz, bu talimatları **eşzamanlı olarak**uygularsınız. Yumurta için tavayı ısıtmaya başlarsın, sonra da pastırma başlardın. Ekmeği tost makinesine koyup yumurtaya başla. İşlemin her adımında, bir göreve başlar, sonra dikkatinizi çekmek için hazır olan görevlere dikkatinizi çekersiniz.

Yemek kahvaltı paralel olmayan asynchronous iş iyi bir örnektir. Bir kişi (veya iş parçacığı) tüm bu görevleri işleyebilir. Kahvaltı benzetmesini sürdüren bir kişi, ilk tamamlanmadan bir sonraki göreve başlayarak kahvaltıyı eş senkronize bir şekilde yapabilir. Yemek pişirme, birinin izlemesine bakılmaksızın ilerler. En kısa sürede yumurta için tava ısınma ya başlar, pastırma kızartma başlayabilirsiniz. Pastırma başladıktan sonra ekmeği tost makinesine koyabilirsiniz.

Paralel bir algoritma için birden çok aşçıya (veya iş parçacığına) ihtiyacınız vardır. Biri yumurta, diğeri pastırma, vesaire. Her biri sadece bir göreve odaklanacak. Her aşçı (veya iplik) senkronize pastırma çevirmek için hazır olması için bekleyen bloke olurdu, ya da pop tost.

Şimdi, C# ifadeleri olarak yazılmış aynı talimatları düşünün:

[!code-csharp[SynchronousBreakfast](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-starter/Program.cs#Main)]

Bilgisayarlar bu talimatları insanlar gibi yorumlamaz. Bilgisayar, bir sonraki deyime geçmeden önce çalışma tamamlanana kadar her ifadeyi engeller. Bu tatmin edici olmayan bir kahvaltı yaratır. Önceki görevler tamamlanana kadar sonraki görevler başlatılmazdı. Kahvaltıyı hazırlamak çok daha uzun sürerve bazı eşyalar servis edilmeden önce soğurdu.

Bilgisayarın yukarıdaki yönergeleri eşit olarak yürütmesini istiyorsanız, eşzamanlı kod yazmanız gerekir.

Bu endişeler bugün yazdığınız programlar için önemlidir. İstemci programları yazarken, Kullanıcı Arabirimi'nin kullanıcı girişine yanıt vermesini istersiniz. Uygulamanız, web'den veri indirirken bir telefonun dondurulmuş görünmesini sağlamalıdır. Sunucu programları yazarken, iş parçacıklarının engellenmesini istemezsin. Bu iş parçacıkları diğer isteklere hizmet ediyor olabilir. Eşzamanlı alternatifler mevcutolduğunda senkron kodu kullanmak, daha az pahalı ölçeklendirme yeteneğinizi zedeler. Bu engellenen konuları için ödeme.

Başarılı modern uygulamalar asynchronous kodu gerektirir. Dil desteği olmadan, eşkron kod yazmak, kodun özgün amacını gizleyen geri aramalar, tamamlama olayları veya başka yollarla gereklidir. Senkron kodun avantajı, kolay anlaşılır olmasıdır. Adım adım eylemler, tarayıp anlamayı kolaylaştırır. Geleneksel eşenkron modeller sizi kodun temel eylemlerine değil, kodun eşzamanlı doğasına odaklanmaya zorlar.

## <a name="dont-block-await-instead"></a>Engellemeyin, onun yerine bekleyin

Önceki kod kötü bir uygulama gösterir: eşzamanlı işlemleri gerçekleştirmek için senkron kod oluşturma. Yazıldığı gibi, bu kod iş parçacığının başka bir iş yapmasını engeller. Görevlerin hiçbiri devam ederken kesintiye uğramaz. Ekmeği koyduktan sonra tost makinesine bakmış gibi olursun. Tost patlayana kadar seninle konuşan ları görmezden gelirdin.

İş parçacığının görevler çalışırken engellememesi için bu kodu güncelleyerek başlayalım. Anahtar `await` kelime, bir görevi başlatmak için engellenmeyen bir yol sağlar ve bu görev tamamlandığında yürütmeye devam eder. Bir kahvaltı kodu yapmak basit bir asynchronous sürümü aşağıdaki snippet gibi görünür:

[!code-csharp[SimpleAsyncBreakfast](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V2/Program.cs#Main)]

Yumurta lar veya domuz pastırması pişerken bu kod engellenmez. Bu kod başka görevleri başlatmaz. Yine de tost makinesine tost koyar ve patlayana kadar ona bakardın. Ama en azından dikkatini çekmek isteyen herkese cevap verirsin. Birden fazla sipariş verilen bir restoranda, aşçı ilk yemek yaparken başka bir kahvaltı başlayabilir.

Şimdi, henüz bitmemiş herhangi bir başlangıç görevi beklerken kahvaltı üzerinde çalışan konu engellenmez. Bazı uygulamalar için bu değişiklik gereken tek şeydir. Bir GUI uygulaması yine de kullanıcıya yalnızca bu değişiklikle yanıt verir. Ancak, bu senaryo için daha fazlasını istiyorsunuz. Bileşen görevlerinin her birinin sırayla yürütülmesini istemezsin. Önceki görevin tamamlanmasını beklemeden önce bileşen görevlerinin her birini başlatmak daha iyidir.

## <a name="start-tasks-concurrently"></a>Görevleri aynı anda başlatma

Birçok senaryoda, hemen birkaç bağımsız görevi başlatmak istiyorsunuz. Daha sonra, her görev sona ererken, hazır olan diğer işlere devam edebilirsiniz. Kahvaltı benzetmesinde, kahvaltıyı bu şekilde daha hızlı halledebilirsiniz. Ayrıca her şeyi aynı anda yakın yapılır olsun. Sıcak bir kahvaltı alacaksın.

Ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ilgili türler, devam etmekte olan görevler hakkında neden olmak için kullanabileceğiniz sınıflardır. Bu, aslında kahvaltı oluşturmak istiyorum şekilde daha yakından benzer kod yazmak için olanak sağlar. Aynı anda yumurta, pastırma ve tost pişirmeye başlardın. Her biri eylem gerektirdiğinden, dikkatinizi bu göreve yöneltirsiniz, bir sonraki eylemle ilgilenir, sonra da dikkatinizi gerektiren başka bir şeyi beklersiniz.

Bir görevi başlatın ve <xref:System.Threading.Tasks.Task> çalışmayı temsil eden nesneye tutunun. Sonucuyla `await` çalışmadan önce her görev iniz.

Kahvaltı kanununda şu değişiklikleri yapalım. İlk adım, görevleri beklemek yerine, başladıklarında işlemler için depolamaktır:

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");
Task<Egg> eggsTask = FryEggs(2);
Egg eggs = await eggsTask;
Console.WriteLine("eggs are ready");
Task<Bacon> baconTask = FryBacon(3);
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");
Task<Toast> toastTask = ToastBread(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Console.WriteLine("Breakfast is ready!");
```

Daha sonra, kahvaltı `await` sunmadan önce, yöntemin sonuna pastırma ve yumurta için ifadeler taşıyabilirsiniz:

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");
Task<Egg> eggsTask = FryEggs(2);
Task<Bacon> baconTask = FryBacon(3);
Task<Toast> toastTask = ToastBread(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Egg eggs = await eggsTask;
Console.WriteLine("eggs are ready");
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Console.WriteLine("Breakfast is ready!");
```

Önceki kod daha iyi çalışır. Tüm eşzamanlı görevleri aynı anda başla. Her görevi yalnızca sonuçlara ihtiyacınız olduğunda beklersiniz. Önceki kod, farklı mikro hizmetlerden istekte bulunan, ardından sonuçları tek bir sayfada birleştiren bir web uygulamasındaki koda benzer olabilir. Tüm istekleri hemen yapacaksınız, `await` ardından tüm bu görevler ve web sayfası oluşturacaksınız.

## <a name="composition-with-tasks"></a>Görevlerle kompozisyon

 Tost hariç her şeyi aynı anda kahvaltı için hazır. Tost yapmak bir asynchronous operasyon (ekmek kızartma) ve senkron işlemleri (tereyağı ve reçel ekleyerek) bileşimidir. Bu kodun güncelleştirilmesi önemli bir kavramı göstermektedir:

> [!IMPORTANT]
> Senkron çalışmanın ardından bir eşzamanlı işlemin bileşimi asynchronous işlemidir. Başka bir şekilde belirtildiği gibi, bir işlemin herhangi bir bölümü asynchronous ise, tüm işlem asynchronous olduğunu.

Önceki kod, çalışan görevleri tutmak <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> için kullanabileceğinizi veya nesneleri gösterebileceğinizi gösterdi. `await` Sonucunu kullanmadan önce her görev. Bir sonraki adım, diğer çalışmaların birleşimini temsil eden yöntemler oluşturmaktır. Kahvaltı servis etmeden önce, tereyağı ve reçel eklemeden önce ekmek kızartma temsil eden görevi beklemek istiyorum. Bu çalışmayı aşağıdaki kodla temsil edebilirsiniz:

[!code-csharp[ComposeToastTask](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V3/Program.cs#ComposeToastTask)]

Önceki yöntemin imzasında `async` değiştirici vardır. Derleyiciye bu yöntemin bir `await` deyim içerdiğini bildirir; eşzamanlı işlemler içerir. Bu yöntem, ekmek tost görevi temsil eder, sonra tereyağı ve reçel ekler. Bu yöntem, <xref:System.Threading.Tasks.Task%601> bu üç işlemin bileşimini temsil eden bir döndürür. Ana kod bloğu şimdi olur:

[!code-csharp[StartConcurrentTasks](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V3/Program.cs#Main)]

Önceki değişiklik asynchronous kodu ile çalışmak için önemli bir teknik gösterdi. İşlemleri bir görevi döndüren yeni bir yönteme ayırarak görevleri oluşturursunuz. Bu görevi ne zaman bekleyeceğinizi seçebilirsiniz. Diğer görevleri aynı anda başlatabilirsiniz.

## <a name="await-tasks-efficiently"></a>Görevleri verimli bir şekilde bekleyin

Önceki kodun sonundaki `await` ifadeler dizisi `Task` sınıfın yöntemleri kullanılarak geliştirilebilir. Aşağıdaki kodda gösterildiği <xref:System.Threading.Tasks.Task.WhenAll%2A>gibi, <xref:System.Threading.Tasks.Task> bağımsız değişken listesindeki tüm görevler tamamlandığında tamamlayan apilerden biri olan API'ler:

```csharp
await Task.WhenAll(eggsTask, baconTask, toastTask);
Console.WriteLine("eggs are ready");
Console.WriteLine("bacon is ready");
Console.WriteLine("toast is ready");
Console.WriteLine("Breakfast is ready!");
```

Başka bir seçenek <xref:System.Threading.Tasks.Task.WhenAny%2A>kullanmaktır `Task<Task>` , hangi bir döner bir tamamlar herhangi bir bağımsız değişkenleri tamamlar. İade edilen görevi, zaten tamamlandığını bilerek bekleyebilirsiniz. Aşağıdaki kod, bitirmek ve <xref:System.Threading.Tasks.Task.WhenAny%2A> sonra sonucunu işlemek için ilk görevi beklemek için nasıl kullanabileceğinizi gösterir. Tamamlanan görevden sonucu işledikten sonra, tamamlanan görevi ' ye `WhenAny`geçirilen görevler listesinden kaldırırsınız.

[!code-csharp[AwaitAnyTask](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-final/Program.cs#AwaitAnyTask)]

Tüm bu değişikliklerden `Main` sonra, son sürümü aşağıdaki kod gibi görünür:

[!code-csharp[Final](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-final/Program.cs#Main)]

Bu son kod asynchronous olduğunu. Daha doğru bir kişinin bir kahvaltı pişirmek nasıl yansıtır. Önceki kodu bu makaledeki ilk kod örneğiyle karşılaştırın. Temel eylemler hala kodu okuma açıktır. Bu kodu, bu makalenin başında kahvaltı yapmak için bu talimatları okuduğunuz gibi okuyabilirsiniz. Dil özellikleri `async` için `await` her kişi bu yazılı yönergeleri takip etmek için yapar çeviri sağlar: mümkün olduğunca görevleri başlatmak ve görevleri tamamlamak için bekleyen engellemeyin.
