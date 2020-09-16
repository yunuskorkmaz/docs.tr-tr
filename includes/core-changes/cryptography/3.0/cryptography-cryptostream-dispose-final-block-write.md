---
ms.openlocfilehash: 6ffd4147a99a59d0a2e50d3f88279608e286aed1
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90680044"
---
### <a name="cryptostreamdispose-transforms-final-block-only-when-writing"></a>CryptoStream. Dispose, son bloğu yalnızca yazma sırasında dönüştürür

<xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=nameWithType>İşlemleri tamamlaması için kullanılan yöntemi, `CryptoStream` okurken artık son bloğu dönüştürmeyi denemeyebilir.

#### <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, bir kullanıcı modunda kullanırken tamamlanmamış bir okuma gerçekleştirdiyse <xref:System.Security.Cryptography.CryptoStream> <xref:System.Security.Cryptography.CryptoStreamMode.Read> , <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> Yöntem bir özel durum oluşturabilir (örneğin, doldurma ile AES kullanırken). Son blok dönüştürülürken, ancak veriler eksik olduğundan özel durum oluşturuldu.

.NET Core 3,0 ve sonraki sürümlerinde, <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> artık okuma sırasında son bloğu dönüştürmeyi denemeyecek ve bu da tamamlanmamış okumaların yapılmasına izin vermez.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, bir özel durum yakalamak zorunda kalmadan bir ağ işlemi iptal edildiğinde şifre akışından tamamlanmamış okuma işlemleri yapılmasını sağlar.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Çoğu uygulama bu değişiklikten etkilenmemelidir.

Uygulamanız tamamlanmamış bir okuma durumunda daha önce bir özel durum yakalandığında, bu `catch` bloğu silebilirsiniz.
Uygulamanız, karma senaryolarda son bloğunun dönüştürülmesini kullanıyorsa, tüm akışın atılmadan önce okunduğunuzdan emin olmanız gerekebilir.

#### <a name="category"></a>Kategori

Şifreleme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.CryptoStream.Dispose`

-->
