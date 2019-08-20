---
title: Özellikler ve Dizin oluşturucular arasında karşılaştırma C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 4a14c2bf80ff203c5db7fc7663afeb816dc4a2c0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589473"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="27c23-102">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="27c23-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="27c23-103">Dizin oluşturucular Özellikler gibidir.</span><span class="sxs-lookup"><span data-stu-id="27c23-103">Indexers are like properties.</span></span> <span data-ttu-id="27c23-104">Aşağıdaki tabloda gösterilen farklar dışında, özellik erişimcileri için tanımlanan tüm kurallar Dizin Oluşturucu erişimcileri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="27c23-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="27c23-105">Özellik</span><span class="sxs-lookup"><span data-stu-id="27c23-105">Property</span></span>|<span data-ttu-id="27c23-106">Dizinleyic</span><span class="sxs-lookup"><span data-stu-id="27c23-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="27c23-107">Yöntemlerin ortak veri üyeleri gibi çağrılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="27c23-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="27c23-108">Nesne üzerinde dizi gösterimi kullanılarak bir nesne iç koleksiyonunun öğelerine erişilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="27c23-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="27c23-109">Basit bir ad üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="27c23-109">Accessed through a simple name.</span></span>|<span data-ttu-id="27c23-110">Bir dizin üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="27c23-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="27c23-111">Statik veya örnek üyesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="27c23-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="27c23-112">Örnek üye olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="27c23-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="27c23-113">Özelliğin [Get](../../language-reference/keywords/get.md) erişimcisinin parametresi yok.</span><span class="sxs-lookup"><span data-stu-id="27c23-113">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="27c23-114">Bir dizin oluşturucunun erişimcisi, Dizin Oluşturucu ile aynı biçimsel parametre listesine sahiptir. `get`</span><span class="sxs-lookup"><span data-stu-id="27c23-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="27c23-115">Bir özelliğin [set](../../language-reference/keywords/set.md) erişimcisi örtük `value` parametresi içerir.</span><span class="sxs-lookup"><span data-stu-id="27c23-115">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="27c23-116">Bir dizin oluşturucunun [](../../language-reference/keywords/value.md) erişimcisi,DizinOluşturucuileaynıbiçimselparametrelistesineveayrıcadeğerparametresine`set` sahiptir.</span><span class="sxs-lookup"><span data-stu-id="27c23-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="27c23-117">[Otomatik uygulanan özelliklerle](../classes-and-structs/auto-implemented-properties.md)kısaltılmış sözdizimini destekler.</span><span class="sxs-lookup"><span data-stu-id="27c23-117">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="27c23-118">Yalnızca Get Dizin oluşturucular için ifade gövdeli üyelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="27c23-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27c23-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27c23-119">See also</span></span>

- [<span data-ttu-id="27c23-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="27c23-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="27c23-121">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="27c23-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="27c23-122">Özellikler</span><span class="sxs-lookup"><span data-stu-id="27c23-122">Properties</span></span>](../classes-and-structs/properties.md)
