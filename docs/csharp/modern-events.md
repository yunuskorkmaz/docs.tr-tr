---
title: Güncelleştirilmiş .NET Core olay deseninin
description: .NET Core olay deseninin geriye dönük uyumlulukla esnekliği nasıl sağladığını ve zaman uyumsuz aboneler ile güvenli olay işlemenin nasıl uygulanacağını öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: a916a09b622f8df9bf99fafe52f35c706220f484
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039785"
---
# <a name="the-updated-net-core-event-pattern"></a>Güncelleştirilmiş .NET Core olay deseninin

[Öncekini](event-pattern.md)

Önceki makalede en sık kullanılan olay desenleri ele alınmıştır. .NET Core daha gevşek bir düzene sahiptir. Bu sürümde `EventHandler<TEventArgs>` tanımı artık `TEventArgs` `System.EventArgs`türetilmiş bir sınıf olması gereken kısıtlamaya sahip değildir.

Bu, sizin için esnekliği artırır ve geriye dönük olarak uyumludur. Esneklik ile başlayalım. System. EventArgs sınıfı bir yöntemi tanıtır: nesnenin basit bir kopyasını oluşturan `MemberwiseClone()`.
Bu yöntemin, `EventArgs`türetilmiş herhangi bir sınıf için işlevselliğini uygulamak üzere yansıma kullanması gerekir. Bu işlevsellik, belirli bir türetilmiş sınıfta oluşturmak daha kolaydır. Bu, System. EventArgs 'dan Türetmenin tasarımlarınızı sınırlayan bir kısıtlamadır, ancak başka bir avantaj sunmaz.
Aslında, `EventArgs`türetmemesi için `FileFoundArgs` ve `SearchDirectoryArgs` tanımlarını değiştirebilirsiniz.
Program tamamen aynı şekilde çalışır.

Ayrıca, daha fazla değişiklik yaparsanız `SearchDirectoryArgs` bir struct olarak değiştirebilirsiniz:

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

Ek değişiklik, tüm alanları Başlatan oluşturucuyu girmeden önce parametresiz oluşturucuyu çağırmaktır. Bu ek olmadan, kuralları C# atanmadan önce özelliklere erişilmekte olduğunu raporlayabilir.

Bir sınıftan (başvuru türü) `FileFoundArgs` bir struct (değer türü) olarak değiştirmemelisiniz. Bunun nedeni, Cancel işleme Protokolü olay bağımsız değişkenlerinin başvuruya göre geçirilmesini gerektirir. Aynı değişikliği yaptıysanız, dosya arama sınıfı hiçbir türlü olay abonesinin yaptığı değişiklikleri hiçbir şekilde gözlemlemez. Her abone için yapının yeni bir kopyası kullanılır ve bu kopya dosya arama nesnesi tarafından görülenden farklı bir kopya olacaktır.

Daha sonra, bu değişikliğin geriye dönük olarak nasıl uyumlu olduğunu ele alalım.
Kısıtlamanın kaldırılması var olan herhangi bir kodu etkilemez. Mevcut herhangi bir olay bağımsız değişken türü `System.EventArgs`türetmeye devam eder.
Geriye dönük uyumluluk, `System.EventArgs`türetmeye devam edebilecekleri önemli bir nedendir. Var olan tüm olay aboneleri, klasik kalıbı izleyen bir olaya abone olur.

Benzer mantığın ardından, artık oluşturulan herhangi bir olay bağımsız değişken türü herhangi bir mevcut kod tabanı içinde abone olamaz. `System.EventArgs` türetmeyen yeni olay türleri, bu kod temellerini bozmaz.

## <a name="events-with-async-subscribers"></a>Zaman uyumsuz aboneler içeren olaylar

Bilgi edinmek için bir son örüntüsünün olması gerekir: zaman uyumsuz kod çağıran olay abonelerini doğru şekilde yazma. Bu zorluk, [zaman uyumsuz ve await](async.md)makalesinde açıklanmaktadır. Zaman uyumsuz metotlar void dönüş türüne sahip olabilir, ancak bu kesinlikle önerilmez. Olay abone kodunuz zaman uyumsuz bir yöntem çağırdığında, hiçbir seçeneğiniz yoktur ancak bir `async void` yöntemi oluşturabilirsiniz. Olay işleyicisi imzası gereklidir.

Bu rakip kılavuzun mutabakatını yapmanız gerekir. Bir şekilde, güvenli bir `async void` yöntemi oluşturmanız gerekir. Uygulamanız gereken düzenin temelleri aşağıda verilmiştir:

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

İlk olarak, işleyicinin zaman uyumsuz işleyici olarak işaretlendiğinden emin olun. Bir olay işleyicisi temsilci türüne atanmakta olduğundan, void dönüş türüne sahip olur. Bu, işleyicide gösterilen kalıbı izlemeniz ve tüm özel durumların zaman uyumsuz işleyicinin içeriğinden çıkmasına izin vermeniz gerektiği anlamına gelir. Bir görev döndürmediğinden, hatayı hatalı duruma girerek bildiremeyen bir görev yoktur. Yöntemi zaman uyumsuz olduğundan, yöntem özel durumu oluşturmamalıdır. (Çağırma yöntemi `async`olduğundan yürütmeye devam etti.) Gerçek çalışma zamanı davranışı farklı ortamlar için farklı şekilde tanımlanır. İş parçacığını veya iş parçacığına sahip olan işlemi sonlandırabilir veya işlemi belirsiz bir durumda bırakabilir. Tüm bu olası sonuçlar yüksek oranda istenmeyen bir süreçlerdir.

Bu nedenle, kendi TRY bloğinizdeki zaman uyumsuz görev için Await ifadesini sarmalısınız. Hatalı bir göreve neden olursa, hatayı günlüğe kaydedebilirsiniz. Uygulamanızın kurtaramayacağı bir hata ise programdan hızlı ve sorunsuz bir şekilde çıkabilirsiniz

Bunlar, .NET olay deseninin önemli güncelleştirmeleridir. Üzerinde çalıştığınız kitaplıklarda daha önceki sürümlere ait birçok örnek görürsünüz. Ancak, en son desenlerin de ne olduğunu anlamanız gerekir.

Bu serinin sonraki makalesi tasarımlarınızın `delegates` ve `events` kullanımını ayırt etmenize yardımcı olur. Bunlar benzer kavramlardır ve bu makale programlarınıza en iyi kararı vermenize yardımcı olur.

[Next](distinguish-delegates-events.md)
