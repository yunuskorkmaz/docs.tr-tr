---
title: "Son değişiklik: IntPtr ve UIntPtr IFormattable 'ı Uygula"
description: IntPtr ve UIntPtr 'in artık IFormattable 'ı uygulayan çekirdek .NET kitaplıklarında .NET 5,0 son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 0684652cdc2b8cf1d237074263bf0809082b0dcd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761641"
---
# <a name="intptr-and-uintptr-implement-iformattable"></a><span data-ttu-id="73fa8-103">IntPtr ve UIntPtr IFormattable 'ı uygular</span><span class="sxs-lookup"><span data-stu-id="73fa8-103">IntPtr and UIntPtr implement IFormattable</span></span>

<span data-ttu-id="73fa8-104"><xref:System.IntPtr> ve <xref:System.UIntPtr> Şimdi uygulamasını uygulayın <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="73fa8-104"><xref:System.IntPtr> and <xref:System.UIntPtr> now implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="73fa8-105">Desteği denetleyen işlevler <xref:System.IFormattable> artık bu türler için farklı sonuçlar döndürebilir, çünkü bir biçim belirticisi ve bir kültür de geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="73fa8-105">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

## <a name="change-description"></a><span data-ttu-id="73fa8-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="73fa8-106">Change description</span></span>

<span data-ttu-id="73fa8-107">.NET ' in önceki sürümlerinde <xref:System.IntPtr> ve <xref:System.UIntPtr> uygulamaz <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="73fa8-107">In previous versions of .NET, <xref:System.IntPtr> and <xref:System.UIntPtr> do not implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="73fa8-108">İçin onay veren işlevler <xref:System.IFormattable> , yalnızca veya çağırmak için geri <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> dönebilir <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> , yani biçim belirticileri ve kültürler dikkate alınmıyor.</span><span class="sxs-lookup"><span data-stu-id="73fa8-108">Functions that check for <xref:System.IFormattable> may fall back to just calling <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> or <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType>, which means that format specifiers and cultures are not respected.</span></span>

<span data-ttu-id="73fa8-109">.NET 5,0 ve sonraki sürümlerde <xref:System.IntPtr> ve <xref:System.UIntPtr> uygulayın <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="73fa8-109">In .NET 5.0 and later versions, <xref:System.IntPtr> and <xref:System.UIntPtr> implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="73fa8-110">Desteği denetleyen işlevler <xref:System.IFormattable> artık bu türler için farklı sonuçlar döndürebilir, çünkü bir biçim belirticisi ve bir kültür de geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="73fa8-110">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

<span data-ttu-id="73fa8-111">Bu değişiklik, enterpolasyonlu dizeler ve <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> diğerleri arasında senaryolar etkiler.</span><span class="sxs-lookup"><span data-stu-id="73fa8-111">This change impacts scenarios like interpolated strings and <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, among others.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="73fa8-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="73fa8-112">Reason for change</span></span>

<span data-ttu-id="73fa8-113"><xref:System.IntPtr> ve <xref:System.UIntPtr> artık C# ' de `nint` ve anahtar kelimeleri aracılığıyla dil desteğine sahiptir `nuint` .</span><span class="sxs-lookup"><span data-stu-id="73fa8-113"><xref:System.IntPtr> and <xref:System.UIntPtr> now have language support in C# through the `nint` and `nuint` keywords.</span></span> <span data-ttu-id="73fa8-114">Yedekleme türleri, gibi diğer temel türler tarafından sunulan işlevlerle neredeyse eşlik (mümkün olduğunda) sağlayacak şekilde güncelleştirildi <xref:System.Int32?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="73fa8-114">The backing types were updated to provide near parity (where possible) with functionality exposed by other primitive types, such as <xref:System.Int32?displayProperty=nameWithType>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="73fa8-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="73fa8-115">Version introduced</span></span>

<span data-ttu-id="73fa8-116">5.0</span><span class="sxs-lookup"><span data-stu-id="73fa8-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="73fa8-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="73fa8-117">Recommended action</span></span>

<span data-ttu-id="73fa8-118">Bu türlerin değerlerini görüntülerken Biçim belirleyicisi veya özel kültürün kullanılmasını istemiyorsanız, ' <xref:System.IntPtr.ToString?displayProperty=nameWithType> <xref:System.UIntPtr.ToString?displayProperty=nameWithType> nin ve aşırı yüklerini çağırabilirsiniz `ToString()` .</span><span class="sxs-lookup"><span data-stu-id="73fa8-118">If you don't want a format specifier or custom culture to be used when displaying values of these types, you can call the <xref:System.IntPtr.ToString?displayProperty=nameWithType> and <xref:System.UIntPtr.ToString?displayProperty=nameWithType> overloads of `ToString()`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="73fa8-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="73fa8-119">Affected APIs</span></span>

<span data-ttu-id="73fa8-120">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="73fa8-120">Not detectable via API analysis.</span></span>

<!--

### Category

Core .NET libraries

### Affected APIs

Not detectable via API analysis.

-->
