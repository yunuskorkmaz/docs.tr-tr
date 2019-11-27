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
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme
Bu konuda, devralınan bileşenlerde olay işleyicileriyle ortaya çıkan yaygın sorunlar listelenmektedir.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>Olay Işleyicisindeki kod her çağrı için Iki kez yürütülür  
  
- Devralınan olay işleyicisi bir [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi içermemelidir. Temel sınıftaki yöntemi, olayla zaten ilişkilendirilmiş ve uygun şekilde harekete geçmeyecektir. Devralınan yöntemden `Handles` yan tümcesini kaldırın.  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- Devralınan yöntemin bir `Handles` anahtar sözcüğü yoksa, kodunuzun ek bir [AddHandler bildirisi](../../../../visual-basic/language-reference/statements/addhandler-statement.md) veya aynı olayı işleyen başka yöntemler içermediğini doğrulayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
