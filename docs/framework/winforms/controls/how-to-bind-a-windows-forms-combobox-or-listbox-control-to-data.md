---
title: 'Nasıl yapılır: Windows Forms ComboBox veya ListBox Denetimini Verilere Bağlama'
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
ms.openlocfilehash: f361526c44f8fbb9ab282fe15ae109b67e8f01dd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922749"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Nasıl yapılır: Windows Forms ComboBox veya ListBox Denetimini Verilere Bağlama
Bir veritabanındaki verilere göz <xref:System.Windows.Forms.ComboBox> atma <xref:System.Windows.Forms.ListBox> , yeni veriler girme veya varolan verileri düzenlemek gibi görevleri gerçekleştirmek için ve verilerini bağlayabilirsiniz.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>ComboBox veya ListBox denetimini bağlamak için  
  
1. `DataSource` Özelliği bir veri kaynağı nesnesi olarak ayarlayın. Olası veri kaynakları, veri <xref:System.Windows.Forms.BindingSource> , veri tablosu, veri görünümü, veri kümesi, veri görünümü Yöneticisi, bir dizi ya da <xref:System.Collections.IList> arabirimi uygulayan herhangi bir sınıf için bir sınırdır. Daha fazla bilgi için bkz. [Windows Forms tarafından desteklenen veri kaynakları](../data-sources-supported-by-windows-forms.md).  
  
2. Bir tabloya bağlıyorsanız, `DisplayMember` özelliği veri kaynağındaki bir sütunun adı olarak ayarlayın.  
  
     \- veya -  
  
     <xref:System.Collections.IList>' A bağlıyorsanız, görüntüleme üyesini listedeki türün ortak özelliği olarak ayarlayın.  
  
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
    > <xref:System.ComponentModel.IBindingList> Arabirimi uygulamayan bir <xref:System.Collections.ArrayList>veri kaynağına (örneğin,) bağlandıysanız, veri kaynağı güncelleştirildiği zaman, bağlanan denetimin verileri güncellenmez. Örneğin, öğesine bir <xref:System.Collections.ArrayList> Birleşik giriş kutusu varsa ve veriler <xref:System.Collections.ArrayList>öğesine eklenirse, bu yeni öğeler Birleşik giriş kutusunda görünmez. Ancak, denetimin bağlı olduğu <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> <xref:System.Windows.Forms.BindingContext> sınıfın örneğindeki ve <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> yöntemlerini çağırarak Birleşik giriş kutusunu güncelleştirilmesini zorlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Windows Forms Veri Bağlama](../windows-forms-data-binding.md)
- [Veri Bağlama ve Windows Forms](../data-binding-and-windows-forms.md)
- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](windows-forms-controls-used-to-list-options.md)
