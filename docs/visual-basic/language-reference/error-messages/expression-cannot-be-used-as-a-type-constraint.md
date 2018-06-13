---
title: '&#39;&lt;ifade&gt; &#39; tür sınırlaması kullanılamaz'
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 8e9aad2ec65e037b15e19ca2e624fdc8f28bc94e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588180"
---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="90f1e-102">&#39;&lt;ifade&gt; &#39; tür sınırlaması kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="90f1e-102">&#39;&lt;expression&gt;&#39; cannot be used as a type constraint</span></span>
<span data-ttu-id="90f1e-103">Bir kısıtlama listesi bir tür parametresi geçerli bir kısıtlaması göstermiyor bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="90f1e-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="90f1e-104">Kısıtlama listesini türü parametresine geçirilen tür bağımsız değişkeni gereksinimlerine uygular.</span><span class="sxs-lookup"><span data-stu-id="90f1e-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="90f1e-105">Aşağıdaki gereksinimleri herhangi bir bileşimini belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="90f1e-105">You can specify the following requirements in any combination:</span></span>  
  
-   <span data-ttu-id="90f1e-106">Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır</span><span class="sxs-lookup"><span data-stu-id="90f1e-106">The type argument must implement one or more interfaces</span></span>  
  
-   <span data-ttu-id="90f1e-107">Tür bağımsız değişkeni en fazla bir sınıftan gerekir</span><span class="sxs-lookup"><span data-stu-id="90f1e-107">The type argument must inherit from at most one class</span></span>  
  
-   <span data-ttu-id="90f1e-108">Tür bağımsız değişkeni oluşturma kodu erişebilirsiniz parametresiz bir kurucusu kullanıma gerekir (dahil `New` kısıtlaması)</span><span class="sxs-lookup"><span data-stu-id="90f1e-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="90f1e-109">Kısıtlama listesinde herhangi bir belirli bir sınıf veya arabirim içermiyorsa, aşağıdakilerden birini belirterek daha genel bir gereksinim uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="90f1e-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
-   <span data-ttu-id="90f1e-110">Tür bağımsız değişkeni bir değer türü olması gerekir (dahil `Structure` kısıtlaması)</span><span class="sxs-lookup"><span data-stu-id="90f1e-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
-   <span data-ttu-id="90f1e-111">Tür bağımsız değişkeni bir başvuru türü olmalıdır (dahil `Class` kısıtlaması)</span><span class="sxs-lookup"><span data-stu-id="90f1e-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="90f1e-112">Her ikisini birden belirtemezsiniz `Structure` ve `Class` aynı tür için parametre ve bunlardan birini birden çok kez belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="90f1e-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="90f1e-113">**Hata Kimliği:** BC32061</span><span class="sxs-lookup"><span data-stu-id="90f1e-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="90f1e-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="90f1e-114">To correct this error</span></span>  
  
-   <span data-ttu-id="90f1e-115">İfade ve öğeleri doğru yazdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="90f1e-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
-   <span data-ttu-id="90f1e-116">İfade önceki gereksinimlerinin listesi için uygun değilse, kısıtlama listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="90f1e-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
-   <span data-ttu-id="90f1e-117">İfade bir arabirim ya da sınıf başvuruyorsa, derleyici bu arabirimi veya sınıf erişimi olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="90f1e-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="90f1e-118">Projeniz için bir başvuru eklemeniz gerekebilir ve adını nitelemek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="90f1e-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="90f1e-119">Daha fazla bilgi için bkz: "Projeleri başvuruları" [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="90f1e-119">For more information, see "References to Projects" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f1e-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="90f1e-120">See Also</span></span>  
 [<span data-ttu-id="90f1e-121">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="90f1e-121">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="90f1e-122">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="90f1e-122">Value Types and Reference Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="90f1e-123">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="90f1e-123">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 
