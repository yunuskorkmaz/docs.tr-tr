---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetimindeki Satırları Özelleştirmek için Satır Şablonunu Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 0dba318e6aa35761f4e9471fdb13b65644747b57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966499"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="3c6fc-102">Nasıl yapılır: Windows Forms DataGridView Denetimindeki Satırları Özelleştirmek için Satır Şablonunu Kullanma</span><span class="sxs-lookup"><span data-stu-id="3c6fc-102">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3c6fc-103">Denetim, veri bağlama yoluyla veya kullanmak üzere varolan bir satırı belirtmeden <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> yöntemi çağırdığınızda denetime eklediği tüm satırların temeli olarak satır şablonunu kullanır. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="3c6fc-103">The <xref:System.Windows.Forms.DataGridView> control uses the row template as a basis for all rows that it adds to the control either through data binding or when you call the <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> method without specifying an existing row to use.</span></span>  
  
 <span data-ttu-id="3c6fc-104">Satır şablonu, <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> özelliğin sağladığı satırların görünümü ve davranışı üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c6fc-104">The row template gives you greater control over the appearance and behavior of rows than the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property provides.</span></span> <span data-ttu-id="3c6fc-105">Satır şablonuyla, dahil olmak üzere <xref:System.Windows.Forms.DataGridViewRow> <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>herhangi bir özelliği ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c6fc-105">With the row template, you can set any <xref:System.Windows.Forms.DataGridViewRow> properties, including <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span></span>  
  
 <span data-ttu-id="3c6fc-106">Belirli bir etkiye ulaşmak için satır şablonunu kullanmanız gereken bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="3c6fc-106">There are some situations where you must use the row template to achieve a particular effect.</span></span> <span data-ttu-id="3c6fc-107">Örneğin, satır yüksekliği bilgileri bir <xref:System.Windows.Forms.DataGridViewCellStyle>içinde depolanamaz, bu nedenle tüm satırlar tarafından kullanılan varsayılan yüksekliği değiştirmek için bir satır şablonu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c6fc-107">For example, row height information cannot be stored in a <xref:System.Windows.Forms.DataGridViewCellStyle>, so you must use a row template to change the default height used by all rows.</span></span> <span data-ttu-id="3c6fc-108">Satır şablonu Ayrıca, ' dan <xref:System.Windows.Forms.DataGridViewRow> türetilmiş kendi sınıflarınızı oluşturduğunuz ve denetime yeni satırlar eklendiğinde özel türü kullanmak istediğiniz zaman da yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3c6fc-108">The row template is also useful when you create your own classes derived from <xref:System.Windows.Forms.DataGridViewRow> and you want your custom type used when new rows are added to the control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c6fc-109">Satır şablonu yalnızca satırlar eklendiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c6fc-109">The row template is used only when rows are added.</span></span> <span data-ttu-id="3c6fc-110">Satır şablonunu değiştirerek mevcut satırları değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c6fc-110">You cannot change existing rows by changing the row template.</span></span>  
  
### <a name="to-use-the-row-template"></a><span data-ttu-id="3c6fc-111">Satır şablonunu kullanmak için</span><span class="sxs-lookup"><span data-stu-id="3c6fc-111">To use the row template</span></span>  
  
- <span data-ttu-id="3c6fc-112"><xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> Özelliğinden alınan nesnedeki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3c6fc-112">Set properties on the object retrieved from the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3c6fc-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3c6fc-113">Compiling the Code</span></span>  
 <span data-ttu-id="3c6fc-114">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3c6fc-114">This example requires:</span></span>  
  
- <span data-ttu-id="3c6fc-115"><xref:System.Windows.Forms.DataGridView> Adlı`dataGridView1`bir denetim.</span><span class="sxs-lookup"><span data-stu-id="3c6fc-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="3c6fc-116"><xref:System?displayProperty=nameWithType> ,<xref:System.Drawing?displayProperty=nameWithType>Ve derlemelerinin<xref:System.Windows.Forms?displayProperty=nameWithType> başvuruları.</span><span class="sxs-lookup"><span data-stu-id="3c6fc-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c6fc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c6fc-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3c6fc-118">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="3c6fc-118">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3c6fc-119">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="3c6fc-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
