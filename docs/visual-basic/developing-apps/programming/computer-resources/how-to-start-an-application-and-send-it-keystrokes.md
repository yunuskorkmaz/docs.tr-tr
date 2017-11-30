---
title: "Nasıl Yapılır: Uygulama Başlatma ve Gönderme Tuş Vuruşları (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bf92a74bc1b60ea3213d80e4df373936c65d89e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
