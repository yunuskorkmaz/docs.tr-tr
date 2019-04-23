---
title: 'İzlenecek yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: e7bc996c3d64c0ea3ac8fca5fef759ad309f2967
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773369"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a>İzlenecek yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma
Erişilebilir bir uygulama oluşturma, önemli iş etkileri vardır. Birçok hükümetler yazılım satın alma için erişilebilirlik düzenlemeleri vardır. Windows için sertifikalıdır logosu erişilebilirlik gereksinimlerini içerir. ABD tek başına kaç tanesinin potansiyel müşteriler, tahmini bir 30 milyon yaşayanlar yazılım erişilebilirliğini tarafından etkilenir.  
  
 Bu izlenecek yol, Windows için sertifikalıdır logosu beş erişilebilirlik gereksinimlerini ele alınacaktır. Bu gereksinimlerine göre erişilebilir bir uygulama olacaktır:  
  
-   Denetim Masası boyutu, renk, yazı tipi desteği ve giriş ayarları. Kullanıcı Denetim Masası ayarları değiştiğinde menü çubuğunda, başlık çubuğu, kenarlık ve durum çubuğu tüm kendilerini boyutlandırılır. Bu uygulamada hiçbir ek değişiklikler denetimlerde veya kod gerekir.  
  
-   Yüksek Karşıtlık modunu destekler.  
  
-   Tüm özellikleri belgelenmiş klavye erişim sağlar.  
  
-   Klavye odağı konumunu görsel olarak hem de programsal olarak kullanıma sunar.  
  
-   Tek başına sesle önemli bilgileri iletmek kaçının.  
  
 Daha fazla bilgi için [erişilebilir uygulamalar tasarlama için kaynaklar](/visualstudio/ide/reference/resources-for-designing-accessible-applications).  
  
 Değişen klavye düzenleri destekleme hakkında daha fazla bilgi için bkz: [dünya çapında kullanılmaya hazır uygulama geliştirmek için en iyi](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Bu izlenecek yolda pizza siparişler alan bir uygulama için kullanıcı arabirimi oluşturur. İçerdiği bir <xref:System.Windows.Forms.TextBox> müşterinin adı için bir <xref:System.Windows.Forms.RadioButton> pizza boyutu seçmek için Grup bir <xref:System.Windows.Forms.CheckedListBox> toppings seçmek için iki düğme denetimi etiketli sırasını ve iptal et ve çıkış komutu ile bir menü.  
  
 Kullanıcı, müşterinin adı, pizza ve istenen toppings boyutunu girer. Kullanıcı sipariş düğmesine tıkladığında, sırasını ve kendi maliyet özeti, bir ileti kutusunda görüntülenir ve denetimler temizlenir ve sonraki siparişi için hazır değil. Kullanıcı iptal düğmesine tıkladığında, denetimler, temizlenmiş ve sonraki siparişi için hazır değil. Kullanıcı çıkış menü öğesini tıkladığında, program kapatır.  
  
 Bu kılavuzun Vurgu perakende sırada sistem, ancak kullanıcı arabirimi erişilebilirliği kodu değil. İzlenecek yol, birçok erişilebilirlik özelliğine düğmeleri, radyo düğmeleri, metin kutuları ve etiketler gibi denetimleri, sık kullanılan gösterir.  
  
#### <a name="to-begin-making-the-application"></a>Uygulama yapmaya başlamak için  
  
-   Visual Basic veya Visual içinde yeni bir Windows uygulaması oluşturma C#. Projeyi adlandırın **PizzaOrder**. (Ayrıntılar için bkz. [oluşturma yeni çözümler ve projeler](/visualstudio/ide/creating-solutions-and-projects).)  
  
## <a name="adding-the-controls-to-the-form"></a>Formu için denetimler ekleme  
 Forma denetim ekleme, erişilebilir bir uygulama yapmak için aşağıdaki yönergeleri dikkate alın:  
  
-   Ayarlama <xref:System.Windows.Forms.Control.AccessibleDescription%2A> ve <xref:System.Windows.Forms.Control.AccessibleName%2A> özellikleri. Bu örnekte, varsayılan ayarı <xref:System.Windows.Forms.Control.AccessibleRole%2A> yeterlidir. Erişilebilirlik özellikleri hakkında daha fazla bilgi için bkz. [bir Windows formundaki denetimler için erişilebilirlik bilgileri sağlama](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).  
  
-   10 noktalarına ya da daha büyük yazı tipi boyutunu ayarlayın.  
  
    > [!NOTE]
    >  Başlattığınızda 10 form yazı tipi boyutunu ayarlayın, tüm denetimler için form daha sonradan eklenen bir yazı tipi boyutu 10 yüklemeniz gerekir.  
  
-   Hemen bir TextBox denetimi tanımlayan herhangi bir etiket denetimi TextBox denetimi içinde sekme sırası önündeki emin olun.  
  
-   "&" Karakteri kullanarak bir erişim anahtarı ekleme <xref:System.Windows.Forms.Control.Text%2A> gitmek istediğiniz kullanıcı denetiminin özelliği.  
  
-   "&" Karakteri kullanarak bir erişim anahtarı ekleme <xref:System.Windows.Forms.Control.Text%2A> önündeki kullanıcı gitmek isteyebilirsiniz bir denetim etiketinin özelliği. Etiketlerin ayarlamak <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğini `true`, böylece kullanıcı erişim tuşuna bastığında odağını sekme sırasında sonraki denetime ayarlanır.  
  
-   Tüm menü öğeleri için erişim anahtarları ekleyin.  
  
#### <a name="to-make-your-windows-application-accessible"></a>Windows uygulamanızı erişilebilir hale getirmek için  
  
-   Formu için denetimler ekleme ve aşağıda açıklandığı gibi özellikleri ayarlayın. Form üzerinde denetimleri düzenlemek nasıl bir model için tablonun sonuna resmi görürsünüz.  
  
    |Nesne|Özellik|Değer|  
    |------------|--------------|-----------|  
    |Form1|AccessibleDescription|Siparişi formu|  
    ||AccessibleName|Siparişi formu|  
    ||Yazı tipi boyutu|10|  
    ||Metin|Pizza siparişi formu|  
    |PictureBox|Ad|Logo|  
    ||AccessibleDescription|Pizza dilimin|  
    ||AccessibleName|Şirket logosu|  
    ||Görüntü|Herhangi bir simge ya da bit eşlem|  
    |Etiketle|Ad|companyLabel|  
    ||Metin|İyi Pizza|  
    ||TabIndex|1.|  
    ||AccessibleDescription|Şirket adı|  
    ||AccessibleName|Şirket adı|  
    ||Arka plan rengi|Mavi|  
    ||ForeColor|Sarı|  
    ||Yazı tipi boyutu|18|  
    |Etiketle|Ad|customerLabel|  
    ||Metin|& adı|  
    ||TabIndex|2|  
    ||AccessibleDescription|Müşteri adı etiketi|  
    ||AccessibleName|Müşteri adı etiketi|  
    ||UseMnemonic|Doğru|  
    |TextBox|Ad|CustomerName|  
    ||Metin|(hiçbiri)|  
    ||TabIndex|3|  
    ||AccessibleDescription|Müşteri adı|  
    ||AccessibleName|Müşteri adı|  
    |GroupBox|Ad|sizeOptions|  
    ||AccessibleDescription|Pizza boyut seçenekleri|  
    ||AccessibleName|Pizza boyut seçenekleri|  
    ||Metin|Pizza boyutu|  
    ||TabIndex|4|  
    |RadioButton|Ad|smallPizza|  
    ||Metin|& küçük $6.00|  
    ||İşaretli|Doğru|  
    ||TabIndex|0|  
    ||AccessibleDescription|Küçük pizza|  
    ||AccessibleName|Küçük pizza|  
    |RadioButton|Ad|largePizza|  
    ||Metin|& büyük $10,00|  
    ||TabIndex|1.|  
    ||AccessibleDescription|Büyük pizza|  
    ||AccessibleName|Büyük pizza|  
    |Etiketle|Ad|toppingsLabel|  
    ||Metin|& toppings ($0,75 her)|  
    ||TabIndex|5|  
    ||AccessibleDescription|Toppings etiketi|  
    ||AccessibleName|Toppings etiketi|  
    ||UseMnemonic|Doğru|  
    |CheckedListBox|Ad|toppings|  
    ||TabIndex|6|  
    ||AccessibleDescription|Kullanılabilir toppings|  
    ||AccessibleName|Kullanılabilir toppings|  
    ||Öğeler|Pepperoni Sausage, Mushrooms|  
    |Düğme|Ad|sıra|  
    ||Metin|& sırası|  
    ||TabIndex|7|  
    ||AccessibleDescription|Toplam sırası|  
    ||AccessibleName|Toplam sırası|  
    |Düğme|Ad|İptal|  
    ||Metin|& iptal et|  
    ||TabIndex|8|  
    ||AccessibleDescription|Siparişi iptal etme|  
    ||AccessibleName|Siparişi iptal etme|  
    |MainMenu|Ad|theMainMenu|  
    |MenuItem|Ad|fileCommands|  
    ||Metin|& dosya|  
    |MenuItem|Ad|exitApp|  
    ||Metin|Çı &|
    
      Formunuza, aşağıdaki görüntüde aşağıdakine benzer:
    
      ![Ad metin, boyut ve toppings seçimi pizza sipariş formla.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)  

## <a name="supporting-high-contrast-mode"></a>Yüksek Karşıtlık modunu kullanmak destekleme  
 Yüksek Karşıtlık modunu kullanmak, karşıt renklerden ve görme engelli kullanıcılar için yararlı olan yazı tipi boyutlarını kullanarak okunabilirliğini artırır bir Windows sistemi ayarıdır. <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Özelliği, yüksek karşıtlık modunu ayarlanmış olup olmadığını belirlemek için sağlanır.  
  
 SystemInformation.HighContrast ise `true`, uygulamanın gerekir:  
  
-   Sistem renk düzenini kullanarak tüm kullanıcı arabirimi öğeleri görüntüleme  
  
-   Görsel ipuçları tarafından iletmek veya ses renk ilettiği tüm bilgileri. Kırmızı bir yazı tipi kullanarak belirli bir liste öğelerini vurgulanır, böylece kullanıcı öğeler vurgulanmıştır bir renk olmayan işaret gibi de kalın yazı ekleyebilirsiniz.  
  
-   Herhangi bir görüntü veya metin arkasında desen atla  
  
 Uygulama ayarını denetlesin <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> uygulamanın ne zaman başlar ve sistem olaya yanıt <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>. <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Olayı her değeri <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> değişiklikler.  
  
 Uygulamamızı, renk için sistem ayarları kullanmayan tek öğe ise `lblCompanyName`. <xref:System.Drawing.SystemColors> Sınıfı kullanıcı tarafından seçilen sistem renkleri için renk ayarlarını etiketin değiştirmek için kullanılır.  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a>Etkili bir şekilde yüksek karşıtlık modunu etkinleştirmek için  
  
1. Sistem renkleri için etiket renklerini ayarlamak için bir yöntem oluşturun.  
  
    ```  
    ' Visual Basic  
    Private Sub SetColorScheme()  
       If SystemInformation.HighContrast Then  
          companyLabel.BackColor = SystemColors.Window  
          companyLabel.ForeColor = SystemColors.WindowText  
       Else  
          companyLabel.BackColor = Color.Blue  
          companyLabel.ForeColor = Color.Yellow  
       End If  
    End Sub  
  
    // C#  
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
  
2. Çağrı `SetColorScheme` form Oluşturucu yordamda (`Public Sub New()` Visual Basic'te ve `public class Form1` görselde C#). Visual Basic'te Oluşturucusu erişmek için etiketli bölgeyi Genişlet gerekecektir **Windows Form Designer üretilen kod**.  
  
    ```  
    ' Visual Basic   
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
    }  
    ```  
  
3. Yanıt vermek için uygun imzaya sahip bir olay yordamı oluşturma <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> olay.  
  
    ```  
    ' Visual Basic  
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _  
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public void UserPreferenceChanged(object sender,   
    Microsoft.Win32.UserPreferenceChangedEventArgs e)  
    {  
       SetColorScheme();  
    }  
    ```  
  
4. Çağrısından sonra form Oluşturucu için kod ekleme `InitializeComponents`, sistem olay olay yordamına bağlama. Bu yöntemin çağırdığı `SetColorScheme` yordamı.  
  
    ```  
    ' Visual Basic  
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          += new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
    }  
    ```  
  
5. Forma kod eklemek <xref:System.Windows.Forms.Control.Dispose%2A> yöntemi çağırmadan önce <xref:System.Windows.Forms.Control.Dispose%2A> yöntemi uygulama kapandığında olay serbest bırakmak için temel sınıf. Erişim için <xref:System.Windows.Forms.Control.Dispose%2A> yöntem Visual Basic'te Windows Form Designer üretilen kod etiketli bölgesini genişletin gerekir.  
  
    > [!NOTE]
    >  Sistem olay kodu, ana uygulamadan ayrı bir iş parçacığı çalıştırır. Olay sunmamayı ise bile programın kapatıldıktan sonra olaya kanca kodu çalıştırın.  
  
    ```  
    ' Visual Basic  
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)  
       If disposing Then  
          If Not (components Is Nothing) Then  
             components.Dispose()  
          End If  
       End If  
       RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
       MyBase.Dispose(disposing)  
    End Sub  
  
    // C#  
    protected override void Dispose( bool disposing )  
    {  
       if( disposing )  
       {  
          if (components != null)   
          {  
             components.Dispose();  
          }  
       }  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          -= new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
       base.Dispose( disposing );  
    }  
    ```  
  
6. Uygulamayı çalıştırmak için F5'e basın.  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a>Ses dışındaki bir yöntemle önemli bilgileri iletmek  
 Bu uygulamada hiçbir bilgi ses başına aktarılır. Uygulamanızda ses kullanıyorsanız, bazı diğer yöntemlerle de bilgileri vermeniz gerekir.  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a>Başka bir şekilde ses daha bilgi sağlamak için  
  
1. Başlık çubuğunda FlashWindow Windows API işlevi kullanarak flash olun. Windows API işlevleri çağırmak nasıl bir örnek için bkz [izlenecek yol: Windows API'larını çağırma](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
    > [!NOTE]
    >  Kullanıcının, ayrıca bilgisayarın yerleşik Konuşmacı sistem seslerini yürütüldüğünde flash pencereye neden olur etkinse, Windows Nöbetçisi hizmet olabilir.  
  
2. Kullanıcı buna yanıt verebilir böylece önemli bilgileri kalıcı olmayan küçük penceresinde görüntüler.  
  
3. Klavye odağı alması bir ileti kutusu görüntüler. Bu yöntem, kullanıcının yazma sırasında kaçının.  
  
4. Görev durum bildirim alanında bir durum göstergesi görüntüler. Ayrıntılar için bkz [Windows Forms Notifyıcon bileşeni taskbar'na uygulama simgeleri ekleme](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Uygulamayı dağıtmadan önce uyguladıysanız erişilebilirlik özellikleri test etmeniz gerekir.  
  
#### <a name="to-test-accessibility-features"></a>Erişilebilirlik özelliklerini test etmek için  
  
1. Klavye erişimi test etmek için fare çıkarın ve yalnızca klavye kullanma her bir özellik için kullanıcı arabirimi gidin. Tüm görevler yalnızca klavyeyi kullanarak gerçekleştirilebilir emin olun.  
  
2. Yüksek Karşıtlık desteğini test etmek için Denetim Masası'ndaki Erişilebilirlik seçenekleri simgesini seçin. Görüntü sekmesini tıklatın ve Yüksek Karşıtlık kullan onay kutusunu seçin. Renk ve yazı tipi değişikliklerin yansıtıldığından emin olmak için tüm kullanıcı arabirimi öğeleri arasında gezinebilirsiniz. Ayrıca, görüntü veya metin çizilmiş desenleri atlanır emin olun.  
  
    > [!NOTE]
    >  Windows NT 4, Denetim Masası'ndaki Erişilebilirlik Seçenekleri simge yok. Bu nedenle, SystemInformation.HighContrast ayarı değiştirmek için bu yordamı Windows NT 4'te çalışmıyor.  
  
3. Diğer araçları uygulama erişilebilirliğini test etmek için hazırdır.  
  
4. Klavye odağı gösterme test etmek için Büyüteç'i çalıştırın. (Açmak için tıklayın **Başlat** menüsünde **programlar**, işaret **Donatılar**, işaret **erişilebilirlik**ve 'yetıklayın **Büyüteç'i**). Sekmeyle gitmeyi klavye ve fareyi kullanarak kullanıcı arabirimi gidin. Tüm gezinti üzerinde düzgün şekilde izlenir olun **Büyüteç**.  
  
5. İfşa edildi ekran öğelerini test etmek için İncele çalıştırın ve her öğe ulaşmak için fare hem SEKME tuşunu kullanın. İnceleyin penceresinin adı, durumu, rol, konum ve değer alanlarda sunulan bilgiler, kullanıcı arabiriminde her nesne için anlamlı olduğundan emin olun.
