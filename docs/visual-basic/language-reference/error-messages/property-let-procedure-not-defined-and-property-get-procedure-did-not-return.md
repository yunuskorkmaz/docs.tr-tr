---
description: 'Hakkında daha fazla bilgi edinin: Özellik Let yordamı tanımlı değil ve Get yordamı bir nesne döndürmedi'
title: Özelliğin Let yordamı tanımlı değil ve Get yordamı bir nesne döndürmedi
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: 8376a30abb476abb1d45973e36eb086cadad0054
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795371"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a><span data-ttu-id="9e1cb-103">Özelliğin Let yordamı tanımlı değil ve Get yordamı bir nesne döndürmedi</span><span class="sxs-lookup"><span data-stu-id="9e1cb-103">Property let procedure not defined and property get procedure did not return an object</span></span>

<span data-ttu-id="9e1cb-104">Belirli özellikler, Yöntemler ve işlemler yalnızca nesneler için geçerlidir `Collection` .</span><span class="sxs-lookup"><span data-stu-id="9e1cb-104">Certain properties, methods, and operations can only apply to `Collection` objects.</span></span> <span data-ttu-id="9e1cb-105">Koleksiyonlar için özel bir işlem veya özellik belirttiniz, ancak nesne bir koleksiyon değil.</span><span class="sxs-lookup"><span data-stu-id="9e1cb-105">You specified an operation or property that is exclusive to collections, but the object is not a collection.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9e1cb-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9e1cb-106">To correct this error</span></span>  
  
1. <span data-ttu-id="9e1cb-107">Nesnenin veya özellik adının yazımını denetleyin ya da nesnenin bir nesne olduğunu doğrulayın `Collection` .</span><span class="sxs-lookup"><span data-stu-id="9e1cb-107">Check the spelling of the object or property name, or verify that the object is a `Collection` object.</span></span>  
  
2. <span data-ttu-id="9e1cb-108">`Add`Sözdiziminin doğru olduğundan ve tanımlayıcıların doğru yazıldığından emin olmak için nesneyi koleksiyona eklemek için kullanılan yöntemine bakın.</span><span class="sxs-lookup"><span data-stu-id="9e1cb-108">Look at the `Add` method used to add the object to the collection to be sure the syntax is correct and that any identifiers were spelled correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e1cb-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e1cb-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Collection>
