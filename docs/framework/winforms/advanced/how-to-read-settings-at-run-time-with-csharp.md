---
title: 'Nasıl yapılır: Çalışma zamanında ile ayarları okumaC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8cdc1a79f1ab327ae037cd6a04aa769196405127
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974854"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Nasıl yapılır: Çalışma zamanında C ile ayarları okuma\#

Çalışma zamanında özellikleri nesnesi aracılığıyla hem uygulama kapsamlı ve kullanıcı kapsamlı ayarları okuyabilirsiniz. Özellikler nesnesinin tüm Properties.Settings.Default üye aracılığıyla proje için varsayılan ayarları gösterir.  
  
## <a name="to-read-settings-at-run-time-with-c"></a>Çalışma zamanında C ile ayarları okunamadı\#
  
Uygun ayarı Properties.Settings.Default üye aracılığıyla erişin. Aşağıdaki örnek adlı bir ayar atama gösterir `myColor` BackColor özelliği. Adlı bir ayarı içeren bir ayarlar dosyası daha önce oluşturmuş olmanız gerekir `myColor` türü `System.Drawing.Color`. Ayarları dosyası oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Tasarım zamanında yeni ayar oluşturma](how-to-create-a-new-setting-at-design-time.md).  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](using-application-settings-and-user-settings.md)
- [Nasıl yapılır: Çalışma zamanında ile kullanıcı ayarlarını yazmaC#](how-to-write-user-settings-at-run-time-with-csharp.md)
- [Uygulama Ayarlarına Genel Bakış](application-settings-overview.md)
