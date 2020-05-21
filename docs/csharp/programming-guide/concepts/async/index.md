---
title: "C 'de zaman uyumsuz programlama #"
description: Async, await, Task ve Task kullanılarak zaman uyumsuz programlama için C# dil desteğine genel bakış<T>
ms.date: 03/18/2019
ms.openlocfilehash: 4bf00d5c77138dfa2d527a262a6cd54a72a688f5
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761856"
---
# <a name="asynchronous-programming-with-async-and-await"></a>Async ve await ile asenkron programlama

Görev zaman uyumsuz programlama modeli (TAP), zaman uyumsuz kod üzerinde bir soyutlama sağlar. Her zaman olduğu gibi, kodu deyimler dizisi olarak yazarsınız. Bu kodu, bir sonraki başlamadan önce her bir deyimin tamamlansa da okuyabilirsiniz. Derleyici bir dizi dönüştürme gerçekleştirir, çünkü bu deyimlerden bazıları işe başlayabilir ve <xref:System.Threading.Tasks.Task> devam eden çalışmayı temsil eden bir döndürür.

Bu sözdiziminin amacı: bir deyim dizisi gibi okuyan kodu etkinleştirin, ancak dış kaynak ayırmaya ve görevler tamamlandığında çok daha karmaşık bir sırayla yürütülür. Kullanıcıların zaman uyumsuz görevler içeren işlemlere yönelik yönergeler verme yöntemi benzerdir. Bu makalede, `async` ve `await` anahtar sözcüklerinin, bir dizi zaman uyumsuz yönergeler içeren kodla ilgili neden olmasının nasıl daha kolay olduğunu görmek için bir yönergeler örneği kullanacaksınız. Daha hızlı nasıl yapılacağını açıklamak için aşağıdaki listeye benzer yönergeler yazın:

1. Kahve kupa dök.
1. Bir Pan, sonra da iki Yumura kadar bir kaydır.
1. Bacon üç dilimi.
1. İki adet içerik.
1. Bildirim 'e alın ve sıkıştı ekleyin.
1. Turuncu bir büyütece bir cam dök.

Pişirme deneyiminiz varsa, bu yönergeleri **zaman uyumsuz**olarak yürütebilirsiniz. Yumurlar için kaydırmayı ısıncak ve sonra Bacon 'u başlatacak. Ekseyi Toaster ' a yerleştirip yumurtalar ' ı başlatın. İşlemin her adımında bir görev başlatır, sonra ilgilenmeniz için uygun olan görevlere dikkat etmeniz gerekir.

Pişirme kahileri, paralel olmayan bir zaman uyumsuz çalışmaya yönelik iyi bir örnektir. Bir kişi (veya iş parçacığı), tüm bu görevleri işleyebilir. Breakfast benzerleme vurguladı devam ederken bir kişi, ilk tamamlanmadan önce sonraki görevi başlatarak zaman uyumsuz olarak zaman uyumsuz hale getirebilirsiniz. Pişirme işlemi, birisinin onu izliyor olup olmadığı konusunda ilerler. Yumurlar için kaydırma işlemini başlattığınızda, Bacon kızartma başlayabilirsiniz. Bacon başladıktan sonra, ekseyi Toaster 'a yerleştirebilirsiniz.

Paralel bir algoritma için birden çok ortak iş (veya iş parçacığı) gerekir. Bunlardan biri, bir, Bacon, vb. olur. Her biri yalnızca bir göreve odaklanılmıştır. Her bir Cook (veya iş parçacığı), Bacon 'un çevrilmeye hazırlanması veya bildirim açılanması için zaman uyumlu olarak engelleniyor.

Şimdi C# deyimleri olarak yazılmış yönergeleri göz önünde bulundurun:

[!code-csharp[SynchronousBreakfast](./snippets/index/AsyncBreakfast-starter/Program.cs#Main)]

Bilgisayarlar bu yönergeleri insanlar ile aynı şekilde yorumlamaz. Bir sonraki ifadeye geçmeden önce, bilgisayar her bir bildirimde, iş tamamlanana kadar engeller. Bu, karşılanunan bir Breakfast oluşturur. Daha sonraki görevler, önceki görevler tamamlanana kadar başlatılamaz. Daha uzun sürer ve bazı öğeler sunulmadan önce soğuk hale gelir.

Bilgisayarın yukarıdaki yönergeleri zaman uyumsuz olarak yürütmesini istiyorsanız, zaman uyumsuz kod yazmanız gerekir.

Bu sorunlar, bugün yazdığınız programlar için önemlidir. İstemci programları yazdığınızda, kullanıcı ARABIRIMININ Kullanıcı girişine yanıt vermesini istersiniz. Uygulamanız, Web 'den veri indirirken bir telefonu dondurulmuş hale döndürmemelidir. Sunucu programları yazdığınızda, iş parçacıklarının engellenmesini istemezsiniz. Bu iş parçacıkları diğer isteklere hizmet verebilir. Zaman uyumsuz alternatifler mevcut olduğunda zaman uyumlu kod kullanarak daha ucuz bir şekilde ölçeklendirme imkanına sahip olabilirsiniz. Engellenen bu iş parçacıkları için ödeme yaparsınız.

Başarılı modern uygulamalar zaman uyumsuz kod gerektirir. Dil desteği olmadan, zaman uyumsuz kod gerekli geri çağırmaları, tamamlanma olaylarını veya başka bir deyişle, kodun orijinal hedefini görünmez hale gelir. Zaman uyumlu kodun avantajı, anlaşılması kolay bir işlemdir. Adım adım eylemler, taramayı ve anlamayı kolaylaştırır. Geleneksel zaman uyumsuz modeller kodun temel eylemlerine değil, kodun zaman uyumsuz yapısına odaklanmaya zorlanır.

## <a name="dont-block-await-instead"></a>Engelleme, yerine await

Yukarıdaki kodda kötü bir uygulama gösterilmektedir: zaman uyumsuz işlemleri gerçekleştirmek için zaman uyumlu kod oluşturma. Yazıldığı gibi, bu kod başka herhangi bir işi yapmadan yürüten iş parçacığını engeller. Görevlerden herhangi biri devam ederken bu işlem kesintiye uğramaz. Bu, ' ın içine yerleştirdikten sonra Toaster ' ta başmış gibi olacaktır. Bildirim alınana kadar sizi konuşuyor olan herkesi yoksayabilirsiniz.

İş parçacığı, görevler çalışırken engellenmemesi için bu kodu güncelleyerek başlayalım. `await`Anahtar sözcüğü, bir görevi başlatmak için engellenmeyen bir yöntem sağlar ve ardından bu görev tamamlandığında yürütmeye devam eder. Bir Breakfast kodu oluştur 'un basit bir zaman uyumsuz sürümü aşağıdaki kod parçacığına benzer:

[!code-csharp[SimpleAsyncBreakfast](./snippets/index/AsyncBreakfast-V2/Program.cs#Main)]

Bu kod, yumurtalar veya Bacon pişirirken engellenmez. Bu kod, diğer görevleri de başlatmayacaktır. Yine de bildirim, siz de bir araya gelene kadar Toaster 'a yerleştirirsiniz. Ancak en azından, ilgilenmeniz istenen herkese yanıt verirsiniz. Birden çok siparişin yerleştirildiği bir restoran içinde, ilk pişirme sırasında Cook bir daha hızlı başlatılabilir.

Şimdi, henüz bitmemiş olan herhangi bir başlatılan görevi beklerken, Kahvalı üzerinde çalışan iş parçacığı engellenmiyor. Bazı uygulamalarda, bu değişiklik gereklidir. Yalnızca bu değişikliğe sahip bir GUI uygulaması kullanıcıya yanıt veriyor. Ancak, bu senaryo için daha fazla bilgi istersiniz. Her bileşen görevinin her ardışık olarak yürütülmesini istemezsiniz. Önceki görevin tamamlanmasını beklerken önce her bir bileşen görevinin başlatılması daha iyidir.

## <a name="start-tasks-concurrently"></a>Görevleri eşzamanlı olarak Başlat

Birçok senaryoda, birkaç bağımsız görevi hemen başlatmak istersiniz. Ardından, her bir görev tamamlandığında, daha önce hazırlanmaya devam edebilirsiniz. Kahhızlı benzerleme vurguladı, daha hızlı bir şekilde daha hızlı bir şekilde daha hızlı bir şekilde yapılır. Her şeyin aynı anda kapatılmasını de sağlar. Sık erişimli bir kahvaltı alacaksınız.

<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>Ve ilgili türler, sürmekte olan görevlerle ilgili nedenlerle kullanabileceğiniz sınıflardır. Bu sayede, aslında daha iyi bir şekilde daha çok benzeyen bir kod yazmanızı sağlar. Eggs, Bacon ve bildirim ' ı aynı anda aşalım. Her biri bir eylem gerektirdiğinden, bu göreve dikkat etmeniz, sonraki eylemi ele almanız ve daha sonra ilgilenmeniz gereken başka bir şey için await ' ı kapatmanız gerekir.

Bir görevi başlatır ve <xref:System.Threading.Tasks.Task> işi temsil eden nesneyi basılı tutabilirsiniz. `await`Sonucuyla çalışmadan önce her görevi gerçekleştirirsiniz.

Bu değişiklikleri Breakfast kodunda yapalim. İlk adım, işlemler için görevleri her zaman beklerken depolamak yerine depolarlar:

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

Daha sonra, bir sonraki `await` ve yumurg deyimlerini, Breakfast sunmadan önce yönteminin sonuna taşıyabilirsiniz:

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

Yukarıdaki kod daha iyi çalışmaktadır. Tüm zaman uyumsuz görevleri aynı anda başlatabilirsiniz. Her bir görevi yalnızca sonuçlara ihtiyacınız olduğunda bekleolursunuz. Yukarıdaki kod, farklı mikro hizmetlere istek yapan bir Web uygulamasındaki koda benzer ve sonuçları tek bir sayfada birleştirir. Tüm istekleri hemen, ardından `await` Tüm bu görevleri ve Web sayfasını oluşturduğunuz şekilde yaparsınız.

## <a name="composition-with-tasks"></a>Görevlerle oluşturma

 Bildirim hariç her şeyi aynı anda kah, daha hızlı bir şekilde hazırlayın. Bildirim, zaman uyumsuz bir işlemin (Ekleyici) ve zaman uyumlu işlemlerin (alın ve sıkışan) bir bileşim haline getirilmesi. Bu kodun güncelleştirilmesi önemli bir kavramı gösterir:

> [!IMPORTANT]
> Zaman uyumsuz bir işlemin ardından zaman uyumlu iş tarafından oluşturulması zaman uyumsuz bir işlemdir. Başka bir şekilde ifade edilen bir işlemin herhangi bir bölümü zaman uyumsuz ise, tüm işlem zaman uyumsuzdur.

Yukarıdaki kod, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> çalışan görevleri tutmak için veya nesneleri kullanacağınızı gösterdi. `await`Sonucunu kullanmadan önce her görevi gerçekleştirebilirsiniz. Sonraki adım, diğer çalışmanın birleşimini temsil eden yöntemler oluşturmaktır. Kahvileri sunmadan önce, Butter ve sıkışmadan önce Ekleyici 'yi temsil eden görevi beklemek istersiniz. Bu işi aşağıdaki kodla temsil edebilirsiniz:

[!code-csharp[ComposeToastTask](./snippets/index/AsyncBreakfast-V3/Program.cs#ComposeToastTask)]

Önceki Yöntem `async` imzasında değiştiriciye sahiptir. Bu yöntemin bir ifade içerdiğini derleyiciye bildirir `await` ; zaman uyumsuz işlemler içerir. Bu yöntem, Ekleyici ve sıkışıklığı ekleyen görevi temsil eder. Bu yöntem, bu <xref:System.Threading.Tasks.Task%601> üç işlemin oluşumunu temsil eden bir döndürür. Kodun ana bloğu şu şekilde olur:

[!code-csharp[StartConcurrentTasks](./snippets/index/AsyncBreakfast-V3/Program.cs#Main)]

Önceki değişiklik, zaman uyumsuz kod ile çalışmak için önemli bir teknik gösterilmiştir. İşlemleri bir görevi döndüren yeni bir yönteme ayırarak görevleri oluşturursunuz. Bu görevin ne zaman bekleme seçeneğini belirleyebilirsiniz. Diğer görevleri eşzamanlı olarak başlatabilirsiniz.

## <a name="await-tasks-efficiently"></a>Görevleri verimli olarak await

`await`Önceki kodun sonundaki deyim dizileri, sınıfının yöntemleri kullanılarak artırılabilir `Task` . Bu API 'lerden biri, <xref:System.Threading.Tasks.Task.WhenAll%2A> <xref:System.Threading.Tasks.Task> aşağıdaki kodda gösterildiği gibi, bağımsız değişken listesindeki tüm görevler tamamlandığında tamamlanan bir döndürür.

```csharp
await Task.WhenAll(eggsTask, baconTask, toastTask);
Console.WriteLine("eggs are ready");
Console.WriteLine("bacon is ready");
Console.WriteLine("toast is ready");
Console.WriteLine("Breakfast is ready!");
```

Diğer bir seçenek de <xref:System.Threading.Tasks.Task.WhenAny%2A> , `Task<Task>` bağımsız değişkenlerinden herhangi biri tamamlandığında tamamlanan bir döndürür. Döndürülen görevi, zaten bitdiğinin farkında olacak şekilde beklede olursunuz. Aşağıdaki kod, <xref:System.Threading.Tasks.Task.WhenAny%2A> ilk görevin bitmesini beklemek için nasıl kullanabileceğinizi gösterir ve sonra sonucunu işleyebilir. Tamamlanan görevden elde edilen sonucu işledikten sonra, bu tamamlanmış görevi öğesine geçirilen görev listesinden kaldırırsınız `WhenAny` .

[!code-csharp[AwaitAnyTask](./snippets/index/AsyncBreakfast-final/Program.cs#AwaitAnyTask)]

Tüm bu değişiklikler yapıldıktan sonra nihai sürümü `Main` Aşağıdaki kod gibi görünür:

[!code-csharp[Final](./snippets/index/AsyncBreakfast-final/Program.cs#Main)]

Bu son kod zaman uyumsuzdur. Bu, bir kişinin ne kadar hızlı bir şekilde bir kahtacağını daha doğru yansıtır. Yukarıdaki kodu, bu makaledeki ilk kod örneğiyle karşılaştırın. Temel eylemler, kodu okumayı hala temizler. Bu kodu, bu makalenin başlangıcında bir daha hızlı hale getirmek için bu talimatları okuduğunuzdan aynı şekilde okuyabilirsiniz. İçin dil özellikleri `async` ve `await` çeviri, her birinin bu yazılı yönergeleri izlemesini sağlar: Başlangıç görevleri, yaptığınız gibi başlatın ve görevlerin tamamlanmasını beklemeyi engellemez.
