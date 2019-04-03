---
title: İsteğe bağlı parametre türleri olarak kullanılan genel parametreler üzerinde sınıf kısıtlaması olmalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 9b0293472f5eda74c2bf8fb215e15ae5cf8d8b98
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813905"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="215e0-102">İsteğe bağlı parametre türleri olarak kullanılan genel parametreler üzerinde sınıf kısıtlaması olmalıdır</span><span class="sxs-lookup"><span data-stu-id="215e0-102">Generic parameters used as optional parameter types must be class constrained</span></span>
<span data-ttu-id="215e0-103">Bir yordam kullanan bir başvuru türü olması zorunlu değildir bir tür parametresi isteğe bağlı bir parametre ile bildirilir.</span><span class="sxs-lookup"><span data-stu-id="215e0-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>  
  
 <span data-ttu-id="215e0-104">Her zaman isteğe bağlı her parametre için varsayılan bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="215e0-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="215e0-105">Parametre bir başvuru türü ise isteğe bağlı bir değer olmalıdır `Nothing`, herhangi bir başvuru türü için geçerli bir değer olduğu.</span><span class="sxs-lookup"><span data-stu-id="215e0-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="215e0-106">Ancak, parametre bir değer türü ise, bu tür Visual Basic tarafından önceden tanımlanmış bir başlangıç veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="215e0-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="215e0-107">Kullanıcı tanımlı bir yapısı gibi bir bileşik değer türü, geçerli varsayılan değere sahip olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="215e0-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>  
  
 <span data-ttu-id="215e0-108">İsteğe bağlı bir parametre için bir tür parametresini kullandığınızda, geçerli varsayılan değer içermeyen bir değer türü olasılığını önlemek için başvuru türünde olduğunu garanti etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="215e0-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="215e0-109">Yani, gerekir sınırlamak tür parametresi ile `Class` anahtar sözcüğü veya belirli bir sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="215e0-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>  
  
 <span data-ttu-id="215e0-110">**Hata Kimliği:** BC32124</span><span class="sxs-lookup"><span data-stu-id="215e0-110">**Error ID:** BC32124</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="215e0-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="215e0-111">To correct this error</span></span>  
  
-   <span data-ttu-id="215e0-112">Tür parametresi yalnızca bir başvuru türü kabul edecek şekilde sınırlamak veya isteğe bağlı parametresi için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="215e0-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215e0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="215e0-113">See also</span></span>

- [<span data-ttu-id="215e0-114">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="215e0-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="215e0-115">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="215e0-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="215e0-116">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="215e0-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="215e0-117">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="215e0-117">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="215e0-118">Yapılar</span><span class="sxs-lookup"><span data-stu-id="215e0-118">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="215e0-119">Nothing</span><span class="sxs-lookup"><span data-stu-id="215e0-119">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
