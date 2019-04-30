---
title: Özellikler ve dizin oluşturucular - arasında karşılaştırma C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 41b27905edb8a0e00a6af5a4cce38988161326d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680096"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="c89ab-102">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c89ab-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="c89ab-103">Dizin oluşturucular gibi özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="c89ab-103">Indexers are like properties.</span></span> <span data-ttu-id="c89ab-104">Aşağıdaki tabloda gösterilen farklılıklar dışında özellik erişimcileri için tanımlanan tüm kurallar dizin oluşturucu erişimcileri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c89ab-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="c89ab-105">Özellik</span><span class="sxs-lookup"><span data-stu-id="c89ab-105">Property</span></span>|<span data-ttu-id="c89ab-106">Dizin Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="c89ab-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="c89ab-107">Ortak veri üyeleri değilmiş gibi çağrılacak yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="c89ab-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="c89ab-108">Nesne üzerinde dizi gösterimi kullanılarak erişilecek bir nesnenin iç bir koleksiyonun öğeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c89ab-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="c89ab-109">Basit bir ad erişilir.</span><span class="sxs-lookup"><span data-stu-id="c89ab-109">Accessed through a simple name.</span></span>|<span data-ttu-id="c89ab-110">Dizin erişilir.</span><span class="sxs-lookup"><span data-stu-id="c89ab-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="c89ab-111">Statik veya örnek üyesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="c89ab-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="c89ab-112">Bir örnek üyesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c89ab-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="c89ab-113">A [alma](../../../csharp/language-reference/keywords/get.md) özellik erişimcisi sahip parametre yok.</span><span class="sxs-lookup"><span data-stu-id="c89ab-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="c89ab-114">A `get` erişimci bir dizin oluşturucu aynı dizin oluşturucu biçimsel parametre listesine sahip.</span><span class="sxs-lookup"><span data-stu-id="c89ab-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="c89ab-115">A [ayarlamak](../../../csharp/language-reference/keywords/set.md) örtük özellik erişimcisi içeren `value` parametresi.</span><span class="sxs-lookup"><span data-stu-id="c89ab-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="c89ab-116">A `set` bir dizin oluşturucu erişimcisine sahip aynı biçimsel parametre listesi dizin oluşturucu olarak yanı sıra [değer](../../../csharp/language-reference/keywords/value.md) parametresi.</span><span class="sxs-lookup"><span data-stu-id="c89ab-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="c89ab-117">Destekler kısaltılmış sözdizimi ile [Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c89ab-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="c89ab-118">Kısaltılmış sözdizimi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c89ab-118">Does not support shortened syntax.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c89ab-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c89ab-119">See also</span></span>

- [<span data-ttu-id="c89ab-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c89ab-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c89ab-121">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="c89ab-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="c89ab-122">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c89ab-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
