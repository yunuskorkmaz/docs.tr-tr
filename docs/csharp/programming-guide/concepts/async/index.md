---
title: C# zaman uyumsuz programlama
description: Genel bir bakış C# await, görev ve görev kullanarak zaman uyumsuz, zaman uyumsuz programlama için dil desteği<T>
ms.date: 03/18/2019
ms.openlocfilehash: a306ff75357f9f61ec9b086485472d99de5ad083
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307134"
---
# <a name="the-task-asynchronous-programming-model-in-c"></a>Görev zaman uyumsuz programlama modeli C\#

Görev zaman uyumsuz programlama modeli (TAP) zaman uyumsuz kod bir Özet sağlar. Deyimler, olduğu gibi her zaman bir dizisi olarak kodunu yazın. Sonraki başlamadan önce her deyimi tamamlar ancak bu kodu okuyabilirsiniz. Bu deyimleri bazıları iş Başlat ve dönüş çünkü derleyici bir dizi dönüşümleri gerçekleştirir bir <xref:System.Threading.Tasks.Task> , devam eden çalışmayı temsil eder.

Bu söz dizimi amacı olan: kod, bir dizi ifadeleri gibi okumaktadır, ancak dış kaynak tahsisine dayalı olarak çok daha karmaşık bir sırayla yürütür ve görevleri tamamlandığında etkinleştirin. Kişilerin ne zaman uyumsuz görevler içeren işlemler için yönergeler vermek benzerdir. Bu makale boyunca yönergeleri örneği görmek için bir kahvaltı yapmak için kullanacağınız nasıl `async` ve `await` anahtar sözcükleri zaman uyumsuz yönergeler bir dizi içeren kod hakkında nedeni kolaylaştırır. Aşağıdakine benzer bir kahvaltı yapma açıklamak için aşağıdaki listeyi yönergeleri yazmalısınız:

1. Kahve dök.
1. Bir kaydırma ısı ve ardından iki örneğin sucuklu fry.
1. Üç dilimleri bacon fry.
1. Ekmekler iki parça kutlayın.
1. Bildirim için ezmesi ve Başınızı ekleyin.
1. Bir cam Portakal suyu, dök.

Deneyimi Aşçılık ile varsa, bu yönergeleri yürütülür **zaman uyumsuz olarak**. Örneğin sucuklu için kaydırma hazırlanıyor Başlat sonra bacon başlatın. İçinde toaster ekmek put sonra Örneğin sucuklu başlatın. İşlemin her adımında bir görev başlatın ardından dikkatinizi dinlediğiniz için hazır olan görevleri açmak.

Kahvaltı Aşçılık, paralel olmayan zaman uyumsuz iş iyi bir örnektir. Bu görevleri tek bir kişi (veya iş parçacığı) işleyebilir. Kahvaltı benzerliği devam, tek bir kişi kahvaltı zaman uyumsuz olarak ilk tamamlanmadan önce sonraki görev başlatarak yapabilirsiniz. Birisi izliyor olup olmadığını Aşçılık ilerler. Örneğin sucuklu için kaydırma hazırlanıyor başlar başlamaz, bacon frying başlayabilirsiniz. Bir kez bacon başladığında, ekmek toaster koyabilirsiniz.

Bir paralel algoritma için birden çok aşçılarına (veya iş parçacığı) gerekir. Örneğin sucuklu oluşturmak bir bacon ve benzeri. Her biri, bir görev için odaklanmış. Her cook (veya iş parçacığı) zaman uyumlu olarak bacon ters çevirmek hazır olması ya da açılan için bildirim için bekleyen engellenebilir. 

Şimdi, olarak yazılan bu yönergeleri göz önünde bulundurun C# ifadeleri:

[!code-csharp[SynchronousBreakfast](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-starter/Program.cs#Main)]

Bilgisayarlar, aynı şekilde yaptığı bu yönergeleri yorumlar yok. Sonraki deyimi geçmeden önce iş tamamlanana kadar bilgisayar her deyim engeller. Bir unsatisfying kahvaltı oluşturur. Sonraki görevlerde, önceki görevlerden tamamlamadığı kadar çalışmaya mıydı. Kahvaltı oluşturmak için daha uzun sürer ve bazı öğeler hizmet önce soğuk edindiğiniz. 

Yukarıdaki yönergeleri zaman uyumsuz olarak yürütmek için bilgisayar istiyorsanız, zaman uyumsuz kod yazmanız gerekir.

Bu sorunlar, bugün yazma programları için önemlidir. İstemci programları yazdığınızda, kullanıcı girişine yanıt olarak UI istersiniz. Uygulamanızı bir telefon Web'den veri yüklenirken dondurulmuş görünür hale olmamalıdır. Sunucu programlarından yazdığınızda, engellenen iş parçacıkları istemezsiniz. Bu iş parçacıkları, diğer isteklerine hizmet. Zaman uyumsuz seçenekler varken zaman uyumlu bir kod kullanarak küçük expensively ölçeklendirme olanağı gelmez. Bu engellenen iş parçacıkları için ödeme yaparsınız.

Başarılı modern uygulamalar, zaman uyumsuz kod gerektirir. Dil desteği olmadan geri çağırmaları, tamamlama veya özgün kodun amacı engellediği başka bir yolla zaman uyumsuz kod yazma gereklidir. Zaman uyumlu bir kod avantajlarından anlaşılması kolay olmasıdır. Adım adım eylemleri tarama ve anlaşılmasını kolaylaştırır. Geleneksel zaman uyumsuz modeller, odağı zorla zaman uyumsuz kod yapısını, kodun temel eylemleri üzerinde değil.

## <a name="dont-block-await-instead"></a>Engelleme, bunun yerine await yok

Yukarıdaki kod, hatalı bir uygulama gösterilmektedir: zaman uyumsuz işlemleri gerçekleştirmek için zaman uyumlu kod oluşturma. Bu kod, yazıldığı gibi herhangi bir iş yapmasını yürütme iş parçacığını engeller. Görevlerden herhangi birini devam ederken durdurulmayacaktır. Ekmekler koymaya sonra toaster stared gibi sorgulamanıza olacaktır. Herkes bildirim POP kadar size Konuşmayı yoksay. 

Görevler çalışırken iş parçacığını engellemez, böylece bu kodu güncelleştirerek başlayalım. `await` Anahtar sözcüğü, bir görev başlatır ve ardından o görev tamamlandıktan sonra yürütmeye devam etmek için engelleyici olmayan bir yol sağlar. Basit bir zaman uyumsuz yap sürümü kahvaltı kodu aşağıdaki kod parçacığı gibi görünür:

[!code-csharp[SimpleAsyncBreakfast](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V2/Program.cs#Main)]

Bu kod, örneğin sucuklu veya bacon Aşçılık sırada engellemez. Bu kod, ancak herhangi bir görevi başlatılmaz. Yine de bildirim içinde toaster yerleştirin ve onu POP kadar adresinden stare. Ancak, en azından, ilgilenmenizi istediği herkes yanıtlamayı ister. İlk tarifinizi sırada birden çok sipariş yerleştirildiği bir restoran başka bir kahvaltı cook başlatabilir.

Şimdi, kahvaltı üzerinde çalışan iş parçacığı henüz tamamlanmadı başlatılan tüm görev beklerken bloke değildir. Bazı uygulamalar için bu değişiklik tüm gereken kullanılır. Bu değişikliği yalnızca kullanıcıya bir GUI uygulama hala yanıt verir. Ancak, bu senaryo için daha fazla istersiniz. Her bileşen görevleri sırayla yürütülen istemezsiniz. Bileşen görevlerin her biri önceki görevin tamamlanmasını bekleme önce başlatmak daha iyidir.

## <a name="start-tasks-concurrently"></a>Eşzamanlı olarak başlangıç görevleri

Birçok senaryoda birkaç bağımsız görev hemen başlamak istiyorsanız. Ardından, her görev bittikçe hazır olan başka bir iş devam edebilirsiniz. Kahvaltı benzerleme daha hızlı bir şekilde bitti kahvaltı nasıl ulaşabileceğinizi olmasıdır. Her şey bitti ayrıca Al aynı anda yakın. Sık erişimli kahvaltı elde edersiniz.

<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Ve ilişkili sınıflar nedeni, sürmekte olan görevler hakkında için kullanabilirsiniz. Aslında kahvaltı oluşturacak şekilde daha yakından benzeyen bir kod yazmanızı sağlar. Örneğin sucuklu bacon ve bildirim aynı anda Aşçılık başlar. Her eylem gerektirdiğinden, dikkatinizi görev açın, sonraki eylemi ilgileniriz sonra başka bir şey ilgilenmenizi gerektiren await.

Bir görevi başlatıp oturum tutun <xref:System.Threading.Tasks.Task> işi temsil eden nesne. Artıracaksınız `await` her görev kendi sonucu ile çalışmaya başlamadan önce.

Bu değişiklikler kahvaltı koda olalım. İlk adım, bunları bekleyen yerine bunların başlattığınızda işlemleri için görevleri depolamaktır:

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");
Task<Egg> eggTask = FryEggs(2);
Egg eggs = await eggTask;
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

Ardından, taşımak `await` kahvaltı tanıtıcısıyla önce deyimleri, yöntemin sonuna Yumurta ve bacon için:

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");
Task<Egg> eggTask = FryEggs(2);
Task<Bacon> baconTask = FryBacon(3);
Task<Toast> toastTask = ToastBread(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Egg eggs = await eggTask;
Console.WriteLine("eggs are ready");
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Console.WriteLine("Breakfast is ready!");
```

Yukarıdaki kod daha iyi çalışır. Zaman uyumsuz görevlerin tümü aynı anda başlatın. Sonuçları yalnızca ihtiyacınız olduğunda her görev bekler. Yukarıdaki kod, farklı mikro isteği yapan ve ardından sonuçları birleştirir tek bir sayfada bir web uygulamasındaki kod benzer olabilir. Tüm istekleri hemen sonra yapacaksınız `await` olan tüm görevleri ve web sayfası oluşturun.

## <a name="composition-with-tasks"></a>Görevler oluşturma

 Bildirim dışında aynı anda kahvaltı hazır her şeye sahip. Bildirim zaman uyumsuz bir işlem (ekmek toasting) ve zaman uyumlu işlemler (ezmesi ve Başınızı ekleme) olarak sunuluyor. Bu kod güncelleştirme bir önemli kavramı gösterir:

> [!IMPORTANT]
> Zaman uyumlu iş tarafından izlenen zaman uyumsuz bir işlem olarak bir zaman uyumsuz bir işlemdir. Başka bir deyişle, belirtilen zaman uyumsuz bir işlemi herhangi bir kısmını ise, tüm zaman uyumsuz bir işlemdir.

Yukarıdaki kod, kullanabileceğiniz gösterdi <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> çalışmakta olan görevlerin tutacak nesne. `await` Her görev kendi sonucu kullanmadan önce. Sonraki adım, diğer iş bileşimini temsil eden yöntemleri oluşturmaktır. Kahvaltı sunmadan önce ezmesi ve Başınızı eklemeden önce ekmek toasting temsil eden görev await istersiniz. Aşağıdaki kod ile çalışan temsil edebilir:

[!code-csharp[ComposeToastTask](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V3/Program.cs#ComposeToastTask)]

Önceki yöntem sahip `async` imzası değiştiricisi. Bu sinyalleri için derleyici bu yöntemini içeren bir `await` deyimi; zaman uyumsuz işlemleri içerir. Bu yöntem ekmek toasts sonra ezmesi ve Başınızı ekler görevi temsil eder. Bu yöntem döndürür bir <xref:System.Threading.Tasks.Task%601> , bu üç işlemi olarak temsil eder. Artık kod ana blok olur:

[!code-csharp[StartConcurrentTasks](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V3/Program.cs#Main)]

Önceki değişiklik, zaman uyumsuz kod ile çalışmak için önemli bir teknik gösterilmektedir. Görevler, bir görev döndüren yeni bir yöntem işlemlere ayrılarak oluşturun. Bu görevi beklemek ne zaman seçebilirsiniz. Eşzamanlı olarak başka görevler başlatabilirsiniz.

## <a name="await-tasks-efficiently"></a>Görevleri verimli bir şekilde await

Dizi `await` sonunda, yukarıdaki kod deyimlerini geliştirilmiş yöntemleri kullanılarak `Task` sınıfı. Bu API'leri biri <xref:System.Threading.Tasks.Task.WhenAll%2A>, döndüren bir <xref:System.Threading.Tasks.Task> tamamlanan kendi bağımsız değişken listesindeki tüm görevleri tamamladıktan sonra aşağıdaki kodda gösterildiği gibi:

```csharp
await Task.WhenAll(eggTask, baconTask, toastTask);
Console.WriteLine("eggs are ready");
Console.WriteLine("bacon is ready");
Console.WriteLine("toast is ready");
Console.WriteLine("Breakfast is ready!");
```

Başka bir seçenek kullanmaktır <xref:System.Threading.Tasks.Task.WhenAny%2A>, döndüren bir `Task<Task>` tamamlanan bağımsız değişkenlerinden biri tamamlar. Zaten bitmiş bilerek döndürülen göreve await. Aşağıdaki kod nasıl kullanabileceğinizi gösterir <xref:System.Threading.Tasks.Task.WhenAny%2A> tamamlayın ve ardından sonucunu işlemek için ilk görevi beklemek için. Tamamlanan görevin sonucu işlendikten sonra tamamlanmış bir görevin geçirilen görevler listesinden kaldırmak `WhenAny`.

[!code-csharp[AwaitAnyTask](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-final/Program.cs#AwaitAnyTask)]

Tüm bu değişiklikler, son sürümü sonra `Main` şu kod gibi görünür:

[!code-csharp[Final](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-final/Program.cs#Main)]

Bu son kod zaman uyumsuzdur. Daha doğru bir şekilde, bir kişinin bir kahvaltı nasıl cook yansıtır. Bu makalede ilk kod örneği önceki kodla karşılaştırın. Kod okumasını hala NET core eylemlerdir. Bu kod, bu makalenin başında bir kahvaltı yapmak için bu yönergeleri okuduğunuz aynı şekilde okuyabilir. Dil özellikleri için `async` ve `await` herkesin hale getirir bu yazılı yönergelere izlemek için çeviri sağlayın: oluşturabilir ve görevlerin tamamlanmasını beklerken engelleme gibi görevleri başlatın.
