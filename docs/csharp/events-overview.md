---
title: Olaylara Giriş
description: Bu genel bakışta olaylar için .NET Core ve dil tasarımı hedeflerimizin olayları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: b1fd2ebe2ae91b55c9179f280d8894f6b40ced9b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771912"
---
# <a name="introduction-to-events"></a>Olaylara Giriş

[Öncekini](delegates-patterns.md)

Olaylar, bir *geç bağlama* mekanizması gibi bir temsilcidir. Aslında, olaylar, temsilciler için dil desteği üzerine kurulmuştur.

Olaylar, bir şeyin meydana geldiği bir nesnenin (sistemdeki tüm ilgi bileşenlerine) bir yoludur. Başka herhangi bir bileşen olaya abone olabilir ve bir olay ortaya çıktığında bildirim alabilir.

Büyük olasılıkla bazı programlarınızdaki olayları kullandınız. Birçok grafik sisteminde kullanıcı etkileşimini raporlamak için bir olay modeli vardır. Bu olaylar, fare hareketini, düğme basışlarını ve benzer etkileşimleri rapor edecektir. Bu en yaygın bir deyişle, olayların kullanıldığı tek senaryo değildir.

Sınıflarınız için oluşturulması gereken olayları tanımlayabilirsiniz. Olaylarla çalışırken dikkat edilmesi gereken önemli bir nokta, belirli bir olay için kayıtlı herhangi bir nesne olmayabilir. Bir dinleyici yapılandırılmadığında olayları tetiklememeleri için kodunuzu yazmanız gerekir.

Bir olaya abone olmak Ayrıca iki nesne (olay kaynağı ve olay havuzu) arasında bir Ida oluşturur. Olay havuzunun artık olaylarla ilgilenmemesi durumunda olay kaynağından abone olmaması gerekir.

## <a name="design-goals-for-event-support"></a>Olay desteği için tasarım hedefleri

Olaylar için dil tasarımı bu hedefleri hedefler.

İlk olarak, bir olay kaynağı ve olay havuzu arasında çok az sayıda bağlantısı etkinleştirin. Bu iki bileşen aynı kuruluş tarafından yazılamaz ve tamamen farklı zamanlamalarda bile güncelleştirilemeyebilir.

İkinci olarak, bir olaya abone olmak ve aynı olaydan aboneliği kaldırmak çok basittir.

Son olarak, olay kaynakları birden çok olay abonesini desteklemelidir. Ayrıca, ekli olay abonesi olmadan da destek sağlamalıdır.

Olayların hedeflerinin temsilcilerle ilgili hedeflere çok benzediğinden emin olabilirsiniz.
Bu nedenle, olay dili desteğinin temsilci dili desteği üzerine kurulmuştur.

## <a name="language-support-for-events"></a>Olaylar için dil desteği

Olayları tanımlama ve olayları abone olma sözdizimi, temsilcilerin sözdizimi uzantısıdır.

Bir olayı tanımlamak için `event` anahtar sözcüğünü kullanırsınız:

```csharp
public event EventHandler<FileListArgs> Progress;
```

Olayın türü (Bu örnekteki`EventHandler<FileListArgs>`) bir temsilci türü olmalıdır. Bir olayı bildirirken izlemeniz gereken birçok kural vardır. Genellikle, olay temsilci türünün void dönüşü vardır.
Olay bildirimleri bir fiil veya bir fiil ifadesi olmalıdır.
Olay gerçekleşen bir şeyi raporladığında geçmiş zaman hali kullanın. Gerçekleşmeyen bir şeyi raporlamak için, mevcut bir zaman hali fiilini (örneğin, `Closing`) kullanın. Genellikle, var zaman hali kullanımı, sınıfınızın bazı özelleştirme davranışlarını desteklediğini gösterir. En yaygın senaryolardan biri iptali destekliyoruz. Örneğin, `Closing` bir olay, kapatma işleminin devam edip edemeyeceğini belirten bir bağımsız değişken içerebilir.  Diğer senaryolar, olay bağımsız değişkenlerinin özelliklerini güncelleştirerek çağıranların davranış değiştirmesine olanak sağlayabilir. Algoritmanın yapması önerilen sonraki eylemi belirten bir olay oluşturabilirsiniz. Olay işleyicisi, olay bağımsız değişkeninin özelliklerini değiştirerek farklı bir eylemi zorunlu kılabilir.

Olayı yükseltmek istediğinizde, temsilci çağırma sözdizimini kullanarak olay işleyicilerini çağırabilirsiniz:

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

[Temsilciler](delegates-patterns.md)hakkında bölümünde açıklandığı gibi,?.
işleci, bu olaya abone olmadığında olayı yapmayı denediğinizden emin olmanızı kolaylaştırır.
 
`+=` işlecini kullanarak bir olaya abone olursunuz:

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

Handler yöntemi genellikle yukarıda gösterildiği gibi ' on ' öneki ve olay adından gelir.

`-=` işlecini kullanarak aboneliğinizi kaldırabilirsiniz:

```csharp
fileLister.Progress -= onProgress;
```

Olay işleyicisini temsil eden ifade için yerel bir değişken bildirdiğim unutulmamalıdır. Bu sayede abonelik kaldırma, işleyiciyi kaldırır.
Bunun yerine, lambda ifadesinin gövdesini kullandıysanız, hiçbir şey iliştirilmemiş hiçbir şey olmayan bir işleyiciyi kaldırmaya çalışıyorsunuz.

Sonraki makalede, tipik olay desenleri ve bu örnekteki farklı Çeşitlemeler hakkında daha fazla bilgi edineceksiniz.

[Next](event-pattern.md)
