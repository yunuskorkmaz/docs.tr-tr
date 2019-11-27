---
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
ms.openlocfilehash: fc9fd9093a3db4785bfc94719dbae9ec1d586050
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329585"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>My.Application, My.Computer ve My.User ile Görev Gerçekleştirme (Visual Basic)

Bilgilere ve yaygın olarak kullanılan işlevlere erişim sağlayan üç merkezi `My` nesnesi `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>) ve `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>). Bu nesneleri, geçerli uygulamayla, uygulamanın yüklendiği bilgisayarın veya uygulamanın geçerli kullanıcısı ile ilgili bilgilere erişmek için kullanabilirsiniz.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>My. Application, My. Computer ve My. User  

 Aşağıdaki örneklerde `My`kullanılarak bilgilerin nasıl alınacağı gösterilmektedir.  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 Bilgileri almanın yanı sıra, bu üç nesne aracılığıyla kullanıma sunulan üyeler de bu nesneyle ilgili yöntemleri yürütmelerine olanak sağlar. Örneğin, dosyaları işlemek veya kayıt defterini `My.Computer`aracılığıyla güncelleştirmek için çeşitli yöntemlere erişebilirsiniz.  
  
 Dosya g/ç, dosyaları, dizinleri ve sürücüleri işlemek için çeşitli yöntemler ve özellikler içeren `My`çok daha kolay ve hızlı bir şekilde daha hızlıdır. <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> nesnesi, ayrılmış veya sabit genişlikte alanları olan büyük yapılandırılmış dosyalardan okumanızı sağlar. Bu örnek `TextFieldParser` `reader` açar ve `C:\TestFolder1\test1.txt`okumak için onu kullanır.  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 `My.Application`, uygulamanız için kültürü değiştirmenize izin verir. Aşağıdaki örnek, bu yöntemin nasıl çağrılacağını gösterir.  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My Özellikleri Proje Türüne Nasıl Bağımlıdır](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
