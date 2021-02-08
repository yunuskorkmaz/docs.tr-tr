---
description: "Hakkında daha fazla bilgi edinin: BC32061: ' <expression> ' tür kısıtlaması olarak kullanılamaz"
title: "'<expression>' tür kısıtlaması olarak kullanılamaz"
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 3484c617b28ed068c917c83454b866f8dd50c5c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796411"
---
# <a name="bc32061-expression-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="1c191-103">BC32061: ' \<expression> ' tür kısıtlaması olarak kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="1c191-103">BC32061: '\<expression>' cannot be used as a type constraint</span></span>

<span data-ttu-id="1c191-104">Kısıtlama listesi, bir tür parametresinde geçerli bir kısıtlamayı temsil eden bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="1c191-104">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>

 <span data-ttu-id="1c191-105">Bir kısıtlama listesi, tür parametresine geçirilen tür bağımsız değişkenine gereksinimleri uygular.</span><span class="sxs-lookup"><span data-stu-id="1c191-105">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="1c191-106">Aşağıdaki gereksinimleri herhangi bir kombinasyonda belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1c191-106">You can specify the following requirements in any combination:</span></span>

- <span data-ttu-id="1c191-107">Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır</span><span class="sxs-lookup"><span data-stu-id="1c191-107">The type argument must implement one or more interfaces</span></span>

- <span data-ttu-id="1c191-108">Tür bağımsız değişkeni en çok bir sınıftan devralması gerekir</span><span class="sxs-lookup"><span data-stu-id="1c191-108">The type argument must inherit from at most one class</span></span>

- <span data-ttu-id="1c191-109">Tür bağımsız değişkeni, oluşturma kodunun erişebileceği parametresiz bir Oluşturucu kullanıma sunmalıdır ( `New` kısıtlamayı dahil)</span><span class="sxs-lookup"><span data-stu-id="1c191-109">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>

 <span data-ttu-id="1c191-110">Kısıtlama listesine belirli bir sınıf veya arabirim eklemezseniz, aşağıdakilerden birini belirterek daha genel bir gereksinim uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1c191-110">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>

- <span data-ttu-id="1c191-111">Tür bağımsız değişkeni bir değer türü olmalıdır ( `Structure` kısıtlamayı dahil)</span><span class="sxs-lookup"><span data-stu-id="1c191-111">The type argument must be a value type (include the `Structure` constraint)</span></span>

- <span data-ttu-id="1c191-112">Tür bağımsız değişkeni bir başvuru türü olmalıdır ( `Class` kısıtlamayı dahil)</span><span class="sxs-lookup"><span data-stu-id="1c191-112">The type argument must be a reference type (include the `Class` constraint)</span></span>

 <span data-ttu-id="1c191-113">`Structure` `Class` Aynı tür parametresi için hem hem de belirtemezsiniz ve birden çok kez belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c191-113">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>

 <span data-ttu-id="1c191-114">**Hata kimliği:** BC32061</span><span class="sxs-lookup"><span data-stu-id="1c191-114">**Error ID:** BC32061</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1c191-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1c191-115">To correct this error</span></span>

- <span data-ttu-id="1c191-116">İfadenin ve öğelerinin doğru yazıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="1c191-116">Verify that the expression and its elements are spelled correctly.</span></span>

- <span data-ttu-id="1c191-117">İfade önceki gereksinimler listesine uygun değilse, kısıtlama listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1c191-117">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>

- <span data-ttu-id="1c191-118">İfade bir arabirime veya sınıfa başvuruyorsa, derleyicinin bu arabirime veya sınıfa erişimi olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="1c191-118">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="1c191-119">Adını nitelemeniz gerekebilir ve projenize bir başvuru eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1c191-119">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="1c191-120">Daha fazla bilgi için, bkz. [belirtilen öğelere başvurularda](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)"projelere başvurular".</span><span class="sxs-lookup"><span data-stu-id="1c191-120">For more information, see "References to Projects" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c191-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c191-121">See also</span></span>

- [<span data-ttu-id="1c191-122">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="1c191-122">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="1c191-123">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="1c191-123">Value Types and Reference Types</span></span>](../../programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="1c191-124">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="1c191-124">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
