---
title: 'İzlenecek Yol: Görsel Devralmayı Gösterme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: b17de01c4a5e89051393aa3c6bb2d0079535dbf6
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703692"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>İzlenecek Yol: Görsel Devralmayı Gösterme
Görsel devralma temel form üzerinde denetimleri görmek için ve yeni denetimler eklemek için sağlar. Bu izlenecek yolda temel bir form oluşturun ve bir sınıf kitaplığı derleyin. Bu sınıf kitaplığı, başka bir projeye içeri aktarmak ve temel formundan devralan yeni bir form oluşturun. Bu kılavuz boyunca, öğreneceksiniz nasıl yapılır:  
  
-   Taban form içeren bir sınıf kitaplığı projesi oluşturun.  
  
-   Bir düğme türetilmiş sınıflar temel formun özelliklerini değiştirebilirsiniz ekleyin.  
  
-   Taban formun devralanlar tarafından değiştirilemez bir düğme ekleyin.  
  
-   Devralınan form içeren bir proje oluşturma `BaseForm`.  
  
 Sonuç olarak, bu izlenecek yol, devralınmış bir form üzerinde özel ve korumalı denetimler arasındaki farkı gösterilecektir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
> [!CAUTION]
>  Tüm denetimleri, temel bir formdan görsel devralmayı destekler. Bu kılavuzda açıklanan senaryo aşağıdaki denetimleri desteklemez:  
>   
>  <xref:System.Windows.Forms.WebBrowser>  
>   
>  <xref:System.Windows.Forms.ToolStrip>  
>   
>  <xref:System.Windows.Forms.ToolStripPanel>  
>   
>  <xref:System.Windows.Forms.TableLayoutPanel>  
>   
>  <xref:System.Windows.Forms.FlowLayoutPanel>  
>   
>  <xref:System.Windows.Forms.DataGridView>  
>   
>  Bu devralınan form denetimlerinde her zaman kullandığınız değiştiriciler bağımsız olarak salt okunurdur (`private`, `protected`, veya `public`).  
  
## <a name="scenario-steps"></a>Senaryo adımları  
 İlk adım, bir taban formunu oluşturmaktır.  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a>Taban form içeren bir sınıf kitaplığı projesi oluşturmak için  
  
1.  Gelen **dosya** menüsünde seçin **yeni**, ardından **proje** açmak için **yeni proje** iletişim kutusu.  
  
2.  Adlı bir Windows Forms uygulaması oluşturma `BaseFormLibrary`.  
  
3.  Standart bir Windows Forms uygulaması yerine bir sınıf kitaplığı oluşturmak için **Çözüm Gezgini**, sağ **BaseFormLibrary** proje düğümünü ve ardından **özellikleri**.  
  
4.  Proje özelliklerini değiştirmek **çıkış türü** gelen **Windows uygulama** için **sınıf kitaplığı**.  
  
5.  Gelen **dosya** menüsünde seçin **Tümünü Kaydet** dosya ve proje varsayılan konuma kaydedin.  
  
 Sonraki iki yordam temel forma düğme ekleyin. Görsel devralma göstermek için düğmeler farklı erişim düzeyleri ayarlayarak erişmenizi kendi `Modifiers` özellikleri.  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a>Taban formun devralanlar değiştirebileceğiniz bir düğme eklemek için  
  
1.  Açık **Form1** Tasarımcısı'nda.  
  
2.  Üzerinde **tüm Windows Formları** sekmesinde **araç kutusu**, çift **düğmesi** forma bir düğme eklemek için. Fare getirin ve düğmeyi yeniden boyutlandırmak için kullanın.  
  
3.  Özellikler penceresinde düğmenin aşağıdaki özellikleri ayarlayın:  
  
    -   Ayarlama **metin** özelliğini **Say Hello**.  
  
    -   Ayarlama **(ad)** özelliğini **btnProtected**.  
  
    -   Ayarlama **değiştiriciler** özelliğini **korumalı**. Bu devralınan formlar için mümkün kılar **Form1** özelliklerini değiştirmek için **btnProtected**.  
  
4.  Çift **Say Hello** için bir olay işleyicisi eklemek için Ekle düğmesine **tıklayın** olay.  
  
5.  Olay işleyicisine aşağıdaki kod satırını ekleyin:  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>Taban formun devralanlar tarafından değiştirilemez bir düğme eklemek için  
  
1.  Tıklayarak Tasarım görünümüne geç **Form1.vb [Design], Form1.cs [Design] veya [Design] Form1.jsl** Kod Düzenleyicisi'ni yukarıda veya F7'ye basarak sekmesi.  
  
2.  İkinci bir düğme ekleyin ve özelliklerini aşağıdaki gibi ayarlayın:  
  
    -   Ayarlama **metin** özelliğini **Say güle güle**.  
  
    -   Ayarlama **(ad)** özelliğini **btnPrivate**.  
  
    -   Ayarlama **değiştiriciler** özelliğini **özel**. Bu, devralınan formlar olanaksız kılar **Form1** özelliklerini değiştirmek için **btnPrivate**.  
  
3.  Çift **Say güle güle** için bir olay işleyicisi eklemek için Ekle düğmesine **tıklayın** olay. Aşağıdaki kod satırını olay yordamda yerleştirin:  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  Gelen **derleme** menüsünde seçin **derleme BaseForm Kitaplığı** sınıf kitaplığı oluşturmak için.  
  
     Kitaplığı oluşturulduktan sonra yeni oluşturduğunuz formundan devralan yeni bir proje oluşturabilirsiniz.  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>Taban form devralan bir formu içeren bir proje oluşturmak için  
  
1.  Gelen **dosya** menüsünde seçin **Ekle** ardından **yeni proje** açmak için **Yeni Proje Ekle** iletişim kutusu.  
  
2.  Adlı bir Windows Forms uygulaması oluşturma `InheritanceTest`.  
  
#### <a name="to-add-an-inherited-form"></a>Devralınmış bir form eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **InheritanceTest** proje, select **Ekle**ve ardından **yeni öğe**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Windows Forms** kategorisi (kategori listesi varsa) ve ardından **devralınan Form** şablonu.  
  
3.  Varsayılan adı bırakın `Form2` ve ardından **Ekle**.  
  
4.  İçinde **devralma Seçici** iletişim kutusunda **Form1** gelen **BaseFormLibrary** devralır ve form olarak proje **Tamam** .  
  
     Bu, bir formda oluşturur **InheritanceTest** biçiminde türetildiği proje **BaseFormLibrary**.  
  
5.  Devralınan form açın (**Form2**) zaten açık değilse, çift tıklayarak tasarımcıda.  
  
     Tasarımcıda bir sembol devralınan düğmeleri sahip (![VisualBasicInheritanceSymbol ekran](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) devralınan belirten kendi üst köşedeki.  
  
6.  Seçin **Say Hello** düğmesine tıklayın ve yeniden boyutlandırma tutamaçları gözlemleyin. Bu düğme korunduğu devralanlar taşıyabilir, yeniden boyutlandırabilir, kendi başlığını değiştirme ve diğer değişiklikleri yapın.  
  
7.  Özel seçin **Say güle güle** düğmesi ve yeniden boyutlandırma tutamaçları yok dikkat edin. Buna ek olarak **özellikleri** penceresinde bu düğmenin özelliklerini gri bunlar değiştirilemez belirtmek için.  
  
8.  Visual C# kullanıyorsanız:  
  
    1.  İçinde **Çözüm Gezgini**, sağ **Form1** içinde **InheritanceTest** proje ve ardından **Sil**. Görüntülenen ileti kutusunda **Tamam** silme işlemini onaylamak için.  
  
    2.  Program.cs dosyasını açın ve satırını `Application.Run(new Form1());` için `Application.Run(new Form2());`.  
  
9. İçinde **Çözüm Gezgini**, sağ **InheritanceTest** seçin ve proje **başlangıç projesi olarak ayarla**.  
  
10. İçinde **Çözüm Gezgini**, sağ **InheritanceTest** seçin ve proje **özellikleri**.  
  
11. İçinde **InheritanceTest** özellik sayfalarını **Başlangıç nesnesi** devralınan form olması (**Form2**).  
  
12. Uygulamayı çalıştırmak ve devralınan form davranışını gözlemlemek için F5 tuşuna basın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Kullanıcı denetimleri için devralma kadar aynı şekilde çalışır. Yeni bir sınıf kitaplığı projesi açın ve bir kullanıcı denetimi ekleyin. Bağlı denetimler üzerindeki yerleştirin ve projeyi derleyin. Başka bir yeni sınıf kitaplığı projesi açın ve derlenmiş sınıf kitaplığına bir başvuru ekleyin. Ayrıca, devralınan bir denetim ekleyerek deneyin (aracılığıyla **yeni öğe ekleme** iletişim kutusu) projeye ve kullanarak **devralma Seçici**. Bir kullanıcı denetimi eklemek ve değiştirmek `Inherits` (`:` Visual C#) deyimi. Daha fazla bilgi için [nasıl yapılır: Windows formlarını devralma](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows Forms’u Devralma](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [Windows Forms Görsel Devralma](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
