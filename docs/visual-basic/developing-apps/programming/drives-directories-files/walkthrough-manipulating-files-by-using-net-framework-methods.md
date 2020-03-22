---
title: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], walkthroughs
- text files [Visual Basic], writing to
- reading text files [Visual Basic]
- text, writing to files
- files [Visual Basic], searching
- StreamReader class, walkthroughs
- files [Visual Basic], accessing
- I/O [Visual Basic], writing text to files
- writing to files [Visual Basic], walkthroughs
- StreamWriter class, walkthroughs
- text files [Visual Basic], reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
ms.openlocfilehash: 02cdbcc59e8817ff4ec06c2f78f835cad77b10f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333777"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="6403e-102">İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6403e-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>

<span data-ttu-id="6403e-103">Bu gözden geçirme, sınıfı kullanarak bir dosyanın <xref:System.IO.StreamReader> nasıl açılacağını ve okunduğunu, dosyaya erişilip erişilip erişilenin <xref:System.IO.StreamReader> ilerde denetlendiğini, sınıfın <xref:System.IO.StreamWriter> bir örneğiyle okunan bir dosya içinde bir dize aramasını ve sınıfı kullanarak bir dosyaya nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6403e-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a><span data-ttu-id="6403e-104">Uygulamayı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6403e-104">Creating the Application</span></span>

<span data-ttu-id="6403e-105">Visual Studio'yu başlatın ve kullanıcının belirlenen dosyaya yazmak için kullanabileceği bir form oluşturarak projeye başlayın.</span><span class="sxs-lookup"><span data-stu-id="6403e-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="6403e-106">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6403e-106">To create the project</span></span>

1. <span data-ttu-id="6403e-107">**Dosya** menüsünde **Yeni Proje'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="6403e-107">On the **File** menu, select **New Project**.</span></span>

2. <span data-ttu-id="6403e-108">Yeni **Proje** bölmesinde **Windows Uygulaması'nı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6403e-108">In the **New Project** pane, click **Windows Application**.</span></span>

3. <span data-ttu-id="6403e-109">**Ad** kutusuna `MyDiary` yazın ve **Tamam'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6403e-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>

     <span data-ttu-id="6403e-110">Visual **Studio, Solution Explorer'a**projeyi ekler ve **Windows Forms Designer** açılır.</span><span class="sxs-lookup"><span data-stu-id="6403e-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>

4. <span data-ttu-id="6403e-111">Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6403e-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="6403e-112">**Nesne**</span><span class="sxs-lookup"><span data-stu-id="6403e-112">**Object**</span></span>|<span data-ttu-id="6403e-113">**Özellikler**</span><span class="sxs-lookup"><span data-stu-id="6403e-113">**Properties**</span></span>|<span data-ttu-id="6403e-114">**Değer**</span><span class="sxs-lookup"><span data-stu-id="6403e-114">**Value**</span></span>|
|---|---|---|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="6403e-115">**Adı**</span><span class="sxs-lookup"><span data-stu-id="6403e-115">**Name**</span></span><br /><br /> <span data-ttu-id="6403e-116">**Metin**</span><span class="sxs-lookup"><span data-stu-id="6403e-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="6403e-117">**Giriş Gönder**</span><span class="sxs-lookup"><span data-stu-id="6403e-117">**Submit Entry**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="6403e-118">**Adı**</span><span class="sxs-lookup"><span data-stu-id="6403e-118">**Name**</span></span><br /><br /> <span data-ttu-id="6403e-119">**Metin**</span><span class="sxs-lookup"><span data-stu-id="6403e-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="6403e-120">**Girişi Temizle**</span><span class="sxs-lookup"><span data-stu-id="6403e-120">**Clear Entry**</span></span>|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="6403e-121">**Adı**</span><span class="sxs-lookup"><span data-stu-id="6403e-121">**Name**</span></span><br /><br /> <span data-ttu-id="6403e-122">**Metin**</span><span class="sxs-lookup"><span data-stu-id="6403e-122">**Text**</span></span><br /><br /> <span data-ttu-id="6403e-123">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="6403e-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="6403e-124">**Lütfen bir şey girin.**</span><span class="sxs-lookup"><span data-stu-id="6403e-124">**Please enter something.**</span></span><br /><br /> `False`|

## <a name="writing-to-the-file"></a><span data-ttu-id="6403e-125">Dosyaya Yazma</span><span class="sxs-lookup"><span data-stu-id="6403e-125">Writing to the File</span></span>

<span data-ttu-id="6403e-126">Uygulama üzerinden bir dosyaya yazma özelliğini eklemek <xref:System.IO.StreamWriter> için sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="6403e-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="6403e-127"><xref:System.IO.StreamWriter>sınıf bayt giriş ve çıktı için tasarlanmış <xref:System.IO.Stream> ise, belirli bir kodlama karakter çıktısı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6403e-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="6403e-128">Standart <xref:System.IO.StreamWriter> bir metin dosyasına bilgi satırları yazmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="6403e-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="6403e-129"><xref:System.IO.StreamWriter> Sınıf hakkında daha fazla <xref:System.IO.StreamWriter>bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="6403e-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>

### <a name="to-add-writing-functionality"></a><span data-ttu-id="6403e-130">Yazma işlevselliği eklemek için</span><span class="sxs-lookup"><span data-stu-id="6403e-130">To add writing functionality</span></span>

1. <span data-ttu-id="6403e-131">**Görünüm** menüsünden Kod Düzenleyicisi'ni açmak için **Kod'u** seçin.</span><span class="sxs-lookup"><span data-stu-id="6403e-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>

2. <span data-ttu-id="6403e-132">Uygulama <xref:System.IO> ad alanına başvurulduğundan, başlayan `Public Class Form1`formun sınıf bildiriminden önce kodunuzun başında aşağıdaki ifadeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6403e-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     <span data-ttu-id="6403e-133">Dosyaya yazmadan önce bir <xref:System.IO.StreamWriter> sınıfın örneğini oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6403e-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>

3. <span data-ttu-id="6403e-134">**Görünüm** **menüsünden, Windows Forms Designer'a**dönmek için **Designer'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="6403e-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="6403e-135">Düğme için `Submit` olay <xref:System.Windows.Forms.Control.Click> işleyicisi oluşturmak için düğmeyi çift tıklatın ve ardından aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6403e-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> <span data-ttu-id="6403e-136">Visual Studio Entegre Geliştirme Ortamı (IDE) Kod Düzenleyicisi'ne geri döner ve ekleme noktasını kod eklemeniz gereken olay işleyicisi içinde konumlandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="6403e-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>

1. <span data-ttu-id="6403e-137">Dosyaya yazmak için sınıfın <xref:System.IO.StreamWriter.Write%2A> yöntemini <xref:System.IO.StreamWriter> kullanın.</span><span class="sxs-lookup"><span data-stu-id="6403e-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="6403e-138">Aşağıdaki kodu doğrudan `Dim fw As StreamWriter`sonra ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6403e-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="6403e-139">Dosya bulunmazsa bir özel durum atılacağından endişelenmenize gerek yoktur, çünkü dosya zaten yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6403e-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. <span data-ttu-id="6403e-140">Kullanıcının aşağıdaki kodu doğrudan sonra `Dim ReadString As String`ekleyerek boş bir giriş gönderemeyeceğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6403e-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. <span data-ttu-id="6403e-141">Bu bir günlük olduğundan, kullanıcı her girişe bir tarih atamak isteyecektir.</span><span class="sxs-lookup"><span data-stu-id="6403e-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="6403e-142">Değişkeni `Today` geçerli tarihe `fw = New StreamWriter("C:\MyDiary.txt", True)` ayarlamak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6403e-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. <span data-ttu-id="6403e-143">Son olarak, temizlemek <xref:System.Windows.Forms.TextBox>için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6403e-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="6403e-144">Düğmenin `Clear` <xref:System.Windows.Forms.Control.Click> olayına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6403e-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="6403e-145">Günlüğe Görüntü Özellikleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="6403e-145">Adding Display Features to the Diary</span></span>

<span data-ttu-id="6403e-146">Bu bölümde, `DisplayEntry` <xref:System.Windows.Forms.TextBox>en son girişi görüntüleyen bir özellik eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="6403e-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="6403e-147">Ayrıca, çeşitli <xref:System.Windows.Forms.ComboBox> girişleri görüntüleyen ve kullanıcının `DisplayEntry` <xref:System.Windows.Forms.TextBox>'de görüntülemek üzere bir giriş seçebileceği bir giriş de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6403e-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="6403e-148"><xref:System.IO.StreamReader> Sınıfın bir örneği `MyDiary.txt`.</span><span class="sxs-lookup"><span data-stu-id="6403e-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="6403e-149"><xref:System.IO.StreamWriter> Sınıf gibi, <xref:System.IO.StreamReader> metin dosyaları ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6403e-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>

<span data-ttu-id="6403e-150">İzlenin bu bölümü için, aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6403e-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="6403e-151">Denetim</span><span class="sxs-lookup"><span data-stu-id="6403e-151">Control</span></span>|<span data-ttu-id="6403e-152">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6403e-152">Properties</span></span>|<span data-ttu-id="6403e-153">Değerler</span><span class="sxs-lookup"><span data-stu-id="6403e-153">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="6403e-154">**Adı**</span><span class="sxs-lookup"><span data-stu-id="6403e-154">**Name**</span></span><br /><br /> <span data-ttu-id="6403e-155">**Visible**</span><span class="sxs-lookup"><span data-stu-id="6403e-155">**Visible**</span></span><br /><br /> <span data-ttu-id="6403e-156">**Boyut**</span><span class="sxs-lookup"><span data-stu-id="6403e-156">**Size**</span></span><br /><br /> <span data-ttu-id="6403e-157">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="6403e-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="6403e-158">**Adı**</span><span class="sxs-lookup"><span data-stu-id="6403e-158">**Name**</span></span><br /><br /> <span data-ttu-id="6403e-159">**Metin**</span><span class="sxs-lookup"><span data-stu-id="6403e-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="6403e-160">**Görüntüleme**</span><span class="sxs-lookup"><span data-stu-id="6403e-160">**Display**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="6403e-161">**Adı**</span><span class="sxs-lookup"><span data-stu-id="6403e-161">**Name**</span></span><br /><br /> <span data-ttu-id="6403e-162">**Metin**</span><span class="sxs-lookup"><span data-stu-id="6403e-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="6403e-163">**Girişleri Al**</span><span class="sxs-lookup"><span data-stu-id="6403e-163">**Get Entries**</span></span>|
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="6403e-164">**Adı**</span><span class="sxs-lookup"><span data-stu-id="6403e-164">**Name**</span></span><br /><br /> <span data-ttu-id="6403e-165">**Metin**</span><span class="sxs-lookup"><span data-stu-id="6403e-165">**Text**</span></span><br /><br /> <span data-ttu-id="6403e-166">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="6403e-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="6403e-167">**Giriş Seçin**</span><span class="sxs-lookup"><span data-stu-id="6403e-167">**Select an Entry**</span></span><br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a><span data-ttu-id="6403e-168">Açılan kutuyu doldurmak için</span><span class="sxs-lookup"><span data-stu-id="6403e-168">To populate the combo box</span></span>

1. <span data-ttu-id="6403e-169">Kullanıcının `PickEntries` <xref:System.Windows.Forms.ComboBox> her girişi gönderdiği tarihleri görüntülemek için kullanılır, böylece kullanıcı belirli bir tarihten bir giriş seçebilir.</span><span class="sxs-lookup"><span data-stu-id="6403e-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="6403e-170">Düğmeye <xref:System.Windows.Forms.Control.Click> bir olay işleyicisi `GetEntries` oluşturun ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6403e-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. <span data-ttu-id="6403e-171">Kodunuzu test etmek için uygulamayı derlemek için F5 tuşuna basın ve ardından **Girişleri Al'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6403e-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="6403e-172">Giriş tarihlerini görüntülemek <xref:System.Windows.Forms.ComboBox> için açılır oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6403e-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>

### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="6403e-173">Tek tek girişleri seçmek ve görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="6403e-173">To choose and display individual entries</span></span>

1. <span data-ttu-id="6403e-174">Düğme <xref:System.Windows.Forms.Control.Click> için bir olay `Display` işleyicisi oluşturun ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6403e-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. <span data-ttu-id="6403e-175">Kodunuzu test etmek için, uygulamayı derlemek için F5 tuşuna basın ve ardından bir giriş gönderin.</span><span class="sxs-lookup"><span data-stu-id="6403e-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="6403e-176">**Girişleri Al'ı**tıklatın, <xref:System.Windows.Forms.ComboBox>giriş seçin ve ardından **Görüntüle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6403e-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="6403e-177">Seçili girişin `DisplayEntry` <xref:System.Windows.Forms.TextBox>içeriği .</span><span class="sxs-lookup"><span data-stu-id="6403e-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="6403e-178">Kullanıcıların Girişleri Silmesini veya Değiştirmesini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="6403e-178">Enabling Users to Delete or Modify Entries</span></span>

<span data-ttu-id="6403e-179">Son olarak, kullanıcıların kullanarak ve `DeleteEntry` `EditEntry` düğmeleri kullanarak bir girişi silmesine veya değiştirmesine olanak tanıyan ek işlevler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6403e-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="6403e-180">Giriş görüntülenmedikçe her iki düğme de devre dışı kalır.</span><span class="sxs-lookup"><span data-stu-id="6403e-180">Both buttons remain disabled unless an entry is displayed.</span></span>

<span data-ttu-id="6403e-181">Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6403e-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="6403e-182">Denetim</span><span class="sxs-lookup"><span data-stu-id="6403e-182">Control</span></span>|<span data-ttu-id="6403e-183">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6403e-183">Properties</span></span>|<span data-ttu-id="6403e-184">Değerler</span><span class="sxs-lookup"><span data-stu-id="6403e-184">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="6403e-185">**Adı**</span><span class="sxs-lookup"><span data-stu-id="6403e-185">**Name**</span></span><br /><br /> <span data-ttu-id="6403e-186">**Metin**</span><span class="sxs-lookup"><span data-stu-id="6403e-186">**Text**</span></span><br /><br /> <span data-ttu-id="6403e-187">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="6403e-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="6403e-188">**Girişi Sil**</span><span class="sxs-lookup"><span data-stu-id="6403e-188">**Delete Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="6403e-189">**Adı**</span><span class="sxs-lookup"><span data-stu-id="6403e-189">**Name**</span></span><br /><br /> <span data-ttu-id="6403e-190">**Metin**</span><span class="sxs-lookup"><span data-stu-id="6403e-190">**Text**</span></span><br /><br /> <span data-ttu-id="6403e-191">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="6403e-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="6403e-192">**Girişi Edit**</span><span class="sxs-lookup"><span data-stu-id="6403e-192">**Edit Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="6403e-193">**Adı**</span><span class="sxs-lookup"><span data-stu-id="6403e-193">**Name**</span></span><br /><br /> <span data-ttu-id="6403e-194">**Metin**</span><span class="sxs-lookup"><span data-stu-id="6403e-194">**Text**</span></span><br /><br /> <span data-ttu-id="6403e-195">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="6403e-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="6403e-196">**Edit Gönder**</span><span class="sxs-lookup"><span data-stu-id="6403e-196">**Submit Edit**</span></span><br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="6403e-197">Girişlerin silinmesini ve değiştirilmesini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="6403e-197">To enable deletion and modification of entries</span></span>

1. <span data-ttu-id="6403e-198">Aşağıdaki kodu düğmenin `Display` <xref:System.Windows.Forms.Control.Click> olayına ekleyin, `DisplayEntry.Text = ReadString`sonra .</span><span class="sxs-lookup"><span data-stu-id="6403e-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. <span data-ttu-id="6403e-199">Düğme <xref:System.Windows.Forms.Control.Click> için bir olay `DeleteEntry` işleyicisi oluşturun ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6403e-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. <span data-ttu-id="6403e-200">Bir kullanıcı bir giriş `EditEntry` görüntülediğinde, düğme etkin olur.</span><span class="sxs-lookup"><span data-stu-id="6403e-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="6403e-201">'den sonra <xref:System.Windows.Forms.Control.Click> `Display` `DisplayEntry.Text = ReadString`düğmeye aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6403e-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. <span data-ttu-id="6403e-202">Düğme <xref:System.Windows.Forms.Control.Click> için bir olay `EditEntry` işleyicisi oluşturun ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6403e-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. <span data-ttu-id="6403e-203">Düğme <xref:System.Windows.Forms.Control.Click> için bir olay `SubmitEdit` işleyicisi oluşturun ve aşağıdaki kodu ekleyin</span><span class="sxs-lookup"><span data-stu-id="6403e-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

<span data-ttu-id="6403e-204">Kodunuzu test etmek için uygulamayı derlemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6403e-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="6403e-205">**Girişleri Al'ı**tıklatın, bir giriş seçin ve ardından **Görüntüle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6403e-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="6403e-206">Giriş. `DisplayEntry` <xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="6403e-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="6403e-207">**Girişi Edit'i**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6403e-207">Click **Edit Entry**.</span></span> <span data-ttu-id="6403e-208">Giriş. `Entry` <xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="6403e-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="6403e-209">Girişi `Entry` <xref:System.Windows.Forms.TextBox> edin ve **Edit'i gönder'e**tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6403e-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="6403e-210">Düzeltmenizi `MyDiary.txt` onaylamak için dosyayı açın.</span><span class="sxs-lookup"><span data-stu-id="6403e-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="6403e-211">Şimdi bir giriş seçin ve **Girişi Sil'i**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6403e-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="6403e-212">İstekte <xref:System.Windows.Forms.MessageBox> onay, **Tamam'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6403e-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="6403e-213">Uygulamayı kapatın ve `MyDiary.txt` silme işlemini onaylamak için açın.</span><span class="sxs-lookup"><span data-stu-id="6403e-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>

## <a name="see-also"></a><span data-ttu-id="6403e-214">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6403e-214">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="6403e-215">Kılavuz</span><span class="sxs-lookup"><span data-stu-id="6403e-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)
