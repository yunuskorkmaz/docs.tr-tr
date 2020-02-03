---
title: 'İzlenecek yol: DataGridView denetiminde sanal modu uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
ms.openlocfilehash: 5db97b321238bc371c94e627a387bd83ca31b58a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746523"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d4bec-102">İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d4bec-102">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d4bec-103"><xref:System.Windows.Forms.DataGridView> denetiminde çok büyük miktarlarda tablo verisi göstermek istediğinizde, <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliğini `true` olarak ayarlayabilir ve denetimin kendi veri deposuyla etkileşimini açıkça yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4bec-103">When you want to display very large quantities of tabular data in a <xref:System.Windows.Forms.DataGridView> control, you can set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and explicitly manage the control's interaction with its data store.</span></span> <span data-ttu-id="d4bec-104">Bu durum, denetimin performansını bu durumda ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4bec-104">This lets you fine-tune the performance of the control in this situation.</span></span>  
  
 <span data-ttu-id="d4bec-105"><xref:System.Windows.Forms.DataGridView> denetimi, özel bir veri deposuyla etkileşim kurmak için işleyebilmeniz gereken çeşitli olaylar sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4bec-105">The <xref:System.Windows.Forms.DataGridView> control provides several events that you can handle to interact with a custom data store.</span></span> <span data-ttu-id="d4bec-106">Bu izlenecek yol, bu olay işleyicilerini uygulama sürecinde size rehberlik eder.</span><span class="sxs-lookup"><span data-stu-id="d4bec-106">This walkthrough guides you through the process of implementing these event handlers.</span></span> <span data-ttu-id="d4bec-107">Bu konudaki kod örneği, çizim amacıyla çok basit bir veri kaynağı kullanır.</span><span class="sxs-lookup"><span data-stu-id="d4bec-107">The code example in this topic uses a very simple data source for illustration purposes.</span></span> <span data-ttu-id="d4bec-108">Bir üretim ayarında genellikle yalnızca bir önbellekte görüntülemesi gereken satırları yüklersiniz ve önbelleği etkileşimde bulunmak ve güncelleştirmek için <xref:System.Windows.Forms.DataGridView> olaylarını işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4bec-108">In a production setting, you will typically load only the rows you need to display into a cache, and handle <xref:System.Windows.Forms.DataGridView> events to interact with and update the cache.</span></span> <span data-ttu-id="d4bec-109">Daha fazla bilgi için bkz [. Windows Forms DataGridView denetiminde tam zamanında veri yükleme Ile sanal modu uygulama](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span><span class="sxs-lookup"><span data-stu-id="d4bec-109">For more information, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span></span>  
  
 <span data-ttu-id="d4bec-110">Bu konudaki kodu tek bir liste olarak kopyalamak için, bkz. [nasıl yapılır: Windows Forms DataGridView denetiminde sanal modu uygulama](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="d4bec-110">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode in the Windows Forms DataGridView Control](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="d4bec-111">Form Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4bec-111">Creating the Form</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="d4bec-112">Sanal modu uygulamak için</span><span class="sxs-lookup"><span data-stu-id="d4bec-112">To implement virtual mode</span></span>  
  
1. <span data-ttu-id="d4bec-113"><xref:System.Windows.Forms.Form> türetilen ve <xref:System.Windows.Forms.DataGridView> denetimi içeren bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d4bec-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="d4bec-114">Aşağıdaki kod, bazı temel başlatma içerir.</span><span class="sxs-lookup"><span data-stu-id="d4bec-114">The following code contains some basic initialization.</span></span> <span data-ttu-id="d4bec-115">Sonraki adımlarda kullanılacak bazı değişkenler bildirir, bir `Main` yöntemi sağlar ve sınıf oluşturucusunda basit bir form düzeni sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4bec-115">It declares some variables that will be used in later steps, provides a `Main` method, and provides a simple form layout in the class constructor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. <span data-ttu-id="d4bec-116">Formunuzun <xref:System.Windows.Forms.Form.Load> olayı için <xref:System.Windows.Forms.DataGridView> denetimini başlatan ve veri deposunu örnek değerlerle dolduran bir işleyici uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d4bec-116">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> control and populates the data store with sample values.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. <span data-ttu-id="d4bec-117">Veri deposundan veya şu anda düzenleme aşamasında olan `Customer` nesnesinden istenen hücre değerini alan <xref:System.Windows.Forms.DataGridView.CellValueNeeded> olayı için bir işleyici uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d4bec-117">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event that retrieves the requested cell value from the data store or the `Customer` object currently in edit.</span></span>  
  
     <span data-ttu-id="d4bec-118">Bu olay, <xref:System.Windows.Forms.DataGridView> denetimi bir hücreyi boyamak gerektiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="d4bec-118">This event occurs whenever the <xref:System.Windows.Forms.DataGridView> control needs to paint a cell.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. <span data-ttu-id="d4bec-119">Düzenlenen satırı temsil eden `Customer` nesnesinde düzenlenmiş bir hücre değerini depolayan <xref:System.Windows.Forms.DataGridView.CellValuePushed> olayı için bir işleyici uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d4bec-119">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValuePushed> event that stores an edited cell value in the `Customer` object representing the edited row.</span></span> <span data-ttu-id="d4bec-120">Bu olay, Kullanıcı bir hücre değeri değişikliğini her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="d4bec-120">This event occurs whenever the user commits a cell value change.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. <span data-ttu-id="d4bec-121">Yeni oluşturulan bir satırı temsil eden yeni bir `Customer` nesnesi oluşturan <xref:System.Windows.Forms.DataGridView.NewRowNeeded> olayı için bir işleyici uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d4bec-121">Implement a handler for the <xref:System.Windows.Forms.DataGridView.NewRowNeeded> event that creates a new `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="d4bec-122">Bu olay, Kullanıcı her yeni kayıt için satırı girdiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="d4bec-122">This event occurs whenever the user enters the row for new records.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. <span data-ttu-id="d4bec-123">Yeni veya değiştirilmiş satırları veri deposuna kaydeden <xref:System.Windows.Forms.DataGridView.RowValidated> olayı için bir işleyici uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d4bec-123">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowValidated> event that saves new or modified rows to the data store.</span></span>  
  
     <span data-ttu-id="d4bec-124">Bu olay, Kullanıcı geçerli satırı her değiştirdiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="d4bec-124">This event occurs whenever the user changes the current row.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. <span data-ttu-id="d4bec-125">Kullanıcı satır yeniden sürümüne, düzenleme modunda veya düzenleme modunun dışında bir kez tuşlarına basarak, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> olayının ne zaman gerçekleşeceğini belirten <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> olayı için bir işleyici uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d4bec-125">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event that indicates whether the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event will occur when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span>  
  
     <span data-ttu-id="d4bec-126">Varsayılan olarak, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> geçerli satırdaki herhangi bir hücre değiştirildiğinde, <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> olay işleyicide `true` olarak ayarlanmadığı takdirde satır yeniden sürümünden sonra gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="d4bec-126">By default, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> occurs upon row reversion when any cells in the current row have been modified unless the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property is set to `true` in the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span> <span data-ttu-id="d4bec-127">Bu olay, çalışma sırasında kayıt kapsamı saptandığı zaman yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d4bec-127">This event is useful when the commit scope is determined at run time.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. <span data-ttu-id="d4bec-128">Geçerli satırı temsil eden `Customer` nesnesinin değerlerini attığı <xref:System.Windows.Forms.DataGridView.CancelRowEdit> olayı için bir işleyici uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d4bec-128">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event that discards the values of the `Customer` object representing the current row.</span></span>  
  
     <span data-ttu-id="d4bec-129">Bu olay, Kullanıcı, düzenleme modunda veya düzenleme modunun dışında bir kez ESC tuşuna basarak satır yeniden sürümüne işaret ediyorsa meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="d4bec-129">This event occurs when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span> <span data-ttu-id="d4bec-130">Geçerli satırda hiçbir hücre değiştirilmemişse veya <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> özelliğinin değeri bir <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> olay işleyicisinde `false` olarak ayarlandıysa bu olay oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="d4bec-130">This event does not occur if no cells in the current row have been modified or if the value of the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property has been set to `false` in a <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <span data-ttu-id="d4bec-131">Veri deposundan var olan bir `Customer` nesnesini silen veya yeni oluşturulan bir satırı temsil eden kaydedilmemiş bir `Customer` nesnesini attığı <xref:System.Windows.Forms.DataGridView.UserDeletingRow> olayı için bir işleyici uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d4bec-131">Implement a handler for the <xref:System.Windows.Forms.DataGridView.UserDeletingRow> event that deletes an existing `Customer` object from the data store or discards an unsaved `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="d4bec-132">Bu olay, Kullanıcı bir satır başlığına tıklayıp DELETE tuşuna basarak bir satırı sildiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="d4bec-132">This event occurs whenever the user deletes a row by clicking a row header and pressing the DELETE key.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. <span data-ttu-id="d4bec-133">Bu kod örneği tarafından kullanılan veri öğelerini temsil etmek için basit bir `Customers` sınıfı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d4bec-133">Implement a simple `Customers` class to represent the data items used by this code example.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="d4bec-134">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="d4bec-134">Testing the Application</span></span>  
 <span data-ttu-id="d4bec-135">Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4bec-135">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="d4bec-136">Formu test etmek için</span><span class="sxs-lookup"><span data-stu-id="d4bec-136">To test the form</span></span>  
  
- <span data-ttu-id="d4bec-137">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d4bec-137">Compile and run the application.</span></span>  
  
     <span data-ttu-id="d4bec-138">Üç müşteri kaydı ile doldurulmuş bir <xref:System.Windows.Forms.DataGridView> denetimi göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d4bec-138">You will see a <xref:System.Windows.Forms.DataGridView> control populated with three customer records.</span></span> <span data-ttu-id="d4bec-139">Bir satırdaki birden çok hücrenin değerlerini değiştirebilir ve tüm satırı özgün değerlerine dönüştürmek için düzenleme modunun dışında iki kez ESC tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d4bec-139">You can modify the values of multiple cells in a row and press ESC twice in edit mode and once outside of edit mode to revert the entire row to its original values.</span></span> <span data-ttu-id="d4bec-140">Denetimdeki satırları değiştirirken, eklediğinizde veya sildiğinizde, veri deposundaki `Customer` nesneleri de değiştirilir, eklenir veya silinir.</span><span class="sxs-lookup"><span data-stu-id="d4bec-140">When you modify, add, or delete rows in the control, `Customer` objects in the data store are modified, added, or deleted as well.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d4bec-141">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="d4bec-141">Next Steps</span></span>  
 <span data-ttu-id="d4bec-142">Bu uygulama, <xref:System.Windows.Forms.DataGridView> denetiminde sanal modu uygulamak için işlemeniz gereken olayların temel bir şekilde anlaşılmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d4bec-142">This application gives you a basic understanding of the events you must handle to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d4bec-143">Bu temel uygulamayı çeşitli yollarla geliştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d4bec-143">You can improve this basic application in a number of ways:</span></span>  
  
- <span data-ttu-id="d4bec-144">Bir dış veritabanından değerleri önbelleğe alan bir veri deposu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d4bec-144">Implement a data store that caches values from an external database.</span></span> <span data-ttu-id="d4bec-145">Önbellek, istemci bilgisayarda az miktarda bellek tüketirken yalnızca görüntülenmek üzere gerekli olan öğeleri içermesi için gereken değerleri alıp atmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4bec-145">The cache should retrieve and discard values as necessary so that it only contains what is necessary for display while consuming a small amount of memory on the client computer.</span></span>  
  
- <span data-ttu-id="d4bec-146">Gereksinimlerinize bağlı olarak veri deposunun performansını ayrıntılı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d4bec-146">Fine-tune the performance of the data store depending on your requirements.</span></span> <span data-ttu-id="d4bec-147">Örneğin, daha büyük bir önbellek boyutu kullanarak ve veritabanı sorgularının sayısını en aza indirerek, istemci bilgisayar bellek sınırlamaları yerine yavaş ağ bağlantılarını dengelemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4bec-147">For example, you might want to compensate for slow network connections rather than client-computer memory limitations by using a larger cache size and minimizing the number of database queries.</span></span>  
  
 <span data-ttu-id="d4bec-148">Bir dış veritabanından verileri önbelleğe alma hakkında daha fazla bilgi için, bkz. [nasıl yapılır: Windows Forms DataGridView denetiminde tam zamanında veri yükleme Ile sanal modu uygulama](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="d4bec-148">For more information about caching values from an external database, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4bec-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4bec-149">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [<span data-ttu-id="d4bec-150">Windows Forms DataGridView Denetiminde Performans Ayarlaması</span><span class="sxs-lookup"><span data-stu-id="d4bec-150">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d4bec-151">Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d4bec-151">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d4bec-152">Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama</span><span class="sxs-lookup"><span data-stu-id="d4bec-152">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="d4bec-153">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d4bec-153">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
