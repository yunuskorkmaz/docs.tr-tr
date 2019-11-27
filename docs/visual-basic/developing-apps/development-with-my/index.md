---
title: My Özelliğiyle Geliştirme
ms.date: 07/20/2015
f1_keywords:
- My.MyWpfExtension.Windows
helpviewer_keywords:
- My object
- My namespace
- My feature
- Visual Basic, programming in
ms.assetid: f1d04509-5e46-4551-9f9f-94334a121fca
ms.openlocfilehash: 2ee9373098d4355628a43ec46302c97c26de5bf9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330279"
---
# <a name="development-with-my-visual-basic"></a><span data-ttu-id="0456c-102">My Özelliğiyle Geliştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0456c-102">Development with My (Visual Basic)</span></span>

<span data-ttu-id="0456c-103">Visual Basic, güç sunarken üretkenliği ve kullanım kolaylığını artıran hızlı uygulama geliştirmeye yönelik yeni özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="0456c-103">Visual Basic provides new features for rapid application development that improve productivity and ease of use while delivering power.</span></span> <span data-ttu-id="0456c-104">`My`olarak adlandırılan bu özelliklerden biri, uygulamayla ve onun çalışma zamanı ortamıyla ilgili bilgilere ve varsayılan nesne örneklerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="0456c-104">One of these features, called `My`, provides access to information and default object instances that are related to the application and its run-time environment.</span></span> <span data-ttu-id="0456c-105">Bu bilgiler IntelliSense aracılığıyla keşfedilmiş bir biçimde düzenlenir ve kullanımına göre mantıksal olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0456c-105">This information is organized in a format that is discoverable through IntelliSense and logically delineated according to use.</span></span>  
  
 <span data-ttu-id="0456c-106">`My` üst düzey üyeleri nesneler olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="0456c-106">Top-level members of `My` are exposed as objects.</span></span> <span data-ttu-id="0456c-107">Her nesne, bir ad alanı veya `Shared` üyelere sahip bir sınıfa benzer şekilde davranır ve ilgili üyelerin bir kümesini sunar.</span><span class="sxs-lookup"><span data-stu-id="0456c-107">Each object behaves similarly to a namespace or a class with `Shared` members, and it exposes a set of related members.</span></span>  
  
 <span data-ttu-id="0456c-108">Bu tabloda, üst düzey `My` nesneleri ve bunların birbirleriyle ilişkileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0456c-108">This table shows the top-level `My` objects and their relationship to each other.</span></span>  
  
 ![Diyagram, My için nesne modelini gösterir.](./media/index/my-object-model-relationships.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="0456c-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0456c-110">In This Section</span></span>  

 [<span data-ttu-id="0456c-111">My.Application, My.Computer ve My.User ile Görev Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="0456c-111">Performing Tasks with My.Application, My.Computer, and My.User</span></span>](../../../visual-basic/developing-apps/development-with-my/performing-tasks-with-my-application-my-computer-and-my-user.md)  
 <span data-ttu-id="0456c-112">Bilgi ve işlevlere erişim sağlayan üç merkezi `My` nesnesini, `My.Application`, `My.Computer`ve `My.User`açıklar</span><span class="sxs-lookup"><span data-stu-id="0456c-112">Describes the three central `My` objects, `My.Application`, `My.Computer`, and `My.User`, which provide access to information and functionality</span></span>  
  
 [<span data-ttu-id="0456c-113">My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri</span><span class="sxs-lookup"><span data-stu-id="0456c-113">Default Object Instances Provided by My.Forms and My.WebServices</span></span>](../../../visual-basic/developing-apps/development-with-my/default-object-instances-provided-by-my-forms-and-my-webservices.md)  
 <span data-ttu-id="0456c-114">, Uygulamanız tarafından kullanılan formlara, veri kaynaklarına ve XML Web hizmetlerine erişim sağlayan `My.Forms` ve `My.WebServices` nesnelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0456c-114">Describes the `My.Forms` and `My.WebServices` objects, which provide access to forms, data sources, and XML Web services used by your application.</span></span>  
  
 [<span data-ttu-id="0456c-115">My.Resources ve My.Settings ile Hızlı Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="0456c-115">Rapid Application Development with My.Resources and My.Settings</span></span>](../../../visual-basic/developing-apps/development-with-my/rapid-application-development-with-my-resources-and-my-settings.md)  
 <span data-ttu-id="0456c-116">Bir uygulamanın kaynaklarına ve ayarlarına erişim sağlayan `My.Resources` ve `My.Settings` nesnelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0456c-116">Describes the `My.Resources` and `My.Settings` objects, which provide access to an application's resources and settings.</span></span>  
  
 [<span data-ttu-id="0456c-117">Visual Basic Uygulama Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0456c-117">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="0456c-118">Visual Basic uygulama başlatma/kapatması modelini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0456c-118">Describes the Visual Basic Application Startup/Shutdown model.</span></span>  
  
 [<span data-ttu-id="0456c-119">My Özellikleri Proje Türüne Nasıl Bağımlıdır</span><span class="sxs-lookup"><span data-stu-id="0456c-119">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)  
 <span data-ttu-id="0456c-120">Farklı proje türlerinde hangi `My` özelliklerinin kullanılabildiği hakkında ayrıntılı bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="0456c-120">Gives details on which `My` features are available in different project types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0456c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0456c-121">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="0456c-122">My.Forms Nesnesi</span><span class="sxs-lookup"><span data-stu-id="0456c-122">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="0456c-123">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="0456c-123">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="0456c-124">My Özellikleri Proje Türüne Nasıl Bağımlıdır</span><span class="sxs-lookup"><span data-stu-id="0456c-124">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
