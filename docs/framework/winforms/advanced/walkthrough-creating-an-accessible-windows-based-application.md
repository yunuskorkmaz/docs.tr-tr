---
title: 'İzlenecek Yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
dev_langs:
- csharp
- vb
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: b8f0c7c4584505d382e78aca68e2e99c9fa7748f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834625"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a>İzlenecek Yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma

Erişilebilir bir uygulama oluşturmak önemli iş etkilerine sahiptir. Birçok kamu yazılımı, yazılım satın alma için erişilebilirlik düzenlemelerine sahiptir. Certified for Windows logosu erişilebilirlik gereksinimlerini içerir. ABD 'deki tahmini bir 30.000.000 sakın tek başına, potansiyel müşterilerinin çoğu yazılım erişilebilirliğiyle etkilenir.

Bu izlenecek yol, Windows için sertifikalı logosu için beş erişilebilirlik gereksinimini ele alacak. Bu gereksinimlere göre, erişilebilir bir uygulama şunları sağlar:

- Denetim Masası boyutunu, rengini, yazı tipini ve giriş ayarlarını destekler. Kullanıcı denetim masası ayarlarını değiştirdiğinde, menü çubuğu, başlık çubuğu, kenarlıklar ve durum çubuğunun hepsi kendini yeniden boyutlandıracaktır. Bu uygulamada denetimlerde veya kodda ek değişiklik yapılması gerekmez.

- Yüksek Karşıtlık modunu destekler.

- Tüm özelliklere belgelenmiş klavye erişimi sağlar.

- Klavye odağının konumunu görsel ve programlı olarak ortaya çıkarın.

- Önemli bilgileri seslerle tek başına vermekten kaçının.

Daha fazla bilgi için bkz. [erişilebilir uygulamalar tasarlama kaynakları](/visualstudio/ide/reference/resources-for-designing-accessible-applications).

Farklı klavye düzenlerini destekleme hakkında daha fazla bilgi için bkz. [Dünya çapında kullanılabilecek uygulamalar geliştirmek Için En Iyi uygulamalar](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).

## <a name="creating-the-project"></a>Projeyi Oluşturma

Bu izlenecek yol, pizza siparişi alan bir uygulama için Kullanıcı arabirimi oluşturur. Müşterinin adı için bir <xref:System.Windows.Forms.TextBox>, pizza boyutunu seçmek için bir <xref:System.Windows.Forms.RadioButton> grubu, toppings seçmek için bir <xref:System.Windows.Forms.CheckedListBox>, Order ve Cancel etiketli iki düğme denetimi ve çıkış komutu içeren bir menü.

Kullanıcı müşterinin adını, pizza boyutunu ve toppings istenen şekilde girer. Kullanıcı sipariş düğmesine tıkladığında, siparişin Özeti ve maliyeti bir ileti kutusunda görüntülenir ve denetimler temizlenir ve bir sonraki sırada kullanılabilir. Kullanıcı Iptal düğmesine tıkladığında, denetimler temizlenir ve bir sonraki sıraya göre hazırlanalınır. Kullanıcı çıkış menü öğesine tıkladığında program kapanır.

Bu izlenecek yolun vurgusu, bir perakende sipariş sisteminin kodu değil, Kullanıcı arabiriminin erişilebilirliği değildir. İzlenecek yol, düğmeler, radyo düğmeleri, metin kutuları ve Etiketler dahil olmak üzere, sık kullanılan birçok denetimin erişilebilirlik özelliklerini gösterir.

#### <a name="to-begin-making-the-application"></a>Uygulamayı yapmaya başlamak için

- Visual Basic veya görselde C#yeni bir Windows uygulaması oluşturun. Projeyi **PizzaOrder**olarak adlandırın. Ayrıntılar için bkz. [yeni çözümler ve projeler oluşturma](/visualstudio/ide/creating-solutions-and-projects).

## <a name="adding-the-controls-to-the-form"></a>Forma denetim ekleme

Denetimleri bir forma eklerken, erişilebilir bir uygulama oluşturmak için aşağıdaki yönergeleri aklınızda bulundurun:

- @No__t-0 ve <xref:System.Windows.Forms.Control.AccessibleName%2A> özelliklerini ayarlayın. Bu örnekte, <xref:System.Windows.Forms.Control.AccessibleRole%2A> ' ın varsayılan ayarı yeterlidir. Erişilebilirlik özellikleri hakkında daha fazla bilgi için bkz. [Windows formundaki denetimler Için erişilebilirlik bilgileri sağlama](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).

- Yazı tipi boyutunu 10 noktaya veya daha büyük olarak ayarlayın.

  > [!NOTE]
  > Başlattığınız sırada formun yazı tipi boyutunu 10 olarak ayarlarsanız, daha sonra forma eklenen tüm denetimlerin 10 yazı tipi boyutu olur.

- TextBox denetimini açıklayan etiket denetiminin, sekme düzeninde TextBox denetiminden hemen önce geldiğinden emin olun.

- Kullanıcının gitmek isteyebileceğiniz herhangi bir denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliğine, "&" karakterini kullanarak bir erişim anahtarı ekleyin.

- "&" Karakterini kullanarak, kullanıcının gitmek isteyebileceğiniz bir denetimin önündeki <xref:System.Windows.Forms.Control.Text%2A> özelliğine bir erişim anahtarı ekleyin. ' @No__t-0 özelliğini `true` olarak ayarlayın. böylece odak, Kullanıcı erişim tuşuna bastığında sekme düzeninde bir sonraki denetime ayarlanır.

- Tüm menü öğelerine erişim anahtarları ekleyin.

#### <a name="to-make-your-windows-application-accessible"></a>Windows uygulamanızı erişilebilir hale getirmek için

- Denetimleri forma ekleyin ve aşağıda açıklandığı gibi özellikleri ayarlayın. Form üzerinde denetimlerin nasıl düzenlendiğini gösteren bir model için tablonun sonundaki resme bakın.

   |Nesne|Özellik|Değer|
   |------------|--------------|-----------|
   |Form1|Erişilebilir açıklama|Sipariş formu|
   ||Erişilebilir ad|Sipariş formu|
   ||Yazı tipi boyutu|10|
   ||Metin|Pizza sırası formu|
   |PictureBox|Name|Le|
   ||Erişilebilir açıklama|Pizza dilimi|
   ||Erişilebilir ad|Şirket logosu|
   ||Görüntü|Herhangi bir simge veya bit eşlem|
   |Etiketle|Name|companyLabel|
   ||Metin|İyi pizza|
   ||Atan|1\.|
   ||Erişilebilir açıklama|Şirket adı|
   ||Erişilebilir ad|Şirket adı|
   ||Rengi|Ma|
   ||ForeColor|Renkle|
   ||Yazı tipi boyutu|18|
   |Etiketle|Name|customerLabel|
   ||Metin|& adı|
   ||Atan|2|
   ||Erişilebilir açıklama|Müşteri adı etiketi|
   ||Erişilebilir ad|Müşteri adı etiketi|
   ||Useanımsatıcı|Doğru|
   |TextBox|Name|customerName|
   ||Metin|seçim|
   ||Atan|3|
   ||Erişilebilir açıklama|Müşteri adı|
   ||Erişilebilir ad|Müşteri adı|
   |GroupBox|Name|sizeOptions|
   ||Erişilebilir açıklama|Pizza boyut seçenekleri|
   ||Erişilebilir ad|Pizza boyut seçenekleri|
   ||Metin|Pizza boyutu|
   ||Atan|4|
   |RadioButton|Name|smallPizza|
   ||Metin|& küçük $6,00|
   ||Edildikten|Doğru|
   ||Atan|0|
   ||Erişilebilir açıklama|Küçük pizza|
   ||Erişilebilir ad|Küçük pizza|
   |RadioButton|Name|largePizza|
   ||Metin|& büyük $10,00|
   ||Atan|1\.|
   ||Erişilebilir açıklama|Büyük pizza|
   ||Erişilebilir ad|Büyük pizza|
   |Etiketle|Name|toppingsLabel|
   ||Metin|& toppings ($0,75)|
   ||Atan|5|
   ||Erişilebilir açıklama|Toppings etiketi|
   ||Erişilebilir ad|Toppings etiketi|
   ||Useanımsatıcı|Doğru|
   |CheckedListBox|Name|toppings|
   ||Atan|6|
   ||Erişilebilir açıklama|Kullanılabilir toppings|
   ||Erişilebilir ad|Kullanılabilir toppings|
   ||Öğeler|Pepperoni, sausage, Mushodalar|
   |Düğme|Name|sıra|
   ||Metin|& sırası|
   ||Atan|7|
   ||Erişilebilir açıklama|Siparişin toplamı|
   ||Erişilebilir ad|Toplam sıra|
   |Düğme|Name|İptal|
   ||Metin|& Iptal et|
   ||Atan|8|
   ||Erişilebilir açıklama|Siparişi iptal et|
   ||Erişilebilir ad|Siparişi iptal et|
   |MainMenu|Name|Birmainmenu|
   |MenuItem|Name|fileCommands|
   ||Metin|& dosyası|
   |MenuItem|Name|exitApp|
   ||Metin|E & çı|

   Formunuz aşağıdaki görüntüye benzer bir şekilde görünür:

   ![Name metin kutusu ve size ve toppings seçimiyle pizza Order form.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)

## <a name="supporting-high-contrast-mode"></a>Yüksek Karşıtlık modunu destekleme

Yüksek Karşıtlık modu, görme engelli kullanıcılar için faydalı olan karşıt renkler ve yazı tipi boyutlarını kullanarak okunabilirliği artıran bir Windows sistem ayarıdır. @No__t-0 özelliği, Yüksek Karşıtlık modunun ayarlanmış olup olmadığını belirleyecek şekilde sağlanır.

SystemInformation. Highkarşıtlıklı `true` ise, uygulamanın şunları yapmanız gerekir:

- Sistem renk şemasını kullanarak tüm Kullanıcı arabirimi öğelerini görüntüleme

- Görsel ipuçlarıyla veya renk aracılığıyla ileten tüm bilgileri sesleyerek bir şekilde dolaşın. Örneğin, belirli liste öğeleri kırmızı bir yazı tipi kullanılarak vurgulanmışsa, yazı tipine de kalın ekleyebilirsiniz, böylece kullanıcının öğelerin vurgulandığı bir Color olmayan ipucu vardır.

- Metnin arkasındaki görüntüleri veya desenleri atlayın

Uygulama başlatıldığında <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> ayarını denetlemelidir ve <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> sistem olayına yanıt verir. @No__t-0 olayı, <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> değeri her değiştiğinde tetiklenir.

Uygulamamızda, renk için sistem ayarlarını kullanmayan tek öğe `lblCompanyName` ' dır. @No__t-0 sınıfı, etiketin renk ayarlarını kullanıcı tarafından seçilen sistem renkleriyle değiştirmek için kullanılır.

#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a>Yüksek Karşıtlık modunu etkili bir şekilde etkinleştirmek için

1. Etiketin renklerini sistem renkleriyle ayarlamak için bir yöntem oluşturun.

    ```vb
    Private Sub SetColorScheme()
        If SystemInformation.HighContrast Then
            companyLabel.BackColor = SystemColors.Window
            companyLabel.ForeColor = SystemColors.WindowText
        Else
            companyLabel.BackColor = Color.Blue
            companyLabel.ForeColor = Color.Yellow
        End If
    End Sub
    ```

    ```csharp
    private void SetColorScheme()
    {
        if (SystemInformation.HighContrast)
        {
            companyLabel.BackColor = SystemColors.Window;
            companyLabel.ForeColor = SystemColors.WindowText;
        }
        else
        {
            companyLabel.BackColor = Color.Blue;
            companyLabel.ForeColor = Color.Yellow;
        }
    }
    ```

2. Form oluşturucusunda `SetColorScheme` yordamını çağırın (Visual Basic ve `public Form1()` ' de `Public Sub New()` C#). Visual Basic oluşturucuya erişmek için, **Windows Form Tasarımcısı tarafından üretilen kod**etiketli bölgeyi genişletmeniz gerekecektir.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
        SetColorScheme()
    End Sub
    ```

    ```csharp
    public Form1()
    {
        InitializeComponent();
        SetColorScheme();
    }
    ```

3. @No__t-0 olayına yanıt vermek için uygun imzayla bir olay yordamı oluşturun.

    ```vb
    Protected Sub UserPreferenceChanged(sender As Object, _
    e As Microsoft.Win32.UserPreferenceChangedEventArgs)
        SetColorScheme()
    End Sub
    ```

    ```csharp
    public void UserPreferenceChanged(object sender,
    Microsoft.Win32.UserPreferenceChangedEventArgs e)
    {
        SetColorScheme();
    }
    ```

4. Olay yordamını sistem olayına bağlamak için `InitializeComponents` ' a çağrıdan sonra form oluşturucusuna kod ekleyin. Bu yöntem `SetColorScheme` yordamını çağırır.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
        SetColorScheme()
        AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
           AddressOf Me.UserPreferenceChanged
    End Sub
    ```

    ```csharp
    public Form1()
    {
        InitializeComponent();
        SetColorScheme();
        Microsoft.Win32.SystemEvents.UserPreferenceChanged
           += new Microsoft.Win32.UserPreferenceChangedEventHandler(
           this.UserPreferenceChanged);
    }
    ```

5. Uygulama kapandığında olayı serbest bırakmak için, temel sınıfın <xref:System.Windows.Forms.Control.Dispose%2A> yöntemine yapılan çağrıdan önce <xref:System.Windows.Forms.Control.Dispose%2A> yöntemine kod ekleyin. Visual Basic <xref:System.Windows.Forms.Control.Dispose%2A> yöntemine erişmek için, Windows Form Tasarımcısı tarafından üretilen kod etiketli bölgeyi genişletmeniz gerekecektir.

    > [!NOTE]
    > Sistem olay kodu, ana uygulamadan ayrı bir iş parçacığı çalıştırır. Olayı yayınlamayın, olaya yedeklediğiniz kod Program kapatıldıktan sonra bile çalışacaktır.

    ```vb
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)
        If disposing AndAlso components IsNot Nothing Then
            components.Dispose()
        End If
        RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
           AddressOf Me.UserPreferenceChanged
        MyBase.Dispose(disposing)
    End Sub
    ```

    ```csharp
    protected override void Dispose(bool disposing)
    {
        if(disposing && components != null)
        {
            components.Dispose();
        }
        Microsoft.Win32.SystemEvents.UserPreferenceChanged
           -= new Microsoft.Win32.UserPreferenceChangedEventHandler(
           this.UserPreferenceChanged);
        base.Dispose( disposing );
    }
    ```

6. Uygulamayı çalıştırmak için F5 tuşuna basın.

## <a name="conveying-important-information-by-means-other-than-sound"></a>Önemli bilgileri ses dışındaki yollarla uygulamaya göre

Bu uygulamada, hiçbir bilgi yalnızca ses ile değil. Uygulamanızda ses kullanıyorsanız, bu bilgileri başka bir yöntemle de sağlamanız gerekir.

#### <a name="to-supply-information-by-some-other-means-than-sound"></a>Daha fazla bilgi için sesinden farklı bir şekilde bilgi sağlamak için

1. Windows API işlevi FlashWindow kullanarak başlık çubuğunu Flash yapın. Windows API işlevlerinin nasıl çağrılacağını gösteren bir örnek için bkz. [Izlenecek yol: Windows API 'Leri çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).

    > [!NOTE]
    > Kullanıcının Windows Ses Nöbetçisi hizmeti etkin olabilir, bu da sistem seslerinin bilgisayarın yerleşik konuşmacı aracılığıyla çalınması durumunda pencerenin yanıp sönmesine neden olur.

2. Kullanıcının yanıt verebilmesi için, önemli bilgileri kalıcı olmayan bir pencerede görüntüleyin.

3. Klavye odağını elde eden bir ileti kutusu görüntüler. Kullanıcı yazmayabilir, bu yöntemden kaçının.

4. Görev çubuğunun durum bildirimi alanında bir durum göstergesi görüntüleyin. Ayrıntılar için bkz. [Windows Forms NotifyIcon bileşeni Ile görev çubuğuna uygulama simgeleri ekleme](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).

## <a name="testing-the-application"></a>Uygulamayı Test Etme

Uygulamayı dağıtılmadan önce, uygulamakta olduğunuz erişilebilirlik özelliklerini sınamalısınız.

#### <a name="to-test-accessibility-features"></a>Erişilebilirlik özelliklerini test etmek için

1. Klavye erişimini test etmek için fare bağlantısını çıkarın ve yalnızca klavyeyi kullanarak her bir özellik için Kullanıcı arabirimine gidin. Tüm görevlerin yalnızca klavye kullanılarak gerçekleştirildiğinden emin olun.

2. Yüksek Karşıtlık desteğini test etmek için Denetim Masası 'nda erişilebilirlik seçenekleri simgesini seçin. Görüntü sekmesine tıklayın ve Yüksek Karşıtlık Kullan onay kutusunu seçin. Renk ve yazı tipi değişikliklerinin yansıtıldığından emin olmak için tüm Kullanıcı Arabirimi öğelerine gidin. Ayrıca, metnin arkasında çizilen görüntülerin veya desenlerin atlandığından emin olun.

    > [!NOTE]
    > Windows NT 4 ' te Denetim Masası 'nda bir erişilebilirlik seçenekleri simgesi yoktur. Bu nedenle, SystemInformation. Highkarşıtlık ayarını değiştirmeye yönelik bu yordam Windows NT 4 ' te çalışmaz.

3. Diğer araçlar, bir uygulamanın erişilebilirliğini test etmek için hazırdır.

4. Klavye odağını ortaya çıkaran test etmek için büyüteci çalıştırın. (Açmak için **Başlat** menüsüne tıklayın, **Programlar**' ın, **Donatılar**' ın, **Erişilebilirlik**' in üzerine gelin ve ardından **Büyüteç**' e tıklayın). Kullanıcı arabiriminde hem klavye sekmeyi hem de fareyi kullanarak gezinin. Tüm gezintinin **Büyüteç**'te düzgün şekilde izlendiğinden emin olun.

5. Ekran öğelerini ortaya çıkarmayı test etmek için Inceleme çalıştırın ve her bir öğeye ulaşmak için hem fareyi hem de sekme tuşunu kullanın. Inceleme penceresinin Ad, durum, rol, konum ve değer alanlarında sunulan bilgilerin, Kullanıcı ARABIRIMINDEKI her nesne için anlamlı olduğundan emin olun.
