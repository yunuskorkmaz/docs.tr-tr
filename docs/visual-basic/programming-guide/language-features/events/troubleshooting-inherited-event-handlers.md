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
ms.openlocfilehash: f2ddef64ca02ca7c96c6c906f5ee79e3cf99dece
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64604056"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="890c8-102">Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="890c8-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="890c8-103">Bu konuda, devralınan bileşenler olay işleyicileri ile ortaya genel sorunları listelemektedir.</span><span class="sxs-lookup"><span data-stu-id="890c8-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="890c8-104">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="890c8-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="890c8-105">İki kez her çağrı için olay işleyicisinde kodu yürütür</span><span class="sxs-lookup"><span data-stu-id="890c8-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="890c8-106">Devralınan bir olay işleyicisi içermemelidir bir [işleme](../../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="890c8-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="890c8-107">Yöntem temel sınıfta zaten olayla ilişkili ve buna göre ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="890c8-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="890c8-108">Kaldırma `Handles` devralınan yöntemi from yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="890c8-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="890c8-109">Devralınan yöntemi yoksa bir `Handles` anahtar sözcüğü, ek kod içermediğinden emin olun [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md) veya aynı olay işleyen ek yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="890c8-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="890c8-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="890c8-110">See also</span></span>

- [<span data-ttu-id="890c8-111">Olaylar</span><span class="sxs-lookup"><span data-stu-id="890c8-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
