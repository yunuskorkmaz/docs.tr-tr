---
title: My.Resources ve My.Settings ile Hızlı Uygulama Geliştirme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: ce9a5bf76ba3132f58aa40227a145d8b5bf1591d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349261"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>My.Resources ve My.Settings ile Hızlı Uygulama Geliştirme (Visual Basic)

`My.Resources` Nesnesi, uygulamanın kaynaklarına erişim sağlar ve uygulamanıza yönelik kaynakları dinamik olarak almanızı sağlar.  
  
## <a name="retrieving-resources"></a>Kaynakları Alma  

 Ses dosyaları, simgeler, görüntüler ve dizeler gibi birçok kaynak `My.Resources` nesne aracılığıyla alınabilir. Örneğin, uygulamanın kültüre özgü kaynak dosyalarına erişebilirsiniz. Aşağıdaki örnek, formun simgesini uygulamanın kaynak dosyasında saklanan adlı `Form1Icon` simgeye ayarlar.  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 `My.Resources` Nesne yalnızca genel kaynakları kullanıma sunar. Formlarla ilişkili kaynak dosyalarına erişim sağlamaz. Form kaynaklarına formdan erişmeniz gerekir.  
  
 Benzer şekilde, `My.Settings` nesnesi uygulamanın ayarlarına erişim sağlar ve uygulamanızın özellik ayarlarını ve diğer bilgilerini dinamik olarak depolamanızı ve almanızı sağlar. Daha fazla bilgi için bkz [. My. Resources nesnesi](../../../visual-basic/language-reference/objects/my-resources-object.md) ve [My. Settings nesnesi](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Resources Nesnesi](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [My.Settings Nesnesi](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Uygulama Ayarlarına Erişme](../../../visual-basic/developing-apps/programming/app-settings/index.md)
