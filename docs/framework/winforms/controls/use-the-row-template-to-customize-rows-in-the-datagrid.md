---
title: DataGridView Denetimindeki satırları özelleştirmek için satır şablonunu kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 35cb95f22c0caa654bf149b5fc4fd0395696a411
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728389"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b74e9-102">Nasıl Yapılır: Windows Forms DataGridView Denetimindeki Satırları Özelleştirmek için Satır Şablonunu Kullanma</span><span class="sxs-lookup"><span data-stu-id="b74e9-102">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b74e9-103"><xref:System.Windows.Forms.DataGridView> denetimi, veri bağlama yoluyla veya kullanılacak varolan bir satırı belirtmeden <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> yöntemini çağırdığınızda, satır şablonunu denetime eklediği tüm satırların temeli olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="b74e9-103">The <xref:System.Windows.Forms.DataGridView> control uses the row template as a basis for all rows that it adds to the control either through data binding or when you call the <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> method without specifying an existing row to use.</span></span>  
  
 <span data-ttu-id="b74e9-104">Satır şablonu, <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> özelliğin sağladığı satırların görünümü ve davranışı üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b74e9-104">The row template gives you greater control over the appearance and behavior of rows than the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property provides.</span></span> <span data-ttu-id="b74e9-105">Satır şablonuyla, <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>dahil olmak üzere herhangi bir <xref:System.Windows.Forms.DataGridViewRow> özelliğini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b74e9-105">With the row template, you can set any <xref:System.Windows.Forms.DataGridViewRow> properties, including <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span></span>  
  
 <span data-ttu-id="b74e9-106">Belirli bir etkiye ulaşmak için satır şablonunu kullanmanız gereken bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="b74e9-106">There are some situations where you must use the row template to achieve a particular effect.</span></span> <span data-ttu-id="b74e9-107">Örneğin, satır yüksekliği bilgileri bir <xref:System.Windows.Forms.DataGridViewCellStyle>depolanamaz, bu nedenle tüm satırlar tarafından kullanılan varsayılan yüksekliği değiştirmek için bir satır şablonu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b74e9-107">For example, row height information cannot be stored in a <xref:System.Windows.Forms.DataGridViewCellStyle>, so you must use a row template to change the default height used by all rows.</span></span> <span data-ttu-id="b74e9-108">Satır şablonu Ayrıca, <xref:System.Windows.Forms.DataGridViewRow> türetilen kendi sınıflarınızı oluşturduğunuzda ve denetime yeni satırlar eklendiğinde özel türü kullanmak istediğinizde de yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="b74e9-108">The row template is also useful when you create your own classes derived from <xref:System.Windows.Forms.DataGridViewRow> and you want your custom type used when new rows are added to the control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b74e9-109">Satır şablonu yalnızca satırlar eklendiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b74e9-109">The row template is used only when rows are added.</span></span> <span data-ttu-id="b74e9-110">Satır şablonunu değiştirerek mevcut satırları değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="b74e9-110">You cannot change existing rows by changing the row template.</span></span>  
  
### <a name="to-use-the-row-template"></a><span data-ttu-id="b74e9-111">Satır şablonunu kullanmak için</span><span class="sxs-lookup"><span data-stu-id="b74e9-111">To use the row template</span></span>  
  
- <span data-ttu-id="b74e9-112"><xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> özelliğinden alınan nesnedeki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b74e9-112">Set properties on the object retrieved from the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b74e9-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b74e9-113">Compiling the Code</span></span>  
 <span data-ttu-id="b74e9-114">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b74e9-114">This example requires:</span></span>  
  
- <span data-ttu-id="b74e9-115">`dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="b74e9-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="b74e9-116"><xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="b74e9-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b74e9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b74e9-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b74e9-118">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="b74e9-118">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b74e9-119">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="b74e9-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
