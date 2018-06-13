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
ms.openlocfilehash: fc8161ea29da92f5dcc2e76f956f3fecd6140acc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527725"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="1b8ce-102">Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="1b8ce-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="1b8ce-103"><xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="1b8ce-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="1b8ce-104">Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1b8ce-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="1b8ce-105">Windows Forms'ta verileri görüntüleyebilir <xref:System.Windows.Forms.DataGrid> tablolar ve sütunlar oluşturarak denetiminde **DataGridTableStyle** nesneleri ve bunlara ekleme **GridTableStylesCollection** nesne üzerinden erişilen <xref:System.Windows.Forms.DataGrid> denetimin **TableStyles** özelliği.</span><span class="sxs-lookup"><span data-stu-id="1b8ce-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="1b8ce-106">Hangi veri tablosu belirtilen İçindekiler her tablo stili görüntüler **DataGridTableStyle** nesnenin **MappingName** özelliği.</span><span class="sxs-lookup"><span data-stu-id="1b8ce-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="1b8ce-107">Varsayılan olarak, bu veri tablosu içindeki tüm sütunlar belirtilmiş hiçbir sütun stilleri sahip bir tablo stili görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1b8ce-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="1b8ce-108">Ekleyerek tablodaki hangi sütunların görünür kısıtlayabilirsiniz **DataGridColumnStyle** nesneleri **GridColumnStylesCollection** üzerinden erişilen nesne  **GridColumnStyles** her özellik **DataGridTableStyle** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1b8ce-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="1b8ce-109">DataGrid denetimine tablo ve sütun programlı olarak eklemek için</span><span class="sxs-lookup"><span data-stu-id="1b8ce-109">To add a table and column to a DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="1b8ce-110">Tablodaki verileri görüntülemek için önce bağlamanız gerekir <xref:System.Windows.Forms.DataGrid> denetlemek için bir veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="1b8ce-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="1b8ce-111">Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="1b8ce-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="1b8ce-112">Sütun stilleri program aracılığıyla belirtirken, her zaman Oluştur **DataGridColumnStyle** nesneleri ve bunları Ekle **GridColumnStylesCollection** eklemeden önce nesne  **DataGridTableStyle** nesneleri **GridTableStylesCollection** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1b8ce-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="1b8ce-113">Boş bir eklediğinizde **DataGridTableStyle** koleksiyonu nesnesine **DataGridColumnStyle** nesneleri otomatik olarak üretilen sizin için.</span><span class="sxs-lookup"><span data-stu-id="1b8ce-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="1b8ce-114">Yeni eklemeyi denediğinizde sonuç olarak, bir özel durum oluşturulacak **DataGridColumnStyle** yinelenen nesneleriyle **MappingName** değerler **GridColumnStylesCollection**nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1b8ce-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>  
  
2.  <span data-ttu-id="1b8ce-115">Yeni Tablo Stili bildirme ve eşleme adını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1b8ce-115">Declare a new table style and set its mapping name.</span></span>  
  
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
  
3.  <span data-ttu-id="1b8ce-116">Yeni bir sütun stili bildirme ve eşleme adını ve diğer özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1b8ce-116">Declare a new column style and set its mapping name and other properties.</span></span>  
  
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
  
4.  <span data-ttu-id="1b8ce-117">Çağrı **Ekle** yöntemi **GridColumnStylesCollection** tablo stiline sütun eklemek için nesnesi</span><span class="sxs-lookup"><span data-stu-id="1b8ce-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  <span data-ttu-id="1b8ce-118">Çağrı **Ekle** yöntemi **GridTableStylesCollection** veri kılavuza tablo stili eklenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="1b8ce-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1b8ce-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b8ce-119">See Also</span></span>  
 [<span data-ttu-id="1b8ce-120">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="1b8ce-120">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="1b8ce-121">Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme</span><span class="sxs-lookup"><span data-stu-id="1b8ce-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
