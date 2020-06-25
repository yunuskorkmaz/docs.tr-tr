---
title: ComboBox veya ListBox denetimini verilere bağlama
description: Bir veritabanındaki verilere göz atma, yeni veri girme veya var olan verileri düzenlemek gibi görevleri gerçekleştirmek için Windows Forms ComboBox ve ListBox 'ı verilere bağlamayı öğrenin.
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
ms.openlocfilehash: 0c07dc90ddc91061c5f34b5a237082cb444e89d9
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324077"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Nasıl yapılır: Windows Forms ComboBox veya ListBox Denetimini Verilere Bağlama
<xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ListBox> Bir veritabanındaki verilere göz atma, yeni veriler girme veya varolan verileri düzenlemek gibi görevleri gerçekleştirmek için ve verilerini bağlayabilirsiniz.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>ComboBox veya ListBox denetimini bağlamak için  
  
1. `DataSource`Özelliği bir veri kaynağı nesnesi olarak ayarlayın. Olası veri kaynakları <xref:System.Windows.Forms.BindingSource> , veri, veri tablosu, veri görünümü, veri kümesi, veri görünümü Yöneticisi, bir dizi ya da arabirimi uygulayan herhangi bir sınıf için bir sınırdır <xref:System.Collections.IList> . Daha fazla bilgi için bkz. [Windows Forms tarafından desteklenen veri kaynakları](../data-sources-supported-by-windows-forms.md).  
  
2. Bir tabloya bağlıyorsanız, `DisplayMember` özelliği veri kaynağındaki bir sütunun adı olarak ayarlayın.  
  
     \-veya  
  
     ' A bağlıyorsanız <xref:System.Collections.IList> , görüntüleme üyesini listedeki türün ortak özelliği olarak ayarlayın.  
  
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
    > Arabirimi uygulamayan bir veri kaynağına (örneğin,) bağlandıysanız <xref:System.ComponentModel.IBindingList> <xref:System.Collections.ArrayList> , veri kaynağı güncelleştirildiği zaman, bağlanan denetimin verileri güncellenmez. Örneğin, öğesine bir Birleşik giriş kutusu varsa <xref:System.Collections.ArrayList> ve veriler öğesine eklenirse <xref:System.Collections.ArrayList> , bu yeni öğeler Birleşik giriş kutusunda görünmez. Ancak, <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> denetimin bağlı olduğu sınıfın örneğindeki ve yöntemlerini çağırarak Birleşik giriş kutusunu güncelleştirilmesini zorlayabilirsiniz <xref:System.Windows.Forms.BindingContext> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Windows Forms Veri Bağlama](../windows-forms-data-binding.md)
- [Veri Bağlama ve Windows Forms](../data-binding-and-windows-forms.md)
- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](windows-forms-controls-used-to-list-options.md)
