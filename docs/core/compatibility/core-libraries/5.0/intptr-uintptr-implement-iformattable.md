---
title: "Son değişiklik: IntPtr ve UIntPtr IFormattable 'ı Uygula"
description: IntPtr ve UIntPtr 'in artık IFormattable 'ı uygulayan çekirdek .NET kitaplıklarında .NET 5 ile ilgili son değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: adfb68807d5fa5f0c750fb41ef75951f63a4b2d5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257446"
---
# <a name="intptr-and-uintptr-implement-iformattable"></a><span data-ttu-id="bf21a-103">IntPtr ve UIntPtr IFormattable uyguluyor</span><span class="sxs-lookup"><span data-stu-id="bf21a-103">IntPtr and UIntPtr implement IFormattable</span></span>

<span data-ttu-id="bf21a-104"><xref:System.IntPtr> ve <xref:System.UIntPtr> Şimdi uygulamasını uygulayın <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="bf21a-104"><xref:System.IntPtr> and <xref:System.UIntPtr> now implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="bf21a-105">Desteği denetleyen işlevler <xref:System.IFormattable> artık bu türler için farklı sonuçlar döndürebilir, çünkü bir biçim belirticisi ve bir kültür de geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="bf21a-105">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

## <a name="change-description"></a><span data-ttu-id="bf21a-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="bf21a-106">Change description</span></span>

<span data-ttu-id="bf21a-107">.NET ' in önceki sürümlerinde <xref:System.IntPtr> ve <xref:System.UIntPtr> uygulamaz <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="bf21a-107">In previous versions of .NET, <xref:System.IntPtr> and <xref:System.UIntPtr> do not implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="bf21a-108">İçin onay veren işlevler <xref:System.IFormattable> , yalnızca veya çağırmak için geri <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> dönebilir <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> , yani biçim belirticileri ve kültürler dikkate alınmıyor.</span><span class="sxs-lookup"><span data-stu-id="bf21a-108">Functions that check for <xref:System.IFormattable> may fall back to just calling <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> or <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType>, which means that format specifiers and cultures are not respected.</span></span>

<span data-ttu-id="bf21a-109">.NET 5 ve sonraki sürümlerde <xref:System.IntPtr> ve <xref:System.UIntPtr> uygulayın <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="bf21a-109">In .NET 5 and later versions, <xref:System.IntPtr> and <xref:System.UIntPtr> implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="bf21a-110">Desteği denetleyen işlevler <xref:System.IFormattable> artık bu türler için farklı sonuçlar döndürebilir, çünkü bir biçim belirticisi ve bir kültür de geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="bf21a-110">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

<span data-ttu-id="bf21a-111">Bu değişiklik, enterpolasyonlu dizeler ve <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> diğerleri arasında senaryolar etkiler.</span><span class="sxs-lookup"><span data-stu-id="bf21a-111">This change impacts scenarios like interpolated strings and <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, among others.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="bf21a-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="bf21a-112">Reason for change</span></span>

<span data-ttu-id="bf21a-113"><xref:System.IntPtr> ve <xref:System.UIntPtr> artık C# ' de `nint` ve anahtar kelimeleri aracılığıyla dil desteğine sahiptir `nuint` .</span><span class="sxs-lookup"><span data-stu-id="bf21a-113"><xref:System.IntPtr> and <xref:System.UIntPtr> now have language support in C# through the `nint` and `nuint` keywords.</span></span> <span data-ttu-id="bf21a-114">Yedekleme türleri, gibi diğer temel türler tarafından sunulan işlevlerle neredeyse eşlik (mümkün olduğunda) sağlayacak şekilde güncelleştirildi <xref:System.Int32?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bf21a-114">The backing types were updated to provide near parity (where possible) with functionality exposed by other primitive types, such as <xref:System.Int32?displayProperty=nameWithType>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="bf21a-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="bf21a-115">Version introduced</span></span>

<span data-ttu-id="bf21a-116">5.0</span><span class="sxs-lookup"><span data-stu-id="bf21a-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="bf21a-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="bf21a-117">Recommended action</span></span>

<span data-ttu-id="bf21a-118">Bu türlerin değerlerini görüntülerken Biçim belirleyicisi veya özel kültürün kullanılmasını istemiyorsanız, ' <xref:System.IntPtr.ToString?displayProperty=nameWithType> <xref:System.UIntPtr.ToString?displayProperty=nameWithType> nin ve aşırı yüklerini çağırabilirsiniz `ToString()` .</span><span class="sxs-lookup"><span data-stu-id="bf21a-118">If you don't want a format specifier or custom culture to be used when displaying values of these types, you can call the <xref:System.IntPtr.ToString?displayProperty=nameWithType> and <xref:System.UIntPtr.ToString?displayProperty=nameWithType> overloads of `ToString()`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="bf21a-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="bf21a-119">Affected APIs</span></span>

<span data-ttu-id="bf21a-120">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="bf21a-120">Not detectable via API analysis.</span></span>

<!--

### Category

Core .NET libraries

### Affected APIs

Not detectable via API analysis.

-->
