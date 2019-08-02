---
title: 'Nasıl yapılır: Çalışma Zamanında C# ile Ayarları Okuma'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 6a40718d57fad4041eeea2fded03b7256abbe8d1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710221"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Nasıl yapılır: Çalışma zamanında C Ile ayarları okuma\#

Özellikler nesnesi aracılığıyla çalışma zamanında uygulama kapsamlı ve kullanıcı kapsamlı ayarları okuyabilirsiniz. Properties nesnesi, proje için varsayılan ayarların tümünü, içinde tanımlandıkları projenin varsayılan ad alanındaki Özellikler. Settings. Default üyesi aracılığıyla gösterir.  
  
## <a name="to-read-settings-at-run-time-with-c"></a>Çalışma zamanında C ile ayarları okumak için\#
  
Properties. Settings. Default üyesi aracılığıyla uygun ayara erişin. Aşağıdaki örnekte, BackColor özelliğine adlı `myColor` bir ayarın nasıl atanacağı gösterilmektedir. Daha önce türünde `myColor` `System.Drawing.Color`adlı bir ayar içeren bir ayarlar dosyası oluşturmuş olmanızı gerektirir. Bir ayarlar dosyası oluşturma hakkında daha fazla bilgi için [bkz. nasıl yapılır: Tasarım zamanında](how-to-create-a-new-setting-at-design-time.md)yeni bir ayar oluşturun.  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](using-application-settings-and-user-settings.md)
- [Nasıl yapılır: Çalışma zamanında Kullanıcı ayarlarını şu şekilde yazın:C#](how-to-write-user-settings-at-run-time-with-csharp.md)
- [Uygulama Ayarlarına Genel Bakış](application-settings-overview.md)
