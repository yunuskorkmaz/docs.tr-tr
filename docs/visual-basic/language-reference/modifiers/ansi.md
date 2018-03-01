---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa5724eb9123b2776c3a579e4244c55b3129816b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="a9c4e-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9c4e-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="a9c4e-103">Visual Basic Amerikan Ulusal Standartlar Enstitüsü (ANSI) değerleri bildirilen dış yordamın adını bağımsız olarak tüm dizeleri sıralama belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9c4e-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="a9c4e-104">Projenizin dışında tanımlı bir yordam çağrısı, Visual Basic derleyici yordamı doğru çağırmak gereken bilgilere erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="a9c4e-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="a9c4e-105">Bu bilgiler yordamı bulunduğu, nasıl tanımlanır, kendi arama sırası ve dönüş türü içerir ve dize karakter kullanır ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a9c4e-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="a9c4e-106">[Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md) dış bir yordam için bir başvuru oluşturur ve bu gerekli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9c4e-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="a9c4e-107">`charsetmodifier` Bölümün `Declare` deyimi dış yordamı yapılan bir çağrı sırasında dizeleri sıralama için karakter kümesi bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9c4e-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="a9c4e-108">Visual Basic dış yordamı adı için dış dosyasını nasıl arayacağını etkiler.</span><span class="sxs-lookup"><span data-stu-id="a9c4e-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="a9c4e-109">`Ansi` Değiştiricisi, Visual Basic ANSI değerleri tüm dizeleri sıralama ve yordam arama sırasında adını değiştirmeden görünmelidir belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9c4e-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="a9c4e-110">Herhangi bir karakter kümesi değiştiricisi belirtilirse, `Ansi` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a9c4e-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9c4e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9c4e-111">Remarks</span></span>  
 <span data-ttu-id="a9c4e-112">`Ansi` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a9c4e-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="a9c4e-113">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="a9c4e-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="a9c4e-114">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="a9c4e-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="a9c4e-115">Bu anahtar sözcük desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="a9c4e-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c4e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9c4e-116">See Also</span></span>  
 [<span data-ttu-id="a9c4e-117">Otomatik</span><span class="sxs-lookup"><span data-stu-id="a9c4e-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="a9c4e-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="a9c4e-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="a9c4e-119">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="a9c4e-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
