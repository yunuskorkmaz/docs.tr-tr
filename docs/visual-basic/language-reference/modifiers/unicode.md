---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 042908b8427de2de0de96bbb32df7be018bb915c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="5f673-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f673-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="5f673-103">Visual Basic Unicode değerleri bildirilen dış yordamın adını bağımsız olarak tüm dizeleri sıralama belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f673-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="5f673-104">Projenizin dışında tanımlı bir yordam çağrısı, Visual Basic derleyici yordamı doğru çağırmak için içermelidir bilgilere erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="5f673-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="5f673-105">Bu bilgiler yordamı bulunduğu, nasıl tanımlanır, kendi arama sırası ve dönüş türü içerir ve dize karakter kullanır ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5f673-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="5f673-106">[Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md) dış bir yordam için bir başvuru oluşturur ve bu gerekli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f673-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="5f673-107">`charsetmodifier` Bölümün `Declare` deyimi dış yordamı yapılan bir çağrı sırasında dizelerini sıralama için karakter kümesi bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f673-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="5f673-108">Visual Basic dış yordamı adı için dış dosyasını nasıl arayacağını etkiler.</span><span class="sxs-lookup"><span data-stu-id="5f673-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="5f673-109">`Unicode` Değiştiricisi, Visual Basic Unicode değerleri tüm dizeleri sıralama ve yordam arama sırasında adını değiştirmeden görünmelidir belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f673-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="5f673-110">Herhangi bir karakter kümesi değiştiricisi belirtilirse, `Ansi` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="5f673-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f673-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f673-111">Remarks</span></span>  
 <span data-ttu-id="5f673-112">`Unicode` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="5f673-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="5f673-113">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="5f673-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="5f673-114">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="5f673-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="5f673-115">Bu anahtar sözcük desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="5f673-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f673-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f673-116">See Also</span></span>  
 [<span data-ttu-id="5f673-117">ANSI</span><span class="sxs-lookup"><span data-stu-id="5f673-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [<span data-ttu-id="5f673-118">Otomatik</span><span class="sxs-lookup"><span data-stu-id="5f673-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="5f673-119">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="5f673-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
