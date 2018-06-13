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
ms.openlocfilehash: c7037acac58de56a396bd89f595ef897743ff4e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595085"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="368ac-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="368ac-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="368ac-103">Visual Basic Amerikan Ulusal Standartlar Enstitüsü (ANSI) değerleri bildirilen dış yordamın adını bağımsız olarak tüm dizeleri sıralama belirtir.</span><span class="sxs-lookup"><span data-stu-id="368ac-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="368ac-104">Projenizin dışında tanımlı bir yordam çağrısı, Visual Basic derleyici yordamı doğru çağırmak gereken bilgilere erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="368ac-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="368ac-105">Bu bilgiler yordamı bulunduğu, nasıl tanımlanır, kendi arama sırası ve dönüş türü içerir ve dize karakter kullanır ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="368ac-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="368ac-106">[Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md) dış bir yordam için bir başvuru oluşturur ve bu gerekli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="368ac-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="368ac-107">`charsetmodifier` Bölümün `Declare` deyimi dış yordamı yapılan bir çağrı sırasında dizeleri sıralama için karakter kümesi bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="368ac-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="368ac-108">Visual Basic dış yordamı adı için dış dosyasını nasıl arayacağını etkiler.</span><span class="sxs-lookup"><span data-stu-id="368ac-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="368ac-109">`Ansi` Değiştiricisi, Visual Basic ANSI değerleri tüm dizeleri sıralama ve yordam arama sırasında adını değiştirmeden görünmelidir belirtir.</span><span class="sxs-lookup"><span data-stu-id="368ac-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="368ac-110">Herhangi bir karakter kümesi değiştiricisi belirtilirse, `Ansi` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="368ac-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="368ac-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="368ac-111">Remarks</span></span>  
 <span data-ttu-id="368ac-112">`Ansi` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="368ac-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="368ac-113">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="368ac-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="368ac-114">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="368ac-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="368ac-115">Bu anahtar sözcük desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="368ac-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="368ac-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="368ac-116">See Also</span></span>  
 [<span data-ttu-id="368ac-117">Auto</span><span class="sxs-lookup"><span data-stu-id="368ac-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="368ac-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="368ac-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="368ac-119">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="368ac-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
