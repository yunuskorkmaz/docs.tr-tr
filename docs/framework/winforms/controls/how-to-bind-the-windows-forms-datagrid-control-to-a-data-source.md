---
title: DataGrid denetimini bir veri kaynağına bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: 2634a6bd8ace36bcf7a49120162474a8c04b2b83
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746693"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> denetimi, bir veri kaynağından bilgileri görüntüleyecek şekilde özel olarak tasarlanmıştır. <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini çağırarak denetimi çalışma zamanında bağlarsınız. Çeşitli veri kaynaklarından veri görüntüleyebilirsiniz, ancak en genel kaynaklar veri kümeleri ve veri görünümleridir.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>DataGrid denetimini programlama yoluyla veri bağlama  
  
1. Veri kümesini dolduracak kodu yazın.  
  
     Veri kaynağı bir veri kümesi veya veri kümesi tablosuna dayalı bir veri görünüminiyorsa, veri kümesini dolduracak şekilde forma kod ekleyin.  
  
     Kullandığınız tam kod, veri kümesinin veri alılabileceği yere bağlıdır. Veri kümesi doğrudan bir veritabanından doldurulursa, genellikle `DsCategories1`adlı bir veri kümesini dolduran aşağıdaki örnekte olduğu gibi bir veri bağdaştırıcısının `Fill` yöntemini çağırabilirsiniz:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Veri kümesi bir XML Web hizmetinden doldurulduysa, genellikle kodunuzda hizmetin bir örneğini oluşturun ve ardından bir veri kümesi döndürmek için yöntemlerinden birini çağırın. Daha sonra veri kümesini XML Web hizmetinden yerel veri kümeniz ile birleştirebilirsiniz. Aşağıdaki örnek, `CategoriesService`adlı bir XML Web hizmetinin örneğini nasıl oluşturabileceğiniz, `GetCategories` metodunu çağırabilmeniz ve elde edilen veri kümesini `DsCategories1`adlı yerel bir veri kümesinde birleştirebilmeniz gösterilmektedir:  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =   
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2. <xref:System.Windows.Forms.DataGrid> denetiminin <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodunu çağırın, veri kaynağını ve bir veri üyesini geçirerek. Bir veri üyesini açıkça geçirmeniz gerekmiyorsa boş bir dize geçirin.  
  
    > [!NOTE]
    > Kılavuzu ilk kez bağlıyorsanız, denetimin <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliklerini ayarlayabilirsiniz. Ancak, ayarlandıklarında bu özellikleri sıfırlayamazsınız. Bu nedenle, <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini her zaman kullanmanız önerilir.  
  
     Aşağıdaki örnek, `DsCustomers1`adlı bir veri kümesindeki Customers tablosuna programlı bir şekilde nasıl bağlayacağınız gösterilmektedir:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Veri kümesindeki tek tablo müşteriler tablosu ise bu şekilde kılavuza bağlayabilirsiniz:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. Seçim Kılavuza uygun tablo stillerini ve sütun stillerini ekleyin. Tablo stili yoksa, tabloyu görürsünüz, ancak en az biçimlendirme ile ve tüm sütunları görünür olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimine Genel Bakış](datagrid-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [Windows Forms Veri Bağlama](../windows-forms-data-binding.md)
