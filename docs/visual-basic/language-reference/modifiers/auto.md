---
title: Otomatik (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: e4beb320b3aa0cadb790dd3ab92255496bc32f05
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843844"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="7281b-102">Otomatik (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7281b-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="7281b-103">Visual Basic dizeleri dış bildirilen dış yordam adına göre .NET Framework kurallarına göre sıralaması olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7281b-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="7281b-104">Projenizin dışında tanımlı bir yordamı çağırdığınızda, Visual Basic Derleyicisi yordamı doğru şekilde çağrılacak olmalıdır bilgilere erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="7281b-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="7281b-105">Bu bilgileri yordamı bulunduğu, nasıl tanımlandığını, çağrı sırası ve dönüş türü içeren ve isteğe bağlı olarak dize karakteri kullanır ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7281b-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="7281b-106">[Declare Deyimi'nin](../../../visual-basic/language-reference/statements/declare-statement.md) bir dış yordam bir başvuru oluşturur ve bu gerekli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7281b-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="7281b-107">`charsetmodifier` Kısmını `Declare` deyimi bir dış yordam çağrısı sırasında dizelerini hazırlama için karakter kümesi bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7281b-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="7281b-108">Ayrıca, Visual Basic dış dosya için dış yordam adının nasıl arama etkiler.</span><span class="sxs-lookup"><span data-stu-id="7281b-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="7281b-109">`Auto` Değiştiricisi, Visual Basic dizeleri .NET Framework kurallarına göre sıralaması ve ilk arama yaparsanız ve büyük olasılıkla çalışma zamanı platformunun temel karakter belirlemelisiniz, dış yordam adının değiştirilmesi gerektiğini belirtir başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="7281b-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="7281b-110">Daha fazla bilgi için bkz: "Karakter kümesi" [Declare Deyimi'nin](../../../visual-basic/language-reference/statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7281b-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="7281b-111">Herhangi bir karakter kümesi değiştiricisi belirtilmişse `Ansi` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="7281b-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7281b-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7281b-112">Remarks</span></span>  
 <span data-ttu-id="7281b-113">`Auto` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="7281b-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="7281b-114">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="7281b-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="7281b-115">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="7281b-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="7281b-116">Bu anahtar sözcük desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="7281b-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7281b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7281b-117">See also</span></span>

- [<span data-ttu-id="7281b-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="7281b-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="7281b-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="7281b-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="7281b-120">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="7281b-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
