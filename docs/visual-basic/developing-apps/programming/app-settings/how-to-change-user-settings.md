---
title: 'Nasıl Yapılır: Kullanıcı Ayarlarını Değiştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: d24b6d239c894788ce67b0723b4bf034050bf307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329623"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme

Nesne üzerinde ayarın özelliğine yeni bir değer atayarak kullanıcı `My.Settings` ayarını değiştirebilirsiniz.  
  
 Nesne `My.Settings` her ayarı bir özellik olarak ortaya çıkarır. Özellik adı ayar adı ile aynıdır ve özellik türü ayar türüyle aynıdır. Ayarın **Kapsamı** özelliğin salt okunup okunmayalı olduğunu belirler: **Uygulama**kapsam ayarı özelliği salt okunurken, **Kullanıcı-kapsam**ayarı özelliği okuma-yazma özelliğidir. Daha fazla bilgi için [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)' e bakın.  
  
> [!NOTE]
> Çalışma zamanında kullanıcı kapsamı ayarlarının değerlerini değiştirip kaydedebilirsiniz, ancak uygulama kapsamı ayarları salt okunur ve programlı olarak değiştirilemez. **Proje Tasarımcısı'nı** kullanarak veya uygulamanın yapılandırma dosyasını düzenleyerek uygulamayı oluştururken uygulama kapsamı ayarlarını değiştirebilirsiniz. Daha fazla bilgi için bkz: [Uygulama Ayarlarını Yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Örnek  

 Bu örnek, kullanıcı `Nickname` ayarı değerini değiştirir.  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 Bu örneğin çalışabilmesi için, uygulamanızın bir `Nickname` kullanıcı `String`ayarı olması gerekir.  
  
 Uygulama kapandığında uygulama kullanıcı ayarlarını kaydeder. Ayarları hemen kaydetmek için `My.Settings.Save` yöntemi arayın. Daha fazla bilgi için [bkz: Visual Basic'te Kullanıcı Ayarlarını Devam](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)Edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
