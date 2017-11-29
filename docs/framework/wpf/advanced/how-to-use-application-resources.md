---
title: "Nasıl yapılır: Uygulama Kaynaklarını Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 23f49481806d386bece1ad0634dd635c9eaf51f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-application-resources"></a><span data-ttu-id="7bc74-102">Nasıl yapılır: Uygulama Kaynaklarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="7bc74-102">How to: Use Application Resources</span></span>
<span data-ttu-id="7bc74-103">Bu örnek uygulama kaynaklarının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bc74-103">This example shows how to use application resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bc74-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bc74-104">Example</span></span>  
 <span data-ttu-id="7bc74-105">Aşağıdaki örnek bir uygulama tanımı dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bc74-105">The following example shows an application definition file.</span></span> <span data-ttu-id="7bc74-106">Uygulama tanımı dosyası bir kaynak bölümü tanımlar (için bir değer <xref:System.Windows.Application.Resources%2A> özelliği).</span><span class="sxs-lookup"><span data-stu-id="7bc74-106">The application definition file defines a resource section (a value for the <xref:System.Windows.Application.Resources%2A> property).</span></span> <span data-ttu-id="7bc74-107">Uygulama düzeyinde tanımlanan kaynaklara uygulamanın parçası olan diğer tüm sayfalar tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="7bc74-107">Resources defined at the application level can be accessed by all other pages that are part of the application.</span></span> <span data-ttu-id="7bc74-108">Bu durumda, bildirilen stili kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="7bc74-108">In this case, the resource is a declared style.</span></span> <span data-ttu-id="7bc74-109">Bir denetim şablonu içeren tam bir stil uzun olabileceğinden, bu örnek içinde tanımlanan denetim şablonunu atlar <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özellik ayarlayıcısı stili.</span><span class="sxs-lookup"><span data-stu-id="7bc74-109">Because a complete style that includes a control template can be lengthy, this example omits the control template that is defined within the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property setter of the style.</span></span>  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 <span data-ttu-id="7bc74-110">Aşağıdaki örnekte gösterildiği bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] önceki örnekte tanımlanan uygulama düzeyi kaynağa başvuran sayfa.</span><span class="sxs-lookup"><span data-stu-id="7bc74-110">The following example shows a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page that references the application-level resource that the previous example defined.</span></span> <span data-ttu-id="7bc74-111">Kaynağı kullanarak başvurulan bir [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) benzersiz kaynak anahtarı istenen kaynağın belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bc74-111">The resource is referenced by using a     [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) that specifies the unique resource key for the requested resource.</span></span> <span data-ttu-id="7bc74-112">İstenen kaynak için kaynak arama kapsamı geçerli sayfanın dışında ve tanımlanan uygulama düzeyi kaynakları olarak çalışmaya devam etmesi için hiçbir kaynak anahtarı "GelButton" olan geçerli sayfa bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="7bc74-112">No resource with key of "GelButton" is found in the current page, so the resource lookup scope for the requested resource continues beyond the current page and into the defined application-level resources.</span></span>  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a><span data-ttu-id="7bc74-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7bc74-113">See Also</span></span>  
 [<span data-ttu-id="7bc74-114">XAML kaynakları</span><span class="sxs-lookup"><span data-stu-id="7bc74-114">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="7bc74-115">Uygulama yönetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="7bc74-115">Application Management Overview</span></span>](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [<span data-ttu-id="7bc74-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="7bc74-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
