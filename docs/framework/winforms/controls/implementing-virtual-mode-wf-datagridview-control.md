---
title: "İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma"
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
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31806d3ed13776e26634914b48bc887297ea4dab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="82387-102">İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="82387-102">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="82387-103">Çok büyük miktarda tablo verilerin görüntülemek istediğinizde bir <xref:System.Windows.Forms.DataGridView> ayarlayabileceğiniz denetimi <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliğine `true` ve açıkça kendi veri deposu denetimin etkileşim yönetin.</span><span class="sxs-lookup"><span data-stu-id="82387-103">When you want to display very large quantities of tabular data in a <xref:System.Windows.Forms.DataGridView> control, you can set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and explicitly manage the control's interaction with its data store.</span></span> <span data-ttu-id="82387-104">Bu, bu durumda denetim performansını ince ayar sağlar.</span><span class="sxs-lookup"><span data-stu-id="82387-104">This lets you fine-tune the performance of the control in this situation.</span></span>  
  
 <span data-ttu-id="82387-105"><xref:System.Windows.Forms.DataGridView> Denetimi, bir özel veri deposuyla etkileşime geçmesini işleyebilir çeşitli olaylarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="82387-105">The <xref:System.Windows.Forms.DataGridView> control provides several events that you can handle to interact with a custom data store.</span></span> <span data-ttu-id="82387-106">Bu kılavuzda bu olay işleyicileri uygulama işleminde size rehberlik eder.</span><span class="sxs-lookup"><span data-stu-id="82387-106">This walkthrough guides you through the process of implementing these event handlers.</span></span> <span data-ttu-id="82387-107">Bu konuda aşağıdaki kod örneğinde çok basit veri kaynağı gösterim amaçları için kullanır.</span><span class="sxs-lookup"><span data-stu-id="82387-107">The code example in this topic uses a very simple data source for illustration purposes.</span></span> <span data-ttu-id="82387-108">Bir üretim ortamında genellikle yalnızca bir önbelleğine görüntülemek ve işlemek için ihtiyacınız satırları yükleyeceğiniz <xref:System.Windows.Forms.DataGridView> etkileşim ve önbellek güncelleştirmek için olaylar.</span><span class="sxs-lookup"><span data-stu-id="82387-108">In a production setting, you will typically load only the rows you need to display into a cache, and handle <xref:System.Windows.Forms.DataGridView> events to interact with and update the cache.</span></span> <span data-ttu-id="82387-109">Daha fazla bilgi için bkz: [Just-In-Time verileri yüklenirken Windows Forms DataGridView denetiminde ile sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span><span class="sxs-lookup"><span data-stu-id="82387-109">For more information, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span></span>  
  
 <span data-ttu-id="82387-110">Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde sanal modu uygulama](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="82387-110">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="82387-111">Form Oluşturma</span><span class="sxs-lookup"><span data-stu-id="82387-111">Creating the Form</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="82387-112">Sanal mod uygulamak için</span><span class="sxs-lookup"><span data-stu-id="82387-112">To implement virtual mode</span></span>  
  
1.  <span data-ttu-id="82387-113">Türeyen bir sınıf oluşturun <xref:System.Windows.Forms.Form> ve içeren bir <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="82387-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="82387-114">Aşağıdaki kod, bazı temel başlatma içerir.</span><span class="sxs-lookup"><span data-stu-id="82387-114">The following code contains some basic initialization.</span></span> <span data-ttu-id="82387-115">Sonraki adımlarda kullanılacak olan bazı değişkenler bildirilmektedir, sağlayan bir `Main` yöntemi ve sınıf oluşturucu basit form düzende sağlar.</span><span class="sxs-lookup"><span data-stu-id="82387-115">It declares some variables that will be used in later steps, provides a `Main` method, and provides a simple form layout in the class constructor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  <span data-ttu-id="82387-116">Form için bir işleyici uygulamak <xref:System.Windows.Forms.Form.Load> başlatır olay <xref:System.Windows.Forms.DataGridView> denetim ve veri deposu örnek değerlerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="82387-116">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> control and populates the data store with sample values.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  <span data-ttu-id="82387-117">Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.CellValueNeeded> istenen hücrenin değeri veri deposundan alır olay veya `Customer` nesne şu anda düzenleme.</span><span class="sxs-lookup"><span data-stu-id="82387-117">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event that retrieves the requested cell value from the data store or the `Customer` object currently in edit.</span></span>  
  
     <span data-ttu-id="82387-118">Bu olay her değiştiğinde gerçekleşir <xref:System.Windows.Forms.DataGridView> denetim bir hücre boyama gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="82387-118">This event occurs whenever the <xref:System.Windows.Forms.DataGridView> control needs to paint a cell.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  <span data-ttu-id="82387-119">Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.CellValuePushed> bir düzenlenen hücre değerini depolar olay `Customer` düzenlenen satır temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="82387-119">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValuePushed> event that stores an edited cell value in the `Customer` object representing the edited row.</span></span> <span data-ttu-id="82387-120">Bu olay, kullanıcı hücrenin değerini değiştirme uygulayan her gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="82387-120">This event occurs whenever the user commits a cell value change.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  <span data-ttu-id="82387-121">Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.NewRowNeeded> yeni bir olay `Customer` yeni oluşturulan bir satır temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="82387-121">Implement a handler for the <xref:System.Windows.Forms.DataGridView.NewRowNeeded> event that creates a new `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="82387-122">Bu olay, yeni kayıtlar için satır kullanıcının girdiği olduğunda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="82387-122">This event occurs whenever the user enters the row for new records.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  <span data-ttu-id="82387-123">Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.RowValidated> yeni veya değiştirilmiş satırları veri deposuna kaydeder olay.</span><span class="sxs-lookup"><span data-stu-id="82387-123">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowValidated> event that saves new or modified rows to the data store.</span></span>  
  
     <span data-ttu-id="82387-124">Bu olay, kullanıcının geçerli satır değiştiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="82387-124">This event occurs whenever the user changes the current row.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  <span data-ttu-id="82387-125">Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> gösteren olay olup olmadığını <xref:System.Windows.Forms.DataGridView.CancelRowEdit> olay iki kez düzenleme modunda veya bir kez düzenleme modunda dışında ESC tuşuna basarak satır geri al kullanıcı işaret ettiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="82387-125">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event that indicates whether the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event will occur when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span>  
  
     <span data-ttu-id="82387-126">Varsayılan olarak, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> geçerli satırda hücreler sürece değiştiren satır geri al oluşur <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> özelliği ayarlanmış `true` içinde <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="82387-126">By default, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> occurs upon row reversion when any cells in the current row have been modified unless the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property is set to `true` in the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span> <span data-ttu-id="82387-127">Bu olay, yürütme kapsam çalışma zamanında belirlenir yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="82387-127">This event is useful when the commit scope is determined at run time.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  <span data-ttu-id="82387-128">Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.CancelRowEdit> değerlerini atar olay `Customer` geçerli satır temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="82387-128">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event that discards the values of the `Customer` object representing the current row.</span></span>  
  
     <span data-ttu-id="82387-129">Bu olay, iki kez düzenleme modunda veya bir kez düzenleme modunda dışında ESC tuşuna basarak satır geri al kullanıcı sinyalleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="82387-129">This event occurs when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span> <span data-ttu-id="82387-130">Geçerli satırda hiçbir hücreleri değiştirilmiş veya gerekiyorsa bu olay oluşmaz değerini <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> özelliği ayarlanmış `false` içinde bir <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="82387-130">This event does not occur if no cells in the current row have been modified or if the value of the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property has been set to `false` in a <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <span data-ttu-id="82387-131">Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.UserDeletingRow> varolan siler olay `Customer` veri deposu nesnesi veya bir kaydedilmemiş atar `Customer` yeni oluşturulan bir satır temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="82387-131">Implement a handler for the <xref:System.Windows.Forms.DataGridView.UserDeletingRow> event that deletes an existing `Customer` object from the data store or discards an unsaved `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="82387-132">Her satırda bir başlık tıklayarak ve DELETE tuşuna basarak bir satır kullanıcıyı siler bu olay gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="82387-132">This event occurs whenever the user deletes a row by clicking a row header and pressing the DELETE key.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. <span data-ttu-id="82387-133">Basit bir uygulama `Customers` Bu kod örneği tarafından kullanılan veri öğelerini temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="82387-133">Implement a simple `Customers` class to represent the data items used by this code example.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="82387-134">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="82387-134">Testing the Application</span></span>  
 <span data-ttu-id="82387-135">Artık formun beklendiği gibi davranır emin olmak için test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82387-135">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="82387-136">Formu sınamak için</span><span class="sxs-lookup"><span data-stu-id="82387-136">To test the form</span></span>  
  
-   <span data-ttu-id="82387-137">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="82387-137">Compile and run the application.</span></span>  
  
     <span data-ttu-id="82387-138">Göreceğiniz bir <xref:System.Windows.Forms.DataGridView> denetim üç müşteri kayıtları ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="82387-138">You will see a <xref:System.Windows.Forms.DataGridView> control populated with three customer records.</span></span> <span data-ttu-id="82387-139">Bir satır içinde birden fazla hücre değerlerini değiştirin ve iki kez düzenleme modunda ve tüm satır kendi özgün değerlerine geri döndürmek için düzenleme moduna dışında bir kez ESC tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="82387-139">You can modify the values of multiple cells in a row and press ESC twice in edit mode and once outside of edit mode to revert the entire row to its original values.</span></span> <span data-ttu-id="82387-140">Değiştirdiğinizde, ekleyin veya denetimindeki satırları silme `Customer` nesneleri veri deposunda değişiklik, eklenen veya de silinir.</span><span class="sxs-lookup"><span data-stu-id="82387-140">When you modify, add, or delete rows in the control, `Customer` objects in the data store are modified, added, or deleted as well.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="82387-141">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="82387-141">Next Steps</span></span>  
 <span data-ttu-id="82387-142">Bu uygulama, sanal modda uygulamak için tanıtıcı olayları temel bir anlayış sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="82387-142">This application gives you a basic understanding of the events you must handle to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="82387-143">Çeşitli yollarla temel bu uygulamada artırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="82387-143">You can improve this basic application in a number of ways:</span></span>  
  
-   <span data-ttu-id="82387-144">Dış veritabanı değerlerinden önbelleğe alan bir veri deposu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="82387-144">Implement a data store that caches values from an external database.</span></span> <span data-ttu-id="82387-145">Önbelleğe almak ve yalnızca küçük miktarda bellek istemci bilgisayardaki tükettikten sırasında görüntülemek için gerekli nedir içeren değerleri gerektiği gibi atmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="82387-145">The cache should retrieve and discard values as necessary so that it only contains what is necessary for display while consuming a small amount of memory on the client computer.</span></span>  
  
-   <span data-ttu-id="82387-146">Gereksinimlerinize bağlı olarak veri deposu performansını ince ayar.</span><span class="sxs-lookup"><span data-stu-id="82387-146">Fine-tune the performance of the data store depending on your requirements.</span></span> <span data-ttu-id="82387-147">Örneğin, istemci bilgisayar bellek kısıtlamaları yerine yavaş ağ bağlantıları için daha büyük bir önbellek boyutu kullanarak ve veritabanı sorguları sayısını en aza indirme dengelemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82387-147">For example, you might want to compensate for slow network connections rather than client-computer memory limitations by using a larger cache size and minimizing the number of database queries.</span></span>  
  
 <span data-ttu-id="82387-148">Dış veritabanı değerlerinden önbelleğe alma hakkında daha fazla bilgi için bkz [nasıl yapılır: Windows Forms DataGridView denetimini Just-In-Time veri yükleme ile sanal modu uygulama](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="82387-148">For more information about caching values from an external database, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82387-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="82387-149">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>  
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>  
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>  
 <xref:System.Windows.Forms.DataGridView.RowValidated>  
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>  
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>  
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>  
 [<span data-ttu-id="82387-150">Performans ayarlama Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="82387-150">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="82387-151">Windows Forms DataGridView denetimini ölçeklendirme için en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="82387-151">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="82387-152">Tam zamanında veri Windows Forms DataGridView denetiminde yükleme ile sanal modu uygulama</span><span class="sxs-lookup"><span data-stu-id="82387-152">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 [<span data-ttu-id="82387-153">Nasıl yapılır: sanal modu Windows Forms DataGridView denetiminde</span><span class="sxs-lookup"><span data-stu-id="82387-153">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
