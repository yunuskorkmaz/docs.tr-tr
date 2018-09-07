---
title: Diziler
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ac7e28c3172f2ed68d402e1d04a1664644c7f25
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047824"
---
# <a name="arrays"></a><span data-ttu-id="307b7-102">Diziler</span><span class="sxs-lookup"><span data-stu-id="307b7-102">Arrays</span></span>
<span data-ttu-id="307b7-103">**✓ DO** ortak API'ler dizilerde üzerinden koleksiyonları kullanmayı tercih.</span><span class="sxs-lookup"><span data-stu-id="307b7-103">**✓ DO** prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="307b7-104">[Koleksiyonları](../../../docs/standard/design-guidelines/guidelines-for-collections.md) bölüm koleksiyonları ve dizileri arasında seçim yapma hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="307b7-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>  
  
 <span data-ttu-id="307b7-105">**X DO NOT** salt okunur dizi alanları kullanın.</span><span class="sxs-lookup"><span data-stu-id="307b7-105">**X DO NOT** use read-only array fields.</span></span> <span data-ttu-id="307b7-106">Alanı salt okunur ve değiştirilemez, ancak dizideki öğeler değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="307b7-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>  
  
 <span data-ttu-id="307b7-107">**✓ CONSIDER** basit dizileri çok boyutlu diziler yerine kullanma.</span><span class="sxs-lookup"><span data-stu-id="307b7-107">**✓ CONSIDER** using jagged arrays instead of multidimensional arrays.</span></span>  
  
 <span data-ttu-id="307b7-108">Basit bir dizi, diziler de olan öğeler ile bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="307b7-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="307b7-109">Öğeleri dizileri çok boyutlu diziler için kıyasla daha az harcanmış bazı (örn. seyrek matris) veri kümeleri için önde gelen farklı boyutlarda olabilir.</span><span class="sxs-lookup"><span data-stu-id="307b7-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="307b7-110">Ayrıca, bazı senaryolarda daha iyi çalışma zamanı performansı göstermesi şekilde CLR basit diziler, dizin işlemleri iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="307b7-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>  
  
 <span data-ttu-id="307b7-111">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="307b7-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="307b7-112">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="307b7-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="307b7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="307b7-113">See also</span></span>

- <xref:System.Array>  
- [<span data-ttu-id="307b7-114">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="307b7-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="307b7-115">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="307b7-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
