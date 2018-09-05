---
title: My.Settings nesnesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 83bba35340a917b649369fc1eb7a01a2bc6a2188
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43557286"
---
# <a name="mysettings-object"></a>My.Settings Nesnesi
Özellikler ve uygulama ayarlarının erişmek için yöntemler sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `My.Settings` Nesne uygulamanın ayarlarına erişim sağlar ve dinamik olarak depolamak ve özellik ayarlarını ve uygulamanızın diğer bilgilerini almak sağlar. Daha fazla bilgi için [uygulama ayarlarını yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Özellikler  
 Özelliklerini `My.Settings` nesne, uygulamanızın ayarlarına erişim sağlar. Ayarlar eklemek veya kaldırmak için kullanın **ayarlar Tasarımcısı**.  
  
 Her ayarının bir **adı**, **türü**, **kapsam**, ve **değer**, ve bu ayarlar belirler nasıl her ayar erişmek için özelliği görünür `My.Settings` nesnesi:  
  
-   **Adı** özelliğin adını belirler.  
  
-   **Tür** özelliğin türünü belirler.  
  
-   **Kapsam** özelliği salt okunur olup olmadığını gösterir. Değer ise **uygulama**, özelliği değer ise salt okunur; **kullanıcı**, okuma-yazma özelliği.  
  
-   **Değer** özelliğinin varsayılan değerdir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|---|---|  
|`Reload`|Son kaydedilen değerler kullanıcı ayarlarının yeniden yükler.|  
|`Save`|Geçerli kullanıcı ayarları kaydeder.|  
  
 `My.Settings` Nesnesi de sağlar Gelişmiş özellikleri ve yöntemleri, devralınan <xref:System.Configuration.ApplicationSettingsBase> sınıfı.  
  
## <a name="tasks"></a>Görevler  
 Aşağıdaki tabloda, ilgili görev örnekleri listelenir `My.Settings` nesne.  
  
|Bitiş|Bkz. |  
|---|---|  
|Uygulama ayarını oku|[Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Bir kullanıcı ayarı|[Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Kullanıcı ayarlarını kalıcı yapma|[Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Kullanıcı ayarları için bir özellik kılavuzu oluşturma|[Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzu oluşturma](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Örnek  
 Bu örnek değeri görüntüler `Nickname` ayarı.  
  
 [!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 Bu örneğin çalışması, uygulamanız olmalıdır bir `Nickname` biriminin türü `String`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Configuration.ApplicationSettingsBase>  
 [Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzu oluşturma](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
