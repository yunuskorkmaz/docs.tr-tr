---
title: 'Nasıl yapılır: Windows Forms DataGridViewComboBoxCell açılır listesindeki nesnelere erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 8a4731e081b31f74b4f17c2796b56cdf6b95e3e2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705733"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="9976a-102">Nasıl yapılır: Windows Forms DataGridViewComboBoxCell açılır listesindeki nesnelere erişme</span><span class="sxs-lookup"><span data-stu-id="9976a-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="9976a-103">Gibi <xref:System.Windows.Forms.ComboBox> denetimi <xref:System.Windows.Forms.DataGridViewComboBoxColumn> ve <xref:System.Windows.Forms.DataGridViewComboBoxCell> türleri açılan listelerine rastgele bir nesne eklemek etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="9976a-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="9976a-104">Bu özellik, ayrı bir koleksiyonda karşılık gelen nesneleri depolamak zorunda kalmadan bir açılan listedeki karmaşık durumları temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="9976a-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="9976a-105">Farklı <xref:System.Windows.Forms.ComboBox> denetimi <xref:System.Windows.Forms.DataGridView> türlerine sahip değil bir <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> özelliği şu anda seçilen nesne alınıyor.</span><span class="sxs-lookup"><span data-stu-id="9976a-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="9976a-106">Bunun yerine, ayarlamalısınız <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> özelliğini, iş nesnesinde bir özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="9976a-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="9976a-107">Kullanıcı bir seçim yaptığında, hücre iş nesnesi belirtilen özelliği ayarlar <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9976a-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="9976a-108">İş nesnesi aracılığıyla bir hücre değerini almak için `ValueMember` özelliği, iş nesnesine bir başvuru döndürür bir özelliği belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="9976a-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="9976a-109">Bu nedenle, iş nesnesi türünü denetiminiz altında değil, devralma yoluyla türü genişleterek böyle bir özellik eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9976a-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="9976a-110">Nasıl iş nesnesi ile bir açılan listeyi doldurmak ve hücre nesnelerde almak aşağıdaki yordamları göstermek <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9976a-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="9976a-111">İş nesnesi aşağı açılan listesine eklemek için</span><span class="sxs-lookup"><span data-stu-id="9976a-111">To add business objects to the drop-down list</span></span>  
  
1.  <span data-ttu-id="9976a-112">Yeni bir <xref:System.Windows.Forms.DataGridViewComboBoxColumn> ve doldurma kendi <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9976a-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="9976a-113">Alternatif olarak, sütun ayarlayabilirsiniz <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> özelliğini iş nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9976a-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="9976a-114">Bu durumda, ancak, "atanmamış" açılan listeye koleksiyonunuzda karşılık gelen iş nesne oluşturulmadan ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="9976a-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  <span data-ttu-id="9976a-115">Ayarlama <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> ve <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="9976a-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <span data-ttu-id="9976a-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> aşağı açılan listede görüntülenecek iş nesnesinin özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9976a-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indicates the property of the business object to display in the drop-down list.</span></span> <span data-ttu-id="9976a-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> iş nesnesine bir başvuru döndürür özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="9976a-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  <span data-ttu-id="9976a-118">İş nesne türünüz geçerli örneğe bir başvuru döndürür bir özelliği içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9976a-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="9976a-119">Bu özellik, atanan değer kullanılarak adlandırılmalıdır. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> önceki adımda.</span><span class="sxs-lookup"><span data-stu-id="9976a-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="9976a-120">Seçili iş nesnesi alınamadı</span><span class="sxs-lookup"><span data-stu-id="9976a-120">To retrieve the currently selected business object</span></span>  
  
-   <span data-ttu-id="9976a-121">Hücreyi alma <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliği ve iş nesne türüne dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="9976a-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="9976a-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="9976a-122">Example</span></span>  
 <span data-ttu-id="9976a-123">Tam bir örnek açılır listesindeki nesnelere iş kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9976a-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="9976a-124">Örnekte, bir <xref:System.Windows.Forms.DataGridView> denetimin bir koleksiyonuna bağlı `Task` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9976a-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="9976a-125">Her `Task` nesnesinin bir `AssignedTo` gösteren özellik `Employee` nesne şu anda bu göreve atanan kişi.</span><span class="sxs-lookup"><span data-stu-id="9976a-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="9976a-126">`Assigned To` Sütunu görüntüler `Name` her özellik değerini atanan çalışan veya "atanmamış" if `Task.AssignedTo` özellik değeri `null`.</span><span class="sxs-lookup"><span data-stu-id="9976a-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="9976a-127">Bu örnek davranışını görüntülemek için aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="9976a-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="9976a-128">Atamalarını değiştirmek `Assigned To` farklı değerler aşağı açılan listelerden seçerek veya CTRL + 0, birleşik giriş kutusu hücredeki tuşuna basarak sütun.</span><span class="sxs-lookup"><span data-stu-id="9976a-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2.  <span data-ttu-id="9976a-129">Tıklayın `Generate Report` geçerli atamaları görüntülenecek.</span><span class="sxs-lookup"><span data-stu-id="9976a-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="9976a-130">Bu gösteren bir değişiklik `Assigned To` sütun otomatik olarak güncelleştirir `tasks` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9976a-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3.  <span data-ttu-id="9976a-131">' A tıklayın bir `Request Status` çağırmak için düğme `RequestStatus` yöntemi geçerli `Employee` ilgili satır için nesne.</span><span class="sxs-lookup"><span data-stu-id="9976a-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="9976a-132">Bu, seçili nesne başarıyla alınmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="9976a-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9976a-133">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9976a-133">Compiling the Code</span></span>  
 <span data-ttu-id="9976a-134">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="9976a-134">This example requires:</span></span>  
  
-   <span data-ttu-id="9976a-135">Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="9976a-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9976a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9976a-136">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ComboBox>
- [<span data-ttu-id="9976a-137">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="9976a-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
