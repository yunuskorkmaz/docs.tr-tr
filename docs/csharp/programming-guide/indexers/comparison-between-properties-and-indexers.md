---
title: Özellikler ve Dizin oluşturucular arasında karşılaştırma-C# Programlama Kılavuzu
description: C# içindeki dizin oluşturucularının özellikler gibi nasıl olduğunu karşılaştırın. Bazı farklılıklar haricinde, özellik erişimcileri için tanımlanan kurallar Dizin Oluşturucu erişimcileri için geçerlidir.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: fff20ca965e7614d26f7da32321a829d13292389
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192535"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="95903-104">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="95903-104">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="95903-105">Dizin oluşturucular Özellikler gibidir.</span><span class="sxs-lookup"><span data-stu-id="95903-105">Indexers are like properties.</span></span> <span data-ttu-id="95903-106">Aşağıdaki tabloda gösterilen farklar dışında, özellik erişimcileri için tanımlanan tüm kurallar Dizin Oluşturucu erişimcileri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="95903-106">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="95903-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="95903-107">Property</span></span>|<span data-ttu-id="95903-108">Dizin Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="95903-108">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="95903-109">Yöntemlerin ortak veri üyeleri gibi çağrılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="95903-109">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="95903-110">Nesne üzerinde dizi gösterimi kullanılarak bir nesne iç koleksiyonunun öğelerine erişilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="95903-110">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="95903-111">Basit bir ad üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="95903-111">Accessed through a simple name.</span></span>|<span data-ttu-id="95903-112">Bir dizin üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="95903-112">Accessed through an index.</span></span>|  
|<span data-ttu-id="95903-113">Statik veya örnek üyesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="95903-113">Can be a static or an instance member.</span></span>|<span data-ttu-id="95903-114">Örnek üye olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="95903-114">Must be an instance member.</span></span>|  
|<span data-ttu-id="95903-115">Özelliğin [Get](../../language-reference/keywords/get.md) erişimcisinin parametresi yok.</span><span class="sxs-lookup"><span data-stu-id="95903-115">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="95903-116">`get`Bir dizin oluşturucunun erişimcisi, Dizin Oluşturucu ile aynı biçimsel parametre listesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="95903-116">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="95903-117">Bir özelliğin [set](../../language-reference/keywords/set.md) erişimcisi örtük `value` parametresi içerir.</span><span class="sxs-lookup"><span data-stu-id="95903-117">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="95903-118">`set`Bir dizin oluşturucunun erişimcisi, Dizin Oluşturucu ile aynı biçimsel parametre listesine ve ayrıca [değer](../../language-reference/keywords/value.md) parametresine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="95903-118">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="95903-119">[Otomatik uygulanan özelliklerle](../classes-and-structs/auto-implemented-properties.md)kısaltılmış sözdizimini destekler.</span><span class="sxs-lookup"><span data-stu-id="95903-119">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="95903-120">Yalnızca Get Dizin oluşturucular için ifade gövdeli üyelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="95903-120">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95903-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95903-121">See also</span></span>

- [<span data-ttu-id="95903-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="95903-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="95903-123">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="95903-123">Indexers</span></span>](./index.md)
- [<span data-ttu-id="95903-124">Özellikler</span><span class="sxs-lookup"><span data-stu-id="95903-124">Properties</span></span>](../classes-and-structs/properties.md)
