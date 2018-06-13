---
title: 'İzlenecek yol: Visual C# İle Bileşik Denetim Yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
ms.openlocfilehash: 1c669860b545150e75777b8c8cc434f47675ec5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541800"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a>İzlenecek yol: Visual C# İle Bileşik Denetim Yazma #
Bileşik denetimler olarak özel grafik arabirimler oluşturulabilir yeniden ve bir yol sağlar. Bileşik Denetim aslında bir görsel gösterimi ile bileşenidir. Bu nedenle, bir veya daha fazla Windows Forms denetimleri, bileşenleri veya kullanıcı girişini doğrulama, görüntü özelliklerini değiştirme veya yazar tarafından gerekli diğer görevleri gerçekleştirme işlevselliğini genişletebildiği kod bloklarını oluşabilir. Bileşik denetimler, diğer denetimler aynı şekilde Windows Forms'ta yerleştirilebilir. Bu kılavuzun ilk bölümünde oluşturduğunuz adlı basit bir bileşik denetim `ctlClock`. İzlenecek yol ikinci bölümünde, işlevselliğini genişletmek `ctlClock` devralma yoluyla.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adı ayarlayabilir ve varsayılan bileşen doğru ad alanında olduğundan emin olmak için adı belirtin.  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>CtlClockLib denetim kitaplığı ve ctlClock denetimi oluşturmak için  
  
1.  Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje** açmak için **yeni proje** iletişim kutusu.  
  
2.  Visual C# projeleri listesinden seçin **Windows Forms Denetim Kitaplığı** proje şablonu, türü `ctlClockLib` içinde **adı** kutusuna ve ardından **Tamam**.  
  
     Proje adı `ctlClockLib`, kök ad alanı için varsayılan olarak da atanmış. Kök ad derleme bileşenlerinde adlarını nitelemek için kullanılır. Örneğin, iki derleme adlı bileşenleri sağlarsanız `ctlClock`, belirtebilirsiniz, `ctlClock` bileşenini kullanarak `ctlClockLib.ctlClock.`  
  
3.  Çözüm Gezgini'nde sağ **UserControl1.cs**ve ardından **yeniden adlandırma**. Dosya adını değiştirmek `ctlClock.cs`. Tıklatın **Evet** düğmesini code öğesi "UserControl1" yapılan tüm başvuruları yeniden adlandırmak istediğiniz sorulduğunda.  
  
    > [!NOTE]
    >  Varsayılan olarak, bileşik denetim devraldığı <xref:System.Windows.Forms.UserControl> sistem tarafından sağlanan sınıfı. <xref:System.Windows.Forms.UserControl> Sınıf tarafından tüm bileşik denetimler gerekli işlevselliği sunar ve standart yöntemleri ve özellikleri uygular.  
  
4.  Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Windows ekleme denetimleri ve bileşenleri bileşik denetim için  
 Görsel bir arabirim bileşik denetim önemli bir parçasıdır. Bu görsel arabirimi bir veya daha fazla Windows denetimleri Tasarımcı yüzeyine eklenmesi tarafından uygulanır. Aşağıdaki örnekte Windows denetimleri bileşik denetime birleştirme ve işlevselliği uygulamak için kod yazma.  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Bir etiket ve bir Zamanlayıcı, bileşik denetim eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlClock.cs**ve ardından **Görünüm Tasarımcısı**.  
  
2.  İçinde **araç**, genişletin **ortak denetimler** düğümü ve çift tıklatarak **etiket**.  
  
     A <xref:System.Windows.Forms.Label> adlı Denetim `label1` Tasarımcı yüzeyine denetiminizde eklenir.  
  
3.  Tasarımcısı'nda tıklayın **label1**. Özellikler penceresinde aşağıdaki özellikleri ayarlayın.  
  
    |Özellik|Değiştirin|  
    |--------------|---------------|  
    |**Ad**|`lblDisplay`|  
    |**Metin**|`(blank space)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  İçinde **araç**, genişletin **bileşenleri** düğümü ve çift tıklatarak **Zamanlayıcı**.  
  
     Çünkü bir <xref:System.Windows.Forms.Timer> bir bileşen olan çalışma zamanında görsel gösterimi bulunmaz. Bu nedenle, bu tasarım yüzeyine denetimlerle ancak bunun yerine görünmez **Bileşen Tasarımcısı** (tasarımcı yüzeyine altındaki bir Tepsisi).  
  
5.  İçinde **Bileşen Tasarımcısı**, tıklatın **Süreölçer1**ve ardından <xref:System.Windows.Forms.Timer.Interval%2A> özelliğine `1000` ve <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğine `true`.  
  
     <xref:System.Windows.Forms.Timer.Interval%2A> Özelliği denetler sıklığı <xref:System.Windows.Forms.Timer> bileşen çizgilerine. Her zaman `timer1` çizgilerine, bunu çalışan kodu `timer1_Tick` olay. Aralık çizgilerine arasındaki milisaniye sayısını temsil eder.  
  
6.  İçinde **Bileşen Tasarımcısı**, çift **Süreölçer1** gitmek için `timer1_Tick` olayı `ctlClock`.  
  
7.  Aşağıdaki kod örneği benzer şekilde kodu değiştirin. Gelen erişim değiştiricisi değiştirdiğinizden emin olun `private` için `protected`.  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     Bu kod gösterilecek geçerli saati neden olacak `lblDisplay`. Çünkü aralığı `timer1` ayarlandı `1000`, böylece her saniye geçerli saati güncelleştiriliyor her bin milisaniyede bu olay meydana gelir.  
  
8.  Geçersiz kılınabilir sahip olacak şekilde değiştirin `virtual` anahtar sözcüğü. Daha fazla bilgi için aşağıdaki "Devralan bir kullanıcı denetimi" bölümüne bakın.  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="adding-properties-to-the-composite-control"></a>Bileşik Denetim Özellikler ekleme  
 Saat denetiminizi şimdi yalıtan bir <xref:System.Windows.Forms.Label> denetim ve <xref:System.Windows.Forms.Timer> bileşeni, her biri kendi devralınmış özellikler kümesi. Bu denetimlerin ayrı ayrı özellikler denetiminizi sonraki kullanıcılara erişilemeyecek olsa da, oluşturabilir ve uygun kod bloklarını yazarak özel özelliklerini ortaya. Aşağıdaki yordamda, arka plan ve metin rengini değiştirmek kullanıcının denetiminizi özellikler ekleyeceksiniz.  
  
#### <a name="to-add-a-property-to-your-composite-control"></a>Bir özellik için bileşik denetim eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlClock.cs**ve ardından **görünümü kodu**.  
  
     **Kod düzenleyicisinde** için denetiminizi açar.  
  
2.  Bulun `public partial class ctlClock` deyimi. Açılan parantez altındaki (`{)`, aşağıdaki kodu yazın.  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     Bu deyimler oluşturmak üzere olduğunuz özelliklerinin değerlerini depolamak için kullanacağı özel değişkenler oluşturun.  
  
3.  2. adımda değişken bildirimleri altına aşağıdaki kodu yazın.  
  
    ```csharp  
    // Declares the name and type of the property.  
    public Color ClockBackColor  
    {  
        // Retrieves the value of the private variable colBColor.  
        get  
        {  
            return colBColor;  
        }  
        // Stores the selected value in the private variable colBColor, and   
        // updates the background color of the label control lblDisplay.  
        set  
        {  
            colBColor = value;  
            lblDisplay.BackColor = colBColor;     
        }  
    }  
    // Provides a similar set of instructions for the foreground color.  
    public Color ClockForeColor  
    {  
        get  
        {  
            return colFColor;  
        }  
        set  
        {  
            colFColor = value;  
            lblDisplay.ForeColor = colFColor;  
        }  
    }  
    ```  
  
     Önceki kod iki özel özellikler yapar `ClockForeColor` ve `ClockBackColor`, bu denetimin sonraki kullanıcılar tarafından kullanılabilir. `get` Ve `set` deyimleri, depolama ve alma, işlevselliği uygulamak için kodu yanı sıra özellik değeri, özellik için uygun için sağlar.  
  
4.  Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="testing-the-control"></a>Denetim test etme  
 Denetimleri bağımsız uygulamalar değildir; bir kapsayıcıda barındırılmalıdır. Denetimin çalışma zamanı davranışını sınama ve özellikleriyle birlikte çalışma **UserControl Test kapsayıcısı**. Daha fazla bilgi için bkz: [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-your-control"></a>Denetim sınamak için  
  
1.  Projeyi derlemek ve denetiminizin çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.  
  
2.  Test kapsayıcının özellik kılavuzunda bulun `ClockBackColor` özelliği ve renk paletini görüntülenecek özelliği seçin.  
  
3.  Bir renk tıklayarak seçin.  
  
     Denetim arka plan rengini seçtiğiniz renge dönüşür.  
  
4.  Doğrulamak için benzer bir olay dizisi kullanmak `ClockForeColor` özelliği beklendiği gibi çalışmıyor.  
  
     Bu bölümde ve önceki bölümlerde, bileşenleri ve Windows denetimleri nasıl birleştirileceğini gördünüz kodla ve paketleme bileşik denetim biçiminde özel işlevsellik sağlar. Bileşik Denetim ve onu tamamlandıktan sonra Denetim test etme özelliklerinde kullanıma sunmak öğrendiniz. Sonraki bölümde nasıl kullanarak bir devralınan bileşik denetim oluşturulacağını öğreneceksiniz `ctlClock` temel olarak.  
  
## <a name="inheriting-from-a-composite-control"></a>Bileşik denetimden devralma  
 Önceki bölümlerde Windows denetimleri, bileşenleri ve kod yeniden kullanılabilir bileşik denetimlere birleştirmek öğrendiniz. Bileşik Denetim artık bağlı diğer denetimleri oluşturulabilir temel olarak kullanılabilir. Sınıf bir taban sınıftan türetme işlemi adlı *devralma*. Bu bölümde, adlı bileşik denetim oluşturacak `ctlAlarmClock`. Bu denetim kendi üst denetiminden türetilen `ctlClock`. İşlevlerini genişletmek öğreneceksiniz `ctlClock` üst yöntemleri geçersiz kılma ve yeni yöntemleri ve özellikleri ekleyerek.  
  
 Devralınan bir denetim oluşturmanın ilk adımı, üst öğesinden türetilen olmaktır. Bu eylem tüm özellikleri, yöntemleri ve üst denetim grafik özelliklere sahip yeni bir denetim oluşturur, ancak aynı zamanda yeni veya değiştirilmiş işlevselliği eklenmesi için bir temel olarak çalışabilir.  
  
#### <a name="to-create-the-inherited-control"></a>Devralınan denetimi oluşturmak için  
  
1.  Çözüm Gezgini'nde sağ **ctlClockLib**, işaret **Ekle**ve ardından **kullanıcı denetimi**.  
  
     **Yeni Öğe Ekle** iletişim kutusu açılır.  
  
2.  Seçin **devralınan kullanıcı denetimi** şablonu.  
  
3.  İçinde **adı** kutusuna `ctlAlarmClock.cs`ve ardından **Ekle**.  
  
     **Devralma Seçici** iletişim kutusu görüntülenir.  
  
4.  Altında **bileşen adı**, çift **ctlClock**.  
  
5.  Çözüm Gezgini'nde geçerli projeleri göz atın.  
  
    > [!NOTE]
    >  Dosya adında **ctlAlarmClock.cs** geçerli projeye eklendi.  
  
### <a name="adding-the-alarm-properties"></a>Uyarı Özellikler ekleme  
 Özellikler devralınan bir denetimi için bileşik denetim eklenen aynı şekilde eklenir. Şimdi özelliği bildiriminin sözdizimi denetiminize iki özellik eklemek için kullanacağınız: `AlarmTime`, tarih ve saat uyarı olduğu kapalı, Git değerini depolar ve `AlarmSet`, hangi uyarı ayarlanıp ayarlanmadığını gösterilir.  
  
##### <a name="to-add-properties-to-your-composite-control"></a>Bileşik denetiminizi özellikleri eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlAlarmClock**ve ardından **görünümü kodu**.  
  
2.  Bulun `public class` deyimi. Denetim devraldığı Not `ctlClockLib.ctlClock`. Açılan parantez altındaki (`{)` deyimi, aşağıdaki kodu yazın.  
  
    ```csharp  
    private DateTime dteAlarmTime;  
    private bool blnAlarmSet;  
    // These properties will be declared as public to allow future   
    // developers to access them.  
    public DateTime AlarmTime  
    {  
        get  
        {  
            return dteAlarmTime;  
        }  
        set  
        {  
            dteAlarmTime = value;  
        }  
    }  
    public bool AlarmSet  
    {  
        get  
        {  
            return blnAlarmSet;  
        }  
        set  
        {  
            blnAlarmSet = value;  
        }  
    }  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a>Denetim grafik arabirimine ekleme  
 Devralınan denetiminizi öğesinden devralınan denetlemek için aynı olan bir görsel arabirimine sahiptir. Aynı bağlı denetimler, üst denetim olarak sahip, ancak özellikle sunulan sürece bağlı denetimlerin özelliklerini kullanılabilir olmaz. Herhangi bir bileşik denetimi eklediğiniz gibi aynı şekilde devralınan bir bileşik denetim grafik arabirimine ekleyebilir. Uyarı saatin visual arabirimine eklemeye devam etmek için uyarı uyarabilir yükleyen yanar bir etiket denetimi ekleyeceksiniz.  
  
##### <a name="to-add-the-label-control"></a>Etiket denetimi eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlAlarmClock**ve ardından **Görünüm Tasarımcısı**.  
  
     Tasarımcı `ctlAlarmClock` ana pencerede açar.  
  
2.  Denetimin görüntüleme bölümünü tıklatın ve Özellikler penceresini görüntüleyin.  
  
    > [!NOTE]
    >  Tüm özellikleri görüntülenir, ancak bunlar soluklaştırılır. Bu bu özellikleri için yerel gösterir `lblDisplay` ve değiştirilemez veya Özellikler penceresinde erişilebilir. Varsayılan olarak, bu bileşik denetim içinde yer alan denetimleridir `private`, ve bunların özelliklerini herhangi bir yolla erişilemiyor.  
  
    > [!NOTE]
    >  Bileşik denetiminizin sonraki kullanıcıların iç denetimlerinden erişmesini isterseniz, bunları olarak bildirin `public` veya `protected`. Bu, ayarlamak ve uygun kodu kullanarak bileşik denetim içinde yer alan denetimlerin özelliklerini değiştirmek olanak tanır.  
  
3.  Ekleme bir <xref:System.Windows.Forms.Label> denetimi için bileşik denetim.  
  
4.  Fareyle sürükleyin <xref:System.Windows.Forms.Label> kutusunu hemen altındaki denetim. Özellikler penceresinde aşağıdaki özellikleri ayarlayın.  
  
    |Özellik|Ayar|  
    |--------------|-------------|  
    |**Ad**|`lblAlarm`|  
    |**Metin**|**Uyarı!**|  
    |**TextAlign**|`MiddleCenter`|  
    |**Görünür**|`false`|  
  
### <a name="adding-the-alarm-functionality"></a>Uyarı işlevsellik ekleme  
 Önceki yordamlarda, özellikleri ve bileşik denetim alarm işlevselliği sağlayacak bir denetim eklendi. Bu yordamda, alarm saati geçerli zamanın karşılaştırmak için kod ekleyeceksiniz ve aynı alarm Flash olmaları durumunda. Geçersiz kılma tarafından `timer1_Tick` yöntemi `ctlClock` ve ek kod eklemeyi, yeteneğini uzatır `ctlAlarmClock` tüm devralınmış işlevselliğini korurken `ctlClock`.  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a>CtlClock timer1_Tick yöntemi geçersiz kılmak için  
  
1.  İçinde **Kod düzenleyicisinde**, bulun `private bool blnAlarmSet;` deyimi. Hemen altında aşağıdaki deyimini ekleyin.  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2.  İçinde **Kod düzenleyicisinde**, kapanış ayracı bulun (`})` sınıfı sonunda. Küme parantezi hemen önce aşağıdaki kodu ekleyin.  
  
    ```csharp  
    protected override void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Calls the Timer1_Tick method of ctlClock.  
        base.timer1_Tick(sender, e);  
        // Checks to see if the alarm is set.  
        if (AlarmSet == false)  
            return;  
        else  
            // If the date, hour, and minute of the alarm time are the same as  
            // the current time, flash an alarm.   
        {  
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==   
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)  
            {  
                // Sets lblAlarmVisible to true, and changes the background color based on  
                // the value of blnColorTicker. The background color of the label   
                // will flash once per tick of the clock.  
                lblAlarm.Visible = true;  
                if (blnColorTicker == false)   
                {  
                    lblAlarm.BackColor = Color.Red;  
                    blnColorTicker = true;  
                }  
                else  
                {  
                    lblAlarm.BackColor = Color.Blue;  
                    blnColorTicker = false;  
                }  
            }  
            else  
            {  
                // Once the alarm has sounded for a minute, the label is made   
                // invisible again.  
                lblAlarm.Visible = false;  
            }  
        }  
    }  
    ```  
  
     Bu kod ayrıca çeşitli görevleri gerçekleştirir. `override` Deyimi temel denetiminden devralındı yöntemi yerine bu yöntemi kullanmak için Denetim yönlendirir. Bu yöntem çağrıldığında, geçersiz kılmalar harekete geçirerek yöntemi çağırır `base.timer1_Tick` deyimi, tüm işlevleri özgün denetiminde birleştirilmiş sağlayarak bu denetimde çoğaltılamaz. Daha sonra uyarı işlevselliği birleştirmek için ek kod çalıştırır. Uyarı ortaya çıktığında yanıp sönen bir etiket denetimi görünür.  
  
     Alarm saati denetiminizi neredeyse tamamlandı. Kalan tek şey, devre dışı bırakmak için bir yol uygulamaktır. Bunu yapmak için kod ekleyeceksiniz `lblAlarm_Click` yöntemi.  
  
##### <a name="to-implement-the-shutoff-method"></a>Kesici yöntemi uygulamak için  
  
1.  Çözüm Gezgini'nde sağ **ctlAlarmClock.cs**ve ardından **Görünüm Tasarımcısı**.  
  
     Tasarımcısı'nı açar.  
  
2.  Düğme denetimine ekleyin. Düğmenin özelliklerini şu şekilde ayarlayın.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|`btnAlarmOff`|  
    |**Metin**|**Uyarı devre dışı bırak**|  
  
3.  Tasarımcıda çift **btnAlarmOff**.  
  
     **Kod düzenleyicisinde** açılır `private void btnAlarmOff_Click` satır.  
  
4.  Bu yöntem, aşağıdaki kodu benzer şekilde değiştirin.  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5.  Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
### <a name="using-the-inherited-control-on-a-form"></a>Bir Form üzerinde devralınan denetimi kullanma  
 Taban sınıfı denetim test aynı şekilde, devralınan denetim sınayabilirsiniz `ctlClock`: F5 tuşuna basarak projeyi oluşturun ve denetiminizin Çalıştır **UserControl Test kapsayıcısı**. Daha fazla bilgi için bkz: [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Kullanmak için denetim yerleştirmek için bir form üzerinde barındırmak gerekir. Standart bileşik denetim olarak, devralınan bir bileşik denetim tek başına olamaz ve bir form veya diğer kapsayıcı barındırılması gerekir. Bu yana `ctlAlarmClock` daha derinlemesine sahip işlevselliğini, test için ek kod gereklidir. Bu yordamda işlevselliğini sınamak için basit bir program yazacaksınız `ctlAlarmClock`. Ayarlama ve görüntülemek için kod yazacaksınız `AlarmTime` özelliği `ctlAlarmClock`ve devralınan işlevleri test.  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a>Yapı ve test forma denetim ekleme  
  
1.  Çözüm Gezgini'nde sağ **ctlClockLib**ve ardından **yapı**.  
  
2.  Yeni bir ekleme **Windows uygulaması** proje çözüme ve adlandırın `Test`.  
  
3.  Çözüm Gezgini'nde sağ **başvuruları** test projeniz için düğüm. Tıklatın **Başvuru Ekle** görüntülemek için **Başvuru Ekle** iletişim kutusu. Etiketli sekmesini **projeleri**. `ctlClockLib` Proje altında listelenir **proje adı**. Projeyi test projesinin başvuru eklemek için çift tıklayın.  
  
4.  Çözüm Gezgini'nde sağ **Test**ve ardından **yapı**.  
  
5.  İçinde **araç**, genişletin **ctlClockLib bileşenleri** düğümü.  
  
6.  Çift **ctlAlarmClock** bir kopyasını eklemek için `ctlAlarmClock` formunuza.  
  
7.  İçinde **araç**, bulun ve çift tıklatın **DateTimePicker** eklemek için bir <xref:System.Windows.Forms.DateTimePicker> formunuza denetlemek ve ardından ekleyin bir <xref:System.Windows.Forms.Label> çift tıklatarak denetim **etiket**.  
  
8.  Denetimleri form üzerinde uygun bir konuma yerleştirmek için fare kullanın.  
  
9. Bu denetimlerin özelliklerini aşağıdaki şekilde ayarlayın.  
  
    |Denetim|Özellik|Değer|  
    |-------------|--------------|-----------|  
    |`label1`|**Metin**|`(blank space)`|  
    ||**Ad**|`lblTest`|  
    |`dateTimePicker1`|**Ad**|`dtpTest`|  
    ||**Biçimi**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. Tasarımcıda çift **dtpTest**.  
  
     **Kod düzenleyicisinde** açılır `private void dtpTest_ValueChanged`.  
  
11. Aşağıdakine benzer şekilde kodu değiştirin.  
  
    ```csharp  
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)  
    {  
        ctlAlarmClock1.AlarmTime = dtpTest.Value;  
        ctlAlarmClock1.AlarmSet = true;  
        lblTest.Text = "Alarm Time is " +  
            ctlAlarmClock1.AlarmTime.ToShortTimeString();  
    }  
    ```  
  
12. Çözüm Gezgini'nde sağ **Test**ve ardından **başlangıç projesi olarak ayarla**.  
  
13. Üzerinde **hata ayıklama** menüsünde tıklatın **hata ayıklamayı Başlat**.  
  
     Test program başlar. Geçerli saat içinde güncelleştirilir Not `ctlAlarmClock` denetimi ve başlangıç saatini gösterildiği <xref:System.Windows.Forms.DateTimePicker> denetim.  
  
14. Tıklatın <xref:System.Windows.Forms.DateTimePicker> saat, dakika görüntülendiği.  
  
15. Klavye kullanılarak ayarlanan bir dakika tarafından gösterilen geçerli saatten büyük bir değer dakika `ctlAlarmClock`.  
  
     Uyarı ayarı süredir gösterilen `lblTest`. Uyarı ayarı zaman ulaşmak görüntülenen bir süre bekleyin. Görüntülenen saat için uyarı ayarlanmış, saatine ulaştığında `lblAlarm` flash.  
  
16. Tıklayarak alarmı devre dışı bırakma `btnAlarmOff`. Uyarı artık sıfırlayabilir.  
  
     Bu kılavuz temel kavramları sayısı ele. Bileşik Denetim kapsayıcıya denetimleri ve bileşenleri birleştiren bileşik denetim oluşturmak öğrendiniz. Denetiminize özellikleri ekleyin ve özel işlevsellik uygulamak için kod yazma öğrendiniz. Son bölümünde devralma yoluyla belirli bir bileşik denetim işlevselliğini genişletmek ve bu yöntemi geçersiz kılarak konak yöntemleri işlevselliğini alter öğrendiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Bileşenleri ile programlama](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [Bileşen geliştirme izlenecek yollar](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
