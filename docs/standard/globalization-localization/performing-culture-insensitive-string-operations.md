---
title: Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme
ms.date: 08/22/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
ms.openlocfilehash: 183078b1f7a3eb3530fea8af06dbb59055d7d25d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120794"
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="44c89-102">Kültüre duyarsız dize işlemlerini gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="44c89-102">Performing culture-insensitive string operations</span></span>
<span data-ttu-id="44c89-103">Kültüre duyarlı dize işlemleri gerçekleştiren çoğu .NET Framework yöntemi varsayılan olarak, bir <xref:System.Globalization.CultureInfo> parametresi geçirerek kullanılacak kültürü açıkça belirtmenize imkan tanıyan yöntem aşırı yüklemeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44c89-103">Most .NET Framework methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="44c89-104">Bu aşırı yüklemeler, büyük/küçük harf eşlemeleri ve sıralama kurallarında kültürel değişimlerini ortadan kaldırmanıza ve kültüre duyarsız sonuçların sağlanmasına imkan sağlar</span><span class="sxs-lookup"><span data-stu-id="44c89-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="44c89-105">Bu bölümde, varsayılan olarak kültüre duyarlı .NET Framework yöntemlerini kullanarak kültüre duyarsız dize işlemlerinin nasıl gerçekleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="44c89-105">This section provides the following topics to demonstrate how to perform culture-insensitive string operations using .NET Framework methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44c89-106">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="44c89-106">In this section</span></span>  
 [<span data-ttu-id="44c89-107">Kültüre Duyarsız Dize Karşılaştırmalarını Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="44c89-107">Performing Culture-Insensitive String Comparisons</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="44c89-108">Kültüre duyarsız dize karşılaştırmaları gerçekleştirmek için <xref:System.String.Compare%2A?displayProperty=nameWithType> ve <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemlerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="44c89-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="44c89-109">Kültüre Duyarsız Büyük/Küçük Harf Değişikliklerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="44c89-109">Performing Culture-Insensitive Case Changes</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="44c89-110"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>ve <xref:System.Char.ToLower%2A?displayProperty=nameWithType> yöntemlerinin kültüre duyarsız büyük/küçük harf değişiklikleri gerçekleştirmek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="44c89-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="44c89-111">Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="44c89-111">Performing Culture-Insensitive String Operations in Collections</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="44c89-112">Koleksiyonlarda kültüre duyarsız işlemler gerçekleştirmek için <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> sınıfı, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> ve <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="44c89-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="44c89-113">Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="44c89-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="44c89-114">Dizilerde kültüre duyarsız işlemler gerçekleştirmek için <xref:System.Array.Sort%2A?displayProperty=nameWithType> ve <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> yöntemlerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="44c89-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="44c89-115">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="44c89-115">Related sections</span></span>  
 [<span data-ttu-id="44c89-116">Kültüre Duyarsız Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="44c89-116">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="44c89-117">Dizeler üzerinde işlem gerçekleştirirken kültür için neden farkında olmanız gerektiğini ve kültüre duyarlı işlemlerin ne zaman gerçekleştirileceğini ve kültüre duyarsız işlemlerin ne zaman gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="44c89-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="44c89-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44c89-118">See also</span></span>

- [<span data-ttu-id="44c89-119">Sıralama ağırlığı tabloları (Windows sistemlerinde .NET için)</span><span class="sxs-lookup"><span data-stu-id="44c89-119">Sorting Weight Tables (for .NET on Windows systems)</span></span>](https://www.microsoft.com/download/details.aspx?id=10921)
- [<span data-ttu-id="44c89-120">Varsayılan Unicode harmanlama öğesi tablosu (Linux ve macOS 'ta .NET Core için)</span><span class="sxs-lookup"><span data-stu-id="44c89-120">Default Unicode Collation Element Table (for .NET Core on Linux and macOS)</span></span>](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
