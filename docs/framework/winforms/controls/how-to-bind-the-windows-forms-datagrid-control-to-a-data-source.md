---
title: DataGrid Denetimini Veri Kaynağına Bağlama
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
ms.openlocfilehash: 42514c6a0ab9cf912a32b13675a069976632ece5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182250"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama
> [!NOTE]
> Denetim, <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGrid> yerini alır ve işlevsellik ekler; ancak, <xref:System.Windows.Forms.DataGrid> isterseniz, denetim hem geriye dönük uyumluluk hem de gelecekteki kullanım için korunur. Daha fazla bilgi için [Bkz. Windows Formları DataGridView ve DataGrid Denetimleri arasındaki farklar.](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> denetimi, bir veri kaynağından gelen bilgileri görüntülemek için özel olarak tasarlanmıştır. <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> Yöntemi arayarak denetimi çalışma zamanında bağlarsınız. Çeşitli veri kaynaklarından veri görüntüleyebiliyor olsanız da, en tipik kaynaklar veri kümeleri ve veri görünümleridir.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>DataGrid denetimini programlı olarak bağlamak için  
  
1. Veri kümesini doldurmak için kod yazın.  
  
     Veri kaynağı bir veri kümesi veya veri kümesi tablosuna dayalı bir veri görünümüyse, veri kümesini doldurmak için forma kod ekleyin.  
  
     Tam kullandığınız kod, veri kümesinin verileri nereden aldığına bağlıdır. Veri kümesi doğrudan bir veritabanından dolduruluyorsa, aşağıdaki `Fill` örnekte olduğu gibi genellikle bir veri bağdaştırıcısı `DsCategories1`yöntemini çağırırsınız:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Veri kümesi bir XML Web hizmetinden dolduruluyorsa, genellikle kodunuzdaki hizmetin bir örneğini oluşturur ve ardından veri kümesini döndürmek için yöntemlerinden birini ararsınız. Ardından XML Web hizmetindeki veri kümesini yerel veri kümenizle birleştirirsiniz. Aşağıdaki örnek, xml Web hizmetinin `CategoriesService`bir örneğini nasıl `GetCategories` oluşturabileceğinizi gösterir, yöntemini çağırın ve `DsCategories1`elde edilen veri kümesini aşağıdaki gibi yerel bir veri kümesiyle birleştirebilirsiniz:  
  
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
  
2. Denetimin <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini çağırın, veri kaynağını ve veri üyesini geçirin. Bir veri üyesini açıkça geçirmeniz gerekmiyorsa, boş bir dize geçirin.  
  
    > [!NOTE]
    > Izgarayı ilk kez bağlıyorsanız, denetimin <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri ayarlayabilirsiniz. Ancak, bu özellikleri ayarlandıktan sonra sıfırlayamazsınız. Bu nedenle, her zaman <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi kullanmanız önerilir.  
  
     Aşağıdaki örnek, aşağıdaki adlı `DsCustomers1`bir veri kümesinde Müşteriler tablosuna nasıl programlı olarak bağlanabileceğinizi gösterir:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Müşteriler tablosu veri kümesindeki tek tabloysa, ızgarayı alternatif olarak şu şekilde bağlayabilirsiniz:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. (İsteğe bağlı) Kılavuza uygun tablo stillerini ve sütun stillerini ekleyin. Tablo stilleri yoksa, tabloyu görürsünüz, ancak en az biçimlendirme ve tüm sütunlar görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimine Genel Bakış](datagrid-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [Windows Forms Veri Bağlama](../windows-forms-data-binding.md)
