---
title: 'Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile DataSet İçindeki Hataları Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: 15fbf4a3cebef1485f0c54ace36ab88f3d4289e7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310453"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile DataSet İçindeki Hataları Görüntüleme
Windows Forms kullanabileceğiniz <xref:System.Windows.Forms.ErrorProvider> bir dataset ya da başka bir veri kaynağı içindeki sütun hataları görüntülemek için bileşen. İçin bir <xref:System.Windows.Forms.ErrorProvider> bir form üzerinde veri hataları görüntülemek için bileşen olacak şekilde yok doğrudan bir denetimle ilişkilendirilen. Bir veri kaynağına bağlandıktan sonra aynı veri kaynağına bağlı herhangi bir denetimi yanında bir hata simgesi görüntüleyebilirsiniz.  
  
> [!NOTE]
>  Hata sağlayıcının değiştirirseniz <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> ve <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> özellikleri çalışma zamanında kullanmalıdır <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> çakışmalarını önlemek için yöntemi.  
  
### <a name="to-display-data-errors"></a>Veri hataları görüntülemek için  
  
1. Bileşen bir veri tablosu içinde belirli bir sütuna bağlama.  
  
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
  
2. Ayarlama <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> forma özelliği.  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3. Bir sütun hatasını içeren bir satır için geçerli kayıt konumunu ayarlayın.  
  
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
