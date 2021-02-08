---
description: 'Daha fazla bilgi edinin: Izlenecek yol: .NET Framework yöntemleri kullanarak dosyaları düzenleme (Visual Basic)'
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
ms.openlocfilehash: e59dca15660a981c487688234c864a818398af65
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775376"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="1a9dc-103">İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a9dc-103">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>

<span data-ttu-id="1a9dc-104">Bu izlenecek yol, sınıfını kullanarak bir dosyayı nasıl açıp okuyacağınızı <xref:System.IO.StreamReader> , bir dosyaya erişilmekte olup olmadığını kontrol etmek için, sınıfın örneğiyle okunan bir dosya içinde bir dizeyi aramak <xref:System.IO.StreamReader> ve sınıfını kullanarak bir dosyaya yazmak için nasıl kullanılacağını gösterir <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-104">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a><span data-ttu-id="1a9dc-105">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a9dc-105">Creating the Application</span></span>

<span data-ttu-id="1a9dc-106">Visual Studio 'Yu başlatın ve kullanıcının belirlenen dosyaya yazmak için kullanabileceği bir form oluşturarak projeye başlayın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-106">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="1a9dc-107">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1a9dc-107">To create the project</span></span>

1. <span data-ttu-id="1a9dc-108">**Dosya** menüsünde **Yeni proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-108">On the **File** menu, select **New Project**.</span></span>

2. <span data-ttu-id="1a9dc-109">**Yeni proje** bölmesinde **Windows uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-109">In the **New Project** pane, click **Windows Application**.</span></span>

3. <span data-ttu-id="1a9dc-110">**Ad** kutusuna yazın `MyDiary` ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-110">In the **Name** box type `MyDiary` and click **OK**.</span></span>

     <span data-ttu-id="1a9dc-111">Visual Studio, projeyi **Çözüm Gezgini** ekler ve **Windows Form Tasarımcısı** açılır.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-111">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>

4. <span data-ttu-id="1a9dc-112">Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-112">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="1a9dc-113">**Nesne**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-113">**Object**</span></span>|<span data-ttu-id="1a9dc-114">**Özellikler**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-114">**Properties**</span></span>|<span data-ttu-id="1a9dc-115">**Değer**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-115">**Value**</span></span>|
|---|---|---|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="1a9dc-116">**Ad**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-116">**Name**</span></span><br /><br /> <span data-ttu-id="1a9dc-117">**Metin**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-117">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="1a9dc-118">**Giriş Gönder**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-118">**Submit Entry**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="1a9dc-119">**Ad**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-119">**Name**</span></span><br /><br /> <span data-ttu-id="1a9dc-120">**Metin**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-120">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="1a9dc-121">**Girişi temizle**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-121">**Clear Entry**</span></span>|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="1a9dc-122">**Ad**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-122">**Name**</span></span><br /><br /> <span data-ttu-id="1a9dc-123">**Metin**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-123">**Text**</span></span><br /><br /> <span data-ttu-id="1a9dc-124">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-124">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="1a9dc-125">**Lütfen bir ad girin.**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-125">**Please enter something.**</span></span><br /><br /> `False`|

## <a name="writing-to-the-file"></a><span data-ttu-id="1a9dc-126">Dosyaya yazma</span><span class="sxs-lookup"><span data-stu-id="1a9dc-126">Writing to the File</span></span>

<span data-ttu-id="1a9dc-127">Uygulama aracılığıyla bir dosyaya yazma yeteneğini eklemek için <xref:System.IO.StreamWriter> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-127">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="1a9dc-128"><xref:System.IO.StreamWriter> , belirli bir kodlamada karakter çıkışı için tasarlanmıştır, ancak <xref:System.IO.Stream> Sınıf bayt girişi ve çıkışı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-128"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="1a9dc-129"><xref:System.IO.StreamWriter>Standart metin dosyasına bilgi satırları yazmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-129">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="1a9dc-130">Sınıfı hakkında daha fazla bilgi için <xref:System.IO.StreamWriter> bkz <xref:System.IO.StreamWriter> ..</span><span class="sxs-lookup"><span data-stu-id="1a9dc-130">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>

### <a name="to-add-writing-functionality"></a><span data-ttu-id="1a9dc-131">Yazma işlevselliği eklemek için</span><span class="sxs-lookup"><span data-stu-id="1a9dc-131">To add writing functionality</span></span>

1. <span data-ttu-id="1a9dc-132">**Görünüm** menüsünde **kod** ' yi seçerek kod düzenleyicisini açın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-132">From the **View** menu, choose **Code** to open the Code Editor.</span></span>

2. <span data-ttu-id="1a9dc-133">Uygulama ad alanına başvurduğundan, <xref:System.IO> form için Sınıf bildiriminden önce, ' nin başladığı, kodunuzun en başına aşağıdaki deyimlerini ekleyin `Public Class Form1` .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-133">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     <span data-ttu-id="1a9dc-134">Dosyaya yazmadan önce bir sınıfın örneğini oluşturmanız gerekir <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-134">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>

3. <span data-ttu-id="1a9dc-135">**Görünüm** menüsünden, **Windows Form Tasarımcısı** geri dönmek için **Tasarımcı** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-135">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="1a9dc-136">Düğmeye çift tıklayarak `Submit` <xref:System.Windows.Forms.Control.Click> düğme için bir olay işleyicisi oluşturun ve ardından aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-136">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> <span data-ttu-id="1a9dc-137">Visual Studio tümleşik geliştirme ortamı (IDE), kod düzenleyicisine dönerek ekleme noktasını kodu eklemeniz gereken olay işleyicisine göre konumlandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-137">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>

1. <span data-ttu-id="1a9dc-138">Dosyaya yazmak için, <xref:System.IO.StreamWriter.Write%2A> sınıfının yöntemini kullanın <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-138">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="1a9dc-139">Hemen sonra aşağıdaki kodu ekleyin `Dim fw As StreamWriter` .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-139">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="1a9dc-140">Zaten mevcut değilse oluşturulacak bir özel durumun, dosyanın bulunamaması durumunda oluşturulmadığından endişelenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-140">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. <span data-ttu-id="1a9dc-141">Kullanıcının aşağıdaki kodu doğrudan ekleyerek boş bir giriş gönderebildiğinden emin olun `Dim ReadString As String` .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-141">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. <span data-ttu-id="1a9dc-142">Bu bir Diary olduğundan, Kullanıcı her girişe bir tarih atamak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-142">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="1a9dc-143">`fw = New StreamWriter("C:\MyDiary.txt", True)`Değişkeni geçerli tarihe ayarlamak için aşağıdaki kodu ekleyin `Today` .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-143">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. <span data-ttu-id="1a9dc-144">Son olarak, silmek için kod ekleyin <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-144">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="1a9dc-145">Düğmenin olayına aşağıdaki kodu ekleyin `Clear` <xref:System.Windows.Forms.Control.Click> .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-145">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="1a9dc-146">Diary 'e görüntüleme özellikleri ekleme</span><span class="sxs-lookup"><span data-stu-id="1a9dc-146">Adding Display Features to the Diary</span></span>

<span data-ttu-id="1a9dc-147">Bu bölümde, içinde en son girişi görüntüleyen bir özellik eklersiniz `DisplayEntry` <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-147">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="1a9dc-148">Ayrıca <xref:System.Windows.Forms.ComboBox> , çeşitli girdileri görüntüleyen ve bir kullanıcının içinde görüntülenecek girişi seçebileceğiniz bir de ekleyebilirsiniz `DisplayEntry` <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-148">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="1a9dc-149">Sınıfının bir örneği <xref:System.IO.StreamReader> öğesinden okur `MyDiary.txt` .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-149">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="1a9dc-150">Sınıfı gibi <xref:System.IO.StreamWriter> , <xref:System.IO.StreamReader> metin dosyalarıyla kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-150">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>

<span data-ttu-id="1a9dc-151">İzlenecek yolun bu bölümü için, aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-151">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="1a9dc-152">Denetim</span><span class="sxs-lookup"><span data-stu-id="1a9dc-152">Control</span></span>|<span data-ttu-id="1a9dc-153">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1a9dc-153">Properties</span></span>|<span data-ttu-id="1a9dc-154">Değerler</span><span class="sxs-lookup"><span data-stu-id="1a9dc-154">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="1a9dc-155">**Ad**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-155">**Name**</span></span><br /><br /> <span data-ttu-id="1a9dc-156">**Görünür**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-156">**Visible**</span></span><br /><br /> <span data-ttu-id="1a9dc-157">**Boyut**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-157">**Size**</span></span><br /><br /> <span data-ttu-id="1a9dc-158">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-158">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="1a9dc-159">**Ad**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-159">**Name**</span></span><br /><br /> <span data-ttu-id="1a9dc-160">**Metin**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-160">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="1a9dc-161">**Görüntüleme**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-161">**Display**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="1a9dc-162">**Ad**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-162">**Name**</span></span><br /><br /> <span data-ttu-id="1a9dc-163">**Metin**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-163">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="1a9dc-164">**Girişleri Al**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-164">**Get Entries**</span></span>|
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="1a9dc-165">**Ad**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-165">**Name**</span></span><br /><br /> <span data-ttu-id="1a9dc-166">**Metin**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-166">**Text**</span></span><br /><br /> <span data-ttu-id="1a9dc-167">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-167">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="1a9dc-168">**Bir giriş seçin**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-168">**Select an Entry**</span></span><br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a><span data-ttu-id="1a9dc-169">Birleşik giriş kutusunu doldurmak için</span><span class="sxs-lookup"><span data-stu-id="1a9dc-169">To populate the combo box</span></span>

1. <span data-ttu-id="1a9dc-170">, Kullanıcının `PickEntries` <xref:System.Windows.Forms.ComboBox> her girişi gönderdiği tarihleri göstermek için kullanılır, böylece Kullanıcı belirli bir tarihten itibaren bir giriş seçebilir.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-170">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="1a9dc-171">Düğmeye bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun `GetEntries` ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-171">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. <span data-ttu-id="1a9dc-172">Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin ve ardından **Girişleri Al**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-172">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="1a9dc-173">Giriş tarihlerini göstermek için içindeki açılan oka tıklayın <xref:System.Windows.Forms.ComboBox> .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-173">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>

### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="1a9dc-174">Tek tek girdileri seçme ve görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1a9dc-174">To choose and display individual entries</span></span>

1. <span data-ttu-id="1a9dc-175"><xref:System.Windows.Forms.Control.Click>Düğme için bir olay işleyicisi oluşturun `Display` ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-175">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. <span data-ttu-id="1a9dc-176">Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin ve ardından bir giriş gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-176">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="1a9dc-177">**Girişleri Al**' a tıklayın, öğesinden bir giriş seçin <xref:System.Windows.Forms.ComboBox> ve ardından **görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-177">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="1a9dc-178">Seçili girdinin içeriği içinde görüntülenir `DisplayEntry` <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-178">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="1a9dc-179">Kullanıcıların girdileri silmesini veya değiştirmesini sağlama</span><span class="sxs-lookup"><span data-stu-id="1a9dc-179">Enabling Users to Delete or Modify Entries</span></span>

<span data-ttu-id="1a9dc-180">Son olarak, kullanıcıların ve düğmelerini kullanarak bir girişi silmesine veya değiştirmesine izin vermek için ek işlevler `DeleteEntry` ekleyebilirsiniz `EditEntry` .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-180">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="1a9dc-181">Bir giriş görüntülenmediği takdirde her iki düğme de devre dışı kalır.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-181">Both buttons remain disabled unless an entry is displayed.</span></span>

<span data-ttu-id="1a9dc-182">Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-182">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="1a9dc-183">Denetim</span><span class="sxs-lookup"><span data-stu-id="1a9dc-183">Control</span></span>|<span data-ttu-id="1a9dc-184">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1a9dc-184">Properties</span></span>|<span data-ttu-id="1a9dc-185">Değerler</span><span class="sxs-lookup"><span data-stu-id="1a9dc-185">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="1a9dc-186">**Ad**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-186">**Name**</span></span><br /><br /> <span data-ttu-id="1a9dc-187">**Metin**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-187">**Text**</span></span><br /><br /> <span data-ttu-id="1a9dc-188">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-188">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="1a9dc-189">**Girişi Sil**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-189">**Delete Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="1a9dc-190">**Ad**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-190">**Name**</span></span><br /><br /> <span data-ttu-id="1a9dc-191">**Metin**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-191">**Text**</span></span><br /><br /> <span data-ttu-id="1a9dc-192">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-192">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="1a9dc-193">**Girişi Düzenle**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-193">**Edit Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="1a9dc-194">**Ad**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-194">**Name**</span></span><br /><br /> <span data-ttu-id="1a9dc-195">**Metin**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-195">**Text**</span></span><br /><br /> <span data-ttu-id="1a9dc-196">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-196">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="1a9dc-197">**Düzenleme gönder**</span><span class="sxs-lookup"><span data-stu-id="1a9dc-197">**Submit Edit**</span></span><br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="1a9dc-198">Girişlerin silinmesini ve değiştirilmesini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="1a9dc-198">To enable deletion and modification of entries</span></span>

1. <span data-ttu-id="1a9dc-199">Aşağıdaki kodu `Display` düğmenin <xref:System.Windows.Forms.Control.Click> olayına, sonrasında ekleyin `DisplayEntry.Text = ReadString` .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-199">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. <span data-ttu-id="1a9dc-200"><xref:System.Windows.Forms.Control.Click>Düğme için bir olay işleyicisi oluşturun `DeleteEntry` ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-200">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. <span data-ttu-id="1a9dc-201">Bir Kullanıcı bir girişi görüntülediğinde, `EditEntry` düğme etkin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-201">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="1a9dc-202">Sonrasında düğme olayına aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> `Display` `DisplayEntry.Text = ReadString` .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-202">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. <span data-ttu-id="1a9dc-203"><xref:System.Windows.Forms.Control.Click>Düğme için bir olay işleyicisi oluşturun `EditEntry` ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. <span data-ttu-id="1a9dc-204"><xref:System.Windows.Forms.Control.Click>Düğme için bir olay işleyicisi oluşturun `SubmitEdit` ve aşağıdaki kodu ekleyin</span><span class="sxs-lookup"><span data-stu-id="1a9dc-204">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

<span data-ttu-id="1a9dc-205">Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-205">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="1a9dc-206">**Girişleri Al**' a tıklayın, bir giriş seçin ve ardından **görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-206">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="1a9dc-207">Giriş öğesinde görüntülenir `DisplayEntry` <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-207">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="1a9dc-208">**Girişi Düzenle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-208">Click **Edit Entry**.</span></span> <span data-ttu-id="1a9dc-209">Giriş öğesinde görüntülenir `Entry` <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="1a9dc-209">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="1a9dc-210">İçindeki girişi düzenleyin `Entry` <xref:System.Windows.Forms.TextBox> ve **düzenleme gönder**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-210">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="1a9dc-211">`MyDiary.txt`Düzeltmeyi onaylamak için dosyayı açın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-211">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="1a9dc-212">Şimdi bir girdi seçip **girişi Sil**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-212">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="1a9dc-213"><xref:System.Windows.Forms.MessageBox>İstek onayı tamamlandığında **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-213">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="1a9dc-214">Uygulamayı kapatın ve `MyDiary.txt` silme işlemini onaylamak için açın.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-214">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a9dc-215">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a9dc-215">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="1a9dc-216">İzlenecek Yollar</span><span class="sxs-lookup"><span data-stu-id="1a9dc-216">Walkthroughs</span></span>](../../../walkthroughs.md)
