---
title: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme
ms.date: 07/20/2015
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
ms.openlocfilehash: 9abb87f3f6cdefefef29eb37c2c2d4d15155e93d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406657"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme (Visual Basic)

Bu izlenecek yol, sınıfını kullanarak bir dosyayı nasıl açıp okuyacağınızı <xref:System.IO.StreamReader> , bir dosyaya erişilmekte olup olmadığını kontrol etmek için, sınıfın örneğiyle okunan bir dosya içinde bir dizeyi aramak <xref:System.IO.StreamReader> ve sınıfını kullanarak bir dosyaya yazmak için nasıl kullanılacağını gösterir <xref:System.IO.StreamWriter> .

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a>Uygulama oluşturma

Visual Studio 'Yu başlatın ve kullanıcının belirlenen dosyaya yazmak için kullanabileceği bir form oluşturarak projeye başlayın.

### <a name="to-create-the-project"></a>Proje oluşturmak için

1. **Dosya** menüsünde **Yeni proje**' yi seçin.

2. **Yeni proje** bölmesinde **Windows uygulaması**' na tıklayın.

3. **Ad** kutusuna yazın `MyDiary` ve **Tamam**' a tıklayın.

     Visual Studio, projeyi **Çözüm Gezgini**ekler ve **Windows Form Tasarımcısı** açılır.

4. Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.

|**Nesne**|**Özellikler**|**Değer**|
|---|---|---|
|<xref:System.Windows.Forms.Button>|**Adı**<br /><br /> **Metin**|`Submit`<br /><br /> **Giriş Gönder**|
|<xref:System.Windows.Forms.Button>|**Adı**<br /><br /> **Metin**|`Clear`<br /><br /> **Girişi temizle**|
|<xref:System.Windows.Forms.TextBox>|**Adı**<br /><br /> **Metin**<br /><br /> **Multiline**|`Entry`<br /><br /> **Lütfen bir ad girin.**<br /><br /> `False`|

## <a name="writing-to-the-file"></a>Dosyaya yazma

Uygulama aracılığıyla bir dosyaya yazma yeteneğini eklemek için <xref:System.IO.StreamWriter> sınıfını kullanın. <xref:System.IO.StreamWriter>, belirli bir kodlamada karakter çıkışı için tasarlanmıştır, ancak <xref:System.IO.Stream> Sınıf bayt girişi ve çıkışı için tasarlanmıştır. <xref:System.IO.StreamWriter>Standart metin dosyasına bilgi satırları yazmak için kullanın. Sınıfı hakkında daha fazla bilgi için <xref:System.IO.StreamWriter> bkz <xref:System.IO.StreamWriter> ..

### <a name="to-add-writing-functionality"></a>Yazma işlevselliği eklemek için

1. **Görünüm** menüsünde **kod** ' yi seçerek kod düzenleyicisini açın.

2. Uygulama ad alanına başvurduğundan, <xref:System.IO> form için Sınıf bildiriminden önce, ' nin başladığı, kodunuzun en başına aşağıdaki deyimlerini ekleyin `Public Class Form1` .

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     Dosyaya yazmadan önce bir sınıfın örneğini oluşturmanız gerekir <xref:System.IO.StreamWriter> .

3. **Görünüm** menüsünden, **Windows Form Tasarımcısı**geri dönmek için **Tasarımcı** ' yı seçin. Düğmeye çift tıklayarak `Submit` <xref:System.Windows.Forms.Control.Click> düğme için bir olay işleyicisi oluşturun ve ardından aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> Visual Studio tümleşik geliştirme ortamı (IDE), kod düzenleyicisine dönerek ekleme noktasını kodu eklemeniz gereken olay işleyicisine göre konumlandıracaktır.

1. Dosyaya yazmak için, <xref:System.IO.StreamWriter.Write%2A> sınıfının yöntemini kullanın <xref:System.IO.StreamWriter> . Hemen sonra aşağıdaki kodu ekleyin `Dim fw As StreamWriter` . Zaten mevcut değilse oluşturulacak bir özel durumun, dosyanın bulunamaması durumunda oluşturulmadığından endişelenmeniz gerekmez.

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. Kullanıcının aşağıdaki kodu doğrudan ekleyerek boş bir giriş gönderebildiğinden emin olun `Dim ReadString As String` .

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. Bu bir Diary olduğundan, Kullanıcı her girişe bir tarih atamak isteyeceksiniz. `fw = New StreamWriter("C:\MyDiary.txt", True)`Değişkeni geçerli tarihe ayarlamak için aşağıdaki kodu ekleyin `Today` .

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. Son olarak, silmek için kod ekleyin <xref:System.Windows.Forms.TextBox> . Düğmenin olayına aşağıdaki kodu ekleyin `Clear` <xref:System.Windows.Forms.Control.Click> .

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a>Diary 'e görüntüleme özellikleri ekleme

Bu bölümde, içinde en son girişi görüntüleyen bir özellik eklersiniz `DisplayEntry` <xref:System.Windows.Forms.TextBox> . Ayrıca <xref:System.Windows.Forms.ComboBox> , çeşitli girdileri görüntüleyen ve bir kullanıcının içinde görüntülenecek girişi seçebileceğiniz bir de ekleyebilirsiniz `DisplayEntry` <xref:System.Windows.Forms.TextBox> . Sınıfının bir örneği <xref:System.IO.StreamReader> öğesinden okur `MyDiary.txt` . Sınıfı gibi <xref:System.IO.StreamWriter> , <xref:System.IO.StreamReader> metin dosyalarıyla kullanılmak üzere tasarlanmıştır.

İzlenecek yolun bu bölümü için, aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.

|Denetim|Özellikler|Değerler|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|**Adı**<br /><br /> **Visible**<br /><br /> **Boyut**<br /><br /> **Multiline**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|**Adı**<br /><br /> **Metin**|`Display`<br /><br /> **Görüntüleme**|
|<xref:System.Windows.Forms.Button>|**Adı**<br /><br /> **Metin**|`GetEntries`<br /><br /> **Girişleri Al**|
|<xref:System.Windows.Forms.ComboBox>|**Adı**<br /><br /> **Metin**<br /><br /> **Etkin**|`PickEntries`<br /><br /> **Bir giriş seçin**<br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a>Birleşik giriş kutusunu doldurmak için

1. , Kullanıcının `PickEntries` <xref:System.Windows.Forms.ComboBox> her girişi gönderdiği tarihleri göstermek için kullanılır, böylece Kullanıcı belirli bir tarihten itibaren bir giriş seçebilir. Düğmeye bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun `GetEntries` ve aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin ve ardından **Girişleri Al**' a tıklayın. Giriş tarihlerini göstermek için içindeki açılan oka tıklayın <xref:System.Windows.Forms.ComboBox> .

### <a name="to-choose-and-display-individual-entries"></a>Tek tek girdileri seçme ve görüntüleme

1. <xref:System.Windows.Forms.Control.Click>Düğme için bir olay işleyicisi oluşturun `Display` ve aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin ve ardından bir giriş gönderebilirsiniz. **Girişleri Al**' a tıklayın, öğesinden bir giriş seçin <xref:System.Windows.Forms.ComboBox> ve ardından **görüntüle**' ye tıklayın. Seçili girdinin içeriği içinde görüntülenir `DisplayEntry` <xref:System.Windows.Forms.TextBox> .

## <a name="enabling-users-to-delete-or-modify-entries"></a>Kullanıcıların girdileri silmesini veya değiştirmesini sağlama

Son olarak, kullanıcıların ve düğmelerini kullanarak bir girişi silmesine veya değiştirmesine izin vermek için ek işlevler `DeleteEntry` ekleyebilirsiniz `EditEntry` . Bir giriş görüntülenmediği takdirde her iki düğme de devre dışı kalır.

Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.

|Denetim|Özellikler|Değerler|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|**Adı**<br /><br /> **Metin**<br /><br /> **Etkin**|`DeleteEntry`<br /><br /> **Girişi Sil**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Adı**<br /><br /> **Metin**<br /><br /> **Etkin**|`EditEntry`<br /><br /> **Girişi Düzenle**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Adı**<br /><br /> **Metin**<br /><br /> **Etkin**|`SubmitEdit`<br /><br /> **Düzenleme gönder**<br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a>Girişlerin silinmesini ve değiştirilmesini etkinleştirmek için

1. Aşağıdaki kodu `Display` düğmenin <xref:System.Windows.Forms.Control.Click> olayına, sonrasında ekleyin `DisplayEntry.Text = ReadString` .

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. <xref:System.Windows.Forms.Control.Click>Düğme için bir olay işleyicisi oluşturun `DeleteEntry` ve aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. Bir Kullanıcı bir girişi görüntülediğinde, `EditEntry` düğme etkin hale gelir. Sonrasında düğme olayına aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> `Display` `DisplayEntry.Text = ReadString` .

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. <xref:System.Windows.Forms.Control.Click>Düğme için bir olay işleyicisi oluşturun `EditEntry` ve aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. <xref:System.Windows.Forms.Control.Click>Düğme için bir olay işleyicisi oluşturun `SubmitEdit` ve aşağıdaki kodu ekleyin

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin. **Girişleri Al**' a tıklayın, bir giriş seçin ve ardından **görüntüle**' ye tıklayın. Giriş öğesinde görüntülenir `DisplayEntry` <xref:System.Windows.Forms.TextBox> . **Girişi Düzenle**' ye tıklayın. Giriş öğesinde görüntülenir `Entry` <xref:System.Windows.Forms.TextBox> . İçindeki girişi düzenleyin `Entry` <xref:System.Windows.Forms.TextBox> ve **düzenleme gönder**' e tıklayın. `MyDiary.txt`Düzeltmeyi onaylamak için dosyayı açın. Şimdi bir girdi seçip **girişi Sil**' e tıklayın. <xref:System.Windows.Forms.MessageBox>İstek onayı tamamlandığında **Tamam**' a tıklayın. Uygulamayı kapatın ve `MyDiary.txt` silme işlemini onaylamak için açın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [İzlenecek Yollar](../../../walkthroughs.md)
