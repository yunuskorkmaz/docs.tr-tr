---
title: "'<expression>' tür kısıtlaması olarak kullanılamaz"
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: e2ba411a5f0db21539a9cf99c7645b8c9309caab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409562"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="05833-102">'\<expression>' tür kısıtlaması olarak kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="05833-102">'\<expression>' cannot be used as a type constraint</span></span>
<span data-ttu-id="05833-103">Kısıtlama listesi, bir tür parametresinde geçerli bir kısıtlamayı temsil eden bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="05833-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="05833-104">Bir kısıtlama listesi, tür parametresine geçirilen tür bağımsız değişkenine gereksinimleri uygular.</span><span class="sxs-lookup"><span data-stu-id="05833-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="05833-105">Aşağıdaki gereksinimleri herhangi bir kombinasyonda belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="05833-105">You can specify the following requirements in any combination:</span></span>  
  
- <span data-ttu-id="05833-106">Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır</span><span class="sxs-lookup"><span data-stu-id="05833-106">The type argument must implement one or more interfaces</span></span>  
  
- <span data-ttu-id="05833-107">Tür bağımsız değişkeni en çok bir sınıftan devralması gerekir</span><span class="sxs-lookup"><span data-stu-id="05833-107">The type argument must inherit from at most one class</span></span>  
  
- <span data-ttu-id="05833-108">Tür bağımsız değişkeni, oluşturma kodunun erişebileceği parametresiz bir Oluşturucu kullanıma sunmalıdır ( `New` kısıtlamayı dahil)</span><span class="sxs-lookup"><span data-stu-id="05833-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="05833-109">Kısıtlama listesine belirli bir sınıf veya arabirim eklemezseniz, aşağıdakilerden birini belirterek daha genel bir gereksinim uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="05833-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
- <span data-ttu-id="05833-110">Tür bağımsız değişkeni bir değer türü olmalıdır ( `Structure` kısıtlamayı dahil)</span><span class="sxs-lookup"><span data-stu-id="05833-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
- <span data-ttu-id="05833-111">Tür bağımsız değişkeni bir başvuru türü olmalıdır ( `Class` kısıtlamayı dahil)</span><span class="sxs-lookup"><span data-stu-id="05833-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="05833-112">`Structure` `Class` Aynı tür parametresi için hem hem de belirtemezsiniz ve birden çok kez belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="05833-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="05833-113">**Hata kimliği:** BC32061</span><span class="sxs-lookup"><span data-stu-id="05833-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="05833-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="05833-114">To correct this error</span></span>  
  
- <span data-ttu-id="05833-115">İfadenin ve öğelerinin doğru yazıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="05833-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
- <span data-ttu-id="05833-116">İfade önceki gereksinimler listesine uygun değilse, kısıtlama listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="05833-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
- <span data-ttu-id="05833-117">İfade bir arabirime veya sınıfa başvuruyorsa, derleyicinin bu arabirime veya sınıfa erişimi olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="05833-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="05833-118">Adını nitelemeniz gerekebilir ve projenize bir başvuru eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="05833-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="05833-119">Daha fazla bilgi için, bkz. [belirtilen öğelere başvurularda](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)"projelere başvurular".</span><span class="sxs-lookup"><span data-stu-id="05833-119">For more information, see "References to Projects" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05833-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05833-120">See also</span></span>

- [<span data-ttu-id="05833-121">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="05833-121">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="05833-122">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="05833-122">Value Types and Reference Types</span></span>](../../programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="05833-123">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="05833-123">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
