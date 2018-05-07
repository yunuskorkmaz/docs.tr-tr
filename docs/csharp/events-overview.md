---
title: Giriş olayları
description: .NET Core ve dil tasarım hedeflerimiz bu genel bakışta olayları için olay hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 2a2230ea5fba1b0cd5b13319677965e7a776549e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-events"></a>Giriş olayları

[Önceki](delegates-patterns.md)

Olaylardır, temsilciler gibi bir *geç bağlama* mekanizması. Aslında, olayları temsilciler dil desteğini üzerinde oluşturulmuştur.

(İçin sistemdeki tüm ilgilenen bileşenleri), bir yayın için bir nesne için bir yol gerçekleştirilmedi olaylardır. Herhangi bir bileşeni olaya abone olabilir ve bir olay oluşturulduğunda bildirilmesi.

Büyük olasılıkla programlama bazıları olayları kullandığınız. Çok sayıda grafik sistemleri rapor kullanıcı etkileşimi olay modeline sahiptir. Bu olaylar fare hareketini, düğme basma işlemlerine ve benzer etkileşimler raporlar. En yaygın ancak kesinlikle Hayır olayları kullanıldığı tek senaryo birini olmasıdır.

Sınıflar için oluşmalıdır olayları tanımlayabilirsiniz. Olaylarla çalışma, olduğunda bir önemli konu için belirli bir olay kayıtlı herhangi bir nesne olabilir. Kodunuzu olaylar hiçbir dinleyicileri zaman oluşturmaz böylece yapılandırılmış olan yazmanız gerekir.

Bir olaya abone (olay kaynağı ve Olay havuzunu) iki nesne arasındaki bir ilişki oluşturur. Olay iç havuz olayları artık ilgileniyor olduğunda olay kaynağından işlemleri emin olmanız gerekir.

## <a name="design-goals-for-event-support"></a>Olay desteği için tasarım hedefleri

Olaylar için dil tasarımı bu hedefleri hedefler.

İlk olarak, bir olay kaynağı ve bir olay havuz arasında çok az bağ etkinleştirin. Bu iki bileşenin aynı kuruluş tarafından yazılabilir değil ve farklı zamanlamada bile güncelleştirilebilir.

İkincisi, bir olaya abone olmak ve o aynı olayından aboneliği için çok basit olmalıdır.

Ve son olarak, olay kaynakları birden çok olay aboneye desteklemesi gerekir. Ekli olay abone olması desteklemelidir.

Hedefler olayları için temsilciler hedefleri için çok benzer olduğunu görebilirsiniz.
İşte bu nedenle olay dil desteği temsilci dil desteği de yerleşiktir.

## <a name="language-support-for-events"></a>Olaylar için dil desteği

Olayları tanımlama ve abone olma ya da olayların aboneliği için sözdizimi temsilciler sözdizimi uzantısıdır.

Kullandığınız bir olay tanımlamak için `event` anahtar sözcüğü:

```csharp
public event EventHandler<FileListArgs> Progress;
```

Olay türü (`EventHandler<FileListArgs>` Bu örnekte) bir temsilci türü olmalıdır. Bir olay bildirirken izlemelisiniz kuralları vardır. Genellikle, olay temsilci türü void dönüş sahiptir.
Olay bildirimleri bir fiil veya bir fiil deyimi olmalıdır.
Olay gerçekleştirilmedi bir şey bildirdiğinde geçmiş zamanın (Bu örnekte olduğu gibi) kullanın. Geçerli zamanın fiil kullanın (örneğin, `Closing`) çakışmasının benzer bildirilecek. Genellikle, geçerli zamanın kullanarak sınıfınız özelleştirme davranışı çeşit desteklediğini gösterir. En sık karşılaşılan senaryolardan biri, iptal desteklemektir. Örneğin, bir `Closing` olay kapatma işlemini, veya devam edip etmediğini gösteren bağımsız değişken içerebilir.  Diğer senaryolar olay bağımsız özelliklerini güncelleştirerek davranışını değiştirmek arayanlar sağlayabilir. Bir algoritma sürer önerilen bir sonraki eylem belirtmek için bir olay neden olabilir. Olay işleyicisi olay bağımsız değişkenini özelliklerini değiştirerek farklı bir eylem zorunlu kılabilir.

Olayı oluşturmak istediğinizde, temsilci çağırma sözdizimini kullanarak olay işleyicileri arayın:

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

Üzerinde bölümünde açıklandığı gibi [Temsilciler](delegates-patterns.md),?
işleci, bu olaya abone olduğunuzda olayı çalışmayın emin olmak kolaylaştırır.
 
Kullanarak bir olaya abone `+=` işleci:

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += OnProgress;
```

İşleyici genellikle önekini 'On' olay adından yukarıda gösterildiği gibi yöntemidir.

Kullanarak aboneliği `-=` işleci:

```csharp
lister.Progress -= onProgress;
```

Olay işleyicisini temsil eden ifade için yerel bir değişkeni bildirilen olduğunu dikkate almak önemlidir. İşleyici abonelikten kaldırır sağlar.
Bunun yerine, lambda ifadesi gövdesi kullandıysanız, hiçbir şey yapmaz, hiçbir zaman eklenmiş olup, bir işleyici kaldırmaya çalışıyorsunuz.

Sonraki makalede tipik olay desenleri ve bu örnek farklı çeşidi hakkında daha fazla bilgi edineceksiniz.

[Next](event-pattern.md)
