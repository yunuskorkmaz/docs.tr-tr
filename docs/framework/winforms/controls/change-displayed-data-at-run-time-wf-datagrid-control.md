---
title: DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme
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
ms.openlocfilehash: 6b788c10784082a0c74ee09f8cd85d540c670b84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142387"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="34e38-102">Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="34e38-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="34e38-103">Denetim, <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGrid> yerini alır ve işlevsellik ekler; ancak, <xref:System.Windows.Forms.DataGrid> isterseniz, denetim hem geriye dönük uyumluluk hem de gelecekteki kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="34e38-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="34e38-104">Daha fazla bilgi için [Bkz. Windows Formları DataGridView ve DataGrid Denetimleri arasındaki farklar.](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)</span><span class="sxs-lookup"><span data-stu-id="34e38-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="34e38-105">Tasarım zamanı özelliklerini kullanarak <xref:System.Windows.Forms.DataGrid> bir Windows Forms oluşturduktan sonra, çalışma zamanında ızgara <xref:System.Data.DataSet> nesnesinin öğelerini dinamik olarak değiştirmek de isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34e38-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="34e38-106">Bu, tablonun tek tek değerlerinde yapılan değişiklikleri veya denetime <xref:System.Windows.Forms.DataGrid> bağlı hangi veri kaynağının değiştirini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="34e38-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="34e38-107">Tek tek değerlerdeki değişiklikler <xref:System.Data.DataSet> <xref:System.Windows.Forms.DataGrid> denetim üzerinden değil, nesne aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="34e38-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="34e38-108">Verileri programlı olarak değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="34e38-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="34e38-109">Nesneden istenen tabloyu <xref:System.Data.DataSet> ve tablodan istenen satır ve alanı belirtin ve hücreyi yeni değere eşit olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="34e38-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="34e38-110">Tablonun ilk tablosunu <xref:System.Data.DataSet> veya ilk satırını belirtmek için 0'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="34e38-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="34e38-111">Aşağıdaki örnekte, bir veri kümesinin ilk tablosunun ilk satırının ikinci `Button1`girişinin nasıl değiştirilen i' yi tıklatarak nasıl değiştirilen bir .</span><span class="sxs-lookup"><span data-stu-id="34e38-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="34e38-112">( <xref:System.Data.DataSet> `ds`) ve`0` Tablolar `1`( ve ) daha önce oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="34e38-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="34e38-113">(Görsel C#, Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="34e38-113">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="34e38-114">Çalışma zamanında <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> <xref:System.Windows.Forms.DataGrid> denetimi farklı bir veri kaynağına bağlamak için yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34e38-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="34e38-115">Örneğin, her biri farklı bir veritabanına bağlı olan birkaç ADO.NET veri denetiminiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="34e38-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="34e38-116">DataSource'u programlı olarak değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="34e38-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="34e38-117"><xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> Yöntemi bağlamak istediğiniz veri kaynağı nın ve tablonun adına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="34e38-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="34e38-118">Aşağıdaki örnek, <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntem kullanarak tarih kaynağının Pubs veritabanındaki Yazarlar tablosuna bağlı ADO.NET veri denetimi (adoPubsAuthors) olarak nasıl değiştirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="34e38-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34e38-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34e38-119">See also</span></span>

- [<span data-ttu-id="34e38-120">ADO.NET Veri Kümeleri</span><span class="sxs-lookup"><span data-stu-id="34e38-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="34e38-121">Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme</span><span class="sxs-lookup"><span data-stu-id="34e38-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="34e38-122">Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="34e38-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="34e38-123">Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama</span><span class="sxs-lookup"><span data-stu-id="34e38-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
