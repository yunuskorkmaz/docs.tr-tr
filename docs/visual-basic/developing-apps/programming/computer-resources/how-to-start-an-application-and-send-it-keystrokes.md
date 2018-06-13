---
title: 'Nasıl Yapılır: Uygulama Başlatma ve Gönderme Tuş Vuruşları (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 716c88153ad01c7b225f31948c8aaaa2694dc512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582154"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Nasıl Yapılır: Uygulama Başlatma ve Gönderme Tuş Vuruşları (Visual Basic)
Bu örnekte `Shell` hesaplayıcı uygulamayı başlatmak için işlev ve iki sayının kullanarak tuş vuruşları göndererek çarpan `My.Computer.Keyboard.SendKeys` yöntemi.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 A <xref:System.ArgumentException> istenen işlem tanıtıcısı olan bir uygulama bulunamazsa, özel durum oluşturuldu.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Çağrı `Shell` işlevi tam güven gerektiren (<xref:System.Security.SecurityException> sınıfı).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
