---
title: 'Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
ms.openlocfilehash: 70229abddb831788f521f85747db1093c941ba8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967382"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="2abdf-102">Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme</span><span class="sxs-lookup"><span data-stu-id="2abdf-102">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="2abdf-103">Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="2abdf-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="2abdf-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="2abdf-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="2abdf-105">Windows Forms <xref:System.Windows.Forms.DataGrid> denetimindeki sütunları, <xref:System.Windows.Forms.GridColumnStylesCollection> ve <xref:System.Windows.Forms.DataGridColumnStyle> nesnelerinin özelliklerini ve yöntemlerini ( <xref:System.Windows.Forms.DataGridTableStyle> sınıfının üyesi olan) kullanarak program aracılığıyla silebilir veya gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2abdf-105">You can programmatically delete or hide columns in the Windows Forms <xref:System.Windows.Forms.DataGrid> control by using the properties and methods of the <xref:System.Windows.Forms.GridColumnStylesCollection> and <xref:System.Windows.Forms.DataGridColumnStyle> objects (which are members of the <xref:System.Windows.Forms.DataGridTableStyle> class).</span></span>  
  
 <span data-ttu-id="2abdf-106">Silinen veya gizli sütunlar, kılavuzun bağlandığı veri kaynağında hala bulunur ve yine de programlı olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="2abdf-106">The deleted or hidden columns still exist in the data source the grid is bound to, and can still be accessed programmatically.</span></span> <span data-ttu-id="2abdf-107">Yalnızca DataGrid 'de görünür olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="2abdf-107">They are just no longer visible in the datagrid.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2abdf-108">Uygulamanız belirli veri sütunlarına erişmezse ve DataGrid 'de görüntülenmesini istemiyorsanız, bu durumda bunları ilk yerde veri kaynağına dahil etmek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="2abdf-108">If your application does not access certain columns of data, and you do not want them displayed in the datagrid, then it is probably not necessary to include them in the data source in the first place.</span></span>  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a><span data-ttu-id="2abdf-109">DataGrid 'den bir sütunu programlı olarak silmek için</span><span class="sxs-lookup"><span data-stu-id="2abdf-109">To delete a column from the DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="2abdf-110">Formunuzun bildirimler alanında, <xref:System.Windows.Forms.DataGridTableStyle> sınıfının yeni bir örneğini bildirin.</span><span class="sxs-lookup"><span data-stu-id="2abdf-110">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2. <span data-ttu-id="2abdf-111"><xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> Özelliğini veri kaynağınızda stilini uygulamak istediğiniz tabloya ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2abdf-111">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> property to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="2abdf-112">Aşağıdaki örnek, önceden ayarlanmış <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> olduğunu varsayan özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="2abdf-112">The following example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3. <span data-ttu-id="2abdf-113">Yeni <xref:System.Windows.Forms.DataGridTableStyle> nesneyi DataGrid 'in tablo stilleri koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2abdf-113">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4. <span data-ttu-id="2abdf-114">Silinecek sütunun sütun dizinini belirterek <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> koleksiyonunun yönteminiçağırın.<xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A></span><span class="sxs-lookup"><span data-stu-id="2abdf-114">Call the <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, specifying the column index of the column to delete.</span></span>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a><span data-ttu-id="2abdf-115">DataGrid 'deki bir sütunu programlı bir şekilde gizlemek için</span><span class="sxs-lookup"><span data-stu-id="2abdf-115">To hide a column in the DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="2abdf-116">Formunuzun bildirimler alanında, <xref:System.Windows.Forms.DataGridTableStyle> sınıfının yeni bir örneğini bildirin.</span><span class="sxs-lookup"><span data-stu-id="2abdf-116">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2. <span data-ttu-id="2abdf-117"><xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> Öğesininözelliğini,verikaynağınızdakistilini<xref:System.Windows.Forms.DataGridTableStyle> uygulamak istediğiniz tabloya ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2abdf-117">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle> to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="2abdf-118">Aşağıdaki kod örneği, zaten ayarlanmış <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> olduğunu varsayan özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="2abdf-118">The following code example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3. <span data-ttu-id="2abdf-119">Yeni <xref:System.Windows.Forms.DataGridTableStyle> nesneyi DataGrid 'in tablo stilleri koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2abdf-119">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4. <span data-ttu-id="2abdf-120">`Width` Özelliğini 0 olarak ayarlayarak ve gizlenecek sütunun sütun dizinini belirterek sütunu gizleyin.</span><span class="sxs-lookup"><span data-stu-id="2abdf-120">Hide the column by setting its `Width` property to 0, specifying the column index of the column to hide.</span></span>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2abdf-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2abdf-121">See also</span></span>

- [<span data-ttu-id="2abdf-122">Nasıl yapılır: Windows Forms DataGrid denetimindeki çalışma zamanında görünen verileri değiştirme</span><span class="sxs-lookup"><span data-stu-id="2abdf-122">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [<span data-ttu-id="2abdf-123">Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme</span><span class="sxs-lookup"><span data-stu-id="2abdf-123">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
