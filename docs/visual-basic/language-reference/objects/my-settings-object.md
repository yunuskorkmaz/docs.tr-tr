---
title: My.Settings Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 9560a51332ea596d4cf2228f1e07c158a0457ece
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350354"
---
# <a name="mysettings-object"></a>My.Settings Nesnesi
Uygulamanın ayarlarına erişmek için özellikleri ve yöntemleri sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `My.Settings` nesnesi uygulama ayarlarına erişim sağlar ve uygulamanızın özellik ayarlarını ve diğer bilgilerini dinamik olarak depolamanızı ve almanızı sağlar. Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Özellikler  
 `My.Settings` nesnesinin özellikleri uygulamanızın ayarlarına erişim sağlar. Ayarları eklemek veya kaldırmak için, **Ayarlar tasarımcısını**kullanın.  
  
 Her ayarın bir **adı**, **türü**, **kapsamı**ve **değeri**vardır ve bu ayarlar `My.Settings` nesnesinde her bir ayara erişme özelliğinin nasıl göründüğünü belirlenir:  
  
- **Ad** , özelliğin adını belirler.  
  
- **Tür** , özelliğin türünü belirler.  
  
- **Kapsam** , özelliğin salt okunurdur olduğunu gösterir. Değer **uygulama**ise, özellik salt okunurdur; değer **Kullanıcı**ise, özelliği okuma-yazma olur.  
  
- **Değer** , özelliğin varsayılan değeridir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|---|---|  
|`Reload`|Son kaydedilen değerlerden Kullanıcı ayarlarını yeniden yükler.|  
|`Save`|Geçerli Kullanıcı ayarlarını kaydeder.|  
  
 `My.Settings` nesnesi, <xref:System.Configuration.ApplicationSettingsBase> sınıfından devralınan gelişmiş özellikler ve yöntemler de sağlar.  
  
## <a name="tasks"></a>Görevler  
 Aşağıdaki tabloda `My.Settings` nesnesini içeren görevlerin örnekleri listelenmektedir.  
  
|Bitiş|Bkz.|  
|---|---|  
|Uygulama ayarını oku|[Nasıl yapılır: Visual Basic uygulama ayarlarını okuma](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Kullanıcı ayarını değiştirme|[Nasıl yapılır: Visual Basic Kullanıcı ayarlarını değiştirme](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Kullanıcı ayarlarını kalıcı yap|[Nasıl yapılır: Visual Basic 'de Kullanıcı ayarlarını kalıcı hale getirme](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Kullanıcı ayarları için özellik Kılavuzu oluşturma|[Nasıl yapılır: Visual Basic Kullanıcı ayarları için özellik kılavuzları oluşturma](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Örnek  
 Bu örnek `Nickname` ayarının değerini görüntüler.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Bu örneğin çalışması için, uygulamanızın `String`türünde bir `Nickname` ayarı olması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.ApplicationSettingsBase>
- [Nasıl yapılır: Visual Basic uygulama ayarlarını okuma](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Nasıl yapılır: Visual Basic Kullanıcı ayarlarını değiştirme](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Nasıl yapılır: Visual Basic 'de Kullanıcı ayarlarını kalıcı hale getirme](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Nasıl yapılır: Visual Basic Kullanıcı ayarları için özellik kılavuzları oluşturma](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
