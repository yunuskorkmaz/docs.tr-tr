---
title: "Windows Forms DataGridView Denetimindeki Varsayılan İşlevler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d6b15085c301f074ef6fcf9e60a75299c4b245b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6108d-102">Windows Forms DataGridView Denetimindeki Varsayılan İşlevler</span><span class="sxs-lookup"><span data-stu-id="6108d-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6108d-103">Windows Forms <xref:System.Windows.Forms.DataGridView> denetim kullanıcılara bir miktarda varsayılan işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="6108d-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="6108d-104">Varsayılan işlevsellik</span><span class="sxs-lookup"><span data-stu-id="6108d-104">Default Functionality</span></span>  
 <span data-ttu-id="6108d-105">Varsayılan olarak, bir <xref:System.Windows.Forms.DataGridView> denetimi:</span><span class="sxs-lookup"><span data-stu-id="6108d-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <span data-ttu-id="6108d-106">Sütun üstbilgileri ve tablo dikey kayarken görünür kalmasını satır üstbilgilerinin otomatik olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6108d-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
-   <span data-ttu-id="6108d-107">Geçerli satır için bir seçim gösterge içeren bir satır üstbilgisi vardır.</span><span class="sxs-lookup"><span data-stu-id="6108d-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
-   <span data-ttu-id="6108d-108">Seçim dikdörtgeninin ilk hücreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6108d-108">Has a selection rectangle in the first cell.</span></span>  
  
-   <span data-ttu-id="6108d-109">Kullanıcı sütun Bölücü tıkladığında, otomatik olarak yeniden boyutlandırılabilir sütun içeriyor.</span><span class="sxs-lookup"><span data-stu-id="6108d-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
-   <span data-ttu-id="6108d-110">Windows XP ve Windows Server 2003 ailesinin görsel stiller otomatik olarak destekler, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi uygulamanın çağrılır `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6108d-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="6108d-111">Ayrıca, içeriğini bir <xref:System.Windows.Forms.DataGridView> denetim varsayılan olarak düzenlenebilir:</span><span class="sxs-lookup"><span data-stu-id="6108d-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
-   <span data-ttu-id="6108d-112">Kullanıcı tıklattığında veya bir hücreye F2 bastığında, denetim otomatik olarak hücre düzenleme moduna geçirir ve hücre içeriğini kullanıcı türleri olarak güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="6108d-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
-   <span data-ttu-id="6108d-113">Kullanıcı Kılavuzu sonuna kadar kaydırır, kullanıcının yeni kayıtları eklemek için bir satır var olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="6108d-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="6108d-114">Kullanıcı bu satır tıkladığında, yeni bir satır eklenir <xref:System.Windows.Forms.DataGridView> varsayılan değerlerle denetim.</span><span class="sxs-lookup"><span data-stu-id="6108d-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="6108d-115">Kullanıcı ESC tuşuna bastığında, bu yeni satır kaybolur.</span><span class="sxs-lookup"><span data-stu-id="6108d-115">When the user presses ESC, this new row disappears.</span></span>  
  
-   <span data-ttu-id="6108d-116">Satırda bir başlık kullanıcı tüm satırı seçilir.</span><span class="sxs-lookup"><span data-stu-id="6108d-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="6108d-117">Bağladığınızda bir <xref:System.Windows.Forms.DataGridView> denetim ayarlayarak bir veri kaynağı için kendi <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği, denetimi:</span><span class="sxs-lookup"><span data-stu-id="6108d-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
-   <span data-ttu-id="6108d-118">Otomatik olarak veri kaynağının sütunlarının adlarını sütunu üstbilgi metni olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="6108d-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
-   <span data-ttu-id="6108d-119">Veri kaynağı içeriğiyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="6108d-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="6108d-120"><xref:System.Windows.Forms.DataGridView>sütun, veri kaynağındaki her sütun için otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6108d-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
-   <span data-ttu-id="6108d-121">Görünür her satır için bir satır bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6108d-121">Creates a row for each visible row in the table.</span></span>  
  
-   <span data-ttu-id="6108d-122">Otomatik olarak kullanıcı bir sütun başlığını tıklattığında temel alınan verilere dayalı satırları sıralar.</span><span class="sxs-lookup"><span data-stu-id="6108d-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6108d-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6108d-123">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="6108d-124">DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="6108d-124">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
