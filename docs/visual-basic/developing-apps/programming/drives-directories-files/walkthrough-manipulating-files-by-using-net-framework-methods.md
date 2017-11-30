---
title: ".NET Framework yöntemlerini (Visual Basic) kullanarak dosyaları düzenleme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bc42dee640271ef84d35ceeb039d98741d296c5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="46690-102">İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46690-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>
<span data-ttu-id="46690-103">Bu izlenecek yol açabilir ve okuyabilir kullanarak bir dosyaya gösterilmiştir <xref:System.IO.StreamReader> sınıfı, bir dosyaya erişim olmadığını denetleyin, bir dize örneği ile okuma dosyasının içinde arama <xref:System.IO.StreamReader> sınıfı ve kullanarak bir dosyaya yazma <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="46690-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-application"></a><span data-ttu-id="46690-104">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="46690-104">Creating the Application</span></span>  
 <span data-ttu-id="46690-105">Başlat [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] ve projeyi kullanıcı için belirtilen dosya yazmak için kullanabileceğiniz bir form oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="46690-105">Start [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] and begin the project by creating a form that the user can use to write to the designated file.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="46690-106">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="46690-106">To create the project</span></span>  
  
1.  <span data-ttu-id="46690-107">Üzerinde **dosya** menüsünde, select **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="46690-107">On the **File** menu, select **New Project**.</span></span>  
  
2.  <span data-ttu-id="46690-108">İçinde **yeni proje** bölmesinde tıklatın **Windows uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="46690-108">In the **New Project** pane, click **Windows Application**.</span></span>  
  
3.  <span data-ttu-id="46690-109">İçinde **adı** kutusuna `MyDiary` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="46690-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>  
  
     [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="46690-110">projeye ekler **Çözüm Gezgini**ve **Windows Form Tasarımcısı** açar.</span><span class="sxs-lookup"><span data-stu-id="46690-110"> adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>  
  
4.  <span data-ttu-id="46690-111">Denetimleri aşağıdaki tabloda forma ekleme ve bunların özelliklerini karşılık gelen değerler ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="46690-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="46690-112">**Nesne**</span><span class="sxs-lookup"><span data-stu-id="46690-112">**Object**</span></span>|<span data-ttu-id="46690-113">**Veri Erişimi**</span><span class="sxs-lookup"><span data-stu-id="46690-113">**Properties**</span></span>|<span data-ttu-id="46690-114">**Değer**</span><span class="sxs-lookup"><span data-stu-id="46690-114">**Value**</span></span>|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="46690-115">**Ad**</span><span class="sxs-lookup"><span data-stu-id="46690-115">**Name**</span></span><br /><br /> <span data-ttu-id="46690-116">**Metin**</span><span class="sxs-lookup"><span data-stu-id="46690-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="46690-117">**Giriş gönderme**</span><span class="sxs-lookup"><span data-stu-id="46690-117">**Submit Entry**</span></span>|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="46690-118">**Ad**</span><span class="sxs-lookup"><span data-stu-id="46690-118">**Name**</span></span><br /><br /> <span data-ttu-id="46690-119">**Metin**</span><span class="sxs-lookup"><span data-stu-id="46690-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="46690-120">**Giriş temizleyin**</span><span class="sxs-lookup"><span data-stu-id="46690-120">**Clear Entry**</span></span>|  
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="46690-121">**Ad**</span><span class="sxs-lookup"><span data-stu-id="46690-121">**Name**</span></span><br /><br /> <span data-ttu-id="46690-122">**Metin**</span><span class="sxs-lookup"><span data-stu-id="46690-122">**Text**</span></span><br /><br /> <span data-ttu-id="46690-123">**Çok satırlı**</span><span class="sxs-lookup"><span data-stu-id="46690-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="46690-124">**Lütfen bir şey girin.**</span><span class="sxs-lookup"><span data-stu-id="46690-124">**Please enter something.**</span></span><br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a><span data-ttu-id="46690-125">Dosyaya yazma</span><span class="sxs-lookup"><span data-stu-id="46690-125">Writing to the File</span></span>  
 <span data-ttu-id="46690-126">Uygulama yoluyla bir dosyaya yazma özelliği eklemek için kullanın <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="46690-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="46690-127"><xref:System.IO.StreamWriter>karakter çıkışını bir belirli kodlama, ancak için tasarlanmış <xref:System.IO.Stream> sınıfı, giriş ve çıkış bayt için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="46690-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="46690-128">Kullanım <xref:System.IO.StreamWriter> satır bilgi standart metin dosyasına yazma.</span><span class="sxs-lookup"><span data-stu-id="46690-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="46690-129">Daha fazla bilgi için <xref:System.IO.StreamWriter> sınıfı için bkz: <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="46690-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>  
  
#### <a name="to-add-writing-functionality"></a><span data-ttu-id="46690-130">Yazma işlevselliği eklemek için</span><span class="sxs-lookup"><span data-stu-id="46690-130">To add writing functionality</span></span>  
  
1.  <span data-ttu-id="46690-131">Gelen **Görünüm** menüsünde seçin **kod** Kod Düzenleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="46690-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="46690-132">Uygulama başvurduğundan <xref:System.IO> ad alanı, kodunuzun en başından aşağıdaki deyimleri ekleyin, form için sınıf bildirimi önce hangi başlar `Public Class Form1`.</span><span class="sxs-lookup"><span data-stu-id="46690-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]  
  
     <span data-ttu-id="46690-133">Dosyaya yazmak için önce bir örneğini oluşturmanız gerekir bir <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="46690-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>  
  
3.  <span data-ttu-id="46690-134">Gelen **Görünüm** menüsünde seçin **Tasarımcısı** geri dönmek için **Windows Form Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="46690-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="46690-135">Çift `Submit` oluşturmak için düğmesini bir <xref:System.Windows.Forms.Control.Click> düğmesi için olay işleyicisini ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46690-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="46690-136">Visual Studio tümleşik geliştirme ortamı (IDE) kod düzenleyicisine dönün ve kodu nereye ekleyin olay işleyici içinde ekleme noktasını yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="46690-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>  
  
1.  <span data-ttu-id="46690-137">Dosyaya yazmak için <xref:System.IO.StreamWriter.Write%2A> yöntemi <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="46690-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="46690-138">Hemen sonra aşağıdaki kodu ekleyin `Dim fw As StreamWriter`.</span><span class="sxs-lookup"><span data-stu-id="46690-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="46690-139">Dosya bulunamazsa, zaten yoksa, oluşturulur çünkü bir özel durum atılır olduğunu endişelenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="46690-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]  
  
2.  <span data-ttu-id="46690-140">Kullanıcı boş bir girdiyi hemen sonra aşağıdaki kodu ekleyerek gönderemiyor emin `Dim ReadString As String`.</span><span class="sxs-lookup"><span data-stu-id="46690-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]  
  
3.  <span data-ttu-id="46690-141">Bu bir günlük olduğundan, kullanıcının her giriş için bir tarih atamak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="46690-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="46690-142">Sonra aşağıdaki kodu ekleyin `fw = New StreamWriter("C:\MyDiary.txt", True)` değişken ayarlamak üzere `Today` geçerli tarihi.</span><span class="sxs-lookup"><span data-stu-id="46690-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]  
  
4.  <span data-ttu-id="46690-143">Son olarak, temizlemek için kod ekleme <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="46690-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="46690-144">Aşağıdaki kodu ekleyin `Clear` düğmenin <xref:System.Windows.Forms.Control.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="46690-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]  
  
## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="46690-145">Günlük görüntüleme özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="46690-145">Adding Display Features to the Diary</span></span>  
 <span data-ttu-id="46690-146">Bu bölümde, en son giriş görüntüleyen özellik ekleme `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="46690-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="46690-147">Ayrıca ekleyebileceğiniz bir <xref:System.Windows.Forms.ComboBox> çeşitli girişleri görüntüler ve kullanıcının seçebileceği görüntülemek için bir giriş `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="46690-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="46690-148">Örneği <xref:System.IO.StreamReader> sınıf okuma `MyDiary.txt`.</span><span class="sxs-lookup"><span data-stu-id="46690-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="46690-149">Gibi <xref:System.IO.StreamWriter> sınıfı, <xref:System.IO.StreamReader> metin dosyalarını kullanılmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="46690-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>  
  
 <span data-ttu-id="46690-150">Bu bölümde örnekler için aşağıdaki tabloda formuna denetim eklemek için ve özelliklerini karşılık gelen değerler ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="46690-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="46690-151">Denetim</span><span class="sxs-lookup"><span data-stu-id="46690-151">Control</span></span>|<span data-ttu-id="46690-152">Özellikler</span><span class="sxs-lookup"><span data-stu-id="46690-152">Properties</span></span>|<span data-ttu-id="46690-153">Değerler</span><span class="sxs-lookup"><span data-stu-id="46690-153">Values</span></span>|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="46690-154">**Ad**</span><span class="sxs-lookup"><span data-stu-id="46690-154">**Name**</span></span><br /><br /> <span data-ttu-id="46690-155">**Görünür**</span><span class="sxs-lookup"><span data-stu-id="46690-155">**Visible**</span></span><br /><br /> <span data-ttu-id="46690-156">**Boyutu**</span><span class="sxs-lookup"><span data-stu-id="46690-156">**Size**</span></span><br /><br /> <span data-ttu-id="46690-157">**Çok satırlı**</span><span class="sxs-lookup"><span data-stu-id="46690-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="46690-158">**Ad**</span><span class="sxs-lookup"><span data-stu-id="46690-158">**Name**</span></span><br /><br /> <span data-ttu-id="46690-159">**Metin**</span><span class="sxs-lookup"><span data-stu-id="46690-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="46690-160">**Görüntüleme**</span><span class="sxs-lookup"><span data-stu-id="46690-160">**Display**</span></span>|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="46690-161">**Ad**</span><span class="sxs-lookup"><span data-stu-id="46690-161">**Name**</span></span><br /><br /> <span data-ttu-id="46690-162">**Metin**</span><span class="sxs-lookup"><span data-stu-id="46690-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="46690-163">**Girişlerini alma**</span><span class="sxs-lookup"><span data-stu-id="46690-163">**Get Entries**</span></span>|  
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="46690-164">**Ad**</span><span class="sxs-lookup"><span data-stu-id="46690-164">**Name**</span></span><br /><br /> <span data-ttu-id="46690-165">**Metin**</span><span class="sxs-lookup"><span data-stu-id="46690-165">**Text**</span></span><br /><br /> <span data-ttu-id="46690-166">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="46690-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="46690-167">**Bir giriş seçin**</span><span class="sxs-lookup"><span data-stu-id="46690-167">**Select an Entry**</span></span><br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a><span data-ttu-id="46690-168">Birleşik giriş kutusunu doldurmak için</span><span class="sxs-lookup"><span data-stu-id="46690-168">To populate the combo box</span></span>  
  
1.  <span data-ttu-id="46690-169">`PickEntries` <xref:System.Windows.Forms.ComboBox> Üzerinde bir kullanıcının gönderdiğini her giriş kullanıcı belirli bir tarihten itibaren bir giriş seçebilmeniz için tarihleri görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46690-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="46690-170">Oluşturma bir <xref:System.Windows.Forms.Control.Click> olay işleyicisine `GetEntries` düğmesine tıklayın ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46690-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]  
  
2.  <span data-ttu-id="46690-171">Kodunuzu test etmek için uygulamayı derleyin ve ardından için F5 tuşuna basın **Girişleri Al**.</span><span class="sxs-lookup"><span data-stu-id="46690-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="46690-172">Aşağı açılan oku tıklatın <xref:System.Windows.Forms.ComboBox> giriş tarihleri görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="46690-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>  
  
#### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="46690-173">Seçin ve girişleri tek tek görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="46690-173">To choose and display individual entries</span></span>  
  
1.  <span data-ttu-id="46690-174">Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisini `Display` düğmesine tıklayın ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46690-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]  
  
2.  <span data-ttu-id="46690-175">Kodunuzu test etmek için uygulama derlemek için F5 tuşuna basın ve ardından bir giriş göndermek.</span><span class="sxs-lookup"><span data-stu-id="46690-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="46690-176">Tıklatın **Girişleri Al**, bir giriş seçin <xref:System.Windows.Forms.ComboBox>ve ardından **görüntü**.</span><span class="sxs-lookup"><span data-stu-id="46690-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="46690-177">Seçilen girişi içeriğini görünür `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="46690-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="46690-178">Silmek veya girişleri değiştirmek kullanıcıları etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="46690-178">Enabling Users to Delete or Modify Entries</span></span>  
 <span data-ttu-id="46690-179">Son olarak, bir giriş kullanarak değiştirmek veya silmek için kullanıcıların ek işlevsellik sağlar içerebilir `DeleteEntry` ve `EditEntry` düğmeler.</span><span class="sxs-lookup"><span data-stu-id="46690-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="46690-180">Bir giriş görüntülenen sürece her iki düğmeleri devre dışı kalır.</span><span class="sxs-lookup"><span data-stu-id="46690-180">Both buttons remain disabled unless an entry is displayed.</span></span>  
  
 <span data-ttu-id="46690-181">Denetimleri aşağıdaki tabloda forma ekleme ve bunların özelliklerini karşılık gelen değerler ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="46690-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="46690-182">Denetim</span><span class="sxs-lookup"><span data-stu-id="46690-182">Control</span></span>|<span data-ttu-id="46690-183">Özellikler</span><span class="sxs-lookup"><span data-stu-id="46690-183">Properties</span></span>|<span data-ttu-id="46690-184">Değerler</span><span class="sxs-lookup"><span data-stu-id="46690-184">Values</span></span>|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="46690-185">**Ad**</span><span class="sxs-lookup"><span data-stu-id="46690-185">**Name**</span></span><br /><br /> <span data-ttu-id="46690-186">**Metin**</span><span class="sxs-lookup"><span data-stu-id="46690-186">**Text**</span></span><br /><br /> <span data-ttu-id="46690-187">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="46690-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="46690-188">**Giriş silme**</span><span class="sxs-lookup"><span data-stu-id="46690-188">**Delete Entry**</span></span><br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="46690-189">**Ad**</span><span class="sxs-lookup"><span data-stu-id="46690-189">**Name**</span></span><br /><br /> <span data-ttu-id="46690-190">**Metin**</span><span class="sxs-lookup"><span data-stu-id="46690-190">**Text**</span></span><br /><br /> <span data-ttu-id="46690-191">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="46690-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="46690-192">**Girişi Düzenle**</span><span class="sxs-lookup"><span data-stu-id="46690-192">**Edit Entry**</span></span><br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="46690-193">**Ad**</span><span class="sxs-lookup"><span data-stu-id="46690-193">**Name**</span></span><br /><br /> <span data-ttu-id="46690-194">**Metin**</span><span class="sxs-lookup"><span data-stu-id="46690-194">**Text**</span></span><br /><br /> <span data-ttu-id="46690-195">**Etkin**</span><span class="sxs-lookup"><span data-stu-id="46690-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="46690-196">**Düzen gönderme**</span><span class="sxs-lookup"><span data-stu-id="46690-196">**Submit Edit**</span></span><br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="46690-197">Silme ve girişleri değiştirilmesini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="46690-197">To enable deletion and modification of entries</span></span>  
  
1.  <span data-ttu-id="46690-198">Aşağıdaki kodu ekleyin `Display` düğmenin <xref:System.Windows.Forms.Control.Click> olay, sonra `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="46690-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]  
  
2.  <span data-ttu-id="46690-199">Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisini `DeleteEntry` düğmesine tıklayın ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46690-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]  
  
3.  <span data-ttu-id="46690-200">Bir kullanıcı bir giriş görüntülediğinde `EditEntry` düğmesi etkin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="46690-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="46690-201">Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olayı `Display` sonra düğmesini `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="46690-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]  
  
4.  <span data-ttu-id="46690-202">Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisini `EditEntry` düğmesine tıklayın ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46690-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]  
  
5.  <span data-ttu-id="46690-203">Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisini `SubmitEdit` düğmesine tıklayın ve aşağıdaki kodu ekleyin</span><span class="sxs-lookup"><span data-stu-id="46690-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]  
  
 <span data-ttu-id="46690-204">Kodunuzu test etmek için uygulama derlemek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="46690-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="46690-205">Tıklatın **Girişleri Al**bir girişi seçin ve ardından **görüntü**.</span><span class="sxs-lookup"><span data-stu-id="46690-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="46690-206">Giriş belirir `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="46690-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="46690-207">Tıklatın **Düzenle girişi**.</span><span class="sxs-lookup"><span data-stu-id="46690-207">Click **Edit Entry**.</span></span> <span data-ttu-id="46690-208">Giriş belirir `Entry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="46690-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="46690-209">Girişi düzenlemek `Entry` <xref:System.Windows.Forms.TextBox> tıklatıp **gönderme Düzenle**.</span><span class="sxs-lookup"><span data-stu-id="46690-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="46690-210">Açık `MyDiary.txt` düzeltmenizi onaylamak için dosya.</span><span class="sxs-lookup"><span data-stu-id="46690-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="46690-211">Şimdi bir girişi seçin ve tıklatın **girişi silmek**.</span><span class="sxs-lookup"><span data-stu-id="46690-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="46690-212">Zaman <xref:System.Windows.Forms.MessageBox> onay istekleri tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="46690-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="46690-213">Uygulamayı kapatıp açın `MyDiary.txt` silme işlemini onaylayın.</span><span class="sxs-lookup"><span data-stu-id="46690-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46690-214">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46690-214">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="46690-215">İzlenecek yollar</span><span class="sxs-lookup"><span data-stu-id="46690-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)
