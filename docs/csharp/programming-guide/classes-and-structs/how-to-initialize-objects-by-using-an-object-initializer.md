---
title: 'Nasıl yapılır: Bir nesneyi kullanarak nesneleri başlatma Başlatıcı - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 29987b9ba1f1f18f4e768766bd2391ebb5862f97
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084881"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="7e9de-102">Nasıl yapılır: Bir nesne Başlatıcı kullanarak nesneleri başlatma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7e9de-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>

<span data-ttu-id="7e9de-103">Nesne başlatıcıları türü nesne türü için bir oluşturucu açıkça çağırmadan bildirim temelli bir şekilde başlatmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e9de-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="7e9de-104">Aşağıdaki örnekler, adlandırılmış nesneleriyle nesne başlatıcıları kullanın gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7e9de-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="7e9de-105">Derleyici işlemleri başlatıcılar nesne ilk varsayılan örnek oluşturucusu erişme ve sonra üye başlatmalar işleme.</span><span class="sxs-lookup"><span data-stu-id="7e9de-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="7e9de-106">Bu nedenle, varsayılan oluşturucu olarak bildirilirse `private` sınıfında genel erişim gerektiren bir nesne başlatıcıları başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="7e9de-106">Therefore, if the default constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="7e9de-107">Anonim bir tür tanımlıyorsanız, bir nesne Başlatıcı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e9de-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="7e9de-108">Daha fazla bilgi için [nasıl yapılır: Bir sorguda öğe özelliklerinin alt kümelerini dönüş](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="7e9de-108">For more information, see [How to: Return Subsets of Element Properties in a Query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e9de-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e9de-109">Example</span></span>  

<span data-ttu-id="7e9de-110">Aşağıdaki örnek, yeni bir başlatma işlemi gösterilmektedir `StudentName` nesne başlatıcıları kullanarak türü.</span><span class="sxs-lookup"><span data-stu-id="7e9de-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="7e9de-111">Bu örnekte'nın özelliklerini ayarlar `StudentName` türü:</span><span class="sxs-lookup"><span data-stu-id="7e9de-111">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp-interactive[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="7e9de-112">Nesne başlatıcıları, bir nesne içinde dizin oluşturucular ayarlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7e9de-112">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="7e9de-113">Aşağıdaki örnekte tanımlayan bir `BaseballTeam` almak ve farklı konumlar oyuncuların ayarlamak için bir dizin oluşturucu kullanan sınıf.</span><span class="sxs-lookup"><span data-stu-id="7e9de-113">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="7e9de-114">Başlatıcı konumu kısaltması göre oyuncuları ya da her konum Beyzbol karneleri için kullanılan sayıyı atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7e9de-114">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp-interactive[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="7e9de-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e9de-115">See Also</span></span>

- [<span data-ttu-id="7e9de-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7e9de-116">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="7e9de-117">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="7e9de-117">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
