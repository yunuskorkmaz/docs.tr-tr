---
title: My Özelliğiyle Geliştirme (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWpfExtension.Windows
helpviewer_keywords:
- My object
- My namespace
- My feature
- Visual Basic, programming in
ms.assetid: f1d04509-5e46-4551-9f9f-94334a121fca
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2cf51e1f6292a61c071fe6d92f5fcbce4be84ff4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="development-with-my-visual-basic"></a><span data-ttu-id="ec974-102">My Özelliğiyle Geliştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec974-102">Development with My (Visual Basic)</span></span>
<span data-ttu-id="ec974-103">Visual Basic üretkenliği ve güç göndermeye çalışırken kullanım kolaylığı artırmak hızlı uygulama geliştirme için yeni özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec974-103">Visual Basic provides new features for rapid application development that improve productivity and ease of use while delivering power.</span></span> <span data-ttu-id="ec974-104">Adlı bu özelliklerden birini `My`, uygulama ve onun çalışma zamanı ortamı ile ilgili nesne örneklerini bilgi ve varsayılan erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec974-104">One of these features, called `My`, provides access to information and default object instances that are related to the application and its run-time environment.</span></span> <span data-ttu-id="ec974-105">Bu bilgiler, IntelliSense aracılığıyla bulunabilir ve kullanım göre mantıksal olarak sonuçları bir biçimde düzenlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ec974-105">This information is organized in a format that is discoverable through IntelliSense and logically delineated according to use.</span></span>  
  
 <span data-ttu-id="ec974-106">Üst düzey üyeleri `My` nesneleri sunulur.</span><span class="sxs-lookup"><span data-stu-id="ec974-106">Top-level members of `My` are exposed as objects.</span></span> <span data-ttu-id="ec974-107">Her nesne için bir ad alanı ya da bir sınıf ile benzer şekilde davranır `Shared` üyeleri ve ilgili üyelerin kümesini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="ec974-107">Each object behaves similarly to a namespace or a class with `Shared` members, and it exposes a set of related members.</span></span>  
  
 <span data-ttu-id="ec974-108">Bu tablo üst düzey gösterir `My` nesneleri ve aralarındaki ilişki.</span><span class="sxs-lookup"><span data-stu-id="ec974-108">This table shows the top-level `My` objects and their relationship to each other.</span></span>  
  
 <span data-ttu-id="ec974-109">![İçin nesne modeli My](../../../visual-basic/developing-apps/development-with-my/media/myobjmodel.gif "MyObjModel")</span><span class="sxs-lookup"><span data-stu-id="ec974-109">![Object Model for My](../../../visual-basic/developing-apps/development-with-my/media/myobjmodel.gif "MyObjModel")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec974-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ec974-110">In This Section</span></span>  
 [<span data-ttu-id="ec974-111">My.Application, My.Computer ve My.User ile görev gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="ec974-111">Performing Tasks with My.Application, My.Computer, and My.User</span></span>](../../../visual-basic/developing-apps/development-with-my/performing-tasks-with-my-application-my-computer-and-my-user.md)  
 <span data-ttu-id="ec974-112">Üç Orta açıklar `My` nesneleri `My.Application`, `My.Computer`, ve `My.User`, bilgi ve işlevsellik erişim sağlar</span><span class="sxs-lookup"><span data-stu-id="ec974-112">Describes the three central `My` objects, `My.Application`, `My.Computer`, and `My.User`, which provide access to information and functionality</span></span>  
  
 [<span data-ttu-id="ec974-113">My.Forms ve My.WebServices ile sağlanan varsayılan nesne örnekleri</span><span class="sxs-lookup"><span data-stu-id="ec974-113">Default Object Instances Provided by My.Forms and My.WebServices</span></span>](../../../visual-basic/developing-apps/development-with-my/default-object-instances-provided-by-my-forms-and-my-webservices.md)  
 <span data-ttu-id="ec974-114">Açıklar `My.Forms` ve `My.WebServices` formlar, veri kaynakları ve uygulamanız tarafından kullanılan XML Web Hizmetleri için erişim sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="ec974-114">Describes the `My.Forms` and `My.WebServices` objects, which provide access to forms, data sources, and XML Web services used by your application.</span></span>  
  
 [<span data-ttu-id="ec974-115">My.Resources ve My.Settings ile hızlı uygulama geliştirme</span><span class="sxs-lookup"><span data-stu-id="ec974-115">Rapid Application Development with My.Resources and My.Settings</span></span>](../../../visual-basic/developing-apps/development-with-my/rapid-application-development-with-my-resources-and-my-settings.md)  
 <span data-ttu-id="ec974-116">Açıklar `My.Resources` ve `My.Settings` uygulamanın kaynakları ve ayarları erişim sağlamak nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ec974-116">Describes the `My.Resources` and `My.Settings` objects, which provide access to an application's resources and settings.</span></span>  
  
 [<span data-ttu-id="ec974-117">Visual Basic uygulama modeline genel bakış</span><span class="sxs-lookup"><span data-stu-id="ec974-117">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="ec974-118">Açıklar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] uygulama başlatma/kapatma modeli.</span><span class="sxs-lookup"><span data-stu-id="ec974-118">Describes the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Application Startup/Shutdown model.</span></span>  
  
 [<span data-ttu-id="ec974-119">Nasıl My proje türüne göre değişir</span><span class="sxs-lookup"><span data-stu-id="ec974-119">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)  
 <span data-ttu-id="ec974-120">Üzerinde ayrıntılarını verir `My` özellikleri farklı proje türlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ec974-120">Gives details on which `My` features are available in different project types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec974-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec974-121">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [<span data-ttu-id="ec974-122">My.Forms nesnesi</span><span class="sxs-lookup"><span data-stu-id="ec974-122">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [<span data-ttu-id="ec974-123">My.WebServices nesnesi</span><span class="sxs-lookup"><span data-stu-id="ec974-123">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)  
 [<span data-ttu-id="ec974-124">Nasıl My proje türüne göre değişir</span><span class="sxs-lookup"><span data-stu-id="ec974-124">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
