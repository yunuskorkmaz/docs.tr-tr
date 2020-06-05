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
ms.openlocfilehash: 4b77618e5cd525cf3ad012405f402681aa5bb52c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406670"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="0a89a-102">İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="0a89a-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>

<span data-ttu-id="0a89a-103">Bu izlenecek yol, Visual Basic dosya g/ç 'nin temelleri için bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a89a-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="0a89a-104">Bir dizindeki metin dosyalarını listeleyen ve inceleyen küçük bir uygulamanın nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0a89a-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="0a89a-105">Uygulama, seçili her metin dosyası için dosya öznitelikleri ve ilk içerik satırı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a89a-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="0a89a-106">Günlük dosyasına bilgi yazma seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="0a89a-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="0a89a-107">Bu izlenecek yol, `My.Computer.FileSystem Object` Visual Basic ' de kullanılabilir olan üyelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0a89a-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="0a89a-108">Daha fazla bilgi edinmek için bkz. <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="0a89a-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="0a89a-109">İzlenecek yolun sonunda, ad alanından sınıfları kullanan eşdeğer bir örnek sağlanır <xref:System.IO> .</span><span class="sxs-lookup"><span data-stu-id="0a89a-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="0a89a-110">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0a89a-110">To create the project</span></span>  
  
1. <span data-ttu-id="0a89a-111">**Dosya** menüsünde **Yeni proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="0a89a-112">**Yeni Proje** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="0a89a-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="0a89a-113">**Yüklü şablonlar** bölmesinde, **Visual Basic**öğesini genişletin ve ardından **Windows**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="0a89a-114">Ortadaki **Şablonlar** bölmesinde **Windows Forms uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="0a89a-115">**Ad** kutusunda, `FileExplorer` proje adını ayarlamak için yazın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="0a89a-116">Visual Studio, projeyi **Çözüm Gezgini**ekler ve Windows Form Tasarımcısı açılır.</span><span class="sxs-lookup"><span data-stu-id="0a89a-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="0a89a-117">Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="0a89a-118">Denetim</span><span class="sxs-lookup"><span data-stu-id="0a89a-118">Control</span></span>|<span data-ttu-id="0a89a-119">Özellik</span><span class="sxs-lookup"><span data-stu-id="0a89a-119">Property</span></span>|<span data-ttu-id="0a89a-120">Değer</span><span class="sxs-lookup"><span data-stu-id="0a89a-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="0a89a-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="0a89a-121">**ListBox**</span></span>|<span data-ttu-id="0a89a-122">**Adı**</span><span class="sxs-lookup"><span data-stu-id="0a89a-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="0a89a-123">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="0a89a-123">**Button**</span></span>|<span data-ttu-id="0a89a-124">**Adı**</span><span class="sxs-lookup"><span data-stu-id="0a89a-124">**Name**</span></span><br /><br /> <span data-ttu-id="0a89a-125">**Metin**</span><span class="sxs-lookup"><span data-stu-id="0a89a-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="0a89a-126">**Gözat**</span><span class="sxs-lookup"><span data-stu-id="0a89a-126">**Browse**</span></span>|  
    |<span data-ttu-id="0a89a-127">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="0a89a-127">**Button**</span></span>|<span data-ttu-id="0a89a-128">**Adı**</span><span class="sxs-lookup"><span data-stu-id="0a89a-128">**Name**</span></span><br /><br /> <span data-ttu-id="0a89a-129">**Metin**</span><span class="sxs-lookup"><span data-stu-id="0a89a-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="0a89a-130">**İncelemesine**</span><span class="sxs-lookup"><span data-stu-id="0a89a-130">**Examine**</span></span>|  
    |<span data-ttu-id="0a89a-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="0a89a-131">**CheckBox**</span></span>|<span data-ttu-id="0a89a-132">**Adı**</span><span class="sxs-lookup"><span data-stu-id="0a89a-132">**Name**</span></span><br /><br /> <span data-ttu-id="0a89a-133">**Metin**</span><span class="sxs-lookup"><span data-stu-id="0a89a-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="0a89a-134">**Sonuçları Kaydet**</span><span class="sxs-lookup"><span data-stu-id="0a89a-134">**Save Results**</span></span>|  
    |<span data-ttu-id="0a89a-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="0a89a-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="0a89a-136">**Adı**</span><span class="sxs-lookup"><span data-stu-id="0a89a-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="0a89a-137">Bir klasörü seçmek ve dosyaları bir klasöre listelemek için</span><span class="sxs-lookup"><span data-stu-id="0a89a-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="0a89a-138">`Click` `browseButton` Form üzerindeki denetime çift tıklayarak için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0a89a-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="0a89a-139">Kod Düzenleyicisi açılır.</span><span class="sxs-lookup"><span data-stu-id="0a89a-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="0a89a-140">Olay işleyicisine aşağıdaki kodu ekleyin `Click` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="0a89a-141">`FolderBrowserDialog1.ShowDialog`Arama, **klasöre gözataaç** iletişim kutusunu açar.</span><span class="sxs-lookup"><span data-stu-id="0a89a-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="0a89a-142">Kullanıcı **Tamam**' ı tıkladıktan sonra, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliği bir `ListFiles` sonraki adımda eklenen yöntemine bir bağımsız değişken olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="0a89a-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="0a89a-143">Aşağıdaki yöntemi ekleyin `ListFiles` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="0a89a-144">Bu kod, önce **ListBox**'ı temizler.</span><span class="sxs-lookup"><span data-stu-id="0a89a-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="0a89a-145"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>Yöntemi daha sonra dizindeki her dosya için bir dize koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="0a89a-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="0a89a-146">`GetFiles`Yöntemi, belirli bir düzenle eşleşen dosyaları almak için bir arama deseninin bağımsız değişkenini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="0a89a-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="0a89a-147">Bu örnekte, yalnızca. txt uzantılı dosyalar döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0a89a-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="0a89a-148">Yöntemi tarafından döndürülen dizeler `GetFiles` daha sonra **ListBox**'a eklenir.</span><span class="sxs-lookup"><span data-stu-id="0a89a-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="0a89a-149">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-149">Run the application.</span></span> <span data-ttu-id="0a89a-150">**Araştır** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-150">Click the **Browse** button.</span></span> <span data-ttu-id="0a89a-151">**Klasöre araştır** iletişim kutusunda. txt dosyalarını içeren bir klasöre gidin ve ardından klasörü seçip **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="0a89a-152">, `ListBox` Seçilen klasördeki. txt dosyalarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0a89a-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="0a89a-153">Uygulamayı çalıştırmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="0a89a-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="0a89a-154">Bir dosyanın özniteliklerini ve bir metin dosyasından içerik almak için</span><span class="sxs-lookup"><span data-stu-id="0a89a-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="0a89a-155">`Click` `examineButton` Form üzerindeki denetime çift tıklayarak için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0a89a-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="0a89a-156">Olay işleyicisine aşağıdaki kodu ekleyin `Click` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="0a89a-157">Kod, içinde bir öğenin seçili olduğunu doğrular `ListBox` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="0a89a-158">Daha sonra konumundan dosya yolu girişini edinir `ListBox` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="0a89a-159"><xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A>Yöntemi, dosyanın hala mevcut olup olmadığını denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a89a-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="0a89a-160">Dosya yolu, bir `GetTextForOutput` sonraki adımda eklenen yöntemine bir bağımsız değişken olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="0a89a-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="0a89a-161">Bu yöntem, dosya bilgilerini içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a89a-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="0a89a-162">Dosya bilgileri bir **MessageBox**içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0a89a-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="0a89a-163">Aşağıdaki yöntemi ekleyin `GetTextForOutput` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="0a89a-164">Kod, <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Dosya parametrelerini almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0a89a-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="0a89a-165">Dosya parametreleri bir öğesine eklenir <xref:System.Text.StringBuilder> .</span><span class="sxs-lookup"><span data-stu-id="0a89a-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="0a89a-166"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>Yöntemi dosya içeriğini bir ile okur <xref:System.IO.StreamReader> .</span><span class="sxs-lookup"><span data-stu-id="0a89a-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="0a89a-167">İçeriklerin ilk satırı öğesinden alınır `StreamReader` ve öğesine eklenir `StringBuilder` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="0a89a-168">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-168">Run the application.</span></span> <span data-ttu-id="0a89a-169">**Araştır**' a tıklayın ve. txt dosyalarını içeren bir klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="0a89a-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="0a89a-170">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="0a89a-171">İçinde bir dosya seçin `ListBox` ve ardından **İncele**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="0a89a-172">`MessageBox`Dosya bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a89a-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="0a89a-173">Uygulamayı çalıştırmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="0a89a-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="0a89a-174">Günlük girdisi eklemek için</span><span class="sxs-lookup"><span data-stu-id="0a89a-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="0a89a-175">Olay işleyicisinin sonuna aşağıdaki kodu ekleyin `examineButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="0a89a-176">Kod, günlük dosyasını seçili dosya ile aynı dizine yerleştirmek için günlük dosyası yolunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0a89a-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="0a89a-177">Günlük girişinin metni geçerli tarih ve saate, sonra da dosya bilgilerine göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0a89a-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="0a89a-178"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> `append` Bağımsız değişkeni olarak ayarlanan yöntemi, `True` günlük girişini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a89a-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="0a89a-179">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-179">Run the application.</span></span> <span data-ttu-id="0a89a-180">Bir metin dosyasına göz atın, içinde seçin, `ListBox` **Sonuçları Kaydet** onay kutusunu seçin ve ardından **İncele**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="0a89a-181">Günlük girişinin dosyaya yazıldığını doğrulayın `log.txt` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="0a89a-182">Uygulamayı çalıştırmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="0a89a-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="0a89a-183">Geçerli dizini kullanmak için</span><span class="sxs-lookup"><span data-stu-id="0a89a-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="0a89a-184">Forma çift tıklayarak için bir olay işleyicisi oluşturun `Form1_Load` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="0a89a-185">Olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0a89a-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="0a89a-186">Bu kod, klasör tarayıcısının varsayılan dizinini geçerli dizine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0a89a-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="0a89a-187">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-187">Run the application.</span></span> <span data-ttu-id="0a89a-188">İlk kez **Araştır** ' a tıkladığınızda, **klasöre yönelik tarama** iletişim kutusu geçerli dizine açılır.</span><span class="sxs-lookup"><span data-stu-id="0a89a-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="0a89a-189">Uygulamayı çalıştırmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="0a89a-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="0a89a-190">Denetimleri seçmeli olarak etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="0a89a-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="0a89a-191">Aşağıdaki yöntemi ekleyin `SetEnabled` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="0a89a-192">`SetEnabled`Yöntemi, içinde bir öğenin seçili olmasına bağlı olarak denetimleri etkinleştirilir veya devre dışı bırakır `ListBox` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="0a89a-193">`SelectedIndexChanged` `filesListBox` Form üzerindeki denetime çift tıklayarak için bir olay işleyicisi oluşturun `ListBox` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="0a89a-194">`SetEnabled`Yeni olay işleyicisine bir çağrı ekleyin `filesListBox_SelectedIndexChanged` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="0a89a-195">`SetEnabled`Olay işleyicisinin sonuna bir çağrı ekleyin `browseButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="0a89a-196">`SetEnabled`Olay işleyicisinin sonuna bir çağrı ekleyin `Form1_Load` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="0a89a-197">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0a89a-197">Run the application.</span></span> <span data-ttu-id="0a89a-198">İçinde bir öğe seçilmezse **Sonuçları Kaydet** onay kutusu ve **İncele** düğmesi devre dışıdır `ListBox` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="0a89a-199">My. Computer. FileSystem kullanarak tam örnek</span><span class="sxs-lookup"><span data-stu-id="0a89a-199">Full example using My.Computer.FileSystem</span></span>  

 <span data-ttu-id="0a89a-200">Aşağıda, tüm örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0a89a-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="0a89a-201">System.IO kullanarak tam örnek</span><span class="sxs-lookup"><span data-stu-id="0a89a-201">Full example using System.IO</span></span>  

 <span data-ttu-id="0a89a-202">Aşağıdaki eşdeğer örnek, <xref:System.IO> nesneleri kullanmak yerine ad alanından sınıfları kullanır `My.Computer.FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="0a89a-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="0a89a-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a89a-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="0a89a-204">İzlenecek yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="0a89a-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](walkthrough-manipulating-files-by-using-net-framework-methods.md)
