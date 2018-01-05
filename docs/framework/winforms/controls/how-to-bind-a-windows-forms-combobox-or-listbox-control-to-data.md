---
title: "Nasıl yapılır: Windows Forms ComboBox veya ListBox Denetimini Verilere Bağlama"
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b671910ac77b7456492cab871ace3abb61ac7fd7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Nasıl yapılır: Windows Forms ComboBox veya ListBox Denetimini Verilere Bağlama
Bağlayabilirsiniz <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.ListBox> verileri bir veritabanındaki verilere göz atma gibi görevleri gerçekleştirmek için yeni verileri girmeden veya var olan verileri düzenleme.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>ComboBox veya ListBox denetimini bağlamak için  
  
1.  Ayarlama `DataSource` bir veri kaynağı nesnesi için özellik. Olası veri kaynaklarını içeren bir <xref:System.Windows.Forms.BindingSource> bağlı verileri, veri tablosu, veri görünümü, bir veri kümesi, veri Yöneticisi, bir dizi veya görüntüleme uygulayan herhangi bir sınıf <xref:System.Collections.IList> arabirimi. Daha fazla bilgi için bkz: [veri kaynaklarını Windows Forms tarafından desteklenen](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).  
  
2.  Bir tabloya bağlıyorsanız ayarlamak `DisplayMember` özelliğini veri kaynağındaki bir sütunun adı.  
  
     \-veya -  
  
     İçin bağlıyorsanız bir <xref:System.Collections.IList>, görüntü üye listesinde türünde ortak bir özelliği ayarlayın.  
  
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
    >  Uygulamayan bir veri kaynağına bağlı değilse <xref:System.ComponentModel.IBindingList> arabirimi, aşağıdaki gibi bir <xref:System.Collections.ArrayList>, veri kaynağı güncelleştirildiğinde ilişkili denetimin veri güncelleştirilmez. Varsa, örneğin, bir birleşik giriş kutusu bağlı bir <xref:System.Collections.ArrayList> ve veri eklenir <xref:System.Collections.ArrayList>, bu yeni öğeler açılan kutuda görünmez. Ancak, çağırarak güncelleştirilmesi birleşik giriş kutusu uygulayabilirsiniz <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> ve <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> örneği üzerinde yöntemleri <xref:System.Windows.Forms.BindingContext> sınıfı denetimin bağlı olduğu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [Windows Forms Veri Bağlama](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Veri Bağlama ve Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
