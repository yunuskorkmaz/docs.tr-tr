---
title: 'Nasıl Yapılır: Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: bed4e8a2b50f0115c3b8d9d6abf427df5f216388
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329607"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma

Nesnenin kullanıcı ayar özellikleri ile bir <xref:System.Windows.Forms.PropertyGrid> denetim doldurma tarafından kullanıcı ayarları için bir özellik ızgarası oluşturabilirsiniz. `My.Settings`  
  
> [!NOTE]
> Bu örneğin çalışabilmesi için uygulamanızın kullanıcı ayarlarını yapılandırması gerekir. Daha fazla bilgi için bkz: [Uygulama Ayarlarını Yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Nesne `My.Settings` her ayarı bir özellik olarak ortaya çıkarır. Özellik adı ayar adı ile aynıdır ve özellik türü ayar türüyle aynıdır. Ayarın **Kapsamı** özelliğin salt okunup okunmayalı olduğunu belirler; **Bir Uygulama**-kapsam ayarı için özellik salt okunurken, **Kullanıcı-kapsam**ayarı özelliği okuma-yazma özelliğidir. Daha fazla bilgi için [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)' e bakın.  
  
> [!NOTE]
> Çalışma zamanında uygulama kapsamı ayarlarının değerlerini değiştiremez veya kaydedemezsiniz. Uygulama kapsamı ayarları yalnızca uygulamayı oluştururken **(Proje Tasarımcısı**aracılığıyla) veya uygulamanın yapılandırma dosyasını düzenleyerek değiştirilebilir. Daha fazla bilgi için bkz: [Uygulama Ayarlarını Yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Bu örnek, <xref:System.Windows.Forms.PropertyGrid> `My.Settings` nesnenin kullanıcı ayar özelliklerine erişmek için bir denetim kullanır. Varsayılan olarak, <xref:System.Windows.Forms.PropertyGrid> `My.Settings` nesnenin tüm özelliklerini gösterir. Ancak, kullanıcı ayar özellikleri <xref:System.Configuration.UserScopedSettingAttribute> özniteliğe sahiptir. Bu örnek, <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> yalnızca <xref:System.Windows.Forms.PropertyGrid> kullanıcı <xref:System.Configuration.UserScopedSettingAttribute> ayar özelliklerini görüntülemek için özelliğini ayarlar.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Kullanıcı ayar özelliği ızgarası eklemek için  
  
1. **Toolbox'tan** **PropertyGrid** denetimini uygulamanız için tasarım yüzeyine `Form1`ekleyin, burada olduğu varsayılır.  
  
     Özellik-ızgara denetiminin varsayılan `PropertyGrid1`adı.  
  
2. Form yükleme olay işleyicisinin kodunu açmak için `Form1` tasarım yüzeyini çift tıklatın.  
  
3. Nesneyi `My.Settings` özellik ızgarası için seçili nesne olarak ayarlayın.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Özellik ızgarasını yalnızca kullanıcı ayarlarını gösterecek şekilde yapılandırın.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > Yalnızca uygulama kapsamı ayarlarını göstermek <xref:System.Configuration.ApplicationScopedSettingAttribute> için, <xref:System.Configuration.UserScopedSettingAttribute>özniteliği yerine kullanın.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Uygulama kapandığında uygulama kullanıcı ayarlarını kaydeder. Ayarları hemen kaydetmek için `My.Settings.Save` yöntemi arayın. Daha fazla bilgi için [bkz: Visual Basic'te Kullanıcı Ayarlarını Devam](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)Edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
