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
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme

Bu izlenecek yol, Visual Basic dosya g/ç 'nin temelleri için bir giriş sağlar. Bir dizindeki metin dosyalarını listeleyen ve inceleyen küçük bir uygulamanın nasıl oluşturulacağını açıklar. Uygulama, seçili her metin dosyası için dosya öznitelikleri ve ilk içerik satırı sağlar. Günlük dosyasına bilgi yazma seçeneği vardır.  
  
 Bu izlenecek yol, `My.Computer.FileSystem Object` Visual Basic ' de kullanılabilir olan üyelerini kullanır. Daha fazla bilgi edinmek için bkz. <xref:Microsoft.VisualBasic.FileIO.FileSystem>. İzlenecek yolun sonunda, ad alanından sınıfları kullanan eşdeğer bir örnek sağlanır <xref:System.IO> .  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1. **Dosya** menüsünde **Yeni proje**' ye tıklayın.  
  
     **Yeni Proje** iletişim kutusu görünür.  
  
2. **Yüklü şablonlar** bölmesinde, **Visual Basic**öğesini genişletin ve ardından **Windows**' a tıklayın. Ortadaki **Şablonlar** bölmesinde **Windows Forms uygulama**' ya tıklayın.  
  
3. **Ad** kutusunda, `FileExplorer` proje adını ayarlamak için yazın ve ardından **Tamam**' a tıklayın.  
  
     Visual Studio, projeyi **Çözüm Gezgini**ekler ve Windows Form Tasarımcısı açılır.  
  
4. Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.  
  
    |Denetim|Özellik|Değer|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Adı**|`filesListBox`|  
    |**Düğme**|**Adı**<br /><br /> **Metin**|`browseButton`<br /><br /> **Gözat**|  
    |**Düğme**|**Adı**<br /><br /> **Metin**|`examineButton`<br /><br /> **İncelemesine**|  
    |**CheckBox**|**Adı**<br /><br /> **Metin**|`saveCheckBox`<br /><br /> **Sonuçları Kaydet**|  
    |**FolderBrowserDialog**|**Adı**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Bir klasörü seçmek ve dosyaları bir klasöre listelemek için  
  
1. `Click` `browseButton` Form üzerindeki denetime çift tıklayarak için bir olay işleyicisi oluşturun. Kod Düzenleyicisi açılır.  
  
2. Olay işleyicisine aşağıdaki kodu ekleyin `Click` .  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     `FolderBrowserDialog1.ShowDialog`Arama, **klasöre gözataaç** iletişim kutusunu açar. Kullanıcı **Tamam**' ı tıkladıktan sonra, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliği bir `ListFiles` sonraki adımda eklenen yöntemine bir bağımsız değişken olarak gönderilir.  
  
3. Aşağıdaki yöntemi ekleyin `ListFiles` .  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     Bu kod, önce **ListBox**'ı temizler.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>Yöntemi daha sonra dizindeki her dosya için bir dize koleksiyonu alır. `GetFiles`Yöntemi, belirli bir düzenle eşleşen dosyaları almak için bir arama deseninin bağımsız değişkenini kabul eder. Bu örnekte, yalnızca. txt uzantılı dosyalar döndürülür.  
  
     Yöntemi tarafından döndürülen dizeler `GetFiles` daha sonra **ListBox**'a eklenir.  
  
4. Uygulamayı çalıştırın. **Araştır** düğmesine tıklayın. **Klasöre araştır** iletişim kutusunda. txt dosyalarını içeren bir klasöre gidin ve ardından klasörü seçip **Tamam**' a tıklayın.  
  
     , `ListBox` Seçilen klasördeki. txt dosyalarının bir listesini içerir.  
  
5. Uygulamayı çalıştırmayı durdurun.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Bir dosyanın özniteliklerini ve bir metin dosyasından içerik almak için  
  
1. `Click` `examineButton` Form üzerindeki denetime çift tıklayarak için bir olay işleyicisi oluşturun.  
  
2. Olay işleyicisine aşağıdaki kodu ekleyin `Click` .  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     Kod, içinde bir öğenin seçili olduğunu doğrular `ListBox` . Daha sonra konumundan dosya yolu girişini edinir `ListBox` . <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A>Yöntemi, dosyanın hala mevcut olup olmadığını denetlemek için kullanılır.  
  
     Dosya yolu, bir `GetTextForOutput` sonraki adımda eklenen yöntemine bir bağımsız değişken olarak gönderilir. Bu yöntem, dosya bilgilerini içeren bir dize döndürür. Dosya bilgileri bir **MessageBox**içinde görüntülenir.  
  
3. Aşağıdaki yöntemi ekleyin `GetTextForOutput` .  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     Kod, <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Dosya parametrelerini almak için yöntemini kullanır. Dosya parametreleri bir öğesine eklenir <xref:System.Text.StringBuilder> .  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>Yöntemi dosya içeriğini bir ile okur <xref:System.IO.StreamReader> . İçeriklerin ilk satırı öğesinden alınır `StreamReader` ve öğesine eklenir `StringBuilder` .  
  
4. Uygulamayı çalıştırın. **Araştır**' a tıklayın ve. txt dosyalarını içeren bir klasöre gidin. **Tamam**'a tıklayın.  
  
     İçinde bir dosya seçin `ListBox` ve ardından **İncele**' ye tıklayın. `MessageBox`Dosya bilgilerini gösterir.  
  
5. Uygulamayı çalıştırmayı durdurun.  
  
### <a name="to-add-a-log-entry"></a>Günlük girdisi eklemek için  
  
1. Olay işleyicisinin sonuna aşağıdaki kodu ekleyin `examineButton_Click` .  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     Kod, günlük dosyasını seçili dosya ile aynı dizine yerleştirmek için günlük dosyası yolunu ayarlar. Günlük girişinin metni geçerli tarih ve saate, sonra da dosya bilgilerine göre ayarlanır.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> `append` Bağımsız değişkeni olarak ayarlanan yöntemi, `True` günlük girişini oluşturmak için kullanılır.  
  
2. Uygulamayı çalıştırın. Bir metin dosyasına göz atın, içinde seçin, `ListBox` **Sonuçları Kaydet** onay kutusunu seçin ve ardından **İncele**' ye tıklayın. Günlük girişinin dosyaya yazıldığını doğrulayın `log.txt` .  
  
3. Uygulamayı çalıştırmayı durdurun.  
  
### <a name="to-use-the-current-directory"></a>Geçerli dizini kullanmak için  
  
1. Forma çift tıklayarak için bir olay işleyicisi oluşturun `Form1_Load` .  
  
2. Olay işleyicisine aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     Bu kod, klasör tarayıcısının varsayılan dizinini geçerli dizine ayarlar.  
  
3. Uygulamayı çalıştırın. İlk kez **Araştır** ' a tıkladığınızda, **klasöre yönelik tarama** iletişim kutusu geçerli dizine açılır.  
  
4. Uygulamayı çalıştırmayı durdurun.  
  
### <a name="to-selectively-enable-controls"></a>Denetimleri seçmeli olarak etkinleştirmek için  
  
1. Aşağıdaki yöntemi ekleyin `SetEnabled` .  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     `SetEnabled`Yöntemi, içinde bir öğenin seçili olmasına bağlı olarak denetimleri etkinleştirilir veya devre dışı bırakır `ListBox` .  
  
2. `SelectedIndexChanged` `filesListBox` Form üzerindeki denetime çift tıklayarak için bir olay işleyicisi oluşturun `ListBox` .  
  
3. `SetEnabled`Yeni olay işleyicisine bir çağrı ekleyin `filesListBox_SelectedIndexChanged` .  
  
4. `SetEnabled`Olay işleyicisinin sonuna bir çağrı ekleyin `browseButton_Click` .  
  
5. `SetEnabled`Olay işleyicisinin sonuna bir çağrı ekleyin `Form1_Load` .  
  
6. Uygulamayı çalıştırın. İçinde bir öğe seçilmezse **Sonuçları Kaydet** onay kutusu ve **İncele** düğmesi devre dışıdır `ListBox` .  
  
## <a name="full-example-using-mycomputerfilesystem"></a>My. Computer. FileSystem kullanarak tam örnek  

 Aşağıda, tüm örnek verilmiştir.  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a>System.IO kullanarak tam örnek  

 Aşağıdaki eşdeğer örnek, <xref:System.IO> nesneleri kullanmak yerine ad alanından sınıfları kullanır `My.Computer.FileSystem` .  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [İzlenecek yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme](walkthrough-manipulating-files-by-using-net-framework-methods.md)
