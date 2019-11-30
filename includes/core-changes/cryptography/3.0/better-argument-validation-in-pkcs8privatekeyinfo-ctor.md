---
ms.openlocfilehash: a9b6af31b68c25ab58c52757f48ed23cca3f5a35
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567971"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="0e834-101">Pkcs8PrivateKeyInfo oluşturucusunda daha iyi bağımsız değişken doğrulaması</span><span class="sxs-lookup"><span data-stu-id="0e834-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="0e834-102">.NET Core 3,0 Preview 9 ' dan itibaren `Pkcs8PrivateKeyInfo` Oluşturucu `algorithmParameters` parametresini tek bir BER kodlamalı değer olarak doğrular.</span><span class="sxs-lookup"><span data-stu-id="0e834-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0e834-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="0e834-103">Change description</span></span>

<span data-ttu-id="0e834-104">.NET Core 3,0 Preview 9 ' dan önce [`Pkcs8PrivateKeyInfo` oluşturucu](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) `algorithmParameters` bağımsız değişkenini doğrulamadı.</span><span class="sxs-lookup"><span data-stu-id="0e834-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="0e834-105">Bu bağımsız değişken geçersiz bir değer temsil ettiğinde, Oluşturucu başarılı olur, ancak <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>veya <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> yöntemlerinin herhangi birine yapılan bir çağrı, kabul etmeyen bir bağımsız değişken için <xref:System.ArgumentException> (`preEncodedValue`) veya bir <xref:System.Security.Cryptography.CryptographicException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e834-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="0e834-106">Preview 9 ' dan önce .NET Core 3,0 ile çalıştırırsanız aşağıdaki kod yalnızca <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> yöntemi çağrıldığında bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0e834-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="0e834-107">.NET Core 3,0 Preview 9 ' dan itibaren, bağımsız değişken oluşturucuda onaylanır ve geçersiz bir değer, <xref:System.Security.Cryptography.CryptographicException>oluşturan Yöntem sonucu oluşur.</span><span class="sxs-lookup"><span data-stu-id="0e834-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="0e834-108">Bu değişiklik, özel durumu veri hatasının kaynağına yaklaştırır.</span><span class="sxs-lookup"><span data-stu-id="0e834-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="0e834-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0e834-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="0e834-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="0e834-110">Version introduced</span></span>

<span data-ttu-id="0e834-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="0e834-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0e834-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0e834-112">Recommended action</span></span>

<span data-ttu-id="0e834-113">Özel durum işleme isteniyorsa yalnızca geçerli `algorithmParameters` değerlerinin sağlandığından veya hem <xref:System.ArgumentException> hem de <xref:System.Security.Cryptography.CryptographicException> için `Pkcs8PrivateKeyInfo` Oluşturucu testine çağrı yapıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="0e834-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="0e834-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="0e834-114">Category</span></span>

<span data-ttu-id="0e834-115">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="0e834-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="0e834-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0e834-116">Affected APIs</span></span>

- <span data-ttu-id="0e834-117">[Pkcs8PrivateKeyInfo Oluşturucusu](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="0e834-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->
