---
title: Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b52ff8d72132c1076dfdece5e1ce47bbece37b81
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855999"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a><span data-ttu-id="e785f-102">Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="e785f-102">Performing Culture-Insensitive String Operations in Arrays</span></span>

<span data-ttu-id="e785f-103">Ve <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> <xref:System.Array.Sort%2A?displayProperty=nameWithType> yöntemlerininaşırıyüklemeleri,özelliğinikullanarakvarsayılanolarakkültüreduyarlısıralargerçekleştirir.<xref:System.Array.BinarySearch%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e785f-103">Overloads of the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods perform culture-sensitive sorts by default using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="e785f-104">Bu yöntemler tarafından döndürülen kültüre duyarlı sonuçlar, sıralama emirlerindeki farklılıklar nedeniyle kültüre göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="e785f-104">Culture-sensitive results returned by these methods can vary by culture due to differences in sort orders.</span></span> <span data-ttu-id="e785f-105">Kültüre duyarlı davranışı ortadan kaldırmak için, bu yöntemin bir `comparer` parametreyi kabul eden aşırı yüklemelerinin birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e785f-105">To eliminate culture-sensitive behavior, use one of the overloads of this method that accepts a `comparer` parameter.</span></span> <span data-ttu-id="e785f-106">Parametresi dizideki öğeleri karşılaştırırken <xref:System.Collections.IComparer> kullanılacak uygulamayı belirtir. `comparer`</span><span class="sxs-lookup"><span data-stu-id="e785f-106">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing elements in the array.</span></span> <span data-ttu-id="e785f-107">Parametresi için, tarafından kullanılan <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>özel bir sabit karşılaştırıcı sınıfı belirtin.</span><span class="sxs-lookup"><span data-stu-id="e785f-107">For the parameter, specify a custom invariant comparer class that uses <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e785f-108">[Koleksiyonlarda kültüre duyarsız dize Işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) konusundaki "SortedList sınıfı kullanma" alt konusunun özel bir sabit karşılaştırıcı sınıfına bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e785f-108">An example of a custom invariant comparer class is provided in the "Using the SortedList Class" subtopic of the [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="e785f-109">Bir karşılaştırma yöntemine **CultureInfo. InvariantCulture** geçirilmesi, kültüre duyarsız bir karşılaştırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e785f-109">Passing **CultureInfo.InvariantCulture** to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="e785f-110">Ancak, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri gibi dil olmayan bir karşılaştırmaya neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="e785f-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="e785f-111">, Karşılaştırma sonucuna göre güvenlik kararlarını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e785f-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="e785f-112">Dil olmayan bir karşılaştırma veya sonuç tabanlı güvenlik kararları için destek için, uygulamanın bir <xref:System.StringComparison> değeri kabul eden bir karşılaştırma yöntemi kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e785f-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="e785f-113">Uygulama daha sonra geçmelidir <xref:System.StringComparison.Ordinal>.</span><span class="sxs-lookup"><span data-stu-id="e785f-113">The application should then pass <xref:System.StringComparison.Ordinal>.</span></span>

## <a name="see-also"></a><span data-ttu-id="e785f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e785f-114">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [<span data-ttu-id="e785f-115">Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="e785f-115">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
