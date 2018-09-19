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
ms.openlocfilehash: 5f8384140b813400e106ad959684264304541c93
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45990058"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a>İzlenecek yol: Visual C# İle Bileşik Denetim Yazma #
Bileşik denetimler, özel bir grafik arabirim oluşturulabilir yeniden ve bir yöntemdir. Bileşik Denetim aslında bir görsel bir temsili ile bileşenidir. Bu nedenle, bir veya daha fazla Windows Forms denetimleri, bileşenleri veya kullanıcı girişini doğrulama, görüntü özelliklerini değiştirerek veya yazar tarafından gereken diğer görevleri gerçekleştirme işlevselliğini genişletebildiği kod bloklarını oluşabilir. Bileşik denetimler, diğer denetimlerle aynı şekilde Windows formlarında yerleştirilebilir. Bu kılavuzun ilk bölümünde oluşturduğunuz adlı basit bir bileşik denetim `ctlClock`. İzlenecek yol ikinci kısmında, işlevlerini genişletmek `ctlClock` devralma yoluyla.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlayın ve varsayılan bileşeni doğru ad alanı içinde olmasını sağlamak için adını belirtin.  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>CtlClockLib denetim kitaplığı ve ctlClock denetimi oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje** açmak için **yeni proje** iletişim kutusu.  
  
2.  Visual C# projelerinin listesinden **Windows Forms Denetim Kitaplığı** proje şablonu, türü `ctlClockLib` içinde **adı** kutusuna ve ardından **Tamam**.  
  
     Proje adı `ctlClockLib`, aynı zamanda kök ad alanı için varsayılan olarak atanır. Kök ad alanı, bileşenleri derleme içindeki adlarını nitelemek için kullanılır. Örneğin, iki derleme adlı bileşenleri sağlarsanız `ctlClock`, belirtebilirsiniz, `ctlClock` bileşenini kullanma `ctlClockLib.ctlClock.`  
  
3.  Çözüm Gezgini'nde sağ **UserControl1.cs**ve ardından **Yeniden Adlandır**. İçin dosya adını değiştirerek `ctlClock.cs`. Tıklayın **Evet** yaptığınız kod öğesi "UserControl1" için tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda düğmesi.  
  
    > [!NOTE]
    >  Bileşik denetim varsayılan olarak, devralınan <xref:System.Windows.Forms.UserControl> sistem tarafından sağlanan sınıfı. <xref:System.Windows.Forms.UserControl> Sınıfı tüm bileşik denetimler tarafından gerekli işlevselliği sunar ve standart yöntemleri ve özellikleri uygular.  
  
4.  Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Windows ekleme denetimleri ve bileşenleri bileşik denetim  
 Görsel bir arabirim, bileşik denetim önemli bir parçasıdır. Bu görsel arabirim Tasarımcı yüzeyine bir veya daha fazla Windows denetimleri eklenmesini tarafından uygulanır. Aşağıdaki örnekte, Windows denetimleri, bileşik denetime eklemek ve işlevselliği uygulamak için kod yazın.  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Bir etiket ve Zamanlayıcı bileşik denetiminize eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlClock.cs**ve ardından **Görünüm Tasarımcısı**.  
  
2.  İçinde **araç kutusu**, genişletme **ortak denetimleri** düğüm gittikten sonra çift tıklayarak **etiket**.  
  
     A <xref:System.Windows.Forms.Label> adlı Denetim `label1` Tasarımcı yüzeyinde, denetimi eklenir.  
  
3.  Tasarımcıda **label1**. Özellikler penceresinde, aşağıdaki özellikleri ayarlayın.  
  
    |Özellik|Değiştirin|  
    |--------------|---------------|  
    |**Ad**|`lblDisplay`|  
    |**Metin**|`(blank space)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  İçinde **araç kutusu**, genişletme **bileşenleri** düğüm gittikten sonra çift tıklayarak **Zamanlayıcı**.  
  
     Çünkü bir <xref:System.Windows.Forms.Timer> bir bileşen çalışma zamanında görsel bir temsili sahiptir. Bu nedenle, bu Tasarımcı yüzeyine denetimler ile ancak bunun yerine görünmez **Bileşen Tasarımcısı** (tasarımcı yüzeyine alt kısmındaki Tepsisi).  
  
5.  İçinde **Bileşen Tasarımcısı**, tıklayın **Süreölçer1**ve ardından <xref:System.Windows.Forms.Timer.Interval%2A> özelliğini `1000` ve <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `true`.  
  
     <xref:System.Windows.Forms.Timer.Interval%2A> Özelliği sıklığı denetleyen <xref:System.Windows.Forms.Timer> bileşen işaretleri. Her zaman `timer1` saat tıklaması, çalışırken kod `timer1_Tick` olay. Aralık işaretleri arasındaki milisaniye sayısını temsil eder.  
  
6.  İçinde **Bileşen Tasarımcısı**, çift **Süreölçer1** gitmek için `timer1_Tick` olayı `ctlClock`.  
  
7.  Kodu aşağıdaki kod örneği benzeyecek şekilde değiştirin. Gelen erişim değiştiricisi değiştirdiğinizden emin olun `private` için `protected`.  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     Bu kodun geçerli saate göre gösterilecek neden olur `lblDisplay`. Çünkü aralığı `timer1` ayarlandı `1000`, bu olay, böylece her saniye geçerli saati güncelleştiriliyor her bin milisaniye meydana gelir.  
  
8.  İle geçersiz kılınabilir olmasını yöntemi Değiştir `virtual` anahtar sözcüğü. Daha fazla bilgi için "Devralan bir kullanıcı denetimi" bölümüne bakın.  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="adding-properties-to-the-composite-control"></a>Bileşik denetime özellik ekleme  
 Saat denetiminiz artık kapsülleyen bir <xref:System.Windows.Forms.Label> denetimi ve bir <xref:System.Windows.Forms.Timer> bileşeni, her biri kendi devralınan özellikler kümesi. Bu denetimlerin özelliklerini bireysel denetiminizin sonraki kullanıcılar için erişilebilir değil ancak oluşturabilir ve uygun blok kod yazarak özel özellikler kullanıma sunar. Aşağıdaki yordamda, metin ve arka plan rengini değiştirmek kullanıcının denetiminize özellikler ekleyeceksiniz.  
  
#### <a name="to-add-a-property-to-your-composite-control"></a>Bileşik denetiminiz için bir özellik eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlClock.cs**ve ardından **kodu görüntüle**.  
  
     **Kod Düzenleyicisi** denetiminiz açılır.  
  
2.  Bulun `public partial class ctlClock` deyimi. Açılış ayracından altında (`{)`, aşağıdaki kodu yazın.  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     Bu deyimler oluşturmak üzere olduğunuz özelliklerinin değerlerini depolamak için kullanılacak özel değişkenleri oluşturun.  
  
3.  2. adımda bir değişken bildirimlerini altına aşağıdaki kodu yazın.  
  
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
  
     Yukarıdaki kod, iki özel özellikler yapar `ClockForeColor` ve `ClockBackColor`, bu denetimin sonraki kullanıcılar tarafından kullanılabilir. `get` Ve `set` deyimleri, depolama ve alma işlevselliğini uygulamak için kod yanı sıra özellik değeri, özellik için uygun sağlayın.  
  
4.  Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="testing-the-control"></a>Denetimini test etme  
 Denetimleri, tek başına uygulamalar değildir; Bunlar, bir kapsayıcıda barındırılan gerekir. Denetimin çalışma zamanı davranışını sınama ve özellikleriyle birlikte çalışma **UserControl Test kapsayıcısı**. Daha fazla bilgi için [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-your-control"></a>Denetiminiz test etmek için  
  
1.  Projeyi oluşturmak ve denetim çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.  
  
2.  Test kapsayıcının özellik kılavuzunda bulun `ClockBackColor` özelliği ve renk paletini görüntülenecek özelliği seçin.  
  
3.  Tıklayarak bir renk seçin.  
  
     Denetim arka plan rengi, seçtiğiniz rengine değiştirir.  
  
4.  Doğrulamak için benzer bir olay dizisi kullanan `ClockForeColor` özelliği beklendiği gibi çalışmıyor.  
  
     Bu bölümde ve önceki bölümlerde, bileşenleri ve Windows denetimleri nasıl birleştirileceğini gördünüz kodla ve paketleme bileşik denetim biçiminde özel işlevsellik sağlamak için. Bileşik Denetim ve denetim, tamamlandıktan sonra test etme özellikleri göstermek öğrendiniz. Sonraki bölümde kullanarak bir devralınan bileşik denetim oluşturmak hakkında bilgi edineceksiniz `ctlClock` temel olarak.  
  
## <a name="inheriting-from-a-composite-control"></a>Bileşik Denetim devralıyor  
 Önceki bölümlerde Windows denetimleri, bileşenleri ve kod yeniden kullanılabilir bileşik denetimler birleştirmek öğrendiniz. Bileşik Denetim artık diğer denetimlerin oluşturulabilir, bir temel olarak kullanılabilir. Sınıf bir taban sınıftan türetme işlemine denir *devralma*. Bu bölümde, adlı bileşik denetim oluşturacaksınız `ctlAlarmClock`. Bu denetim, üst denetiminden elde edilir `ctlClock`. Genişletmek öğreneceksiniz `ctlClock` üst yöntemleri geçersiz kılma ve yeni yöntemleri ve özellikleri ekleme.  
  
 Devralınan bir denetim oluşturmanın ilk adımı, üst öğesinden türetilen sağlamaktır. Bu eylem, tüm özellikleri, yöntemleri ve üst denetimin grafik özelliklerine sahip yeni bir denetim oluşturur, ancak yeni veya değiştirilmiş işlevselliği eklenmesi için temel olarak da hareket.  
  
#### <a name="to-create-the-inherited-control"></a>Devralınan bir denetim oluşturmak için  
  
1.  Çözüm Gezgini'nde sağ **ctlClockLib**, işaret **Ekle**ve ardından **kullanıcı denetimi**.  
  
     **Yeni Öğe Ekle** iletişim kutusu açılır.  
  
2.  Seçin **devralınan kullanıcı denetimi** şablonu.  
  
3.  İçinde **adı** kutusuna `ctlAlarmClock.cs`ve ardından **Ekle**.  
  
     **Devralma Seçici** iletişim kutusu görüntülenir.  
  
4.  Altında **bileşen adı**, çift **ctlClock**.  
  
5.  Çözüm Gezgini içinde geçerli projeleri göz atın.  
  
    > [!NOTE]
    >  Dosya adında **ctlAlarmClock.cs** geçerli projeye eklendi.  
  
### <a name="adding-the-alarm-properties"></a>Uyarı özellikleri ekleme  
 Bileşik denetim için eklenen aynı şekilde, devralınan bir denetim için özellikler eklenir. Şimdi iki özellik denetiminize eklemek için özellik bildirimi sözdizimi kullanır: `AlarmTime`, tarih ve saat alarma olan kapalı, Git değerini depolar ve `AlarmSet`, hangi uyarı ayarlanıp ayarlanmadığını gösterecektir.  
  
##### <a name="to-add-properties-to-your-composite-control"></a>Özellikler birleşik denetiminize eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlAlarmClock**ve ardından **kodu görüntüle**.  
  
2.  Bulun `public class` deyimi. Denetiminiz devralınan Not `ctlClockLib.ctlClock`. Açılış ayracından altında (`{)` deyimi, aşağıdaki kodu yazın.  
  
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
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a>Grafik arabirimine denetimi ekleme  
 Devralınan denetim devraldığı denetlemek için aynı olan görsel bir arabirim sahiptir. Aynı bağlı denetimler, üst denetim olarak sahiptir, ancak özel olarak sunulan sürece bağlı denetimlerin özelliklerini kullanılabilir olmayacak. Herhangi bir bileşik denetimi olduğu gibi aynı şekilde devralınan bir bileşik denetim grafik arabirimine ekleyebilir. Uyarı Saatin görsel arabirim olarak eklemeye devam etmek için alarm uyarabilir yükleyen yanar etiket denetimi ekleyeceksiniz.  
  
##### <a name="to-add-the-label-control"></a>Etiket denetimi eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlAlarmClock**ve ardından **Görünüm Tasarımcısı**.  
  
     Tasarımcı için `ctlAlarmClock` ana penceresinde açılır.  
  
2.  Denetimin görüntüleme kısmına tıklayın ve Özellikler penceresini görüntüleyin.  
  
    > [!NOTE]
    >  Tüm özellikler görüntülenir, ancak bunlar soluklaştırılır. Bu, bu özellikleri için yerel gösterir `lblDisplay` ve değiştirilemez veya Özellikler penceresinde erişilebilir. Varsayılan olarak, bu bileşik denetiminde bulunan denetimlerdir `private`, ve bunların özelliklerini herhangi bir yolla erişilebilir değildir.  
  
    > [!NOTE]
    >  Bileşik denetiminizin sonraki kullanıcıların kendi iç denetimleri erişmesini isterseniz, bunları olarak bildirin `public` veya `protected`. Bu, ayarlamak ve uygun kodu kullanarak bileşik denetiminizin içinde yer alan denetimlerin özelliklerini değiştirmek olanak tanır.  
  
3.  Ekleme bir <xref:System.Windows.Forms.Label> denetimi için bileşik denetim.  
  
4.  Fareyle sürükleyin <xref:System.Windows.Forms.Label> görüntüleme kutusunun hemen altındaki denetimi. Özellikler penceresinde, aşağıdaki özellikleri ayarlayın.  
  
    |Özellik|Ayar|  
    |--------------|-------------|  
    |**Ad**|`lblAlarm`|  
    |**Metin**|**Uyarı!**|  
    |**TextAlign**|`MiddleCenter`|  
    |**Görünür**|`false`|  
  
### <a name="adding-the-alarm-functionality"></a>Uyarı işlevsellik ekleme  
 Önceki yordamlarda, özellikleri ve bileşik denetim uyarısı işlevselliği sağlayan bir denetimi eklendi. Bu yordamda, alarm saati geçerli saate karşılaştırmak için kod ekleyeceksiniz ve aynı alarm Flash olmaları durumunda. Geçersiz kılma tarafından `timer1_Tick` yöntemi `ctlClock` ve ek kod ekleme, yeteneğini genişletecek `ctlAlarmClock` tüm devralınan işlevselliğini korurken `ctlClock`.  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a>CtlClock timer1_Tick yöntemi geçersiz kılmak için  
  
1.  İçinde **Kod Düzenleyicisi**, bulun `private bool blnAlarmSet;` deyimi. Hemen altında aşağıdaki deyimi ekleyin.  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2.  İçinde **Kod Düzenleyicisi**, kapatma küme ayracından bulun (`})` sınıfı sonunda. Küme ayracı hemen önce aşağıdaki kodu ekleyin.  
  
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
  
     Bu kodu eklenmesi birkaç görev gerçekleştirir. `override` Deyimi temel denetiminden devralındı yöntemi yerine bu yöntemi kullanmak için denetimi yönlendirir. Bu yöntem çağrıldığında, onu geçersiz kılar çağırarak yöntemini çağırır `base.timer1_Tick` deyimi, tüm işlevlerin özgün denetiminde dahil sağlayarak bu denetimde çoğaltılamaz. Ardından, uyarı işlevselliği eklemek için ek kod çalıştırır. Uyarı oluştuğunda, yanıp sönen bir etiket denetimi görünür.  
  
     Uyarı saat denetiminiz hemen tamamlanır. Kalan tek şey, devre dışı bırakmak için bir yol uygulamaktır. Bunu yapmak için kod ekleyeceksiniz `lblAlarm_Click` yöntemi.  
  
##### <a name="to-implement-the-shutoff-method"></a>Kesici yöntemi uygulamak için  
  
1.  Çözüm Gezgini'nde sağ **ctlAlarmClock.cs**ve ardından **Görünüm Tasarımcısı**.  
  
     Tasarımcısı açılır.  
  
2.  Bir düğme denetimi ekleyin. Düğmenin özelliklerini şu şekilde ayarlayın.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|`btnAlarmOff`|  
    |**Metin**|**Uyarı devre dışı bırak**|  
  
3.  Tasarımcıda çift **btnAlarmOff**.  
  
     **Kod Düzenleyicisi** açılır `private void btnAlarmOff_Click` satır.  
  
4.  Bu yöntem, aşağıdaki koda benzer şekilde değiştirin.  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5.  Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
### <a name="using-the-inherited-control-on-a-form"></a>Devralınan Form denetimi kullanma  
 Devralınan denetim temel sınıf denetim test aynı şekilde test edebilirsiniz `ctlClock`: F5 tuşuna basarak projeyi oluşturun ve denetim Çalıştır **UserControl Test kapsayıcısı**. Daha fazla bilgi için [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Denetiminizi kullanmak için koymak için bir form üzerinde barındırmak gerekir. Devralınan bir bileşik denetim standart bileşik denetim gibi tek başına duramaz ve bir form veya diğer kapsayıcı içinde barındırılması gerekir. Bu yana `ctlAlarmClock` daha derinlemesine sahip, işlevselliğini test etmek için ek kod gereklidir. Bu yordamda işlevselliğini test etmek için basit bir program yazacak `ctlAlarmClock`. Ayarlayın ve görüntülemek için kod yazacaksınız `AlarmTime` özelliği `ctlAlarmClock`ve iç işlevleri test eder.  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a>Derleme ve test forma denetim ekleme  
  
1.  Çözüm Gezgini'nde sağ **ctlClockLib**ve ardından **yapı**.  
  
2.  Yeni bir **Windows uygulama** çözüme proje ve adlandırın `Test`.  
  
3.  Çözüm Gezgini'nde sağ **başvuruları** test projeniz için düğüm. Tıklayın **Başvuru Ekle** görüntülenecek **Başvuru Ekle** iletişim kutusu. Etiketli sekmesini **projeleri**. `ctlClockLib` Projesi altında listelenir **proje adı**. Projeyi test projesinin başvuru eklemek için çift tıklayın.  
  
4.  Çözüm Gezgini'nde sağ **Test**ve ardından **yapı**.  
  
5.  İçinde **araç kutusu**, genişletme **ctlClockLib bileşenleri** düğümü.  
  
6.  Çift **ctlAlarmClock** bir kopyasını eklemek için `ctlAlarmClock` formunuza.  
  
7.  İçinde **araç kutusu**, bulun ve çift **DateTimePicker** eklemek için bir <xref:System.Windows.Forms.DateTimePicker> Formunuza denetim ve ardından eklemek bir <xref:System.Windows.Forms.Label> denetimi çift tıklayarak **etiketi**.  
  
8.  Fare bir kullanışlı yerde form üzerinde denetimleri konumlandırmak için kullanın.  
  
9. Bu denetimin özelliklerini şu şekilde ayarlayın.  
  
    |Denetim|Özellik|Değer|  
    |-------------|--------------|-----------|  
    |`label1`|**Metin**|`(blank space)`|  
    ||**Ad**|`lblTest`|  
    |`dateTimePicker1`|**Ad**|`dtpTest`|  
    ||**Biçim**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. Tasarımcıda çift **dtpTest**.  
  
     **Kod Düzenleyicisi** açılır `private void dtpTest_ValueChanged`.  
  
11. Kodu aşağıdakine benzer şekilde değiştirin.  
  
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
  
13. Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**.  
  
     Test program başlar. Geçerli saat içinde güncelleştirilir Not `ctlAlarmClock` denetimi ve başlangıç saatini gösterildiği <xref:System.Windows.Forms.DateTimePicker> denetimi.  
  
14. Tıklayın <xref:System.Windows.Forms.DateTimePicker> saat, dakika burada görüntülenir.  
  
15. Klavyeyi kullanarak, bir dakika tarafından gösterilen geçerli saatten büyük bir değer dakika ayarlamak `ctlAlarmClock`.  
  
     Uyarı ayar için zaman gösterilen `lblTest`. Uyarı ayarını zaman ulaşmak görüntülenen saat için bekleyin. Görüntülenen saat için uyarı ayarlanır, bir zaman geldiğinde `lblAlarm` flash.  
  
16. Alarmın tıklatarak açın `btnAlarmOff`. Uyarı artık sıfırlayabilir.  
  
     Bu izlenecek yol, bir dizi temel kavramları kapsamında. Bileşik Denetim kapsayıcıya denetimleri ve Bileşenleri'ni birleştirerek bileşik denetim oluşturulacağını öğrendiniz. Özellikleri denetiminize eklemek ve özel işlevselliği uygulamak üzere kod yazmak için öğrendiniz. Son bölümde, devralma yoluyla belirli bir bileşik denetim işlevlerini genişletmek ve bu yöntemi geçersiz kılarak konak yöntemleri işlevlerini değiştirmek için öğrendiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Bileşenler ile programlama](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [Bileşen yazma izlenecek yolları](https://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
