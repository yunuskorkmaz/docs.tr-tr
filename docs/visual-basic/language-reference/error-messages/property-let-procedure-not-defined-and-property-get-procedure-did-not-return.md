---
title: Özelliğin Let yordamı tanımlı değil ve Get yordamı bir nesne döndürmedi
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: fbeaa224ea9e095f86c37e571492d83bc98b4397
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871090"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a><span data-ttu-id="bccd9-102">Özelliğin Let yordamı tanımlı değil ve Get yordamı bir nesne döndürmedi</span><span class="sxs-lookup"><span data-stu-id="bccd9-102">Property let procedure not defined and property get procedure did not return an object</span></span>

<span data-ttu-id="bccd9-103">Belirli özellikler, Yöntemler ve işlemler yalnızca nesneler için geçerlidir `Collection` .</span><span class="sxs-lookup"><span data-stu-id="bccd9-103">Certain properties, methods, and operations can only apply to `Collection` objects.</span></span> <span data-ttu-id="bccd9-104">Koleksiyonlar için özel bir işlem veya özellik belirttiniz, ancak nesne bir koleksiyon değil.</span><span class="sxs-lookup"><span data-stu-id="bccd9-104">You specified an operation or property that is exclusive to collections, but the object is not a collection.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bccd9-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="bccd9-105">To correct this error</span></span>  
  
1. <span data-ttu-id="bccd9-106">Nesnenin veya özellik adının yazımını denetleyin ya da nesnenin bir nesne olduğunu doğrulayın `Collection` .</span><span class="sxs-lookup"><span data-stu-id="bccd9-106">Check the spelling of the object or property name, or verify that the object is a `Collection` object.</span></span>  
  
2. <span data-ttu-id="bccd9-107">`Add`Sözdiziminin doğru olduğundan ve tanımlayıcıların doğru yazıldığından emin olmak için nesneyi koleksiyona eklemek için kullanılan yöntemine bakın.</span><span class="sxs-lookup"><span data-stu-id="bccd9-107">Look at the `Add` method used to add the object to the collection to be sure the syntax is correct and that any identifiers were spelled correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bccd9-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bccd9-108">See also</span></span>

- <xref:Microsoft.VisualBasic.Collection>
