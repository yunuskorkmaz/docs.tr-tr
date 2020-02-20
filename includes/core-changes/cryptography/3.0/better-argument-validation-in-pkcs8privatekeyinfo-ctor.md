---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449236"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Pkcs8PrivateKeyInfo oluşturucusunda daha iyi bağımsız değişken doğrulaması

.NET Core 3,0 Preview 9 ' dan itibaren `Pkcs8PrivateKeyInfo` Oluşturucu `algorithmParameters` parametresini tek bir BER kodlamalı değer olarak doğrular.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 9 ' dan önce [`Pkcs8PrivateKeyInfo` oluşturucu](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) `algorithmParameters` bağımsız değişkenini doğrulamadı.  Bu bağımsız değişken geçersiz bir değer temsil ettiğinde, Oluşturucu başarılı olur, ancak <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>veya <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> yöntemlerinin herhangi birine yapılan bir çağrı, kabul etmeyen bir bağımsız değişken için <xref:System.ArgumentException> (`preEncodedValue`) veya bir <xref:System.Security.Cryptography.CryptographicException>oluşturur.

Preview 9 ' dan önce .NET Core 3,0 ile çalıştırırsanız aşağıdaki kod yalnızca <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> yöntemi çağrıldığında bir özel durum oluşturur:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

.NET Core 3,0 Preview 9 ' dan itibaren, bağımsız değişken oluşturucuda onaylanır ve geçersiz bir değer, <xref:System.Security.Cryptography.CryptographicException>oluşturan Yöntem sonucu oluşur. Bu değişiklik, özel durumu veri hatasının kaynağına yaklaştırır. Örnek:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Özel durum işleme isteniyorsa yalnızca geçerli `algorithmParameters` değerlerinin sağlandığından veya hem <xref:System.ArgumentException> hem de <xref:System.Security.Cryptography.CryptographicException> için `Pkcs8PrivateKeyInfo` Oluşturucu testine çağrı yapıldığından emin olun.

### <a name="category"></a>Kategori

Şifreleme

### <a name="affected-apis"></a>Etkilenen API’ler

- [Pkcs8PrivateKeyInfo Oluşturucusu](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
