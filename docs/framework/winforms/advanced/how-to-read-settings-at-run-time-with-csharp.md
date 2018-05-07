---
title: 'Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8259e2f429718793c01868855651d1000620fae5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Nasıl Yapılır: Çalışma Zamanında C# ile Kullanıcı Ayarlarını Yazma](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [Uygulama Ayarlarına Genel Bakış](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
