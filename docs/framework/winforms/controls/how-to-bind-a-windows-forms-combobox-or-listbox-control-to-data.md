---
title: 'Nasıl yapılır: Bir Windows Forms ComboBox veya ListBox denetimini verilere bağlama'
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
ms.openlocfilehash: c8eb224cbb8ec7ab271edaed8bb25f9cc7fb8ddc
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709932"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Nasıl yapılır: Bir Windows Forms ComboBox veya ListBox denetimini verilere bağlama
Bağlayabilirsiniz <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.ListBox> verileri bir veritabanındaki verilere gözatma gibi görevleri gerçekleştirmek için yeni veri girme veya mevcut bir veri düzenleme.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Bir ComboBox veya ListBox denetimini bağlamak için  
  
1.  Ayarlama `DataSource` özelliği için bir veri kaynağı nesnesi. Olası veri kaynaklarını içeren bir <xref:System.Windows.Forms.BindingSource> ilişkili verileri, bir veri tablosu, bir veri görünümü, bir veri kümesi, veri görüntüleme Yöneticisi, bir dizi veya uygulayan sınıf <xref:System.Collections.IList> arabirimi. Daha fazla bilgi için [Windows Forms tarafından desteklenen veri kaynakları](../data-sources-supported-by-windows-forms.md).  
  
2.  Bir tabloya bağlanıyorsanız, ayarlama `DisplayMember` özelliğini veri kaynağındaki bir sütunun adı.  
  
     \- veya -  
  
     İçin bağlıyorsanız bir <xref:System.Collections.IList>, ekran üye listesindeki türü ortak özellik ayarlayın.  
  
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
    >  Uygulamayan bir veri kaynağına bağlı olup olmadığını <xref:System.ComponentModel.IBindingList> arabirim gibi bir <xref:System.Collections.ArrayList>, veri kaynağı güncelleştirildiğinde ilişkili denetim verileri güncelleştirilmez. Varsa, örneğin, bir birleşik giriş kutusu bağlı bir <xref:System.Collections.ArrayList> ve veri eklendiğinde <xref:System.Collections.ArrayList>, bu yeni öğeleri birleşik giriş kutusunda görünmez. Ancak çağırarak güncelleştirilmesi için birleşik giriş kutusu zorlayabilirsiniz <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> ve <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> örneği üzerinde yöntemleri <xref:System.Windows.Forms.BindingContext> denetimin bağlı olduğu sınıf.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Windows Forms Veri Bağlama](../windows-forms-data-binding.md)
- [Veri Bağlama ve Windows Forms](../data-binding-and-windows-forms.md)
- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](windows-forms-controls-used-to-list-options.md)
