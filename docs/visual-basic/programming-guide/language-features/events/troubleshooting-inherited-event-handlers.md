---
title: "Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0e8f0b669566bbee6530931bfba9808fad0c085
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="2a22d-102">Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="2a22d-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="2a22d-103">Bu konu, devralınan bileşenleri olay işleyicileri ile ortaya çıkan ortak sorunları listeler.</span><span class="sxs-lookup"><span data-stu-id="2a22d-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="2a22d-104">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="2a22d-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="2a22d-105">İki kez yapılan her çağrı için olay işleyicisini kodu çalıştırır</span><span class="sxs-lookup"><span data-stu-id="2a22d-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="2a22d-106">Devralınmış olay işleyicisi içermemelidir bir [işler](../../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="2a22d-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="2a22d-107">Taban sınıf yönteminde zaten olayla ilişkili ve buna göre ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="2a22d-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="2a22d-108">Kaldırma `Handles` devralınan yöntemi from yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="2a22d-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   <span data-ttu-id="2a22d-109">Devralınan yöntemi yoksa bir `Handles` anahtar sözcüğü, kodunuzu fazladan içermediğinden olup [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md) veya aynı olayı işleyen ek yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="2a22d-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a22d-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a22d-110">See Also</span></span>  
 [<span data-ttu-id="2a22d-111">Olayları</span><span class="sxs-lookup"><span data-stu-id="2a22d-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
