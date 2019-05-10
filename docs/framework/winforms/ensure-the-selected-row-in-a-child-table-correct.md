---
title: 'Nasıl yapılır: Bir Alt Tabloda Seçilen Satırın Doğru Konumda Kalmasını Sağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- master-details view
- row position [Windows Forms]
- parent/child view [Windows Forms]
- resetting child position
- data binding [.NET Framework], row selection
- caching [.NET Framework], child position
- child position
- master/details view [Windows Forms]
- child tables row selection
- current child position
ms.assetid: c5fa2562-43a4-46fa-a604-52d8526a87bd
ms.openlocfilehash: bbebd9f040c60016305a861abee3723450a7456b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651978"
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a><span data-ttu-id="736f7-102">Nasıl yapılır: Bir Alt Tabloda Seçilen Satırın Doğru Konumda Kalmasını Sağlama</span><span class="sxs-lookup"><span data-stu-id="736f7-102">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>
<span data-ttu-id="736f7-103">Aktardığınızda genellikle, Windows Forms veri bağlama ile çalışırken, verilerin ne üst/alt adlı veya ana/Ayrıntılar görünümü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="736f7-103">Oftentimes when you work with data binding in Windows Forms, you will display data in what is called a parent/child or master/details view.</span></span> <span data-ttu-id="736f7-104">Bu iki denetimlerinde aynı kaynaktan verilerin görüntülendiği bir veri bağlama senaryosu ifade eder.</span><span class="sxs-lookup"><span data-stu-id="736f7-104">This refers to a data-binding scenario where data from the same source is displayed in two controls.</span></span> <span data-ttu-id="736f7-105">Bir denetim seçimini değiştirmeden değiştirmek için ikinci denetimde görüntülenen veri neden olur.</span><span class="sxs-lookup"><span data-stu-id="736f7-105">Changing the selection in one control causes the data displayed in the second control to change.</span></span> <span data-ttu-id="736f7-106">Örneğin, ilk denetim müşteriler ve siparişler listesi ilk denetiminde ise seçili müşterilerle ilgili ikinci bir listesini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="736f7-106">For example, the first control might contain a list of customers and the second a list of orders related to the selected customer in the first control.</span></span>  
  
 <span data-ttu-id="736f7-107">Alt tabloda seçilen olan satır tablonun ilk satırına sıfırlanmaz emin olmak için ek adımlar gerekebilir üst/alt görünüm verileri görüntülerken .NET Framework sürüm 2.0 ile başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="736f7-107">Starting with the .NET Framework version 2.0, when you display data in a parent/child view you might have to take extra steps to make sure that the currently selected row in the child table is not reset to the first row of the table.</span></span> <span data-ttu-id="736f7-108">Bunu yapmak için önbelleğe alma alt tablo konum ve üst tablo değiştikten sonra sıfırlamak alması gerekir.</span><span class="sxs-lookup"><span data-stu-id="736f7-108">In order to do this, you will have to cache the child table position and reset it after the parent table changes.</span></span> <span data-ttu-id="736f7-109">Genellikle alt sıfırlama bir alanda bir üst tablosu değişiklikleri satırının ilk kez gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="736f7-109">Typically the child reset occurs the first time a field in a row of the parent table changes.</span></span>  
  
### <a name="to-cache-the-current-child-position"></a><span data-ttu-id="736f7-110">Geçerli alt konum önbelleğe almak için</span><span class="sxs-lookup"><span data-stu-id="736f7-110">To Cache the Current Child Position</span></span>  
  
1. <span data-ttu-id="736f7-111">Bağımlı liste konumu depolamak için bir tam sayı değişkeni ve alt konum önbelleğe verilip verilmeyeceğini depolamak için bir Boolean değişkeni bildirir.</span><span class="sxs-lookup"><span data-stu-id="736f7-111">Declare an integer variable to store the child list position and a Boolean variable to store whether to cache the child position.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2. <span data-ttu-id="736f7-112">Tanıtıcı <xref:System.Windows.Forms.CurrencyManager.ListChanged> bağlama için olay <xref:System.Windows.Forms.CurrencyManager> ve denetlemek için bir <xref:System.ComponentModel.ListChangedType> , <xref:System.ComponentModel.ListChangedType.Reset>.</span><span class="sxs-lookup"><span data-stu-id="736f7-112">Handle the <xref:System.Windows.Forms.CurrencyManager.ListChanged> event for the binding's <xref:System.Windows.Forms.CurrencyManager> and check for a <xref:System.ComponentModel.ListChangedType> of <xref:System.ComponentModel.ListChangedType.Reset>.</span></span>  
  
3. <span data-ttu-id="736f7-113">Geçerli konumunu denetleyin <xref:System.Windows.Forms.CurrencyManager>.</span><span class="sxs-lookup"><span data-stu-id="736f7-113">Check the current position of the <xref:System.Windows.Forms.CurrencyManager>.</span></span> <span data-ttu-id="736f7-114">Listedeki ilk girdi'dan büyük olup olmadığı (genellikle 0), bir değişkene kaydedin.</span><span class="sxs-lookup"><span data-stu-id="736f7-114">If it is greater than first entry in the list (typically 0), save it to a variable.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="736f7-115">Üst listenin işlemek <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> ana para birimi Yöneticisi için olay.</span><span class="sxs-lookup"><span data-stu-id="736f7-115">Handle the parent list's <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> event for the parent currency manager.</span></span> <span data-ttu-id="736f7-116">İşleyicisinde bir önbelleğe alma bir senaryo değildir belirtmek için Boolean değeri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="736f7-116">In the handler, set the Boolean value to indicate it is not a caching scenario.</span></span> <span data-ttu-id="736f7-117">Varsa <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> üst değişikliktir liste konumu değiştirme ve öğe değeri değişikliği oluşur.</span><span class="sxs-lookup"><span data-stu-id="736f7-117">If the <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> occurs, the change to the parent is a list position change and not an item value change.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a><span data-ttu-id="736f7-118">Alt konumu sıfırlama</span><span class="sxs-lookup"><span data-stu-id="736f7-118">To Reset the Child Position</span></span>  
  
1. <span data-ttu-id="736f7-119">Tanıtıcı <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> alt için olay bağlamanın <xref:System.Windows.Forms.CurrencyManager>.</span><span class="sxs-lookup"><span data-stu-id="736f7-119">Handle the <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> event for the child binding's <xref:System.Windows.Forms.CurrencyManager>.</span></span>  
  
2. <span data-ttu-id="736f7-120">Önceki yordamda kaydedilen önbelleğe alınmış konumuna alt tablo konum sıfırlayın.</span><span class="sxs-lookup"><span data-stu-id="736f7-120">Reset the child table position to the cached position saved in the previous procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="736f7-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="736f7-121">Example</span></span>  
 <span data-ttu-id="736f7-122">Aşağıdaki örnek, geçerli konum kaydetmek gösterilmiştir <xref:System.Windows.Forms.CurrencyManager>sunulabilen bir alt tabloda ve sıfırlama üst tablosunda bir düzenleme tamamlandıktan sonra konumu.</span><span class="sxs-lookup"><span data-stu-id="736f7-122">The following example demonstrates how to save the current position on the <xref:System.Windows.Forms.CurrencyManager>.for a child table and reset the position after an edit is completed on the parent table.</span></span> <span data-ttu-id="736f7-123">Bu örnek iki tane <xref:System.Windows.Forms.DataGridView> iki tablo ilişkili bir <xref:System.Data.DataSet> kullanarak bir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="736f7-123">This example contains two <xref:System.Windows.Forms.DataGridView> controls bound to two tables in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="736f7-124">İki tablo arasında bir ilişki kurulur ve ilişki eklendiğinden <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="736f7-124">A relation is established between the two tables and the relation is added to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="736f7-125">Tanıtım amacıyla üçüncü satır alt tablo konumu başlangıçta ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="736f7-125">The position in the child table is initially set to the third row for demonstration purposes.</span></span>  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 <span data-ttu-id="736f7-126">Örnek kodu test etmek için aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="736f7-126">To test the code example, perform the following steps:</span></span>  
  
1. <span data-ttu-id="736f7-127">Örneği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="736f7-127">Run the example.</span></span>  
  
2. <span data-ttu-id="736f7-128">Emin **önbellek ve konumlandırma sıfırlama** onay kutusu seçilidir.</span><span class="sxs-lookup"><span data-stu-id="736f7-128">Make sure the **Cache and reset position** check box is selected.</span></span>  
  
3. <span data-ttu-id="736f7-129">Tıklayın **Temizle üst alan** üst tablo bir alanda bir değişiklik neden düğme.</span><span class="sxs-lookup"><span data-stu-id="736f7-129">Click the **Clear parent field** button to cause a change in a field of the parent table.</span></span> <span data-ttu-id="736f7-130">Alt tabloda seçilen satırın değişmez dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="736f7-130">Notice that the selected row in the child table does not change.</span></span>  
  
4. <span data-ttu-id="736f7-131">Kapatın ve örneği tekrar çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="736f7-131">Close and run the example again.</span></span> <span data-ttu-id="736f7-132">Yalnızca üst satırdaki ilk değişiklik üzerinde sıfırlama davranışı oluştuğu için bunu yapmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="736f7-132">You need to do this because the reset behavior occurs only on the first change in the parent row.</span></span>  
  
5. <span data-ttu-id="736f7-133">NET **önbellek ve konumlandırma sıfırlama** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="736f7-133">Clear the **Cache and reset position** check box.</span></span>  
  
6. <span data-ttu-id="736f7-134">Tıklayın **Temizle üst alan** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="736f7-134">Click the **Clear parent field** button.</span></span> <span data-ttu-id="736f7-135">Alt tabloda seçilen satırın ilk satırın değiştiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="736f7-135">Notice that the selected row in the child table changes to the first row.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="736f7-136">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="736f7-136">Compiling the Code</span></span>  
 <span data-ttu-id="736f7-137">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="736f7-137">This example requires:</span></span>  
  
- <span data-ttu-id="736f7-138">Sistem, System.Data System.Drawing, System.Windows.Forms ve System.XML derlemesine ilişkin başvurular.</span><span class="sxs-lookup"><span data-stu-id="736f7-138">References to the System, System.Data, System.Drawing, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="736f7-139">Bu örnek komut satırından Visual Basic veya Visual C# için oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [yapı komut satırı ile csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="736f7-139">For information about how to build this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="736f7-140">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="736f7-140">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="736f7-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="736f7-141">See also</span></span>

- [<span data-ttu-id="736f7-142">Nasıl yapılır: Birden çok denetimin eşitlenmiş kalmasını aynı veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="736f7-142">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](multiple-controls-bound-to-data-source-synchronized.md)
- [<span data-ttu-id="736f7-143">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="736f7-143">BindingSource Component</span></span>](./controls/bindingsource-component.md)
- [<span data-ttu-id="736f7-144">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="736f7-144">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
