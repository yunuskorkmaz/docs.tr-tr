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
ms.openlocfilehash: d228e916e45054bc088aa633afd9d591e592210d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058007"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme

Bu konuda, devralınan bileşenlerde olay işleyicileriyle ortaya çıkan yaygın sorunlar listelenmektedir.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>Olay Işleyicisindeki kod her çağrı için Iki kez yürütülür  
  
- Devralınan olay işleyicisi bir [Handles](../../../language-reference/statements/handles-clause.md) yan tümcesi içermemelidir. Temel sınıftaki yöntemi, olayla zaten ilişkilendirilmiş ve uygun şekilde harekete geçmeyecektir. `Handles`Devralınan yöntemden yan tümceyi kaldırın.  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- Devralınan yöntemin bir `Handles` anahtar sözcüğü yoksa, kodunuzun bir ek [AddHandler bildirisi](../../../language-reference/statements/addhandler-statement.md) veya aynı olayı işleyen başka yöntemler içermediğini doğrulayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ekinlikler](index.md)
