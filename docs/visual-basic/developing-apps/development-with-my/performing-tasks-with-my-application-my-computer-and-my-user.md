---
title: My.Application, My.Computer ve My.User ile Görev Gerçekleştirme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: 5340c137842591bb1f4408392e02329fb2a491ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651636"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="25ed9-102">My.Application, My.Computer ve My.User ile Görev Gerçekleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25ed9-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>
<span data-ttu-id="25ed9-103">Üç orta `My` erişim bilgileri ve yaygın olarak kullanılan işlevler sağlayan nesneler `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), ve `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span><span class="sxs-lookup"><span data-stu-id="25ed9-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="25ed9-104">Bu nesneler, geçerli uygulamayı, uygulamanın yüklendiği bilgisayarın veya uygulamanın, geçerli kullanıcının ilgili bilgileri sırasıyla erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25ed9-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="25ed9-105">My.Application, My.Computer ve My.User</span><span class="sxs-lookup"><span data-stu-id="25ed9-105">My.Application, My.Computer, and My.User</span></span>  
 <span data-ttu-id="25ed9-106">Aşağıdaki örnek bilgileri nasıl olabileceğini gösterir kullanarak `My`.</span><span class="sxs-lookup"><span data-stu-id="25ed9-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 <span data-ttu-id="25ed9-107">Bilgi almanın yanı sıra, kullanıma sunulan bu üç nesnelerde üyeleri Ayrıca bu nesneyle ilişkili bir yöntem yürütülemez olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="25ed9-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="25ed9-108">Örneğin, birçok farklı yöntemle dosyaları yönetmek veya kayıt defteri aracılığıyla güncelleştirmek için erişebilirsiniz `My.Computer`.</span><span class="sxs-lookup"><span data-stu-id="25ed9-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="25ed9-109">Dosya g/ç önemli ölçüde daha kolay ve daha hızlı bir şekilde `My`, çeşitli yöntemleri ve dosyalar, dizinler ve sürücüler yönlendirmeye yönelik özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="25ed9-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="25ed9-110"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Nesne ayrılmış büyük yapılandırılmış dosyaları ya da sabit genişlikli alanları okumanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="25ed9-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="25ed9-111">Bu örnek açılır `TextFieldParser` `reader` ve okuma için kullandığı `C:\TestFolder1\test1.txt`.</span><span class="sxs-lookup"><span data-stu-id="25ed9-111">This example opens the `TextFieldParser` `reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 <span data-ttu-id="25ed9-112">`My.Application` Uygulamanız için kültür değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="25ed9-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="25ed9-113">Aşağıdaki örnek, bu yöntem nasıl çağrılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="25ed9-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="25ed9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25ed9-114">See also</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="25ed9-115">My Özellikleri Proje Türüne Nasıl Bağımlıdır</span><span class="sxs-lookup"><span data-stu-id="25ed9-115">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
