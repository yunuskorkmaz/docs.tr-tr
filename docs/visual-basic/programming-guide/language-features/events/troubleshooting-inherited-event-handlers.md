---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic devralınan olay Işleyicilerinin sorunlarını giderme'
title: Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: b489b6c85510bb942b403a508b6bbe232c3e1853
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424482"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="769c9-103">Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="769c9-103">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>

<span data-ttu-id="769c9-104">Bu konuda, devralınan bileşenlerde olay işleyicileriyle ortaya çıkan yaygın sorunlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="769c9-104">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="769c9-105">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="769c9-105">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="769c9-106">Olay Işleyicisindeki kod her çağrı için Iki kez yürütülür</span><span class="sxs-lookup"><span data-stu-id="769c9-106">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="769c9-107">Devralınan olay işleyicisi bir [Handles](../../../language-reference/statements/handles-clause.md) yan tümcesi içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="769c9-107">An inherited event handler must not include a [Handles](../../../language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="769c9-108">Temel sınıftaki yöntemi, olayla zaten ilişkilendirilmiş ve uygun şekilde harekete geçmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="769c9-108">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="769c9-109">`Handles`Devralınan yöntemden yan tümceyi kaldırın.</span><span class="sxs-lookup"><span data-stu-id="769c9-109">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="769c9-110">Devralınan yöntemin bir `Handles` anahtar sözcüğü yoksa, kodunuzun bir ek [AddHandler bildirisi](../../../language-reference/statements/addhandler-statement.md) veya aynı olayı işleyen başka yöntemler içermediğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="769c9-110">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="769c9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="769c9-111">See also</span></span>

- [<span data-ttu-id="769c9-112">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="769c9-112">Events</span></span>](index.md)
