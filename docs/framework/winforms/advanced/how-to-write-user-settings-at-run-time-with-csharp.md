---
title: "Nasıl Yapılır: Çalışma Zamanında C# ile Kullanıcı Ayarlarını Yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5966aef77c994d2657bd282ad15e8f59a64eeb47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>Nasıl Yapılır: Çalışma Zamanında C# ile Kullanıcı Ayarlarını Yazma #
Uygulama kapsamlı ayarları salt okunurdur ve yalnızca tasarım zamanında veya uygulama oturumları arasında .config dosyasını değiştirmeden tarafından değiştirilebilir. Herhangi bir özelliğin değerini değiştirmek gibi kullanıcı kapsamlı ayarları ancak, çalışma zamanında yazılabilir. Yeni değer uygulama oturumu boyunca devam ettirir. Save yöntemi çağrılarak uygulama oturumları arasında ayarlarında yapılan değişiklikler devam edebilir.  
  
### <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>Nasıl yapılır: Yazma ve çalışma zamanında C# ile kullanıcı ayarlarını sürdürmek  
  
1.  Ayar erişmek ve bu örnekte gösterildiği gibi yeni bir değer atayabilirsiniz:  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  Uygulama oturumları arasında ayarlarında yapılan değişiklikler kalıcı hale getirmek istiyorsanız, bu örnekte gösterildiği gibi kaydetme yöntemini çağırın:  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     Kullanıcı ayarları kullanıcının yerel gizli uygulama veri klasörünün bir alt dosyasında kaydedilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama ayarları ve kullanıcı ayarlarını kullanma](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Nasıl yapılır: Çalışma zamanında C# ile ayarları okuma](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
 [Uygulama ayarlarına genel bakış](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
