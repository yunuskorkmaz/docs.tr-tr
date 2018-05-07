---
title: "Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma"
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: e9d3ab96ffece3c7f441721b90c8c82c734b1405
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma
Kullanabileceğiniz `My.Settings.Save` kullanıcı ayarlarında yapılan değişiklikler kalıcı hale getirmek için yöntem.  
  
 Genellikle, uygulamalar, uygulama kapatıldığında kullanıcı ayarlarında yapılan değişiklikler kalıcı hale getirmek için tasarlanmıştır. Ayarları kaydetme, birkaç etkene bağlı olarak birkaç saniye sürebilir olmasıdır.  
  
 Daha fazla bilgi için bkz: [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Değiştirmek ve çalışma zamanında kullanıcı kapsam ayarlarının değerleri kaydedin, ancak uygulama kapsamı ayarları salt okunurdur ve programlı olarak değiştirilemez. Aracılığıyla uygulama oluştururken, uygulama kapsamı ayarlarını değiştirebilirsiniz **Proje Tasarımcısı**, ya da uygulamanın yapılandırma dosyasını düzenleyerek. Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Örnek  
 Bu örnek değerini değiştirir `LastChanged` kullanıcı ayarı ve çağırarak değiştirmek kaydeder `My.Settings.Save` yöntemi.  
  
 [!code-vb[VbVbalrMyResources#5](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-persist-user-settings_1.vb)]  
  
 Bu örnekte çalışması, uygulamanızın olmalıdır bir `LastChanged` türü kullanıcı ayarı `Date`. Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [My.Settings Nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzları oluşturma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
