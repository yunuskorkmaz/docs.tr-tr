---
title: 'Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma'
description: Özellikler nesnesi aracılığıyla C# ile çalışma zamanında uygulama kapsamlı ve kullanıcı kapsamlı ayarların nasıl okunacağını öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d784544e018bb693c501e35ea36fcae1946ef5eb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903368"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Nasıl yapılır: çalışma zamanında C Ile ayarları okuma\#

Özellikler nesnesi aracılığıyla çalışma zamanında uygulama kapsamlı ve kullanıcı kapsamlı ayarları okuyabilirsiniz. Properties nesnesi, proje için varsayılan ayarların tümünü, içinde tanımlandıkları projenin varsayılan ad alanındaki Özellikler. Settings. Default üyesi aracılığıyla gösterir.  
  
## <a name="to-read-settings-at-run-time-with-c"></a>Çalışma zamanında C ile ayarları okumak için\#
  
Properties. Settings. Default üyesi aracılığıyla uygun ayara erişin. Aşağıdaki örnekte, BackColor özelliğine adlı bir ayarın nasıl atanacağı gösterilmektedir `myColor` . Daha önce türünde adlı bir ayar içeren bir ayarlar dosyası oluşturmuş olmanızı gerektirir `myColor` `System.Drawing.Color` . Bir ayarlar dosyası oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: tasarım zamanında yeni ayar oluşturma](how-to-create-a-new-setting-at-design-time.md).  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](using-application-settings-and-user-settings.md)
- [Nasıl Yapılır: Çalışma Zamanında C# ile Kullanıcı Ayarlarını Yazma](how-to-write-user-settings-at-run-time-with-csharp.md)
- [Uygulama Ayarlarına Genel Bakış](application-settings-overview.md)
