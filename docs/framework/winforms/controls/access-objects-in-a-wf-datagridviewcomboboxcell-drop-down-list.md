---
title: 'Nasıl yapılır: Windows Forms DataGridViewComboBoxCell Açılır Listesindeki Nesnelere Erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 2758841031be9ca9f0a5eb5e57165191d6870e87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529408"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="94381-102">Nasıl yapılır: Windows Forms DataGridViewComboBoxCell Açılır Listesindeki Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="94381-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="94381-103">Gibi <xref:System.Windows.Forms.ComboBox> denetimi <xref:System.Windows.Forms.DataGridViewComboBoxColumn> ve <xref:System.Windows.Forms.DataGridViewComboBoxCell> türleri açılan listelerine rasgele nesne eklemek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="94381-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="94381-104">Bu özellik, ayrı bir koleksiyonda karşılık gelen nesneleri depolamak zorunda kalmadan bir açılan listedeki karmaşık durumları temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="94381-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="94381-105">Farklı <xref:System.Windows.Forms.ComboBox> denetimi <xref:System.Windows.Forms.DataGridView> türlerine sahip değil bir <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> şu anda seçili nesnenin alma özelliği.</span><span class="sxs-lookup"><span data-stu-id="94381-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="94381-106">Bunun yerine, ayarlamalısınız <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> özelliği, iş nesnesi üzerinde bir özellik adı.</span><span class="sxs-lookup"><span data-stu-id="94381-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="94381-107">Kullanıcı bir seçim yaptığında, hücre iş nesnesi belirtilen özelliği ayarlar <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="94381-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="94381-108">Hücre değeri ile iş nesnesi almak için `ValueMember` özelliği, iş nesnesine başvuru döndüren bir özelliği belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="94381-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="94381-109">Bu nedenle, iş nesnesi türünde denetiminiz altında değil, devralma üzerinden türü genişleterek böyle bir özellik eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="94381-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="94381-110">Aşağıdaki yordamlarda açılan listeyi iş nesnelerle doldurmak ve hücre nesnelerde almak nasıl gösterilmektedir <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="94381-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="94381-111">Aşağı açılan listeye iş nesneleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="94381-111">To add business objects to the drop-down list</span></span>  
  
1.  <span data-ttu-id="94381-112">Yeni bir <xref:System.Windows.Forms.DataGridViewComboBoxColumn> ve doldurmak kendi <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="94381-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="94381-113">Alternatif olarak, sütun ayarlayabilirsiniz <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> iş nesneleri koleksiyonu özelliğine.</span><span class="sxs-lookup"><span data-stu-id="94381-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="94381-114">Bu durumda, ancak, "atanmamış" aşağı açılan listesine koleksiyonunuzda karşılık gelen bir iş nesnesini oluşturmadan ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="94381-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  <span data-ttu-id="94381-115">Ayarlama <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> ve <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="94381-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <span data-ttu-id="94381-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> aşağı açılan listede görüntülenecek iş nesnesinin özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="94381-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indicates the property of the business object to display in the drop-down list.</span></span> <span data-ttu-id="94381-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> İş nesnesi için bir başvuru döndürür özelliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="94381-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  <span data-ttu-id="94381-118">İş nesne türü geçerli örneğine başvuru döndüren bir özelliği içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="94381-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="94381-119">Bu özellik, atanan değer ile adlandırılmalıdır <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> önceki adımda.</span><span class="sxs-lookup"><span data-stu-id="94381-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="94381-120">Şu anda seçili iş nesnesi alınamadı</span><span class="sxs-lookup"><span data-stu-id="94381-120">To retrieve the currently selected business object</span></span>  
  
-   <span data-ttu-id="94381-121">Hücre alma <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliği ve iş nesne türüne dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="94381-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="94381-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="94381-122">Example</span></span>  
 <span data-ttu-id="94381-123">Tam bir örnek iş nesneleri bir açılan listedeki kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="94381-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="94381-124">Örnekte, bir <xref:System.Windows.Forms.DataGridView> denetimi bir koleksiyona bağlı `Task` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="94381-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="94381-125">Her `Task` nesnesi bir `AssignedTo` gösteren özellik `Employee` şu anda bu göreve atanan nesne.</span><span class="sxs-lookup"><span data-stu-id="94381-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="94381-126">`Assigned To` Sütunu görüntüler `Name` her özellik değerini atanan çalışan veya "atanmamış" IF `Task.AssignedTo` özellik değeri `null`.</span><span class="sxs-lookup"><span data-stu-id="94381-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="94381-127">Bu örnek davranışını görüntülemek için aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="94381-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="94381-128">Atamalarını değiştirmek `Assigned To` farklı değerler aşağı açılan listelerden seçerek veya CTRL + 0 birleşik giriş kutusu hücresinde tuşuna basarak sütun.</span><span class="sxs-lookup"><span data-stu-id="94381-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2.  <span data-ttu-id="94381-129">Tıklatın `Generate Report` geçerli atamaları görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="94381-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="94381-130">Bu gösteren bir değişiklik `Assigned To` sütun otomatik olarak güncelleştirir `tasks` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="94381-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3.  <span data-ttu-id="94381-131">Tıklatın bir `Request Status` çağırmak için düğmesini `RequestStatus` yöntemi geçerli `Employee` ilgili satır nesnesi.</span><span class="sxs-lookup"><span data-stu-id="94381-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="94381-132">Bu, seçili nesnenin başarıyla aldı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="94381-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="94381-133">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="94381-133">Compiling the Code</span></span>  
 <span data-ttu-id="94381-134">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="94381-134">This example requires:</span></span>  
  
-   <span data-ttu-id="94381-135">Sistem ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="94381-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94381-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94381-136">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ComboBox>  
 [<span data-ttu-id="94381-137">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="94381-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
