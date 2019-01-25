---
title: Windows Forms DataGridView Denetimindeki Varsayılan İşlevler
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: 1b67fa4da987778b08bad59d2e2829d0a974512a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710566"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="085d2-102">Windows Forms DataGridView Denetimindeki Varsayılan İşlevler</span><span class="sxs-lookup"><span data-stu-id="085d2-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="085d2-103">Windows Forms <xref:System.Windows.Forms.DataGridView> denetimi varsayılan işlevselliği önemli ölçüde ile kullanıcılara sağlar.</span><span class="sxs-lookup"><span data-stu-id="085d2-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="085d2-104">Varsayılan işlevsellik</span><span class="sxs-lookup"><span data-stu-id="085d2-104">Default Functionality</span></span>  
 <span data-ttu-id="085d2-105">Varsayılan olarak, bir <xref:System.Windows.Forms.DataGridView> denetimi:</span><span class="sxs-lookup"><span data-stu-id="085d2-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <span data-ttu-id="085d2-106">Sütun üst bilgilerini ve tablo dikey kaydırma yaparken görünür kalmasını satır üst bilgileri otomatik olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="085d2-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
-   <span data-ttu-id="085d2-107">Seçimi göstergesi geçerli satır içeren bir satır üst bilgisi yok.</span><span class="sxs-lookup"><span data-stu-id="085d2-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
-   <span data-ttu-id="085d2-108">Seçim dikdörtgeninin ilk hücreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="085d2-108">Has a selection rectangle in the first cell.</span></span>  
  
-   <span data-ttu-id="085d2-109">Sütun ayırıcılarını kullanıcı çift tıkladığında, otomatik olarak yeniden boyutlandırılıp boyutlandırılamayacağını sütun içeriyor.</span><span class="sxs-lookup"><span data-stu-id="085d2-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
-   <span data-ttu-id="085d2-110">Görsel stiller, Windows XP ve Windows Server 2003 ailesinde otomatik olarak destekler, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi uygulamanın çağrılır `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="085d2-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="085d2-111">Ayrıca, içeriğini bir <xref:System.Windows.Forms.DataGridView> denetim varsayılan olarak düzenlenebilir:</span><span class="sxs-lookup"><span data-stu-id="085d2-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
-   <span data-ttu-id="085d2-112">Kullanıcı çift tıklamaları birbirinden ayırma ya da bir hücreye F2 tuşuna basar denetimi otomatik olarak hücre düzenleme moduna geçirir ve hücre içeriğini kullanıcı türleri olarak güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="085d2-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
-   <span data-ttu-id="085d2-113">Kullanıcı Kılavuzu sonuna kadar kaydırma ise kullanıcı yeni kayıtları eklemek için bir satır bulunduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="085d2-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="085d2-114">Kullanıcı bu satırı tıkladığında, yeni bir satır eklenir <xref:System.Windows.Forms.DataGridView> denetimiyle varsayılan değerleri.</span><span class="sxs-lookup"><span data-stu-id="085d2-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="085d2-115">Bu yeni satır, kullanıcı ESC tuşuna bastığında kaybolur.</span><span class="sxs-lookup"><span data-stu-id="085d2-115">When the user presses ESC, this new row disappears.</span></span>  
  
-   <span data-ttu-id="085d2-116">Kullanıcı bir satır üst bilgisi tıklarsa, tüm satırı seçilir.</span><span class="sxs-lookup"><span data-stu-id="085d2-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="085d2-117">Bağladığınızda bir <xref:System.Windows.Forms.DataGridView> denetim ayarlayarak bir veri kaynağı için kendi <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği, denetimi:</span><span class="sxs-lookup"><span data-stu-id="085d2-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
-   <span data-ttu-id="085d2-118">Otomatik olarak veri kaynağının sütunlarının adlarını, sütun üst bilgi metni olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="085d2-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
-   <span data-ttu-id="085d2-119">Veri kaynağının içeriğiyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="085d2-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="085d2-120"><xref:System.Windows.Forms.DataGridView> sütunlar, veri kaynağındaki her sütun için otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="085d2-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
-   <span data-ttu-id="085d2-121">Görünür her satır için bir satır bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="085d2-121">Creates a row for each visible row in the table.</span></span>  
  
-   <span data-ttu-id="085d2-122">Kullanıcı bir sütun başlığına sağ tıkladığında, temel alınan verileri temel alan satır otomatik olarak sıralar.</span><span class="sxs-lookup"><span data-stu-id="085d2-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="085d2-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="085d2-123">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="085d2-124">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="085d2-124">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
