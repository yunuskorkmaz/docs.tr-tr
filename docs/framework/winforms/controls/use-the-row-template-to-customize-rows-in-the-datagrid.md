---
title: 'Nasıl yapılır: Windows Forms DataGridView denetimindeki satırları özelleştirmek için satır şablonunu kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 215b04ce47a393a0ec3ad01957a311bc5508d24f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580245"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ebd60-102">Nasıl yapılır: Windows Forms DataGridView denetimindeki satırları özelleştirmek için satır şablonunu kullanma</span><span class="sxs-lookup"><span data-stu-id="ebd60-102">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ebd60-103"><xref:System.Windows.Forms.DataGridView> Denetimi denetimine veri bağlama aracılığıyla ya da çağırdığınızda ekler tüm satırlar için temel olarak satır şablonunu kullanır <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> kullanmak için mevcut bir satırı belirtmeden yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ebd60-103">The <xref:System.Windows.Forms.DataGridView> control uses the row template as a basis for all rows that it adds to the control either through data binding or when you call the <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> method without specifying an existing row to use.</span></span>  
  
 <span data-ttu-id="ebd60-104">Satır şablonunu görünümünü ve davranışını satır üzerinde daha fazla denetim verir <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebd60-104">The row template gives you greater control over the appearance and behavior of rows than the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property provides.</span></span> <span data-ttu-id="ebd60-105">Satır şablonla herhangi ayarlayabilirsiniz <xref:System.Windows.Forms.DataGridViewRow> özellikleri dahil olmak üzere, <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebd60-105">With the row template, you can set any <xref:System.Windows.Forms.DataGridViewRow> properties, including <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span></span>  
  
 <span data-ttu-id="ebd60-106">Burada belirli etkiyi elde etmek için satır şablonunu kullanma gerekir bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="ebd60-106">There are some situations where you must use the row template to achieve a particular effect.</span></span> <span data-ttu-id="ebd60-107">Örneğin, satır yüksekliğini bilgi içinde depolanamaz bir <xref:System.Windows.Forms.DataGridViewCellStyle>, tüm satırları tarafından kullanılan varsayılan yükseklik değiştirmek için satır şablonunu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ebd60-107">For example, row height information cannot be stored in a <xref:System.Windows.Forms.DataGridViewCellStyle>, so you must use a row template to change the default height used by all rows.</span></span> <span data-ttu-id="ebd60-108">Satır şablonunu de kendi sınıflar türetilmiş oluşturduğunuzda yararlıdır <xref:System.Windows.Forms.DataGridViewRow> ve denetime yeni satır eklendiğinde kullanılan özel türünüzü istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="ebd60-108">The row template is also useful when you create your own classes derived from <xref:System.Windows.Forms.DataGridViewRow> and you want your custom type used when new rows are added to the control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebd60-109">Yalnızca satır eklendiğinde satır şablonunu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ebd60-109">The row template is used only when rows are added.</span></span> <span data-ttu-id="ebd60-110">Var olan satır satır şablonunu değiştirerek değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebd60-110">You cannot change existing rows by changing the row template.</span></span>  
  
### <a name="to-use-the-row-template"></a><span data-ttu-id="ebd60-111">İçin satır şablonunu kullanma</span><span class="sxs-lookup"><span data-stu-id="ebd60-111">To use the row template</span></span>  
  
-   <span data-ttu-id="ebd60-112">Alınan nesne üzerindeki özellikleri ayarlamak <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ebd60-112">Set properties on the object retrieved from the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ebd60-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ebd60-113">Compiling the Code</span></span>  
 <span data-ttu-id="ebd60-114">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ebd60-114">This example requires:</span></span>  
  
-   <span data-ttu-id="ebd60-115">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="ebd60-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="ebd60-116">Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="ebd60-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebd60-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebd60-117">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ebd60-118">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="ebd60-118">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ebd60-119">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="ebd60-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
