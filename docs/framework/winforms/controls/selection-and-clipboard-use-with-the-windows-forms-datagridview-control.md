---
title: "Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], Clipboard use
- cells [Windows Forms], selecting in grids
- Clipboard [Windows Forms], in DataGridView control
- selection [Windows Forms], in DataGridView control
- data grids [Windows Forms], selecting cells
- DataGridView control [Windows Forms], selecting cells
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ceea4108f39619ccbcbf0286905a94b8236607cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="4439d-102">Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı</span><span class="sxs-lookup"><span data-stu-id="4439d-102">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4439d-103">`DataGridView` Denetimi, çeşitli kullanıcılar hücrelerini, satırları ve sütunları nasıl seçebilir yapılandırma seçenekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4439d-103">The `DataGridView` control provides you with a variety of options for configuring how users can select cells, rows, and columns.</span></span> <span data-ttu-id="4439d-104">Yalnızca kendi üst bilgiler, kullanıcılar'ı tıklatın, örneğin, tek veya birden çok seçim, tüm satırları veya kullanıcıların hücreleri tıkladığınızda sütun seçimi ya da tüm satır veya sütun seçimi hücre seçimi sağlayan etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4439d-104">For example, you can enable single or multiple selection, selection of whole rows or columns when users click cells, or selection of whole rows or columns only when users click their headers, which enables cell selection as well.</span></span> <span data-ttu-id="4439d-105">Seçim için kendi kullanıcı arabirimi sağlamak istiyorsanız, sıradan seçimi devre dışı bırakabilir ve tüm seçimi programlı olarak işleme.</span><span class="sxs-lookup"><span data-stu-id="4439d-105">If you want to provide your own user interface for selection, you can disable ordinary selection and handle all selection programmatically.</span></span> <span data-ttu-id="4439d-106">Ayrıca, seçilen değerleri panoya kopyalamak kullanıcıların sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4439d-106">Additionally, you can enable users to copy the selected values to the Clipboard.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4439d-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4439d-107">In This Section</span></span>  
 [<span data-ttu-id="4439d-108">Windows Forms DataGridView Denetimindeki Seçim Modları</span><span class="sxs-lookup"><span data-stu-id="4439d-108">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4439d-109">Kullanıcı ve denetiminde programlı seçimi için seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="4439d-109">Describes the options for user and programmatic selection in the control.</span></span>  
  
 [<span data-ttu-id="4439d-110">Nasıl yapılır: Windows Forms DataGridView Denetiminin Seçim Modunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="4439d-110">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4439d-111">Bir kullanıcı bir hücre tıkladığında denetiminin tek satır seçimi için nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4439d-111">Describes how to configure the control for single-row selection when a user clicks a cell.</span></span>  
  
 [<span data-ttu-id="4439d-112">Nasıl yapılır: Windows Forms DataGridView Denetiminde Seçili Hücre, Satır ve Sütunları Alma</span><span class="sxs-lookup"><span data-stu-id="4439d-112">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selected-cells-rows-and-columns-datagridview.md)  
 <span data-ttu-id="4439d-113">Seçili hücre, satır ve sütun koleksiyonlarla çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4439d-113">Describes how to work with the selected cell, row, and column collections.</span></span>  
  
 [<span data-ttu-id="4439d-114">Nasıl yapılır: Kullanıcıların Windows Forms DataGridView Denetiminden Panoya Birden Fazla Hücre Kopyalamasına Olanak Tanıma</span><span class="sxs-lookup"><span data-stu-id="4439d-114">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 <span data-ttu-id="4439d-115">Denetimdeki panoya desteğini etkinleştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="4439d-115">Describes how to enable Clipboard support in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4439d-116">Başvuru</span><span class="sxs-lookup"><span data-stu-id="4439d-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="4439d-117">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="4439d-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="4439d-118">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4439d-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <span data-ttu-id="4439d-119">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4439d-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <span data-ttu-id="4439d-120">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4439d-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <span data-ttu-id="4439d-121">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4439d-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <span data-ttu-id="4439d-122">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4439d-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4439d-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4439d-123">See Also</span></span>  
 [<span data-ttu-id="4439d-124">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="4439d-124">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="4439d-125">Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı</span><span class="sxs-lookup"><span data-stu-id="4439d-125">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
