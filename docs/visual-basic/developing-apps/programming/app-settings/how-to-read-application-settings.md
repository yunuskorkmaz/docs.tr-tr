---
title: 'Nasıl Yapılır: Uygulama Ayarlarını Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 04726381f8d285ae61045d1624b3b41b7f47e491
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329565"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma

Nesne üzerinde ayarın özelliğine erişerek bir kullanıcı `My.Settings` ayarını okuyabilirsiniz.  
  
 Nesne `My.Settings` her ayarı bir özellik olarak ortaya çıkarır. Özellik adı ayar adı ile aynıdır ve özellik türü ayar türüyle aynıdır. Ayarın **Kapsamı** özelliğin salt okunup okunmaz olduğunu gösterir; **Bir Uygulama** kapsamı ayarı için özellik salt okunur, **Kullanıcı** kapsam ayarı için özellik okuma-yazma. Daha fazla bilgi için [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)' e bakın.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `Nickname` ayarın değerini görüntüler.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Bu örneğin çalışması için, uygulamanızın `Nickname` türünde `String`bir ayarı olması gerekir. Daha fazla bilgi için bkz: [Uygulama Ayarlarını Yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
