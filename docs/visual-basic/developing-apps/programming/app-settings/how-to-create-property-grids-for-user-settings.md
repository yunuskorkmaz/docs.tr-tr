---
title: 'Nasıl yapılır: Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: e93c62ad138be260422319e28a3ed85dd1871a1b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410172"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma

<xref:System.Windows.Forms.PropertyGrid>Nesnenin Kullanıcı ayarı özellikleriyle bir denetim doldurarak Kullanıcı ayarları için özellik Kılavuzu oluşturabilirsiniz `My.Settings` .  
  
> [!NOTE]
> Bu örneğin çalışması için, uygulamanız kullanıcı ayarlarının yapılandırılmış olması gerekir. Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 `My.Settings`Nesnesi her ayarı bir özellik olarak gösterir. Özellik adı, ayar adıyla aynıdır ve özellik türü ayar türüyle aynıdır. Ayarın **kapsamı** , özelliğin salt okunurdur belirler; bir **uygulama**kapsamı ayarının özelliği salt okunurdur, ancak **Kullanıcı**kapsamı ayarının özelliği okuma-yazma olur. Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Çalışma zamanında uygulama kapsamı ayarlarının değerlerini değiştiremez veya kaydedemezsiniz. Uygulama kapsamı ayarları yalnızca uygulama oluşturulurken ( **Proje Tasarımcısı**aracılığıyla) veya uygulamanın yapılandırma dosyası düzenlenerek değiştirilebilir. Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Bu örnek, <xref:System.Windows.Forms.PropertyGrid> nesnenin Kullanıcı ayarı özelliklerine erişmek için bir denetim kullanır `My.Settings` . Varsayılan olarak, <xref:System.Windows.Forms.PropertyGrid> nesnesinin tüm özelliklerini gösterir `My.Settings` . Ancak, Kullanıcı ayarı özelliklerinin <xref:System.Configuration.UserScopedSettingAttribute> özniteliği vardır. Bu örnek <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> , öğesinin özelliğini <xref:System.Windows.Forms.PropertyGrid> <xref:System.Configuration.UserScopedSettingAttribute> yalnızca Kullanıcı ayarı özelliklerini görüntüleyecek şekilde ayarlar.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Kullanıcı ayarı Özellik Kılavuzu eklemek için  
  
1. **Araç kutusundan** **PropertyGrid** denetimini uygulamanızın tasarım yüzeyine ekleyin, burada kabul edilir `Form1` .  
  
     Özellik Kılavuzu denetiminin varsayılan adı `PropertyGrid1` .  
  
2. `Form1`Form yükleme olay işleyicisi için kodu açmak üzere tasarım yüzeyine çift tıklayın.  
  
3. Nesne, `My.Settings` Özellik kılavuzu için seçilen nesne olarak ayarlanır.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Özellik kılavuzunu yalnızca Kullanıcı ayarlarını gösterecek şekilde yapılandırın.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > Yalnızca uygulama kapsamı ayarlarını göstermek için <xref:System.Configuration.ApplicationScopedSettingAttribute> yerine özniteliğini kullanın <xref:System.Configuration.UserScopedSettingAttribute> .  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Uygulama kapandığında uygulama kullanıcı ayarlarını kaydeder. Ayarları hemen kaydetmek için `My.Settings.Save` yöntemini çağırın. Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı ayarlarını Visual Basic kalıcı hale](how-to-persist-user-settings.md)getirme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../language-reference/objects/my-settings-object.md)
- [Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma](how-to-read-application-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme](how-to-change-user-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma](how-to-persist-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
