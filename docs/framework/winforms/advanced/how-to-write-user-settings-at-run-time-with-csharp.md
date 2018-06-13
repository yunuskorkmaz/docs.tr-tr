---
title: 'Nasıl Yapılır: Çalışma Zamanında C# ile Kullanıcı Ayarlarını Yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: f289b6a6a4a726ffa6bb2c9df99c665e2872e8d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522301"
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
 [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
 [Uygulama Ayarlarına Genel Bakış](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
