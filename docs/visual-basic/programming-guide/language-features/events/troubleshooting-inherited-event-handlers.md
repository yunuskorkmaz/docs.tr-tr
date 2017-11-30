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
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme
Bu konu, devralınan bileşenleri olay işleyicileri ile ortaya çıkan ortak sorunları listeler.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>İki kez yapılan her çağrı için olay işleyicisini kodu çalıştırır  
  
-   Devralınmış olay işleyicisi içermemelidir bir [işler](../../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi. Taban sınıf yönteminde zaten olayla ilişkili ve buna göre ateşlenir. Kaldırma `Handles` devralınan yöntemi from yan tümcesi.  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   Devralınan yöntemi yoksa bir `Handles` anahtar sözcüğü, kodunuzu fazladan içermediğinden olup [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md) veya aynı olayı işleyen ek yöntemleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olayları](../../../../visual-basic/programming-guide/language-features/events/index.md)
