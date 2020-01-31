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
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="8a7a8-102">Nasıl yapılır: Windows Forms ComboBox veya ListBox Denetimini Verilere Bağlama</span><span class="sxs-lookup"><span data-stu-id="8a7a8-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="8a7a8-103">Bir veritabanındaki verilere göz atma, yeni veriler girme veya var olan verileri düzenlemek gibi görevleri gerçekleştirmek için <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.ListBox> verileri bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a7a8-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="8a7a8-104">ComboBox veya ListBox denetimini bağlamak için</span><span class="sxs-lookup"><span data-stu-id="8a7a8-104">To bind a ComboBox or ListBox control</span></span>  
  
1. <span data-ttu-id="8a7a8-105">`DataSource` özelliğini bir veri kaynağı nesnesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8a7a8-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="8a7a8-106">Olası veri kaynakları, veri, veri tablosu, veri görünümü, veri kümesi, veri görünümü Yöneticisi, bir dizi veya <xref:System.Collections.IList> arabirimini uygulayan herhangi bir sınıf ile ilişkili <xref:System.Windows.Forms.BindingSource> içerir.</span><span class="sxs-lookup"><span data-stu-id="8a7a8-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="8a7a8-107">Daha fazla bilgi için bkz. [Windows Forms tarafından desteklenen veri kaynakları](../data-sources-supported-by-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8a7a8-107">For more information, see [Data Sources Supported by Windows Forms](../data-sources-supported-by-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="8a7a8-108">Bir tabloya bağlıyorsanız, `DisplayMember` özelliğini veri kaynağındaki bir sütunun adı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8a7a8-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="8a7a8-109">\- veya -</span><span class="sxs-lookup"><span data-stu-id="8a7a8-109">\- or -</span></span>  
  
     <span data-ttu-id="8a7a8-110">Bir <xref:System.Collections.IList>bağlıyorsanız, görüntüleme üyesini listedeki türün ortak özelliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8a7a8-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
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
    > <span data-ttu-id="8a7a8-111"><xref:System.Collections.ArrayList>gibi <xref:System.ComponentModel.IBindingList> arabirimini uygulamayan bir veri kaynağına bağlandıysanız, veri kaynağı güncelleştirildiği zaman, bağlanan denetimin verileri güncellenmez.</span><span class="sxs-lookup"><span data-stu-id="8a7a8-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="8a7a8-112">Örneğin, bir <xref:System.Collections.ArrayList> bağlantılı bir Birleşik giriş kutusu varsa ve veriler <xref:System.Collections.ArrayList>eklenirse, bu yeni öğeler Birleşik giriş kutusunda görünmez.</span><span class="sxs-lookup"><span data-stu-id="8a7a8-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="8a7a8-113">Ancak, denetimin bağlı olduğu <xref:System.Windows.Forms.BindingContext> sınıfının örneği üzerinde <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> ve <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> yöntemlerini çağırarak açılan kutuyu güncelleştirilmesini zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a7a8-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a7a8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a7a8-114">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="8a7a8-115">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="8a7a8-115">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="8a7a8-116">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a7a8-116">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="8a7a8-117">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="8a7a8-117">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
