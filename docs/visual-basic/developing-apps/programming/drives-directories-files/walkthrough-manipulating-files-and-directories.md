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
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme

Bu gözden geçirme, Visual Basic'teki Dosya G/Ç'nin temellerine giriş sağlar. Metin dosyalarını listeleyen ve bir dizinde inceleyen küçük bir uygulamanın nasıl oluşturulacağını açıklar. Seçili her metin dosyası için uygulama, dosya özniteliklerini ve ilk içerik satırını sağlar. Günlük dosyasına bilgi yazma seçeneği vardır.  
  
 Bu `My.Computer.FileSystem Object`walkthrough, Visual Basic'te bulunan , üyeleri kullanır. Daha fazla bilgi edinmek için bkz. <xref:Microsoft.VisualBasic.FileIO.FileSystem>. İzlemenin sonunda, <xref:System.IO> ad alanından sınıfları kullanan eşdeğer bir örnek sağlanır.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1. **Dosya** menüsünde **Yeni Proje'yi**tıklatın.  
  
     **Yeni Proje** iletişim kutusu görünür.  
  
2. Yüklü **Şablonlar** bölmesinde Visual **Basic'i**genişletin ve ardından **Windows'u**tıklatın. Ortadaki **Şablonlar** bölmesinde Windows **Forms Application'ı**tıklatın.  
  
3. **Ad** kutusuna, `FileExplorer` proje adını ayarlamak için yazın ve sonra **Tamam'ı**tıklatın.  
  
     Visual **Studio, Solution Explorer'a**projeyi ekler ve Windows Forms Designer açılır.  
  
4. Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.  
  
    |Denetim|Özellik|Değer|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Adı**|`filesListBox`|  
    |**Düğme**|**Adı**<br /><br /> **Metin**|`browseButton`<br /><br /> **Gözat**|  
    |**Düğme**|**Adı**<br /><br /> **Metin**|`examineButton`<br /><br /> **Incelemek**|  
    |**CheckBox**|**Adı**<br /><br /> **Metin**|`saveCheckBox`<br /><br /> **Sonuçları Kaydet**|  
    |**Folderbrowserdialog**|**Adı**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Bir klasör seçmek ve klasördeki dosyaları listelemek için  
  
1. Formdaki `Click` denetimi çift `browseButton` tıklatarak için bir olay işleyicisi oluşturun. Kod Düzenleyicisi açılır.  
  
2. Olay işleyicisine `Click` aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     Arama, `FolderBrowserDialog1.ShowDialog` **Klasör İçin Gözat** iletişim kutusunu açar. Kullanıcı **Tamam'ı**tıklattıktan sonra, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özellik bir `ListFiles` sonraki adımda eklenen yönteme bağımsız değişken olarak gönderilir.  
  
3. Aşağıdaki `ListFiles` yöntemi ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     Bu kod önce **ListBox'ı**temizler.  
  
     Yöntem <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> daha sonra dizindeki her dosya için bir tane olan bir dize koleksiyonu alır. Yöntem, `GetFiles` belirli bir desenle eşleşen dosyaları almak için bir arama deseni bağımsız değişkeni kabul eder. Bu örnekte, yalnızca .txt uzantısı olan dosyalar döndürülür.  
  
     `GetFiles` Yöntemle döndürülen dizeleri daha sonra **ListBox**eklenir.  
  
4. Uygulamayı çalıştırın. **Gözat** düğmesini tıklatın. Klasör **Için Gözat** iletişim kutusunda ,.txt dosyaları içeren bir klasöre göz atın ve sonra klasörü seçin ve **Tamam'ı**tıklatın.  
  
     Seçili `ListBox` klasörde .txt dosyalarının bir listesini içerir.  
  
5. Uygulamayı çalıştırmayı durdurun.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Bir dosyanın özniteliklerini ve metin dosyasından içerik elde etmek için  
  
1. Formdaki `Click` denetimi çift `examineButton` tıklatarak için bir olay işleyicisi oluşturun.  
  
2. Olay işleyicisine `Click` aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     Kod, bir öğenin `ListBox`seçilir olduğunu doğrular. Daha sonra dosya yolu girişini `ListBox`. Yöntem, <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> dosyanın hala var olup olmadığını denetlemek için kullanılır.  
  
     Dosya yolu, bir sonraki adımda eklenen `GetTextForOutput` yönteme bağımsız değişken olarak gönderilir. Bu yöntem, dosya bilgilerini içeren bir dize döndürür. Dosya bilgileri **MessageBox'ta**görünür.  
  
3. Aşağıdaki `GetTextForOutput` yöntemi ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     Kod, dosya <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> parametrelerini elde etmek için yöntemi kullanır. Dosya parametreleri bir <xref:System.Text.StringBuilder>.  
  
     Yöntem, <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> dosya içeriğini bir <xref:System.IO.StreamReader>. İçeriğin ilk satırı elde edilir `StreamReader` ve eklenir `StringBuilder`.  
  
4. Uygulamayı çalıştırın. **Gözat'ı**tıklatın ve .txt dosyaları içeren bir klasöre göz atın. **Tamam**'a tıklayın.  
  
     `ListBox`'de bir dosya seçin ve sonra **İncele'yi**tıklatın. A `MessageBox` dosya bilgilerini gösterir.  
  
5. Uygulamayı çalıştırmayı durdurun.  
  
### <a name="to-add-a-log-entry"></a>Günlük girişi eklemek için  
  
1. `examineButton_Click` Olay işleyicisinin sonuna aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     Kod, günlük dosyasını seçili dosyayla aynı dizine koymak için günlük dosyası yolunu ayarlar. Günlük girişinin metni, dosya bilgilerinin ardından geçerli tarih ve saate ayarlanır.  
  
     Yöntem, <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> `append` bağımsız değişken olarak `True`ayarlanmış , günlük girişi oluşturmak için kullanılır.  
  
2. Uygulamayı çalıştırın. Bir metin dosyasına göz atın, `ListBox`sonuçları **kaydet** onay kutusunu seçin ve sonra **İncele'yi**tıklatın. Günlük girişinin `log.txt` dosyaya yazıldığını doğrulayın.  
  
3. Uygulamayı çalıştırmayı durdurun.  
  
### <a name="to-use-the-current-directory"></a>Geçerli dizini kullanmak için  
  
1. Formu çift tıklatarak `Form1_Load` için bir olay işleyicisi oluşturun.  
  
2. Olay işleyicisine aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     Bu kod, klasör tarayıcısının varsayılan dizinini geçerli dizine ayarlar.  
  
3. Uygulamayı çalıştırın. İlk kez **Gözat'ı** tıklattığınızda, **Klasör İçin Gözat** iletişim kutusu geçerli dizine açılır.  
  
4. Uygulamayı çalıştırmayı durdurun.  
  
### <a name="to-selectively-enable-controls"></a>Denetimleri seçişekilde etkinleştirmek için  
  
1. Aşağıdaki `SetEnabled` yöntemi ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     Yöntem, `SetEnabled` `ListBox`bir öğenin seçilip seçilmediğine bağlı olarak denetimleri etkinleştiriyor veya devre dışı salar.  
  
2. Formdaki `SelectedIndexChanged` `ListBox` denetimi çift `filesListBox` tıklatarak için bir olay işleyicisi oluşturun.  
  
3. Yeni `filesListBox_SelectedIndexChanged` olay `SetEnabled` işleyicisine bir çağrı ekleyin.  
  
4. Olay işleyicisinin sonunda bir `SetEnabled` çağrı ekleyin. `browseButton_Click`  
  
5. Olay işleyicisinin sonunda bir `SetEnabled` çağrı ekleyin. `Form1_Load`  
  
6. Uygulamayı çalıştırın. **Sonuçları Kaydet** onay kutusunu ve 'de bir öğe seçilmemişse **İncele** düğmesi devre dışı `ListBox`bırakılır.  
  
## <a name="full-example-using-mycomputerfilesystem"></a>My.Computer.FileSystem kullanarak tam örnek  

 Aşağıdaki tam bir örnektir.  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a>System.IO kullanarak tam örnek  

 Aşağıdaki eşdeğer örneknesneleri kullanmak <xref:System.IO> `My.Computer.FileSystem` yerine ad alanından sınıflar kullanır.  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
