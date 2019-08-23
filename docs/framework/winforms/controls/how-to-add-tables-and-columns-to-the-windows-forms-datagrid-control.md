---
title: 'Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
ms.openlocfilehash: 55e30744f57364fb37c9fde5b6bade6bab60fa26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925096"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="1af3d-102">Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="1af3d-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="1af3d-103">Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="1af3d-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="1af3d-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1af3d-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="1af3d-105">**DataGridTableStyle** nesneleri oluşturarak ve bunları <xref:System.Windows.Forms.DataGrid> denetimin tarafından <xref:System.Windows.Forms.DataGrid> erişilen **GridTableStylesCollection** nesnesine ekleyerek tablo ve sütunlardaki verileri Windows Forms denetiminde görüntüleyebilirsiniz. **TableStyles** özelliği.</span><span class="sxs-lookup"><span data-stu-id="1af3d-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="1af3d-106">Her tablo stili, **DataGridTableStyle** nesnesinin **MappingName** özelliğinde belirtilen veri tablosunun içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1af3d-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="1af3d-107">Varsayılan olarak, hiçbir sütun stili belirtilmemiş bir tablo stili, bu veri tablosundaki tüm sütunları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1af3d-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="1af3d-108">Her bir **DataGridTableStyle** 'ın **GridColumnStyles** özelliğinden erişilen **GridColumnStylesCollection** nesnesine **DataGridColumnStyle** nesneleri ekleyerek tablodaki sütunların görüneceğini kısıtlayabilirsiniz nesne.</span><span class="sxs-lookup"><span data-stu-id="1af3d-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="1af3d-109">Bir DataGrid 'e programlı bir şekilde tablo ve sütun eklemek için</span><span class="sxs-lookup"><span data-stu-id="1af3d-109">To add a table and column to a DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="1af3d-110">Tablodaki verileri göstermek için öncelikle <xref:System.Windows.Forms.DataGrid> denetimi bir veri kümesine bağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1af3d-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="1af3d-111">Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGrid denetimini bir veri kaynağına](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)bağlayın.</span><span class="sxs-lookup"><span data-stu-id="1af3d-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="1af3d-112">Program aracılığıyla sütun stillerini belirtirken, her zaman **DataGridColumnStyle** nesneleri oluşturun ve bu nesneye **DataGridTableStyle** nesneleri **eklemeden önce GridColumnStylesCollection nesnesine ekleyin GridTableStylesCollection** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1af3d-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="1af3d-113">Koleksiyona boş bir **DataGridTableStyle** nesnesi eklediğinizde, sizin Için **DataGridColumnStyle** nesneleri otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1af3d-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="1af3d-114">Sonuç olarak, **GridColumnStylesCollection** nesnesine yinelenen **MappingName** değerleriyle yeni **DataGridColumnStyle** nesneleri eklemeye çalışırsanız bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1af3d-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>  
  
2. <span data-ttu-id="1af3d-115">Yeni bir tablo stili bildirin ve onun eşleme adını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1af3d-115">Declare a new table style and set its mapping name.</span></span>  
  
    ```vb  
    Dim ts1 As New DataGridTableStyle()  
    ts1.MappingName = "Customers"  
    ```  
  
    ```csharp  
    DataGridTableStyle ts1 = new DataGridTableStyle();  
    ts1.MappingName = "Customers";  
    ```  
  
    ```cpp  
    DataGridTableStyle* ts1 = new DataGridTableStyle();  
    ts1->MappingName = S"Customers";  
    ```  
  
3. <span data-ttu-id="1af3d-116">Yeni bir sütun stili bildirin ve onun eşleme adını ve diğer özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1af3d-116">Declare a new column style and set its mapping name and other properties.</span></span>  
  
    ```vb  
    Dim myDataCol As New DataGridBoolColumn()  
    myDataCol.HeaderText = "My New Column"  
    myDataCol.MappingName = "Current"  
    ```  
  
    ```csharp  
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();  
    myDataCol.HeaderText = "My New Column";  
    myDataCol.MappingName = "Current";  
    ```  
  
    ```cpp  
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();  
    myDataCol->HeaderText = "My New Column";  
    myDataCol->MappingName = "Current";  
    ```  
  
4. <span data-ttu-id="1af3d-117">Sütunu tablo stiline eklemek için **GridColumnStylesCollection** nesnesinin **Add** metodunu çağırın</span><span class="sxs-lookup"><span data-stu-id="1af3d-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5. <span data-ttu-id="1af3d-118">Tablo stilini veri kılavuzuna eklemek için **GridTableStylesCollection** nesnesinin **Add** metodunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="1af3d-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1af3d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1af3d-119">See also</span></span>

- [<span data-ttu-id="1af3d-120">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="1af3d-120">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="1af3d-121">Nasıl yapılır: Windows Forms DataGrid denetimindeki sütunları silme veya gizleme</span><span class="sxs-lookup"><span data-stu-id="1af3d-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
