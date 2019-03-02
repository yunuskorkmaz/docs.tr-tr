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
ms.openlocfilehash: cb7fda617118c01e6ee54339bcc3ff8f8b342450
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202450"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme
Bu izlenecek yol, Visual Basic'te dosya g/ç temelleri tanıtılmaktadır. Bu listeler ve bir dizinde metin dosyaları inceler, küçük bir uygulamanın nasıl oluşturulacağını açıklar. Her seçili metin dosyası için dosya öznitelikleri ve içeriğindeki birinci satırın uygulama sağlar. Bir günlük dosyasına yazmak için bir seçenek yoktur.  
  
 Bu izlenecek yolda üyeleri kullanan `My.Computer.FileSystem Object`, Visual Basic'te kullanılabilir olduğu. Daha fazla bilgi edinmek için bkz. <xref:Microsoft.VisualBasic.FileIO.FileSystem>. İzlenecek yol sonunda sınıflarını kullanan eşdeğer bir örnek sağlanır <xref:System.IO> ad alanı.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Üzerinde **dosya** menüsünü tıklatın **yeni proje**.  
  
     **Yeni Proje** iletişim kutusu görünür.  
  
2.  İçinde **yüklü şablonlar** bölmesini genişletin **Visual Basic**ve ardından **Windows**. İçinde **şablonları** Orta tıklayarak bölmesinde **Windows Forms uygulaması**.  
  
3.  İçinde **adı** kutusuna `FileExplorer` proje adını ayarlayın ve ardından **Tamam**.  
  
     Visual Studio projeyi ekler **Çözüm Gezgini**, ve Windows Forms Tasarımcısı açılır.  
  
4.  Denetimler aşağıdaki tabloda forma eklemek ve karşılık gelen özelliklerini ayarlayın.  
  
    |Denetim|Özellik|Değer|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Ad**|`filesListBox`|  
    |**Düğme**|**Ad**<br /><br /> **Metin**|`browseButton`<br /><br /> **Göz atma**|  
    |**Düğme**|**Ad**<br /><br /> **Metin**|`examineButton`<br /><br /> **İnceleyin**|  
    |**CheckBox**|**Ad**<br /><br /> **Metin**|`saveCheckBox`<br /><br /> **Sonuçları Kaydet**|  
    |**FolderBrowserDialog**|**Ad**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Bir klasör seçin ve bir klasördeki dosyaları Listele  
  
1.  Oluşturma bir `Click` için olay işleyicisi `browseButton` formdaki bir denetime çift tıklayın. Kod Düzenleyicisi açılır.  
  
2.  Aşağıdaki kodu ekleyin `Click` olay işleyicisi.  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     `FolderBrowserDialog1.ShowDialog` Çağrı açılır **klasöre Gözat** iletişim kutusu. Sonra kullanıcı **Tamam**, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliği gönderilen bağımsız değişken olarak `ListFiles` sonraki adımda eklenen yöntemi.  
  
3.  Aşağıdaki `ListFiles` yöntemi.  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     Bu kod önce temizler **ListBox**.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> Yöntemi ardından dizeleri, dizindeki her dosya için bir koleksiyonunu alır. `GetFiles` Yöntemi belirli bir desenle eşleşen dosyaları almak için bir arama deseni bağımsız değişkeni kabul eder. Bu örnekte, yalnızca uzantısı .txt sahip dosyalar döndürülür.  
  
     Tarafından döndürülen dizeler `GetFiles` yöntemi ardından eklenir **ListBox**.  
  
4.  Uygulamayı çalıştırın. Tıklayın **Gözat** düğmesi. İçinde **klasöre Gözat** iletişim kutusu, .txt dosyaları içeren bir klasörü klasörü seçin ve tıklayın **Tamam**.  
  
     `ListBox` Seçilen klasördeki .txt dosyalarının bir listesini içerir.  
  
5.  Uygulamanın çalışmayı durdurur.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Bir dosyanın özniteliklerini alma ve bir metin dosyasından içerik  
  
1.  Oluşturma bir `Click` için olay işleyicisi `examineButton` formdaki bir denetime çift tıklayın.  
  
2.  Aşağıdaki kodu ekleyin `Click` olay işleyicisi.  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     Kod içinde bir öğe seçildiğinde doğrular `ListBox`. Ardından dosya yolu girdisinden elde `ListBox`. <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> Yöntemi, dosyanın hala varolup olmadığını denetlemek için kullanılır.  
  
     Dosya yolu için bağımsız değişken olarak gönderilen `GetTextForOutput` sonraki adımda eklenen yöntemi. Bu yöntem dosya bilgileri içeren bir dize döndürür. Dosya bilgileri görünür bir **MessageBox**.  
  
3.  Aşağıdaki `GetTextForOutput` yöntemi.  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     Kod <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> dosya parametrelerini elde etmek için yöntemi. Dosya parametrelerini eklenen bir <xref:System.Text.StringBuilder>.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> Yöntemi okur dosya içeriğine bir <xref:System.IO.StreamReader>. İlk satırının içeriğini elde edilen `StreamReader` ve eklendiğinden `StringBuilder`.  
  
4.  Uygulamayı çalıştırın. Tıklayın **Gözat**, .txt dosyaları içeren bir klasöre göz atın. **Tamam**'ı tıklatın.  
  
     Bir dosya seçin `ListBox`ve ardından **inceleyin**. A `MessageBox` dosya bilgilerini gösterir.  
  
5.  Uygulamanın çalışmayı durdurur.  
  
### <a name="to-add-a-log-entry"></a>Günlük girdisi eklemek için  
  
1.  Sonuna aşağıdaki kodu ekleyin `examineButton_Click` olay işleyicisi.  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     Bu kod, seçilen dosya ile aynı dizine günlük dosyasına koymak için günlük dosyası yolu ayarlar. Geçerli tarih ve saate dosya bilgilerin günlük girişinin metnini ayarlayın.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Yöntemi ile `append` değişkenini `True`, günlüğü girdisi oluşturmak için kullanılır.  
  
2.  Uygulamayı çalıştırın. Bir metin dosyasına göz atın, onu seçip `ListBox`seçin **Sonuçları Kaydet** onay kutusunu işaretleyin ve ardından **inceleyin**. Günlük girişi için yazıldığını doğrulayın `log.txt` dosya.  
  
3.  Uygulamanın çalışmayı durdurur.  
  
### <a name="to-use-the-current-directory"></a>Geçerli dizin kullanmak için  
  
1.  İçin bir olay işleyicisi oluşturun `Form1_Load` formun çift tıklayın.  
  
2.  Olay işleyicisine aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     Bu kod, geçerli dizine klasör tarayıcı varsayılan dizinini ayarlar.  
  
3.  Uygulamayı çalıştırın. Tıkladığınızda **Gözat** ilk kez **klasöre Gözat** geçerli dizine iletişim kutusu açılır.  
  
4.  Uygulamanın çalışmayı durdurur.  
  
### <a name="to-selectively-enable-controls"></a>Seçmeli olarak denetimleri etkinleştirmek için  
  
1.  Aşağıdaki `SetEnabled` yöntemi.  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     `SetEnabled` Yöntemi etkinleştirir veya bir öğe olup olmadığını seçildiğinde bağlı olarak denetimleri devre dışı bırakan `ListBox`.  
  
2.  Oluşturma bir `SelectedIndexChanged` için olay işleyicisi `filesListBox` çift tıklayarak `ListBox` form denetimi.  
  
3.  Bir çağrı ekleyin `SetEnabled` yeni `filesListBox_SelectedIndexChanged` olay işleyicisi.  
  
4.  Bir çağrı ekleyin `SetEnabled` sonunda `browseButton_Click` olay işleyicisi.  
  
5.  Bir çağrı ekleyin `SetEnabled` sonunda `Form1_Load` olay işleyicisi.  
  
6.  Uygulamayı çalıştırın. **Sonuçları Kaydet** onay kutusunu ve **inceleyin** içinde bir öğe seçili değilse düğmesi devre dışı `ListBox`.  
  
## <a name="full-example-using-mycomputerfilesystem"></a>My.Computer.FileSystem kullanarak tam örnek  
 Tam bir örnek aşağıda verilmiştir.  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a>System.IO kullanarak tam örnek  
 Aşağıdaki eşdeğer sınıflardan örnekte <xref:System.IO> kullanmak yerine ad alanı `My.Computer.FileSystem` nesneleri.  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [İzlenecek yol: .NET Framework yöntemlerini kullanarak dosyaları düzenleme](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
