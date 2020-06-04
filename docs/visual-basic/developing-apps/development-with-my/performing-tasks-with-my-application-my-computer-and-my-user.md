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
ms.openlocfilehash: 55961d6857b690fc2726f541df8a5497a3207928
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411700"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="91a42-102">My.Application, My.Computer ve My.User ile Görev Gerçekleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91a42-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>

<span data-ttu-id="91a42-103">`My`Bilgilere ve yaygın olarak kullanılan işlevlere erişim sağlayan üç merkezi nesne `My.Application` ( <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> ), `My.Computer` ( <xref:Microsoft.VisualBasic.Devices.Computer> ) ve `My.User` ( <xref:Microsoft.VisualBasic.ApplicationServices.User> ).</span><span class="sxs-lookup"><span data-stu-id="91a42-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="91a42-104">Bu nesneleri, geçerli uygulamayla, uygulamanın yüklendiği bilgisayarın veya uygulamanın geçerli kullanıcısı ile ilgili bilgilere erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91a42-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="91a42-105">My. Application, My. Computer ve My. User</span><span class="sxs-lookup"><span data-stu-id="91a42-105">My.Application, My.Computer, and My.User</span></span>  

 <span data-ttu-id="91a42-106">Aşağıdaki örneklerde, kullanılarak bilgilerin nasıl alınacağı gösterilmektedir `My` .</span><span class="sxs-lookup"><span data-stu-id="91a42-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 <span data-ttu-id="91a42-107">Bilgileri almanın yanı sıra, bu üç nesne aracılığıyla kullanıma sunulan üyeler de bu nesneyle ilgili yöntemleri yürütmelerine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="91a42-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="91a42-108">Örneğin, dosyaları işlemek veya kayıt defterini ile güncelleştirmek için çeşitli yöntemlere erişebilirsiniz `My.Computer` .</span><span class="sxs-lookup"><span data-stu-id="91a42-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="91a42-109">Dosya g/ç `My` , dosya, dizin ve sürücü işleme için çeşitli yöntemler ve özellikler içeren çok daha kolay ve hızlı bir şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="91a42-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="91a42-110"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser>Nesnesi, ayrılmış veya sabit genişlikte alanları olan büyük yapılandırılmış dosyalardan okumanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="91a42-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="91a42-111">Bu örnek öğesini açar `TextFieldParser` `reader` ve öğesinden okumak için kullanır `C:\TestFolder1\test1.txt` .</span><span class="sxs-lookup"><span data-stu-id="91a42-111">This example opens the `TextFieldParser` `reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 <span data-ttu-id="91a42-112">`My.Application`uygulamanız için kültürü değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="91a42-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="91a42-113">Aşağıdaki örnek, bu yöntemin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="91a42-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="91a42-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91a42-114">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="91a42-115">My Özellikleri Proje Türüne Nasıl Bağımlıdır</span><span class="sxs-lookup"><span data-stu-id="91a42-115">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)
