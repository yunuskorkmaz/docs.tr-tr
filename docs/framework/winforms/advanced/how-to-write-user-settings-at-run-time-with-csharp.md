---
title: 'Nasıl yapılır: Çalışma zamanında ile kullanıcı ayarlarını yazmaC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: a62bf540ebdc383f26bd4aed760b2562437047aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560951"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>Nasıl yapılır: Çalışma zamanında ile kullanıcı ayarlarını yazmaC# #
Uygulama kapsamlı ayarlar salt okunurdur ve yalnızca tasarım zamanında ya da uygulama oturumları arasında .config dosyasını değiştirerek değiştirilebilir. Herhangi bir özelliğin değerini değiştirmek gibi kullanıcı kapsamlı ayarları ancak çalışma zamanında yazılabilir. Yeni değer, uygulama oturum süresi boyunca devam ettirir. Ayarları kaydetme yöntemini çağırarak uygulama oturumları arasında yapılan değişiklikleri kalıcı hale getirebilirsiniz.  
  
### <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>Nasıl yapılır: Yazma ve çalışma zamanında ile kullanıcı ayarlarını kalıcı yapmaC#  
  
1.  Ayar erişmek ve bu örnekte gösterildiği gibi yeni bir değer atayabilirsiniz:  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  Uygulama oturumları arasında ayarlarındaki değişiklikler kalıcı hale getirmek istiyorsanız, bu örnekte gösterildiği gibi Save metoduna çağrı:  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     Kullanıcı ayarları kullanıcının yerel gizli uygulama veri klasörünün bir alt dosyasında kaydedilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [Nasıl yapılır: Çalışma zamanında ile ayarları okumaC#](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)
- [Uygulama Ayarlarına Genel Bakış](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
