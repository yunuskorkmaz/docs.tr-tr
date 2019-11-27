---
title: 'Nasıl yapılır: Kullanıcı ayarları için özellik kılavuzları oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: bed4e8a2b50f0115c3b8d9d6abf427df5f216388
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329607"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma

`My.Settings` nesnesinin kullanıcı ayarı özellikleriyle <xref:System.Windows.Forms.PropertyGrid> denetimi doldurarak Kullanıcı ayarları için bir özellik ızgarası oluşturabilirsiniz.  
  
> [!NOTE]
> Bu örneğin çalışması için, uygulamanız kullanıcı ayarlarının yapılandırılmış olması gerekir. Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 `My.Settings` nesnesi her ayarı bir özellik olarak kullanıma sunar. Özellik adı, ayar adıyla aynıdır ve özellik türü ayar türüyle aynıdır. Ayarın **kapsamı** , özelliğin salt okunurdur belirler; bir **uygulama**kapsamı ayarının özelliği salt okunurdur, ancak **Kullanıcı**kapsamı ayarının özelliği okuma-yazma olur. Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Çalışma zamanında uygulama kapsamı ayarlarının değerlerini değiştiremez veya kaydedemezsiniz. Uygulama kapsamı ayarları yalnızca uygulama oluşturulurken ( **Proje Tasarımcısı**aracılığıyla) veya uygulamanın yapılandırma dosyası düzenlenerek değiştirilebilir. Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Bu örnek, `My.Settings` nesnesinin kullanıcı ayarı özelliklerine erişmek için <xref:System.Windows.Forms.PropertyGrid> denetimini kullanır. Varsayılan olarak, <xref:System.Windows.Forms.PropertyGrid> `My.Settings` nesnesinin tüm özelliklerini gösterir. Ancak, Kullanıcı ayarı özelliklerinin <xref:System.Configuration.UserScopedSettingAttribute> özniteliği vardır. Bu örnek, <xref:System.Windows.Forms.PropertyGrid> <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> özelliğini yalnızca Kullanıcı ayarı özelliklerini görüntüleyecek şekilde <xref:System.Configuration.UserScopedSettingAttribute> olarak ayarlar.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Kullanıcı ayarı Özellik Kılavuzu eklemek için  
  
1. **Araç kutusundan** **PropertyGrid** denetimini uygulamanızın tasarım yüzeyine ekleyin, burada `Form1`olarak kabul edilir.  
  
     Özellik Kılavuzu denetiminin varsayılan adı `PropertyGrid1`.  
  
2. Form yükleme olay işleyicisi için kodu açmak üzere `Form1` için tasarım yüzeyine çift tıklayın.  
  
3. `My.Settings` nesnesini, Özellik kılavuzu için seçilen nesne olarak ayarlayın.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Özellik kılavuzunu yalnızca Kullanıcı ayarlarını gösterecek şekilde yapılandırın.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > Yalnızca uygulama kapsamı ayarlarını göstermek için <xref:System.Configuration.UserScopedSettingAttribute>yerine <xref:System.Configuration.ApplicationScopedSettingAttribute> özniteliğini kullanın.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Uygulama kapandığında uygulama kullanıcı ayarlarını kaydeder. Ayarları hemen kaydetmek için `My.Settings.Save` yöntemini çağırın. Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı ayarlarını Visual Basic kalıcı hale](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)getirme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Nasıl yapılır: Visual Basic uygulama ayarlarını okuma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Nasıl yapılır: Visual Basic Kullanıcı ayarlarını değiştirme](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Nasıl yapılır: Visual Basic 'de Kullanıcı ayarlarını kalıcı hale getirme](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
