---
title: Dosyaları ve Dizinleri Düzenleme
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
ms.openlocfilehash: 83dc6ce0d29c1c368c36b51fc84ecad34d72e01f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333802"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="a1ac3-102">İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="a1ac3-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>

<span data-ttu-id="a1ac3-103">Bu izlenecek yol, Visual Basic dosya g/ç 'nin temelleri için bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="a1ac3-104">Bir dizindeki metin dosyalarını listeleyen ve inceleyen küçük bir uygulamanın nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="a1ac3-105">Uygulama, seçili her metin dosyası için dosya öznitelikleri ve ilk içerik satırı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="a1ac3-106">Günlük dosyasına bilgi yazma seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="a1ac3-107">Bu izlenecek yol, Visual Basic `My.Computer.FileSystem Object`' de kullanılabilir olan üyelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="a1ac3-108">Daha fazla bilgi edinmek için bkz. <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="a1ac3-109">İzlenecek yolun sonunda, <xref:System.IO> ad alanından sınıfları kullanan eşdeğer bir örnek sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="a1ac3-110">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a1ac3-110">To create the project</span></span>  
  
1. <span data-ttu-id="a1ac3-111">**Dosya** menüsünde **Yeni proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="a1ac3-112">**Yeni Proje** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="a1ac3-113">**Yüklü şablonlar** bölmesinde, **Visual Basic**öğesini genişletin ve ardından **Windows**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="a1ac3-114">Ortadaki **Şablonlar** bölmesinde **Windows Forms uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="a1ac3-115">**Ad** kutusunda, proje adını ayarlamak `FileExplorer` Için yazın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a1ac3-116">Visual Studio, projeyi **Çözüm Gezgini**ekler ve Windows Form Tasarımcısı açılır.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="a1ac3-117">Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="a1ac3-118">Denetim</span><span class="sxs-lookup"><span data-stu-id="a1ac3-118">Control</span></span>|<span data-ttu-id="a1ac3-119">Özellik</span><span class="sxs-lookup"><span data-stu-id="a1ac3-119">Property</span></span>|<span data-ttu-id="a1ac3-120">Değer</span><span class="sxs-lookup"><span data-stu-id="a1ac3-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="a1ac3-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-121">**ListBox**</span></span>|<span data-ttu-id="a1ac3-122">**Adı**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="a1ac3-123">**Bu**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-123">**Button**</span></span>|<span data-ttu-id="a1ac3-124">**Adı**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-124">**Name**</span></span><br /><br /> <span data-ttu-id="a1ac3-125">**Metin**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="a1ac3-126">**Gözat**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-126">**Browse**</span></span>|  
    |<span data-ttu-id="a1ac3-127">**Bu**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-127">**Button**</span></span>|<span data-ttu-id="a1ac3-128">**Adı**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-128">**Name**</span></span><br /><br /> <span data-ttu-id="a1ac3-129">**Metin**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="a1ac3-130">**İncelemesine**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-130">**Examine**</span></span>|  
    |<span data-ttu-id="a1ac3-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-131">**CheckBox**</span></span>|<span data-ttu-id="a1ac3-132">**Adı**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-132">**Name**</span></span><br /><br /> <span data-ttu-id="a1ac3-133">**Metin**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="a1ac3-134">**Sonuçları Kaydet**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-134">**Save Results**</span></span>|  
    |<span data-ttu-id="a1ac3-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="a1ac3-136">**Adı**</span><span class="sxs-lookup"><span data-stu-id="a1ac3-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="a1ac3-137">Bir klasörü seçmek ve dosyaları bir klasöre listelemek için</span><span class="sxs-lookup"><span data-stu-id="a1ac3-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="a1ac3-138">Form üzerindeki `Click` denetime çift tıklayarak `browseButton` için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="a1ac3-139">Kod Düzenleyicisi açılır.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="a1ac3-140">`Click` Olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="a1ac3-141">`FolderBrowserDialog1.ShowDialog` Arama, **klasöre gözataaç** iletişim kutusunu açar.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="a1ac3-142">Kullanıcı **Tamam**' ı tıkladıktan sonra, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliği bir sonraki adımda eklenen `ListFiles` yöntemine bir bağımsız değişken olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="a1ac3-143">Aşağıdaki `ListFiles` yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="a1ac3-144">Bu kod, önce **ListBox**'ı temizler.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="a1ac3-145"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> Yöntemi daha sonra dizindeki her dosya için bir dize koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="a1ac3-146">Yöntemi `GetFiles` , belirli bir düzenle eşleşen dosyaları almak için bir arama deseninin bağımsız değişkenini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="a1ac3-147">Bu örnekte, yalnızca. txt uzantılı dosyalar döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="a1ac3-148">`GetFiles` Yöntemi tarafından döndürülen dizeler daha sonra **ListBox**'a eklenir.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="a1ac3-149">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-149">Run the application.</span></span> <span data-ttu-id="a1ac3-150">**Araştır** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-150">Click the **Browse** button.</span></span> <span data-ttu-id="a1ac3-151">**Klasöre araştır** iletişim kutusunda. txt dosyalarını içeren bir klasöre gidin ve ardından klasörü seçip **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="a1ac3-152">, `ListBox` Seçilen klasördeki. txt dosyalarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="a1ac3-153">Uygulamayı çalıştırmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="a1ac3-154">Bir dosyanın özniteliklerini ve bir metin dosyasından içerik almak için</span><span class="sxs-lookup"><span data-stu-id="a1ac3-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="a1ac3-155">Form üzerindeki `Click` denetime çift tıklayarak `examineButton` için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="a1ac3-156">`Click` Olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="a1ac3-157">Kod, `ListBox`içinde bir öğenin seçili olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="a1ac3-158">Daha sonra konumundan dosya yolu girişini edinir `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="a1ac3-159"><xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> Yöntemi, dosyanın hala mevcut olup olmadığını denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="a1ac3-160">Dosya yolu, bir sonraki adımda eklenen `GetTextForOutput` yöntemine bir bağımsız değişken olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="a1ac3-161">Bu yöntem, dosya bilgilerini içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="a1ac3-162">Dosya bilgileri bir **MessageBox**içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="a1ac3-163">Aşağıdaki `GetTextForOutput` yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="a1ac3-164">Kod, dosya parametrelerini <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="a1ac3-165">Dosya parametreleri bir <xref:System.Text.StringBuilder>öğesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="a1ac3-166"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> Yöntemi dosya içeriğini bir <xref:System.IO.StreamReader>ile okur.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="a1ac3-167">İçeriklerin ilk satırı öğesinden alınır `StreamReader` ve öğesine eklenir. `StringBuilder`</span><span class="sxs-lookup"><span data-stu-id="a1ac3-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="a1ac3-168">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-168">Run the application.</span></span> <span data-ttu-id="a1ac3-169">**Araştır**' a tıklayın ve. txt dosyalarını içeren bir klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="a1ac3-170">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="a1ac3-171">İçinde `ListBox`bir dosya seçin ve ardından **İncele**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="a1ac3-172">Dosya `MessageBox` bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="a1ac3-173">Uygulamayı çalıştırmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="a1ac3-174">Günlük girdisi eklemek için</span><span class="sxs-lookup"><span data-stu-id="a1ac3-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="a1ac3-175">`examineButton_Click` Olay işleyicisinin sonuna aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="a1ac3-176">Kod, günlük dosyasını seçili dosya ile aynı dizine yerleştirmek için günlük dosyası yolunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="a1ac3-177">Günlük girişinin metni geçerli tarih ve saate, sonra da dosya bilgilerine göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="a1ac3-178">`append` Bağımsız değişkeni olarak `True`ayarlanan <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> yöntemi, günlük girişini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="a1ac3-179">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-179">Run the application.</span></span> <span data-ttu-id="a1ac3-180">Bir metin dosyasına göz atın, içinde `ListBox`seçin, **Sonuçları Kaydet** onay kutusunu seçin ve ardından **İncele**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="a1ac3-181">Günlük girişinin `log.txt` dosyaya yazıldığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="a1ac3-182">Uygulamayı çalıştırmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="a1ac3-183">Geçerli dizini kullanmak için</span><span class="sxs-lookup"><span data-stu-id="a1ac3-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="a1ac3-184">Forma çift tıklayarak için `Form1_Load` bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="a1ac3-185">Olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="a1ac3-186">Bu kod, klasör tarayıcısının varsayılan dizinini geçerli dizine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="a1ac3-187">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-187">Run the application.</span></span> <span data-ttu-id="a1ac3-188">İlk kez **Araştır** ' a tıkladığınızda, **klasöre yönelik tarama** iletişim kutusu geçerli dizine açılır.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="a1ac3-189">Uygulamayı çalıştırmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="a1ac3-190">Denetimleri seçmeli olarak etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="a1ac3-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="a1ac3-191">Aşağıdaki `SetEnabled` yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="a1ac3-192">`SetEnabled` Yöntemi, `ListBox`içinde bir öğenin seçili olmasına bağlı olarak denetimleri etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="a1ac3-193">Form üzerindeki `SelectedIndexChanged` `ListBox` denetime çift tıklayarak `filesListBox` için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="a1ac3-194">Yeni `filesListBox_SelectedIndexChanged` olay işleyicisine bir `SetEnabled` çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="a1ac3-195">Olay işleyicisinin sonuna bir `SetEnabled` çağrı ekleyin. `browseButton_Click`</span><span class="sxs-lookup"><span data-stu-id="a1ac3-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="a1ac3-196">Olay işleyicisinin sonuna bir `SetEnabled` çağrı ekleyin. `Form1_Load`</span><span class="sxs-lookup"><span data-stu-id="a1ac3-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="a1ac3-197">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-197">Run the application.</span></span> <span data-ttu-id="a1ac3-198">İçinde bir öğe seçilmezse **Sonuçları Kaydet** onay kutusu ve **İncele** düğmesi devre dışıdır `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="a1ac3-199">My. Computer. FileSystem kullanarak tam örnek</span><span class="sxs-lookup"><span data-stu-id="a1ac3-199">Full example using My.Computer.FileSystem</span></span>  

 <span data-ttu-id="a1ac3-200">Aşağıda, tüm örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="a1ac3-201">System.IO kullanarak tam örnek</span><span class="sxs-lookup"><span data-stu-id="a1ac3-201">Full example using System.IO</span></span>  

 <span data-ttu-id="a1ac3-202">Aşağıdaki eşdeğer örnek, nesneleri kullanmak <xref:System.IO> `My.Computer.FileSystem` yerine ad alanından sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="a1ac3-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1ac3-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="a1ac3-204">İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="a1ac3-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
