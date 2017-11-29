---
title: "Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 81a79945dfc0b1501134bc1b0197c18093a5dfae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma
Kullanıcı ayarları için özellik kılavuzunu doldurarak oluşturabileceğiniz bir <xref:System.Windows.Forms.PropertyGrid> kullanıcı ayarı özelliklerinin denetimiyle `My.Settings` nesnesi.  
  
> [!NOTE]
>  Çalışmak bu örnek için uygulamanızın yapılandırılmış kullanıcı ayarlarını olması gerekir. Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 `My.Settings` Nesne her ayar özelliği olarak kullanıma sunar. Özellik adı ayar adı ile aynıdır ve özellik türü ayar türü ile aynıdır. Ayarın **kapsam** özelliği salt okunur; olup olmadığını belirler özelliği için bir **uygulama**-kapsam ayarıdır hatayla özelliği için salt okunur bir **kullanıcı**-kapsamı salt okunur bir ayardır. Daha fazla bilgi için bkz: [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Değiştiremez veya çalışma zamanında uygulama kapsamı ayarlarının değerleri kaydedin. Uygulama kapsam ayarları değiştirilebilir, yalnızca uygulama oluşturulurken (aracılığıyla **Proje Tasarımcısı**) ya da uygulamanın yapılandırma dosyasını düzenleyerek. Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Bu örnekte bir <xref:System.Windows.Forms.PropertyGrid> kullanıcı ayarı özelliklerine erişmek için Denetim `My.Settings` nesnesi. Varsayılan olarak, <xref:System.Windows.Forms.PropertyGrid> tüm özelliklerini gösterir `My.Settings` nesnesi. Ancak, kullanıcı ayarı özelliklerine sahip <xref:System.Configuration.UserScopedSettingAttribute> özniteliği. Bu örnek ayarlar <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> özelliği <xref:System.Windows.Forms.PropertyGrid> için <xref:System.Configuration.UserScopedSettingAttribute> yalnızca kullanıcı ayarı özelliklerini görüntüleyin.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Kullanıcı ayarı özellik Kılavuzu eklemek için  
  
1.  Ekleme **PropertyGrid** gelen denetim **araç** uygulamanız için tasarım yüzeyine varsayılır burada `Form1`.  
  
     Özellik Kılavuzu denetim varsayılan adı `PropertyGrid1`.  
  
2.  Tasarım yüzeyi için çift `Form1` form yük olay işleyicisi için kod açın.  
  
3.  Ayarlama `My.Settings` nesnesi seçili nesne için özellik kılavuzunu olarak.  
  
     [!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_1.vb)]  
  
4.  Yalnızca kullanıcı ayarlarını göstermek için özellik kılavuzunu yapılandırın.  
  
     [!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_2.vb)]  
  
    > [!NOTE]
    >  Yalnızca uygulama kapsamı ayarlarını görüntülemek için kullanın <xref:System.Configuration.ApplicationScopedSettingAttribute> yerine özniteliği <xref:System.Configuration.UserScopedSettingAttribute>.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Uygulama kapatıldığında uygulama kullanıcı ayarlarını kaydeder. Ayarlar hemen kaydetmek için arama `My.Settings.Save` yöntemi. Daha fazla bilgi için bkz: [nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını sürdürmek](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Uygulama ayarları (.NET) yönetme](/visualstudio/ide/managing-application-settings-dotnet)
