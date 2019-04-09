---
title: 'Nasıl yapılır: GridViewRowPresenter Kullanarak Veri Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- displaying data with GridViewRowPresenter [WPF]
- GridViewRowPresenter [WPF]
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
ms.openlocfilehash: 0e471df3ab6fd10417fc58ece4cdb8ff1c457c95
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149155"
---
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a><span data-ttu-id="abd66-102">Nasıl yapılır: GridViewRowPresenter Kullanarak Veri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="abd66-102">How to: Display Data by Using GridViewRowPresenter</span></span>
<span data-ttu-id="abd66-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.GridViewRowPresenter> ve <xref:System.Windows.Controls.GridViewHeaderRowPresenter> sütunlardaki verileri görüntülemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="abd66-103">This example shows how to use the <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects to display data in columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abd66-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="abd66-104">Example</span></span>  
 <span data-ttu-id="abd66-105">Aşağıdaki örnek nasıl belirtileceğini gösteren bir <xref:System.Windows.Controls.GridViewColumnCollection> görüntüleyen <xref:System.DateTime.DayOfWeek%2A> ve <xref:System.DateTime.Year%2A> , bir <xref:System.DateTime> kullanarak nesne <xref:System.Windows.Controls.GridViewRowPresenter> ve <xref:System.Windows.Controls.GridViewHeaderRowPresenter> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="abd66-105">The following example shows how to specify a <xref:System.Windows.Controls.GridViewColumnCollection> that displays the <xref:System.DateTime.DayOfWeek%2A> and <xref:System.DateTime.Year%2A> of a <xref:System.DateTime> object by using <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects.</span></span> <span data-ttu-id="abd66-106">Örnek ayrıca tanımlar bir <xref:System.Windows.Style> için <xref:System.Windows.Controls.GridViewColumn.Header%2A> , bir <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="abd66-106">The example also defines a <xref:System.Windows.Style> for the <xref:System.Windows.Controls.GridViewColumn.Header%2A> of a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a><span data-ttu-id="abd66-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abd66-107">See also</span></span>

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewColumnCollection>
- [<span data-ttu-id="abd66-108">GridView Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="abd66-108">GridView Overview</span></span>](gridview-overview.md)
