---
title: Projeleri özelleştirme ve My 'ı genişletme
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 06ca80b9-1192-4eb5-8537-8ef5edfb9be0
ms.openlocfilehash: e6ed43aeff90295f71590bcee180ca1e0f88e5ff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330333"
---
# <a name="customizing-projects-and-extending-my-with-visual-basic"></a><span data-ttu-id="456e4-102">Visual Basic ile Projeleri Özelleştirme ve My Özelliklerini Genişletme</span><span class="sxs-lookup"><span data-stu-id="456e4-102">Customizing Projects and Extending My with Visual Basic</span></span>

<span data-ttu-id="456e4-103">Proje şablonlarını, ek `My` nesneler sağlamak için özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="456e4-103">You can customize project templates to provide additional `My` objects.</span></span> <span data-ttu-id="456e4-104">Bu, diğer geliştiricilerin nesnelerinizi bulmasını ve kullanmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="456e4-104">This makes it easy for other developers to find and use your objects.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="456e4-105">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="456e4-105">In this section</span></span>

- [<span data-ttu-id="456e4-106">Visual Basic'te My Ad Alanını Genişletme</span><span class="sxs-lookup"><span data-stu-id="456e4-106">Extending the My Namespace in Visual Basic</span></span>](extending-the-my-namespace.md)  
 <span data-ttu-id="456e4-107">Visual Basic `My` ad alanına özel üye ve değerlerin nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="456e4-107">Describes how to add custom members and values to the `My` namespace in Visual Basic.</span></span>
- [<span data-ttu-id="456e4-108">My Extensions'ı Paketleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="456e4-108">Packaging and Deploying Custom My Extensions</span></span>](packaging-and-deploying-custom-my-extensions.md)  
 <span data-ttu-id="456e4-109">Visual Studio şablonları kullanarak özel `My` ad alanı uzantılarının nasıl yayımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="456e4-109">Describes how to publish custom `My` namespace extensions by using Visual Studio templates.</span></span>
- [<span data-ttu-id="456e4-110">Visual Basic Uygulama Modelini Genişletme</span><span class="sxs-lookup"><span data-stu-id="456e4-110">Extending the Visual Basic Application Model</span></span>](extending-the-visual-basic-application-model.md)  
 <span data-ttu-id="456e4-111"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> Sınıfının üyelerini geçersiz kılarak uygulama modeli için kendi uzantılarınızın nasıl belirtileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="456e4-111">Describes how to specify your own extensions to the application model by overriding members of the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class.</span></span>
- [<span data-ttu-id="456e4-112">My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="456e4-112">Customizing Which Objects are Available in My</span></span>](customizing-which-objects-are-available-in-my.md)  
 <span data-ttu-id="456e4-113">Projenizin \_MyType koşullu derleme `My` sabiti ayarlanarak hangi nesnelerin etkinleştirildiğini nasıl denetleyebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="456e4-113">Describes how to control which `My` objects are enabled by setting your project's \_MYTYPE conditional-compilation constant.</span></span>

## <a name="related-sections"></a><span data-ttu-id="456e4-114">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="456e4-114">Related sections</span></span>

- [<span data-ttu-id="456e4-115">My Özelliğiyle Geliştirme</span><span class="sxs-lookup"><span data-stu-id="456e4-115">Development with My</span></span>](../development-with-my/index.md)  
 <span data-ttu-id="456e4-116">Varsayılan olarak `My` farklı proje türlerinde hangi nesnelerin kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="456e4-116">Describes which `My` objects are available in different project types by default.</span></span>
- [<span data-ttu-id="456e4-117">Visual Basic Uygulama Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="456e4-117">Overview of the Visual Basic Application Model</span></span>](../development-with-my/overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="456e4-118">Windows Forms uygulamalarının davranışını denetlemek için Visual Basic modelini açıklar.</span><span class="sxs-lookup"><span data-stu-id="456e4-118">Describes Visual Basic's model for controlling the behavior of Windows Forms applications.</span></span>
- [<span data-ttu-id="456e4-119">My Özellikleri Proje Türüne Nasıl Bağımlıdır</span><span class="sxs-lookup"><span data-stu-id="456e4-119">How My Depends on Project Type</span></span>](../development-with-my/how-my-depends-on-project-type.md)  
 <span data-ttu-id="456e4-120">Varsayılan olarak `My` farklı proje türlerinde hangi nesnelerin kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="456e4-120">Describes which `My` objects are available in different project types by default.</span></span>
- [<span data-ttu-id="456e4-121">Koşullu derleme</span><span class="sxs-lookup"><span data-stu-id="456e4-121">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="456e4-122">Derleyicinin diğer bölümleri derlemek ve hariç tutmak için kodun belirli bölümlerini seçmek üzere koşullu derlemeyi nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="456e4-122">Discusses how the compiler uses conditional-compilation to select particular sections of code to compile and exclude other sections.</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <span data-ttu-id="456e4-123">Geçerli uygulamayla `My` ilgili özellikleri, yöntemleri ve olayları sağlayan nesneyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="456e4-123">Describes the `My` object that provides properties, methods, and events related to the current application.</span></span>

## <a name="see-also"></a><span data-ttu-id="456e4-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="456e4-124">See also</span></span>

- [<span data-ttu-id="456e4-125">Visual Basic ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="456e4-125">Developing Applications with Visual Basic</span></span>](../index.md)
