---
title: "Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzu oluşturma"
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: 5f4b962762aeecea65748c5456bc4a2d75595d4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014104"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzu oluşturma
Kullanıcı ayarları için bir özellik kılavuzunda doldurarak oluşturabileceğiniz bir <xref:System.Windows.Forms.PropertyGrid> kullanıcı ayarı özelliklerini denetimiyle `My.Settings` nesne.  
  
> [!NOTE]
>  Çalışmak bu örneğin sırada, uygulamanızın kullanıcı ayarlarına yapılandırılmış olmalıdır. Daha fazla bilgi için [uygulama ayarlarını yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 `My.Settings` Nesnesi, her ayarın bir özellik olarak kullanıma sunar. Özellik adı ayar adı ile aynıdır ve özellik türü ayar türü ile aynıdır. Ayarın **kapsam** özelliği salt okunur; olup olmadığını belirler özellik için bir **uygulama**-kapsam ayardır sırasında özelliği salt okunur bir **kullanıcı**-kapsam okuma-yazma ayardır. Daha fazla bilgi için [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Değiştiremez veya çalışma zamanında uygulama kapsamı ayarlarının değerleri kaydedin. Uygulama kapsamı ayarları, yalnızca uygulama oluşturulurken değiştirilebilir (aracılığıyla **Proje Tasarımcısı**) veya uygulama yapılandırma dosyasını düzenleyerek. Daha fazla bilgi için [uygulama ayarlarını yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Bu örnekte bir <xref:System.Windows.Forms.PropertyGrid> kullanıcı ayarı özelliklerine erişmek için Denetim `My.Settings` nesne. Varsayılan olarak, <xref:System.Windows.Forms.PropertyGrid> tüm özelliklerini gösterir `My.Settings` nesne. Ancak, kullanıcı ayarı özelliklerine sahip <xref:System.Configuration.UserScopedSettingAttribute> özniteliği. Bu örnekte ayarlar <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> özelliği <xref:System.Windows.Forms.PropertyGrid> için <xref:System.Configuration.UserScopedSettingAttribute> yalnızca kullanıcı ayarı özelliklerini görüntülemek için.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Bir kullanıcı ayarı özellik kılavuzunda eklemek için  
  
1. Ekleme **PropertyGrid** denetimi **araç kutusu** uygulamanız için tasarım yüzeyine varsayılır burada `Form1`.  
  
     Özellik Kılavuzu denetimini varsayılan adıdır `PropertyGrid1`.  
  
2. Tasarım yüzeyi için çift `Form1` form-load olay işleyicisinde kodu açın.  
  
3. Ayarlama `My.Settings` seçili nesne için özellik kılavuzu olarak nesnesi.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Özellik Kılavuzu, yalnızca kullanıcı ayarlarını yapılandırın.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    >  Yalnızca uygulama kapsamlı ayarlar göstermek için kullanın <xref:System.Configuration.ApplicationScopedSettingAttribute> özniteliği yerine <xref:System.Configuration.UserScopedSettingAttribute>.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Uygulama kapatıldığında kullanıcı ayarlarını uygulamayı kaydeder. Hemen ayarları kaydetmek için çağrı `My.Settings.Save` yöntemi. Daha fazla bilgi için [nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
