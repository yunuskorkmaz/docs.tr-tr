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
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="9ea21-102">My.Application, My.Computer ve My.User ile Görev Gerçekleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ea21-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>
<span data-ttu-id="9ea21-103">Üç orta `My` erişimi bilgilere ve yaygın olarak kullanılan işlevselliği sağlamak nesneler `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), ve `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span><span class="sxs-lookup"><span data-stu-id="9ea21-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="9ea21-104">Bu nesneler, sırasıyla geçerli uygulama, uygulamanın yüklü olduğu bilgisayarın veya uygulamanın, geçerli kullanıcının ilgili bilgilere erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ea21-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="9ea21-105">My.Application, My.Computer ve My.User</span><span class="sxs-lookup"><span data-stu-id="9ea21-105">My.Application, My.Computer, and My.User</span></span>  
 <span data-ttu-id="9ea21-106">Aşağıdaki örnekler nasıl bilgi olabilir gösterir kullanarak alınan `My`.</span><span class="sxs-lookup"><span data-stu-id="9ea21-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 <span data-ttu-id="9ea21-107">Bilgi almanın yanı sıra, bu üç nesnelerde gösterilen üyeler de bu nesneyle ilişkili bir yöntem yürütülemez olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ea21-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="9ea21-108">Örneği için çeşitli yöntemler dosyaları yönetmek veya kayıt defteri aracılığıyla güncelleştirmek için erişebilirsiniz `My.Computer`.</span><span class="sxs-lookup"><span data-stu-id="9ea21-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="9ea21-109">Dosya g/ç önemli ölçüde daha kolay ve hızlı `My`, yöntemleri ve özellikleri dosya, dizinler ve sürücüleri yönetmek için çeşitli içerir.</span><span class="sxs-lookup"><span data-stu-id="9ea21-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="9ea21-110"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Nesne ayrılmış büyük yapılandırılmış dosyalar veya sabit genişlikli alanlar okumanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ea21-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="9ea21-111">Bu örnek açar `TextFieldParser``reader` ve okuma için kullandığı `C:\TestFolder1\test1.txt`.</span><span class="sxs-lookup"><span data-stu-id="9ea21-111">This example opens the `TextFieldParser``reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 <span data-ttu-id="9ea21-112">`My.Application`Uygulamanız için kültürü değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="9ea21-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="9ea21-113">Aşağıdaki örnek, bu yöntem nasıl çağrılabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="9ea21-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9ea21-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ea21-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [<span data-ttu-id="9ea21-115">Nasıl My proje türüne göre değişir</span><span class="sxs-lookup"><span data-stu-id="9ea21-115">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
