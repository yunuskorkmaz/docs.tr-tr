---
title: Dosyaları ve dizinleri Visual Basic'te düzenleme
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], reading text
- reading files [Visual Basic], text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files [Visual Basic], walkthroughs
- Visual Basic code, file access
- files [Visual Basic], writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files [Visual Basic], walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
ms.openlocfilehash: 9410d166a3f91770cb0c64b9971dc58ad9cd07cb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843701"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="d2cb6-102">İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme</span><span class="sxs-lookup"><span data-stu-id="d2cb6-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>
<span data-ttu-id="d2cb6-103">Bu izlenecek yol, Visual Basic'te dosya g/ç temelleri tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="d2cb6-104">Bu listeler ve bir dizinde metin dosyaları inceler, küçük bir uygulamanın nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="d2cb6-105">Her seçili metin dosyası için dosya öznitelikleri ve içeriğindeki birinci satırın uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="d2cb6-106">Bir günlük dosyasına yazmak için bir seçenek yoktur.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="d2cb6-107">Bu izlenecek yolda üyeleri kullanan `My.Computer.FileSystem Object`, Visual Basic'te kullanılabilir olduğu.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="d2cb6-108">Daha fazla bilgi edinmek için bkz. <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="d2cb6-109">İzlenecek yol sonunda sınıflarını kullanan eşdeğer bir örnek sağlanır <xref:System.IO> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="d2cb6-110">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d2cb6-110">To create the project</span></span>  
  
1.  <span data-ttu-id="d2cb6-111">Üzerinde **dosya** menüsünü tıklatın **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="d2cb6-112">**Yeni Proje** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-112">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="d2cb6-113">İçinde **yüklü şablonlar** bölmesini genişletin **Visual Basic**ve ardından **Windows**.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="d2cb6-114">İçinde **şablonları** Orta tıklayarak bölmesinde **Windows Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="d2cb6-115">İçinde **adı** kutusuna `FileExplorer` proje adını ayarlayın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d2cb6-116">Visual Studio projeyi ekler **Çözüm Gezgini**, ve Windows Forms Tasarımcısı açılır.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4.  <span data-ttu-id="d2cb6-117">Denetimler aşağıdaki tabloda forma eklemek ve karşılık gelen özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="d2cb6-118">Denetim</span><span class="sxs-lookup"><span data-stu-id="d2cb6-118">Control</span></span>|<span data-ttu-id="d2cb6-119">Özellik</span><span class="sxs-lookup"><span data-stu-id="d2cb6-119">Property</span></span>|<span data-ttu-id="d2cb6-120">Değer</span><span class="sxs-lookup"><span data-stu-id="d2cb6-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="d2cb6-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-121">**ListBox**</span></span>|<span data-ttu-id="d2cb6-122">**Ad**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="d2cb6-123">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-123">**Button**</span></span>|<span data-ttu-id="d2cb6-124">**Ad**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-124">**Name**</span></span><br /><br /> <span data-ttu-id="d2cb6-125">**Metin**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="d2cb6-126">**Göz atma**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-126">**Browse**</span></span>|  
    |<span data-ttu-id="d2cb6-127">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-127">**Button**</span></span>|<span data-ttu-id="d2cb6-128">**Ad**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-128">**Name**</span></span><br /><br /> <span data-ttu-id="d2cb6-129">**Metin**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="d2cb6-130">**İnceleyin**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-130">**Examine**</span></span>|  
    |<span data-ttu-id="d2cb6-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-131">**CheckBox**</span></span>|<span data-ttu-id="d2cb6-132">**Ad**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-132">**Name**</span></span><br /><br /> <span data-ttu-id="d2cb6-133">**Metin**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="d2cb6-134">**Sonuçları Kaydet**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-134">**Save Results**</span></span>|  
    |<span data-ttu-id="d2cb6-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="d2cb6-136">**Ad**</span><span class="sxs-lookup"><span data-stu-id="d2cb6-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="d2cb6-137">Bir klasör seçin ve bir klasördeki dosyaları Listele</span><span class="sxs-lookup"><span data-stu-id="d2cb6-137">To select a folder, and list files in a folder</span></span>  
  
1.  <span data-ttu-id="d2cb6-138">Oluşturma bir `Click` için olay işleyicisi `browseButton` formdaki bir denetime çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="d2cb6-139">Kod Düzenleyicisi açılır.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-139">The Code Editor opens.</span></span>  
  
2.  <span data-ttu-id="d2cb6-140">Aşağıdaki kodu ekleyin `Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="d2cb6-141">`FolderBrowserDialog1.ShowDialog` Çağrı açılır **klasöre Gözat** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="d2cb6-142">Sonra kullanıcı **Tamam**, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliği gönderilen bağımsız değişken olarak `ListFiles` sonraki adımda eklenen yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3.  <span data-ttu-id="d2cb6-143">Aşağıdaki `ListFiles` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="d2cb6-144">Bu kod önce temizler **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="d2cb6-145"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> Yöntemi ardından dizeleri, dizindeki her dosya için bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="d2cb6-146">`GetFiles` Yöntemi belirli bir desenle eşleşen dosyaları almak için bir arama deseni bağımsız değişkeni kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="d2cb6-147">Bu örnekte, yalnızca uzantısı .txt sahip dosyalar döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="d2cb6-148">Tarafından döndürülen dizeler `GetFiles` yöntemi ardından eklenir **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4.  <span data-ttu-id="d2cb6-149">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-149">Run the application.</span></span> <span data-ttu-id="d2cb6-150">Tıklayın **Gözat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-150">Click the **Browse** button.</span></span> <span data-ttu-id="d2cb6-151">İçinde **klasöre Gözat** iletişim kutusu, .txt dosyaları içeren bir klasörü klasörü seçin ve tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="d2cb6-152">`ListBox` Seçilen klasördeki .txt dosyalarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5.  <span data-ttu-id="d2cb6-153">Uygulamanın çalışmayı durdurur.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="d2cb6-154">Bir dosyanın özniteliklerini alma ve bir metin dosyasından içerik</span><span class="sxs-lookup"><span data-stu-id="d2cb6-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1.  <span data-ttu-id="d2cb6-155">Oluşturma bir `Click` için olay işleyicisi `examineButton` formdaki bir denetime çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2.  <span data-ttu-id="d2cb6-156">Aşağıdaki kodu ekleyin `Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="d2cb6-157">Kod içinde bir öğe seçildiğinde doğrular `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="d2cb6-158">Ardından dosya yolu girdisinden elde `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="d2cb6-159"><xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> Yöntemi, dosyanın hala varolup olmadığını denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="d2cb6-160">Dosya yolu için bağımsız değişken olarak gönderilen `GetTextForOutput` sonraki adımda eklenen yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="d2cb6-161">Bu yöntem dosya bilgileri içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="d2cb6-162">Dosya bilgileri görünür bir **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-162">The file information appears in a **MessageBox**.</span></span>  
  
3.  <span data-ttu-id="d2cb6-163">Aşağıdaki `GetTextForOutput` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="d2cb6-164">Kod <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> dosya parametrelerini elde etmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="d2cb6-165">Dosya parametrelerini eklenen bir <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="d2cb6-166"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> Yöntemi okur dosya içeriğine bir <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="d2cb6-167">İlk satırının içeriğini elde edilen `StreamReader` ve eklendiğinden `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4.  <span data-ttu-id="d2cb6-168">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-168">Run the application.</span></span> <span data-ttu-id="d2cb6-169">Tıklayın **Gözat**, .txt dosyaları içeren bir klasöre göz atın.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="d2cb6-170">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="d2cb6-171">Bir dosya seçin `ListBox`ve ardından **inceleyin**.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="d2cb6-172">A `MessageBox` dosya bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-172">A `MessageBox` shows the file information.</span></span>  
  
5.  <span data-ttu-id="d2cb6-173">Uygulamanın çalışmayı durdurur.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="d2cb6-174">Günlük girdisi eklemek için</span><span class="sxs-lookup"><span data-stu-id="d2cb6-174">To add a log entry</span></span>  
  
1.  <span data-ttu-id="d2cb6-175">Sonuna aşağıdaki kodu ekleyin `examineButton_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="d2cb6-176">Bu kod, seçilen dosya ile aynı dizine günlük dosyasına koymak için günlük dosyası yolu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="d2cb6-177">Geçerli tarih ve saate dosya bilgilerin günlük girişinin metnini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="d2cb6-178"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Yöntemi ile `append` değişkenini `True`, günlüğü girdisi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2.  <span data-ttu-id="d2cb6-179">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-179">Run the application.</span></span> <span data-ttu-id="d2cb6-180">Bir metin dosyasına göz atın, onu seçip `ListBox`seçin **Sonuçları Kaydet** onay kutusunu işaretleyin ve ardından **inceleyin**.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="d2cb6-181">Günlük girişi için yazıldığını doğrulayın `log.txt` dosya.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3.  <span data-ttu-id="d2cb6-182">Uygulamanın çalışmayı durdurur.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="d2cb6-183">Geçerli dizin kullanmak için</span><span class="sxs-lookup"><span data-stu-id="d2cb6-183">To use the current directory</span></span>  
  
1.  <span data-ttu-id="d2cb6-184">İçin bir olay işleyicisi oluşturun `Form1_Load` formun çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2.  <span data-ttu-id="d2cb6-185">Olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="d2cb6-186">Bu kod, geçerli dizine klasör tarayıcı varsayılan dizinini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3.  <span data-ttu-id="d2cb6-187">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-187">Run the application.</span></span> <span data-ttu-id="d2cb6-188">Tıkladığınızda **Gözat** ilk kez **klasöre Gözat** geçerli dizine iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4.  <span data-ttu-id="d2cb6-189">Uygulamanın çalışmayı durdurur.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="d2cb6-190">Seçmeli olarak denetimleri etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="d2cb6-190">To selectively enable controls</span></span>  
  
1.  <span data-ttu-id="d2cb6-191">Aşağıdaki `SetEnabled` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="d2cb6-192">`SetEnabled` Yöntemi etkinleştirir veya bir öğe olup olmadığını seçildiğinde bağlı olarak denetimleri devre dışı bırakan `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2.  <span data-ttu-id="d2cb6-193">Oluşturma bir `SelectedIndexChanged` için olay işleyicisi `filesListBox` çift tıklayarak `ListBox` form denetimi.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3.  <span data-ttu-id="d2cb6-194">Bir çağrı ekleyin `SetEnabled` yeni `filesListBox_SelectedIndexChanged` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4.  <span data-ttu-id="d2cb6-195">Bir çağrı ekleyin `SetEnabled` sonunda `browseButton_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5.  <span data-ttu-id="d2cb6-196">Bir çağrı ekleyin `SetEnabled` sonunda `Form1_Load` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6.  <span data-ttu-id="d2cb6-197">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-197">Run the application.</span></span> <span data-ttu-id="d2cb6-198">**Sonuçları Kaydet** onay kutusunu ve **inceleyin** içinde bir öğe seçili değilse düğmesi devre dışı `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="d2cb6-199">My.Computer.FileSystem kullanarak tam örnek</span><span class="sxs-lookup"><span data-stu-id="d2cb6-199">Full example using My.Computer.FileSystem</span></span>  
 <span data-ttu-id="d2cb6-200">Tam bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="d2cb6-201">System.IO kullanarak tam örnek</span><span class="sxs-lookup"><span data-stu-id="d2cb6-201">Full example using System.IO</span></span>  
 <span data-ttu-id="d2cb6-202">Aşağıdaki eşdeğer sınıflardan örnekte <xref:System.IO> kullanmak yerine ad alanı `My.Computer.FileSystem` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="d2cb6-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2cb6-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="d2cb6-204">İzlenecek yol: .NET Framework yöntemlerini kullanarak dosyaları düzenleme</span><span class="sxs-lookup"><span data-stu-id="d2cb6-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
