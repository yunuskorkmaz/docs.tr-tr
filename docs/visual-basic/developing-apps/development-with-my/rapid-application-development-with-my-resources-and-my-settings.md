---
description: 'Hakkında daha fazla bilgi edinin: My. resources ve My. Settings ile hızlı uygulama geliştirme (Visual Basic)'
title: My.Resources ve My.Settings ile Hızlı Uygulama Geliştirme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 38846b3a6ac273306f588ad8b043d7f35f7230a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797932"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>My.Resources ve My.Settings ile Hızlı Uygulama Geliştirme (Visual Basic)

`My.Resources`Nesnesi, uygulamanın kaynaklarına erişim sağlar ve uygulamanıza yönelik kaynakları dinamik olarak almanızı sağlar.  
  
## <a name="retrieving-resources"></a>Kaynakları Alma  

 Ses dosyaları, simgeler, görüntüler ve dizeler gibi birçok kaynak nesne aracılığıyla alınabilir `My.Resources` . Örneğin, uygulamanın kültüre özgü kaynak dosyalarına erişebilirsiniz. Aşağıdaki örnek, formun simgesini `Form1Icon` uygulamanın kaynak dosyasında saklanan adlı simgeye ayarlar.  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 `My.Resources`Nesne yalnızca genel kaynakları kullanıma sunar. Formlarla ilişkili kaynak dosyalarına erişim sağlamaz. Form kaynaklarını formdan erişin.  
  
 Benzer şekilde, `My.Settings` nesnesi uygulamanın ayarlarına erişim sağlar ve uygulamanızın özellik ayarlarını ve diğer bilgilerini dinamik olarak depolamanızı ve almanızı sağlar. Daha fazla bilgi için bkz [. My. Resources nesnesi](../../language-reference/objects/my-resources-object.md) ve [My. Settings nesnesi](../../language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Resources Nesnesi](../../language-reference/objects/my-resources-object.md)
- [My.Settings Nesnesi](../../language-reference/objects/my-settings-object.md)
- [Uygulama Ayarlarına Erişme](../programming/app-settings/index.md)
