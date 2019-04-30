---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: b3c9452f8d144fb18ea3efcb35b85caed80e8692
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778683"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="9da7a-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9da7a-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="9da7a-103">Visual Basic dizeleri Unicode değerleri bildirilen dış yordam adından bağımsız olarak tüm hazırlama belirtir.</span><span class="sxs-lookup"><span data-stu-id="9da7a-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="9da7a-104">Projenizin dışında tanımlı bir yordamı çağırdığınızda, Visual Basic Derleyicisi yordamı doğru şekilde çağırmak için olmalıdır bilgilere erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="9da7a-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="9da7a-105">Bu bilgileri yordamı bulunduğu, nasıl tanımlandığını, çağrı sırası ve dönüş türü içeren ve isteğe bağlı olarak dize karakteri kullanır ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9da7a-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="9da7a-106">[Declare Deyimi'nin](../../../visual-basic/language-reference/statements/declare-statement.md) bir dış yordam bir başvuru oluşturur ve bu gerekli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9da7a-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="9da7a-107">`charsetmodifier` Kısmını `Declare` deyimi bir dış yordam çağrısı sırasında dizelerini sıralama için karakter kümesi bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9da7a-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="9da7a-108">Ayrıca, Visual Basic dış dosya için dış yordam adının nasıl arama etkiler.</span><span class="sxs-lookup"><span data-stu-id="9da7a-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="9da7a-109">`Unicode` Değiştiricisi, Visual Basic tüm dizeleri Unicode değerleri olarak sıralaması ve yordamı arama sırasında adını değiştirmeden araması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9da7a-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="9da7a-110">Herhangi bir karakter kümesi değiştiricisi belirtilmişse `Ansi` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9da7a-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9da7a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9da7a-111">Remarks</span></span>  
 <span data-ttu-id="9da7a-112">`Unicode` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="9da7a-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="9da7a-113">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="9da7a-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="9da7a-114">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="9da7a-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="9da7a-115">Bu anahtar sözcük desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="9da7a-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da7a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9da7a-116">See also</span></span>

- [<span data-ttu-id="9da7a-117">Ansi</span><span class="sxs-lookup"><span data-stu-id="9da7a-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="9da7a-118">Auto</span><span class="sxs-lookup"><span data-stu-id="9da7a-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="9da7a-119">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9da7a-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
