---
title: "Visual Basic ile Projeleri Özelleştirme ve My Özelliklerini Genişletme"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 06ca80b9-1192-4eb5-8537-8ef5edfb9be0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 397b345239f8707f0129ac14ab426f93372b4010
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="customizing-projects-and-extending-my-with-visual-basic"></a><span data-ttu-id="5a548-102">Visual Basic ile Projeleri Özelleştirme ve My Özelliklerini Genişletme</span><span class="sxs-lookup"><span data-stu-id="5a548-102">Customizing Projects and Extending My with Visual Basic</span></span>
<span data-ttu-id="5a548-103">Ek sağlamak üzere proje şablonları özelleştirebilirsiniz `My` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5a548-103">You can customize project templates to provide additional `My` objects.</span></span> <span data-ttu-id="5a548-104">Bu, nesnelerinizi bulabilir ve diğer geliştiriciler için kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="5a548-104">This makes it easy for other developers to find and use your objects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a548-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5a548-105">In This Section</span></span>  
 [<span data-ttu-id="5a548-106">Genişletme Visual Basic'te My Namespace</span><span class="sxs-lookup"><span data-stu-id="5a548-106">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)  
 <span data-ttu-id="5a548-107">Özel üye eklemeyi açıklar ve değerler `My` Visual Basic'de ad alanı.</span><span class="sxs-lookup"><span data-stu-id="5a548-107">Describes how to add custom members and values to the `My` namespace in Visual Basic.</span></span>  
  
 [<span data-ttu-id="5a548-108">Paketleme ve özel My uzantıları dağıtma</span><span class="sxs-lookup"><span data-stu-id="5a548-108">Packaging and Deploying Custom My Extensions</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)  
 <span data-ttu-id="5a548-109">Özel yayımlama açıklanır `My` Visual Studio şablonları kullanarak ad alanı uzantıları.</span><span class="sxs-lookup"><span data-stu-id="5a548-109">Describes how to publish custom `My` namespace extensions by using Visual Studio templates.</span></span>  
  
 [<span data-ttu-id="5a548-110">Visual Basic uygulama modelini genişletme</span><span class="sxs-lookup"><span data-stu-id="5a548-110">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 <span data-ttu-id="5a548-111">Üyeleri geçersiz kılarak uygulama modeli için kendi uzantılarını belirtmek açıklar <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5a548-111">Describes how to specify your own extensions to the application model by overriding members of the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class.</span></span>  
  
 [<span data-ttu-id="5a548-112">Özelleştirme hangi nesnelerin kullanılabilir olduğunu My</span><span class="sxs-lookup"><span data-stu-id="5a548-112">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 <span data-ttu-id="5a548-113">Hangi denetlemek açıklar `My` nesneleri, projenizin _MYTYPE koşullu derleme sabiti ayarlayarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5a548-113">Describes how to control which `My` objects are enabled by setting your project's _MYTYPE conditional-compilation constant.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5a548-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="5a548-114">Related Sections</span></span>  
 [<span data-ttu-id="5a548-115">İle geliştirme My</span><span class="sxs-lookup"><span data-stu-id="5a548-115">Development with My</span></span>](../../../visual-basic/developing-apps/development-with-my/index.md)  
 <span data-ttu-id="5a548-116">Açıklayan `My` nesneleri, varsayılan olarak farklı proje türleri de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5a548-116">Describes which `My` objects are available in different project types by default.</span></span>  
  
 [<span data-ttu-id="5a548-117">Visual Basic uygulama modeline genel bakış</span><span class="sxs-lookup"><span data-stu-id="5a548-117">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="5a548-118">Windows Forms uygulamaları davranışını denetlemek için Visual Basic'ın modeli açıklar.</span><span class="sxs-lookup"><span data-stu-id="5a548-118">Describes Visual Basic's model for controlling the behavior of Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="5a548-119">Nasıl My proje türüne göre değişir</span><span class="sxs-lookup"><span data-stu-id="5a548-119">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)  
 <span data-ttu-id="5a548-120">Açıklayan `My` nesneleri, varsayılan olarak farklı proje türleri de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5a548-120">Describes which `My` objects are available in different project types by default.</span></span>  
  
 [<span data-ttu-id="5a548-121">Koşullu derleme</span><span class="sxs-lookup"><span data-stu-id="5a548-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="5a548-122">Koşullu derleme derleyici Kodu derlemek ve diğer bölümler hariç tutmak için belirli bölümlerini seçmek için nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5a548-122">Discusses how the compiler uses conditional-compilation to select particular sections of code to compile and exclude other sections.</span></span>  
  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <span data-ttu-id="5a548-123">Açıklar `My` özellikleri, yöntemleri ve olayları sağlayan nesne geçerli uygulamaya ilgili.</span><span class="sxs-lookup"><span data-stu-id="5a548-123">Describes the `My` object that provides properties, methods, and events related to the current application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a548-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a548-124">See Also</span></span>  
 [<span data-ttu-id="5a548-125">Visual Basic ile uygulamaları geliştirme</span><span class="sxs-lookup"><span data-stu-id="5a548-125">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)
