---
title: Özellikler ve Dizinleyiciler Arasında Karşılaştırma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 330d222083ce599719698c023803196dfe88da84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712136"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="deaff-102">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="deaff-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="deaff-103">Dizin leyiciler özellikler gibidir.</span><span class="sxs-lookup"><span data-stu-id="deaff-103">Indexers are like properties.</span></span> <span data-ttu-id="deaff-104">Aşağıdaki tabloda gösterilen farklar dışında, özellik erişime girenler için tanımlanan tüm kurallar dizinleyici erişime girenler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="deaff-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="deaff-105">Özellik</span><span class="sxs-lookup"><span data-stu-id="deaff-105">Property</span></span>|<span data-ttu-id="deaff-106">Dizin Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="deaff-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="deaff-107">Yöntemlerin genel veri üyesi gibi çağrılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="deaff-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="deaff-108">Nesnenin iç koleksiyonunun öğelerine, nesnenin kendisinde dizi gösterimi kullanılarak erişilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="deaff-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="deaff-109">Basit bir isimle erişildi.</span><span class="sxs-lookup"><span data-stu-id="deaff-109">Accessed through a simple name.</span></span>|<span data-ttu-id="deaff-110">Bir dizin üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="deaff-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="deaff-111">Statik veya örnek üye olabilir.</span><span class="sxs-lookup"><span data-stu-id="deaff-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="deaff-112">Örnek üye olmalı.</span><span class="sxs-lookup"><span data-stu-id="deaff-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="deaff-113">Bir özelliğin [erişime](../../language-reference/keywords/get.md) erişiminin parametreleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="deaff-113">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="deaff-114">Bir `get` dizinleyicinin erişimi, dizinleyiciyle aynı resmi parametre listesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="deaff-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="deaff-115">Bir özelliğin [ayarlanmış](../../language-reference/keywords/set.md) bir erişimcisi örtük `value` parametre içerir.</span><span class="sxs-lookup"><span data-stu-id="deaff-115">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="deaff-116">Bir `set` dizin leyicinin erişicisi, dizinleyiciyle ve [değer](../../language-reference/keywords/value.md) parametresi ile aynı resmi parametre listesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="deaff-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="deaff-117">[Otomatik Uygulanan Özellikler](../classes-and-structs/auto-implemented-properties.md)ile kısaltılmış sözdizimini destekler.</span><span class="sxs-lookup"><span data-stu-id="deaff-117">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="deaff-118">Yalnızca dizin oluşturma için ifade gövdeli üyeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="deaff-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="deaff-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="deaff-119">See also</span></span>

- [<span data-ttu-id="deaff-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="deaff-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="deaff-121">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="deaff-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="deaff-122">Özellikler</span><span class="sxs-lookup"><span data-stu-id="deaff-122">Properties</span></span>](../classes-and-structs/properties.md)
