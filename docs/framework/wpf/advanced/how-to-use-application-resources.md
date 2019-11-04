---
title: 'Nasıl yapılır: Uygulama Kaynaklarını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: e4114466fa8016f8e31100d7a37038b0abfdccca
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460263"
---
# <a name="how-to-use-application-resources"></a><span data-ttu-id="a6da5-102">Nasıl yapılır: Uygulama Kaynaklarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="a6da5-102">How to: Use Application Resources</span></span>
<span data-ttu-id="a6da5-103">Bu örnek, uygulama kaynaklarının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6da5-103">This example shows how to use application resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6da5-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6da5-104">Example</span></span>  
 <span data-ttu-id="a6da5-105">Aşağıdaki örnek bir uygulama tanımı dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6da5-105">The following example shows an application definition file.</span></span> <span data-ttu-id="a6da5-106">Uygulama tanımı dosyası bir kaynak bölümü tanımlar (<xref:System.Windows.Application.Resources%2A> özelliği için bir değer).</span><span class="sxs-lookup"><span data-stu-id="a6da5-106">The application definition file defines a resource section (a value for the <xref:System.Windows.Application.Resources%2A> property).</span></span> <span data-ttu-id="a6da5-107">Uygulama düzeyinde tanımlanan kaynaklara uygulamanın parçası olan diğer tüm sayfalar erişebilir.</span><span class="sxs-lookup"><span data-stu-id="a6da5-107">Resources defined at the application level can be accessed by all other pages that are part of the application.</span></span> <span data-ttu-id="a6da5-108">Bu durumda, kaynak tanımlanmış bir stildir.</span><span class="sxs-lookup"><span data-stu-id="a6da5-108">In this case, the resource is a declared style.</span></span> <span data-ttu-id="a6da5-109">Bir denetim şablonu içeren bir bütün stil uzun sürebileceğinden, bu örnek stilin <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> Özellik ayarlayıcısı içinde tanımlanan denetim şablonunu atlar.</span><span class="sxs-lookup"><span data-stu-id="a6da5-109">Because a complete style that includes a control template can be lengthy, this example omits the control template that is defined within the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property setter of the style.</span></span>  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 <span data-ttu-id="a6da5-110">Aşağıdaki örnekte, önceki örneğin tanımladığı uygulama düzeyi kaynağına başvuran bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfası gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a6da5-110">The following example shows a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page that references the application-level resource that the previous example defined.</span></span> <span data-ttu-id="a6da5-111">Kaynağa, istenen kaynak için benzersiz kaynak anahtarını belirten bir [StaticResource Işaretleme uzantısı](staticresource-markup-extension.md) kullanılarak başvurulur.</span><span class="sxs-lookup"><span data-stu-id="a6da5-111">The resource is referenced by using a     [StaticResource Markup Extension](staticresource-markup-extension.md) that specifies the unique resource key for the requested resource.</span></span> <span data-ttu-id="a6da5-112">Geçerli sayfada "GelButton" anahtarına sahip hiçbir kaynak bulunamadı. bu nedenle, istenen kaynak için kaynak arama kapsamı geçerli sayfanın ötesine ve tanımlanan uygulama düzeyi kaynaklarına devam eder.</span><span class="sxs-lookup"><span data-stu-id="a6da5-112">No resource with key of "GelButton" is found in the current page, so the resource lookup scope for the requested resource continues beyond the current page and into the defined application-level resources.</span></span>  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a><span data-ttu-id="a6da5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6da5-113">See also</span></span>

- [<span data-ttu-id="a6da5-114">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="a6da5-114">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="a6da5-115">Uygulama Yönetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6da5-115">Application Management Overview</span></span>](../app-development/application-management-overview.md)
- [<span data-ttu-id="a6da5-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="a6da5-116">How-to Topics</span></span>](resources-how-to-topics.md)
