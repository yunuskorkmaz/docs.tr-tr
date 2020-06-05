---
title: My.Settings Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: c905ff85c8e9729dd4d6068f0d34f729962bbb57
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372407"
---
# <a name="mysettings-object"></a>My.Settings Nesnesi
Uygulamanın ayarlarına erişmek için özellikleri ve yöntemleri sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `My.Settings`Nesnesi, uygulama ayarlarına erişim sağlar ve uygulamanızın özellik ayarlarını ve diğer bilgilerini dinamik olarak depolamanızı ve almanızı sağlar. Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Özellikler  
 `My.Settings`Nesnesinin özellikleri uygulamanızın ayarlarına erişim sağlar. Ayarları eklemek veya kaldırmak için, **Ayarlar tasarımcısını**kullanın.  
  
 Her ayarın bir **adı**, **türü**, **kapsamı**ve **değeri**vardır ve bu ayarlar, her bir ayara erişme özelliğinin nesnede nasıl göründüğünü belirlenir `My.Settings` :  
  
- **Ad** , özelliğin adını belirler.  
  
- **Tür** , özelliğin türünü belirler.  
  
- **Kapsam** , özelliğin salt okunurdur olduğunu gösterir. Değer **uygulama**ise, özellik salt okunurdur; değer **Kullanıcı**ise, özelliği okuma-yazma olur.  
  
- **Değer** , özelliğin varsayılan değeridir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|---|---|  
|`Reload`|Son kaydedilen değerlerden Kullanıcı ayarlarını yeniden yükler.|  
|`Save`|Geçerli Kullanıcı ayarlarını kaydeder.|  
  
 `My.Settings`Nesnesi ayrıca sınıfından devralınan gelişmiş özellikler ve yöntemler de sağlar <xref:System.Configuration.ApplicationSettingsBase> .  
  
## <a name="tasks"></a>Görevler  
 Aşağıdaki tabloda, nesnesiyle ilgili görevlerin örnekleri listelenmektedir `My.Settings` .  
  
|Alıcı|Bkz.|  
|---|---|  
|Uygulama ayarını oku|[Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Kullanıcı ayarını değiştirme|[Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Kullanıcı ayarlarını kalıcı yap|[Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Kullanıcı ayarları için özellik Kılavuzu oluşturma|[Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Örnek  
 Bu örnek, ayarın değerini gösterir `Nickname` .  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Bu örneğin çalışması için, uygulamanızın türünde bir ayarı olması gerekir `Nickname` `String` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.ApplicationSettingsBase>
- [Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
