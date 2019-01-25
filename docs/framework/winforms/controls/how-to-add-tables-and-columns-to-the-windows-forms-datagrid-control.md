---
title: 'Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme'
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
ms.openlocfilehash: be0bb6d3d7b8d8b362653257139e83900dbb2780
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717876"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="065a0-102">Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme</span><span class="sxs-lookup"><span data-stu-id="065a0-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="065a0-103"><xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="065a0-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="065a0-104">Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="065a0-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="065a0-105">Windows Forms'ta verileri görüntüleyebilirsiniz <xref:System.Windows.Forms.DataGrid> tablolar ve sütunlar oluşturarak denetiminde **DataGridTableStyle** nesneleri ve bunlara ekleme **GridTableStylesCollection** nesne üzerinden erişilen <xref:System.Windows.Forms.DataGrid> denetimin **TableStyles** özelliği.</span><span class="sxs-lookup"><span data-stu-id="065a0-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="065a0-106">Hangi veri tablosu belirtilen İçindekiler her tablo stili görüntüler **DataGridTableStyle** nesnenin **MappingName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="065a0-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="065a0-107">Varsayılan olarak, veri tablosunun tüm sütunları belirtilen hiçbir sütun stillerini sahip bir tablo stili görüntüler.</span><span class="sxs-lookup"><span data-stu-id="065a0-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="065a0-108">Tablodaki hangi sütunların ekleyerek görünür kısıtlayabilirsiniz **DataGridColumnStyle** nesneleri için **GridColumnStylesCollection** aracılığıyla erişilen nesne  **GridColumnStyles** her özellik **DataGridTableStyle** nesne.</span><span class="sxs-lookup"><span data-stu-id="065a0-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="065a0-109">DataGrid denetimine tablo ve sütun programsal olarak eklemek için</span><span class="sxs-lookup"><span data-stu-id="065a0-109">To add a table and column to a DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="065a0-110">Tablodaki verileri görüntülemek için öncelikle bağlanmalıdır <xref:System.Windows.Forms.DataGrid> denetlemek için bir veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="065a0-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="065a0-111">Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="065a0-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="065a0-112">Sütun stillerini programlı olarak belirtme, her zaman Oluştur **DataGridColumnStyle** nesneleri ve bunları Ekle **GridColumnStylesCollection** eklemeden önce nesne  **DataGridTableStyle** nesneleri için **GridTableStylesCollection** nesne.</span><span class="sxs-lookup"><span data-stu-id="065a0-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="065a0-113">Boş bir eklediğinizde **DataGridTableStyle** nesnesini koleksiyonuna **DataGridColumnStyle** nesneleri otomatik olarak üretilen sizin için.</span><span class="sxs-lookup"><span data-stu-id="065a0-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="065a0-114">Yeni eklemeyi denerseniz, bu nedenle, bir özel durum oluşturulur **DataGridColumnStyle** yinelenen nesneleriyle **MappingName** değerler **GridColumnStylesCollection**nesne.</span><span class="sxs-lookup"><span data-stu-id="065a0-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>  
  
2.  <span data-ttu-id="065a0-115">Yeni bir tablo stili bildirme ve eşleme adını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="065a0-115">Declare a new table style and set its mapping name.</span></span>  
  
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
  
3.  <span data-ttu-id="065a0-116">Yeni bir sütun stili bildirme ve eşleme adını ve diğer özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="065a0-116">Declare a new column style and set its mapping name and other properties.</span></span>  
  
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
  
4.  <span data-ttu-id="065a0-117">Çağrı **Ekle** yöntemi **GridColumnStylesCollection** nesne için tablo stili sütun eklemek için</span><span class="sxs-lookup"><span data-stu-id="065a0-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  <span data-ttu-id="065a0-118">Çağrı **Ekle** yöntemi **GridTableStylesCollection** veri kılavuzu için tablo stili eklenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="065a0-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="065a0-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="065a0-119">See also</span></span>
- [<span data-ttu-id="065a0-120">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="065a0-120">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
- [<span data-ttu-id="065a0-121">Nasıl yapılır: Silme veya Windows Forms DataGrid denetiminde sütunları gizleme</span><span class="sxs-lookup"><span data-stu-id="065a0-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
