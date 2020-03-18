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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120794"
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="3fcb7-102">Kültüre duyarsız dize işlemleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="3fcb7-102">Performing culture-insensitive string operations</span></span>
<span data-ttu-id="3fcb7-103">Varsayılan olarak kültüre duyarlı dize işlemleri gerçekleştiren çoğu .NET Framework yöntemi, bir <xref:System.Globalization.CultureInfo> parametre geçerek kullanılacak kültürü açıkça belirtmenize olanak tanıyan yöntem aşırı yüklemeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-103">Most .NET Framework methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="3fcb7-104">Bu aşırı yüklemeler, durum haritalama ve sıralama kurallarındaki kültürel varyasyonları ortadan kaldırmanızı ve kültüre duyarsız sonuçları garanti etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="3fcb7-105">Bu bölümde, varsayılan olarak kültüre duyarlı .NET Framework yöntemlerini kullanarak kültüre duyarsız dize işlemlerinin nasıl gerçekleştirildiğini göstermek için aşağıdaki konular sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-105">This section provides the following topics to demonstrate how to perform culture-insensitive string operations using .NET Framework methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3fcb7-106">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="3fcb7-106">In this section</span></span>  
 [<span data-ttu-id="3fcb7-107">Kültüre Duyarsız Dize Karşılaştırmalarını Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="3fcb7-107">Performing Culture-Insensitive String Comparisons</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="3fcb7-108">Kültüre duyarsız <xref:System.String.Compare%2A?displayProperty=nameWithType> dize karşılaştırmaları gerçekleştirmek için yöntemlerin ve <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemlerin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="3fcb7-109">Kültüre Duyarsız Büyük/Küçük Harf Değişikliklerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="3fcb7-109">Performing Culture-Insensitive Case Changes</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="3fcb7-110">Kültür duyarsız büyük/küçük harf <xref:System.String.ToUpper%2A?displayProperty=nameWithType>değişikliklerini gerçekleştirmek için , , ve <xref:System.String.ToLower%2A?displayProperty=nameWithType> <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> <xref:System.Char.ToLower%2A?displayProperty=nameWithType> yöntemleri nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="3fcb7-111">Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="3fcb7-111">Performing Culture-Insensitive String Operations in Collections</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="3fcb7-112"><xref:System.Collections.CaseInsensitiveComparer>Sınıf, <xref:System.Collections.CaseInsensitiveHashCodeProvider> <xref:System.Collections.SortedList>'ı nasıl kullanacağımı <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> ve <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> koleksiyonlarda kültüre duyarsız işlemleri nasıl gerçekleştireceklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="3fcb7-113">Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="3fcb7-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="3fcb7-114">Diziler halinde <xref:System.Array.Sort%2A?displayProperty=nameWithType> kültüre duyarsız işlemler gerçekleştirmek için yöntemleri ve <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> yöntemleri nasıl kullanacağımı açıklar.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3fcb7-115">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="3fcb7-115">Related sections</span></span>  
 [<span data-ttu-id="3fcb7-116">Kültür-Duyarsız Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="3fcb7-116">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="3fcb7-117">Dizeleri üzerinde işlem yaparken kültürün neden farkında olmanız gerektiğini açıklar ve kültüre duyarlı işlemleri ne zaman gerçekleştireceğiniz ve kültüre duyarlı işlemleri ne zaman gerçekleştireceğiniz için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fcb7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-118">See also</span></span>

- [<span data-ttu-id="3fcb7-119">Ağırlık Tablolarını Sıralama (Windows sistemlerinde .NET için)</span><span class="sxs-lookup"><span data-stu-id="3fcb7-119">Sorting Weight Tables (for .NET on Windows systems)</span></span>](https://www.microsoft.com/download/details.aspx?id=10921)
- [<span data-ttu-id="3fcb7-120">Varsayılan Unicode Collation Element Table (Linux ve macOS'ta .NET Core için)</span><span class="sxs-lookup"><span data-stu-id="3fcb7-120">Default Unicode Collation Element Table (for .NET Core on Linux and macOS)</span></span>](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
