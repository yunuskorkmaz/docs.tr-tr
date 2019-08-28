---
title: 'İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: cee6fe3b049378fa7bbe2585a3607049eaf231bc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046084"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="fef93-102">İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma</span><span class="sxs-lookup"><span data-stu-id="fef93-102">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>

<span data-ttu-id="fef93-103">Temel alınan veri deposundaki hataları işleme, veri girişi uygulaması için gerekli bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="fef93-103">Handling errors from the underlying data store is a required feature for a data-entry application.</span></span> <span data-ttu-id="fef93-104">Windows Forms <xref:System.Windows.Forms.DataGridView> denetimi, veri deposu bir kısıtlama ihlali algıladığında <xref:System.Windows.Forms.DataGridView.DataError> veya bozuk bir iş kuralı algıladığında oluşan olayını ortaya çıkaran şekilde kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="fef93-104">The Windows Forms <xref:System.Windows.Forms.DataGridView> control makes this easy by exposing the <xref:System.Windows.Forms.DataGridView.DataError> event, which is raised when the data store detects a constraint violation or a broken business rule.</span></span>

<span data-ttu-id="fef93-105">Bu izlenecek yolda, Northwind örnek veritabanındaki `Customers` tablodan satırları alacak ve bunları bir <xref:System.Windows.Forms.DataGridView> denetimde görüntüleriz.</span><span class="sxs-lookup"><span data-stu-id="fef93-105">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="fef93-106">Yeni bir satırda `CustomerID` veya düzenlenmiş var olan bir satırda yinelenen bir değer algılandığında <xref:System.Windows.Forms.DataGridView.DataError> , bu durum, özel durumu açıklayan bir <xref:System.Windows.Forms.MessageBox> görüntüleyerek işlenecek olan olay oluşur.</span><span class="sxs-lookup"><span data-stu-id="fef93-106">When a duplicate `CustomerID` value is detected in a new row or an edited existing row, the <xref:System.Windows.Forms.DataGridView.DataError> event will occur, which will be handled by displaying a <xref:System.Windows.Forms.MessageBox> that describes the exception.</span></span>

<span data-ttu-id="fef93-107">Bu konudaki kodu tek bir liste olarak kopyalamak için bkz [. nasıl yapılır: Windows Forms DataGridView Denetimindeki](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)veri girişi sırasında oluşan hataları işleyin.</span><span class="sxs-lookup"><span data-stu-id="fef93-107">To copy the code in this topic as a single listing, see [How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fef93-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="fef93-108">Prerequisites</span></span>

<span data-ttu-id="fef93-109">Bu izlenecek yolu tamamlamak için şunlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="fef93-109">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="fef93-110">Northwind SQL Server örnek veritabanına sahip bir sunucuya erişim.</span><span class="sxs-lookup"><span data-stu-id="fef93-110">Access to a server that has the Northwind SQL Server sample database.</span></span>

## <a name="creating-the-form"></a><span data-ttu-id="fef93-111">Form Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fef93-111">Creating the Form</span></span>

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a><span data-ttu-id="fef93-112">DataGridView Denetimindeki veri girişi hatalarını işlemek için</span><span class="sxs-lookup"><span data-stu-id="fef93-112">To handle data-entry errors in the DataGridView control</span></span>

1. <span data-ttu-id="fef93-113">Öğesinden <xref:System.Windows.Forms.Form> türetilen ve bir <xref:System.Windows.Forms.DataGridView> denetim ve <xref:System.Windows.Forms.BindingSource> bileşen içeren bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fef93-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>

    <span data-ttu-id="fef93-114">Aşağıdaki kod örneği temel başlatma sağlar ve bir `Main` yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="fef93-114">The following code example provides basic initialization and includes a `Main` method.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. <span data-ttu-id="fef93-115">Veritabanına bağlanma ayrıntılarını işlemek için formunuzun sınıf tanımına bir yöntem uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fef93-115">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>

    <span data-ttu-id="fef93-116">Bu kod örneği, doldurulmuş `GetData` <xref:System.Data.DataTable> bir nesne döndüren bir yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fef93-116">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="fef93-117">Değişkeni, `connectionString` veritabanınız için uygun bir değere ayarladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fef93-117">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="fef93-118">Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="fef93-118">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="fef93-119">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="fef93-119">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="fef93-120">Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="fef93-120">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. <span data-ttu-id="fef93-121"><xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.Form.Load> Ve<xref:System.Windows.Forms.BindingSource> ' i başlatan ve veri bağlamayı ayarlayan formunuzun olayı için bir işleyici uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fef93-121">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. <span data-ttu-id="fef93-122">Üzerinde olayı işleyin. <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.DataError></span><span class="sxs-lookup"><span data-stu-id="fef93-122">Handle the <xref:System.Windows.Forms.DataGridView.DataError> event on the <xref:System.Windows.Forms.DataGridView>.</span></span>

    <span data-ttu-id="fef93-123">Hatanın bağlamı bir işleme işlemi ise, hatayı bir <xref:System.Windows.Forms.MessageBox>ile görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="fef93-123">If the context for the error is a commit operation, display the error in a <xref:System.Windows.Forms.MessageBox>.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a><span data-ttu-id="fef93-124">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="fef93-124">Testing the Application</span></span>

<span data-ttu-id="fef93-125">Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fef93-125">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="fef93-126">Formu test etmek için</span><span class="sxs-lookup"><span data-stu-id="fef93-126">To test the form</span></span>

- <span data-ttu-id="fef93-127">Uygulamayı çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="fef93-127">Press F5 to run the application.</span></span>

  <span data-ttu-id="fef93-128">Müşteriler tablosundan alınan verilerle <xref:System.Windows.Forms.DataGridView> doldurulmuş bir denetim görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="fef93-128">You will see a <xref:System.Windows.Forms.DataGridView> control filled with data from the Customers table.</span></span> <span data-ttu-id="fef93-129">İçin `CustomerID` yinelenen bir değer girerseniz ve düzenleme hareketi yaparsanız, hücre değeri otomatik olarak döndürülür ve veri girişi hatasını görüntüleyen bir <xref:System.Windows.Forms.MessageBox> görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="fef93-129">If you enter a duplicate value for `CustomerID` and commit the edit, the cell value will revert automatically and you will see a <xref:System.Windows.Forms.MessageBox> that displays the data entry error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fef93-130">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="fef93-130">Next Steps</span></span>

<span data-ttu-id="fef93-131">Bu uygulama, <xref:System.Windows.Forms.DataGridView> denetimin yeteneklerini temel olarak öğrenmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fef93-131">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="fef93-132"><xref:System.Windows.Forms.DataGridView> Denetimin görünümünü ve davranışını çeşitli yollarla özelleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fef93-132">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>

- <span data-ttu-id="fef93-133">Kenarlık ve başlık stillerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fef93-133">Change border and header styles.</span></span> <span data-ttu-id="fef93-134">Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView Denetimindeki](change-the-border-and-gridline-styles-in-the-datagrid.md)kenarlık ve kılavuz çizgisi stillerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fef93-134">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>

- <span data-ttu-id="fef93-135"><xref:System.Windows.Forms.DataGridView> Denetim için Kullanıcı girişini etkinleştirin veya kısıtlayın.</span><span class="sxs-lookup"><span data-stu-id="fef93-135">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="fef93-136">Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView denetiminde](prevent-row-addition-and-deletion-datagridview.md)satır eklemeyi ve silmeyi önleyin ve [şunları yapın: Sütunları Windows Forms DataGridView denetiminde](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="fef93-136">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="fef93-137"><xref:System.Windows.Forms.DataGridView> Denetim için Kullanıcı girişini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="fef93-137">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="fef93-138">Daha fazla bilgi için bkz [. İzlenecek yol: Windows Forms DataGridView Denetimindeki](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)veriler doğrulanıyor.</span><span class="sxs-lookup"><span data-stu-id="fef93-138">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="fef93-139">Sanal modu kullanarak çok büyük veri kümelerini işleyin.</span><span class="sxs-lookup"><span data-stu-id="fef93-139">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="fef93-140">Daha fazla bilgi için bkz [. İzlenecek yol: Windows Forms DataGridView denetiminde](implementing-virtual-mode-wf-datagridview-control.md)sanal mod uygulama.</span><span class="sxs-lookup"><span data-stu-id="fef93-140">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>

- <span data-ttu-id="fef93-141">Hücrelerin görünümünü özelleştirin.</span><span class="sxs-lookup"><span data-stu-id="fef93-141">Customize the appearance of cells.</span></span> <span data-ttu-id="fef93-142">Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView Denetimindeki](customize-the-appearance-of-cells-in-the-datagrid.md) hücrelerin görünümünü özelleştirin ve [şunları yapın: Windows Forms DataGridView denetimi](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)Için varsayılan hücre stillerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fef93-142">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fef93-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fef93-143">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="fef93-144">Windows Forms DataGridView Denetiminde Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="fef93-144">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="fef93-145">Nasıl yapılır: Windows Forms DataGridView Denetimindeki veri girişi sırasında oluşan hataları işleme</span><span class="sxs-lookup"><span data-stu-id="fef93-145">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="fef93-146">İzlenecek yol: Windows Forms DataGridView Denetimindeki verileri doğrulama</span><span class="sxs-lookup"><span data-stu-id="fef93-146">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="fef93-147">Bağlantı Bilgilerini Koruma</span><span class="sxs-lookup"><span data-stu-id="fef93-147">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
