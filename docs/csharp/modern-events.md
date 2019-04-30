---
title: Güncelleştirilmiş .NET Core olay deseni
description: Nasıl .NET Core olay deseni esneklik ile geriye dönük uyumluluk sağlar ve nasıl güvenli bir olay işleme ile zaman uyumsuz aboneleri uygulanacağını öğrenin.
ms.date: 06/20/2016
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: 5c7b9b4cb9bc22a73b865c45e225ce5c382380b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61652045"
---
# <a name="the-updated-net-core-event-pattern"></a>Güncelleştirilmiş .NET Core olay deseni

[Önceki](event-pattern.md)

Önceki makalede en yaygın olay desenleri açıklanmıştır. .NET core daha gevşek bir düzeni vardır. Bu sürümde `EventHandler<TEventArgs>` tanımı artık kısıtlaması vardır, `TEventArgs` bir sınıf nesnesinden türetilmesi gerekir `System.EventArgs`.

Bu, sizin için daha fazla esneklik sunan ve geriye dönük uyumludur. Esnekliği başlayalım. ' % S'sınıfı System.EventArgs bir yöntem sunar: `MemberwiseClone()`, nesnenin sığ bir kopya oluşturur.
Yöntemi herhangi bir sınıftan türetilen için işlevselliği uygulamak için yansıma kullanması gerektiğini `EventArgs`. Bu işlevsellik belirli bir türetilmiş sınıfta oluşturmak daha kolay olur. Etkili bir şekilde System.EventArgs türetme tasarımlarınızı sınırlar, ancak herhangi bir ek yararı sağlamaz bir kısıtlaması olduğu anlamına gelir.
Aslında, tanımlarını değiştirebilirsiniz `FileFoundArgs` ve `SearchDirectoryArgs` oldukları türetilmesi değil böylece `EventArgs`.
Program tamamen aynı çalışır.

Ayrıca değişebilir `SearchDirectoryArgs` bir daha fazla değişiklik yaparsanız, bir yapı için:

```csharp
internal struct SearchDirectoryArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs) : this()
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
```

Ek değişiklik parametresiz bir oluşturucu tüm alanları başlatır Oluşturucusu girmeden önce çağırmaktır. Ayrıca, kurallarına olmadan C# özellikleri, atanmış önce erişildiği rapor.

Değil değiştirmelisiniz `FileFoundArgs` yapı (değer türü) için sınıfından (başvuru türü). Olay bağımsız değişkenleri başvuruya göre iletilir iptal işlemek için bir protokol gerektiren olmasıdır. Aynı değişikliği yaptıysanız, dosya arama sınıfı hiçbir zaman herhangi bir olay aboneler tarafından yapılan değişiklikler mümkün. Her abone için yeni bir kopyasını yapısı kullanılacaktır ve bu kopyayı dosya arama nesne tarafından görülen olandan farklı bir kopyasını olacaktır.

Ardından, bu değişiklik nasıl geriye dönük olarak uyumlu olabilir düşünelim.
Kısıtlamanın kaldırılması, mevcut kodlar etkilemez. Var olan herhangi bir olay bağımsız değişken türü hala türetilen `System.EventArgs`.
Geriye dönük uyumluluk neden bunlar çalışmaya devam edecek öğesinden türetilen önemli nedenlerinden biri olan `System.EventArgs`. Var olan bir etkinlik abonelerinden Klasik desenin takip bir olaya abone olur.

Benzer mantığı, tüm izleme olay bağımsız değişkeni oluşturulan türü artık değil sahip herhangi bir varolan tüm aboneler çıkabilirsiniz. Öğesinden türetilen değil yeni olay türleri `System.EventArgs` Bu kod tabanlarında sonu olur.

## <a name="events-with-async-subscribers"></a>Zaman uyumsuz abonelere olayları

Bilgi edinmek için bir son deseni aşağıdakiler: Zaman uyumsuz kodu çağıran etkinlik abonelerinden doğru şekilde yazmak nasıl. Sınama üzerinde makalesinde açıklanan [async ve await](async.md). Zaman uyumsuz yöntemlerin dönüş türü void olabilir, ancak kesinlikle önerilmez. Olay abonesi kodunuz bir zaman uyumsuz yöntemini çağırdığında oluşturmak için seçim yok ancak sahip bir `async void` yöntemi. Olay işleyicisinin imzası gerektiriyor.

Kpı'lere bu kılavuz mutabakat sağlamak gerekir. Güvenli bir şekilde, oluşturmalısınız `async void` yöntemi. Desen uygulamak için gereken temel aşağıda verilmiştir:

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try 
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

İlk olarak, işleyiciyi zaman uyumsuz bir işleyici işaretlenmiş olduğuna dikkat edin. Kendine atanan temsilci türüne bir olay işleyicisi, void dönüş türüne sahip. Bu işleyici içinde gösterilen desenini izler ve zaman uyumsuz işleyici bağlamı dışında oluşturulması tüm özel durumlara izin vermeyecek anlamına gelir. Bir task döndürmüyor olduğundan, hata, hatalı durumuna girerek bildirebileceği görev yok. Zaman uyumsuz yöntem olduğundan, yöntemi yalnızca özel durumu atılamıyor. (Yöntemi çağrılırken, olduğundan yürütme devam etti `async`.) Fiili çalışma zamanı davranışı farklı farklı ortamlar için tanımlanır. İş parçacığı sonlandırabilir, program sonlandırabilir veya program belirsiz bir durumda bırakabilir. Bu iyi bir sonuç yok.

İşte bu nedenle kendi try bloğunda bekleme ifadesinin zaman uyumsuz görev için uzun olmamalıdır. Hatalı bir görev neden olmaz, hata oturum açabilirsiniz. Uygulamanızın içinden kurtaramazsınız bir hata olması durumunda, hızlı ve düzgün bir şekilde program çıkabilirsiniz

Önemli güncelleştirmeler .NET olay deseni olanlardır. Birlikte çalıştığınız kitaplıklar daha önceki sürümlerinde, birçok örneği görürsünüz. Ancak, en son desenleri de nelerdir anlamanız gerekir.

Bu serideki sonraki makalede kullanma arasında ayırt etmenize yardımcı olur. `delegates` ve `events` tasarımlarınızı içinde. Benzer kavramları olduklarını ve bu makalede programlar için en iyi karar vermenize yardımcı olur.

[Next](distinguish-delegates-events.md)
