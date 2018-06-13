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
ms.openlocfilehash: f6355cf7fc2e43651c1112d048220a8179968c76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646340"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="ec512-102">Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="ec512-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="ec512-103">Bu konu, devralınan bileşenleri olay işleyicileri ile ortaya çıkan ortak sorunları listeler.</span><span class="sxs-lookup"><span data-stu-id="ec512-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="ec512-104">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ec512-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="ec512-105">İki kez yapılan her çağrı için olay işleyicisini kodu çalıştırır</span><span class="sxs-lookup"><span data-stu-id="ec512-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="ec512-106">Devralınmış olay işleyicisi içermemelidir bir [işler](../../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ec512-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="ec512-107">Taban sınıf yönteminde zaten olayla ilişkili ve buna göre ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="ec512-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="ec512-108">Kaldırma `Handles` devralınan yöntemi from yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ec512-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   <span data-ttu-id="ec512-109">Devralınan yöntemi yoksa bir `Handles` anahtar sözcüğü, kodunuzu fazladan içermediğinden olup [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md) veya aynı olayı işleyen ek yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="ec512-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec512-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec512-110">See Also</span></span>  
 [<span data-ttu-id="ec512-111">Olaylar</span><span class="sxs-lookup"><span data-stu-id="ec512-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
