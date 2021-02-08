---
description: 'Daha fazla bilgi: nasıl yapılır: Kullanıcı ayarlarını Visual Basic kalıcı hale getirme'
title: 'Nasıl yapılır: Kullanıcı Ayarlarını Kalıcı Yapma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 43ca82442678356afacb8e05149a35d485603059
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797841"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma

`My.Settings.Save`Kullanıcı ayarlarındaki değişiklikleri kalıcı hale getirmek için yöntemini kullanabilirsiniz.  
  
 Genellikle, uygulamalar, uygulama kapandığında Kullanıcı ayarlarındaki değişiklikleri kalıcı hale getirmek için tasarlanmıştır. Bunun nedeni, ayarların kaydedilmesi birkaç etmene bağlı olarak birkaç saniyeye göre yapılabilir.  
  
 Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Çalışma zamanında kullanıcı kapsamı ayarlarının değerlerini değiştirebilir ve kaydedebilirsiniz, ancak uygulama kapsamı ayarları salt okunurdur ve program aracılığıyla değiştirilemez. Uygulamayı oluştururken, **Proje Tasarımcısı** aracılığıyla veya uygulamanın yapılandırma dosyasını düzenleyerek uygulama kapsamı ayarlarını değiştirebilirsiniz. Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Örnek  

 Bu örnek, Kullanıcı ayarının değerini değiştirir `LastChanged` ve yöntemini çağırarak bu değişikliği kaydeder `My.Settings.Save` .  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 Bu örneğin çalışması için, uygulamanızın `LastChanged` türünde bir Kullanıcı ayarı olması gerekir `Date` . Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../language-reference/objects/my-settings-object.md)
- [Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma](how-to-read-application-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme](how-to-change-user-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma](how-to-create-property-grids-for-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
