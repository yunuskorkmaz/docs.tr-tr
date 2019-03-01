---
title: 'Nasıl yapılır: Çalışma zamanında ile kullanıcı ayarlarını yazmaC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 264fa9706f9255d7324cad6d02c36cc424e28995
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981601"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>Nasıl yapılır: Çalışma zamanında C ile kullanıcı ayarlarını yazma\#

Uygulama kapsamlı ayarlar salt okunurdur ve yalnızca tasarım zamanında ya da uygulama oturumları arasında .config dosyasını değiştirerek değiştirilebilir. Herhangi bir özelliğin değerini değiştirmek gibi kullanıcı kapsamlı ayarları ancak çalışma zamanında yazılabilir. Yeni değer, uygulama oturum süresi boyunca devam ettirir. Ayarları kaydetme yöntemini çağırarak uygulama oturumları arasında yapılan değişiklikleri kalıcı hale getirebilirsiniz.  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>Nasıl yapılır: Yazma ve çalışma zamanında C ile kullanıcı ayarlarını kalıcı yapma\#
  
1. Ayar erişmek ve bu örnekte gösterildiği gibi yeni bir değer atayabilirsiniz:  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. Uygulama oturumları arasında ayarlarındaki değişiklikler kalıcı hale getirmek istiyorsanız, bu örnekte gösterildiği gibi Save metoduna çağrı:  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
Kullanıcı ayarları kullanıcının yerel gizli uygulama veri klasörünün bir alt dosyasında kaydedilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](using-application-settings-and-user-settings.md)
- [Nasıl yapılır: Çalışma zamanında ile ayarları okumaC#](how-to-read-settings-at-run-time-with-csharp.md)
- [Uygulama Ayarlarına Genel Bakış](application-settings-overview.md)
