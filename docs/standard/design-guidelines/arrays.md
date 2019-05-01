---
title: Diziler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: KrzysztofCwalina
ms.openlocfilehash: dd30cdee0440553a9f955f0b3f4ee420e938b9ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864123"
---
# <a name="arrays"></a><span data-ttu-id="b2f5a-102">Diziler</span><span class="sxs-lookup"><span data-stu-id="b2f5a-102">Arrays</span></span>
<span data-ttu-id="b2f5a-103">**✓ DO** ortak API'ler dizilerde üzerinden koleksiyonları kullanmayı tercih.</span><span class="sxs-lookup"><span data-stu-id="b2f5a-103">**✓ DO** prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="b2f5a-104">[Koleksiyonları](../../../docs/standard/design-guidelines/guidelines-for-collections.md) bölüm koleksiyonları ve dizileri arasında seçim yapma hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2f5a-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>  
  
 <span data-ttu-id="b2f5a-105">**X DO NOT** salt okunur dizi alanları kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2f5a-105">**X DO NOT** use read-only array fields.</span></span> <span data-ttu-id="b2f5a-106">Alanı salt okunur ve değiştirilemez, ancak dizideki öğeler değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b2f5a-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>  
  
 <span data-ttu-id="b2f5a-107">**✓ CONSIDER** basit dizileri çok boyutlu diziler yerine kullanma.</span><span class="sxs-lookup"><span data-stu-id="b2f5a-107">**✓ CONSIDER** using jagged arrays instead of multidimensional arrays.</span></span>  
  
 <span data-ttu-id="b2f5a-108">Basit bir dizi, diziler de olan öğeler ile bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="b2f5a-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="b2f5a-109">Öğeleri dizileri çok boyutlu diziler için kıyasla daha az harcanmış bazı (örn. seyrek matris) veri kümeleri için önde gelen farklı boyutlarda olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2f5a-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="b2f5a-110">Ayrıca, bazı senaryolarda daha iyi çalışma zamanı performansı göstermesi şekilde CLR basit diziler, dizin işlemleri iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="b2f5a-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>  
  
 <span data-ttu-id="b2f5a-111">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="b2f5a-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b2f5a-112">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="b2f5a-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2f5a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2f5a-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="b2f5a-114">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b2f5a-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="b2f5a-115">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b2f5a-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
