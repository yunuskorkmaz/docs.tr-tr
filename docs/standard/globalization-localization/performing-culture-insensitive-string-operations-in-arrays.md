---
title: "Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d273fbaa792092f5ea56bfa59392794b6728ed67
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a><span data-ttu-id="feaa3-102">Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="feaa3-102">Performing Culture-Insensitive String Operations in Arrays</span></span>
<span data-ttu-id="feaa3-103">Overloads <xref:System.Array.Sort%2A?displayProperty=nameWithType> ve <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> yöntemleri kullanarak varsayılan kültüre duyarlı sıralar gerçekleştirmek <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="feaa3-103">Overloads of the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods perform culture-sensitive sorts by default using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="feaa3-104">Bu yöntemler tarafından döndürülen kültüre duyarlı sonuçları sıralamalar farklılıkları nedeniyle kültür göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="feaa3-104">Culture-sensitive results returned by these methods can vary by culture due to differences in sort orders.</span></span> <span data-ttu-id="feaa3-105">Kültüre duyarlı davranışı ortadan kaldırmak için kabul bu yöntem aşırı birini kullanın bir `comparer` parametresi.</span><span class="sxs-lookup"><span data-stu-id="feaa3-105">To eliminate culture-sensitive behavior, use one of the overloads of this method that accepts a `comparer` parameter.</span></span> <span data-ttu-id="feaa3-106">`comparer` Parametresi belirtir <xref:System.Collections.IComparer> dizideki öğeler karşılaştırılırken kullanmak için uygulama.</span><span class="sxs-lookup"><span data-stu-id="feaa3-106">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing elements in the array.</span></span> <span data-ttu-id="feaa3-107">Kullanan bir özel değişmez karşılaştırıcı sınıfı parametresi için belirlediğiniz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="feaa3-107">For the parameter, specify a custom invariant comparer class that uses <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="feaa3-108">Özel sabit karşılaştırıcı sınıf örneği "SortedList sınıfı kullanarak" konu sağlanan [koleksiyonlarda kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) konu.</span><span class="sxs-lookup"><span data-stu-id="feaa3-108">An example of a custom invariant comparer class is provided in the "Using the SortedList Class" subtopic of the [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) topic.</span></span>  
  
 <span data-ttu-id="feaa3-109">**Not** geçirme **CultureInfo.InvariantCulture** karşılaştırma yöntemi kültüre duyarsız bir karşılaştırma işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="feaa3-109">**Note** Passing **CultureInfo.InvariantCulture** to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="feaa3-110">Ancak, bu dile ait olmayan bir karşılaştırma, örneğin, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri için neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="feaa3-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="feaa3-111">Güvenlik kararları karşılaştırma sonucuna desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="feaa3-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="feaa3-112">Dil olmayan karşılaştırma veya sonuç tabanlı güvenlik kararları desteği için uygulama kabul eden bir karşılaştırma yöntemi kullanması gereken bir <xref:System.StringComparison> değeri.</span><span class="sxs-lookup"><span data-stu-id="feaa3-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="feaa3-113">Uygulama sonra geçirmelisiniz <xref:System.StringComparison.Ordinal>.</span><span class="sxs-lookup"><span data-stu-id="feaa3-113">The application should then pass <xref:System.StringComparison.Ordinal>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feaa3-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="feaa3-114">See Also</span></span>  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="feaa3-115">Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="feaa3-115">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
