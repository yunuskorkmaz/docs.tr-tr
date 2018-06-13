---
title: İsteğe bağlı parametre türleri olarak kullanılan genel parametreler üzerinde sınıf kısıtlaması olmalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 7e2b59f758ef236717a912694576b514e2ae8a60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590045"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="93837-102">İsteğe bağlı parametre türleri olarak kullanılan genel parametreler üzerinde sınıf kısıtlaması olmalıdır</span><span class="sxs-lookup"><span data-stu-id="93837-102">Generic parameters used as optional parameter types must be class constrained</span></span>
<span data-ttu-id="93837-103">Bir yordam bir başvuru türü kısıtlı olmayan bir tür parametresi kullanan isteğe bağlı bir parametre ile bildirilir.</span><span class="sxs-lookup"><span data-stu-id="93837-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>  
  
 <span data-ttu-id="93837-104">Her zaman her isteğe bağlı bir parametre için varsayılan bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="93837-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="93837-105">Parametre bir başvuru türü ise, isteğe bağlı değeri olmalıdır `Nothing`, herhangi bir başvuru türü için geçerli bir değer değil.</span><span class="sxs-lookup"><span data-stu-id="93837-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="93837-106">Ancak, parametre değeri türü ise, bu tür Visual Basic tarafından önceden tanımlanmış bir başlangıç veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="93837-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="93837-107">Bir kullanıcı tarafından tanımlanan yapısı gibi bir bileşik değeri türü geçerli varsayılan değere sahip olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="93837-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>  
  
 <span data-ttu-id="93837-108">İsteğe bağlı bir parametre için bir tür parametresi kullandığınızda, geçerli varsayılan bir değeri ile bir değer türü olasılığını önlemek için başvuru türünde olduğunu güvence altına almalıdır.</span><span class="sxs-lookup"><span data-stu-id="93837-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="93837-109">Bu, gerekir sınırlamak tür parametresi ile birlikte gelir `Class` anahtar sözcüğü veya belirli bir sınıf adı.</span><span class="sxs-lookup"><span data-stu-id="93837-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>  
  
 <span data-ttu-id="93837-110">**Hata Kimliği:** BC32124</span><span class="sxs-lookup"><span data-stu-id="93837-110">**Error ID:** BC32124</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="93837-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="93837-111">To correct this error</span></span>  
  
-   <span data-ttu-id="93837-112">Yalnızca bir başvuru türü kabul etmek için tür parametresi sınırlamak veya isteğe bağlı bir parametre için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="93837-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93837-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="93837-113">See Also</span></span>  
 [<span data-ttu-id="93837-114">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="93837-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="93837-115">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="93837-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="93837-116">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="93837-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="93837-117">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="93837-117">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [<span data-ttu-id="93837-118">Yapılar</span><span class="sxs-lookup"><span data-stu-id="93837-118">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="93837-119">Nothing</span><span class="sxs-lookup"><span data-stu-id="93837-119">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
