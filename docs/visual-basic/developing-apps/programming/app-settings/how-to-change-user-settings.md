---
title: "Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme"
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 05c95026d061918b38cf301209afefa9498e33bf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820977"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme
Üzerinde yeni bir değer ayarlar özelliğine atayarak bir kullanıcı ayarı değiştirebilirsiniz `My.Settings` nesne.  
  
 `My.Settings` Nesnesi, her ayarın bir özellik olarak kullanıma sunar. Özellik adı ayar adı ile aynıdır ve özellik türü ayar türü ile aynıdır. Ayarın **kapsam** özelliği salt okunur olup olmadığını belirler: Özellik için bir **uygulama**-kapsam ayardır sırasında özelliği salt okunur bir **kullanıcı**-kapsam ayarı okuma-yazma. Daha fazla bilgi için [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Değiştirin ve çalışma zamanında kullanıcı kapsamlı ayarların değerleri kaydedin olsa da, uygulama kapsamı ayarları salt okunurdur ve program aracılığıyla değiştirilemez. Kullanarak bir uygulama oluşturduğunuzda, uygulama kapsamı ayarlarını değiştirebilirsiniz **Proje Tasarımcısı** veya uygulama yapılandırma dosyasını düzenleyerek. Daha fazla bilgi için [uygulama ayarlarını yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Örnek  
 Bu örnekte değiştirir `Nickname` kullanıcı ayarı.  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 Bu örneğin çalışması, uygulamanız olmalıdır bir `Nickname` türü kullanıcı ayarı `String`.  
  
 Uygulama kapatıldığında kullanıcı ayarlarını uygulamayı kaydeder. Hemen ayarları kaydetmek için çağrı `My.Settings.Save` yöntemi. Daha fazla bilgi için [nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzu oluşturma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
