---
title: Nesne başharflerini kullanarak nesneleri başlatma - C# Programlama Kılavuzu
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: a2ecc9df211d0082bd4b413653e374758c877abc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705593"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="69e3d-102">Nesne başharfi (C# Programlama Kılavuzu) kullanarak nesneleri başlatma</span><span class="sxs-lookup"><span data-stu-id="69e3d-102">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="69e3d-103">Tür için açıkça bir oluşturucu çağırmadan, tür nesnelerini açıklayıcı bir şekilde başlatmak için nesne başharflerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69e3d-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="69e3d-104">Aşağıdaki örnekler, adlandırılmış nesnelerle nesne baş harflerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="69e3d-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="69e3d-105">Derleyici, önce varsayılan örnek oluşturucuya erişerek ve daha sonra üye başlatmaişlemlerini işleyerek nesne başlatılmasını işler.</span><span class="sxs-lookup"><span data-stu-id="69e3d-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="69e3d-106">Bu nedenle, parametresiz oluşturucu `private` sınıfta olduğu gibi bildirilirse, ortak erişim gerektiren nesne baş harfleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="69e3d-106">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="69e3d-107">Anonim bir tür tanımlıyorsanız, nesne baş harflerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="69e3d-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="69e3d-108">Daha fazla bilgi için, [sorgudaki öğe özelliklerialt kümelerini nasıl döndürürsünüz](how-to-return-subsets-of-element-properties-in-a-query.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="69e3d-108">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69e3d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="69e3d-109">Example</span></span>  

<span data-ttu-id="69e3d-110">Aşağıdaki örnek, nesne başharflerini `StudentName` kullanarak yeni bir türün nasıl baş harfe çarptırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="69e3d-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="69e3d-111">Bu örnek, `StudentName` türözellikleri ayarlar:</span><span class="sxs-lookup"><span data-stu-id="69e3d-111">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="69e3d-112">Nesne baş harfleri bir nesnedeki dizinleyicileri ayarlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="69e3d-112">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="69e3d-113">Aşağıdaki örnek, oyuncuları `BaseballTeam` farklı konumlara almak ve ayarlamak için dizinleyici kullanan bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="69e3d-113">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="69e3d-114">Baş harf, pozisyonun kısaltması veya her pozisyon beyzbol karneleri için kullanılan sayıya bağlı olarak oyuncu atayabilir:</span><span class="sxs-lookup"><span data-stu-id="69e3d-114">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="69e3d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69e3d-115">See also</span></span>

- [<span data-ttu-id="69e3d-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="69e3d-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="69e3d-117">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="69e3d-117">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
