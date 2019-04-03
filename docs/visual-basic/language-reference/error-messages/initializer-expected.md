---
title: Başlatıcı bekleniyor
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 77cfeb57bc313ded2d2c4d5a0c59041c5c19f515
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826086"
---
# <a name="initializer-expected"></a><span data-ttu-id="37516-102">Başlatıcı bekleniyor</span><span class="sxs-lookup"><span data-stu-id="37516-102">Initializer expected</span></span>
<span data-ttu-id="37516-103">Başlatma listesi aşağıdaki örnekte gösterildiği gibi boş olduğu bir nesne Başlatıcı kullanarak bir sınıfın örneği bildirin çalıştınız.</span><span class="sxs-lookup"><span data-stu-id="37516-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 <span data-ttu-id="37516-104">En az bir alan veya özellik Başlatıcı listesinde, aşağıdaki örnekte gösterildiği gibi başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="37516-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 <span data-ttu-id="37516-105">**Hata Kimliği:** BC30996</span><span class="sxs-lookup"><span data-stu-id="37516-105">**Error ID:** BC30996</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="37516-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="37516-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="37516-107">En az bir alan veya özellik başlatıcısında başlatmak veya bir nesne Başlatıcı kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="37516-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37516-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37516-108">See also</span></span>

- [<span data-ttu-id="37516-109">Nesne başlatıcıları: Adlandırılmış ve anonim türler</span><span class="sxs-lookup"><span data-stu-id="37516-109">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="37516-110">Nasıl yapılır: Bir nesne Başlatıcı kullanarak nesne bildirme</span><span class="sxs-lookup"><span data-stu-id="37516-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
