---
title: 'Nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama'
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
ms.openlocfilehash: 5f8c0c2865d219eecb88ddd176d99f80521c9ab3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664219"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> denetim bir veri kaynağından bilgileri görüntülemek için özel olarak tasarlanmıştır. Çağırarak denetimini çalışma zamanında bağlama <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi. Çeşitli veri kaynaklarından verileri görüntüleyebilse de, en sık karşılaşılan veri kümeleri ve veri görünümleri kaynaklarıdır.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>DataGrid denetimi program aracılığıyla veri-bağlamak için  
  
1.  DataSet'i doldurmak için kod yazın.  
  
     Veri kaynağı bir veri kümesi veya bir veri kümesi tabloyu temel alan bir veri görünümü, forma DataSet'i doldurmak için kod ekleyin.  
  
     Kullandığınız tam kod burada veri veri kümesi alma bağlıdır. Veri kümesi doğrudan bir veritabanından doldurulmuş, genellikle arama `Fill` adlı bir veri kümesi doldurur aşağıdaki örnekte olduğu gibi bir veri bağdaştırıcısı yöntemi `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Bir XML Web hizmetinden doldurulmuş veri kümesi, genellikle kodunuzda Hizmeti'nin bir örneğini oluşturur ve ardından bir veri kümesi döndürülecek yöntemlerinden birini çağırın. XML Web hizmetinden dataset sonra yerel kümenize birleştirin. Aşağıdaki örnek, bir XML Web hizmeti olarak adlandırılan bir örneğini nasıl oluşturacağınızı gösterir. `CategoriesService`, arama, `GetCategories` yöntemi ve sonuç veri kümesini yerel bir veri kümesine adlı birleştirme `DsCategories1`:  
  
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
  
2.  Çağrı <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi, veri kaynağı ve veri üyesi geçirme. Veri üyesi açıkça geçirebilirsiniz ihtiyacınız yoksa boş bir dize geçirin.  
  
    > [!NOTE]
    >  Kılavuzun ilk kez bağlanıyorsanız, denetimin ayarlayabilirsiniz <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri. Ancak, ayarlandıktan sonra bu özellikleri sıfırlayamazsınız. Bu nedenle, her zaman kullanmanız önerilir <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi.  
  
     Aşağıdaki örnek nasıl program aracılığıyla adlı bir veri kümesi Müşteriler tablosunda adlarınıza bağlayabileceğiniz gösterir `DsCustomers1`:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Müşteriler tablosu veri kümesi yalnızca tablodaki ise, kılavuz alternatif olarak bu şekilde bağlayabilirsiniz:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  (İsteğe bağlı) Sütun stillerini ve uygun tablo stilleri kılavuza ekleyin. Hiçbir tablo stilleri varsa, bir tablo görürsünüz ancak en az biçimlendirme ile tüm sütunlar görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [DataGrid Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid Denetimi](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
- [Windows Forms Veri Bağlama](../../../../docs/framework/winforms/windows-forms-data-binding.md)
