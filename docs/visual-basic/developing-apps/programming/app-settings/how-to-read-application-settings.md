---
title: "Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: e7d909563ca7e991a51c2f921b5248aa587a83d7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823590"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma
Bir kullanıcı ayarı üzerinde ayarın özelliğine erişerek edinebilirsiniz `My.Settings` nesne.  
  
 `My.Settings` Nesnesi, her ayarın bir özellik olarak kullanıma sunar. Özellik adı ayar adı ile aynıdır ve özellik türü ayar türü ile aynıdır. Ayarın **kapsam** özelliği salt okunur; olup olmadığını gösterir özellik için bir **uygulama** kapsam ayardır sırasında özelliği salt okunur bir **kullanıcı** kapsam ayarı okunur-yazılır olmuştur. Daha fazla bilgi için [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek değeri görüntüler `Nickname` ayarı.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Bu örneğin çalışması, uygulamanız olmalıdır bir `Nickname` biriminin türü `String`. Daha fazla bilgi için [uygulama ayarlarını yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzu oluşturma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
