---
title: .NET Framework yöntemleri kullanarak dosyaları düzenleme (Visual Basic)
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
ms.openlocfilehash: fc02b795834dba4a777dc78f4c8179238ac593af
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582491"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="53419-102">İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53419-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>

<span data-ttu-id="53419-103">Bu izlenecek yol, <xref:System.IO.StreamReader> sınıfını kullanarak bir dosyayı nasıl açıp okuyacağınızı, bir dosyaya erişilmekte olup olmadığını kontrol etmek için <xref:System.IO.StreamReader> sınıfının örneğiyle okunan bir dosya içinde bir dizeyi aramak ve <xref:System.IO.StreamWriter> sınıfını kullanarak bir dosyaya yazmak demektir.</span><span class="sxs-lookup"><span data-stu-id="53419-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a><span data-ttu-id="53419-104">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="53419-104">Creating the Application</span></span>

<span data-ttu-id="53419-105">Visual Studio 'Yu başlatın ve kullanıcının belirlenen dosyaya yazmak için kullanabileceği bir form oluşturarak projeye başlayın.</span><span class="sxs-lookup"><span data-stu-id="53419-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="53419-106">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="53419-106">To create the project</span></span>

1. <span data-ttu-id="53419-107">**Dosya** menüsünde **Yeni proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="53419-107">On the **File** menu, select **New Project**.</span></span>

2. <span data-ttu-id="53419-108">**Yeni proje** bölmesinde **Windows uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="53419-108">In the **New Project** pane, click **Windows Application**.</span></span>

3. <span data-ttu-id="53419-109">**Ad** kutusuna `MyDiary` yazın ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="53419-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>

     <span data-ttu-id="53419-110">Visual Studio, projeyi **Çözüm Gezgini**ekler ve **Windows Form Tasarımcısı** açılır.</span><span class="sxs-lookup"><span data-stu-id="53419-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>

4. <span data-ttu-id="53419-111">Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="53419-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="53419-112">**Nesne**</span><span class="sxs-lookup"><span data-stu-id="53419-112">**Object**</span></span>|<span data-ttu-id="53419-113">**Veri Erişimi**</span><span class="sxs-lookup"><span data-stu-id="53419-113">**Properties**</span></span>|<span data-ttu-id="53419-114">**Değer**</span><span class="sxs-lookup"><span data-stu-id="53419-114">**Value**</span></span>|
|---|---|---|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="53419-115">**Ad**</span><span class="sxs-lookup"><span data-stu-id="53419-115">**Name**</span></span><br /><br /> <span data-ttu-id="53419-116">**Metin**</span><span class="sxs-lookup"><span data-stu-id="53419-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="53419-117">**Giriş Gönder**</span><span class="sxs-lookup"><span data-stu-id="53419-117">**Submit Entry**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="53419-118">**Ad**</span><span class="sxs-lookup"><span data-stu-id="53419-118">**Name**</span></span><br /><br /> <span data-ttu-id="53419-119">**Metin**</span><span class="sxs-lookup"><span data-stu-id="53419-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="53419-120">**Girişi temizle**</span><span class="sxs-lookup"><span data-stu-id="53419-120">**Clear Entry**</span></span>|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="53419-121">**Ad**</span><span class="sxs-lookup"><span data-stu-id="53419-121">**Name**</span></span><br /><br /> <span data-ttu-id="53419-122">**Metin**</span><span class="sxs-lookup"><span data-stu-id="53419-122">**Text**</span></span><br /><br /> <span data-ttu-id="53419-123">**Çok satırlı**</span><span class="sxs-lookup"><span data-stu-id="53419-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="53419-124">**Lütfen bir ad girin.**</span><span class="sxs-lookup"><span data-stu-id="53419-124">**Please enter something.**</span></span><br /><br /> `False`|

## <a name="writing-to-the-file"></a><span data-ttu-id="53419-125">Dosyaya yazma</span><span class="sxs-lookup"><span data-stu-id="53419-125">Writing to the File</span></span>

<span data-ttu-id="53419-126">Uygulama aracılığıyla bir dosyaya yazma özelliğini eklemek için <xref:System.IO.StreamWriter> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="53419-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="53419-127"><xref:System.IO.StreamWriter>, belirli bir kodlamada karakter çıkışı için tasarlanmıştır, ancak <xref:System.IO.Stream> sınıfı bayt girişi ve çıkışı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="53419-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="53419-128">Bir standart metin dosyasına bilgi satırları yazmak için <xref:System.IO.StreamWriter> kullanın.</span><span class="sxs-lookup"><span data-stu-id="53419-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="53419-129">@No__t_0 sınıfı hakkında daha fazla bilgi için bkz. <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="53419-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>

### <a name="to-add-writing-functionality"></a><span data-ttu-id="53419-130">Yazma işlevselliği eklemek için</span><span class="sxs-lookup"><span data-stu-id="53419-130">To add writing functionality</span></span>

1. <span data-ttu-id="53419-131">**Görünüm** menüsünde **kod** ' yi seçerek kod düzenleyicisini açın.</span><span class="sxs-lookup"><span data-stu-id="53419-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>

2. <span data-ttu-id="53419-132">Uygulama <xref:System.IO> ad alanına başvurduğundan, form için Sınıf bildiriminden önce, `Public Class Form1` başlayan, kodunuzun en başına aşağıdaki deyimlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53419-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     <span data-ttu-id="53419-133">Dosyaya yazmadan önce <xref:System.IO.StreamWriter> sınıfının bir örneğini oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="53419-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>

3. <span data-ttu-id="53419-134">**Görünüm** menüsünden, **Windows Form Tasarımcısı**geri dönmek için **Tasarımcı** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="53419-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="53419-135">Düğme için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturmak üzere `Submit` düğmesine çift tıklayın ve ardından aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53419-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> <span data-ttu-id="53419-136">Visual Studio tümleşik geliştirme ortamı (IDE), kod düzenleyicisine dönerek ekleme noktasını kodu eklemeniz gereken olay işleyicisine göre konumlandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="53419-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>

1. <span data-ttu-id="53419-137">Dosyaya yazmak için <xref:System.IO.StreamWriter> sınıfının <xref:System.IO.StreamWriter.Write%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="53419-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="53419-138">@No__t_0 sonra doğrudan aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53419-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="53419-139">Zaten mevcut değilse oluşturulacak bir özel durumun, dosyanın bulunamaması durumunda oluşturulmadığından endişelenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="53419-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. <span data-ttu-id="53419-140">@No__t_0 hemen sonra aşağıdaki kodu ekleyerek kullanıcının boş bir giriş gönderebildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="53419-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. <span data-ttu-id="53419-141">Bu bir Diary olduğundan, Kullanıcı her girişe bir tarih atamak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="53419-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="53419-142">@No__t_0 sonra `Today` değişkeni geçerli tarihe ayarlamak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53419-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. <span data-ttu-id="53419-143">Son olarak, <xref:System.Windows.Forms.TextBox> temizlemek için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53419-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="53419-144">@No__t_0 düğmesinin <xref:System.Windows.Forms.Control.Click> olayına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53419-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="53419-145">Diary 'e görüntüleme özellikleri ekleme</span><span class="sxs-lookup"><span data-stu-id="53419-145">Adding Display Features to the Diary</span></span>

<span data-ttu-id="53419-146">Bu bölümde, `DisplayEntry` <xref:System.Windows.Forms.TextBox> en son girişi görüntüleyen bir özellik eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="53419-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="53419-147">Ayrıca, çeşitli girdileri görüntüleyen ve kullanıcının `DisplayEntry` <xref:System.Windows.Forms.TextBox> görüntülenecek girişi seçebileceğiniz bir <xref:System.Windows.Forms.ComboBox> ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53419-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="53419-148">@No__t_0 sınıfının bir örneği `MyDiary.txt` okur.</span><span class="sxs-lookup"><span data-stu-id="53419-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="53419-149">@No__t_0 sınıfı gibi, <xref:System.IO.StreamReader> metin dosyalarıyla kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="53419-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>

<span data-ttu-id="53419-150">İzlenecek yolun bu bölümü için, aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="53419-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="53419-151">Denetim</span><span class="sxs-lookup"><span data-stu-id="53419-151">Control</span></span>|<span data-ttu-id="53419-152">Özellikler</span><span class="sxs-lookup"><span data-stu-id="53419-152">Properties</span></span>|<span data-ttu-id="53419-153">Değerler</span><span class="sxs-lookup"><span data-stu-id="53419-153">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="53419-154">**Ad**</span><span class="sxs-lookup"><span data-stu-id="53419-154">**Name**</span></span><br /><br /> <span data-ttu-id="53419-155">**Görüne**</span><span class="sxs-lookup"><span data-stu-id="53419-155">**Visible**</span></span><br /><br /> <span data-ttu-id="53419-156">**Boyutla**</span><span class="sxs-lookup"><span data-stu-id="53419-156">**Size**</span></span><br /><br /> <span data-ttu-id="53419-157">**Çok satırlı**</span><span class="sxs-lookup"><span data-stu-id="53419-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="53419-158">**Ad**</span><span class="sxs-lookup"><span data-stu-id="53419-158">**Name**</span></span><br /><br /> <span data-ttu-id="53419-159">**Metin**</span><span class="sxs-lookup"><span data-stu-id="53419-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="53419-160">**Görüntülenme**</span><span class="sxs-lookup"><span data-stu-id="53419-160">**Display**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="53419-161">**Ad**</span><span class="sxs-lookup"><span data-stu-id="53419-161">**Name**</span></span><br /><br /> <span data-ttu-id="53419-162">**Metin**</span><span class="sxs-lookup"><span data-stu-id="53419-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="53419-163">**Girişleri Al**</span><span class="sxs-lookup"><span data-stu-id="53419-163">**Get Entries**</span></span>|
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="53419-164">**Ad**</span><span class="sxs-lookup"><span data-stu-id="53419-164">**Name**</span></span><br /><br /> <span data-ttu-id="53419-165">**Metin**</span><span class="sxs-lookup"><span data-stu-id="53419-165">**Text**</span></span><br /><br /> <span data-ttu-id="53419-166">**Etkinletir**</span><span class="sxs-lookup"><span data-stu-id="53419-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="53419-167">**Bir giriş seçin**</span><span class="sxs-lookup"><span data-stu-id="53419-167">**Select an Entry**</span></span><br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a><span data-ttu-id="53419-168">Birleşik giriş kutusunu doldurmak için</span><span class="sxs-lookup"><span data-stu-id="53419-168">To populate the combo box</span></span>

1. <span data-ttu-id="53419-169">@No__t_0 <xref:System.Windows.Forms.ComboBox>, kullanıcının her girişi gönderdiği tarihleri göstermek için kullanılır, böylece Kullanıcı belirli bir tarihten itibaren bir giriş seçebilir.</span><span class="sxs-lookup"><span data-stu-id="53419-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="53419-170">@No__t_1 düğmesine <xref:System.Windows.Forms.Control.Click> bir olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53419-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. <span data-ttu-id="53419-171">Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin ve ardından **Girişleri Al**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="53419-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="53419-172">Giriş tarihlerini göstermek için <xref:System.Windows.Forms.ComboBox> açılan oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="53419-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>

### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="53419-173">Tek tek girdileri seçme ve görüntüleme</span><span class="sxs-lookup"><span data-stu-id="53419-173">To choose and display individual entries</span></span>

1. <span data-ttu-id="53419-174">@No__t_1 düğmesi için <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53419-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. <span data-ttu-id="53419-175">Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin ve ardından bir giriş gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53419-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="53419-176">**Girişleri Al**' a tıklayın, <xref:System.Windows.Forms.ComboBox> bir giriş seçin ve ardından **görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="53419-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="53419-177">Seçili girdinin içeriği `DisplayEntry` <xref:System.Windows.Forms.TextBox> görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="53419-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="53419-178">Kullanıcıların girdileri silmesini veya değiştirmesini sağlama</span><span class="sxs-lookup"><span data-stu-id="53419-178">Enabling Users to Delete or Modify Entries</span></span>

<span data-ttu-id="53419-179">Son olarak, kullanıcıların `DeleteEntry` ve `EditEntry` düğmelerini kullanarak bir girişi silmesine veya değiştirmesine olanak tanıyan ek işlevler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53419-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="53419-180">Bir giriş görüntülenmediği takdirde her iki düğme de devre dışı kalır.</span><span class="sxs-lookup"><span data-stu-id="53419-180">Both buttons remain disabled unless an entry is displayed.</span></span>

<span data-ttu-id="53419-181">Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="53419-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="53419-182">Denetim</span><span class="sxs-lookup"><span data-stu-id="53419-182">Control</span></span>|<span data-ttu-id="53419-183">Özellikler</span><span class="sxs-lookup"><span data-stu-id="53419-183">Properties</span></span>|<span data-ttu-id="53419-184">Değerler</span><span class="sxs-lookup"><span data-stu-id="53419-184">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="53419-185">**Ad**</span><span class="sxs-lookup"><span data-stu-id="53419-185">**Name**</span></span><br /><br /> <span data-ttu-id="53419-186">**Metin**</span><span class="sxs-lookup"><span data-stu-id="53419-186">**Text**</span></span><br /><br /> <span data-ttu-id="53419-187">**Etkinletir**</span><span class="sxs-lookup"><span data-stu-id="53419-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="53419-188">**Girişi Sil**</span><span class="sxs-lookup"><span data-stu-id="53419-188">**Delete Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="53419-189">**Ad**</span><span class="sxs-lookup"><span data-stu-id="53419-189">**Name**</span></span><br /><br /> <span data-ttu-id="53419-190">**Metin**</span><span class="sxs-lookup"><span data-stu-id="53419-190">**Text**</span></span><br /><br /> <span data-ttu-id="53419-191">**Etkinletir**</span><span class="sxs-lookup"><span data-stu-id="53419-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="53419-192">**Girişi Düzenle**</span><span class="sxs-lookup"><span data-stu-id="53419-192">**Edit Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="53419-193">**Ad**</span><span class="sxs-lookup"><span data-stu-id="53419-193">**Name**</span></span><br /><br /> <span data-ttu-id="53419-194">**Metin**</span><span class="sxs-lookup"><span data-stu-id="53419-194">**Text**</span></span><br /><br /> <span data-ttu-id="53419-195">**Etkinletir**</span><span class="sxs-lookup"><span data-stu-id="53419-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="53419-196">**Düzenleme gönder**</span><span class="sxs-lookup"><span data-stu-id="53419-196">**Submit Edit**</span></span><br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="53419-197">Girişlerin silinmesini ve değiştirilmesini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="53419-197">To enable deletion and modification of entries</span></span>

1. <span data-ttu-id="53419-198">@No__t_0 düğmenin <xref:System.Windows.Forms.Control.Click> olayına, `DisplayEntry.Text = ReadString` sonra aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53419-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. <span data-ttu-id="53419-199">@No__t_1 düğmesi için <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53419-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. <span data-ttu-id="53419-200">Bir Kullanıcı bir girişi görüntülediğinde `EditEntry` düğmesi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="53419-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="53419-201">@No__t_2 sonra `Display` düğmesinin <xref:System.Windows.Forms.Control.Click> olayına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53419-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. <span data-ttu-id="53419-202">@No__t_1 düğmesi için <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53419-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. <span data-ttu-id="53419-203">@No__t_1 düğmesi için <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin</span><span class="sxs-lookup"><span data-stu-id="53419-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

<span data-ttu-id="53419-204">Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin.</span><span class="sxs-lookup"><span data-stu-id="53419-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="53419-205">**Girişleri Al**' a tıklayın, bir giriş seçin ve ardından **görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="53419-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="53419-206">Giriş `DisplayEntry` <xref:System.Windows.Forms.TextBox> görünür.</span><span class="sxs-lookup"><span data-stu-id="53419-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="53419-207">**Girişi Düzenle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="53419-207">Click **Edit Entry**.</span></span> <span data-ttu-id="53419-208">Giriş `Entry` <xref:System.Windows.Forms.TextBox> görünür.</span><span class="sxs-lookup"><span data-stu-id="53419-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="53419-209">@No__t_0 <xref:System.Windows.Forms.TextBox> girişi düzenleyin ve **Düzenle gönder**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="53419-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="53419-210">Düzeltinizi onaylamak için `MyDiary.txt` dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="53419-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="53419-211">Şimdi bir girdi seçip **girişi Sil**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="53419-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="53419-212">@No__t_0 onay istediğinde, **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="53419-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="53419-213">Uygulamayı kapatın ve silme işlemini onaylamak için `MyDiary.txt` açın.</span><span class="sxs-lookup"><span data-stu-id="53419-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>

## <a name="see-also"></a><span data-ttu-id="53419-214">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53419-214">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="53419-215">İzlenecek yollar</span><span class="sxs-lookup"><span data-stu-id="53419-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)
