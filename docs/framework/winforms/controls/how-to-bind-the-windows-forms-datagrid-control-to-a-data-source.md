---
title: "Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama"
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
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c136aca0eda9ea906ad8bf6853a263adf6130609
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> denetimi veri kaynağı bilgilerini görüntülemek için özel olarak tasarlanmıştır. Çağırarak çalışma zamanında denetimi bağlamak <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi. Çeşitli veri kaynakları verileri görüntüleyebilse de, en tipik veri kümeleri ve veri görünümleri kaynaklardır.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>DataGrid denetimi program aracılığıyla Data-bind için  
  
1.  Veri kümesini doldurmak için kod yazma.  
  
     Veri kaynağı bir veri kümesi ya da bir veri kümesi tabloya dayalı bir veri görünümü ise, veri kümesini doldurmak üzere formuna kodu ekleyin.  
  
     Kullandığınız tam kod burada veri kümesi alma bağlıdır. Veri kümesi bir veritabanından doğrudan doldurulmuş, genellikle çağırmanız `Fill` adlı bir veri kümesi doldurur aşağıdaki örnekteki gibi bir veri bağdaştırıcısı yöntemi `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Veri kümesi bir XML Web hizmetinden doldurulmuş, genellikle kodunuzda Hizmeti'nin bir örneğini oluşturun ve bir veri kümesi döndürülecek yöntemlerinden birini çağırın. XML Web hizmeti kümesinden sonra yerel veri kümesine birleştirin. Aşağıdaki örnek adlı bir XML Web hizmeti örneğini nasıl oluşturabileceğinizi gösterir `CategoriesService`, çağrı kendi `GetCategories` yöntemi ve sonuçta elde edilen yerel bir veri kümesine adlı birleştirme `DsCategories1`:  
  
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
  
2.  Çağrı <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi, veri kaynağı ve veri üyesi geçirme. Bir veri üyesi açıkça geçmesine gerekmiyorsa, boş bir dizeyi geçirmek.  
  
    > [!NOTE]
    >  Izgaranın ilk kez bağlanıyorsanız, denetimin ayarlayabilirsiniz <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri. Ancak, bunlar ayarlandıktan sonra bu özellikleri sıfırlayamazsınız. Bu nedenle, her zaman kullanmanız önerilir <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi.  
  
     Aşağıdaki örnek, nasıl program aracılığıyla adlı bir veri kümesi Müşteriler tablosunda bağlayabilirsiniz gösterir `DsCustomers1`:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Müşteriler tablosu veri kümesi yalnızca tabloda ise, kılavuz alternatif olarak bu şekilde bağlayabilirsiniz:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  (İsteğe bağlı) Sütun stilleri ve uygun tablo stilleri kılavuzuna ekleyin. Hiçbir tablo stilleri varsa Tablo görürsünüz, ancak en az biçimlendirme ile tüm sütunları görünür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataGrid Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [DataGrid Denetimi](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Windows Forms Veri Bağlama](../../../../docs/framework/winforms/windows-forms-data-binding.md)
