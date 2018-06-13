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
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme
Bu konu, devralınan bileşenleri olay işleyicileri ile ortaya çıkan ortak sorunları listeler.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>İki kez yapılan her çağrı için olay işleyicisini kodu çalıştırır  
  
-   Devralınmış olay işleyicisi içermemelidir bir [işler](../../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi. Taban sınıf yönteminde zaten olayla ilişkili ve buna göre ateşlenir. Kaldırma `Handles` devralınan yöntemi from yan tümcesi.  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   Devralınan yöntemi yoksa bir `Handles` anahtar sözcüğü, kodunuzu fazladan içermediğinden olup [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md) veya aynı olayı işleyen ek yöntemleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
