---
title: Özellikler ve dizin oluşturucular - arasında karşılaştırma C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 053eb7ee0fe9333f049e5b4f8a8e709e42aa2119
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53234467"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="66327-102">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="66327-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="66327-103">Dizin oluşturucular gibi özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="66327-103">Indexers are like properties.</span></span> <span data-ttu-id="66327-104">Aşağıdaki tabloda gösterilen farklılıklar dışında özellik erişimcileri için tanımlanan tüm kurallar dizin oluşturucu erişimcileri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="66327-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="66327-105">Özellik</span><span class="sxs-lookup"><span data-stu-id="66327-105">Property</span></span>|<span data-ttu-id="66327-106">Dizin Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="66327-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="66327-107">Ortak veri üyeleri değilmiş gibi çağrılacak yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="66327-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="66327-108">Nesne üzerinde dizi gösterimi kullanılarak erişilecek bir nesnenin iç bir koleksiyonun öğeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="66327-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="66327-109">Basit bir ad erişilir.</span><span class="sxs-lookup"><span data-stu-id="66327-109">Accessed through a simple name.</span></span>|<span data-ttu-id="66327-110">Dizin erişilir.</span><span class="sxs-lookup"><span data-stu-id="66327-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="66327-111">Statik veya örnek üyesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="66327-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="66327-112">Bir örnek üyesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="66327-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="66327-113">A [alma](../../../csharp/language-reference/keywords/get.md) özellik erişimcisi sahip parametre yok.</span><span class="sxs-lookup"><span data-stu-id="66327-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="66327-114">A `get` erişimci bir dizin oluşturucu aynı dizin oluşturucu biçimsel parametre listesine sahip.</span><span class="sxs-lookup"><span data-stu-id="66327-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="66327-115">A [ayarlamak](../../../csharp/language-reference/keywords/set.md) örtük özellik erişimcisi içeren `value` parametresi.</span><span class="sxs-lookup"><span data-stu-id="66327-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="66327-116">A `set` bir dizin oluşturucu erişimcisine sahip aynı biçimsel parametre listesi dizin oluşturucu olarak yanı sıra [değer](../../../csharp/language-reference/keywords/value.md) parametresi.</span><span class="sxs-lookup"><span data-stu-id="66327-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="66327-117">Destekler kısaltılmış sözdizimi ile [Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="66327-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="66327-118">Kısaltılmış sözdizimi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="66327-118">Does not support shortened syntax.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66327-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="66327-119">See Also</span></span>

- [<span data-ttu-id="66327-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="66327-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="66327-121">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="66327-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="66327-122">Özellikler</span><span class="sxs-lookup"><span data-stu-id="66327-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
