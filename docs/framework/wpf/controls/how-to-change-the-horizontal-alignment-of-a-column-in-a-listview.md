---
title: "Nasıl yapılır: ListView İçerisindeki Bir Sütunun Yatay Hizalamasını Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a465ae44d3b8a4c43e5e34eaeedcd739d328bff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a><span data-ttu-id="1a217-102">Nasıl yapılır: ListView İçerisindeki Bir Sütunun Yatay Hizalamasını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="1a217-102">How to: Change the Horizontal Alignment of a Column in a ListView</span></span>
<span data-ttu-id="1a217-103">Varsayılan olarak, her bir sütunun içeriğini bir <xref:System.Windows.Controls.ListViewItem> sola hizalı değil.</span><span class="sxs-lookup"><span data-stu-id="1a217-103">By default, the content of each column in a <xref:System.Windows.Controls.ListViewItem> is left-aligned.</span></span> <span data-ttu-id="1a217-104">Her sütunun hizalamasını sağlayarak değiştirebileceğiniz bir <xref:System.Windows.DataTemplate> ve ayarı <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> öğe içinde özellikte <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="1a217-104">You can change the alignment of each column by providing a <xref:System.Windows.DataTemplate> and setting the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property on the element within the <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="1a217-105">Bu konuda gösterilmektedir nasıl bir <xref:System.Windows.Controls.ListView> içeriğini varsayılan ve bir sütunda hizalamasını değiştirme hizalar bir <xref:System.Windows.Controls.ListView>.</span><span class="sxs-lookup"><span data-stu-id="1a217-105">This topic shows how a <xref:System.Windows.Controls.ListView> aligns its content by default and how to change the alignment of one column in a <xref:System.Windows.Controls.ListView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a217-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a217-106">Example</span></span>  
 <span data-ttu-id="1a217-107">Aşağıdaki örnekte, verileri `Title` ve `ISBN` sütunları sola hizalı.</span><span class="sxs-lookup"><span data-stu-id="1a217-107">In the following example, the data in the `Title` and `ISBN` columns is left-aligned.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="1a217-108">Hizalamasını değiştirmek için `ISBN` sütun, belirtmeniz gerekir <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> her özellik <xref:System.Windows.Controls.ListViewItem> olan <xref:System.Windows.HorizontalAlignment.Stretch>, böylece her öğeleri <xref:System.Windows.Controls.ListViewItem> kapsayabilir veya her bir sütunun tüm genişliği boyunca konumlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1a217-108">To change the alignment of the `ISBN` column, you need to specify that the <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> property of each <xref:System.Windows.Controls.ListViewItem> is <xref:System.Windows.HorizontalAlignment.Stretch>, so that the elements in each <xref:System.Windows.Controls.ListViewItem> can span or be positioned along the entire width of each column.</span></span> <span data-ttu-id="1a217-109">Çünkü <xref:System.Windows.Controls.ListView> bağlı bir veri kaynağına ayarlayan bir stil oluşturmanız gerekir. <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="1a217-109">Because the <xref:System.Windows.Controls.ListView> is bound to a data source, you need to create a style that sets the <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>.</span></span> <span data-ttu-id="1a217-110">Ardından, kullanılacak ihtiyacınız bir <xref:System.Windows.DataTemplate> kullanmak yerine içeriği görüntülemek için <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1a217-110">Next, you need to use a <xref:System.Windows.DataTemplate> to display the content instead of using the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property.</span></span> <span data-ttu-id="1a217-111">Görüntülenecek `ISBN` her şablonunun <xref:System.Windows.DataTemplate> yalnızca içerebilir bir <xref:System.Windows.Controls.TextBlock> olan kendi <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğini <xref:System.Windows.HorizontalAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="1a217-111">To display the `ISBN` of each template, the <xref:System.Windows.DataTemplate> can just contain a <xref:System.Windows.Controls.TextBlock> that has its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property set to <xref:System.Windows.HorizontalAlignment.Right>.</span></span>  
  
 <span data-ttu-id="1a217-112">Aşağıdaki örnek, stilini tanımlar ve <xref:System.Windows.DataTemplate> yapmak gerekli `ISBN` sütunu sağa hizalı ve değişiklikleri <xref:System.Windows.Controls.GridViewColumn> başvuru <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="1a217-112">The following example defines the style and <xref:System.Windows.DataTemplate> necessary to make the `ISBN` column right-aligned, and changes the <xref:System.Windows.Controls.GridViewColumn> to reference the <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="1a217-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a217-113">See Also</span></span>  
 [<span data-ttu-id="1a217-114">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1a217-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="1a217-115">Veri Şablonu Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1a217-115">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="1a217-116">XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama</span><span class="sxs-lookup"><span data-stu-id="1a217-116">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [<span data-ttu-id="1a217-117">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1a217-117">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
