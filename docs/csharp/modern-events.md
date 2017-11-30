---
title: "Güncelleştirilmiş .NET Core olay düzeni"
description: "Nasıl .NET Core olay deseni esnekliği geriye dönük uyumluluk sağlar ve zaman uyumsuz aboneleri ile güvenli olay işleme uygulama öğrenin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: cf69cbe0a7adbd274d1cb9e9544dda77d9fa1740
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="the-updated-net-core-event-pattern"></a>Güncelleştirilmiş .NET Core olay düzeni

[Önceki](event-pattern.md)

Önceki makaleyi en yaygın olay desenleri açıklanmıştır. .NET core daha esnek bir deseni vardır. Bu sürümde `EventHandler<TEventArgs>` tanımı artık kısıtlaması var, `TEventArgs` bir sınıfın türetildiği gerekir `System.EventArgs`.

Bu sizin için esnekliğini artırır ve geriye dönük olarak uyumludur. Esnekliği başlayalım. System.EventArgs sınıfı bir yöntem sunar: `MemberwiseClone()`, nesne basit bir kopyasını oluşturur.
Herhangi bir sınıfın türetildiği için işlevselliği uygulamak için yöntemi yansıma kullanmalıdır `EventArgs`. Bu işlevselliği, belirli bir türetilmiş sınıfta oluşturmak kolaydır. Etkili bir şekilde System.EventArgs türetme sizin tasarımlar sınırlar, ancak ek bir avantaja sağlamaz bir kısıtlaması olduğu anlamına gelir.
Aslında, değişiklikler tanımlarını `FileFoundArgs` ve `SearchDirectoryArgs` böylece bunlar öğesinden türetilen değil `EventArgs`.
Program tam olarak aynı çalışır.

Aynı zamanda değişebilir `SearchDirectoryArgs` ayrıca bir daha fazla değişiklik yaparsanız, bir yapı için:

```csharp  
internal struct SearchDirectoryArgs  
{  
    internal string CurrentSearchDirectory { get; }  
    internal int TotalDirs { get; }  
    internal int CompletedDirs { get; }  
    
    internal SearchDirectoryArgs(string dir, int totalDirs, 
        int completedDirs) : this()  
    {  
        CurrentSearchDirectory = dir;  
        TotalDirs = totalDirs;  
        CompletedDirs = completedDirs;  
    }  
}  
```   

Ek değişiklik varsayılan oluşturucu tüm alanları başlatır Oluşturucusu girmeden önce çağırmaktır. Bu ayrıca, C# kuralları, atanmış önce özellikleri Erişilmekte olduğunu raporlar.

Değil değiştirmelisiniz `FileFoundArgs` yapısı (değer türü) için bir sınıftan (başvuru türü). Olay bağımsız değişkenleri başvuruya göre geçirilir iptal işlemek için protokol gerektirir olmasıdır. Aynı değişiklik yaptıysanız, dosya arama sınıfı hiçbir zaman herhangi bir olay aboneler tarafından yapılan değişiklikler girdiğini. Yapısının yeni bir kopya her abone için kullanılır ve bu kopyayı dosya arama nesne tarafından görülen olandan farklı bir kopyasını olacaktır.

Ardından, şimdi bu değişiklik nasıl geriye dönük olarak uyumlu olabilir göz önünde bulundurun.
Kısıtlama kaldırılmasını herhangi bir varolan kod etkilemez. Tüm mevcut olay bağımsız değişken türleri hala türetilen `System.EventArgs`.
Geriye dönük uyumluluk neden bunlar devam öğesinden türetilen bir ana nedeni `System.EventArgs`. Mevcut tüm olay aboneler Klasik düzeni izlenen bir olay abonelere olacaktır.

Benzer mantığı herhangi aşağıdaki oluşturulan türü artık sahip tüm mevcut olan tüm abonelerin olay bağımsız değişken olarak kullanılabilecek kod temeli. Öğesinden türetilen değil yeni olay türleri `System.EventArgs` olanlar olarak kullanılabilecek kod temeli sonu olur.

## <a name="events-with-async-subscribers"></a>Zaman uyumsuz aboneleri olan olaylar

Bilgi edinmek için bir son deseni vardır: zaman uyumsuz kodu çağırma olay aboneleri doğru yazma. Sınama üzerinde makalesinde açıklanan [async ve await](async.md). Zaman uyumsuz yöntemleri geçersiz bir dönüş türüne sahip olabilir, ancak bu kesinlikle önerilmez. Olay abone kodunuzu bir zaman uyumsuz yöntem çağırdığında oluşturmak için choice yok ancak sahip bir `async void` yöntemi. Olay işleyici imzası gerektiriyor.

Bu rakip kılavuz karşılaştırmanız gerekir. Güvenli şekilde, oluşturmalısınız `async void` yöntemi. Aşağıda, uygulamanız gereken desen ile ilgili temel bilgiler verilmiştir:

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

İlk olarak, işleyiciyi zaman uyumsuz işleyici olarak işaretlenmiş dikkat edin. Atanmış olduğu için olay işleyicisi için temsilci türüne, geçersiz bir dönüş türüne sahip olur. İşleyicisinde gösterilen düzeni izleyin ve zaman uyumsuz işleyici bağlamı dışında durum tüm özel durumlara izin vermeyecek anlamına gelir. Bir görev döndürmediğinden hata hatalı durum girerek bildirebileceği görev yok. Zaman uyumsuz yöntem olduğu için yöntemi yalnızca özel durumu atılamıyor. (Çünkü arama yöntemi yürütme devam etti `async`.) Gerçek çalışma zamanı davranışı farklı farklı ortamlar için tanımlanır. İş parçacığı sonlandırabilir, program sonlandırabilir veya program belirlenmemiş bir durumda bırakabilir. Bu iyi sonuç yok.

İşte bu nedenle bekleme deyim zaman uyumsuz görev için kendi try bloğunda kaydırılacağını. Hatalı bir görev neden, hata oturum açabilirsiniz. Uygulamanızı kurtarma gerçekleştiremezsiniz bir hata olması durumunda hızla ve dikkatlice program çıkabilirsiniz

.NET olay deseni önemli güncelleştirmeler olanlardır. İle çalışma kitaplıkları önceki sürümlerde birçok örnekleri görürsünüz. Ancak, en son desenleri de nelerdir anlamanız gerekir.

Bu serideki sonraki makalede kullanma arasında ayrım yardımcı olan `delegates` ve `events` sizin tasarımlar içinde. Benzer kavram olan ve bu makalede programlarınız için en iyi karar vermenize yardımcı olur.

[Sonraki](distinguish-delegates-events.md)
