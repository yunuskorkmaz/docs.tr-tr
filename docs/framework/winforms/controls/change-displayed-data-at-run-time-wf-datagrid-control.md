---
title: "Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme"
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
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45772035a7f2229ca0e0320ee9b65eb128c4fc32
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="febf5-102">Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="febf5-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="febf5-103"><xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="febf5-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="febf5-104">Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="febf5-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="febf5-105">Windows Forms oluşturduktan sonra <xref:System.Windows.Forms.DataGrid> tasarım-zamanı özellikleri kullanarak, ayrıca dinamik olarak öğeleri değiştirmek istediğiniz <xref:System.Data.DataSet> kılavuza çalışma zamanında nesne.</span><span class="sxs-lookup"><span data-stu-id="febf5-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="febf5-106">Bu tablonun ya da tek tek değerlerine değişiklikleri içerebilir veya hangi veri kaynağını değiştirme bağlı <xref:System.Windows.Forms.DataGrid> denetim.</span><span class="sxs-lookup"><span data-stu-id="febf5-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="febf5-107">Değerlerini ayrı ayrı yapılan değişiklikler aracılığıyla yapılır <xref:System.Data.DataSet> nesnesi değil, <xref:System.Windows.Forms.DataGrid> denetim.</span><span class="sxs-lookup"><span data-stu-id="febf5-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="febf5-108">Verileri programlı olarak değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="febf5-108">To change data programmatically</span></span>  
  
1.  <span data-ttu-id="febf5-109">İstenen tablosundan belirtin <xref:System.Data.DataSet> nesne ve istenen satır ve tablosundan alan ve hücre yeni değere eşit ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="febf5-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="febf5-110">İlk tablonun belirtmek için <xref:System.Data.DataSet> veya tablonun ilk satırını 0 kullanın.</span><span class="sxs-lookup"><span data-stu-id="febf5-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="febf5-111">Aşağıdaki örnek, bir veri kümesi ilk tablonun ilk satırının ikinci giriş tıklayarak değiştirmek gösterilmiştir `Button1`.</span><span class="sxs-lookup"><span data-stu-id="febf5-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="febf5-112"><xref:System.Data.DataSet> (`ds`) Ve tablolar (`0` ve `1`) daha önce oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="febf5-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
    ```  
  
    ```cpp  
    private:   
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     <span data-ttu-id="febf5-113">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="febf5-113">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="febf5-114">Çalışma zamanında kullanabileceğiniz <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> bağlamak için yöntemi <xref:System.Windows.Forms.DataGrid> denetlemek için farklı bir veri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="febf5-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="febf5-115">Örneğin, birkaç olabilir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] veri denetimleri, her bağlı farklı bir veritabanına.</span><span class="sxs-lookup"><span data-stu-id="febf5-115">For example, you may have several [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="febf5-116">Veri kaynağı programlı olarak değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="febf5-116">To change the DataSource programmatically</span></span>  
  
1.  <span data-ttu-id="febf5-117">Ayarlama <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> veri kaynağı ve bağlamak istediğiniz tablo adını yöntemi.</span><span class="sxs-lookup"><span data-stu-id="febf5-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="febf5-118">Aşağıdaki örnek değişiklik tarihi kaynağı kullanma gösterilmektedir <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yönteme bir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] Pubs veritabanındaki yazarlar tabloya bağlı veri denetimi (adoPubsAuthors).</span><span class="sxs-lookup"><span data-stu-id="febf5-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="febf5-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="febf5-119">See Also</span></span>  
 [<span data-ttu-id="febf5-120">ADO.NET veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="febf5-120">ADO.NET DataSets</span></span>](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 [<span data-ttu-id="febf5-121">Nasıl yapılır: sütunları silme veya gizleme Windows Forms DataGrid denetimi</span><span class="sxs-lookup"><span data-stu-id="febf5-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="febf5-122">Nasıl yapılır: tabloları ekleyebilir ve sütunları Windows Forms DataGrid denetimi</span><span class="sxs-lookup"><span data-stu-id="febf5-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="febf5-123">Nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="febf5-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
