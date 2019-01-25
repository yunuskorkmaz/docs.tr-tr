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
ms.openlocfilehash: e7c56757d18a22a65b4ef8e81d2a05e5f4f4dffc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680211"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="8c2d9-102">Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="8c2d9-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="8c2d9-103">Bu konuda, devralınan bileşenler olay işleyicileri ile ortaya genel sorunları listelemektedir.</span><span class="sxs-lookup"><span data-stu-id="8c2d9-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="8c2d9-104">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8c2d9-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="8c2d9-105">İki kez her çağrı için olay işleyicisinde kodu yürütür</span><span class="sxs-lookup"><span data-stu-id="8c2d9-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="8c2d9-106">Devralınan bir olay işleyicisi içermemelidir bir [işleme](../../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8c2d9-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="8c2d9-107">Yöntem temel sınıfta zaten olayla ilişkili ve buna göre ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="8c2d9-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="8c2d9-108">Kaldırma `Handles` devralınan yöntemi from yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8c2d9-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   <span data-ttu-id="8c2d9-109">Devralınan yöntemi yoksa bir `Handles` anahtar sözcüğü, ek kod içermediğinden emin olun [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md) veya aynı olay işleyen ek yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="8c2d9-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c2d9-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c2d9-110">See also</span></span>
- [<span data-ttu-id="8c2d9-111">Olaylar</span><span class="sxs-lookup"><span data-stu-id="8c2d9-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
