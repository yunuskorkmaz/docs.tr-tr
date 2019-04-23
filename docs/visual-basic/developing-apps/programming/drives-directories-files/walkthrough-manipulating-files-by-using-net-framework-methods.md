---
title: .NET Framework yöntemleri (Visual Basic) kullanarak dosyaları düzenleme
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
ms.openlocfilehash: f3fecf521ca4a9397bacffbb084c4107af97f5b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345280"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="c9d3f-102">İzlenecek yol: .NET Framework yöntemleri (Visual Basic) kullanarak dosyaları düzenleme</span><span class="sxs-lookup"><span data-stu-id="c9d3f-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>
<span data-ttu-id="c9d3f-103">Bu izlenecek yol, açın ve kullanarak bir dosyayı okumak gösterilmiştir <xref:System.IO.StreamReader> sınıfı, bir dosya erişilebilir olmadığını kontrol edin, bir dize örneği ile okuma dosya içindeki arama <xref:System.IO.StreamReader> sınıfı ve kullanarak bir dosyaya yazma <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-application"></a><span data-ttu-id="c9d3f-104">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="c9d3f-104">Creating the Application</span></span>  
 <span data-ttu-id="c9d3f-105">Visual Studio'yu başlatın ve proje kullanıcı belirtilen dosyaya yazmak için kullanabileceğiniz bir form oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="c9d3f-106">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c9d3f-106">To create the project</span></span>  
  
1. <span data-ttu-id="c9d3f-107">Üzerinde **dosya** menüsünde **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-107">On the **File** menu, select **New Project**.</span></span>  
  
2. <span data-ttu-id="c9d3f-108">İçinde **yeni proje** bölmesinde tıklayın **Windows uygulama**.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-108">In the **New Project** pane, click **Windows Application**.</span></span>  
  
3. <span data-ttu-id="c9d3f-109">İçinde **adı** kutusuna `MyDiary` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>  
  
     <span data-ttu-id="c9d3f-110">Visual Studio projeyi ekler **Çözüm Gezgini**ve **Windows Form Tasarımcısı** açılır.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>  
  
4. <span data-ttu-id="c9d3f-111">Denetimler aşağıdaki tabloda forma ekleyin ve karşılık gelen özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="c9d3f-112">**Nesne**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-112">**Object**</span></span>|<span data-ttu-id="c9d3f-113">**Özellikler**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-113">**Properties**</span></span>|<span data-ttu-id="c9d3f-114">**Değer**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-114">**Value**</span></span>|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="c9d3f-115">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-115">**Name**</span></span><br /><br /> <span data-ttu-id="c9d3f-116">**Metin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="c9d3f-117">**Giriş başvurunuzu**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-117">**Submit Entry**</span></span>|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="c9d3f-118">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-118">**Name**</span></span><br /><br /> <span data-ttu-id="c9d3f-119">**Metin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="c9d3f-120">**Girişi Temizle**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-120">**Clear Entry**</span></span>|  
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="c9d3f-121">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-121">**Name**</span></span><br /><br /> <span data-ttu-id="c9d3f-122">**Metin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-122">**Text**</span></span><br /><br /> <span data-ttu-id="c9d3f-123">**Çok satırlı**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="c9d3f-124">**Lütfen bir şey girin.**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-124">**Please enter something.**</span></span><br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a><span data-ttu-id="c9d3f-125">Dosyaya yazma</span><span class="sxs-lookup"><span data-stu-id="c9d3f-125">Writing to the File</span></span>  
 <span data-ttu-id="c9d3f-126">Uygulama yoluyla bir dosyaya yazma olanağı eklemek için <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="c9d3f-127"><xref:System.IO.StreamWriter> belirli bir kodlamaya, karakter çıkışını ise tasarlanmıştır <xref:System.IO.Stream> sınıfı giriş ve çıkış baytı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="c9d3f-128">Kullanım <xref:System.IO.StreamWriter> satır bilgi standart bir metin dosyasına yazma.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="c9d3f-129">Daha fazla bilgi için <xref:System.IO.StreamWriter> sınıfı <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>  
  
#### <a name="to-add-writing-functionality"></a><span data-ttu-id="c9d3f-130">Yazma işlevselliği eklemek için</span><span class="sxs-lookup"><span data-stu-id="c9d3f-130">To add writing functionality</span></span>  
  
1. <span data-ttu-id="c9d3f-131">Gelen **görünümü** menüsünde seçin **kod** Kod Düzenleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>  
  
2. <span data-ttu-id="c9d3f-132">Uygulama başvurduğundan <xref:System.IO> ad alanı, kodunuzu çok başında aşağıdaki deyimleri ekleyin, formu için sınıf bildiriminden önce başlar `Public Class Form1`.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]  
  
     <span data-ttu-id="c9d3f-133">Dosyaya yazmadan önce bir örneğini oluşturmanız gerekir bir <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>  
  
3. <span data-ttu-id="c9d3f-134">Gelen **görünümü** menüsünde seçin **Tasarımcısı** dönmek için **Windows Form Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="c9d3f-135">Çift `Submit` oluşturmak için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi, düğmenin ve ardından aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]  
  
> [!NOTE]
>  <span data-ttu-id="c9d3f-136">Visual Studio tümleşik geliştirme ortamı (IDE), Kod Düzenleyicisi'ne dönmek ve burada kodu buraya eklemelisiniz içinde olay işleyicisi ekleme noktasını yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>  
  
1. <span data-ttu-id="c9d3f-137">Dosyaya yazmak için kullanın <xref:System.IO.StreamWriter.Write%2A> yöntemi <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="c9d3f-138">Hemen sonra aşağıdaki kodu ekleyin `Dim fw As StreamWriter`.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="c9d3f-139">Dosya bulunamazsa, zaten yoksa, oluşturulur çünkü bir özel durum oluşturulur, endişelenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]  
  
2. <span data-ttu-id="c9d3f-140">Hemen sonra aşağıdaki kodu ekleyerek kullanıcı boş bir girdiyi gönderemiyor emin `Dim ReadString As String`.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]  
  
3. <span data-ttu-id="c9d3f-141">Bu bir günlük olduğundan, kullanıcının her giriş için bir tarih atamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="c9d3f-142">Sonra aşağıdaki kodu ekleyin `fw = New StreamWriter("C:\MyDiary.txt", True)` değişkenini ayarlamak üzere `Today` geçerli tarih.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]  
  
4. <span data-ttu-id="c9d3f-143">Son olarak, temizlemek için kod ekleme <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="c9d3f-144">Aşağıdaki kodu ekleyin `Clear` düğmenin <xref:System.Windows.Forms.Control.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]  
  
## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="c9d3f-145">Görüntü özellikleri için günlük ekleme</span><span class="sxs-lookup"><span data-stu-id="c9d3f-145">Adding Display Features to the Diary</span></span>  
 <span data-ttu-id="c9d3f-146">Bu bölümde, en son giriş görüntüleyen özellik ekleme `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="c9d3f-147">Ayrıca bir <xref:System.Windows.Forms.ComboBox> girdilerin görüntüleyen ve kendisinden kullanıcı görüntülemek için bir giriş seçebilirsiniz `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="c9d3f-148">Örneği <xref:System.IO.StreamReader> sınıfı okumalardan `MyDiary.txt`.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="c9d3f-149">Gibi <xref:System.IO.StreamWriter> sınıfı <xref:System.IO.StreamReader> metin dosyalarını kullanması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>  
  
 <span data-ttu-id="c9d3f-150">Bu bölümde örnekler için denetimleri aşağıdaki tabloda forma eklemek ve özelliklerine karşılık gelen değerlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="c9d3f-151">Denetim</span><span class="sxs-lookup"><span data-stu-id="c9d3f-151">Control</span></span>|<span data-ttu-id="c9d3f-152">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c9d3f-152">Properties</span></span>|<span data-ttu-id="c9d3f-153">Değerler</span><span class="sxs-lookup"><span data-stu-id="c9d3f-153">Values</span></span>|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="c9d3f-154">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-154">**Name**</span></span><br /><br /> <span data-ttu-id="c9d3f-155">**Görünür**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-155">**Visible**</span></span><br /><br /> <span data-ttu-id="c9d3f-156">**Boyutu**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-156">**Size**</span></span><br /><br /> <span data-ttu-id="c9d3f-157">**Çok satırlı**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="c9d3f-158">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-158">**Name**</span></span><br /><br /> <span data-ttu-id="c9d3f-159">**Metin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="c9d3f-160">**Görüntüleme**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-160">**Display**</span></span>|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="c9d3f-161">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-161">**Name**</span></span><br /><br /> <span data-ttu-id="c9d3f-162">**Metin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="c9d3f-163">**Girişlerini alma**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-163">**Get Entries**</span></span>|  
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="c9d3f-164">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-164">**Name**</span></span><br /><br /> <span data-ttu-id="c9d3f-165">**Metin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-165">**Text**</span></span><br /><br /> <span data-ttu-id="c9d3f-166">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="c9d3f-167">**Bir giriş seçin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-167">**Select an Entry**</span></span><br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a><span data-ttu-id="c9d3f-168">Birleşik giriş kutusunu doldurmak için</span><span class="sxs-lookup"><span data-stu-id="c9d3f-168">To populate the combo box</span></span>  
  
1. <span data-ttu-id="c9d3f-169">`PickEntries` <xref:System.Windows.Forms.ComboBox> Üzerinde bir kullanıcının gönderdiğini her girdi, kullanıcının belirli bir tarihten itibaren bir giriş seçebilmeniz tarihleri görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="c9d3f-170">Oluşturma bir <xref:System.Windows.Forms.Control.Click> olay işleyicisine `GetEntries` düğmesine tıklayın ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]  
  
2. <span data-ttu-id="c9d3f-171">Kodunuzu test etmek için uygulamayı derleyin ve ardından F5 tuşuna basarak **Girişleri Al**.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="c9d3f-172">Aşağı açılan oku tıklatın <xref:System.Windows.Forms.ComboBox> giriş tarihleri görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>  
  
#### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="c9d3f-173">Seçin ve girişler görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="c9d3f-173">To choose and display individual entries</span></span>  
  
1. <span data-ttu-id="c9d3f-174">Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisi `Display` düğmesine tıklayın ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]  
  
2. <span data-ttu-id="c9d3f-175">Kodunuzu test etmek için uygulamayı derlemek üzere F5 tuşuna basın ve sonra bir giriş gönderin.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="c9d3f-176">Tıklayın **Girişleri Al**, bir giriş seçin <xref:System.Windows.Forms.ComboBox>ve ardından **görünen**.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="c9d3f-177">Seçili girişi içeriğini görünür `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="c9d3f-178">Girişleri değiştirmek veya silmek kullanıcıları etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="c9d3f-178">Enabling Users to Delete or Modify Entries</span></span>  
 <span data-ttu-id="c9d3f-179">Son olarak, bir giriş kullanarak değiştirmek veya silmek için kullanıcıların ek işlevsellik sağlar içerebilir `DeleteEntry` ve `EditEntry` düğmeleri.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="c9d3f-180">Bir giriş görüntülenen sürece her iki düğme devre dışı kalır.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-180">Both buttons remain disabled unless an entry is displayed.</span></span>  
  
 <span data-ttu-id="c9d3f-181">Denetimler aşağıdaki tabloda forma ekleyin ve karşılık gelen özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="c9d3f-182">Denetim</span><span class="sxs-lookup"><span data-stu-id="c9d3f-182">Control</span></span>|<span data-ttu-id="c9d3f-183">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c9d3f-183">Properties</span></span>|<span data-ttu-id="c9d3f-184">Değerler</span><span class="sxs-lookup"><span data-stu-id="c9d3f-184">Values</span></span>|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="c9d3f-185">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-185">**Name**</span></span><br /><br /> <span data-ttu-id="c9d3f-186">**Metin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-186">**Text**</span></span><br /><br /> <span data-ttu-id="c9d3f-187">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="c9d3f-188">**Girişi Sil**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-188">**Delete Entry**</span></span><br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="c9d3f-189">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-189">**Name**</span></span><br /><br /> <span data-ttu-id="c9d3f-190">**Metin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-190">**Text**</span></span><br /><br /> <span data-ttu-id="c9d3f-191">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="c9d3f-192">**Girişi düzenlemek**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-192">**Edit Entry**</span></span><br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="c9d3f-193">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-193">**Name**</span></span><br /><br /> <span data-ttu-id="c9d3f-194">**Metin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-194">**Text**</span></span><br /><br /> <span data-ttu-id="c9d3f-195">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="c9d3f-196">**Düzenleme gönderin**</span><span class="sxs-lookup"><span data-stu-id="c9d3f-196">**Submit Edit**</span></span><br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="c9d3f-197">Silme ve girişleri değiştirilmesini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="c9d3f-197">To enable deletion and modification of entries</span></span>  
  
1. <span data-ttu-id="c9d3f-198">Aşağıdaki kodu ekleyin `Display` düğmenin <xref:System.Windows.Forms.Control.Click> olay, sonra `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]  
  
2. <span data-ttu-id="c9d3f-199">Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisi `DeleteEntry` düğmesine tıklayın ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]  
  
3. <span data-ttu-id="c9d3f-200">Bir kullanıcı bir giriş görüntülediğinde `EditEntry` düğmesi hale etkin.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="c9d3f-201">Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olayı `Display` sonra düğme `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]  
  
4. <span data-ttu-id="c9d3f-202">Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisi `EditEntry` düğmesine tıklayın ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]  
  
5. <span data-ttu-id="c9d3f-203">Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisi `SubmitEdit` düğmesine tıklayın ve aşağıdaki kodu ekleyin</span><span class="sxs-lookup"><span data-stu-id="c9d3f-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]  
  
 <span data-ttu-id="c9d3f-204">Kodunuzu test etmek için uygulamayı derlemek üzere F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="c9d3f-205">Tıklayın **Girişleri Al**bir girişi seçin ve ardından **görünen**.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="c9d3f-206">Giriş belirir `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="c9d3f-207">Tıklayın **Düzenle giriş**.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-207">Click **Edit Entry**.</span></span> <span data-ttu-id="c9d3f-208">Giriş belirir `Entry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="c9d3f-209">Girişi düzenlemek `Entry` <xref:System.Windows.Forms.TextBox> tıklatıp **gönderme Düzenle**.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="c9d3f-210">Açık `MyDiary.txt` düzeltmenizi onaylamak için dosya.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="c9d3f-211">Artık bir girişi seçin ve tıklayın **girdiyi Sil**.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="c9d3f-212">Zaman <xref:System.Windows.Forms.MessageBox> onay istekleri tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="c9d3f-213">Uygulamayı kapatın ve açın `MyDiary.txt` silme işlemini onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d3f-214">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9d3f-214">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="c9d3f-215">İzlenecek Yollar</span><span class="sxs-lookup"><span data-stu-id="c9d3f-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)
