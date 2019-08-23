---
title: 'Nasıl yapılır: Visual Basic Kullanıcı ayarları için özellik kılavuzları oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: 4a31b44cca61caea5fdf725405646f628b5430b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968389"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Nasıl yapılır: Visual Basic Kullanıcı ayarları için özellik kılavuzları oluşturma
`My.Settings` Nesnenin Kullanıcı ayarı özellikleriyle bir <xref:System.Windows.Forms.PropertyGrid> denetim doldurarak Kullanıcı ayarları için özellik Kılavuzu oluşturabilirsiniz.  
  
> [!NOTE]
> Bu örneğin çalışması için, uygulamanız kullanıcı ayarlarının yapılandırılmış olması gerekir. Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 `My.Settings` Nesnesi her ayarı bir özellik olarak gösterir. Özellik adı, ayar adıyla aynıdır ve özellik türü ayar türüyle aynıdır. Ayarın **kapsamı** , özelliğin salt okunurdur belirler; bir **uygulama**kapsamı ayarının özelliği salt okunurdur, ancak **Kullanıcı**kapsamı ayarının özelliği okuma-yazma olur. Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Çalışma zamanında uygulama kapsamı ayarlarının değerlerini değiştiremez veya kaydedemezsiniz. Uygulama kapsamı ayarları yalnızca uygulama oluşturulurken ( **Proje Tasarımcısı**aracılığıyla) veya uygulamanın yapılandırma dosyası düzenlenerek değiştirilebilir. Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Bu örnek, `My.Settings` nesnenin <xref:System.Windows.Forms.PropertyGrid> Kullanıcı ayarı özelliklerine erişmek için bir denetim kullanır. Varsayılan olarak, <xref:System.Windows.Forms.PropertyGrid> `My.Settings` nesnesinin tüm özelliklerini gösterir. Ancak, Kullanıcı ayarı özelliklerinin <xref:System.Configuration.UserScopedSettingAttribute> özniteliği vardır. Bu örnek <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> <xref:System.Windows.Forms.PropertyGrid>,öğesinin özelliğini yalnızca Kullanıcı ayarı özelliklerini görüntüleyecek şekildeayarlar.<xref:System.Configuration.UserScopedSettingAttribute>  
  
### <a name="to-add-a-user-setting-property-grid"></a>Kullanıcı ayarı Özellik Kılavuzu eklemek için  
  
1. Araç kutusundan **PropertyGrid** denetimini uygulamanızın tasarım yüzeyine ekleyin, `Form1`burada kabul edilir.  
  
     Özellik Kılavuzu denetiminin `PropertyGrid1`varsayılan adı.  
  
2. Form yükleme olay işleyicisi için kodu açmak `Form1` üzere tasarım yüzeyine çift tıklayın.  
  
3. `My.Settings` Nesne, Özellik kılavuzu için seçilen nesne olarak ayarlanır.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Özellik kılavuzunu yalnızca Kullanıcı ayarlarını gösterecek şekilde yapılandırın.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > Yalnızca uygulama kapsamı ayarlarını göstermek için <xref:System.Configuration.ApplicationScopedSettingAttribute> <xref:System.Configuration.UserScopedSettingAttribute>yerine özniteliğini kullanın.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Uygulama kapandığında uygulama kullanıcı ayarlarını kaydeder. Ayarları hemen kaydetmek için `My.Settings.Save` yöntemini çağırın. Daha fazla bilgi için [nasıl yapılır: Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)Kullanıcı ayarlarını kalıcı hale getirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Nasıl yapılır: Visual Basic uygulama ayarlarını okuyun](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Nasıl yapılır: Visual Basic Kullanıcı ayarlarını değiştirme](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Nasıl yapılır: Visual Basic Kullanıcı ayarlarını kalıcı yapma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
