---
title: DataGrid denetiminde çalışma zamanında görünen verileri değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
ms.openlocfilehash: f91e2ea01ef4a52dd649efed70319017efb8368a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740593"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="28457-102">Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="28457-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="28457-103"><xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="28457-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="28457-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="28457-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="28457-105">Tasarım zamanı özelliklerini kullanarak bir Windows Forms <xref:System.Windows.Forms.DataGrid> oluşturduktan sonra, çalışma zamanında kılavuzun <xref:System.Data.DataSet> nesnesinin öğelerini dinamik olarak değiştirmek de isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28457-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="28457-106">Bu, tablodaki tek tek değerler veya <xref:System.Windows.Forms.DataGrid> denetimine hangi veri kaynağının bağlandığını değiştirme gibi değişiklikler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="28457-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="28457-107">Tek tek değerlerde yapılan değişiklikler <xref:System.Windows.Forms.DataGrid> denetiminden değil <xref:System.Data.DataSet> nesnesi aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="28457-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="28457-108">Verileri program aracılığıyla değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="28457-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="28457-109"><xref:System.Data.DataSet> nesnesinden istenen tabloyu ve tablodaki istenen satırı ve alanı belirtin ve hücreyi yeni değere eşit olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="28457-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="28457-110"><xref:System.Data.DataSet> ilk tablosunu veya tablonun ilk satırını belirtmek için 0 kullanın.</span><span class="sxs-lookup"><span data-stu-id="28457-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="28457-111">Aşağıdaki örnek, `Button1`' ye tıklayarak bir veri kümesinin ilk satırının ilk satırının ikinci girişinin nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="28457-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="28457-112"><xref:System.Data.DataSet> (`ds`) ve tablolar (`0` ve `1`) önceden oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="28457-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="28457-113">(Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="28457-113">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="28457-114">Çalışma zamanında, <xref:System.Windows.Forms.DataGrid> denetimini farklı bir veri kaynağına bağlamak için <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28457-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="28457-115">Örneğin, her biri farklı bir veritabanına bağlı olan birkaç ADO.NET veri denetimine sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28457-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="28457-116">Veri kaynağını program aracılığıyla değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="28457-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="28457-117"><xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini, bağlamak istediğiniz veri kaynağı ve tablonun adı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="28457-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="28457-118">Aşağıdaki örnek, <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini kullanarak, pubs veritabanındaki yazarlar tablosuna bağlanan bir ADO.NET veri denetimine (adoPubsAuthors) göre tarih kaynağının nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="28457-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="28457-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28457-119">See also</span></span>

- [<span data-ttu-id="28457-120">ADO.NET Veri Kümeleri</span><span class="sxs-lookup"><span data-stu-id="28457-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="28457-121">Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme</span><span class="sxs-lookup"><span data-stu-id="28457-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="28457-122">Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="28457-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="28457-123">Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama</span><span class="sxs-lookup"><span data-stu-id="28457-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
