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
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="cf3fc-102">Nasıl yapılır: Windows Forms ComboBox veya ListBox Denetimini Verilere Bağlama</span><span class="sxs-lookup"><span data-stu-id="cf3fc-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="cf3fc-103">Bir veritabanındaki verilere göz <xref:System.Windows.Forms.ComboBox> atma <xref:System.Windows.Forms.ListBox> , yeni veriler girme veya varolan verileri düzenlemek gibi görevleri gerçekleştirmek için ve verilerini bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf3fc-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="cf3fc-104">ComboBox veya ListBox denetimini bağlamak için</span><span class="sxs-lookup"><span data-stu-id="cf3fc-104">To bind a ComboBox or ListBox control</span></span>  
  
1. <span data-ttu-id="cf3fc-105">`DataSource` Özelliği bir veri kaynağı nesnesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cf3fc-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="cf3fc-106">Olası veri kaynakları, veri <xref:System.Windows.Forms.BindingSource> , veri tablosu, veri görünümü, veri kümesi, veri görünümü Yöneticisi, bir dizi ya da <xref:System.Collections.IList> arabirimi uygulayan herhangi bir sınıf için bir sınırdır.</span><span class="sxs-lookup"><span data-stu-id="cf3fc-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="cf3fc-107">Daha fazla bilgi için bkz. [Windows Forms tarafından desteklenen veri kaynakları](../data-sources-supported-by-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cf3fc-107">For more information, see [Data Sources Supported by Windows Forms](../data-sources-supported-by-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="cf3fc-108">Bir tabloya bağlıyorsanız, `DisplayMember` özelliği veri kaynağındaki bir sütunun adı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cf3fc-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="cf3fc-109">\- veya -</span><span class="sxs-lookup"><span data-stu-id="cf3fc-109">\- or -</span></span>  
  
     <span data-ttu-id="cf3fc-110"><xref:System.Collections.IList>' A bağlıyorsanız, görüntüleme üyesini listedeki türün ortak özelliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cf3fc-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
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
    > <span data-ttu-id="cf3fc-111"><xref:System.ComponentModel.IBindingList> Arabirimi uygulamayan bir <xref:System.Collections.ArrayList>veri kaynağına (örneğin,) bağlandıysanız, veri kaynağı güncelleştirildiği zaman, bağlanan denetimin verileri güncellenmez.</span><span class="sxs-lookup"><span data-stu-id="cf3fc-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="cf3fc-112">Örneğin, öğesine bir <xref:System.Collections.ArrayList> Birleşik giriş kutusu varsa ve veriler <xref:System.Collections.ArrayList>öğesine eklenirse, bu yeni öğeler Birleşik giriş kutusunda görünmez.</span><span class="sxs-lookup"><span data-stu-id="cf3fc-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="cf3fc-113">Ancak, denetimin bağlı olduğu <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> <xref:System.Windows.Forms.BindingContext> sınıfın örneğindeki ve <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> yöntemlerini çağırarak Birleşik giriş kutusunu güncelleştirilmesini zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf3fc-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf3fc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf3fc-114">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="cf3fc-115">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="cf3fc-115">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="cf3fc-116">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf3fc-116">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="cf3fc-117">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="cf3fc-117">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
