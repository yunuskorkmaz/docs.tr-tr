---
title: "Özel Durumları İşleme ve Atma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET Framework], exceptions
- exceptions [.NET Framework], throwing
- exceptions [.NET Framework]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b064dc39f5807b154a1529eebe17493ae84981cf
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2017
---
# <a name="handling-and-throwing-exceptions-in-net"></a>İşleme ve .NET özel durumları atma

Uygulamaları tutarlı bir şekilde yürütme sırasında oluşan hataları ele kurabilmesi gerekir. .NET uygulamaları hataların Tekdüzen şekilde bildirmek için bir model sağlar: .NET işlemlerini özel durumları atma hatası belirtin.

## <a name="exceptions"></a>Özel Durumlar

Herhangi bir hata koşulu veya çalışan bir program tarafından karşılaşılan beklenmeyen davranışları bir özel durumdur. Kodunuzu veya (gibi paylaşılan bir kitaplık) çağıran kodu, kullanılamayan işletim sistem kaynakları, çalışma zamanı (doğrulanamayan kodu gibi) karşılaştığında beklenmeyen koşullar ve benzeri bir hata nedeniyle durumlar. Uygulamanızı bazı Bu koşullar, ancak diğer kurtarabilirsiniz. Çoğu uygulama özel durumları kurtarabilirsiniz rağmen çoğu çalışma zamanı özel durumları kurtaramazsınız.

.NET içinde öğesinden devralan bir nesne istisnadır <xref:System.Exception?displayProperty=nameWithType> sınıfı. Bir sorun oluştuğu bir alanından kod bir özel durum oluşur. Özel durum yığını uygulama, işleme veya program sonlandırır kadar geçirilir.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Özel durumlar geleneksel hata işleme yöntemlerini karşılaştırması

Geleneksel olarak, bir dil hata işleme modeli hataları algılama ve bunlar için işleyiciler bulma dil benzersiz şekilde veya işletim sistemi tarafından sağlanan hata işleme mekanizması dayanıyordu. Özel durum işleme .NET uygulayan yol aşağıdaki avantajları sağlar:

- Özel durum atma ve işleme .NET programlama dilleri için aynı şekilde çalışır.

- Belirli bir dili sözdizimi özel durumları işlemek için gerekli değildir, ancak kendi sözdizimi tanımlamak her bir dilin verir.

- Özel işlem ve hatta makine sınırları içinde durum.

- Özel durum işleme kod program güvenilirliğini artırmak için uygulamaya eklenebilir.

Özel durumlar hata bildirimi, dönüş kodları gibi diğer yöntemleri avantaj sunar. Bir özel durum ve işlemek yok, çalışma zamanı uygulamanızı sona erdiğinden hataları gözden kaçan geçmemektedir. Geçersiz değerler denetlemek için bir hata dönüş kodu için başarısız kod sonucunda sistemi aracılığıyla yaymak devam etmeyin. 

## <a name="common-exceptions"></a>Genel özel durumlar

Aşağıdaki tabloda ortak bazı özel durumlar ne bunlara neden olabilecek örnekleri ile listeler.

| Özel durum türü | Temel tür | Açıklama | Örnek |
| -------------- | --------- | ----------- | ------- |
| <xref:System.Exception> | <xref:System.Object> | Tüm özel durumlar için temel sınıf. | Hiçbiri (Bu özel durumun türetilmiş bir sınıf kullanın). |
| <xref:System.IndexOutOfRangeException> | <xref:System.Exception> | Çalışma zamanı tarafından yalnızca bir dizi yanlış sıralandığında oluşturulur. | Geçerli aralığın dışında bir dizi dizin oluşturma:`arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <xref:System.Exception> | Çalışma zamanı tarafından yalnızca null bir nesne başvurulduğunda oluşturulur. | `object o = null; o.ToString();` |
| <xref:System.InvalidOperationException> | <xref:System.Exception> | Geçersiz bir durumda olduğunda yöntemler tarafından oluşturulur. | Çağırma `Enumerator.GetNext()` bir öğe temel alınan koleksiyonundan kaldırdıktan sonra. |
| <xref:System.ArgumentException> | <xref:System.Exception> | Tüm bağımsız değişken özel durumlar için temel sınıf. | Hiçbiri (Bu özel durumun türetilmiş bir sınıf kullanın). |
| <xref:System.ArgumentNullException> | <xref:System.Exception> | Bir bağımsız değişken boş olmasına izin verme yöntemler tarafından oluşturulur. | `String s = null; "Calculate".IndexOf (s);` |
| <xref:System.ArgumentOutOfRangeException> | <xref:System.Exception> | Bağımsız değişkenler aralıktan doğrulayın yöntemler tarafından oluşturulur. | `String s = "string"; s.Substring(s.Length+1);` |

## <a name="see-also"></a>Ayrıca Bkz.

* [Özel durum sınıfı ve özellikleri](exception-class-and-properties.md)
* [Nasıl yapılır: özel durumları yakalamak için Try-Catch bloğu kullanın](how-to-use-the-try-catch-block-to-catch-exceptions.md)
* [Nasıl yapılır: bir Catch bloğunda belirli özel durumların kullanın](how-to-use-specific-exceptions-in-a-catch-block.md)
* [Nasıl yapılır: açıkça özel durumlar oluşturma](how-to-explicitly-throw-exceptions.md)
* [Nasıl yapılır: kullanıcı tanımlı özel durumlar oluşturma](how-to-create-user-defined-exceptions.md)
* [Kullanıcı tarafından filtrelenmiş özel durum işleyicilerini kullanma](using-user-filtered-exception-handlers.md)
* [Nasıl yapılır: Finally bloklarını kullanma](how-to-use-finally-blocks.md)
* [COM birlikte çalışma özel durumları işleme](handling-com-interop-exceptions.md)
* [Özel durumlar için en iyi yöntemler](best-practices-for-exceptions.md)

Özel durumları .NET içinde nasıl çalıştığı hakkında daha fazla bilgi için bkz: [ne her geliştirme gereken bilmeniz hakkında özel durumlara çalışma zamanında](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).
