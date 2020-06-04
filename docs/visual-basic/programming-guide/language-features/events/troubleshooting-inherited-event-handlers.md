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
ms.openlocfilehash: 4e7bedd1de5197fcf8b69091f4cc878f41b01cd5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405112"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="822cd-102">Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="822cd-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="822cd-103">Bu konuda, devralınan bileşenlerde olay işleyicileriyle ortaya çıkan yaygın sorunlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="822cd-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="822cd-104">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="822cd-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="822cd-105">Olay Işleyicisindeki kod her çağrı için Iki kez yürütülür</span><span class="sxs-lookup"><span data-stu-id="822cd-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="822cd-106">Devralınan olay işleyicisi bir [Handles](../../../language-reference/statements/handles-clause.md) yan tümcesi içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="822cd-106">An inherited event handler must not include a [Handles](../../../language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="822cd-107">Temel sınıftaki yöntemi, olayla zaten ilişkilendirilmiş ve uygun şekilde harekete geçmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="822cd-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="822cd-108">`Handles`Devralınan yöntemden yan tümceyi kaldırın.</span><span class="sxs-lookup"><span data-stu-id="822cd-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="822cd-109">Devralınan yöntemin bir `Handles` anahtar sözcüğü yoksa, kodunuzun bir ek [AddHandler bildirisi](../../../language-reference/statements/addhandler-statement.md) veya aynı olayı işleyen başka yöntemler içermediğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="822cd-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="822cd-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="822cd-110">See also</span></span>

- [<span data-ttu-id="822cd-111">Olaylar</span><span class="sxs-lookup"><span data-stu-id="822cd-111">Events</span></span>](index.md)
