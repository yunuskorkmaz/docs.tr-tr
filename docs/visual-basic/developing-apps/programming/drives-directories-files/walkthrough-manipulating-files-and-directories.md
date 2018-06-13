---
title: Dosyalar ve dizinler Visual Basic'te düzenleme
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
ms.openlocfilehash: ab1c119d2c5cd9bfa0ff725774144bc65817cad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592515"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme
Bu kılavuz, Visual Basic'te dosya g/ç ile ilgili temel bilgileri tanıtılmaktadır. Listeler ve metin dosyaları bir dizinde inceler küçük bir uygulamasının nasıl oluşturulacağını açıklar. Her seçili metin dosyası için dosya özniteliklerini ve içeriğindeki birinci satırın uygulama sağlar. Bilgilerini bir günlük dosyasına yazmak için bir seçenek yoktur.  
  
 Bu kılavuzda üyeleri kullanılır `My.Computer.FileSystem Object`, Visual Basic'te kullanılabilir olduğu. Daha fazla bilgi edinmek için bkz. <xref:Microsoft.VisualBasic.FileIO.FileSystem>. İzlenecek yol sonunda sınıflardan kullanan bir eşdeğer örnek sağlanır <xref:System.IO> ad alanı.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde tıklatın **yeni proje**.  
  
     **Yeni proje** iletişim kutusu görüntülenir.  
  
2.  İçinde **yüklü şablonlar** bölmesini genişletin **Visual Basic**ve ardından **Windows**. İçinde **şablonları** Orta tıklatın bölmesinde **Windows Forms uygulaması**.  
  
3.  İçinde **adı** kutusuna `FileExplorer` proje adını ayarlayın ve ardından **Tamam**.  
  
     Visual Studio projeye ekler **Çözüm Gezgini**, ve Windows Forms Tasarımcısı'nı açar.  
  
4.  Denetimleri aşağıdaki tabloda forma ekleme ve bunların özelliklerini karşılık gelen değerler ayarlayın.  
  
    |Denetim|Özellik|Değer|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Ad**|`filesListBox`|  
    |**Düğme**|**Ad**<br /><br /> **Metin**|`browseButton`<br /><br /> **Gözat**|  
    |**Düğme**|**Ad**<br /><br /> **Metin**|`examineButton`<br /><br /> **İnceleyin**|  
    |**CheckBox**|**Ad**<br /><br /> **Metin**|`saveCheckBox`<br /><br /> **Sonuçları Kaydet**|  
    |**FolderBrowserDialog**|**Ad**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Bir klasör seçin ve bir klasördeki dosyaları listelemek için  
  
1.  Oluşturma bir `Click` için olay işleyicisini `browseButton` formdaki denetim çift tıklatarak. Kod Düzenleyicisi açılır.  
  
2.  Aşağıdaki kodu ekleyin `Click` olay işleyicisi.  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]  
  
     `FolderBrowserDialog1.ShowDialog` Çağrısı açılır **klasöre Gözat** iletişim kutusu. Sonra kullanıcı **Tamam**, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliği için bağımsız değişken olarak gönderilir `ListFiles` sonraki adımda eklenen yöntemi.  
  
3.  Aşağıdakileri ekleyin `ListFiles` yöntemi.  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]  
  
     Bu kod ilk temizler **ListBox**.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> Yöntemi sonra dizeler, bir dizinin her dosya için bir koleksiyonunu alır. `GetFiles` Yöntemi, belirli bir desenle eşleşen dosyaları almak için bir arama deseni bağımsız değişkeni kabul eder. Bu örnekte, yalnızca .txt uzantılı dosyalar döndürülür.  
  
     Tarafından döndürülen dize `GetFiles` yöntemi eklenir **ListBox**.  
  
4.  Uygulamayı çalıştırın. Tıklatın **Gözat** düğmesi. İçinde **klasöre Gözat** iletişim kutusunda, Gözat .txt dosyaları içeren bir klasörü klasörü seçin ve tıklatın **Tamam**.  
  
     `ListBox` .Txt dosyaları seçili klasörde listesini içerir.  
  
5.  Uygulama çalışmayı durdurur.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Bir dosyanın özniteliklerini elde edin ve bir metin dosyasından içerik  
  
1.  Oluşturma bir `Click` için olay işleyicisini `examineButton` formdaki denetim çift tıklatarak.  
  
2.  Aşağıdaki kodu ekleyin `Click` olay işleyicisi.  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]  
  
     Kod bir öğe seçili olduğunu doğrular `ListBox`. Ardından dosya yolu girişinden elde `ListBox`. <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> Yöntemi, dosyanın hala var olup olmadığını denetlemek için kullanılır.  
  
     Dosya yolu için bağımsız değişken olarak gönderilen `GetTextForOutput` sonraki adımda eklenen yöntemi. Bu yöntem, dosya bilgileri içeren bir dize döndürür. Dosya bilgileri görünür bir **MessageBox**.  
  
3.  Aşağıdakileri ekleyin `GetTextForOutput` yöntemi.  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]  
  
     Kod kullanan <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> dosya parametrelerini elde etmek için yöntemi. Dosya parametrelerini eklenen bir <xref:System.Text.StringBuilder>.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> Yöntemi okur içine dosya içeriğini bir <xref:System.IO.StreamReader>. İlk satırı içeriği ile elde edilen `StreamReader` ve eklenir `StringBuilder`.  
  
4.  Uygulamayı çalıştırın. Tıklatın **Gözat**ve .txt dosyaları içeren bir klasöre göz atın. **Tamam**'ı tıklatın.  
  
     Bir dosya seçin `ListBox`ve ardından **inceleyin**. A `MessageBox` dosya bilgilerini gösterir.  
  
5.  Uygulama çalışmayı durdurur.  
  
### <a name="to-add-a-log-entry"></a>Bir günlük girdisi eklemek için  
  
1.  Sonuna aşağıdaki kodu ekleyin `examineButton_Click` olay işleyicisi.  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]  
  
     Günlük dosyası seçilen dosyanın aynı dizine koyun için günlük dosyası yolu ayarlar. Günlük girişi metnin geçerli tarih ve saate göre dosya bilgileri ve ardından ayarlanır.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Yöntemi ile `append` değişkenini `True`, günlük girişi oluşturmak için kullanılır.  
  
2.  Uygulamayı çalıştırın. Bir metin dosyasına göz atın, seçin `ListBox`seçin **Sonuçları Kaydet** onay kutusunu işaretleyin ve ardından **inceleyin**. Günlük girişi için yazıldığından emin olun `log.txt` dosya.  
  
3.  Uygulama çalışmayı durdurur.  
  
### <a name="to-use-the-current-directory"></a>Geçerli dizin kullanmak için  
  
1.  İçin bir olay işleyicisi oluşturun `Form1_Load` formun çift tıklatarak.  
  
2.  Olay işleyicisi için aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]  
  
     Bu kod varsayılan dizini klasörü tarayıcının geçerli dizine ayarlar.  
  
3.  Uygulamayı çalıştırın. Tıkladığınızda **Gözat** ilk kez **klasöre Gözat** geçerli dizine iletişim kutusu açılır.  
  
4.  Uygulama çalışmayı durdurur.  
  
### <a name="to-selectively-enable-controls"></a>Denetimleri seçmeli olarak etkinleştirmek için  
  
1.  Aşağıdakileri ekleyin `SetEnabled` yöntemi.  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]  
  
     `SetEnabled` Yöntemi etkinleştirir veya öğeyi olup seçildiyse bağlı olarak denetimleri devre dışı bırakan `ListBox`.  
  
2.  Oluşturma bir `SelectedIndexChanged` için olay işleyicisini `filesListBox` çift tıklatarak `ListBox` form üzerinde denetim.  
  
3.  Bir çağrı ekleyin `SetEnabled` yeni `filesListBox_SelectedIndexChanged` olay işleyicisi.  
  
4.  Bir çağrı ekleyin `SetEnabled` sonunda `browseButton_Click` olay işleyicisi.  
  
5.  Bir çağrı ekleyin `SetEnabled` sonunda `Form1_Load` olay işleyicisi.  
  
6.  Uygulamayı çalıştırın. **Sonuçları Kaydet** onay kutusunu ve **inceleyin** içinde bir öğe seçili değilse düğmesi devre dışı `ListBox`.  
  
## <a name="full-example-using-mycomputerfilesystem"></a>My.Computer.FileSystem kullanarak tam örnek  
 Tam bir örnek verilmiştir.  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]  
  
## <a name="full-example-using-systemio"></a>System.IO kullanarak tam örnek  
 Aşağıdaki eşdeğer örnek sınıflardan kullanır <xref:System.IO> kullanmak yerine ad alanı `My.Computer.FileSystem` nesneleri.  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>  
 [İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
