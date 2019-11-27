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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333802"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme

Bu izlenecek yol, Visual Basic dosya g/ç 'nin temelleri için bir giriş sağlar. Bir dizindeki metin dosyalarını listeleyen ve inceleyen küçük bir uygulamanın nasıl oluşturulacağını açıklar. Uygulama, seçili her metin dosyası için dosya öznitelikleri ve ilk içerik satırı sağlar. Günlük dosyasına bilgi yazma seçeneği vardır.  
  
 Bu izlenecek yol, Visual Basic kullanılabilen `My.Computer.FileSystem Object`üyelerini kullanır. Daha fazla bilgi edinmek için bkz. <xref:Microsoft.VisualBasic.FileIO.FileSystem>. İzlenecek yolun sonunda, <xref:System.IO> ad alanından sınıfları kullanan eşdeğer bir örnek verilmiştir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1. **Dosya** menüsünde **Yeni proje**' ye tıklayın.  
  
     **Yeni proje** iletişim kutusu görüntülenir.  
  
2. **Yüklü şablonlar** bölmesinde, **Visual Basic**öğesini genişletin ve ardından **Windows**' a tıklayın. Ortadaki **Şablonlar** bölmesinde **Windows Forms uygulama**' ya tıklayın.  
  
3. **Ad** kutusuna, proje adını ayarlamak için `FileExplorer` yazın ve ardından **Tamam**' a tıklayın.  
  
     Visual Studio, projeyi **Çözüm Gezgini**ekler ve Windows Form Tasarımcısı açılır.  
  
4. Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.  
  
    |Denetim|Özellik|Değer|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Ad**|`filesListBox`|  
    |**Düğme**|**Ad**<br /><br /> **Metin**|`browseButton`<br /><br /> **Ata**|  
    |**Düğme**|**Ad**<br /><br /> **Metin**|`examineButton`<br /><br /> **İncelemesine**|  
    |**CheckBox**|**Ad**<br /><br /> **Metin**|`saveCheckBox`<br /><br /> **Sonuçları Kaydet**|  
    |**FolderBrowserDialog**|**Ad**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Bir klasörü seçmek ve dosyaları bir klasöre listelemek için  
  
1. Formdaki denetime çift tıklayarak `browseButton` için `Click` olay işleyicisi oluşturun. Kod Düzenleyicisi açılır.  
  
2. `Click` olay işleyicisine aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     `FolderBrowserDialog1.ShowDialog` çağrısı **klasöre Gözataaç** iletişim kutusunu açar. Kullanıcı **Tamam**' ı tıkladıktan sonra, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliği bir sonraki adımda eklenen `ListFiles` yöntemine bir bağımsız değişken olarak gönderilir.  
  
3. Aşağıdaki `ListFiles` yöntemi ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     Bu kod, önce **ListBox**'ı temizler.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> yöntemi daha sonra dizindeki her dosya için bir dize koleksiyonu alır. `GetFiles` yöntemi, belirli bir düzenle eşleşen dosyaları almak için bir arama deseninin bağımsız değişkenini kabul eder. Bu örnekte, yalnızca. txt uzantılı dosyalar döndürülür.  
  
     `GetFiles` yöntemi tarafından döndürülen dizeler daha sonra **ListBox**'a eklenir.  
  
4. Uygulamayı çalıştırın. **Araştır** düğmesine tıklayın. **Klasöre araştır** iletişim kutusunda. txt dosyalarını içeren bir klasöre gidin ve ardından klasörü seçip **Tamam**' a tıklayın.  
  
     `ListBox` seçili klasördeki. txt dosyalarının bir listesini içerir.  
  
5. Uygulamayı çalıştırmayı durdurun.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Bir dosyanın özniteliklerini ve bir metin dosyasından içerik almak için  
  
1. Formdaki denetime çift tıklayarak `examineButton` için `Click` olay işleyicisi oluşturun.  
  
2. `Click` olay işleyicisine aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     Kod, `ListBox`bir öğenin seçili olduğunu doğrular. Ardından `ListBox`dosya yolu girişini edinir. <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> yöntemi, dosyanın hala mevcut olup olmadığını denetlemek için kullanılır.  
  
     Dosya yolu, bir sonraki adımda eklenen `GetTextForOutput` yöntemine bir bağımsız değişken olarak gönderilir. Bu yöntem, dosya bilgilerini içeren bir dize döndürür. Dosya bilgileri bir **MessageBox**içinde görüntülenir.  
  
3. Aşağıdaki `GetTextForOutput` yöntemi ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     Kod, dosya parametrelerini almak için <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> yöntemini kullanır. Dosya parametreleri <xref:System.Text.StringBuilder>eklenir.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> yöntemi dosya içeriğini bir <xref:System.IO.StreamReader>okur. İçeriğin ilk satırı `StreamReader` alınır ve `StringBuilder`eklenir.  
  
4. Uygulamayı çalıştırın. **Araştır**' a tıklayın ve. txt dosyalarını içeren bir klasöre gidin. **Tamam**a tıklayın.  
  
     `ListBox`bir dosya seçin ve ardından **İncele**' ye tıklayın. `MessageBox` dosya bilgilerini gösterir.  
  
5. Uygulamayı çalıştırmayı durdurun.  
  
### <a name="to-add-a-log-entry"></a>Günlük girdisi eklemek için  
  
1. `examineButton_Click` olay işleyicisinin sonuna aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     Kod, günlük dosyasını seçili dosya ile aynı dizine yerleştirmek için günlük dosyası yolunu ayarlar. Günlük girişinin metni geçerli tarih ve saate, sonra da dosya bilgilerine göre ayarlanır.  
  
     `append` bağımsız değişkeni `True`olarak ayarlanan <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> yöntemi, günlük girişini oluşturmak için kullanılır.  
  
2. Uygulamayı çalıştırın. Bir metin dosyasına göz atın, `ListBox`seçin, **Sonuçları Kaydet** onay kutusunu seçin ve ardından **İncele**' ye tıklayın. Günlük girişinin `log.txt` dosyasına yazıldığını doğrulayın.  
  
3. Uygulamayı çalıştırmayı durdurun.  
  
### <a name="to-use-the-current-directory"></a>Geçerli dizini kullanmak için  
  
1. Forma çift tıklayarak `Form1_Load` için bir olay işleyicisi oluşturun.  
  
2. Olay işleyicisine aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     Bu kod, klasör tarayıcısının varsayılan dizinini geçerli dizine ayarlar.  
  
3. Uygulamayı çalıştırın. İlk kez **Araştır** ' a tıkladığınızda, **klasöre yönelik tarama** iletişim kutusu geçerli dizine açılır.  
  
4. Uygulamayı çalıştırmayı durdurun.  
  
### <a name="to-selectively-enable-controls"></a>Denetimleri seçmeli olarak etkinleştirmek için  
  
1. Aşağıdaki `SetEnabled` yöntemi ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     `SetEnabled` yöntemi, `ListBox`bir öğenin seçili olmasına bağlı olarak denetimleri devre dışı bırakır veya devre dışı bırakır.  
  
2. Formundaki `ListBox` denetimine çift tıklayarak `filesListBox` için `SelectedIndexChanged` olay işleyicisi oluşturun.  
  
3. Yeni `filesListBox_SelectedIndexChanged` olay işleyicisine `SetEnabled` bir çağrı ekleyin.  
  
4. `browseButton_Click` olay işleyicisinin sonundaki `SetEnabled` bir çağrı ekleyin.  
  
5. `Form1_Load` olay işleyicisinin sonundaki `SetEnabled` bir çağrı ekleyin.  
  
6. Uygulamayı çalıştırın. `ListBox`bir öğe seçilmezse **Sonuçları Kaydet** onay kutusu ve **İncele** düğmesi devre dışıdır.  
  
## <a name="full-example-using-mycomputerfilesystem"></a>My. Computer. FileSystem kullanarak tam örnek  

 Aşağıda, tüm örnek verilmiştir.  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a>System.IO kullanarak tam örnek  

 Aşağıdaki eşdeğer örnek, `My.Computer.FileSystem` nesneleri kullanmak yerine <xref:System.IO> ad alanındaki sınıfları kullanır.  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
