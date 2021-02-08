---
description: 'Daha fazla bilgi edinin: Izlenecek yol: Visual Basic dosya ve dizinleri düzenleme'
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
ms.openlocfilehash: 315635ee43ee4d4956fc35b7f9bc635b374646f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775389"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="c7ed7-103">İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="c7ed7-103">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>

<span data-ttu-id="c7ed7-104">Bu izlenecek yol, Visual Basic dosya g/ç 'nin temelleri için bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-104">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="c7ed7-105">Bir dizindeki metin dosyalarını listeleyen ve inceleyen küçük bir uygulamanın nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-105">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="c7ed7-106">Uygulama, seçili her metin dosyası için dosya öznitelikleri ve ilk içerik satırı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-106">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="c7ed7-107">Günlük dosyasına bilgi yazma seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-107">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="c7ed7-108">Bu izlenecek yol, `My.Computer.FileSystem Object` Visual Basic ' de kullanılabilir olan üyelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-108">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="c7ed7-109">Daha fazla bilgi edinmek için bkz. <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-109">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="c7ed7-110">İzlenecek yolun sonunda, ad alanından sınıfları kullanan eşdeğer bir örnek sağlanır <xref:System.IO> .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-110">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="c7ed7-111">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c7ed7-111">To create the project</span></span>  
  
1. <span data-ttu-id="c7ed7-112">**Dosya** menüsünde **Yeni proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-112">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="c7ed7-113">**Yeni Proje** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-113">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="c7ed7-114">**Yüklü şablonlar** bölmesinde, **Visual Basic** öğesini genişletin ve ardından **Windows**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-114">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="c7ed7-115">Ortadaki **Şablonlar** bölmesinde **Windows Forms uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-115">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="c7ed7-116">**Ad** kutusunda, `FileExplorer` proje adını ayarlamak için yazın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-116">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c7ed7-117">Visual Studio, projeyi **Çözüm Gezgini** ekler ve Windows Form Tasarımcısı açılır.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-117">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="c7ed7-118">Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-118">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="c7ed7-119">Denetim</span><span class="sxs-lookup"><span data-stu-id="c7ed7-119">Control</span></span>|<span data-ttu-id="c7ed7-120">Özellik</span><span class="sxs-lookup"><span data-stu-id="c7ed7-120">Property</span></span>|<span data-ttu-id="c7ed7-121">Değer</span><span class="sxs-lookup"><span data-stu-id="c7ed7-121">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="c7ed7-122">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-122">**ListBox**</span></span>|<span data-ttu-id="c7ed7-123">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-123">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="c7ed7-124">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-124">**Button**</span></span>|<span data-ttu-id="c7ed7-125">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-125">**Name**</span></span><br /><br /> <span data-ttu-id="c7ed7-126">**Metin**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-126">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="c7ed7-127">**Gözat**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-127">**Browse**</span></span>|  
    |<span data-ttu-id="c7ed7-128">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-128">**Button**</span></span>|<span data-ttu-id="c7ed7-129">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-129">**Name**</span></span><br /><br /> <span data-ttu-id="c7ed7-130">**Metin**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-130">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="c7ed7-131">**İncelemesine**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-131">**Examine**</span></span>|  
    |<span data-ttu-id="c7ed7-132">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-132">**CheckBox**</span></span>|<span data-ttu-id="c7ed7-133">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-133">**Name**</span></span><br /><br /> <span data-ttu-id="c7ed7-134">**Metin**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-134">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="c7ed7-135">**Sonuçları Kaydet**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-135">**Save Results**</span></span>|  
    |<span data-ttu-id="c7ed7-136">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-136">**FolderBrowserDialog**</span></span>|<span data-ttu-id="c7ed7-137">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c7ed7-137">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="c7ed7-138">Bir klasörü seçmek ve dosyaları bir klasöre listelemek için</span><span class="sxs-lookup"><span data-stu-id="c7ed7-138">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="c7ed7-139">`Click` `browseButton` Form üzerindeki denetime çift tıklayarak için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-139">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="c7ed7-140">Kod Düzenleyicisi açılır.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-140">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="c7ed7-141">Olay işleyicisine aşağıdaki kodu ekleyin `Click` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-141">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="c7ed7-142">`FolderBrowserDialog1.ShowDialog`Arama, **klasöre gözataaç** iletişim kutusunu açar.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-142">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="c7ed7-143">Kullanıcı **Tamam**' ı tıkladıktan sonra, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliği bir `ListFiles` sonraki adımda eklenen yöntemine bir bağımsız değişken olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-143">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="c7ed7-144">Aşağıdaki yöntemi ekleyin `ListFiles` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-144">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="c7ed7-145">Bu kod, önce **ListBox**'ı temizler.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-145">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="c7ed7-146"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>Yöntemi daha sonra dizindeki her dosya için bir dize koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-146">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="c7ed7-147">`GetFiles`Yöntemi, belirli bir düzenle eşleşen dosyaları almak için bir arama deseninin bağımsız değişkenini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-147">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="c7ed7-148">Bu örnekte, yalnızca. txt uzantılı dosyalar döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-148">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="c7ed7-149">Yöntemi tarafından döndürülen dizeler `GetFiles` daha sonra **ListBox**'a eklenir.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-149">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="c7ed7-150">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-150">Run the application.</span></span> <span data-ttu-id="c7ed7-151">**Araştır** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-151">Click the **Browse** button.</span></span> <span data-ttu-id="c7ed7-152">**Klasöre araştır** iletişim kutusunda. txt dosyalarını içeren bir klasöre gidin ve ardından klasörü seçip **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-152">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="c7ed7-153">, `ListBox` Seçilen klasördeki. txt dosyalarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-153">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="c7ed7-154">Uygulamayı çalıştırmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-154">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="c7ed7-155">Bir dosyanın özniteliklerini ve bir metin dosyasından içerik almak için</span><span class="sxs-lookup"><span data-stu-id="c7ed7-155">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="c7ed7-156">`Click` `examineButton` Form üzerindeki denetime çift tıklayarak için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-156">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="c7ed7-157">Olay işleyicisine aşağıdaki kodu ekleyin `Click` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-157">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="c7ed7-158">Kod, içinde bir öğenin seçili olduğunu doğrular `ListBox` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-158">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="c7ed7-159">Daha sonra konumundan dosya yolu girişini edinir `ListBox` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-159">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="c7ed7-160"><xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A>Yöntemi, dosyanın hala mevcut olup olmadığını denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-160">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="c7ed7-161">Dosya yolu, bir `GetTextForOutput` sonraki adımda eklenen yöntemine bir bağımsız değişken olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-161">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="c7ed7-162">Bu yöntem, dosya bilgilerini içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-162">This method returns a string that contains file information.</span></span> <span data-ttu-id="c7ed7-163">Dosya bilgileri bir **MessageBox** içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-163">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="c7ed7-164">Aşağıdaki yöntemi ekleyin `GetTextForOutput` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-164">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="c7ed7-165">Kod, <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Dosya parametrelerini almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-165">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="c7ed7-166">Dosya parametreleri bir öğesine eklenir <xref:System.Text.StringBuilder> .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-166">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="c7ed7-167"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>Yöntemi dosya içeriğini bir ile okur <xref:System.IO.StreamReader> .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-167">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="c7ed7-168">İçeriklerin ilk satırı öğesinden alınır `StreamReader` ve öğesine eklenir `StringBuilder` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-168">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="c7ed7-169">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-169">Run the application.</span></span> <span data-ttu-id="c7ed7-170">**Araştır**' a tıklayın ve. txt dosyalarını içeren bir klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-170">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="c7ed7-171">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-171">Click **OK**.</span></span>  
  
     <span data-ttu-id="c7ed7-172">İçinde bir dosya seçin `ListBox` ve ardından **İncele**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-172">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="c7ed7-173">`MessageBox`Dosya bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-173">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="c7ed7-174">Uygulamayı çalıştırmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-174">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="c7ed7-175">Günlük girdisi eklemek için</span><span class="sxs-lookup"><span data-stu-id="c7ed7-175">To add a log entry</span></span>  
  
1. <span data-ttu-id="c7ed7-176">Olay işleyicisinin sonuna aşağıdaki kodu ekleyin `examineButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-176">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="c7ed7-177">Kod, günlük dosyasını seçili dosya ile aynı dizine yerleştirmek için günlük dosyası yolunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-177">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="c7ed7-178">Günlük girişinin metni geçerli tarih ve saate, sonra da dosya bilgilerine göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-178">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="c7ed7-179"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> `append` Bağımsız değişkeni olarak ayarlanan yöntemi, `True` günlük girişini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-179">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="c7ed7-180">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-180">Run the application.</span></span> <span data-ttu-id="c7ed7-181">Bir metin dosyasına göz atın, içinde seçin, `ListBox` **Sonuçları Kaydet** onay kutusunu seçin ve ardından **İncele**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-181">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="c7ed7-182">Günlük girişinin dosyaya yazıldığını doğrulayın `log.txt` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-182">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="c7ed7-183">Uygulamayı çalıştırmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-183">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="c7ed7-184">Geçerli dizini kullanmak için</span><span class="sxs-lookup"><span data-stu-id="c7ed7-184">To use the current directory</span></span>  
  
1. <span data-ttu-id="c7ed7-185">Forma çift tıklayarak için bir olay işleyicisi oluşturun `Form1_Load` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-185">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="c7ed7-186">Olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-186">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="c7ed7-187">Bu kod, klasör tarayıcısının varsayılan dizinini geçerli dizine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-187">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="c7ed7-188">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-188">Run the application.</span></span> <span data-ttu-id="c7ed7-189">İlk kez **Araştır** ' a tıkladığınızda, **klasöre yönelik tarama** iletişim kutusu geçerli dizine açılır.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-189">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="c7ed7-190">Uygulamayı çalıştırmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-190">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="c7ed7-191">Denetimleri seçmeli olarak etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="c7ed7-191">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="c7ed7-192">Aşağıdaki yöntemi ekleyin `SetEnabled` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-192">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="c7ed7-193">`SetEnabled`Yöntemi, içinde bir öğenin seçili olmasına bağlı olarak denetimleri etkinleştirilir veya devre dışı bırakır `ListBox` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-193">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="c7ed7-194">`SelectedIndexChanged` `filesListBox` Form üzerindeki denetime çift tıklayarak için bir olay işleyicisi oluşturun `ListBox` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-194">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="c7ed7-195">`SetEnabled`Yeni olay işleyicisine bir çağrı ekleyin `filesListBox_SelectedIndexChanged` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-195">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="c7ed7-196">`SetEnabled`Olay işleyicisinin sonuna bir çağrı ekleyin `browseButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-196">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="c7ed7-197">`SetEnabled`Olay işleyicisinin sonuna bir çağrı ekleyin `Form1_Load` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-197">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="c7ed7-198">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-198">Run the application.</span></span> <span data-ttu-id="c7ed7-199">İçinde bir öğe seçilmezse **Sonuçları Kaydet** onay kutusu ve **İncele** düğmesi devre dışıdır `ListBox` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-199">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="c7ed7-200">My. Computer. FileSystem kullanarak tam örnek</span><span class="sxs-lookup"><span data-stu-id="c7ed7-200">Full example using My.Computer.FileSystem</span></span>  

 <span data-ttu-id="c7ed7-201">Aşağıda, tüm örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-201">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="c7ed7-202">System.IO kullanarak tam örnek</span><span class="sxs-lookup"><span data-stu-id="c7ed7-202">Full example using System.IO</span></span>  

 <span data-ttu-id="c7ed7-203">Aşağıdaki eşdeğer örnek, <xref:System.IO> nesneleri kullanmak yerine ad alanından sınıfları kullanır `My.Computer.FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="c7ed7-203">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="c7ed7-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7ed7-204">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="c7ed7-205">İzlenecek yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="c7ed7-205">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](walkthrough-manipulating-files-by-using-net-framework-methods.md)
