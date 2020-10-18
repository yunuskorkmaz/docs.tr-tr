---
title: İsteğe bağlı parametre türleri olarak kullanılan genel parametreler üzerinde sınıf kısıtlaması olmalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 5e0d4eaf7557eb9a544a8845299f3d69dbb78486
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163226"
---
# <a name="bc32124-generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="550df-102">BC32124: isteğe bağlı parametre türleri olarak kullanılan genel parametreler sınıf kısıtlı olmalıdır</span><span class="sxs-lookup"><span data-stu-id="550df-102">BC32124: Generic parameters used as optional parameter types must be class constrained</span></span>

<span data-ttu-id="550df-103">Bir yordam, bir başvuru türü olarak kısıtlanmış olmayan bir tür parametresi kullanan isteğe bağlı bir parametreyle bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="550df-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>

 <span data-ttu-id="550df-104">Her isteğe bağlı parametre için her zaman bir varsayılan değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="550df-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="550df-105">Parametresi bir başvuru türü ise, isteğe bağlı değer `Nothing` , herhangi bir başvuru türü için geçerli bir değer olan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="550df-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="550df-106">Ancak, parametre bir değer türünde ise, bu tür Visual Basic tarafından önceden tanımlanan bir elemensel veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="550df-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="550df-107">Bunun nedeni, Kullanıcı tanımlı yapı gibi bir bileşik değer türünün geçerli bir varsayılan değer içermez.</span><span class="sxs-lookup"><span data-stu-id="550df-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>

 <span data-ttu-id="550df-108">İsteğe bağlı bir parametre için bir tür parametresi kullandığınızda, geçerli bir varsayılan değer olmadan bir değer türü olasılığa engel olmak için bir başvuru türü olduğunu garanti etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="550df-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="550df-109">Bu, tür parametresini `Class` anahtar sözcüğüyle veya belirli bir sınıfın adıyla sınırlandırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="550df-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>

 <span data-ttu-id="550df-110">**Hata kimliği:** BC32124</span><span class="sxs-lookup"><span data-stu-id="550df-110">**Error ID:** BC32124</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="550df-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="550df-111">To correct this error</span></span>

- <span data-ttu-id="550df-112">Tür parametresini yalnızca bir başvuru türünü kabul edecek şekilde sınırlayın veya isteğe bağlı parametre için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="550df-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="550df-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="550df-113">See also</span></span>

- [<span data-ttu-id="550df-114">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="550df-114">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="550df-115">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="550df-115">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="550df-116">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="550df-116">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="550df-117">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="550df-117">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="550df-118">Yapılar</span><span class="sxs-lookup"><span data-stu-id="550df-118">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="550df-119">Yapma</span><span class="sxs-lookup"><span data-stu-id="550df-119">Nothing</span></span>](../nothing.md)
