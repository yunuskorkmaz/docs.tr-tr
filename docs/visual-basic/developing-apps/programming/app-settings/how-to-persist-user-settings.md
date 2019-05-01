---
title: "Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma"
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 35997db52a59aeaff5a2c404ea83b15639ea23a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014381"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma
Kullanabileceğiniz `My.Settings.Save` kullanıcı ayarlarında yapılan değişiklikleri kalıcı hale getirmek için yöntemi.  
  
 Genellikle, uygulamalar, uygulama kapatıldığında yapılan kullanıcı ayarlarını kalıcı hale getirmek için tasarlanmıştır. Ayarlar kaydedilirken, birkaç etkene bağlı olarak birkaç saniye sürebilir olmasıdır.  
  
 Daha fazla bilgi için [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Değiştirin ve çalışma zamanında kullanıcı kapsamlı ayarların değerleri kaydedin olsa da, uygulama kapsamı ayarları salt okunurdur ve program aracılığıyla değiştirilemez. Uygulama kapsamı ayarları aracılığıyla uygulama oluştururken değiştirebilirsiniz **Proje Tasarımcısı**, ya da uygulama yapılandırma dosyasını düzenleyerek. Daha fazla bilgi için [uygulama ayarlarını yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Örnek  
 Bu örnekte değiştirir `LastChanged` kullanıcı ayarı ve çağırarak değiştirme kaydeder `My.Settings.Save` yöntemi.  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 Bu örneğin çalışması, uygulamanız olmalıdır bir `LastChanged` türü kullanıcı ayarı `Date`. Daha fazla bilgi için [uygulama ayarlarını yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzu oluşturma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
