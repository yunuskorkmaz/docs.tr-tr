---
title: 'İzlenecek Yol: Görsel Devralmayı Gösterme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e76ddcb33980db1a6d1b6e602c1b71da60b53381
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>İzlenecek Yol: Görsel Devralmayı Gösterme
Görsel devralma temel form üzerinde denetimleri görmek için ve yeni denetim eklemek için sağlar. Bu kılavuzda temel form oluşturma ve bir sınıf kitaplığı'na derleyin. Bu sınıf kitaplığı başka bir projeye almak ve temel formundan devralan yeni bir form oluşturun. Bu gözden geçirme sırasında öğreneceksiniz nasıl yapılır:  
  
-   Bir taban formunu içeren bir sınıf kitaplığı projesi oluşturun.  
  
-   Türetilmiş sınıflar temel formunun özelliklere sahip bir düğme değiştirebilirsiniz ekleyin.  
  
-   Taban form Notlar tarafından değiştirilemez bir düğme ekleyin.  
  
-   Öğesinden devralınan bir form içeren bir proje oluşturun `BaseForm`.  
  
 Sonuç olarak, bu kılavuzda devralınan bir form üzerinde özel ve korumalı denetimler arasındaki fark gösterilmektedir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!CAUTION]
>  Tüm denetimler temel bir formdan görsel devralma destekler. Bu kılavuzda açıklanan senaryo aşağıdaki denetimleri desteklenmez:  
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
>  Bu devralınan formdaki denetimlerin her zaman kullandığınız değiştiricileri bağımsız olarak salt okunurdur (`private`, `protected`, veya `public`).  
  
## <a name="scenario-steps"></a>Senaryo adımları  
 İlk adım, temel form oluşturmaktır.  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a>Bir taban formunu içeren bir sınıf kitaplığı proje oluşturmak için  
  
1.  Gelen **dosya** menüsünde seçin **yeni**ve ardından **proje** açmak için **yeni proje** iletişim kutusu.  
  
2.  Adlı bir Windows Forms uygulaması oluşturma `BaseFormLibrary`.  
  
3.  Standart bir Windows Forms uygulaması yerine bir sınıf kitaplığı oluşturmak için **Çözüm Gezgini**, sağ **BaseFormLibrary** proje düğümünü ve ardından **özellikleri**.  
  
4.  Proje özelliklerini değiştirme **çıktı türü** gelen **Windows uygulaması** için **sınıf kitaplığı**.  
  
5.  Gelen **dosya** menüsünde seçin **Tümünü Kaydet** proje ve dosyaları varsayılan konuma kaydetmek için.  
  
 Sonraki iki yordam, taban formun düğmeleri ekleyin. Görsel devralma göstermek için düğmeler farklı erişim düzeyleri ayarlayarak erişmenizi sağlayan kendi `Modifiers` özellikleri.  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a>Taban formun Notlar değiştirebilirsiniz bir düğme eklemek için  
  
1.  Açık **Form1** Tasarımcısı'nda.  
  
2.  Üzerinde **tüm Windows Formları** sekmesinde **araç**, çift **düğmesi** forma bir düğme eklemek için. Fare getirin ve düğmeye yeniden boyutlandırma için kullanın.  
  
3.  Özellikler penceresinde düğmesinin aşağıdaki özellikleri ayarlayın:  
  
    -   Ayarlama **metin** özelliğine **Say Hello**.  
  
    -   Ayarlama **(ad)** özelliğine **btnProtected**.  
  
    -   Ayarlama**değiştiricileri** özelliğine **korumalı**. Bu devralınan formlar için mümkün kılar **Form1** özelliklerini değiştirmek için **btnProtected**.  
  
4.  Çift **Say Hello** bir olay işleyicisi için Ekle düğmesini **tıklatın** olay.  
  
5.  Aşağıdaki kod satırını olay işleyicisine ekleyin:  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>Taban form Notlar tarafından değiştirilemez bir düğme eklemek için  
  
1.  Tıklatarak Tasarım görünümüne geçiş **Form1.vb [tasarım], Form1.cs [Design] veya [tasarım] Form1.jsl** Kod düzenleyicisinde yukarıda ya da F7 tuşlarına basarak sekme.  
  
2.  İkinci düğme ekleme ve özelliklerini şu şekilde ayarlayın:  
  
    -   Ayarlama **metin** özelliğine **Say güle güle**.  
  
    -   Ayarlama **(ad)** özelliğine **btnPrivate**.  
  
    -   Ayarlama **değiştiricileri** özelliğine **özel**. Bu devralınan formlar mümkün kılar **Form1** özelliklerini değiştirmek için **btnPrivate**.  
  
3.  Çift **Say güle güle** bir olay işleyicisi için Ekle düğmesini **tıklatın** olay. Aşağıdaki kod satırını olay yordamında koyun:  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  Gelen **yapı** menüsünde seçin **yapı BaseForm Kitaplığı** sınıf kitaplığı oluşturmak için.  
  
     Kitaplığı oluşturulduktan sonra yeni oluşturduğunuz formundan devralan yeni bir proje oluşturabilirsiniz.  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>Temel formundan devralan bir form içeren bir proje oluşturmak için  
  
1.  Gelen **dosya** menüsünde seçin **Ekle** ve ardından **yeni proje** açmak için **Yeni Proje Ekle** iletişim kutusu.  
  
2.  Adlı bir Windows Forms uygulaması oluşturma `InheritanceTest`.  
  
#### <a name="to-add-an-inherited-form"></a>Devralınan bir form eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **InheritanceTest** proje, select **Ekle**ve ardından**yeni öğe**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Windows Forms** (kategori listesi varsa) kategori ve ardından **devralınan Form** şablonu.  
  
3.  Varsayılan adı bırakın `Form2` ve ardından **Ekle**.  
  
4.  İçinde **devralma Seçici** iletişim kutusunda **Form1** gelen **BaseFormLibrary** projesi devralınmalıdır tıklatıp form olarak **Tamam** .  
  
     Bu bir form oluşturur **InheritanceTest** biçiminde türetilen proje **BaseFormLibrary**.  
  
5.  Devralınan formunu açın (**Form2**) zaten açık değilse, çift tıklatarak Tasarımcısı'nda.  
  
     Tasarımcısı'nda bir simge devralınan düğmeleri sahip (![VisualBasicInheritanceSymbol ekran görüntüsü](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) bunlar devralınır gösteren kendi üst köşedeki.  
  
6.  Seçin **Say Hello** düğmesine tıklayın ve yeniden boyutlandırma inceleyin. Bu düğme korunduğu için Notlar taşıyabilir, yeniden boyutlandırabilir, resim yazısını değiştirmek ve başka değişiklikler yapmayın.  
  
7.  Özel seçin **Say güle güle** düğmesi ve yeniden boyutlandırma yok dikkat edin. Buna ek olarak **özellikleri** penceresinde, bu düğmenin özelliklerini gri bunlar değiştirilemez belirtmek için.  
  
8.  Visual C# kullanıyorsanız:  
  
    1.  İçinde **Çözüm Gezgini**, sağ **Form1** içinde **InheritanceTest** proje ve ardından **silmek**. Görüntülenen ileti kutusunda tıklatın **Tamam** silme işlemini onaylayın.  
  
    2.  Program.cs dosyasını açın ve satırı değiştirin `Application.Run(new Form1());` için `Application.Run(new Form2());`.  
  
9. İçinde **Çözüm Gezgini**, sağ **InheritanceTest** proje ve seçin **başlangıç projesi olarak ayarla**.  
  
10. İçinde **Çözüm Gezgini**, sağ **InheritanceTest** proje ve seçin **özellikleri**.  
  
11. İçinde **InheritanceTest** özellik sayfaları, ayarlamak **Başlangıç nesnesi** devralınan biçiminde için (**Form2**).  
  
12. Uygulamayı çalıştırın ve devralınan form davranışını izlemek için F5 tuşuna basın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Kullanıcı denetimleri için devralma kadar aynı şekilde çalışır. Yeni bir sınıf kitaplığı projesi açın ve bir kullanıcı denetimi ekle. Bağlı denetimler üzerindeki yerleştirin ve projeyi derleyin. Başka bir yeni sınıf kitaplığı proje açın ve derlenmiş sınıf kitaplığına bir başvuru ekleyin. Ayrıca, devralınan bir denetim eklemeyi deneyin (aracılığıyla **yeni öğeler eklemek** iletişim kutusu) projeye ve kullanarak **devralma Seçici**. Bir kullanıcı denetimi ekleme ve değiştirme `Inherits` (`:` Visual C# ' ta) ifadesi. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms devral](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows Forms’u Devralma](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [Windows Forms Görsel Devralma](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
