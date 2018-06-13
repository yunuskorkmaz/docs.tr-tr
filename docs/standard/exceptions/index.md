---
title: Özel Durumları İşleme ve Atma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET Framework], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET Framework], exceptions
- exceptions [.NET Framework], throwing
- exceptions [.NET Framework]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b71ffd9bfcfcb048f148ac1a3a418c03b9834ea2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575459"
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
| <xref:System.IndexOutOfRangeException> | <xref:System.Exception> | Çalışma zamanı tarafından yalnızca bir dizi yanlış sıralandığında oluşturulur. | Geçerli aralığın dışında bir dizi dizin oluşturma: `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <xref:System.Exception> | Çalışma zamanı tarafından yalnızca null bir nesne başvurulduğunda oluşturulur. | `object o = null; o.ToString();` |
| <xref:System.InvalidOperationException> | <xref:System.Exception> | Geçersiz bir durumda olduğunda yöntemler tarafından oluşturulur. | Çağırma `Enumerator.GetNext()` bir öğe temel alınan koleksiyonundan kaldırdıktan sonra. |
| <xref:System.ArgumentException> | <xref:System.Exception> | Tüm bağımsız değişken özel durumlar için temel sınıf. | Hiçbiri (Bu özel durumun türetilmiş bir sınıf kullanın). |
| <xref:System.ArgumentNullException> | <xref:System.Exception> | Bir bağımsız değişken boş olmasına izin verme yöntemler tarafından oluşturulur. | `String s = null; "Calculate".IndexOf (s);` |
| <xref:System.ArgumentOutOfRangeException> | <xref:System.Exception> | Bağımsız değişkenler aralıktan doğrulayın yöntemler tarafından oluşturulur. | `String s = "string"; s.Substring(s.Length+1);` |

## <a name="see-also"></a>Ayrıca Bkz.

* [Özel Durum Sınıfı ve Özellikleri](exception-class-and-properties.md)
* [Nasıl yapılır: Özel Durumları Yakalamak için Try-Catch Bloğu Kullanma](how-to-use-the-try-catch-block-to-catch-exceptions.md)
* [Nasıl yapılır: Bir Catch Bloğunda Belirli Özel Durumları Kullanma](how-to-use-specific-exceptions-in-a-catch-block.md)
* [Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](how-to-explicitly-throw-exceptions.md)
* [Nasıl yapılır: Kullanıcı Tanımlı Özel Durumlar Oluşturma](how-to-create-user-defined-exceptions.md)
* [Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma](using-user-filtered-exception-handlers.md)
* [Nasıl yapılır: Finally Bloklarını Kullanma](how-to-use-finally-blocks.md)
* [COM Birlikte Çalışma Özel Durumlarını İşleme](handling-com-interop-exceptions.md)
* [Özel Durumlar için En İyi Yöntemler](best-practices-for-exceptions.md)

Özel durumları .NET içinde nasıl çalıştığı hakkında daha fazla bilgi için bkz: [ne her geliştirme gereken bilmeniz hakkında özel durumlara çalışma zamanında](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).
