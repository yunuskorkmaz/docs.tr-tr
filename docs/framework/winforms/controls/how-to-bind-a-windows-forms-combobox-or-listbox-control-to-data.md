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
ms.openlocfilehash: 270ed1c9fab4013df72b715ce8b074d287616713
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530139"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="c5372-102">Nasıl yapılır: Windows Forms ComboBox veya ListBox Denetimini Verilere Bağlama</span><span class="sxs-lookup"><span data-stu-id="c5372-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="c5372-103">Bağlayabilirsiniz <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.ListBox> verileri bir veritabanındaki verilere göz atma gibi görevleri gerçekleştirmek için yeni verileri girmeden veya var olan verileri düzenleme.</span><span class="sxs-lookup"><span data-stu-id="c5372-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="c5372-104">ComboBox veya ListBox denetimini bağlamak için</span><span class="sxs-lookup"><span data-stu-id="c5372-104">To bind a ComboBox or ListBox control</span></span>  
  
1.  <span data-ttu-id="c5372-105">Ayarlama `DataSource` bir veri kaynağı nesnesi için özellik.</span><span class="sxs-lookup"><span data-stu-id="c5372-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="c5372-106">Olası veri kaynaklarını içeren bir <xref:System.Windows.Forms.BindingSource> bağlı verileri, veri tablosu, veri görünümü, bir veri kümesi, veri Yöneticisi, bir dizi veya görüntüleme uygulayan herhangi bir sınıf <xref:System.Collections.IList> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c5372-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="c5372-107">Daha fazla bilgi için bkz: [veri kaynaklarını Windows Forms tarafından desteklenen](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c5372-107">For more information, see [Data Sources Supported by Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="c5372-108">Bir tabloya bağlıyorsanız ayarlamak `DisplayMember` özelliğini veri kaynağındaki bir sütunun adı.</span><span class="sxs-lookup"><span data-stu-id="c5372-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="c5372-109">\- veya -</span><span class="sxs-lookup"><span data-stu-id="c5372-109">\- or -</span></span>  
  
     <span data-ttu-id="c5372-110">İçin bağlıyorsanız bir <xref:System.Collections.IList>, görüntü üye listesinde türünde ortak bir özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c5372-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
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
    >  <span data-ttu-id="c5372-111">Uygulamayan bir veri kaynağına bağlı değilse <xref:System.ComponentModel.IBindingList> arabirimi, aşağıdaki gibi bir <xref:System.Collections.ArrayList>, veri kaynağı güncelleştirildiğinde ilişkili denetimin veri güncelleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="c5372-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="c5372-112">Varsa, örneğin, bir birleşik giriş kutusu bağlı bir <xref:System.Collections.ArrayList> ve veri eklenir <xref:System.Collections.ArrayList>, bu yeni öğeler açılan kutuda görünmez.</span><span class="sxs-lookup"><span data-stu-id="c5372-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="c5372-113">Ancak, çağırarak güncelleştirilmesi birleşik giriş kutusu uygulayabilirsiniz <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> ve <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> örneği üzerinde yöntemleri <xref:System.Windows.Forms.BindingContext> sınıfı denetimin bağlı olduğu.</span><span class="sxs-lookup"><span data-stu-id="c5372-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5372-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5372-114">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [<span data-ttu-id="c5372-115">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="c5372-115">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="c5372-116">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5372-116">Data Binding and Windows Forms</span></span>](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="c5372-117">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="c5372-117">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
