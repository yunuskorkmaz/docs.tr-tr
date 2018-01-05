---
title: "Nasıl yapılır: Kaynağı Tanımlama ve Kaynağa Başvurma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 173be3048f7bf082db2eef2ea21eb1e0319f9a43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-and-reference-a-resource"></a><span data-ttu-id="72d90-102">Nasıl yapılır: Kaynağı Tanımlama ve Kaynağa Başvurma</span><span class="sxs-lookup"><span data-stu-id="72d90-102">How to: Define and Reference a Resource</span></span>
<span data-ttu-id="72d90-103">Bu örnek bir kaynak tanımlamak ve bir öznitelik kullanarak başvuru gösterilmektedir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="72d90-103">This example shows how to define a resource and reference it by using an attribute in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="72d90-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="72d90-104">Example</span></span>  
 <span data-ttu-id="72d90-105">Aşağıdaki örnek, iki tür kaynak tanımlar: bir <xref:System.Windows.Media.SolidColorBrush> kaynağı ve birkaç <xref:System.Windows.Style> kaynakları.</span><span class="sxs-lookup"><span data-stu-id="72d90-105">The following example defines two types of resources: a <xref:System.Windows.Media.SolidColorBrush> resource, and several <xref:System.Windows.Style> resources.</span></span> <span data-ttu-id="72d90-106"><xref:System.Windows.Media.SolidColorBrush> Kaynak `MyBrush` herbiri çeşitli özelliklerin değerini sağlamak için kullanılan bir <xref:System.Windows.Media.Brush> değeri yazın.</span><span class="sxs-lookup"><span data-stu-id="72d90-106">The <xref:System.Windows.Media.SolidColorBrush> resource `MyBrush` is used to provide the value of several properties that each take a <xref:System.Windows.Media.Brush> type value.</span></span> <span data-ttu-id="72d90-107"><xref:System.Windows.Style> Kaynakları `PageBackground`, `TitleText` ve `Label` her hedef belirli denetim türü.</span><span class="sxs-lookup"><span data-stu-id="72d90-107">The <xref:System.Windows.Style> resources `PageBackground`, `TitleText` and `Label` each target a particular control type.</span></span> <span data-ttu-id="72d90-108">Stil kaynağı kaynak anahtarı tarafından başvurulan ve ayarlamak için kullanılan stiller farklı özellikler çeşitli hedeflenen denetimler üzerinde ayarlanır <xref:System.Windows.FrameworkElement.Style%2A> tanımlanan birkaç özel denetim öğelerinin özellik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="72d90-108">The styles set a variety of different properties on the targeted controls, when that style resource is referenced by resource key and is used to set the <xref:System.Windows.FrameworkElement.Style%2A> property of several specific control elements defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="72d90-109">Not Bu özelliklerden birini ayarlayıcıları içindeki `Label` stili de başvuran `MyBrush` önceden tanımlanmış kaynak.</span><span class="sxs-lookup"><span data-stu-id="72d90-109">Note that one of the properties within the setters of the `Label` style also references the `MyBrush` resource defined earlier.</span></span> <span data-ttu-id="72d90-110">Bu ortak bir tekniktir, ancak kaynakları ayrıştırılır ve bir kaynak sözlüğü verildikleri sırada girilen unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="72d90-110">This is a common technique, but it is important to remember that resources are parsed and entered into a resource dictionary in the order that they are given.</span></span> <span data-ttu-id="72d90-111">Kaynaklar ayrıca kullanırsanız sözlükte bulundukları sıraya göre istenen [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) onlardan içindeki başka bir kaynak başvurmak için.</span><span class="sxs-lookup"><span data-stu-id="72d90-111">Resources are also requested by the order found within the dictionary if you use the [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) to reference them from within another resource.</span></span> <span data-ttu-id="72d90-112">Başvuru herhangi bir kaynağa burada bu kaynak ardından istenen daha kaynaklar koleksiyonu içinde daha önce tanımlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="72d90-112">Make sure that any resource that you reference is defined earlier within the resources collection than where that resource is then requested.</span></span> <span data-ttu-id="72d90-113">Gerekirse, kaynak referanslarının kesin oluşturulma sırasını kullanarak çalışabilirsiniz bir [DynamicResource Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) çalışma zamanında bunun yerine, referans için ancak, farkında olmalıdır, bu DynamicResource Teknik performans sonuçları vardır.</span><span class="sxs-lookup"><span data-stu-id="72d90-113">If necessary, you can work around the strict creation order of resource refererences by using a [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) to reference the resource at runtime instead, but you should be aware that this DynamicResource technique has performance consequences.</span></span> <span data-ttu-id="72d90-114">Ayrıntılar için bkz [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="72d90-114">For details, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a><span data-ttu-id="72d90-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="72d90-115">See Also</span></span>  
 [<span data-ttu-id="72d90-116">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="72d90-116">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="72d90-117">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="72d90-117">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
