---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: uygulama başlatma ve bu tuşlara gönderme (Visual Basic)'
title: 'Nasıl yapılır: uygulama başlatma ve tuş vuruşu gönderme-Visual Basic'
ms.date: 10/23/2019
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: ea54b940b528e0833d9c7a6cbef67f65a4cb4f6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666465"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Nasıl yapılır: uygulama başlatma ve tuş vuruşu gönderme (Visual Basic)

Bu örnek, <xref:Microsoft.VisualBasic.Interaction.Shell%2A> Notepad uygulamasını başlatmak için yöntemini kullanır ve sonra, [My. Computer. Keyboard. SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) yöntemini kullanarak tuş vuruşları göndererek bir cümle yazdırır.

## <a name="example"></a>Örnek

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a>Güçlü programlama

<xref:System.ArgumentException>İstenen işlem tanımlayıcısına sahip bir uygulama bulunamazsa bir özel durum oluşur.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği

İşleve yapılan çağrı için `Shell` tam güven ( <xref:System.Security.SecurityException> sınıf) gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
