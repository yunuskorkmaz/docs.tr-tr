---
title: Olaylara Giriş
description: .NET Core ve olayları bu genel bakış için dil tasarım hedeflerimiz olayları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 9f14954dd2e8aeacf3c5ae70a9e891ad11a6f0d7
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45509581"
---
# <a name="introduction-to-events"></a>Olaylara Giriş

[Önceki](delegates-patterns.md)

Olaylar, temsilciler gibi bir *geç bağlama* mekanizması. Aslında, olaylar, temsilciler için dil desteği oluşturulur.

Bir yol ('ilgilenen tüm sistem bileşenlerinde), bir yayın bir nesne için gerçekleşen olaylardır. Başka bir bileşen olaya abone olabilir ve bir olay oluşturulduğunda bildirilmesi.

Büyük olasılıkla programlama bazıları olayları kullandınız. Pek çok grafik sistemleri rapor kullanıcı etkileşimi bir olay modeline sahiptir. Bu olaylar, fare hareketini, düğme basma işlemlerine ve benzer etkileşimleri rapor. Bu en yaygın ancak açmamalı olayları kullanıldığı tek senaryo biridir.

Sınıfları için harekete Geçirilmemesi gereken olayları tanımlayabilirsiniz. Olaylar ile çalışmayla, olduğunda önemli bir husus, belirli bir olay için kaydedilen herhangi bir nesne olmayabilir. Kodunuzu böylece hiçbir dinleyicileri olduğunda olayları geçirmemesi yapılandırılmış yazmanız gerekir.

Bir olaya abone olma, iki nesne (olay kaynağı ve olay havuzu) arasında bir bağlantı oluşturur. Olay havuzu olayları artık ilgilenilmiyor olduğunda olay kaynağından abonelikten çıkma emin olmak gerekir.

## <a name="design-goals-for-event-support"></a>Olay desteği için tasarım hedefleri

Olaylar için dil tasarımını bu hedeflere hedefler.

İlk olarak, bir olay kaynağı ve olay havuzu arasında çok az eşleştirmeye etkinleştirin. Bu iki bileşenin aynı kuruluş tarafından yazılabilir değil ve hatta tamamen farklı zamanlamalarda güncelleştirilmemiş olabilir.

İkincisi, çok basit bir olaya abone olun ve bu aynı olayın aboneliğini kaldırmak için olmalıdır.

Ve son olarak, olay kaynakları birden çok etkinlik abonelerinden desteklemelidir. Bağlı hiçbir etkinlik abonelerinden sahip desteklemelidir.

Olaylar için hedef hedefler için temsilciler çok benzer olduğunu görebilirsiniz.
İşte bu olay dil desteği temsilci dil desteği de yerleşik olarak bulunur.

## <a name="language-support-for-events"></a>Olaylar için dil desteği

Olayları tanımlama ve abone veya olaylardan aboneliği sözdizimi temsilcileri söz diziminin bir uzantısıdır.

Kullandığınız bir olayı tanımlamak için `event` anahtar sözcüğü:

```csharp
public event EventHandler<FileListArgs> Progress;
```

Olay türü (`EventHandler<FileListArgs>` Bu örnekte) bir temsilci türü olmalıdır. Bir olay bildirirken izlemelidir kuralları vardır. Genellikle, olay temsilci türü bir void dönüş sahiptir.
Olay bildirimleri, fiil veya bir fiil ifade olmalıdır.
Olay gerçekleşen bir sorun bildirdiğinde geçmiş şimdiki (Bu örnekte olduğu gibi) kullanın. Şimdiki fiil kullanın (örneğin, `Closing`) gerçekleşmek üzere olan bir sorun bildirmek için. Genellikle, şimdiki kullanarak sınıfınız özelleştirme davranışı tür desteklediğini belirtir. En sık karşılaşılan senaryolardan biri, iptal desteklemektir. Örneğin, bir `Closing` olay kapatma işlemi, veya devam edip etmediğini belirtir bir bağımsız değişken içerebilir.  Olay bağımsız değişkenlerinin özelliklerini güncelleştirerek davranışını değiştirmek çağıranlar diğer senaryoları etkinleştirebilirsiniz. Bir algoritma sürer önerilen bir sonraki eylemi belirtmek için bir olay neden olabilir. Olay işleyicisi, olay bağımsız değişkenini özelliklerini değiştirerek farklı bir eylem zorunlu.

Olayı oluşturmak istediğinizde, temsilci çağırma söz dizimi kullanarak olay işleyicileri çağırın:

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

Üzerinde bölümünde açıklandığı gibi [Temsilciler](delegates-patterns.md),?
işleci, o olaya abone olduğunuzda olayı çalışmayın emin olmak kolaylaştırır.
 
Kullanarak bir olaya abone `+=` işleci:

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += onProgress;
```

İşleyicisi yöntemi genellikle 'On' olay adından önce gelen yukarıda da gösterildiği gibi önekidir.

Kullanarak abonelikten `-=` işleci:

```csharp
lister.Progress -= onProgress;
```

Olay işleyicisi temsil eden ifade için yerel bir değişken bildirildi olduğunu unutmayın. İşleyici unsubscribe kaldırır sağlar.
Bunun yerine, lambda ifadesinin gövdesinin kullandıysanız, hiçbir şey yapan hiçbir zaman eklenmiş bir işleyici kaldırmaya çalışıyorsunuz.

Sonraki makalede, tipik olay desenleri ve bu örnekte farklı çeşitlerini hakkında daha fazla bilgi edineceksiniz.

[Next](event-pattern.md)
