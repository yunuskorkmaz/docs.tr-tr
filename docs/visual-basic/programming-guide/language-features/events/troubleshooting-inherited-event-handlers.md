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
ms.openlocfilehash: fd2ef1c25233cc1eaad6bcde68923688393b471d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345102"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="90773-102">Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="90773-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="90773-103">Bu konuda, devralınan bileşenlerde olay işleyicileriyle ortaya çıkan yaygın sorunlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="90773-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="90773-104">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="90773-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="90773-105">Olay Işleyicisindeki kod her çağrı için Iki kez yürütülür</span><span class="sxs-lookup"><span data-stu-id="90773-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="90773-106">Devralınan olay işleyicisi bir [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="90773-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="90773-107">Temel sınıftaki yöntemi, olayla zaten ilişkilendirilmiş ve uygun şekilde harekete geçmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="90773-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="90773-108">Devralınan yöntemden `Handles` yan tümcesini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="90773-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="90773-109">Devralınan yöntemin bir `Handles` anahtar sözcüğü yoksa, kodunuzun ek bir [AddHandler bildirisi](../../../../visual-basic/language-reference/statements/addhandler-statement.md) veya aynı olayı işleyen başka yöntemler içermediğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="90773-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90773-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90773-110">See also</span></span>

- [<span data-ttu-id="90773-111">Olaylar</span><span class="sxs-lookup"><span data-stu-id="90773-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
