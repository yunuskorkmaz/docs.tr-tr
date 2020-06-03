---
ms.openlocfilehash: 32030698c12de87daef5e1d8851a0f55ec36d688
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721110"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Pkcs8PrivateKeyInfo oluşturucusunda daha iyi bağımsız değişken doğrulaması

.NET Core 3,0 Preview 9 ' dan itibaren, `Pkcs8PrivateKeyInfo` Oluşturucu `algorithmParameters` parametreyi tek bir ber kodlamalı değer olarak doğrular.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 9 ' dan önce, [ `Pkcs8PrivateKeyInfo` Oluşturucu](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) `algorithmParameters` bağımsız değişkeni doğrulamadı.  Bu bağımsız değişken geçersiz bir değer temsil ettiğinde, Oluşturucu başarılı olur, ancak,, veya metotlarından herhangi birine yapılan bir çağrı <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> , <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> <xref:System.ArgumentException> kabul etmeyen bir bağımsız değişken ( `preEncodedValue` ) veya bir için bir çağrı oluşturur <xref:System.Security.Cryptography.CryptographicException> .

Preview 9 ' dan önce .NET Core 3,0 ile çalıştırırsanız aşağıdaki kod yalnızca yöntem çağrıldığında bir özel durum oluşturur <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> :

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

.NET Core 3,0 Preview 9 ' dan itibaren bağımsız değişken oluşturucuda onaylanır ve geçersiz bir değer, oluşturan yöntemi ile sonuçlanır <xref:System.Security.Cryptography.CryptographicException> . Bu değişiklik, özel durumu veri hatasının kaynağına yaklaştırır. Örnek:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Yalnızca geçerli `algorithmParameters` değerlerin sağlandığından veya `Pkcs8PrivateKeyInfo` hem hem de <xref:System.ArgumentException> <xref:System.Security.Cryptography.CryptographicException> özel durum işlemenin isteniyorsa Oluşturucu testine çağrı yapıldığından emin olun.

#### <a name="category"></a>Kategori

Şifreleme

#### <a name="affected-apis"></a>Etkilenen API’ler

- [Pkcs8PrivateKeyInfo Oluşturucusu](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
