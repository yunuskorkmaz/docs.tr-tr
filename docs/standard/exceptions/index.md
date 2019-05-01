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
ms.openlocfilehash: a417e964c2f44c291892f9ddec6e32438fbff9a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945437"
---
# <a name="handling-and-throwing-exceptions-in-net"></a>İşleme ve .NET özel durumları atma

Uygulamaları tutarlı bir şekilde yürütme sırasında oluşan hataları işleyebilir olması gerekir. .NET uygulamaları hataların Tekdüzen bir şekilde bildirmek için bir model sağlar: .NET işlemlerini özel durumları atma tarafından hata belirtin.

## <a name="exceptions"></a>Özel Durumlar

Herhangi bir hata koşulu veya yürütülen bir program tarafından karşılaşılan beklenmeyen davranışı bir özel durumdur. Kodunuzu veya (gibi paylaşılan bir kitaplık) çağıran kod, kullanılamayan işletim sistem kaynakları, çalışma zamanı (doğrulanamayan kodu gibi) karşılaştığında beklenmeyen koşulları ve benzeri bir hata nedeniyle özel durumlar. Uygulamanız bazı bu koşulların, ancak diğerleri kurtarabilirsiniz. Çoğu uygulama özel durumlarından kurtulmak olsa da, birçok çalışma zamanı özel durumları kurtaramazsınız.

. NET'te, bir özel durum devralınan bir nesnedir <xref:System.Exception?displayProperty=nameWithType> sınıfı. Bir sorun oluştuğu bir alandan kod bir özel durum oluşturulur. Özel durum yığını uygulama, işleme veya program sona erer kadar geçirilir.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Özel durumlar ile geleneksel hata işleme yöntemleri

Geleneksel olarak, bir dil hata işleme modeli, benzersiz şekilde hataları algılama ve bunlar için işleyiciler bulma dil veya işletim sistemi tarafından sağlanan hata işleme mekanizması yararlandı. .NET özel durum işleme uygular. yol, aşağıdaki avantajları sağlar:

- Özel durum işleme ve atma .NET programlama dilleri için aynı şekilde çalışır.

- Özel durumları işlemek için herhangi bir dilin sözdizimi gerektirmez, ancak kendi sözdizimi tanımlamak her bir dilin izin verir.

- İşlem ve hatta makine sınırları içinde özel durumlar atılabilir.

- Özel durum işleme kodu program güvenilirliğini artırmak için bir uygulamaya eklenebilir.

Özel durumları hata bildirimin dönüş kodları gibi diğer yöntemleri avantaj sunar. Bir özel durum oluşturulur ve bu işlemez, çalışma zamanının uygulamanızı bittiğinden hataları gözden kaçan yapılmaz. Hata dönüş kodunu denetlemek için başarısız olan kod sonucu olarak sistem aracılığıyla yaymak geçersiz değer geçmeyin.

## <a name="common-exceptions"></a>Sık karşılaşılan özel durumlar

Aşağıdaki tabloda neler bunlara neden olabilecek örnekleri ile sık kullanılan bazı özel durumlar listeler.

| Özel durum türü | Açıklama | Örnek |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | Tüm özel durumları için temel sınıf. | Hiçbiri (Bu özel durumun türetilmiş bir sınıf kullanın). |
| <xref:System.IndexOutOfRangeException> | Yalnızca bir dizi yanlış sıralandığında çalışma zamanı tarafından oluşturulur. | Geçerli aralığın dışında bir dizi dizini oluşturma: <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | Çalışma zamanı tarafından yalnızca bir null Nesne başvurulduğunda oluşturulur. | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | Geçersiz bir durumda olduğunda yöntemlerle oluşturulur. | Çağırma `Enumerator.MoveNext()` bir öğe temel alınan koleksiyonundan kaldırdıktan sonra. |
| <xref:System.ArgumentException> | Tüm bağımsız değişken özel durumları için temel sınıf. | Hiçbiri (Bu özel durumun türetilmiş bir sınıf kullanın). |
| <xref:System.ArgumentNullException> | Bağımsız değişken null olması izin vermeyen yöntemleri tarafından oluşturulur. | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | Verili bir aralıktaki bağımsız değişkenlerini doğrulayın yöntemlerle oluşturulur. | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum Sınıfı ve Özellikleri](exception-class-and-properties.md)
- [Nasıl yapılır: Özel durumları yakalamak için Try-Catch bloğu kullanma](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [Nasıl yapılır: Bir Catch bloğunda belirli özel durumları kullanma](how-to-use-specific-exceptions-in-a-catch-block.md)
- [Nasıl yapılır: Açıkça özel durumlar oluşturma](how-to-explicitly-throw-exceptions.md)
- [Nasıl yapılır: Kullanıcı tanımlı özel durumlar oluşturma](how-to-create-user-defined-exceptions.md)
- [Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma](using-user-filtered-exception-handlers.md)
- [Nasıl yapılır: Finally bloklarını kullanma](how-to-use-finally-blocks.md)
- [COM Birlikte Çalışma Özel Durumlarını İşleme](handling-com-interop-exceptions.md)
- [Özel Durumlar için En İyi Yöntemler](best-practices-for-exceptions.md)
- [Her geliştiricinin bilmesi hakkında özel durumlar çalışma zamanında için gerekenler](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md)
