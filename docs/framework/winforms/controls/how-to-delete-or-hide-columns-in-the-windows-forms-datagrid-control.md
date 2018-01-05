---
title: "Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65257ec5f9ca51a795abca119e5449d6219042bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="9f78b-102">Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme</span><span class="sxs-lookup"><span data-stu-id="9f78b-102">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="9f78b-103"><xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="9f78b-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="9f78b-104">Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="9f78b-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="9f78b-105">Program aracılığıyla silme veya Windows Forms'ta sütunları gizleme <xref:System.Windows.Forms.DataGrid> özelliklerini ve yöntemlerini kullanarak denetim <xref:System.Windows.Forms.GridColumnStylesCollection> ve <xref:System.Windows.Forms.DataGridColumnStyle> nesneleri (üyeleri <xref:System.Windows.Forms.DataGridTableStyle> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="9f78b-105">You can programmatically delete or hide columns in the Windows Forms <xref:System.Windows.Forms.DataGrid> control by using the properties and methods of the <xref:System.Windows.Forms.GridColumnStylesCollection> and <xref:System.Windows.Forms.DataGridColumnStyle> objects (which are members of the <xref:System.Windows.Forms.DataGridTableStyle> class).</span></span>  
  
 <span data-ttu-id="9f78b-106">Veri kaynağı kılavuz bağlı ve hala programlı olarak erişilebilir silinmiş ya da gizli sütunlar hala var.</span><span class="sxs-lookup"><span data-stu-id="9f78b-106">The deleted or hidden columns still exist in the data source the grid is bound to, and can still be accessed programmatically.</span></span> <span data-ttu-id="9f78b-107">Yalnızca artık datagrid denetiminde görünür değildir.</span><span class="sxs-lookup"><span data-stu-id="9f78b-107">They are just no longer visible in the datagrid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f78b-108">Uygulamanızı belirli veri sütunlarının erişmez ve bunları datagrid denetiminde görüntülenen istemiyorsanız, ardından bu veri kaynağındaki ilk başta dahil etmek gerekli değildir büyük olasılıkla.</span><span class="sxs-lookup"><span data-stu-id="9f78b-108">If your application does not access certain columns of data, and you do not want them displayed in the datagrid, then it is probably not necessary to include them in the data source in the first place.</span></span>  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a><span data-ttu-id="9f78b-109">DataGrid programlı olarak bir sütun silmek için</span><span class="sxs-lookup"><span data-stu-id="9f78b-109">To delete a column from the DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="9f78b-110">Formunuz bildirimleri alanında yeni bir örneğini bildirme <xref:System.Windows.Forms.DataGridTableStyle> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9f78b-110">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2.  <span data-ttu-id="9f78b-111">Ayarlama <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> stil uygulamak istediğiniz veri kaynağınız tablosuna özelliği.</span><span class="sxs-lookup"><span data-stu-id="9f78b-111">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> property to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="9f78b-112">Aşağıdaki örnek kullanır <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> zaten ayarlanmış varsayar özelliği.</span><span class="sxs-lookup"><span data-stu-id="9f78b-112">The following example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3.  <span data-ttu-id="9f78b-113">Yeni Ekle <xref:System.Windows.Forms.DataGridTableStyle> DataGrid'in tablo stilleri koleksiyonunda nesnesine.</span><span class="sxs-lookup"><span data-stu-id="9f78b-113">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4.  <span data-ttu-id="9f78b-114">Çağrı <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> yöntemi <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> silmek için sütunun sütun dizini belirtme koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9f78b-114">Call the <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, specifying the column index of the column to delete.</span></span>  
  
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
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a><span data-ttu-id="9f78b-115">DataGrid sütununda program aracılığıyla gizleme</span><span class="sxs-lookup"><span data-stu-id="9f78b-115">To hide a column in the DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="9f78b-116">Formunuz bildirimleri alanında yeni bir örneğini bildirme <xref:System.Windows.Forms.DataGridTableStyle> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9f78b-116">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2.  <span data-ttu-id="9f78b-117">Ayarlama <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliği <xref:System.Windows.Forms.DataGridTableStyle> stil uygulamak istediğiniz veri kaynağınız tablosuna.</span><span class="sxs-lookup"><span data-stu-id="9f78b-117">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle> to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="9f78b-118">Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> zaten ayarlanmış varsayar özelliği.</span><span class="sxs-lookup"><span data-stu-id="9f78b-118">The following code example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3.  <span data-ttu-id="9f78b-119">Yeni Ekle <xref:System.Windows.Forms.DataGridTableStyle> DataGrid'in tablo stilleri koleksiyonunda nesnesine.</span><span class="sxs-lookup"><span data-stu-id="9f78b-119">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4.  <span data-ttu-id="9f78b-120">Ayarlayarak sütun gizleme kendi `Width` özelliği 0 olarak gizlemek için sütunun sütun dizini belirtme.</span><span class="sxs-lookup"><span data-stu-id="9f78b-120">Hide the column by setting its `Width` property to 0, specifying the column index of the column to hide.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f78b-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f78b-121">See Also</span></span>  
 [<span data-ttu-id="9f78b-122">Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="9f78b-122">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)  
 [<span data-ttu-id="9f78b-123">Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="9f78b-123">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
