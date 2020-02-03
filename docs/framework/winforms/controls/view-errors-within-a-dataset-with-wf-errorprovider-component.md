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
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="0f3f6-102">Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile DataSet İçindeki Hataları Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="0f3f6-102">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="0f3f6-103">Bir veri kümesi veya başka bir veri kaynağı içindeki sütun hatalarını görüntülemek için Windows Forms <xref:System.Windows.Forms.ErrorProvider> bileşenini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f3f6-103">You can use the Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to view column errors within a dataset or other data source.</span></span> <span data-ttu-id="0f3f6-104">Bir <xref:System.Windows.Forms.ErrorProvider> bileşenin veri hatalarını bir form üzerinde görüntülemesi için, bir denetimle doğrudan ilişkilendirilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0f3f6-104">For an <xref:System.Windows.Forms.ErrorProvider> component to display data errors on a form, it does not have to be directly associated with a control.</span></span> <span data-ttu-id="0f3f6-105">Bir veri kaynağına bağlandıktan sonra, aynı veri kaynağına bağlanan herhangi bir denetimin yanında bir hata simgesi görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="0f3f6-105">Once it is bound to a data source, it can display an error icon next to any control that is bound to the same data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f3f6-106">Çalışma zamanında hata sağlayıcısının <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> ve <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> özelliklerini değiştirirseniz, çakışmaları önlemek için <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> yöntemini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f3f6-106">If you change the error provider's <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> and <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> properties at run time, you should use the <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> method to avoid conflicts.</span></span>  
  
### <a name="to-display-data-errors"></a><span data-ttu-id="0f3f6-107">Veri hatalarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="0f3f6-107">To display data errors</span></span>  
  
1. <span data-ttu-id="0f3f6-108">Bileşeni veri tablosu içindeki belirli bir sütuna bağlayın.</span><span class="sxs-lookup"><span data-stu-id="0f3f6-108">Bind the component to a specific column within a data table.</span></span>  
  
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
  
2. <span data-ttu-id="0f3f6-109"><xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> özelliğini form olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0f3f6-109">Set the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property to the form.</span></span>  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3. <span data-ttu-id="0f3f6-110">Geçerli kaydın konumunu sütun hatası içeren bir satıra ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0f3f6-110">Set the position of the current record to a row that contains a column error.</span></span>  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0f3f6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f3f6-111">See also</span></span>

- [<span data-ttu-id="0f3f6-112">ErrorProvider Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0f3f6-112">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="0f3f6-113">Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile Form Doğrulama için Hata Simgeleri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="0f3f6-113">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>](display-error-icons-for-form-validation-with-wf-errorprovider.md)
