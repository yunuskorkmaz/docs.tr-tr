---
title: "GridView Sütun Üstbilgi Stil ve Şablonlarına Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 996d6d5f531a866d4fc80acc3848cdf264901032
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="gridview-column-header-styles-and-templates-overview"></a><span data-ttu-id="c6bcb-102">GridView Sütun Üstbilgi Stil ve Şablonlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c6bcb-102">GridView Column Header Styles and Templates Overview</span></span>
<span data-ttu-id="c6bcb-103">Bu genel bir sütun başlığını özelleştirmek için kullandığınız özellikler için öncelik sırasını açıklar <xref:System.Windows.Controls.GridView> görüntüleme modu, bir <xref:System.Windows.Controls.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-103">This overview discusses the order of precedence for properties that you use to customize a column header in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="customizing-a-column-header-in-a-gridview"></a><span data-ttu-id="c6bcb-104">GridView içinde bir sütun başlığını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c6bcb-104">Customizing a Column Header in a GridView</span></span>  
 <span data-ttu-id="c6bcb-105">İçerik, Düzen ve bir sütun başlığına stilini tanımlayan özellikleri bir <xref:System.Windows.Controls.GridView> üzerinde birçok ilişkili sınıflar bulunur.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-105">The properties that define the content, layout, and style of a column header in a <xref:System.Windows.Controls.GridView> are found on many related classes.</span></span> <span data-ttu-id="c6bcb-106">Bu özelliklerden bazıları, benzer işlevselliği veya aynı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-106">Some of these properties have functionality that is similar or the same.</span></span>  
  
 <span data-ttu-id="c6bcb-107">Aşağıdaki tabloda satır grupları aynı işlevi gerçekleştirir özellikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-107">The rows in the following table show groups of properties that perform the same function.</span></span> <span data-ttu-id="c6bcb-108">Bu özellikler sütun başlıklarının özelleştirmek için kullanabileceğiniz bir <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-108">You can use these properties to customize the column headers in a <xref:System.Windows.Controls.GridView>.</span></span> <span data-ttu-id="c6bcb-109">Sağdan sola özelliği sağdan sağ sütundaki en yüksek önceliğe sahip olduğu ilgili özellikler için öncelik sırasını değil.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-109">The order of precedence for related properties is from right to left where the property in the farthest right column has the highest precedence.</span></span> <span data-ttu-id="c6bcb-110">Örneğin, bir <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> üzerinde ayarlanmış <xref:System.Windows.Controls.GridViewColumnHeader> nesne ve <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> ilişkili üzerinde ayarlandı <xref:System.Windows.Controls.GridViewColumn>, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-110">For example, if a <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> is set on the <xref:System.Windows.Controls.GridViewColumnHeader> object and the <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> is set on the associated <xref:System.Windows.Controls.GridViewColumn>, the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> takes precedence.</span></span> <span data-ttu-id="c6bcb-111">Bu senaryoda, <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-111">In this scenario, the <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> has no effect.</span></span>  
  
 <span data-ttu-id="c6bcb-112">**GridView içinde sütun üstbilgilerinin ilgili özellikleri**</span><span class="sxs-lookup"><span data-stu-id="c6bcb-112">**Related properties for column headers in a GridView**</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="c6bcb-113">**Sınıflar**</span><span class="sxs-lookup"><span data-stu-id="c6bcb-113">**Classes**</span></span>|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|<span data-ttu-id="c6bcb-114">**Bağlam Menüsü Özellikleri**</span><span class="sxs-lookup"><span data-stu-id="c6bcb-114">**Context Menu Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|<span data-ttu-id="c6bcb-115">Geçerli değil</span><span class="sxs-lookup"><span data-stu-id="c6bcb-115">Not applicable</span></span>|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|<span data-ttu-id="c6bcb-116">**Araç İpucu**</span><span class="sxs-lookup"><span data-stu-id="c6bcb-116">**ToolTip**</span></span><br /><br /> <span data-ttu-id="c6bcb-117">**Özellikler**</span><span class="sxs-lookup"><span data-stu-id="c6bcb-117">**Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|<span data-ttu-id="c6bcb-118">Geçerli değil</span><span class="sxs-lookup"><span data-stu-id="c6bcb-118">Not applicable</span></span>|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|<span data-ttu-id="c6bcb-119">**Üstbilgi şablonu**</span><span class="sxs-lookup"><span data-stu-id="c6bcb-119">**Header Template**</span></span><br /><br /> <span data-ttu-id="c6bcb-120">**Özellikler**</span><span class="sxs-lookup"><span data-stu-id="c6bcb-120">**Properties**</span></span>|<span data-ttu-id="c6bcb-121"><xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="c6bcb-121"><xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<span data-ttu-id="c6bcb-122"><xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="c6bcb-122"><xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<span data-ttu-id="c6bcb-123"><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="c6bcb-123"><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|<span data-ttu-id="c6bcb-124">**Stil özellikleri**</span><span class="sxs-lookup"><span data-stu-id="c6bcb-124">**Style Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <span data-ttu-id="c6bcb-125"><sup>1</sup>için **Üstbilgi Şablon Özellikleri**, ayarlarsanız şablonu ve şablon seçici özelliklerini, şablon özelliği önceliğe.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-125"><sup>1</sup>For **Header Template Properties**, if you set both the template and template selector properties, the template property takes precedence.</span></span> <span data-ttu-id="c6bcb-126">Örneğin, her ikisini de ayarlarsanız <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> ve <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> özelliklerini <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özelliği önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-126">For example, if you set both the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> and <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> properties, the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6bcb-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6bcb-127">See Also</span></span>  
 [<span data-ttu-id="c6bcb-128">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="c6bcb-128">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="c6bcb-129">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c6bcb-129">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="c6bcb-130">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c6bcb-130">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
