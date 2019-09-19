---
ms.openlocfilehash: f72a9f60d0adcace2df6f1761940f8d8cd33d3af
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119291"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="83e53-101">Pkcs8PrivateKeyInfo oluşturucusunda daha iyi bağımsız değişken doğrulaması</span><span class="sxs-lookup"><span data-stu-id="83e53-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="83e53-102">.NET Core 3,0 Preview 9 ' dan itibaren, `Pkcs8PrivateKeyInfo` Oluşturucu `algorithmParameters` parametreyi tek bir ber kodlamalı değer olarak doğrular.</span><span class="sxs-lookup"><span data-stu-id="83e53-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span> 

#### <a name="change-description"></a><span data-ttu-id="83e53-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="83e53-103">Change description</span></span>

<span data-ttu-id="83e53-104">.NET Core 3,0 Preview 9 ' dan önce, [ `Pkcs8PrivateKeyInfo` Oluşturucu](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) `algorithmParameters` bağımsız değişkeni doğrulamadı.</span><span class="sxs-lookup"><span data-stu-id="83e53-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="83e53-105">Bu bağımsız değişken geçersiz bir değer temsil ettiğinde, Oluşturucu başarılı olur, ancak,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>veya <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> metotlarından herhangi <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>birine yönelik bir çağrı kabul etmediği bağımsız değişken <xref:System.ArgumentException> için bir oluşturur (`preEncodedValue`) <xref:System.Security.Cryptography.CryptographicException>veya.</span><span class="sxs-lookup"><span data-stu-id="83e53-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="83e53-106">Preview 9 ' dan önce .NET Core 3,0 ile çalıştırırsanız aşağıdaki kod yalnızca <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> yöntem çağrıldığında bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="83e53-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="83e53-107">.NET Core 3,0 Preview 9 ' dan itibaren bağımsız değişken oluşturucuda onaylanır ve geçersiz bir <xref:System.Security.Cryptography.CryptographicException>değer, oluşturan yöntemi ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="83e53-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="83e53-108">Bu değişiklik, özel durumu veri hatasının kaynağına yaklaştırır.</span><span class="sxs-lookup"><span data-stu-id="83e53-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="83e53-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="83e53-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="83e53-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="83e53-110">Version introduced</span></span>

<span data-ttu-id="83e53-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="83e53-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="83e53-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="83e53-112">Recommended action</span></span>

<span data-ttu-id="83e53-113">Yalnızca geçerli `algorithmParameters` değerlerin sağlandığından veya hem hem de <xref:System.ArgumentException> <xref:System.Security.Cryptography.CryptographicException> özel durum işlemenin isteniyorsa `Pkcs8PrivateKeyInfo` Oluşturucu testine çağrı yapıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="83e53-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="83e53-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="83e53-114">Category</span></span>

<span data-ttu-id="83e53-115">To</span><span class="sxs-lookup"><span data-stu-id="83e53-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="83e53-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="83e53-116">Affected APIs</span></span>

- <span data-ttu-id="83e53-117">[Pkcs8PrivateKeyInfo Oluşturucusu](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="83e53-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->