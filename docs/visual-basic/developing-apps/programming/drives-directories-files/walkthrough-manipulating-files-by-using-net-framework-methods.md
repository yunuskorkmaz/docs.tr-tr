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
ms.openlocfilehash: 02cdbcc59e8817ff4ec06c2f78f835cad77b10f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333777"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme (Visual Basic)

Bu gözden geçirme, sınıfı kullanarak bir dosyanın <xref:System.IO.StreamReader> nasıl açılacağını ve okunduğunu, dosyaya erişilip erişilip erişilenin <xref:System.IO.StreamReader> ilerde denetlendiğini, sınıfın <xref:System.IO.StreamWriter> bir örneğiyle okunan bir dosya içinde bir dize aramasını ve sınıfı kullanarak bir dosyaya nasıl yazılacağını gösterir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a>Uygulamayı Oluşturma

Visual Studio'yu başlatın ve kullanıcının belirlenen dosyaya yazmak için kullanabileceği bir form oluşturarak projeye başlayın.

### <a name="to-create-the-project"></a>Proje oluşturmak için

1. **Dosya** menüsünde **Yeni Proje'yi**seçin.

2. Yeni **Proje** bölmesinde **Windows Uygulaması'nı**tıklatın.

3. **Ad** kutusuna `MyDiary` yazın ve **Tamam'ı**tıklatın.

     Visual **Studio, Solution Explorer'a**projeyi ekler ve **Windows Forms Designer** açılır.

4. Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.

|**Nesne**|**Özellikler**|**Değer**|
|---|---|---|
|<xref:System.Windows.Forms.Button>|**Adı**<br /><br /> **Metin**|`Submit`<br /><br /> **Giriş Gönder**|
|<xref:System.Windows.Forms.Button>|**Adı**<br /><br /> **Metin**|`Clear`<br /><br /> **Girişi Temizle**|
|<xref:System.Windows.Forms.TextBox>|**Adı**<br /><br /> **Metin**<br /><br /> **Multiline**|`Entry`<br /><br /> **Lütfen bir şey girin.**<br /><br /> `False`|

## <a name="writing-to-the-file"></a>Dosyaya Yazma

Uygulama üzerinden bir dosyaya yazma özelliğini eklemek <xref:System.IO.StreamWriter> için sınıfı kullanın. <xref:System.IO.StreamWriter>sınıf bayt giriş ve çıktı için tasarlanmış <xref:System.IO.Stream> ise, belirli bir kodlama karakter çıktısı için tasarlanmıştır. Standart <xref:System.IO.StreamWriter> bir metin dosyasına bilgi satırları yazmak için kullanın. <xref:System.IO.StreamWriter> Sınıf hakkında daha fazla <xref:System.IO.StreamWriter>bilgi için bkz.

### <a name="to-add-writing-functionality"></a>Yazma işlevselliği eklemek için

1. **Görünüm** menüsünden Kod Düzenleyicisi'ni açmak için **Kod'u** seçin.

2. Uygulama <xref:System.IO> ad alanına başvurulduğundan, başlayan `Public Class Form1`formun sınıf bildiriminden önce kodunuzun başında aşağıdaki ifadeleri ekleyin.

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     Dosyaya yazmadan önce bir <xref:System.IO.StreamWriter> sınıfın örneğini oluşturmanız gerekir.

3. **Görünüm** **menüsünden, Windows Forms Designer'a**dönmek için **Designer'ı** seçin. Düğme için `Submit` olay <xref:System.Windows.Forms.Control.Click> işleyicisi oluşturmak için düğmeyi çift tıklatın ve ardından aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> Visual Studio Entegre Geliştirme Ortamı (IDE) Kod Düzenleyicisi'ne geri döner ve ekleme noktasını kod eklemeniz gereken olay işleyicisi içinde konumlandıracaktır.

1. Dosyaya yazmak için sınıfın <xref:System.IO.StreamWriter.Write%2A> yöntemini <xref:System.IO.StreamWriter> kullanın. Aşağıdaki kodu doğrudan `Dim fw As StreamWriter`sonra ekleyin. Dosya bulunmazsa bir özel durum atılacağından endişelenmenize gerek yoktur, çünkü dosya zaten yoksa oluşturulur.

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. Kullanıcının aşağıdaki kodu doğrudan sonra `Dim ReadString As String`ekleyerek boş bir giriş gönderemeyeceğinden emin olun.

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. Bu bir günlük olduğundan, kullanıcı her girişe bir tarih atamak isteyecektir. Değişkeni `Today` geçerli tarihe `fw = New StreamWriter("C:\MyDiary.txt", True)` ayarlamak için aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. Son olarak, temizlemek <xref:System.Windows.Forms.TextBox>için kod ekleyin. Düğmenin `Clear` <xref:System.Windows.Forms.Control.Click> olayına aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a>Günlüğe Görüntü Özellikleri Ekleme

Bu bölümde, `DisplayEntry` <xref:System.Windows.Forms.TextBox>en son girişi görüntüleyen bir özellik eklersiniz. Ayrıca, çeşitli <xref:System.Windows.Forms.ComboBox> girişleri görüntüleyen ve kullanıcının `DisplayEntry` <xref:System.Windows.Forms.TextBox>'de görüntülemek üzere bir giriş seçebileceği bir giriş de ekleyebilirsiniz. <xref:System.IO.StreamReader> Sınıfın bir örneği `MyDiary.txt`. <xref:System.IO.StreamWriter> Sınıf gibi, <xref:System.IO.StreamReader> metin dosyaları ile kullanılmak üzere tasarlanmıştır.

İzlenin bu bölümü için, aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.

|Denetim|Özellikler|Değerler|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|**Adı**<br /><br /> **Visible**<br /><br /> **Boyut**<br /><br /> **Multiline**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|**Adı**<br /><br /> **Metin**|`Display`<br /><br /> **Görüntüleme**|
|<xref:System.Windows.Forms.Button>|**Adı**<br /><br /> **Metin**|`GetEntries`<br /><br /> **Girişleri Al**|
|<xref:System.Windows.Forms.ComboBox>|**Adı**<br /><br /> **Metin**<br /><br /> **Etkin**|`PickEntries`<br /><br /> **Giriş Seçin**<br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a>Açılan kutuyu doldurmak için

1. Kullanıcının `PickEntries` <xref:System.Windows.Forms.ComboBox> her girişi gönderdiği tarihleri görüntülemek için kullanılır, böylece kullanıcı belirli bir tarihten bir giriş seçebilir. Düğmeye <xref:System.Windows.Forms.Control.Click> bir olay işleyicisi `GetEntries` oluşturun ve aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. Kodunuzu test etmek için uygulamayı derlemek için F5 tuşuna basın ve ardından **Girişleri Al'ı**tıklatın. Giriş tarihlerini görüntülemek <xref:System.Windows.Forms.ComboBox> için açılır oka tıklayın.

### <a name="to-choose-and-display-individual-entries"></a>Tek tek girişleri seçmek ve görüntülemek için

1. Düğme <xref:System.Windows.Forms.Control.Click> için bir olay `Display` işleyicisi oluşturun ve aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. Kodunuzu test etmek için, uygulamayı derlemek için F5 tuşuna basın ve ardından bir giriş gönderin. **Girişleri Al'ı**tıklatın, <xref:System.Windows.Forms.ComboBox>giriş seçin ve ardından **Görüntüle'yi**tıklatın. Seçili girişin `DisplayEntry` <xref:System.Windows.Forms.TextBox>içeriği .

## <a name="enabling-users-to-delete-or-modify-entries"></a>Kullanıcıların Girişleri Silmesini veya Değiştirmesini Etkinleştirme

Son olarak, kullanıcıların kullanarak ve `DeleteEntry` `EditEntry` düğmeleri kullanarak bir girişi silmesine veya değiştirmesine olanak tanıyan ek işlevler ekleyebilirsiniz. Giriş görüntülenmedikçe her iki düğme de devre dışı kalır.

Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.

|Denetim|Özellikler|Değerler|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|**Adı**<br /><br /> **Metin**<br /><br /> **Etkin**|`DeleteEntry`<br /><br /> **Girişi Sil**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Adı**<br /><br /> **Metin**<br /><br /> **Etkin**|`EditEntry`<br /><br /> **Girişi Edit**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Adı**<br /><br /> **Metin**<br /><br /> **Etkin**|`SubmitEdit`<br /><br /> **Edit Gönder**<br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a>Girişlerin silinmesini ve değiştirilmesini etkinleştirmek için

1. Aşağıdaki kodu düğmenin `Display` <xref:System.Windows.Forms.Control.Click> olayına ekleyin, `DisplayEntry.Text = ReadString`sonra .

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. Düğme <xref:System.Windows.Forms.Control.Click> için bir olay `DeleteEntry` işleyicisi oluşturun ve aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. Bir kullanıcı bir giriş `EditEntry` görüntülediğinde, düğme etkin olur. 'den sonra <xref:System.Windows.Forms.Control.Click> `Display` `DisplayEntry.Text = ReadString`düğmeye aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. Düğme <xref:System.Windows.Forms.Control.Click> için bir olay `EditEntry` işleyicisi oluşturun ve aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. Düğme <xref:System.Windows.Forms.Control.Click> için bir olay `SubmitEdit` işleyicisi oluşturun ve aşağıdaki kodu ekleyin

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

Kodunuzu test etmek için uygulamayı derlemek için F5 tuşuna basın. **Girişleri Al'ı**tıklatın, bir giriş seçin ve ardından **Görüntüle'yi**tıklatın. Giriş. `DisplayEntry` <xref:System.Windows.Forms.TextBox> **Girişi Edit'i**tıklatın. Giriş. `Entry` <xref:System.Windows.Forms.TextBox> Girişi `Entry` <xref:System.Windows.Forms.TextBox> edin ve **Edit'i gönder'e**tıklayın. Düzeltmenizi `MyDiary.txt` onaylamak için dosyayı açın. Şimdi bir giriş seçin ve **Girişi Sil'i**tıklatın. İstekte <xref:System.Windows.Forms.MessageBox> onay, **Tamam'ı**tıklatın. Uygulamayı kapatın ve `MyDiary.txt` silme işlemini onaylamak için açın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [Kılavuz](../../../../visual-basic/walkthroughs.md)
