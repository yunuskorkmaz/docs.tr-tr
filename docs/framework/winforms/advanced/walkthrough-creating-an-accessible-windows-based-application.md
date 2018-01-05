---
title: "İzlenecek Yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8f0a35b569b38e0d7ca79129f720034420ecd23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a>İzlenecek Yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma
Erişilebilir bir uygulama oluşturmaya önemli iş etkilere sahiptir. Birçok hükümetler erişilebilirlik düzenlemeleri yazılım satın vardır. Certified for Windows logo erişilebilirlik gereksinimleri içerir. ABD tek başına, bunların olası müşteriler, kaç tahmini bir 30 milyon yaşayanlar yazılım erişilebilirlik tarafından etkilenir.  
  
 Bu izlenecek yol da Certified for Windows logosu için beş erişilebilirlik gereksinimleri ele alınacaktır. Bu gereksinimleri göre erişilebilir bir uygulama olur:  
  
-   Denetim Masası boyutu, renk, yazı tipi desteği ve giriş ayarları. Kullanıcı Denetim Masası Ayarları değiştirdiğinde menü çubuğunda, başlık çubuğu, kenarlıklar ve durum çubuğu tüm kendilerini boyutlandırılır. Ek değişiklik denetimleri veya kod bu uygulamada gerekli değildir.  
  
-   Yüksek Karşıtlık modunu destekler.  
  
-   Tüm özellikleri belgelenen klavye erişim sağlar.  
  
-   Klavye odağı konumunu görsel olarak ve program aracılığıyla kullanıma sunar.  
  
-   Önemli bilgileri tek başına sesle açıklamak kaçının.  
  
 Daha fazla bilgi için bkz: [erişilebilir uygulamalar tasarlama için kaynaklar](/visualstudio/ide/reference/resources-for-designing-accessible-applications).  
  
 Değişen klavye düzenleri destekleme hakkında daha fazla bilgi için bkz: [dünya çapında kullanılmaya hazır uygulamalar geliştirmek için en iyi uygulamaları](../../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Bu kılavuzda pizza siparişleri götüren bir uygulama için kullanıcı arabirimi oluşturur. Oluşur bir <xref:System.Windows.Forms.TextBox> Müşteri'nin adı için bir <xref:System.Windows.Forms.RadioButton> pizza boyutu seçmek için Grup bir <xref:System.Windows.Forms.CheckedListBox> toppings seçmek için iki düğmenin denetimleri etiketli sırası ve iptal ve çıkış komutu menüsüyle.  
  
 Kullanıcı, Müşteri'nin adı, pizza ve istenen toppings boyutunu girer. Kullanıcı sipariş düğmesine tıkladığında, sipariş ve kendi maliyet özetini bir ileti kutusunda görüntülenir ve denetimleri temizlenmiş ve sonraki sipariş için hazır. Kullanıcı iptal düğmesine tıkladığında, denetimleri temizlenmiş ve sonraki sipariş için hazırdır. Kullanıcı çıkış menü öğesi tıkladığında, programı kapatır.  
  
 Bu kılavuzda Vurgu perakende sipariş sistem ancak kullanıcı arabiriminin erişilebilirlik kodunu değil. İzlenecek yol erişilebilirlik özelliklerini birkaç denetimleri düğmeleri, radyo düğmeleri, metin kutuları ve etiketleri de dahil olmak üzere, sık kullanılan gösterir.  
  
#### <a name="to-begin-making-the-application"></a>Uygulama yapmaya başlamak için  
  
-   Yeni bir Windows uygulaması oluşturma [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]. Proje adı **PizzaOrder**. (Ayrıntılar için bkz: [oluşturma yeni çözümler ve projeler](/visualstudio/ide/creating-solutions-and-projects).)  
  
## <a name="adding-the-controls-to-the-form"></a>Forma denetim ekleme  
 Denetimleri form eklerken, erişilebilir uygulama yapmak için aşağıdaki yönergeleri göz önünde bulundurun:  
  
-   Ayarlama <xref:System.Windows.Forms.Control.AccessibleDescription%2A> ve <xref:System.Windows.Forms.Control.AccessibleName%2A> özellikleri. Bu örnekte, varsayılan ayarı <xref:System.Windows.Forms.Control.AccessibleRole%2A> yeterlidir. Erişilebilirlik özellikleri hakkında daha fazla bilgi için bkz: [bir Windows formundaki denetimler için erişilebilirlik bilgileri sağlama](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md).  
  
-   10 puan veya daha büyük yazı tipi boyutunu ayarlayın.  
  
    > [!NOTE]
    >  Başlattığınızda 10 formun yazı tipi boyutunu ayarlarsanız, form sonradan eklenen tüm denetimler 10 yazı tipi boyutunu sahip olur.  
  
-   TextBox denetimi hemen açıklar herhangi bir etiket denetimi TextBox denetimi sekme sırası önündeki emin olun.  
  
-   "&" Karakter kullanarak bir erişim anahtarı eklemek <xref:System.Windows.Forms.Control.Text%2A> kullanıcı gitmek için isteyebilir denetiminin özelliği.  
  
-   "&" Karakter kullanarak bir erişim anahtarı eklemek <xref:System.Windows.Forms.Control.Text%2A> kullanıcı gitmek istediğiniz bir denetim önündeki etiket özelliği. Etiketleri ayarlama <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğine `true`, böylece kullanıcı erişim tuşuna bastığında odağını sekme sırasında bir sonraki denetime ayarlanır.  
  
-   Erişim tuşları tüm menü öğelerini ekleyin.  
  
#### <a name="to-make-your-windows-application-accessible"></a>Windows uygulamanızı erişilebilir yapma  
  
-   Forma denetimler ekleme ve aşağıda açıklandığı gibi özellikleri ayarlayın. Resim form üzerinde denetimleri düzenlemek nasıl bir model için tablonun sonuna bakın.  
  
    |Nesne|Özellik|Değer|  
    |------------|--------------|-----------|  
    |Form1|AccessibleDescription|Sipariş formu|  
    ||AccessibleName|Sipariş formu|  
    ||Yazı tipi boyutu|10|  
    ||Metin|Pizza sipariş formu|  
    |PictureBox|Ad|logosu|  
    ||AccessibleDescription|Pizza dilimin|  
    ||AccessibleName|Şirket logosu|  
    ||Görüntü|Herhangi bir simge veya bit eşlem|  
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
    |TextBox|Ad|customerName|  
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
    ||Metin|& küçük $6,00|  
    ||İşaretli|Doğru|  
    ||TabIndex|0|  
    ||AccessibleDescription|Küçük pizza|  
    ||AccessibleName|Küçük pizza|  
    |RadioButton|Ad|largePizza|  
    ||Metin|& büyük $10,00|  
    ||TabIndex|1.|  
    ||AccessibleDescription|Büyük bir pizza|  
    ||AccessibleName|Büyük bir pizza|  
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
    ||Öğeler|Pepperoni, Sausage, Mushrooms|  
    |Düğme|Ad|sıra|  
    ||Metin|& sırası|  
    ||TabIndex|7|  
    ||AccessibleDescription|Toplam sırası|  
    ||AccessibleName|Toplam sırayı|  
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
  
     ![Pizza sipariş formu](../../../../docs/framework/winforms/advanced/media/vbpizzaorderform.gif "vbPizzaOrderForm")  
Formunuz aşağıdakine benzer görünecektir:  
  
## <a name="supporting-high-contrast-mode"></a>Yüksek karşıtlıklı modu destekleme  
 Yüksek karşıtlıklı modu karşıt renkleri ve görme engelli kullanıcılar için yararlı yazı tipi boyutlarını kullanarak okunabilirlik artıran bir Windows Sistem ayardır. <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Özelliği, yüksek karşıtlık modunda ayarlanmış olup olmadığını belirlemek için sağlanır.  
  
 SystemInformation.HighContrast ise `true`, uygulama gerekir:  
  
-   Sistem renk düzenini kullanarak tüm kullanıcı arabirimi öğeleri görüntüleme  
  
-   Görsel ipuçları tarafından iletmek veya ses rengi üzerinden aktarılır bilgileri. Kırmızı bir yazı tipi kullanarak belirli liste öğelerini vurgulanmış, kullanıcı öğeler vurgulanır renk olmayan işaret sahip olması gibi de kalın yazı tipiyle ekleyebilirsiniz.  
  
-   Herhangi bir görüntü veya metin arkasında desen atlayın  
  
 Uygulama ayarını denetlemelisiniz <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> zaman uygulama başlar ve sistem olay yanıt <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>. <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Olayı her değeri <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> değişiklikler.  
  
 Bizim uygulamada, sistem ayarlarını rengini kullanmayan tek öğe ise `lblCompanyName`. <xref:System.Drawing.SystemColors> Sınıfı, kullanıcı tarafından seçilen sistem renkleri etiketinin renk ayarlarını değiştirmek için kullanılır.  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a>Etkili bir şekilde yüksek karşıtlık modunu etkinleştirmek için  
  
1.  Sistem renkleri etiketi rengini ayarlamak için bir yöntem oluşturma.  
  
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
  
2.  Çağrı `SetColorScheme` form Oluşturucusu yordamda (`Public Sub New()` Visual Basic'te ve `public class Form1` Visual C# ' ta). Visual Basic oluşturucuda erişmek için etiketli bölgesini genişletin gerekecektir **Windows Form Tasarımcısı oluşturulan kod**.  
  
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
  
3.  Yanıt için uygun imzalı bir olay yordamı oluşturun <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> olay.  
  
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
  
4.  Çağrısından sonra form oluşturucusu için kodu ekleyin `InitializeComponents`, sistem olay olay yordamına bağlanacağını için. Bu yöntemi çağırır `SetColorScheme` yordamı.  
  
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
  
5.  Forma kod eklemek <xref:System.Windows.Forms.Control.Dispose%2A> yöntemi çağırmadan önce <xref:System.Windows.Forms.Control.Dispose%2A> yöntemi uygulama kapandığında olay serbest bırakmak için temel sınıf. Erişim için <xref:System.Windows.Forms.Control.Dispose%2A> yöntemi Visual Basic'te Windows Form Tasarımcısı'nın oluşturulan kod etiketli bölgesini genişletin gerekir.  
  
    > [!NOTE]
    >  Sistem olay kodu ana uygulama ayrı bir iş parçacığı çalıştırır. Olay bırakmaz durumunda bile program kapatıldıktan sonra olaya kanca kod çalıştırılır.  
  
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
  
6.  Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a>Ses dışında bir yöntem sağlamak önemli bilgiler  
 Bu uygulamada hiçbir bilgi tek başına sesle aktarılır. Uygulamanızda ses kullanırsanız, bazı diğer yöntemlerle de bilgileri vermeniz gerekir.  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a>Diğer bir yöntem ses daha bilgi sağlamak için  
  
1.  Başlık çubuğu FlashWindow Windows API işlevi kullanarak flash yapın. Windows API işlevleri çağırmak nasıl bir örnek için bkz: [izlenecek yol: Windows API'larını çağırma](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
    > [!NOTE]
    >  Kullanıcı ayrıca bilgisayarın yerleşik Konuşmacı sistem sesleri yürütüldüğünde flash pencereye neden olur etkin, Windows Nöbetçisi hizmet olabilir.  
  
2.  Böylece kullanıcı şekilde yanıt verebilir önemli bilgileri kalıcı olmayan penceresinde görüntüler.  
  
3.  Klavye odağı alması bir ileti kutusu görüntüler. Bu yöntem, kullanıcının yazma sırasında kaçının.  
  
4.  Görev durumu bildirim alanında bir durum göstergesi görüntüler. Ayrıntılar için bkz [görev çubuğundan Windows Forms Notifyıcon bileşeniyle uygulama simgeleri ekleme](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Uygulamayı dağıtmadan önce uyguladıysanız erişilebilirlik özellikleri test etmeniz gerekir.  
  
#### <a name="to-test-accessibility-features"></a>Erişilebilirlik özelliklerini sınamak için  
  
1.  Klavye erişimi test etmek için fare çıkarın ve sadece klavyeyi kullanarak her bir özellik için kullanıcı arabirimi gidin. Tüm görevler yalnızca klavye kullanma gerçekleştirilebilir emin olun.  
  
2.  Yüksek Karşıtlık desteğini test etmek için Denetim Masası'ndaki Erişilebilirlik seçenekleri simgesini seçin. Görüntü sekmesini tıklatın ve Yüksek Karşıtlık kullan onay kutusunu seçin. Renk ve yazı tipi değişiklikler yansıtılır emin olmak için tüm kullanıcı arabirimi aracılığıyla öğelerin gidin. Ayrıca, görüntü veya metin çizilmiş desenleri atlanır emin olun.  
  
    > [!NOTE]
    >  Windows NT 4, Denetim Masası'ndaki Erişilebilirlik Seçenekleri simge yok. Bu nedenle, SystemInformation.HighContrast ayarını değiştirmek için bu yordamı Windows NT 4'te çalışmaz.  
  
3.  Diğer araçları uygulama erişilebilirliğini test etmek için hazır.  
  
4.  Klavye odağı gösterme test etmek için Büyüteç'i çalıştırın. (Açmak için tıklatın **Başlat** menüsündeki **programları**, işaret **Donatılar**, işaret **erişilebilirlik**ve 'ıtıklatın **Büyüteç'i**). Sekme klavye ve fare kullanarak kullanıcı arabirimi gidin. Tüm gezinti düzgün şekilde izlenen olun **Büyüteç**.  
  
5.  Sunan ekran öğelerini test etmek için İncele çalıştırın ve her öğe ulaşmak için fare ve için SEKME tuşunu kullanın. İncele penceresinde adı, durumu, rol, konum ve değer alanları sunulan bilgiler kullanıcı arabiriminde her nesne için anlamlı olduğundan emin olun.
