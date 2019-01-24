---
title: 'Nasıl yapılır: Uygulama başlatma ve gönderme tuş vuruşları (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 36d6110a9e0ccf20718e95e6d7601e21e8d8f22c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688395"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Nasıl yapılır: Uygulama başlatma ve gönderme tuş vuruşları (Visual Basic)
Bu örnekte `Shell` hesaplayıcı uygulamayı başlatmak için işlevi ve ardından tuş vuruşları kullanarak göndererek iki sayıyı çarpar `My.Computer.Keyboard.SendKeys` yöntemi.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 A <xref:System.ArgumentException> istenen işlem tanımlayıcısına sahip bir uygulama bulunamazsa özel durum oluşturulur.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Çağrı `Shell` işlevi, tam güven gerektirir (<xref:System.Security.SecurityException> sınıfı).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
