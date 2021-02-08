---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic uygulama ayarlarını okuma'
title: 'Nasıl yapılır: Uygulama Ayarlarını Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 30b5a3b0cdf3565fc8c1f0dfa19e7717a714c350
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797828"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma

Nesne üzerindeki ayara erişerek bir kullanıcı ayarını okuyabilirsiniz `My.Settings` .  
  
 `My.Settings`Nesnesi her ayarı bir özellik olarak gösterir. Özellik adı, ayar adıyla aynıdır ve özellik türü ayar türüyle aynıdır. Ayarın **kapsamı** , özelliğin salt okunurdur belirtir; bir **uygulama** kapsamı ayarının özelliği salt okunurdur, ancak bir **Kullanıcı** kapsamı ayarı özelliği okuma-yazma olur. Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../language-reference/objects/my-settings-object.md).  
  
## <a name="example"></a>Örnek  

 Bu örnek, ayarın değerini gösterir `Nickname` .  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Bu örneğin çalışması için, uygulamanızın türünde bir ayarı olması gerekir `Nickname` `String` . Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../language-reference/objects/my-settings-object.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme](how-to-change-user-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma](how-to-persist-user-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma](how-to-create-property-grids-for-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
