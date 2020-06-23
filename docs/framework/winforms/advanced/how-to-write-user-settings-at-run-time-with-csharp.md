---
title: 'Nasıl Yapılır: Çalışma Zamanında C# ile Kullanıcı Ayarlarını Yazma'
description: Save metodunu çağırarak uygulama oturumları arasındaki ayarları değişikliklerle kalıcı hale getirerek, çalışma zamanında C# ile ayarları yazmayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 6154ff1b92d6c2d4c788299e59eb8f73e6b69c4b
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904331"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>Nasıl yapılır: çalışma zamanında C ile Kullanıcı ayarlarını yazma\#

Uygulama kapsamlı olan ayarlar salt okunurdur ve yalnızca tasarım zamanında veya uygulama oturumları arasındaki. config dosyasını değiştirerek değiştirilebilir. Ancak, kullanıcı kapsamlı olan ayarlar, tıpkı herhangi bir özellik değerini değiştirdiğiniz gibi çalışma zamanında yazılabilir. Yeni değer, uygulama oturumunun süresi boyunca devam ettirir. Save metodunu çağırarak uygulama oturumları arasındaki ayarları değişikliklerle kalıcı hale getirebilirsiniz.  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>Nasıl yapılır: çalışma zamanında C ile Kullanıcı ayarlarını yazma ve kalıcı hale getirme\#
  
1. Bu ayara erişin ve bu örnekte gösterildiği gibi yeni bir değer atayın:  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. Değişiklikleri uygulama oturumları arasında kalıcı hale getirmek istiyorsanız, bu örnekte gösterildiği gibi Save metodunu çağırın:  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
Kullanıcı ayarları, kullanıcının yerel gizli uygulama verileri klasörünün bir alt klasörü içindeki bir dosyaya kaydedilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](using-application-settings-and-user-settings.md)
- [Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma](how-to-read-settings-at-run-time-with-csharp.md)
- [Uygulama Ayarlarına Genel Bakış](application-settings-overview.md)
