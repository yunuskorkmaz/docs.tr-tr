---
title: DataGridViewComboBoxCell açılır listesindeki nesnelere erişme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 7e76ab1ac9089778e4371f4ee65b06d5ebc570bf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746316"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="321f1-102">Nasıl yapılır: Windows Forms DataGridViewComboBoxCell Açılır Listesindeki Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="321f1-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="321f1-103"><xref:System.Windows.Forms.ComboBox> denetimi gibi <xref:System.Windows.Forms.DataGridViewComboBoxColumn> ve <xref:System.Windows.Forms.DataGridViewComboBoxCell> türleri, açılan listelerine rastgele nesneler eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="321f1-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="321f1-104">Bu özellikle, ilgili nesneleri ayrı bir koleksiyonda depolamak zorunda kalmadan, karmaşık durumları bir açılan listede temsil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="321f1-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="321f1-105"><xref:System.Windows.Forms.ComboBox> denetiminden farklı olarak, <xref:System.Windows.Forms.DataGridView> türler seçili nesneyi almak için bir <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> özelliğine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="321f1-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="321f1-106">Bunun yerine, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> özelliğini iş nesnenizin bir özelliğin adı olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="321f1-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="321f1-107">Kullanıcı bir seçim yaptığında, iş nesnesinin belirtilen özelliği, hücre <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="321f1-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="321f1-108">İş nesnesini hücre değeri aracılığıyla almak için `ValueMember` özelliği, iş nesnesinin kendisi için bir başvuru döndüren bir özelliği belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="321f1-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="321f1-109">Bu nedenle, iş nesnesinin türü denetiminizin altındaysa, türü devralma yoluyla genişleterek böyle bir özelliği eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="321f1-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="321f1-110">Aşağıdaki yordamlarda, bir açılan listeyi iş nesneleriyle doldurma ve nesneleri hücre <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliği aracılığıyla alma işlemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="321f1-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="321f1-111">Açılan listeye iş nesneleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="321f1-111">To add business objects to the drop-down list</span></span>  
  
1. <span data-ttu-id="321f1-112">Yeni bir <xref:System.Windows.Forms.DataGridViewComboBoxColumn> oluşturun ve <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> koleksiyonunu doldurun.</span><span class="sxs-lookup"><span data-stu-id="321f1-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="321f1-113">Alternatif olarak, sütun <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> özelliğini iş nesneleri koleksiyonuna ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="321f1-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="321f1-114">Ancak, bu durumda, koleksiyonunuzda karşılık gelen bir iş nesnesi oluşturmadan açılan listeye "atanmamış" ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="321f1-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2. <span data-ttu-id="321f1-115"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> ve <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="321f1-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <span data-ttu-id="321f1-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>, açılan listede gösterilecek iş nesnesinin özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="321f1-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indicates the property of the business object to display in the drop-down list.</span></span> <span data-ttu-id="321f1-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>, iş nesnesine bir başvuru döndüren özelliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="321f1-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3. <span data-ttu-id="321f1-118">İş nesnesi türünün geçerli örneğe bir başvuru döndüren bir özellik içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="321f1-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="321f1-119">Bu özellik, önceki adımda <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> için atanan değerle birlikte adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="321f1-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="321f1-120">Şu anda seçili olan iş nesnesini almak için</span><span class="sxs-lookup"><span data-stu-id="321f1-120">To retrieve the currently selected business object</span></span>  
  
- <span data-ttu-id="321f1-121">Hücreyi <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliğini alın ve iş nesnesi türüne dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="321f1-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="321f1-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="321f1-122">Example</span></span>  
 <span data-ttu-id="321f1-123">Tam örnek, iş nesnelerinin bir açılan listede kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="321f1-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="321f1-124">Örnekte, bir <xref:System.Windows.Forms.DataGridView> denetimi bir `Task` nesneleri koleksiyonuna bağlanır.</span><span class="sxs-lookup"><span data-stu-id="321f1-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="321f1-125">Her `Task` nesnesi, o göreve atanmış olan `Employee` nesnesini gösteren bir `AssignedTo` özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="321f1-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="321f1-126">`Assigned To` sütununda, atanan her çalışana ait `Name` Özellik değeri veya `Task.AssignedTo` Özellik değeri `null`ise "atanmamış" görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="321f1-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="321f1-127">Bu örneğin davranışını görüntülemek için aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="321f1-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1. <span data-ttu-id="321f1-128">`Assigned To` sütunundaki atamaları, açılan listelerden farklı değerler seçerek veya Birleşik giriş kutusu hücresinde CTRL + 0 tuşlarına basarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="321f1-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2. <span data-ttu-id="321f1-129">Geçerli atamaları göstermek için `Generate Report` ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="321f1-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="321f1-130">Bu, `Assigned To` sütununda bir değişikliğin `tasks` koleksiyonunu otomatik olarak güncelleştirdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="321f1-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3. <span data-ttu-id="321f1-131">Bu satır için geçerli `Employee` nesnesinin `RequestStatus` yöntemini çağırmak için bir `Request Status` düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="321f1-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="321f1-132">Bu, seçilen nesnenin başarıyla alındığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="321f1-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="321f1-133">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="321f1-133">Compiling the Code</span></span>  
 <span data-ttu-id="321f1-134">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="321f1-134">This example requires:</span></span>  
  
- <span data-ttu-id="321f1-135">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="321f1-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="321f1-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="321f1-136">See also</span></span>

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
- [<span data-ttu-id="321f1-137">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="321f1-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
