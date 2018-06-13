---
title: Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: a8b347be33ea6acbdf8a78a7af45fd3d0c27f8fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330378"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="f3dff-102">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f3dff-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="f3dff-103">Dizin oluşturucular gibi özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="f3dff-103">Indexers are like properties.</span></span> <span data-ttu-id="f3dff-104">Aşağıdaki tabloda gösterilen farklar dışında özellik erişimcisi için tanımlanan tüm kurallar dizin oluşturucu erişimciler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f3dff-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="f3dff-105">Özellik</span><span class="sxs-lookup"><span data-stu-id="f3dff-105">Property</span></span>|<span data-ttu-id="f3dff-106">Dizin Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="f3dff-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="f3dff-107">Genel veri üyelerini değilmiş gibi çağrılacak yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3dff-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="f3dff-108">Bir iç nesne üzerinde dizi gösterim biçimini kullanarak erişilmesi için bir nesne koleksiyonu öğelerinin sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3dff-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="f3dff-109">Basit bir ad erişilir.</span><span class="sxs-lookup"><span data-stu-id="f3dff-109">Accessed through a simple name.</span></span>|<span data-ttu-id="f3dff-110">Bir dizin erişilir.</span><span class="sxs-lookup"><span data-stu-id="f3dff-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="f3dff-111">Statik veya örnek üyesine olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3dff-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="f3dff-112">Bir örnek üyesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3dff-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="f3dff-113">A [almak](../../../csharp/language-reference/keywords/get.md) bir özelliğin erişimcisine sahip herhangi bir parametre.</span><span class="sxs-lookup"><span data-stu-id="f3dff-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="f3dff-114">A `get` erişimci bir dizin oluşturucu aynı dizin oluşturucu biçimsel parametresi listesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f3dff-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="f3dff-115">A [ayarlamak](../../../csharp/language-reference/keywords/set.md) bir özellik erişimcisi içeren örtük `value` parametresi.</span><span class="sxs-lookup"><span data-stu-id="f3dff-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="f3dff-116">A `set` bir dizin oluşturucu erişimcisine sahip aynı biçimsel parametresi listenin dizin oluşturucu olarak ve ayrıca [değeri](../../../csharp/language-reference/keywords/value.md) parametresi.</span><span class="sxs-lookup"><span data-stu-id="f3dff-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="f3dff-117">Destekler kısaltılmış sözdizimi ile [Auto-Implemented özellikleri](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="f3dff-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="f3dff-118">Kısaltılmış sözdizimi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f3dff-118">Does not support shortened syntax.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3dff-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3dff-119">See Also</span></span>  
 [<span data-ttu-id="f3dff-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f3dff-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f3dff-121">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="f3dff-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="f3dff-122">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f3dff-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
