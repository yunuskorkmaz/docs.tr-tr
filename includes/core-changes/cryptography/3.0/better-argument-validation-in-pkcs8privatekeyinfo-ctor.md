---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449236"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Pkcs8PrivateKeyInfo oluşturucu daha iyi argüman doğrulama

.NET Core 3.0 Preview 9 `Pkcs8PrivateKeyInfo` ile başlayarak, oluşturucu parametreyi `algorithmParameters` TEK BER kodlanmış değer olarak doğrular.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 3.0 Preview 9'dan önce, `algorithmParameters` [ `Pkcs8PrivateKeyInfo` oluşturucu](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) bağımsız değişkeni doğrulamadı.  Bu bağımsız değişken geçersiz bir değeri temsil ettiğinde, oluşturucu başarılı olur, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>ancak <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> , <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, , <xref:System.ArgumentException> veya yöntemlerden herhangi biri için bir çağrı kabul etmedikleri bir argüman için ya bir atar (`preEncodedValue`) ya da bir <xref:System.Security.Cryptography.CryptographicException>.

Önizleme 9'dan önce .NET Core 3.0 ile çalıştırılırsa, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> aşağıdaki kod yalnızca yöntem çağrıldığında bir özel durum oluşturur:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

.NET Core 3.0 Preview 9 ile başlayarak, bağımsız değişken oluşturucuda doğrulanır ve <xref:System.Security.Cryptography.CryptographicException>geçersiz bir değer bir . Bu değişiklik, özel durumu veri hatasıkaynağına yaklaştırıyor. Örnek:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 9

#### <a name="recommended-action"></a>Önerilen eylem

`algorithmParameters` Yalnızca geçerli değerlerin sağlandığından veya her `Pkcs8PrivateKeyInfo` ikisi <xref:System.ArgumentException> için de <xref:System.Security.Cryptography.CryptographicException> ve özel durum işleme isteniyorsa yapı testine çağrıda bulunulandan emin olun.

### <a name="category"></a>Kategori

Şifreleme

### <a name="affected-apis"></a>Etkilenen API’ler

- [Pkcs8PrivateKeyInfo yapıcı](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
