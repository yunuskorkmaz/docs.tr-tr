---
title: DataGridView Denetimindeki varsayılan Işlevsellik
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: b695883ac7ec3fb0c459adb66214b0eceab3a128
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746126"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b5291-102">Windows Forms DataGridView Denetimindeki Varsayılan İşlevler</span><span class="sxs-lookup"><span data-stu-id="b5291-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b5291-103">Windows Forms <xref:System.Windows.Forms.DataGridView> denetimi kullanıcılara önemli miktarda varsayılan işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5291-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="b5291-104">Varsayılan Işlevsellik</span><span class="sxs-lookup"><span data-stu-id="b5291-104">Default Functionality</span></span>  
 <span data-ttu-id="b5291-105">Varsayılan olarak, bir <xref:System.Windows.Forms.DataGridView> denetimi:</span><span class="sxs-lookup"><span data-stu-id="b5291-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
- <span data-ttu-id="b5291-106">Tablo dikey olarak kaydırıldığında görünür kalan sütun üst bilgilerini ve satır üstbilgilerini otomatik olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b5291-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
- <span data-ttu-id="b5291-107">Geçerli satır için seçim göstergesi içeren bir satır üst bilgisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b5291-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
- <span data-ttu-id="b5291-108">İlk hücrede seçim dikdörtgeni vardır.</span><span class="sxs-lookup"><span data-stu-id="b5291-108">Has a selection rectangle in the first cell.</span></span>  
  
- <span data-ttu-id="b5291-109">Kullanıcı sütun bölücüleri çift tıkladığında otomatik olarak yeniden boyutlandırılabileceği sütunlar içerir.</span><span class="sxs-lookup"><span data-stu-id="b5291-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
- <span data-ttu-id="b5291-110"><xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi uygulamanın `Main` yönteminden çağrıldığında Windows XP ve Windows Server 2003 ailesinden görsel stilleri otomatik olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="b5291-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="b5291-111">Ayrıca, bir <xref:System.Windows.Forms.DataGridView> denetiminin içeriği varsayılan olarak düzenlenebilir:</span><span class="sxs-lookup"><span data-stu-id="b5291-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
- <span data-ttu-id="b5291-112">Kullanıcı hücredeki F2 tuşuna çift tıkladığında veya basarsa, denetim hücreyi otomatik olarak düzenleme moduna geçirir ve hücrenin içeriğini Kullanıcı türleri olarak güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="b5291-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
- <span data-ttu-id="b5291-113">Kullanıcı kılavuzun sonuna kaydığında, Kullanıcı yeni kayıt eklemek için bir satır bulunduğunu görür.</span><span class="sxs-lookup"><span data-stu-id="b5291-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="b5291-114">Kullanıcı bu satıra tıkladığında, <xref:System.Windows.Forms.DataGridView> denetimine varsayılan değerlerle yeni bir satır eklenir.</span><span class="sxs-lookup"><span data-stu-id="b5291-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="b5291-115">Kullanıcı ESC tuşuna bastığında bu yeni satır kaybolur.</span><span class="sxs-lookup"><span data-stu-id="b5291-115">When the user presses ESC, this new row disappears.</span></span>  
  
- <span data-ttu-id="b5291-116">Kullanıcı bir satır başlığına tıklarsa, satırın tamamı seçilir.</span><span class="sxs-lookup"><span data-stu-id="b5291-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="b5291-117"><xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliğini ayarlayarak bir <xref:System.Windows.Forms.DataGridView> denetimini bir veri kaynağına bağladığınızda denetim:</span><span class="sxs-lookup"><span data-stu-id="b5291-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
- <span data-ttu-id="b5291-118">, Sütun üst bilgisi metni olarak veri kaynağının sütunlarının adlarını otomatik olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5291-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
- <span data-ttu-id="b5291-119">Veri kaynağının içeriğiyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="b5291-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="b5291-120"><xref:System.Windows.Forms.DataGridView> sütunları, veri kaynağındaki her bir sütun için otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b5291-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
- <span data-ttu-id="b5291-121">Tablodaki her bir görünür satır için bir satır oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5291-121">Creates a row for each visible row in the table.</span></span>  
  
- <span data-ttu-id="b5291-122">Kullanıcı bir sütun başlığına tıkladığında, temel alınan verilere göre satırları otomatik olarak sıralar.</span><span class="sxs-lookup"><span data-stu-id="b5291-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5291-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5291-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="b5291-124">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="b5291-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
