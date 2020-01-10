---
title: Özellikler ve Dizin oluşturucular arasında karşılaştırma C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 330d222083ce599719698c023803196dfe88da84
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712136"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="5df48-102">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5df48-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="5df48-103">Dizin oluşturucular Özellikler gibidir.</span><span class="sxs-lookup"><span data-stu-id="5df48-103">Indexers are like properties.</span></span> <span data-ttu-id="5df48-104">Aşağıdaki tabloda gösterilen farklar dışında, özellik erişimcileri için tanımlanan tüm kurallar Dizin Oluşturucu erişimcileri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5df48-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="5df48-105">Özellik</span><span class="sxs-lookup"><span data-stu-id="5df48-105">Property</span></span>|<span data-ttu-id="5df48-106">Dizin Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="5df48-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="5df48-107">Yöntemlerin ortak veri üyeleri gibi çağrılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="5df48-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="5df48-108">Nesne üzerinde dizi gösterimi kullanılarak bir nesne iç koleksiyonunun öğelerine erişilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="5df48-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="5df48-109">Basit bir ad üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="5df48-109">Accessed through a simple name.</span></span>|<span data-ttu-id="5df48-110">Bir dizin üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="5df48-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="5df48-111">Statik veya örnek üyesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="5df48-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="5df48-112">Örnek üye olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5df48-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="5df48-113">Özelliğin [Get](../../language-reference/keywords/get.md) erişimcisinin parametresi yok.</span><span class="sxs-lookup"><span data-stu-id="5df48-113">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="5df48-114">Bir dizin oluşturucunun `get` erişimcisi, Indexer ile aynı biçimsel parametre listesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5df48-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="5df48-115">Bir özelliğin [set](../../language-reference/keywords/set.md) erişimcisi örtük `value` parametresi içerir.</span><span class="sxs-lookup"><span data-stu-id="5df48-115">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="5df48-116">Bir dizin oluşturucunun `set` erişimcisi, Dizin Oluşturucu ile aynı biçimsel parametre listesine ve ayrıca [değer](../../language-reference/keywords/value.md) parametresine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5df48-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="5df48-117">[Otomatik uygulanan özelliklerle](../classes-and-structs/auto-implemented-properties.md)kısaltılmış sözdizimini destekler.</span><span class="sxs-lookup"><span data-stu-id="5df48-117">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="5df48-118">Yalnızca Get Dizin oluşturucular için ifade gövdeli üyelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="5df48-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5df48-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5df48-119">See also</span></span>

- [<span data-ttu-id="5df48-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5df48-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5df48-121">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="5df48-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="5df48-122">Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="5df48-122">Properties</span></span>](../classes-and-structs/properties.md)
