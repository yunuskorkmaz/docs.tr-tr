---
title: ComboBox veya ListBox denetimini verilere bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], binding to controls
- list boxes [Windows Forms], data binding
- ComboBox control [Windows Forms], data binding
- data binding [Windows Forms], combo boxes
- ListBox control [Windows Forms], data binding
- combo boxes [Windows Forms], data binding
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
ms.openlocfilehash: 99d9b53b32d6faae888b134d4ed486980c05a75b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742040"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Nasıl yapılır: Windows Forms ComboBox veya ListBox Denetimini Verilere Bağlama
Bir veritabanındaki verilere göz atma, yeni veriler girme veya var olan verileri düzenlemek gibi görevleri gerçekleştirmek için <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.ListBox> verileri bağlayabilirsiniz.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>ComboBox veya ListBox denetimini bağlamak için  
  
1. `DataSource` özelliğini bir veri kaynağı nesnesi olarak ayarlayın. Olası veri kaynakları, veri, veri tablosu, veri görünümü, veri kümesi, veri görünümü Yöneticisi, bir dizi veya <xref:System.Collections.IList> arabirimini uygulayan herhangi bir sınıf ile ilişkili <xref:System.Windows.Forms.BindingSource> içerir. Daha fazla bilgi için bkz. [Windows Forms tarafından desteklenen veri kaynakları](../data-sources-supported-by-windows-forms.md).  
  
2. Bir tabloya bağlıyorsanız, `DisplayMember` özelliğini veri kaynağındaki bir sütunun adı olarak ayarlayın.  
  
     \- veya-  
  
     Bir <xref:System.Collections.IList>bağlıyorsanız, görüntüleme üyesini listedeki türün ortak özelliği olarak ayarlayın.  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
    ```  
  
    > [!NOTE]
    > <xref:System.Collections.ArrayList>gibi <xref:System.ComponentModel.IBindingList> arabirimini uygulamayan bir veri kaynağına bağlandıysanız, veri kaynağı güncelleştirildiği zaman, bağlanan denetimin verileri güncellenmez. Örneğin, bir <xref:System.Collections.ArrayList> bağlantılı bir Birleşik giriş kutusu varsa ve veriler <xref:System.Collections.ArrayList>eklenirse, bu yeni öğeler Birleşik giriş kutusunda görünmez. Ancak, denetimin bağlı olduğu <xref:System.Windows.Forms.BindingContext> sınıfının örneği üzerinde <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> ve <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> yöntemlerini çağırarak açılan kutuyu güncelleştirilmesini zorlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Windows Forms Veri Bağlama](../windows-forms-data-binding.md)
- [Veri Bağlama ve Windows Forms](../data-binding-and-windows-forms.md)
- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](windows-forms-controls-used-to-list-options.md)
