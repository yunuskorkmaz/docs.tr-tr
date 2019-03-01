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
ms.openlocfilehash: 56d79691a216f87c847474ce4340b454850b9b11
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969706"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="68cac-102">My.Application, My.Computer ve My.User ile Görev Gerçekleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68cac-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>
<span data-ttu-id="68cac-103">Üç orta `My` erişim bilgileri ve yaygın olarak kullanılan işlevler sağlayan nesneler `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), ve `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span><span class="sxs-lookup"><span data-stu-id="68cac-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="68cac-104">Bu nesneler, geçerli uygulamayı, uygulamanın yüklendiği bilgisayarın veya uygulamanın, geçerli kullanıcının ilgili bilgileri sırasıyla erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68cac-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="68cac-105">My.Application, My.Computer ve My.User</span><span class="sxs-lookup"><span data-stu-id="68cac-105">My.Application, My.Computer, and My.User</span></span>  
 <span data-ttu-id="68cac-106">Aşağıdaki örnek bilgileri nasıl olabileceğini gösterir kullanarak `My`.</span><span class="sxs-lookup"><span data-stu-id="68cac-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 <span data-ttu-id="68cac-107">Bilgi almanın yanı sıra, kullanıma sunulan bu üç nesnelerde üyeleri Ayrıca bu nesneyle ilişkili bir yöntem yürütülemez olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="68cac-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="68cac-108">Örneğin, birçok farklı yöntemle dosyaları yönetmek veya kayıt defteri aracılığıyla güncelleştirmek için erişebilirsiniz `My.Computer`.</span><span class="sxs-lookup"><span data-stu-id="68cac-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="68cac-109">Dosya g/ç önemli ölçüde daha kolay ve daha hızlı bir şekilde `My`, çeşitli yöntemleri ve dosyalar, dizinler ve sürücüler yönlendirmeye yönelik özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="68cac-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="68cac-110"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Nesne ayrılmış büyük yapılandırılmış dosyaları ya da sabit genişlikli alanları okumanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="68cac-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="68cac-111">Bu örnek açılır `TextFieldParser` `reader` ve okuma için kullandığı `C:\TestFolder1\test1.txt`.</span><span class="sxs-lookup"><span data-stu-id="68cac-111">This example opens the `TextFieldParser` `reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 <span data-ttu-id="68cac-112">`My.Application` Uygulamanız için kültür değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="68cac-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="68cac-113">Aşağıdaki örnek, bu yöntem nasıl çağrılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="68cac-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="68cac-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68cac-114">See also</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="68cac-115">My Özellikleri Proje Türüne Nasıl Bağımlıdır</span><span class="sxs-lookup"><span data-stu-id="68cac-115">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
