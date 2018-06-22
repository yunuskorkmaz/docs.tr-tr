---
title: İşleme ve .NET özel durumları atma
ms.date: 06/19/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET], exceptions
- exceptions [.NET], throwing
- exceptions [.NET]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a278940528966e32646a3551b4c133223de9746e
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298350"
---
# <a name="handling-and-throwing-exceptions-in-net"></a>İşleme ve .NET özel durumları atma

Uygulamaları tutarlı bir şekilde yürütme sırasında oluşan hataları ele kurabilmesi gerekir. .NET uygulamaları hataların Tekdüzen şekilde bildirmek için bir model sağlar: .NET işlemlerini özel durumları atma hatası belirtin.

## <a name="exceptions"></a>Özel Durumlar

Herhangi bir hata koşulu veya çalışan bir program tarafından karşılaşılan beklenmeyen davranışları bir özel durumdur. Kodunuzu veya (gibi paylaşılan bir kitaplık) çağıran kodu, kullanılamayan işletim sistem kaynakları, çalışma zamanı (doğrulanamayan kodu gibi) karşılaştığında beklenmeyen koşullar ve benzeri bir hata nedeniyle durumlar. Uygulamanızı bazı Bu koşullar, ancak diğer kurtarabilirsiniz. Çoğu uygulama özel durumları kurtarabilirsiniz rağmen çoğu çalışma zamanı özel durumları kurtaramazsınız.

.NET içinde öğesinden devralan bir nesne istisnadır <xref:System.Exception?displayProperty=nameWithType> sınıfı. Bir sorun oluştuğu bir alanından kod bir özel durum oluşur. Özel durum yığını uygulama, işleme veya program sonlandırır kadar geçirilir.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Özel durumlar geleneksel hata işleme yöntemlerini karşılaştırması

Geleneksel olarak, bir dil hata işleme modeli hataları algılama ve bunlar için işleyiciler bulma dil benzersiz şekilde veya işletim sistemi tarafından sağlanan hata işleme mekanizması dayanıyordu. Özel durum işleme .NET uygulayan yol aşağıdaki avantajları sağlar:

- Özel durum atma ve işleme .NET programlama dilleri için aynı şekilde çalışır.

- Özel durum işleme için belirli bir dili sözdizimi gerektirmez, ancak kendi sözdizimi tanımlamak her bir dilin verir.

- Özel işlem ve hatta makine sınırları içinde durum.

- Özel durum işleme kod program güvenilirliğini artırmak için uygulamaya eklenebilir.

Özel durumlar hata bildirimi, dönüş kodları gibi diğer yöntemleri avantaj sunar. Bir özel durum ve işlemek yok, çalışma zamanı uygulamanızı sona erdiğinden hataları gözden kaçan geçmez. Geçersiz değerler denetlemek için bir hata dönüş kodu için başarısız kod sonucunda sistemi aracılığıyla yayılmaya devam yok.

## <a name="common-exceptions"></a>Genel özel durumlar

Aşağıdaki tabloda ortak bazı özel durumlar ne bunlara neden olabilecek örnekleri ile listeler.

| Özel durum türü | Açıklama | Örnek |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | Tüm özel durumlar için temel sınıf. | Hiçbiri (Bu özel durumun türetilmiş bir sınıf kullanın). |
| <xref:System.IndexOutOfRangeException> | Çalışma zamanı tarafından yalnızca bir dizi yanlış sıralandığında oluşturulur. | Geçerli aralığın dışında bir dizi dizin oluşturma: <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | Çalışma zamanı tarafından yalnızca null bir nesne başvurulduğunda oluşturulur. | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | Geçersiz bir durumda olduğunda yöntemler tarafından oluşturulur. | Çağırma `Enumerator.MoveNext()` bir öğe temel alınan koleksiyonundan kaldırdıktan sonra. |
| <xref:System.ArgumentException> | Tüm bağımsız değişken özel durumlar için temel sınıf. | Hiçbiri (Bu özel durumun türetilmiş bir sınıf kullanın). |
| <xref:System.ArgumentNullException> | Bir bağımsız değişken boş olmasına izin verme yöntemler tarafından oluşturulur. | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | Bağımsız değişkenler aralıktan doğrulayın yöntemler tarafından oluşturulur. | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a>Ayrıca bkz.

[Özel Durum Sınıfı ve Özellikleri](exception-class-and-properties.md)  
[Nasıl yapılır: Özel Durumları Yakalamak için Try-Catch Bloğu Kullanma](how-to-use-the-try-catch-block-to-catch-exceptions.md)  
[Nasıl yapılır: Bir Catch Bloğunda Belirli Özel Durumları Kullanma](how-to-use-specific-exceptions-in-a-catch-block.md)  
[Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](how-to-explicitly-throw-exceptions.md)  
[Nasıl yapılır: Kullanıcı Tanımlı Özel Durumlar Oluşturma](how-to-create-user-defined-exceptions.md)  
[Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma](using-user-filtered-exception-handlers.md)  
[Nasıl yapılır: Finally Bloklarını Kullanma](how-to-use-finally-blocks.md)  
[COM Birlikte Çalışma Özel Durumlarını İşleme](handling-com-interop-exceptions.md)  
[Özel Durumlar için En İyi Yöntemler](best-practices-for-exceptions.md)  
[Her geliştirici bilmeniz hakkında özel durumlara çalışma zamanında gereken](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).
