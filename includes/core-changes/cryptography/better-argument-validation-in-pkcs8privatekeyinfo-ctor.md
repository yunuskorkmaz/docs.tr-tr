---
ms.openlocfilehash: f72a9f60d0adcace2df6f1761940f8d8cd33d3af
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119291"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Pkcs8PrivateKeyInfo oluşturucusunda daha iyi bağımsız değişken doğrulaması

.NET Core 3,0 Preview 9 ' dan itibaren, `Pkcs8PrivateKeyInfo` Oluşturucu `algorithmParameters` parametreyi tek bir ber kodlamalı değer olarak doğrular. 

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 9 ' dan önce, [ `Pkcs8PrivateKeyInfo` Oluşturucu](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) `algorithmParameters` bağımsız değişkeni doğrulamadı.  Bu bağımsız değişken geçersiz bir değer temsil ettiğinde, Oluşturucu başarılı olur, ancak,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>veya <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> metotlarından herhangi <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>birine yönelik bir çağrı kabul etmediği bağımsız değişken <xref:System.ArgumentException> için bir oluşturur (`preEncodedValue`) <xref:System.Security.Cryptography.CryptographicException>veya.

Preview 9 ' dan önce .NET Core 3,0 ile çalıştırırsanız aşağıdaki kod yalnızca <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> yöntem çağrıldığında bir özel durum oluşturur:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

.NET Core 3,0 Preview 9 ' dan itibaren bağımsız değişken oluşturucuda onaylanır ve geçersiz bir <xref:System.Security.Cryptography.CryptographicException>değer, oluşturan yöntemi ile sonuçlanır. Bu değişiklik, özel durumu veri hatasının kaynağına yaklaştırır. Örneğin:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Yalnızca geçerli `algorithmParameters` değerlerin sağlandığından veya hem hem de <xref:System.ArgumentException> <xref:System.Security.Cryptography.CryptographicException> özel durum işlemenin isteniyorsa `Pkcs8PrivateKeyInfo` Oluşturucu testine çağrı yapıldığından emin olun.

### <a name="category"></a>Kategori

To

### <a name="affected-apis"></a>Etkilenen API’ler

- [Pkcs8PrivateKeyInfo Oluşturucusu](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->