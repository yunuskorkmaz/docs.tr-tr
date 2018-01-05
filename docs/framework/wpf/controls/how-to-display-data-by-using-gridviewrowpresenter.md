---
title: "Nasıl yapılır: GridViewRowPresenter Kullanarak Veri Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- displaying data with GridViewRowPresenter [WPF]
- GridViewRowPresenter [WPF]
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f540ad92c69219a2c22763403ce4ecc734c8e5cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a><span data-ttu-id="41203-102">Nasıl yapılır: GridViewRowPresenter Kullanarak Veri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="41203-102">How to: Display Data by Using GridViewRowPresenter</span></span>
<span data-ttu-id="41203-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.GridViewRowPresenter> ve <xref:System.Windows.Controls.GridViewHeaderRowPresenter> sütunlarda verileri görüntülemek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="41203-103">This example shows how to use the <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects to display data in columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41203-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="41203-104">Example</span></span>  
 <span data-ttu-id="41203-105">Aşağıdaki örnekte nasıl belirtileceğini gösterir bir <xref:System.Windows.Controls.GridViewColumnCollection> görüntüleyen <xref:System.DateTime.DayOfWeek%2A> ve <xref:System.DateTime.Year%2A> , bir <xref:System.DateTime> kullanarak nesne <xref:System.Windows.Controls.GridViewRowPresenter> ve <xref:System.Windows.Controls.GridViewHeaderRowPresenter> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="41203-105">The following example shows how to specify a <xref:System.Windows.Controls.GridViewColumnCollection> that displays the <xref:System.DateTime.DayOfWeek%2A> and <xref:System.DateTime.Year%2A> of a <xref:System.DateTime> object by using <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects.</span></span> <span data-ttu-id="41203-106">Örnek ayrıca tanımlar bir <xref:System.Windows.Style> için <xref:System.Windows.Controls.GridViewColumn.Header%2A> , bir <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="41203-106">The example also defines a <xref:System.Windows.Style> for the <xref:System.Windows.Controls.GridViewColumn.Header%2A> of a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a><span data-ttu-id="41203-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41203-107">See Also</span></span>  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewColumnCollection>  
 [<span data-ttu-id="41203-108">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="41203-108">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
