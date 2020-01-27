---
title: ErrorProvider bileşeni kullanarak bir veri kümesi Içindeki hataları görüntüleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: 8c2155bf288db89b5d53567738fd399b915d50b6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745459"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile DataSet İçindeki Hataları Görüntüleme
Bir veri kümesi veya başka bir veri kaynağı içindeki sütun hatalarını görüntülemek için Windows Forms <xref:System.Windows.Forms.ErrorProvider> bileşenini kullanabilirsiniz. Bir <xref:System.Windows.Forms.ErrorProvider> bileşenin veri hatalarını bir form üzerinde görüntülemesi için, bir denetimle doğrudan ilişkilendirilmesi gerekmez. Bir veri kaynağına bağlandıktan sonra, aynı veri kaynağına bağlanan herhangi bir denetimin yanında bir hata simgesi görüntülenebilir.  
  
> [!NOTE]
> Çalışma zamanında hata sağlayıcısının <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> ve <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> özelliklerini değiştirirseniz, çakışmaları önlemek için <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> yöntemini kullanmanız gerekir.  
  
### <a name="to-display-data-errors"></a>Veri hatalarını görüntüleme  
  
1. Bileşeni veri tablosu içindeki belirli bir sütuna bağlayın.  
  
    ```vb  
    ' Assumes existence of DataSet1, DataTable1  
    TextBox1.DataBindings.Add("Text", DataSet1, "Customers.Name")  
    ErrorProvider1.DataSource = DataSet1  
    ErrorProvider1.DataMember = "Customers"  
    ```  
  
    ```csharp  
    // Assumes existence of DataSet1, DataTable1  
    textBox1.DataBindings.Add("Text", DataSet1, "Customers.Name");  
    errorProvider1.DataSource = DataSet1;  
    errorProvider1.DataMember = "Customers";  
    ```  
  
2. <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> özelliğini form olarak ayarlayın.  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3. Geçerli kaydın konumunu sütun hatası içeren bir satıra ayarlayın.  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ErrorProvider Bileşenine Genel Bakış](errorprovider-component-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile Form Doğrulama için Hata Simgeleri Görüntüleme](display-error-icons-for-form-validation-with-wf-errorprovider.md)
