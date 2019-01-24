---
title: "Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme"
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 3cf50f838124539dc774574cd1ad0b629d01a9ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688205"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme
Üzerinde yeni bir değer ayarlar özelliğine atayarak bir kullanıcı ayarı değiştirebilirsiniz `My.Settings` nesne.  
  
 `My.Settings` Nesnesi, her ayarın bir özellik olarak kullanıma sunar. Özellik adı ayar adı ile aynıdır ve özellik türü ayar türü ile aynıdır. Ayarın **kapsam** özelliği salt okunur olup olmadığını belirler: Özellik için bir **uygulama**-kapsam ayardır sırasında özelliği salt okunur bir **kullanıcı**-kapsam ayarı okuma-yazma. Daha fazla bilgi için [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Değiştirin ve çalışma zamanında kullanıcı kapsamlı ayarların değerleri kaydedin olsa da, uygulama kapsamı ayarları salt okunurdur ve program aracılığıyla değiştirilemez. Kullanarak bir uygulama oluşturduğunuzda, uygulama kapsamı ayarlarını değiştirebilirsiniz **Proje Tasarımcısı** veya uygulama yapılandırma dosyasını düzenleyerek. Daha fazla bilgi için [uygulama ayarlarını yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Örnek  
 Bu örnekte değiştirir `Nickname` kullanıcı ayarı.  
  
 [!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-change-user-settings_1.vb)]  
  
 Bu örneğin çalışması, uygulamanız olmalıdır bir `Nickname` türü kullanıcı ayarı `String`.  
  
 Uygulama kapatıldığında kullanıcı ayarlarını uygulamayı kaydeder. Hemen ayarları kaydetmek için çağrı `My.Settings.Save` yöntemi. Daha fazla bilgi için [nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [My.Settings Nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzu oluşturma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
