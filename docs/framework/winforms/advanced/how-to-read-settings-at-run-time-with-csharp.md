---
title: "Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c23fd88d33ff4ca480c435f2058f4c568320578
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma #
Özellikleri nesnesi aracılığıyla çalışma zamanında uygulama kapsamlı hem de kullanıcı kapsamlı ayarlarını okuyabilirsiniz. Özellikleri nesnesi Properties.Settings.Default üye aracılığıyla proje için varsayılan ayarlar kullanıma sunar.  
  
### <a name="to-read-settings-at-run-time-with-c"></a>Çalışma zamanında C# ile ayarları okunamıyor  
  
-   Uygun ayarı Properties.Settings.Default üye üzerinden erişebilirsiniz. Aşağıdaki örnek adlı bir ayarı atama gösterilmiştir `myColor` BackColor özelliği. Adlı bir ayar içeren ayarlar dosyası önceden oluşturulmuş gerekir `myColor` türü `System.Drawing.Color`. Ayarlar dosyası oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: tasarım zamanında yeni ayar oluşturun](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama ayarları ve kullanıcı ayarlarını kullanma](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Nasıl yapılır: Çalışma zamanında C# ile kullanıcı ayarlarını yazma](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [Uygulama ayarlarına genel bakış](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
