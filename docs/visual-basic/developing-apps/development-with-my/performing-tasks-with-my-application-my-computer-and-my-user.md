---
description: 'Hakkında daha fazla bilgi edinin: My. Application, My. Computer ve My. User ile görev gerçekleştirme (Visual Basic)'
title: My.Application, My.Computer ve My.User ile Görev Gerçekleştirme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: 46f8e4654008b38ae98b4c61f5a0c54506e42fcd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797945"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>My.Application, My.Computer ve My.User ile Görev Gerçekleştirme (Visual Basic)

`My`Bilgilere ve yaygın olarak kullanılan işlevlere erişim sağlayan üç merkezi nesne `My.Application` ( <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> ), `My.Computer` ( <xref:Microsoft.VisualBasic.Devices.Computer> ) ve `My.User` ( <xref:Microsoft.VisualBasic.ApplicationServices.User> ). Bu nesneleri, geçerli uygulamayla, uygulamanın yüklendiği bilgisayarın veya uygulamanın geçerli kullanıcısı ile ilgili bilgilere erişmek için kullanabilirsiniz.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>My. Application, My. Computer ve My. User  

 Aşağıdaki örneklerde, kullanılarak bilgilerin nasıl alınacağı gösterilmektedir `My` .  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 Bilgileri almanın yanı sıra, bu üç nesne aracılığıyla kullanıma sunulan üyeler de bu nesneyle ilgili yöntemleri yürütmelerine olanak sağlar. Örneğin, dosyaları işlemek veya kayıt defterini ile güncelleştirmek için çeşitli yöntemlere erişebilirsiniz `My.Computer` .  
  
 Dosya g/ç `My` , dosya, dizin ve sürücü işleme için çeşitli yöntemler ve özellikler içeren çok daha kolay ve hızlı bir şekilde çalışır. <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>Nesnesi, ayrılmış veya sabit genişlikte alanları olan büyük yapılandırılmış dosyalardan okumanızı sağlar. Bu örnek öğesini açar `TextFieldParser` `reader` ve öğesinden okumak için kullanır `C:\TestFolder1\test1.txt` .  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 `My.Application` uygulamanız için kültürü değiştirmenize izin verir. Aşağıdaki örnek, bu yöntemin nasıl çağrılacağını gösterir.  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My Özellikleri Proje Türüne Nasıl Bağımlıdır](how-my-depends-on-project-type.md)
