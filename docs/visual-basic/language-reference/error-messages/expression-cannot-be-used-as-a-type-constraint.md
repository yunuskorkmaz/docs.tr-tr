---
title: '&#39;&lt;ifade&gt; &#39; tür kısıtlaması olarak kullanılamaz'
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: b7f77c8113f8af113b4c8515994093958970864a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742139"
---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="061ba-102">&#39;&lt;ifade&gt; &#39; tür kısıtlaması olarak kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="061ba-102">&#39;&lt;expression&gt;&#39; cannot be used as a type constraint</span></span>
<span data-ttu-id="061ba-103">Bir kısıtlama listesi geçerli bir tür parametresi kısıtlaması göstermiyor bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="061ba-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="061ba-104">Tür parametresi için geçirilen tür bağımsız değişkeni gereksinimlerine kısıtlaması listesini uygular.</span><span class="sxs-lookup"><span data-stu-id="061ba-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="061ba-105">Herhangi bir bileşimini aşağıdaki gereksinimleri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="061ba-105">You can specify the following requirements in any combination:</span></span>  
  
-   <span data-ttu-id="061ba-106">Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır</span><span class="sxs-lookup"><span data-stu-id="061ba-106">The type argument must implement one or more interfaces</span></span>  
  
-   <span data-ttu-id="061ba-107">Tür bağımsız değişkeni en fazla bir sınıftan devralmalıdır</span><span class="sxs-lookup"><span data-stu-id="061ba-107">The type argument must inherit from at most one class</span></span>  
  
-   <span data-ttu-id="061ba-108">Tür bağımsız değişkeni oluşturma kodunu erişip parametresiz bir oluşturucu kullanıma açmalıdır (dahil `New` kısıtlaması)</span><span class="sxs-lookup"><span data-stu-id="061ba-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="061ba-109">Kısıtlama listede herhangi bir belirli bir sınıf veya arabirim eklemezseniz, aşağıdakilerden birini belirterek daha genel bir gereksinim uygulayabilir:</span><span class="sxs-lookup"><span data-stu-id="061ba-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
-   <span data-ttu-id="061ba-110">Tür bağımsız değişkeni bir değer türü olmalıdır (dahil `Structure` kısıtlaması)</span><span class="sxs-lookup"><span data-stu-id="061ba-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
-   <span data-ttu-id="061ba-111">Tür bağımsız değişkeninin bir başvuru türü olmalıdır (dahil `Class` kısıtlaması)</span><span class="sxs-lookup"><span data-stu-id="061ba-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="061ba-112">Her ikisini de belirtemezsiniz `Structure` ve `Class` aynı türünde parametre ve bunlardan birini birden çok kez belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="061ba-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="061ba-113">**Hata Kimliği:** BC32061</span><span class="sxs-lookup"><span data-stu-id="061ba-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="061ba-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="061ba-114">To correct this error</span></span>  
  
-   <span data-ttu-id="061ba-115">İfade ve onun öğelerine doğru yazdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="061ba-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
-   <span data-ttu-id="061ba-116">İfade önceki gereksinimleri listesi için uymuyorsa kısıtlama listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="061ba-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
-   <span data-ttu-id="061ba-117">İfade bir arabirimin veya sınıfın başvuruyorsa, derleyici bu arabirimin veya sınıfın erişimi olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="061ba-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="061ba-118">Adıyla nitelemeniz gerekebilir ve projenize bir başvuru eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="061ba-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="061ba-119">Daha fazla bilgi için bkz: "Projeler için başvurular" [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="061ba-119">For more information, see "References to Projects" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="061ba-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="061ba-120">See also</span></span>
- [<span data-ttu-id="061ba-121">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="061ba-121">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="061ba-122">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="061ba-122">Value Types and Reference Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="061ba-123">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="061ba-123">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

