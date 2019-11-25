---
title: Nesne Başlatıcısı kullanarak nesneleri başlatma- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: be555688a645c7689e76b5b4499c44255c18dbc8
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970873"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="4ce4d-102">Nesne Başlatıcısı kullanarak nesneleri başlatma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4ce4d-102">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="4ce4d-103">Tür nesnelerini, tür için açıkça bir Oluşturucu çağırmadan, bildirime dayalı olarak başlatmak için nesne başlatıcıları ' nı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ce4d-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="4ce4d-104">Aşağıdaki örneklerde, adlandırılmış nesneler ile nesne başlatıcılarının nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4ce4d-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="4ce4d-105">Derleyici, önce varsayılan örnek oluşturucusuna erişerek ve sonra üye başlatmaları işleyerek nesne başlatıcıları işler.</span><span class="sxs-lookup"><span data-stu-id="4ce4d-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="4ce4d-106">Bu nedenle, parametresiz Oluşturucu sınıfında `private` olarak bildirilirse, genel erişim gerektiren nesne başlatıcıları başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4ce4d-106">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="4ce4d-107">Anonim bir tür tanımlıyorsanız bir nesne Başlatıcısı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ce4d-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="4ce4d-108">Daha fazla bilgi için bkz. [bir sorgudaki öğe özelliklerinin alt kümelerini döndürme](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="4ce4d-108">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ce4d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ce4d-109">Example</span></span>  

<span data-ttu-id="4ce4d-110">Aşağıdaki örnekte, nesne başlatıcıları kullanarak yeni bir `StudentName` türünün nasıl başlatılacağını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4ce4d-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="4ce4d-111">Bu örnek `StudentName` türündeki özellikleri ayarlar:</span><span class="sxs-lookup"><span data-stu-id="4ce4d-111">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="4ce4d-112">Nesne başlatıcıları, bir nesnedeki Dizin oluşturucuyu ayarlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ce4d-112">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="4ce4d-113">Aşağıdaki örnek, farklı konumlarda oynatıcı almak ve ayarlamak için bir dizin oluşturucu kullanan bir `BaseballTeam` sınıfını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ce4d-113">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="4ce4d-114">Başlatıcı, konum kısaltmasını veya her bir konum için kullanılan her bir konum için kullanılan sayıyı temel alarak oyuncuları atayabilir:</span><span class="sxs-lookup"><span data-stu-id="4ce4d-114">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="4ce4d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ce4d-115">See also</span></span>

- [<span data-ttu-id="4ce4d-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4ce4d-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4ce4d-117">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="4ce4d-117">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
