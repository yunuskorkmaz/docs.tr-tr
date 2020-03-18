---
title: Olaylara giriş
description: Bu genel bakışta .NET Core'daki olaylar ve etkinlikler için dil tasarımı hedeflerimiz hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 4e660f85eecfd5668919baf21a0d26f858faf5a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146120"
---
# <a name="introduction-to-events"></a>Olaylara giriş

[Önceki](delegates-patterns.md)

Olaylar, delegeler *gibi, geç bağlama* mekanizmasıdır. Aslında, olaylar delegeler için dil desteği üzerine inşa edilmiştir.

Olaylar, bir nesnenin bir şey olduğunu (sistemdeki tüm ilgili bileşenlere) yayınlamasının bir yoludur. Başka bir bileşen olaya abone olabilir ve bir olay yükseltildiğinde bilgilendirilebilir.

Muhtemelen bazı programlarınızda olayları kullandınız. Birçok grafik sistemi, kullanıcı etkileşimini bildirmek için bir olay modeline sahiptir. Bu olaylar fare hareketini, düğme tuşlarını ve benzer etkileşimleri bildirir. Bu en yaygın, ama kesinlikle olayların kullanıldığı tek senaryo değil.

Sınıflarınız için yükseltilmesi gereken olayları tanımlayabilirsiniz. Olaylarla çalışırken göz önünde bulundurulması gereken önemli noktalardan biri, belirli bir olay için kayıtlı herhangi bir nesne nin olmamasıdır. Hiçbir dinleyici yapılandırılınca olayları yükseltmemesi için kodunuzu yazmanız gerekir.

Bir olaya abone olmak da iki nesne (olay kaynağı ve olay batması) arasında bir bağlantı oluşturur. Olaylarla artık ilgilenmediğinde olayın etkinlik kaynağından aboneliğini kaldırdığından emin olmanız gerekir.

## <a name="design-goals-for-event-support"></a>Etkinlik desteği için tasarım hedefleri

Etkinlikler için dil tasarımı şu hedefleri hedefler:

- Olay kaynağı ile olay lavabosu arasında çok az bağlantı olmasını etkinleştirin. Bu iki bileşen aynı kuruluş tarafından yazılmayabilir ve hatta tamamen farklı zamanlamalarda güncelleştirilebilir.

- Bir etkinliğe abone olmak ve aynı etkinlikten aboneliğinizi iptal etmek çok basit olmalıdır.

- Olay kaynakları birden çok olay abonelerini desteklemelidir. Ayrıca hiçbir olay aboneleri ekli olan destek olmalıdır.

Etkinliklerin hedeflerinin delegelerin hedeflerine çok benzediğini görebilirsiniz.
Bu nedenle etkinlik dili desteği temsilci dil desteği üzerine kuruludur.

## <a name="language-support-for-events"></a>Etkinlikler için dil desteği

Olayları tanımlamak ve olaylardan abone olmak veya aboneliğini bozmak için sözdizimi, temsilciler için sözdiziminin bir uzantısıdır.

Bir olayı tanımlamak için `event` anahtar kelimeyi kullanın:

```csharp
public event EventHandler<FileListArgs> Progress;
```

Olayın türü (bu`EventHandler<FileListArgs>` örnekte) bir temsilci türü olmalıdır. Bir olayı bildirirken izlemeniz gereken birkaç kural vardır. Genellikle, olay temsilcisi türü geçersiz bir dönüş vardır.
Olay bildirimleri bir fiil veya fiil tümceciği olmalıdır.
Olay, olan bir şeyi bildirdiğinde geçmiş zaman'ı kullanın. Olmak üzere olan bir şeyi `Closing`bildirmek için şimdiki zaman fiilini (örneğin,) kullanın. Genellikle, şimdiki zaman kullanarak sınıf özelleştirme davranışı çeşit desteklediğini gösterir. En yaygın senaryolardan biri iptali desteklemektir. Örneğin, bir `Closing` olay, yakın işlemin devam edip etmeyeceğini belirten bir bağımsız değişken içerebilir.  Diğer senaryolar, arayanların olay bağımsız değişkenlerinin özelliklerini güncelleştirerek davranışı değiştirmesini sağlayabilir. Bir algoritmanın yapacağı önerilen sonraki eylemi belirtmek için bir olay yükseltebilirsiniz. Olay işleyicisi olay bağımsız değişkeninin özelliklerini değiştirerek farklı bir eylem görevden alabilir.

Olayı yükseltmek istediğinizde, temsilci çağırma sözdizimini kullanarak olay işleyicilerini çağırırsınız:

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

[Delegeler](delegates-patterns.md)bölümünde tartışıldığı gibi , ?.
işleci, bu etkinliğe abone olmadığında olayı yükseltmeye çalışmadığınızdan emin olmayı kolaylaştırır.

İşletici kullanarak bir `+=` etkinliğe abone olabilirsiniz:

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

Işleyici yöntemi genellikle yukarıda gösterildiği gibi olay adı ardından 'Açık' öneki vardır.

İşleç kullanarak `-=` aboneliğinizi iptal elabilirsiniz:

```csharp
fileLister.Progress -= onProgress;
```

Olay işleyicisini temsil eden ifade için yerel bir değişken ilân ettiğimi belirtmek önemlidir. Bu, aboneliği iptal etme işleyicisini kaldırır.
Bunun yerine, lambda ifadesinin gövdesini kullandıysanız, hiç eklenmiş olmayan ve hiçbir şey yapmayan bir işleyiciyi kaldırmaya çalışıyorsunuz.

Sonraki makalede, tipik olay desenleri ve bu örnekte farklı varyasyonlar hakkında daha fazla bilgi edineceksiniz.

[Sonraki](event-pattern.md)
