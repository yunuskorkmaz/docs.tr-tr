---
title: "My.Application, My.Computer ve My.User ile Görev Gerçekleştirme (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d55e0b3a126f2216d005c7bddbcaefb7d8f0a580
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>My.Application, My.Computer ve My.User ile Görev Gerçekleştirme (Visual Basic)
Üç orta `My` erişimi bilgilere ve yaygın olarak kullanılan işlevselliği sağlamak nesneler `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), ve `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>). Bu nesneler, sırasıyla geçerli uygulama, uygulamanın yüklü olduğu bilgisayarın veya uygulamanın, geçerli kullanıcının ilgili bilgilere erişmek için kullanabilirsiniz.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>My.Application, My.Computer ve My.User  
 Aşağıdaki örnekler nasıl bilgi olabilir gösterir kullanarak alınan `My`.  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 Bilgi almanın yanı sıra, bu üç nesnelerde gösterilen üyeler de bu nesneyle ilişkili bir yöntem yürütülemez olanak sağlar. Örneği için çeşitli yöntemler dosyaları yönetmek veya kayıt defteri aracılığıyla güncelleştirmek için erişebilirsiniz `My.Computer`.  
  
 Dosya g/ç önemli ölçüde daha kolay ve hızlı `My`, yöntemleri ve özellikleri dosya, dizinler ve sürücüleri yönetmek için çeşitli içerir. <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Nesne ayrılmış büyük yapılandırılmış dosyalar veya sabit genişlikli alanlar okumanızı sağlar. Bu örnek açar `TextFieldParser``reader` ve okuma için kullandığı `C:\TestFolder1\test1.txt`.  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 `My.Application`Uygulamanız için kültürü değiştirmenize izin verir. Aşağıdaki örnek, bu yöntem nasıl çağrılabilir gösterir.  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [Nasıl My proje türüne göre değişir](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
