---
title: "Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea6cfc529262053daf7c8111271de2c51e9cab4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma
Bir kullanıcı ayarı üzerinde ayarın özelliğine erişerek okuyabilirsiniz `My.Settings` nesnesi.  
  
 `My.Settings` Nesne her ayar özelliği olarak kullanıma sunar. Özellik adı ayar adı ile aynıdır ve özellik türü ayar türü ile aynıdır. Ayarın **kapsam** özelliği salt okunur; olup olmadığını gösteren özelliği için bir **uygulama** kapsam ayarıdır hatayla özelliği için salt okunur bir **kullanıcı** kapsam ayarı okuma-yazma olur. Daha fazla bilgi için bkz: [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek değerini görüntüler `Nickname` ayarı.  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 Bu örnekte çalışması, uygulamanızın olmalıdır bir `Nickname` türü ayarı `String`. Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını sürdürmek](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzları oluşturma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Uygulama ayarları (.NET) yönetme](/visualstudio/ide/managing-application-settings-dotnet)
