---
title: "Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 62aa839d2dae2f6dc84d529a8abf5061367f221f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="a8960-102">Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="a8960-102">Performing Culture-Insensitive String Operations</span></span>
<span data-ttu-id="a8960-103">Açıkça geçirerek kullanılacak kültürü belirtmenize olanak veren yöntemi aşırı yüklemeleri varsayılan kültüre duyarlı dize işlemleri çoğu .NET Framework yöntemleri sunar bir <xref:System.Globalization.CultureInfo> parametresi.</span><span class="sxs-lookup"><span data-stu-id="a8960-103">Most .NET Framework methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="a8960-104">Bu aşırı eşlemeler sıralama kuralları ve kültüre duyarsız sonuçları garanti durumda kültürel Çeşitlemeler ortadan kaldırmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8960-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="a8960-105">Bu bölümde kültüre duyarlı .NET Framework yöntemlerini kullanarak kültüre duyarsız dize işlemlerini gerçekleştirme göstermek için aşağıdaki konuları varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="a8960-105">This section provides the following topics to demonstrate how to perform culture-insensitive string operations using .NET Framework methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8960-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a8960-106">In This Section</span></span>  
 [<span data-ttu-id="a8960-107">Kültüre Duyarsız Dize Karşılaştırmalarını Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="a8960-107">Performing Culture-Insensitive String Comparisons</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="a8960-108">Nasıl kullanılacağını açıklar <xref:System.String.Compare%2A?displayProperty=nameWithType> ve <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemleri kültüre duyarsız dize karşılaştırmalarını gerçekleştirme.</span><span class="sxs-lookup"><span data-stu-id="a8960-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="a8960-109">Kültüre Duyarsız Büyük/Küçük Harf Değişikliklerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="a8960-109">Performing Culture-Insensitive Case Changes</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="a8960-110">Nasıl kullanılacağını açıklar <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, ve <xref:System.Char.ToLower%2A?displayProperty=nameWithType> yöntemleri kültüre duyarsız büyük/küçük değişikliklerini gerçekleştirme.</span><span class="sxs-lookup"><span data-stu-id="a8960-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="a8960-111">Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="a8960-111">Performing Culture-Insensitive String Operations in Collections</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="a8960-112">Nasıl kullanılacağını açıklar <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> sınıfı, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> ve <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> koleksiyonlarda kültüre duyarsız işlemlerini gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="a8960-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="a8960-113">Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="a8960-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="a8960-114">Nasıl kullanılacağını açıklar <xref:System.Array.Sort%2A?displayProperty=nameWithType> ve <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> dizilerde kültüre duyarsız işlemlerini gerçekleştirmek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="a8960-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a8960-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a8960-115">Related Sections</span></span>  
 [<span data-ttu-id="a8960-116">Kültüre Duyarsız Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="a8960-116">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="a8960-117">Neden dizelerde işlemleri gerçekleştirirken kültürünü bilmeniz gereken açıklar ve kültüre duyarlı işlemlerini gerçekleştirmek ne zaman ve ne zaman kültüre duyarsız işlemleri gerçekleştirmek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8960-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>
