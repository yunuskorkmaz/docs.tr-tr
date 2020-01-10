---
title: Diziler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: ac4b073d2d3291922498a0e56c7e81f7e7868c65
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709575"
---
# <a name="arrays"></a><span data-ttu-id="0df66-102">Diziler</span><span class="sxs-lookup"><span data-stu-id="0df66-102">Arrays</span></span>
<span data-ttu-id="0df66-103">**✓ DO** ortak API'ler dizilerde üzerinden koleksiyonları kullanmayı tercih.</span><span class="sxs-lookup"><span data-stu-id="0df66-103">**✓ DO** prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="0df66-104">[Koleksiyonlar](../../../docs/standard/design-guidelines/guidelines-for-collections.md) bölümü koleksiyonlar ve diziler arasında nasıl seçim yapılacağı hakkında ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0df66-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>  
  
 <span data-ttu-id="0df66-105">**X DO NOT** salt okunur dizi alanları kullanın.</span><span class="sxs-lookup"><span data-stu-id="0df66-105">**X DO NOT** use read-only array fields.</span></span> <span data-ttu-id="0df66-106">Alanın kendisi salt okunurdur ve değiştirilemez, ancak dizideki öğeler değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0df66-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>  
  
 <span data-ttu-id="0df66-107">**✓ CONSIDER** basit dizileri çok boyutlu diziler yerine kullanma.</span><span class="sxs-lookup"><span data-stu-id="0df66-107">**✓ CONSIDER** using jagged arrays instead of multidimensional arrays.</span></span>  
  
 <span data-ttu-id="0df66-108">Sivri dizi öğeleri de diziler olan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="0df66-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="0df66-109">Öğeleri oluşturan diziler farklı boyutlarda olabilir ve çok boyutlu dizilere kıyasla bazı veri kümeleri (örn. seyrek matris) için daha az harcanan alana sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0df66-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="0df66-110">Ayrıca, CLR, basit diziler üzerinde dizin işlemlerini iyileştirir, bu nedenle bazı senaryolarda çalışma zamanı daha iyi bir performans sergilebilirler.</span><span class="sxs-lookup"><span data-stu-id="0df66-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>  
  
 <span data-ttu-id="0df66-111">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="0df66-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0df66-112">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="0df66-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df66-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0df66-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="0df66-114">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0df66-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="0df66-115">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0df66-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
