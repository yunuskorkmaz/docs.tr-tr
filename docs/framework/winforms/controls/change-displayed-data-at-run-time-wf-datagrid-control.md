---
title: 'Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme'
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
ms.openlocfilehash: c7bf70a67729744f4cf96318f6b270a5ea81b812
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917721"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="b3e9b-102">Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="b3e9b-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="b3e9b-103">Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="b3e9b-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="b3e9b-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b3e9b-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="b3e9b-105">Tasarım zamanı özelliklerini kullanarak bir Windows Forms <xref:System.Windows.Forms.DataGrid> oluşturduktan sonra, çalışma zamanında kılavuzun <xref:System.Data.DataSet> nesne öğelerini dinamik olarak değiştirmek de isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3e9b-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="b3e9b-106">Bu, tablonun tek tek değerlerine yapılan değişiklikleri veya <xref:System.Windows.Forms.DataGrid> denetime hangi veri kaynağının bağlandığını değiştirmek içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b3e9b-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="b3e9b-107">Tek tek değerlerde yapılan değişiklikler, <xref:System.Data.DataSet> <xref:System.Windows.Forms.DataGrid> denetim değil, nesnesi aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="b3e9b-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="b3e9b-108">Verileri program aracılığıyla değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="b3e9b-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="b3e9b-109"><xref:System.Data.DataSet> Nesneden istenen tabloyu ve tablodaki istenen satırı ve alanı belirtin ve hücreyi yeni değere eşit olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b3e9b-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b3e9b-110">Tablonun ilk tablosunu <xref:System.Data.DataSet> veya ilk satırını belirtmek için 0 kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3e9b-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="b3e9b-111">Aşağıdaki örnek, öğesine tıklayarak `Button1`bir veri kümesinin ilk tablosunun ilk satırının ikinci girişinin nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3e9b-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="b3e9b-112">() Ve`0` tabloları (ve `1`) daha önce oluşturulmuştur.`ds` <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="b3e9b-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="b3e9b-113">(Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="b3e9b-113">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="b3e9b-114">Çalışma zamanında, <xref:System.Windows.Forms.DataGrid> denetimi farklı bir veri <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> kaynağına bağlamak için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3e9b-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="b3e9b-115">Örneğin, her biri farklı bir veritabanına bağlı olan birkaç ADO.NET veri denetimine sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3e9b-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="b3e9b-116">Veri kaynağını program aracılığıyla değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="b3e9b-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="b3e9b-117">Yöntemini, <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> bağlamak istediğiniz veri kaynağı ve tablo adına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b3e9b-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="b3e9b-118">Aşağıdaki örnek, pubs veritabanındaki yazarlar tablosuna bağlı olan ADO.NET veri denetimine <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (adopubsauthors) yöntemi kullanılarak tarih kaynağının nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3e9b-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3e9b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3e9b-119">See also</span></span>

- [<span data-ttu-id="b3e9b-120">ADO.NET Veri Kümeleri</span><span class="sxs-lookup"><span data-stu-id="b3e9b-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="b3e9b-121">Nasıl yapılır: Windows Forms DataGrid denetimindeki sütunları silme veya gizleme</span><span class="sxs-lookup"><span data-stu-id="b3e9b-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="b3e9b-122">Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme</span><span class="sxs-lookup"><span data-stu-id="b3e9b-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="b3e9b-123">Nasıl yapılır: Windows Forms DataGrid denetimini bir veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="b3e9b-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
