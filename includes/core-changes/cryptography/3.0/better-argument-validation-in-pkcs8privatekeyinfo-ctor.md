---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449236"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="f3a13-101">Pkcs8PrivateKeyInfo oluşturucu daha iyi argüman doğrulama</span><span class="sxs-lookup"><span data-stu-id="f3a13-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="f3a13-102">.NET Core 3.0 Preview 9 `Pkcs8PrivateKeyInfo` ile başlayarak, oluşturucu parametreyi `algorithmParameters` TEK BER kodlanmış değer olarak doğrular.</span><span class="sxs-lookup"><span data-stu-id="f3a13-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f3a13-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="f3a13-103">Change description</span></span>

<span data-ttu-id="f3a13-104">.NET Core 3.0 Preview 9'dan önce, `algorithmParameters` [ `Pkcs8PrivateKeyInfo` oluşturucu](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) bağımsız değişkeni doğrulamadı.</span><span class="sxs-lookup"><span data-stu-id="f3a13-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="f3a13-105">Bu bağımsız değişken geçersiz bir değeri temsil ettiğinde, oluşturucu başarılı olur, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>ancak <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> , <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, , <xref:System.ArgumentException> veya yöntemlerden herhangi biri için bir çağrı kabul etmedikleri bir argüman için ya bir atar (`preEncodedValue`) ya da bir <xref:System.Security.Cryptography.CryptographicException>.</span><span class="sxs-lookup"><span data-stu-id="f3a13-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="f3a13-106">Önizleme 9'dan önce .NET Core 3.0 ile çalıştırılırsa, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> aşağıdaki kod yalnızca yöntem çağrıldığında bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="f3a13-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="f3a13-107">.NET Core 3.0 Preview 9 ile başlayarak, bağımsız değişken oluşturucuda doğrulanır ve <xref:System.Security.Cryptography.CryptographicException>geçersiz bir değer bir .</span><span class="sxs-lookup"><span data-stu-id="f3a13-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="f3a13-108">Bu değişiklik, özel durumu veri hatasıkaynağına yaklaştırıyor.</span><span class="sxs-lookup"><span data-stu-id="f3a13-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="f3a13-109">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f3a13-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="f3a13-110">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="f3a13-110">Version introduced</span></span>

<span data-ttu-id="f3a13-111">3.0 Önizleme 9</span><span class="sxs-lookup"><span data-stu-id="f3a13-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f3a13-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f3a13-112">Recommended action</span></span>

<span data-ttu-id="f3a13-113">`algorithmParameters` Yalnızca geçerli değerlerin sağlandığından veya her `Pkcs8PrivateKeyInfo` ikisi <xref:System.ArgumentException> için de <xref:System.Security.Cryptography.CryptographicException> ve özel durum işleme isteniyorsa yapı testine çağrıda bulunulandan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f3a13-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="f3a13-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="f3a13-114">Category</span></span>

<span data-ttu-id="f3a13-115">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="f3a13-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="f3a13-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f3a13-116">Affected APIs</span></span>

- <span data-ttu-id="f3a13-117">[Pkcs8PrivateKeyInfo yapıcı](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="f3a13-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
