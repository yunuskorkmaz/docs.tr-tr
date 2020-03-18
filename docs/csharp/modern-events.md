---
title: Güncelleştirilmiş .NET Çekirdek Olay Deseni
description: .NET Core olay deseninin geriye dönük uyumlulukla esnekliği nasıl sağladığını ve async aboneleri ile güvenli olay işlemenin nasıl uygulanacağını öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: c8858158ede761db8a3002beb26e521880f77feb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170442"
---
# <a name="the-updated-net-core-event-pattern"></a>Güncelleştirilmiş .NET Çekirdek Olay Deseni

[Önceki](event-pattern.md)

Önceki makalede en yaygın olay desenleri tartışıldı. .NET Core daha rahat bir desene sahiptir. Bu sürümde, `EventHandler<TEventArgs>` tanım artık türetilmiş bir sınıf `TEventArgs` `System.EventArgs`olması gereken kısıtlamaya sahip değildir.

Bu sizin için esnekliği artırır ve geriye dönük uyumludur. Esneklikle başlayalım. Class System.EventArgs bir yöntem `MemberwiseClone()`sunar: , nesnenin sığ bir kopyasını oluşturur.
Bu yöntem, türetilen herhangi bir sınıf için `EventArgs`işlevselliğini uygulamak için yansıma kullanmanız gerekir. Bu işlevselliği belirli bir türemiş sınıfta oluşturmak daha kolaydır. Bu, System.EventArgs'dan türeyen bir kısıtlamanın tasarımlarınızı sınırlayan, ancak ek bir fayda sağlamadığı anlamına gelir.
Aslında, tanımlarını değiştirebilirsiniz `FileFoundArgs` ve `SearchDirectoryArgs` böylece onlar türetilmiştir `EventArgs`.
Program tam olarak aynı çalışacaktır.

Bir değişiklik daha `SearchDirectoryArgs` yaparsanız, yapıyı da değiştirebilirsiniz:

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

Ek değişiklik, tüm alanları başlarayan açime girmeden önce parametresiz oluşturucuyu çağırmaktır. Bu ek olmadan, C# kuralları, mülklere atanmadan önce erişildiğini bildirir.

Bir `FileFoundArgs` sınıftan (başvuru türü) bir yapıya (değer türü) değiştirmemelisiniz. Bunun nedeni, iptal etme protokolünün olay bağımsız değişkenlerinin başvuruyla geçirilmesini gerektirmesidir. Aynı değişikliği yaptıysanız, dosya arama sınıfı hiçbir olay abonesi tarafından yapılan değişiklikleri gözlemleyemedi. Yapının yeni bir kopyası her abone için kullanılır ve bu kopya dosya arama nesnesi tarafından görülenkopyadan farklı bir kopya olur.

Sonra, bu değişikliğin geriye doğru nasıl uyumlu olabileceğini düşünelim.
Kısıtlamanın kaldırılması varolan herhangi bir kodu etkilemez. Varolan tüm olay bağımsız değişken `System.EventArgs`türleri hala.
Geriye doğru uyumluluk, neden türetmeye devam `System.EventArgs`edecekleri önemli bir nedendir. Varolan etkinlik aboneleri, klasik deseni izleyen bir etkinliğe abone olacaktır.

Benzer mantığı izleyerek, şimdi oluşturulan herhangi bir olay bağımsız değişken türü varolan codebases herhangi bir abone olmaz. Türetilemeyen `System.EventArgs` yeni olay türleri bu kod tabanlarını bozmaz.

## <a name="events-with-async-subscribers"></a>Async aboneleri ile etkinlikler

Öğrenmeniz gereken son bir desen var: Async kodu arayan olay abonelerini nasıl doğru yazabilirsiniz. Meydan [async](async.md)üzerinde makalede açıklanan ve bekliyor . Async yöntemleri bir boşluk dönüş türü olabilir, ancak bu şiddetle önerilmez. Olay abone kodunuz bir async yöntemi aradığında, bir `async void` yöntem oluşturmaktan başka seçeneğiniz yoktur. Olay işleyiciimzası bunu gerektirir.

Bu karşıt rehberliği uzlaştırmanız gerekiyor. Her nasılsa, `async void` güvenli bir yöntem oluşturmanız gerekir. Uygulamanız gereken örüntünün temelleri aşağıda verilmiştir:

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

İlk olarak, işleyicinin bir async işleyicisi olarak işaretlendiğini unutmayın. Olay işleyicisi temsilci türüne atandığından, geçersiz bir dönüş türüne sahip olacaktır. Bu, işleyicide gösterilen deseni izlemeniz ve özel durumların async işleyicisinin bağlamından atılmasına izin vermemeniz gerektiği anlamına gelir. Bir görevi döndürmediği için, hatalı durumu girerek hatayı bildirebilecek bir görev yoktur. Yöntem async olduğundan, yöntem sadece özel durum atamaz. (Arama yöntemi yürütmeye devam `async`etti çünkü öyle.) Gerçek çalışma zamanı davranışı farklı ortamlar için farklı tanımlanır. İş parçacığı veya iş parçacığı sahibi işlem sona erdirebilir veya belirsiz bir durumda işlem bırakabilirsiniz. Tüm bu potansiyel sonuçlar son derece istenmeyen vardır.

Bu nedenle, async Task için bekleme deyimini kendi deneme bloğunuzda tamamlamanız gerekir. Hatalı bir göreve neden olursa, hatayı günlüğe kaydedebilirsiniz. Uygulamanızın kurtaramadığı bir hataysa, programdan hızlı ve zarif bir şekilde çıkabilirsiniz

Bunlar .NET olay deseninin ana güncelleştirmeleridir. Birlikte çalıştığınız kitaplıklarda önceki sürümlerden birçok örnek görürsünüz. Ancak, en son desenlerde ne olduğunu da anlamalısınız.

Bu serinin bir sonraki makalesi, `delegates` `events` tasarımlarınızı kullanmak la ayırt etmek arasında ayrım yaptığınızda yardımcı olur. Bunlar benzer kavramlardır ve bu makale, programlarınız için en iyi kararı vermenize yardımcı olacaktır.

[Sonraki](distinguish-delegates-events.md)
