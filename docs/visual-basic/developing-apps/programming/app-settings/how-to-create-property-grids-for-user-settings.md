---
title: 'Nasıl yapılır: Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma'
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

`My.Settings` Nesnenin Kullanıcı ayarı özellikleriyle bir <xref:System.Windows.Forms.PropertyGrid> denetim doldurarak Kullanıcı ayarları için özellik Kılavuzu oluşturabilirsiniz.  
  
> [!NOTE]
> Bu örneğin çalışması için, uygulamanız kullanıcı ayarlarının yapılandırılmış olması gerekir. Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 `My.Settings` Nesnesi her ayarı bir özellik olarak gösterir. Özellik adı, ayar adıyla aynıdır ve özellik türü ayar türüyle aynıdır. Ayarın **kapsamı** , özelliğin salt okunurdur belirler; bir **uygulama**kapsamı ayarının özelliği salt okunurdur, ancak **Kullanıcı**kapsamı ayarının özelliği okuma-yazma olur. Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Çalışma zamanında uygulama kapsamı ayarlarının değerlerini değiştiremez veya kaydedemezsiniz. Uygulama kapsamı ayarları yalnızca uygulama oluşturulurken ( **Proje Tasarımcısı**aracılığıyla) veya uygulamanın yapılandırma dosyası düzenlenerek değiştirilebilir. Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Bu örnek, `My.Settings` nesnenin <xref:System.Windows.Forms.PropertyGrid> Kullanıcı ayarı özelliklerine erişmek için bir denetim kullanır. Varsayılan olarak, <xref:System.Windows.Forms.PropertyGrid> `My.Settings` nesnesinin tüm özelliklerini gösterir. Ancak, Kullanıcı ayarı özelliklerinin <xref:System.Configuration.UserScopedSettingAttribute> özniteliği vardır. Bu örnek, <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> <xref:System.Windows.Forms.PropertyGrid> öğesinin özelliğini yalnızca Kullanıcı ayarı <xref:System.Configuration.UserScopedSettingAttribute> özelliklerini görüntüleyecek şekilde ayarlar.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Kullanıcı ayarı Özellik Kılavuzu eklemek için  
  
1. Araç kutusundan **PropertyGrid** denetimini uygulamanızın tasarım **Toolbox** yüzeyine ekleyin, burada kabul edilir `Form1`.  
  
     Özellik Kılavuzu denetiminin varsayılan adı `PropertyGrid1`.  
  
2. Form yükleme olay işleyicisi için kodu açmak `Form1` üzere tasarım yüzeyine çift tıklayın.  
  
3. `My.Settings` Nesne, Özellik kılavuzu için seçilen nesne olarak ayarlanır.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Özellik kılavuzunu yalnızca Kullanıcı ayarlarını gösterecek şekilde yapılandırın.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > Yalnızca uygulama kapsamı ayarlarını göstermek için yerine <xref:System.Configuration.ApplicationScopedSettingAttribute> özniteliğini kullanın. <xref:System.Configuration.UserScopedSettingAttribute>  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Uygulama kapandığında uygulama kullanıcı ayarlarını kaydeder. Ayarları hemen kaydetmek için `My.Settings.Save` yöntemini çağırın. Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı ayarlarını Visual Basic kalıcı hale](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)getirme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
