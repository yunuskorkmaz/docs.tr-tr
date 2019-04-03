---
title: "'<expression>' tür kısıtlaması olarak kullanılamaz"
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 8dbf510d7c6ee80e2dcd2f9d2552bc870413cbab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838111"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="43ebc-102">'\<ifadesi >' tür kısıtlaması olarak kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="43ebc-102">'\<expression>' cannot be used as a type constraint</span></span>
<span data-ttu-id="43ebc-103">Bir kısıtlama listesi geçerli bir tür parametresi kısıtlaması göstermiyor bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="43ebc-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="43ebc-104">Tür parametresi için geçirilen tür bağımsız değişkeni gereksinimlerine kısıtlaması listesini uygular.</span><span class="sxs-lookup"><span data-stu-id="43ebc-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="43ebc-105">Herhangi bir bileşimini aşağıdaki gereksinimleri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="43ebc-105">You can specify the following requirements in any combination:</span></span>  
  
-   <span data-ttu-id="43ebc-106">Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır</span><span class="sxs-lookup"><span data-stu-id="43ebc-106">The type argument must implement one or more interfaces</span></span>  
  
-   <span data-ttu-id="43ebc-107">Tür bağımsız değişkeni en fazla bir sınıftan devralmalıdır</span><span class="sxs-lookup"><span data-stu-id="43ebc-107">The type argument must inherit from at most one class</span></span>  
  
-   <span data-ttu-id="43ebc-108">Tür bağımsız değişkeni oluşturma kodunu erişip parametresiz bir oluşturucu kullanıma açmalıdır (dahil `New` kısıtlaması)</span><span class="sxs-lookup"><span data-stu-id="43ebc-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="43ebc-109">Kısıtlama listede herhangi bir belirli bir sınıf veya arabirim eklemezseniz, aşağıdakilerden birini belirterek daha genel bir gereksinim uygulayabilir:</span><span class="sxs-lookup"><span data-stu-id="43ebc-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
-   <span data-ttu-id="43ebc-110">Tür bağımsız değişkeni bir değer türü olmalıdır (dahil `Structure` kısıtlaması)</span><span class="sxs-lookup"><span data-stu-id="43ebc-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
-   <span data-ttu-id="43ebc-111">Tür bağımsız değişkeninin bir başvuru türü olmalıdır (dahil `Class` kısıtlaması)</span><span class="sxs-lookup"><span data-stu-id="43ebc-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="43ebc-112">Her ikisini de belirtemezsiniz `Structure` ve `Class` aynı türünde parametre ve bunlardan birini birden çok kez belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="43ebc-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="43ebc-113">**Hata Kimliği:** BC32061</span><span class="sxs-lookup"><span data-stu-id="43ebc-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="43ebc-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="43ebc-114">To correct this error</span></span>  
  
-   <span data-ttu-id="43ebc-115">İfade ve onun öğelerine doğru yazdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="43ebc-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
-   <span data-ttu-id="43ebc-116">İfade önceki gereksinimleri listesi için uymuyorsa kısıtlama listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="43ebc-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
-   <span data-ttu-id="43ebc-117">İfade bir arabirimin veya sınıfın başvuruyorsa, derleyici bu arabirimin veya sınıfın erişimi olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="43ebc-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="43ebc-118">Adıyla nitelemeniz gerekebilir ve projenize bir başvuru eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="43ebc-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="43ebc-119">Daha fazla bilgi için bkz: "Projeler için başvurular" [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="43ebc-119">For more information, see "References to Projects" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ebc-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43ebc-120">See also</span></span>

- [<span data-ttu-id="43ebc-121">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="43ebc-121">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="43ebc-122">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="43ebc-122">Value Types and Reference Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="43ebc-123">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="43ebc-123">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
