---
title: My.Settings Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 54176ae6706311b17227c7dc21a5060c9b369753
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mysettings-object"></a>My.Settings Nesnesi
Özellikler ve uygulamanın ayarlarına erişmek için yöntemler sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `My.Settings` Nesne uygulamanın ayarlarına erişim sağlar ve dinamik olarak depolamak ve özellik ayarları ve uygulamanız için diğer bilgilerini almak sağlar. Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Özellikler  
 Özelliklerini `My.Settings` nesne uygulamanızın ayarlarına erişim sağlar. Ayarlar eklemek veya kaldırmak için kullanın **ayarları Tasarımcısı**.  
  
 Her ayarına sahip bir **adı**, **türü**, **kapsam**, ve **değeri**, ve bu ayarlar belirler nasıl her ayar erişmek için özelliğini görünür `My.Settings` nesnesi:  
  
-   **Ad** özelliğinin adını belirler.  
  
-   **Tür** özelliğin türünü belirler.  
  
-   **Kapsam** özelliği salt okunur olup olmadığını gösterir. Değer ise **uygulama**, özellik değeri geçerliyse salt okunur; **kullanıcı**, salt okunur bir özelliktir.  
  
-   **Değer** özelliğinin varsayılan değerdir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|---|---|  
|`Reload`|Son kaydedilen değerlerini kullanıcı ayarlarından yeniden yükler.|  
|`Save`|Geçerli kullanıcı ayarları kaydeder.|  
  
 `My.Settings` Nesnesi de sağlar Gelişmiş özellikleri ve yöntemleri, devralınan <xref:System.Configuration.ApplicationSettingsBase> sınıfı.  
  
## <a name="tasks"></a>Görevler  
 Örnekler ilgili görevleri aşağıdaki tabloda listelenmektedir `My.Settings` nesnesi.  
  
|Bitiş|Bkz. |  
|---|---|  
|Bir uygulama ayarı okuma|[Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Bir kullanıcı ayarı değiştirme|[Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Kullanıcı ayarlarını sürdürmek|[Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını sürdürmek](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Kullanıcı ayarları için özellik kılavuzu oluşturma|[Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzları oluşturma](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Örnek  
 Bu örnek değerini görüntüler `Nickname` ayarı.  
  
 [!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 Bu örnekte çalışması, uygulamanızın olmalıdır bir `Nickname` türü ayarı `String`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Configuration.ApplicationSettingsBase>  
 [Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını sürdürmek](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzları oluşturma](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
