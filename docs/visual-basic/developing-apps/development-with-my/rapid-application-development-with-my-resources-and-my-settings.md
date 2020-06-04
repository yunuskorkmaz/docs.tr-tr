---
title: My.Resources ve My.Settings ile Hızlı Uygulama Geliştirme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 6c53d11a3830a5a8a2cb898728bed8694a226686
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411674"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>My.Resources ve My.Settings ile Hızlı Uygulama Geliştirme (Visual Basic)

`My.Resources`Nesnesi, uygulamanın kaynaklarına erişim sağlar ve uygulamanıza yönelik kaynakları dinamik olarak almanızı sağlar.  
  
## <a name="retrieving-resources"></a>Kaynakları Alma  

 Ses dosyaları, simgeler, görüntüler ve dizeler gibi birçok kaynak nesne aracılığıyla alınabilir `My.Resources` . Örneğin, uygulamanın kültüre özgü kaynak dosyalarına erişebilirsiniz. Aşağıdaki örnek, formun simgesini `Form1Icon` uygulamanın kaynak dosyasında saklanan adlı simgeye ayarlar.  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 `My.Resources`Nesne yalnızca genel kaynakları kullanıma sunar. Formlarla ilişkili kaynak dosyalarına erişim sağlamaz. Form kaynaklarına formdan erişmeniz gerekir.  
  
 Benzer şekilde, `My.Settings` nesnesi uygulamanın ayarlarına erişim sağlar ve uygulamanızın özellik ayarlarını ve diğer bilgilerini dinamik olarak depolamanızı ve almanızı sağlar. Daha fazla bilgi için bkz [. My. Resources nesnesi](../../language-reference/objects/my-resources-object.md) ve [My. Settings nesnesi](../../language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Resources Nesnesi](../../language-reference/objects/my-resources-object.md)
- [My.Settings Nesnesi](../../language-reference/objects/my-settings-object.md)
- [Uygulama Ayarlarına Erişme](../programming/app-settings/index.md)
