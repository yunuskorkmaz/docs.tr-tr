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
ms.openlocfilehash: b869898a20008343b6c6cbe4bc7e399fc86fb232
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306059"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="09fc7-102">Nasıl yapılır: Windows Forms ComboBox veya ListBox Denetimini Verilere Bağlama</span><span class="sxs-lookup"><span data-stu-id="09fc7-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="09fc7-103">Bağlayabilirsiniz <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.ListBox> verileri bir veritabanındaki verilere gözatma gibi görevleri gerçekleştirmek için yeni veri girme veya mevcut bir veri düzenleme.</span><span class="sxs-lookup"><span data-stu-id="09fc7-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="09fc7-104">Bir ComboBox veya ListBox denetimini bağlamak için</span><span class="sxs-lookup"><span data-stu-id="09fc7-104">To bind a ComboBox or ListBox control</span></span>  
  
1. <span data-ttu-id="09fc7-105">Ayarlama `DataSource` özelliği için bir veri kaynağı nesnesi.</span><span class="sxs-lookup"><span data-stu-id="09fc7-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="09fc7-106">Olası veri kaynaklarını içeren bir <xref:System.Windows.Forms.BindingSource> ilişkili verileri, bir veri tablosu, bir veri görünümü, bir veri kümesi, veri görüntüleme Yöneticisi, bir dizi veya uygulayan sınıf <xref:System.Collections.IList> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="09fc7-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="09fc7-107">Daha fazla bilgi için [Windows Forms tarafından desteklenen veri kaynakları](../data-sources-supported-by-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="09fc7-107">For more information, see [Data Sources Supported by Windows Forms](../data-sources-supported-by-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="09fc7-108">Bir tabloya bağlanıyorsanız, ayarlama `DisplayMember` özelliğini veri kaynağındaki bir sütunun adı.</span><span class="sxs-lookup"><span data-stu-id="09fc7-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="09fc7-109">\- veya -</span><span class="sxs-lookup"><span data-stu-id="09fc7-109">\- or -</span></span>  
  
     <span data-ttu-id="09fc7-110">İçin bağlıyorsanız bir <xref:System.Collections.IList>, ekran üye listesindeki türü ortak özellik ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="09fc7-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
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
    >  <span data-ttu-id="09fc7-111">Uygulamayan bir veri kaynağına bağlı olup olmadığını <xref:System.ComponentModel.IBindingList> arabirim gibi bir <xref:System.Collections.ArrayList>, veri kaynağı güncelleştirildiğinde ilişkili denetim verileri güncelleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="09fc7-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="09fc7-112">Varsa, örneğin, bir birleşik giriş kutusu bağlı bir <xref:System.Collections.ArrayList> ve veri eklendiğinde <xref:System.Collections.ArrayList>, bu yeni öğeleri birleşik giriş kutusunda görünmez.</span><span class="sxs-lookup"><span data-stu-id="09fc7-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="09fc7-113">Ancak çağırarak güncelleştirilmesi için birleşik giriş kutusu zorlayabilirsiniz <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> ve <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> örneği üzerinde yöntemleri <xref:System.Windows.Forms.BindingContext> denetimin bağlı olduğu sınıf.</span><span class="sxs-lookup"><span data-stu-id="09fc7-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09fc7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09fc7-114">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="09fc7-115">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="09fc7-115">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="09fc7-116">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="09fc7-116">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="09fc7-117">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="09fc7-117">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
