---
title: Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: 91bded2f1249bfcbeeca28419ee9bcec819babf6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965430"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="14686-102">Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="14686-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="14686-103">Bu konuda, devralınan bileşenler olay işleyicileri ile ortaya genel sorunları listelemektedir.</span><span class="sxs-lookup"><span data-stu-id="14686-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="14686-104">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="14686-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="14686-105">İki kez her çağrı için olay işleyicisinde kodu yürütür</span><span class="sxs-lookup"><span data-stu-id="14686-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="14686-106">Devralınan bir olay işleyicisi içermemelidir bir [işleme](../../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="14686-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="14686-107">Yöntem temel sınıfta zaten olayla ilişkili ve buna göre ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="14686-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="14686-108">Kaldırma `Handles` devralınan yöntemi from yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="14686-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
-   <span data-ttu-id="14686-109">Devralınan yöntemi yoksa bir `Handles` anahtar sözcüğü, ek kod içermediğinden emin olun [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md) veya aynı olay işleyen ek yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="14686-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14686-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14686-110">See also</span></span>
- [<span data-ttu-id="14686-111">Olaylar</span><span class="sxs-lookup"><span data-stu-id="14686-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
