---
title: 'Nasıl yapılır: Uygulama başlatma ve gönderme tuş vuruşları (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: f130429e5b0964dc8680441fb83cb06d45904a69
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966209"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Nasıl yapılır: Uygulama başlatma ve gönderme tuş vuruşları (Visual Basic)
Bu örnekte `Shell` hesaplayıcı uygulamayı başlatmak için işlevi ve ardından tuş vuruşları kullanarak göndererek iki sayıyı çarpar `My.Computer.Keyboard.SendKeys` yöntemi.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 A <xref:System.ArgumentException> istenen işlem tanımlayıcısına sahip bir uygulama bulunamazsa özel durum oluşturulur.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Çağrı `Shell` işlevi, tam güven gerektirir (<xref:System.Security.SecurityException> sınıfı).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
