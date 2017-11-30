---
title: "Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile DataSet İçindeki Hataları Görüntüleme"
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
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 28c90df258db8480f68eea05f922b36f30d81a3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile DataSet İçindeki Hataları Görüntüleme
Windows Forms kullanabilirsiniz <xref:System.Windows.Forms.ErrorProvider> bir dataset ya da başka bir veri kaynağını içindeki sütun hataları görüntülemek için bileşen. İçin bir <xref:System.Windows.Forms.ErrorProvider> veri hatalarını bir formda görüntülemek için bileşen olmasını yok doğrudan denetimi ile ilişkilendirilmiş. Bir veri kaynağına bağlandıktan sonra aynı veri kaynağına bağlı olduğu herhangi bir denetimi yanındaki hata simgesi görüntüleyebilirsiniz.  
  
> [!NOTE]
>  Hata sağlayıcının değiştirirseniz <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> ve <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> çalışma zamanında özelliklerini, kullanmanız gereken <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> çakışmaları önlemek için yöntem.  
  
### <a name="to-display-data-errors"></a>Veri hataları görüntülemek için  
  
1.  Veri tablosu içindeki belirli bir sütuna bileşen bağlayın.  
  
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
  
2.  Ayarlanmış <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> forma özelliği.  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3.  Geçerli kayıt konumunu sütun hata içeren bir satır ayarlayın.  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ErrorProvider bileşenine genel bakış](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [Nasıl yapılır: Forms ErrorProvider bileşeni Windows ile Form doğrulama için hata simgeleri görüntüleme](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
