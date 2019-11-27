---
title: 'Nasıl yapılır: Kullanıcı ayarlarını değiştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: d24b6d239c894788ce67b0723b4bf034050bf307
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329623"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme

`My.Settings` nesnesindeki ayar özelliğine yeni bir değer atayarak, bir kullanıcı ayarını değiştirebilirsiniz.  
  
 `My.Settings` nesnesi her ayarı bir özellik olarak kullanıma sunar. Özellik adı, ayar adıyla aynıdır ve özellik türü ayar türüyle aynıdır. Ayarın **kapsamı** özelliğin salt okunurdur olduğunu belirler: bir **uygulama**kapsamı ayarının özelliği salt okunurdur, ancak **Kullanıcı**kapsamı ayarı özelliği okuma-yazma olur. Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Çalışma zamanında kullanıcı kapsamı ayarlarının değerlerini değiştirebilir ve kaydedebilirsiniz, ancak uygulama kapsamı ayarları salt okunurdur ve program aracılığıyla değiştirilemez. Uygulamayı **Proje tasarımcısını** kullanarak oluştururken veya uygulamanın yapılandırma dosyasını düzenleyerek, uygulama kapsamı ayarlarını değiştirebilirsiniz. Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Örnek  

 Bu örnek `Nickname` Kullanıcı ayarının değerini değiştirir.  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 Bu örneğin çalışması için, uygulamanızın `String`türünde bir `Nickname` Kullanıcı ayarı olması gerekir.  
  
 Uygulama kapandığında uygulama kullanıcı ayarlarını kaydeder. Ayarları hemen kaydetmek için `My.Settings.Save` yöntemini çağırın. Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı ayarlarını Visual Basic kalıcı hale](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)getirme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Nasıl yapılır: Visual Basic uygulama ayarlarını okuma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Nasıl yapılır: Visual Basic 'de Kullanıcı ayarlarını kalıcı hale getirme](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Nasıl yapılır: Visual Basic Kullanıcı ayarları için özellik kılavuzları oluşturma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
