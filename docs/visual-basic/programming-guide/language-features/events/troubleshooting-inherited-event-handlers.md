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
ms.openlocfilehash: 704ca667a6d14ade7be0192e872f5e40791cb864
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053814"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme
Bu konuda, devralınan bileşenler olay işleyicileri ile ortaya genel sorunları listelemektedir.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>İki kez her çağrı için olay işleyicisinde kodu yürütür  
  
- Devralınan bir olay işleyicisi içermemelidir bir [işleme](../../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi. Yöntem temel sınıfta zaten olayla ilişkili ve buna göre ateşlenir. Kaldırma `Handles` devralınan yöntemi from yan tümcesi.  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- Devralınan yöntemi yoksa bir `Handles` anahtar sözcüğü, ek kod içermediğinden emin olun [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md) veya aynı olay işleyen ek yöntemleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
