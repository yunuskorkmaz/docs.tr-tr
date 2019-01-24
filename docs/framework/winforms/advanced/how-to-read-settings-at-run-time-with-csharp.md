---
title: 'Nasıl yapılır: Çalışma zamanında ile ayarları okumaC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d798b40e5e337ea7652c8e82cb7fa860a87528b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521757"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Nasıl yapılır: Çalışma zamanında ile ayarları okumaC# #
Çalışma zamanında özellikleri nesnesi aracılığıyla hem uygulama kapsamlı ve kullanıcı kapsamlı ayarları okuyabilirsiniz. Özellikler nesnesinin tüm Properties.Settings.Default üye aracılığıyla proje için varsayılan ayarları gösterir.  
  
### <a name="to-read-settings-at-run-time-with-c"></a>Çalışma zamanında ile ayarları okunamadıC#  
  
-   Uygun ayarı Properties.Settings.Default üye aracılığıyla erişin. Aşağıdaki örnek adlı bir ayar atama gösterir `myColor` BackColor özelliği. Adlı bir ayarı içeren bir ayarlar dosyası daha önce oluşturmuş olmanız gerekir `myColor` türü `System.Drawing.Color`. Ayarları dosyası oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Tasarım zamanında yeni ayar oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [Nasıl yapılır: Çalışma zamanında ile kullanıcı ayarlarını yazmaC#](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)
- [Uygulama Ayarlarına Genel Bakış](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
