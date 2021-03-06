---
title: 'Son değişiklik: TripleDES tarafından oluşturulan örnekler için varsayılan FeedbackSize değeri. oluşturma değiştirildi'
description: .NET 5 ' teki önemli değişiklik hakkında bilgi edinmek için, TripleDES. Create () tarafından döndürülen TripleDES örneğinde bulunan FeedbackSize özelliğinin varsayılan değeri 64 ' den 8 ' e değişmiştir.
ms.date: 10/16/2020
ms.openlocfilehash: 9d3259da30cce84e83a3f13c610dad5884b445b8
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256770"
---
# <a name="default-feedbacksize-value-for-instances-created-by-tripledescreate-changed"></a><span data-ttu-id="e8bd1-103">TripleDES tarafından oluşturulan örnekler için varsayılan FeedbackSize değeri. oluşturma değiştirildi</span><span class="sxs-lookup"><span data-stu-id="e8bd1-103">Default FeedbackSize value for instances created by TripleDES.Create changed</span></span>

<span data-ttu-id="e8bd1-104"><xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType>Öğesinden döndürülen örnekteki özelliğin varsayılan değeri, <xref:System.Security.Cryptography.TripleDES> <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> .NET Framework geçişinin daha kolay olması için 64 ' den 8 ' e değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="e8bd1-104">The default value for the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType> property on the <xref:System.Security.Cryptography.TripleDES> instance returned from <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> has changed from 64 to 8 to make migration from .NET Framework easier.</span></span> <span data-ttu-id="e8bd1-105">Doğrudan çağıran kodda kullanılmadığı takdirde bu özellik yalnızca özelliği olduğunda kullanılır <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e8bd1-105">This property, unless used directly in caller code, is used only when the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> property is <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="e8bd1-106"><xref:System.Security.Cryptography.CipherMode.CFB>Mod desteği ilk olarak 5,0 RC1 sürümü için .net 'e eklenmiştir, bu nedenle yalnızca .NET 5 RC1 ve .NET 5 RC2 uygulamalarının bu değişiklikten etkilenmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8bd1-106">Support for the <xref:System.Security.Cryptography.CipherMode.CFB> mode was first added to .NET for the 5.0 RC1 release, so only .NET 5 RC1 and .NET 5 RC2 applications should be impacted by this change.</span></span>

## <a name="change-description"></a><span data-ttu-id="e8bd1-107">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="e8bd1-107">Change description</span></span>

<span data-ttu-id="e8bd1-108">.NET Core ve önceki yayın öncesi sürüm sürümlerinde, .NET 5 ' in `TripleDES.Create().FeedbackSize` varsayılan değeri 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e8bd1-108">In .NET Core and previous pre-release versions of .NET 5, `TripleDES.Create().FeedbackSize` has a default value of 64.</span></span> <span data-ttu-id="e8bd1-109">.NET 5 ' in RTM sürümünden itibaren `TripleDES.Create().FeedbackSize` varsayılan değer 8 ' i içerir.</span><span class="sxs-lookup"><span data-stu-id="e8bd1-109">Starting in the RTM version of .NET 5, `TripleDES.Create().FeedbackSize` has a default value of 8.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e8bd1-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e8bd1-110">Reason for change</span></span>

<span data-ttu-id="e8bd1-111">.NET Framework, <xref:System.Security.Cryptography.TripleDES> temel sınıf değerini 64 olarak belirler <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> , ancak <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> sınıf varsayılan olarak 8 ' e yazar.</span><span class="sxs-lookup"><span data-stu-id="e8bd1-111">In .NET Framework, the <xref:System.Security.Cryptography.TripleDES> base class defaults the value of <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> to 64, but the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class overwrites the default to 8.</span></span> <span data-ttu-id="e8bd1-112">Özellik, <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> sürüm 2,0 ' de .NET Core 'a sunulsa da aynı davranış korundu.</span><span class="sxs-lookup"><span data-stu-id="e8bd1-112">When the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property was introduced to .NET Core in version 2.0, this same behavior was preserved.</span></span> <span data-ttu-id="e8bd1-113">Ancak, .NET Framework ' de <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> bir örneği döndürür <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> , bu nedenle algoritma fabrikasından varsayılan değer 8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e8bd1-113">However, in .NET Framework, <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> returns an instance of <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>, so the default value from the algorithm factory is 8.</span></span> <span data-ttu-id="e8bd1-114">.NET Core ve .NET 5 + için, algoritma fabrikası genel olmayan bir uygulama döndürür ve bu, şu anda varsayılan 64 değerine sahip olur.</span><span class="sxs-lookup"><span data-stu-id="e8bd1-114">For .NET Core and .NET 5+, the algorithm factory returns a non-public implementation, which, until now, had a default value of 64.</span></span>

<span data-ttu-id="e8bd1-115"><xref:System.Security.Cryptography.TripleDES>Uygulama sınıfı <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> değerinin 8 olarak değiştirilmesi, şifreleme modunu belirtilen .NET Framework için yazılan uygulamalar için izin verir <xref:System.Security.Cryptography.CipherMode.CFB> <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> , ancak .NET 5 ' te çalışmaya devam etmek için özelliği açıkça atamamıştı.</span><span class="sxs-lookup"><span data-stu-id="e8bd1-115">Changing the <xref:System.Security.Cryptography.TripleDES> implementation class' <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> value to 8 allows for applications written for .NET Framework that specified the cipher mode as <xref:System.Security.Cryptography.CipherMode.CFB> but didn't explicitly assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property, to continue to function on .NET 5.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e8bd1-116">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e8bd1-116">Version introduced</span></span>

<span data-ttu-id="e8bd1-117">5.0</span><span class="sxs-lookup"><span data-stu-id="e8bd1-117">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e8bd1-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e8bd1-118">Recommended action</span></span>

<span data-ttu-id="e8bd1-119">.NET 5 ' ün RC1 veya RC2 sürümlerindeki verileri şifreleyen veya şifresini çözen uygulamalar aşağıdaki koşullar karşılandığında CFB64 ile yapılır:</span><span class="sxs-lookup"><span data-stu-id="e8bd1-119">Applications that encrypt or decrypt data in the RC1 or RC2 versions of .NET 5 do so with CFB64, when the following conditions are met:</span></span>

- <span data-ttu-id="e8bd1-120">Bir <xref:System.Security.Cryptography.TripleDES> örneği ile <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e8bd1-120">With a <xref:System.Security.Cryptography.TripleDES> instance from <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="e8bd1-121">İçin varsayılan değer kullanılıyor <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> .</span><span class="sxs-lookup"><span data-stu-id="e8bd1-121">Using the default value for <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize>.</span></span>
- <span data-ttu-id="e8bd1-122"><xref:System.Security.Cryptography.SymmetricAlgorithm.Mode>Özelliği olarak ayarlanır <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e8bd1-122">With the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> property set to <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="e8bd1-123">Bu davranışı sürdürmek için <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> özelliğini öğesine atayın `64` .</span><span class="sxs-lookup"><span data-stu-id="e8bd1-123">To maintain this behavior, assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property to `64`.</span></span>

<span data-ttu-id="e8bd1-124">Tüm `TripleDES` uygulamalar için aynı varsayılanı kullanmaz <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> .</span><span class="sxs-lookup"><span data-stu-id="e8bd1-124">Not all `TripleDES` implementations use the same default for <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize>.</span></span> <span data-ttu-id="e8bd1-125"><xref:System.Security.Cryptography.CipherMode.CFB>Örneklerde şifre modunu kullanırsanız <xref:System.Security.Cryptography.TripleDES> , özellik değerini her zaman açıkça atamanız önerilir <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> .</span><span class="sxs-lookup"><span data-stu-id="e8bd1-125">We recommend that if you use the <xref:System.Security.Cryptography.CipherMode.CFB> cipher mode on <xref:System.Security.Cryptography.TripleDES> instances, you should always explicitly assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property value.</span></span>

```csharp
TripleDES cipher = TripleDES.Create();
cipher.Mode = CipherMode.CFB;
// Explicitly set the FeedbackSize for CFB to control between CFB8 and CFB64.
cipher.FeedbackSize = 8;
```

## <a name="affected-apis"></a><span data-ttu-id="e8bd1-126">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e8bd1-126">Affected APIs</span></span>

- <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Security.Cryptography.TripleDES.Create`
- `P:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize`

### Category

- Cryptography

-->
