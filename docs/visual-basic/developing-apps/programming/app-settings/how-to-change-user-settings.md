---
title: "Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: db35a5d63938fcc508c23af5588957d8dc518676
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme
Kullanıcı ayarı üzerinde ayarın özelliği için yeni bir değer atayarak değiştirebileceğiniz `My.Settings` nesnesi.  
  
 `My.Settings` Nesne her ayar özelliği olarak kullanıma sunar. Özellik adı ayar adı ile aynıdır ve özellik türü ayar türü ile aynıdır. Ayarın **kapsam** özelliği salt okunur olup olmadığını belirler: özelliği için bir **uygulama**-kapsam ayarıdır hatayla özelliği için salt okunur bir **kullanıcı**-kapsamı salt okunur bir ayardır. Daha fazla bilgi için bkz: [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Değiştirmek ve çalışma zamanında kullanıcı kapsam ayarlarının değerleri kaydedin, ancak uygulama kapsamı ayarları salt okunurdur ve programlı olarak değiştirilemez. Kullanarak uygulama oluşturduğunuzda uygulama kapsamı ayarlarını değiştirebilirsiniz **Proje Tasarımcısı** ya da uygulamanın yapılandırma dosyasını düzenleyerek. Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Örnek  
 Bu örnek değerini değiştirir `Nickname` kullanıcı ayarı.  
  
 [!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-change-user-settings_1.vb)]  
  
 Bu örnekte çalışması, uygulamanızın olmalıdır bir `Nickname` türü kullanıcı ayarı `String`.  
  
 Uygulama kapatıldığında uygulama kullanıcı ayarlarını kaydeder. Ayarlar hemen kaydetmek için arama `My.Settings.Save` yöntemi. Daha fazla bilgi için bkz: [nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını sürdürmek](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzları oluşturma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Uygulama ayarları (.NET) yönetme](/visualstudio/ide/managing-application-settings-dotnet)
