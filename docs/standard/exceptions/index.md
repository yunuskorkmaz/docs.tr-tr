---
title: .NET'te özel durumları işleme ve atma
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
ms.openlocfilehash: 8e78b2a8d7a815637e143eeb88bcfb51ded33771
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75741349"
---
# <a name="handling-and-throwing-exceptions-in-net"></a>.NET'te özel durumları işleme ve atma

Uygulamalar yürütme sırasında oluşan hataları tutarlı bir şekilde işleyebilmelidir. .NET, uygulamaları tek tip bir şekilde bildirmek için bir model sağlar: .NET işlemleri özel durumlar atarak başarısızlığı gösterir.

## <a name="exceptions"></a>Özel durumlar

Özel durum, yürütme programı tarafından karşılaşılan herhangi bir hata koşulu veya beklenmeyen davranıştır. Özel durumlar, kodunuzdaki bir hata dan veya (paylaşılan kitaplık gibi), kullanılamayan işletim sistemi kaynakları, çalışma zamanının karşılaştığı beklenmeyen koşullar (doğrulanamayan kod gibi) vb. olarak adlandırdığınız koddaki bir hata nedeniyle atılabilir. Uygulamanız bu koşullardan bazılarını kurtarabilir, ancak diğerlerinden kurtaramaz. Çoğu uygulama özel durumlarından kurtarabilirsiniz, ancak çoğu çalışma zamanı özel durumlarını kurtaramazsınız.

.NET'te özel <xref:System.Exception?displayProperty=nameWithType> durum, sınıftan devralan bir nesnedir. Bir özel durum, bir sorunun oluştuğu bir kod alanından atılır. Özel durum, uygulama işlenine veya program sonlandırına kadar yığına aktarılır.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Özel durumlar ve geleneksel hata işleme yöntemleri

Geleneksel olarak, bir dilin hata işleme modeli, dilin hataları algılama ve bunlar için işleyicileri bulma benzersiz bir şekilde veya işletim sistemi tarafından sağlanan hata işleme mekanizması dayanıyordu. .NET'in özel durum işlemeyi uygulama şekli aşağıdaki avantajları sağlar:

- Özel durum atma ve işleme .NET programlama dilleri için aynı çalışır.

- Özel durumları işlemek için belirli bir dil sözdizimi gerektirmez, ancak her dilin kendi sözdizimini tanımlamasına izin verir.

- Özel durumlar proses ve hatta makine sınırları arasında atılabilir.

- Program güvenilirliğini artırmak için bir uygulamaya özel durum işleme kodu eklenebilir.

Özel durumlar, iade kodları gibi diğer hata bildirim yöntemlerine göre avantajlar sunar. Bir özel durum atılırsa ve bunu işlemezseniz, çalışma zamanı uygulamanızı sonlandırdığından, hatalar fark edilmez. Geçersiz değerler, hata iade kodunu denetlemede başarısız olan bir kod sonucunda sistem de yayılmaya devam etmez.

## <a name="common-exceptions"></a>Sık karşılaşılan özel durumlar

Aşağıdaki tabloda, bunlara neyin neden olabileceğine dair örnekleriçeren bazı yaygın özel durumlar listelenebilmektedir.

| Özel durum türü | Açıklama | Örnek |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | Tüm özel durumlar için taban sınıf. | Yok (bu özel durum türetilmiş bir sınıf kullanın). |
| <xref:System.IndexOutOfRangeException> | Yalnızca bir dizi yanlış dizieklendiğinde çalışma zamanı tarafından atılır. | Bir diziyi geçerli aralığının dışında dizidizileme: <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | Yalnızca null nesne başvurulduğunda çalışma zamanı tarafından atılır. | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | Geçersiz bir durumdayken yöntemlerle atılır. | Bir `Enumerator.MoveNext()` öğeyi temel koleksiyondan kaldırdıktan sonra arama. |
| <xref:System.ArgumentException> | Tüm bağımsız değişken özel durumları için taban sınıf. | Yok (bu özel durum türetilmiş bir sınıf kullanın). |
| <xref:System.ArgumentNullException> | Bir bağımsız değişkenin null olmasını izin vermez yöntemler tarafından atılır. | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | Bağımsız değişkenlerin belirli bir aralıkta olduğunu doğrulayan yöntemlertarafından atılır. | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumu Sınıfı ve Özellikleri](exception-class-and-properties.md)
- [Nasıl yapılır: Özel Durumları Yakalamak için Try-Catch Bloğu Kullanma](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [Nasıl yapılır: Bir Catch Bloğunda Belirli Özel Durumları Kullanma](how-to-use-specific-exceptions-in-a-catch-block.md)
- [Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](how-to-explicitly-throw-exceptions.md)
- [Nasıl yapılır: Kullanıcı Tanımlı Özel Durumlar Oluşturma](how-to-create-user-defined-exceptions.md)
- [Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma](using-user-filtered-exception-handlers.md)
- [Nasıl yapılır: Finally Bloklarını Kullanma](how-to-use-finally-blocks.md)
- [COM Birlikte Çalışması Özel Durumlarını İşleme](handling-com-interop-exceptions.md)
- [Özel Durumlar için En İyi Yöntemler](best-practices-for-exceptions.md)
- [Her Dev'in Çalışma ZamanındaKi İstisnalar Hakkında Bilmesi Gerekenler](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/exceptions.md)
