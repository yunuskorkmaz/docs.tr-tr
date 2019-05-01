---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 98dafab3e524ea371bba228eb231e28d46cc3b4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802563"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="e9b43-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9b43-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="e9b43-103">Visual Basic Amerikan Ulusal Standartlar Enstitüsü (ANSI) değerleri bildirilen dış yordam adından bağımsız olarak tüm dizeleri sıralaması olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9b43-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="e9b43-104">Projenizin dışında tanımlı bir yordamı çağırdığınızda, Visual Basic Derleyicisi yordamı doğru şekilde çağırmak gereken bilgilere erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="e9b43-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="e9b43-105">Bu bilgileri yordamı bulunduğu, nasıl tanımlandığını, çağrı sırası ve dönüş türü içeren ve isteğe bağlı olarak dize karakteri kullanır ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e9b43-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="e9b43-106">[Declare Deyimi'nin](../../../visual-basic/language-reference/statements/declare-statement.md) bir dış yordam bir başvuru oluşturur ve bu gerekli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9b43-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="e9b43-107">`charsetmodifier` Kısmını `Declare` deyimi bir dış yordam çağrısı sırasında dizelerini hazırlama için karakter kümesi bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9b43-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="e9b43-108">Ayrıca, Visual Basic dış dosya için dış yordam adının nasıl arama etkiler.</span><span class="sxs-lookup"><span data-stu-id="e9b43-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="e9b43-109">`Ansi` Değiştiricisi, Visual Basic tüm dizeleri ANSI değerleri olarak sıralaması ve yordamı arama sırasında adını değiştirmeden araması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9b43-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="e9b43-110">Herhangi bir karakter kümesi değiştiricisi belirtilmişse `Ansi` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e9b43-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9b43-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9b43-111">Remarks</span></span>  
 <span data-ttu-id="e9b43-112">`Ansi` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e9b43-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="e9b43-113">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="e9b43-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="e9b43-114">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="e9b43-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="e9b43-115">Bu anahtar sözcük desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e9b43-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9b43-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9b43-116">See also</span></span>

- [<span data-ttu-id="e9b43-117">Auto</span><span class="sxs-lookup"><span data-stu-id="e9b43-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="e9b43-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="e9b43-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="e9b43-119">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e9b43-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
