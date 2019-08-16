---
title: 'İzlenecek yol: C# ile Bileşik Denetim Yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
ms.openlocfilehash: fa6881614725ddf7628ddc484a9a4130bb23bc77
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040234"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a>İzlenecek yol: Visual C ile bileşik denetim yazma\#

Bileşik denetimler, özel grafik arabirimlerinin oluşturulup yeniden kullanılabilmesi için bir yol sağlar. Bileşik denetim temelde görsel temsili olan bir bileşendir. Bu nedenle, Kullanıcı girişini doğrulayarak, görüntü özelliklerini değiştirerek veya yazar için gereken diğer görevleri gerçekleştirerek işlevselliği genişletebilen bir veya daha fazla Windows Forms denetimi, bileşeni veya kod bloklarında bulunabilir. Bileşik denetimler Windows Forms diğer denetimlerle aynı şekilde yerleştirilebilir. Bu izlenecek yolun ilk bölümünde adlı `ctlClock`basit bir bileşik denetim oluşturursunuz. İzlenecek yolun ikinci bölümünde, devralma `ctlClock` ile işlevlerini genişletebilirsiniz.


## <a name="creating-the-project"></a>Projeyi Oluşturma

Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlamak için adını belirtin ve varsayılan bileşenin doğru ad alanında yer aldığından emin olun.

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>CtlClockLib denetim kitaplığını ve ctlClock denetimini oluşturmak için

1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje** ' ye tıklayarak **Yeni proje** iletişim kutusunu açın.

2. Görsel C# proje listesinden **Windows Forms denetim kitaplığı** proje şablonu ' nu seçin, `ctlClockLib` **ad** kutusuna yazın ve ardından **Tamam**' a tıklayın.

     Proje adı `ctlClockLib`, varsayılan olarak kök ad alanına da atanır. Kök ad alanı, derlemedeki bileşenlerin adlarını nitelemek için kullanılır. Örneğin, iki derleme adlı `ctlClock`bileşenler içeriyorsa, `ctlClock` bileşenini kullanarak`ctlClockLib.ctlClock.`

3. Çözüm Gezgini ' de, **UserControl1.cs**' a sağ tıklayın ve ardından **Yeniden Adlandır**' a tıklayın. Dosya adını olarak `ctlClock.cs`değiştirin. "UserControl1" kod öğesiyle tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet** düğmesine tıklayın.

    > [!NOTE]
    > Varsayılan olarak, bileşik bir denetim sistem tarafından sunulan <xref:System.Windows.Forms.UserControl> sınıftan devralınır. <xref:System.Windows.Forms.UserControl> Sınıfı, tüm bileşik denetimlerin gerektirdiği işlevselliği sağlar ve standart yöntemler ve özellikler uygular.

4. Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Bileşik denetime Windows denetimleri ve bileşenleri ekleme

Görsel arabirim, bileşik denetiminizin temel bir parçasıdır. Bu görsel arabirim, tasarımcı yüzeyine bir veya daha fazla Windows denetimi eklenerek uygulanır. Aşağıdaki gösteride, Windows denetimlerini bileşik denetiminizle birleştirirsiniz ve işlevselliği uygulamak için kod yazabilirsiniz.

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Bileşik denetilemenize bir etiket ve süreölçer eklemek için

1. Çözüm Gezgini ' de, **ctlClock.cs**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

2. **Araç kutusunda** **ortak denetimler** düğümünü genişletin ve ardından **etiket**' e çift tıklayın.

     Tasarımcı <xref:System.Windows.Forms.Label> yüzeyinde denetimciyle adlandırılmış `label1` bir denetim eklenir.

3. Tasarımcıda **Label1**' ye tıklayın. Özellikler penceresi, aşağıdaki özellikleri ayarlayın.

    |Özellik|Değiştir|
    |--------------|---------------|
    |**Ad**|`lblDisplay`|
    |**Metin**|`(blank space)`|
    |**TextAlign**|`MiddleCenter`|
    |**Yazı tipi. boyutu**|`14`|

4. **Araç kutusunda**, **Bileşenler** düğümünü genişletin ve ardından **Zamanlayıcı**' ya çift tıklayın.

     Bir <xref:System.Windows.Forms.Timer> bileşen olduğundan, çalışma zamanında görsel temsili yoktur. Bu nedenle, tasarımcı yüzeyindeki denetimlerde görünmez, ancak **Bileşen tasarımcısında** (tasarımcı yüzeyinin altındaki bir tepsi) değil.

5. **Bileşen tasarımcısında**, **Süreölçer1** <xref:System.Windows.Forms.Timer.Interval%2A> ' a tıklayın ve ardından özelliğini `1000` ve <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini olarak `true`ayarlayın.

     <xref:System.Windows.Forms.Timer.Interval%2A> Özelliği <xref:System.Windows.Forms.Timer> bileşeni işaret eden sıklığı denetler. Her zaman `timer1` Tick, `timer1_Tick` olaydaki kodu çalıştırır. Aralık, zaman işaretleri arasındaki milisaniye sayısını temsil eder.

6. **Bileşen tasarımcısında**, için **Süreölçer1** öğesine çift tıklayarak için `timer1_Tick` `ctlClock`olayına gidin.

7. Kodu aşağıdaki kod örneğine benzer olacak şekilde değiştirin. Erişim değiştiricisini ' dan `private` `protected`' a değiştirdiğinizden emin olun.

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     Bu kod, geçerli saatin ' de `lblDisplay`görüntülenmesine neden olur. Aralığı `timer1` olarak ayarlandığı için `1000`bu olay her bin milisaniyede bir gerçekleşeceğinden, bu nedenle her saniye geçerli saati güncelliyor.

8. Yöntemini `virtual` anahtar sözcüğüyle geçersiz kılınabilir olacak şekilde değiştirin. Daha fazla bilgi için aşağıdaki "Kullanıcı denetiminden devralma" bölümüne bakın.

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.

## <a name="adding-properties-to-the-composite-control"></a>Bileşik denetime özellikler ekleme

Saat denetiminiz artık, her biri <xref:System.Windows.Forms.Label> kendi kendine ait <xref:System.Windows.Forms.Timer> özellikler kümesiyle birlikte bir denetimi ve bileşeni kapsüller. Bu denetimlerin tek tek özelliklerine denetiminizin sonraki kullanıcıları tarafından erişilemese de, uygun kod bloklarını yazarak özel özellikler oluşturabilir ve kullanıma sunabilirsiniz. Aşağıdaki yordamda, denetime, kullanıcının arka plan ve metin rengini değiştirmesini sağlayan özellikler ekleyeceksiniz.

### <a name="to-add-a-property-to-your-composite-control"></a>Bileşik denetimi bir özellik eklemek için

1. Çözüm Gezgini ' de, **ctlClock.cs**' a sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

     Denetiminizin **Kod Düzenleyicisi** açılır.

2. `public partial class ctlClock` İfadesini bulun. Açma küme ayracı`{)`altında, aşağıdaki kodu yazın.

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     Bu deyimler, oluşturmak üzere olduğunuz özelliklerin değerlerini depolamak için kullanacağınız özel değişkenleri oluşturur.

3. 2\. adımdaki değişken bildirimlerinin altına aşağıdaki kodu yazın.

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

     Yukarıdaki kod iki özel özellik `ClockForeColor` yapar ve `ClockBackColor`bu denetimin sonraki kullanıcıları tarafından kullanılabilir. `get` Ve`set` deyimleri, özellik değerinin depolanmasını ve alınmasını, ayrıca özelliğine uygun işlevselliği uygulamak için de kod sağlar.

4. Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.

## <a name="testing-the-control"></a>Denetimi test etme

Denetimler tek başına uygulamalar değildir; Bunlar bir kapsayıcıda barındırılmalıdır. Denetiminizin çalışma zamanı davranışını test edin ve özelliklerini **UserControl Test kapsayıcısı**ile çalıştırın. Daha fazla bilgi için [nasıl yapılır: UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)'un çalışma zamanı davranışını test edin.

### <a name="to-test-your-control"></a>Denetiminizi test etmek için

1. Projeyi derlemek için F5 tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın.

2. Test kapsayıcısının özellik kılavuzunda, `ClockBackColor` özelliğini bulun ve ardından renk paletini göstermek için özelliği seçin.

3. Tıklayarak bir renk seçin.

     Denetiminizin arka plan rengi, seçtiğiniz renge değişir.

4. `ClockForeColor` Özelliğin beklendiği gibi çalıştığını doğrulamak için benzer bir olay dizisi kullanın.

     Bu bölümde ve önceki bölümlerde, bileşik denetim biçiminde özel işlevsellik sağlamak için bileşenlerin ve Windows denetimlerinin kod ve paketleme ile nasıl birleştirilebileceği gördünüz. Birleşik denetidiklerinizin özelliklerini açığa çıkarmak ve tamamlandıktan sonra denetiminizi test etmek için öğrendiniz. Sonraki bölümde, temel olarak kullanarak `ctlClock` devralınmış bir bileşik denetim oluşturmayı öğreneceksiniz.

## <a name="inheriting-from-a-composite-control"></a>Bileşik denetimden devralma

Önceki bölümlerde, Windows denetimlerini, bileşenleri ve kodu yeniden kullanılabilir bileşik denetimlere nasıl birleştirebileceğinizi öğrendiniz. Bileşik denetiminiz artık diğer denetimlerin derlenme temeli olarak kullanılabilir. Temel sınıftan bir sınıfın türeme işlemi *Devralma*olarak adlandırılır. Bu bölümde, adlı `ctlAlarmClock`bir bileşik denetim oluşturacaksınız. Bu denetim, `ctlClock`üst denetiminden türetilecektir. Üst yöntemleri geçersiz kılarak ve yeni yöntemler ve `ctlClock` özellikler ekleyerek işlevselliğini genişletmeyi öğreneceksiniz.

Devralınan bir denetim oluşturmanın ilk adımı onu üst öğesinden türemektir. Bu eylem, üst denetimin tüm özelliklerine, yöntemlerine ve grafiksel özelliklerine sahip yeni bir denetim oluşturur, ancak yeni veya değiştirilmiş işlevselliğin eklenmesi için temel olarak da davranabilir.

### <a name="to-create-the-inherited-control"></a>Devralınan denetimi oluşturmak için

1. Çözüm Gezgini ' de, **ctlClockLib**' a sağ tıklayın, **Ekle**' nin üzerine gelin ve **Kullanıcı denetimi**' ne tıklayın.

     **Yeni Öğe Ekle** iletişim kutusu açılır.

2. **Devralınan Kullanıcı denetimi** şablonunu seçin.

3. **Ad** kutusuna yazın `ctlAlarmClock.cs`ve ardından **Ekle**' ye tıklayın.

     **Devralma Seçicisi** iletişim kutusu görüntülenir.

4. **Bileşen adı**altında **ctlClock**' ye çift tıklayın.

5. Çözüm Gezgini, geçerli projelere göz atabilirsiniz.

    > [!NOTE]
    >  Geçerli projeye **ctlAlarmClock.cs** adlı bir dosya eklendi.

### <a name="adding-the-alarm-properties"></a>Alarm özelliklerini ekleme

Özellikler, devralınan bir denetime, Birleşik bir denetime eklendikçe aynı şekilde eklenir. Şimdi, denetimidir için iki özellik eklemek üzere özellik bildirimi söz dizimini kullanacaksınız: `AlarmTime`bu, uyarının bitiş tarihini ve saatini depolayan ve `AlarmSet`alarmın ayarlanmış olup olmadığını belirtecektir.

#### <a name="to-add-properties-to-your-composite-control"></a>Bileşik denetimi özellikler eklemek için

1. Çözüm Gezgini ' de, **ctlAlarmClock**' a sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

2. `public class` İfadesini bulun. Denetiminizin öğesinden `ctlClockLib.ctlClock`devraldığını unutmayın. Açma küme ayracı (`{)` deyimin altına aşağıdaki kodu yazın.

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

### <a name="adding-to-the-graphical-interface-of-the-control"></a>Denetimin grafik arabirimine ekleme

Devralınan denetiminizin devraldığı denetimle özdeş bir görsel arabirimi vardır. Kendi üst denetimiyle aynı bileşen denetimlerine sahip olur, ancak yapısal denetimlerin özellikleri özellikle gösterilmedikleri sürece kullanılamaz. Devralınan bir bileşik denetimin grafik arabirimine, herhangi bir bileşik denetime ekleyeceğiniz şekilde ekleyebilirsiniz. Alarm saatinizin görsel arabirimine eklemeye devam etmek için, alarm bir işlem olduğunda Flash olacak bir etiket denetimi ekleyeceksiniz.

#### <a name="to-add-the-label-control"></a>Etiket denetimi eklemek için

1. Çözüm Gezgini ' de, **ctlAlarmClock**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

     İçin `ctlAlarmClock` tasarımcı ana pencerede açılır.

2. Denetimin görüntüleme bölümüne tıklayın ve Özellikler penceresi görüntüleyin.

    > [!NOTE]
    > Tüm özellikler görüntülenirken, soluk olurlar. Bu özelliklerin yerel `lblDisplay` olduğunu ve Özellikler penceresi değiştirilemeyeceğini veya erişilmeyeceğini gösterir. Varsayılan olarak, bileşik denetimde `private`bulunan denetimler ve özellikleri herhangi bir şekilde erişilebilir değildir.

    > [!NOTE]
    > Bileşik denetiminizin sonraki kullanıcılarının iç denetimlerine erişimi olmasını istiyorsanız, veya `public` `protected`olarak bildirin. Bu, uygun kodu kullanarak bileşik denetilinizin içindeki denetimlerin özelliklerini ayarlamanıza ve değiştirmenize izin verir.

3. Bileşik denetimi bir <xref:System.Windows.Forms.Label> denetim ekleyin.

4. Fareyi kullanarak <xref:System.Windows.Forms.Label> denetimi, ekran kutusunun hemen altına sürükleyin. Özellikler penceresi, aşağıdaki özellikleri ayarlayın.

    |Özellik|Ayar|
    |--------------|-------------|
    |**Ad**|`lblAlarm`|
    |**Metin**|**Alarm!**|
    |**TextAlign**|`MiddleCenter`|
    |**Görüne**|`false`|

### <a name="adding-the-alarm-functionality"></a>Alarm Işlevlerini ekleme

Önceki yordamlarda, bileşik denetiminizdeki alarm işlevselliğini etkinleştiren Özellikler ve bir denetim eklediniz. Bu yordamda, geçerli saati alarm zamanına göre karşılaştırmak için kod ekleyeceksiniz ve aynı ise, bir alarm Flash için de aynı olduğunda. `timer1_Tick` `ctlAlarmClock` Yöntemini geçersiz kılarak ve buna ek kod ekleyerek, tüm devralınan işlevlerini `ctlClock`korurken özelliğini genişletebilirsiniz. `ctlClock`

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a>CtlClock timer1_Tick yöntemini geçersiz kılmak için

1. **Kod düzenleyicisinde**, `private bool blnAlarmSet;` ifadesini bulun. Hemen hemen altına aşağıdaki ifadeyi ekleyin.

    ```csharp
    private bool blnColorTicker;
    ```

2. **Kod Düzenleyicisi**'nde, kapatma küme ayracını (`})` sınıfının sonundaki) bulun. Küme ayracından hemen önce aşağıdaki kodu ekleyin.

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

     Bu kodun eklenmesi birkaç görevi gerçekleştirir. `override` İfade, denetimi temel denetimden devralınan yöntemin yerine bu yöntemi kullanacak şekilde yönlendirir. Bu yöntem çağrıldığında, `base.timer1_Tick` ifadeyi çağırarak geçersiz kıldığından, özgün denetimde dahil edilen tüm işlevlerin Bu denetimde yeniden üretildiğinden emin olarak çağrılır. Daha sonra alarm işlevselliğini birleştirmek için ek kod çalıştırır. Uyarı oluştuğunda yanıp sönen bir etiket denetimi görünür.

     Alarm saati denetiminiz neredeyse tamamlanmıştır. Kalan tek şey, devre dışı bırakmak için bir yol uygulamaktır. Bunu yapmak için `lblAlarm_Click` yöntemine kod ekleyeceksiniz.

#### <a name="to-implement-the-shutoff-method"></a>Shutoff yöntemini uygulamak için

1. Çözüm Gezgini ' de, **ctlAlarmClock.cs**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

     Tasarımcı açılır.

2. Denetime düğme ekleyin. Düğmenin özelliklerini aşağıdaki gibi ayarlayın.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|`btnAlarmOff`|
    |**Metin**|**Alarmı devre dışı bırak**|

3. Tasarımcı 'da, **btnAlarmOff**' a çift tıklayın.

     **Kod Düzenleyicisi** `private void btnAlarmOff_Click` satıra açılır.

4. Bu yöntemi, aşağıdaki koda benzer olacak şekilde değiştirin.

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.

### <a name="using-the-inherited-control-on-a-form"></a>Bir form üzerinde devralınmış denetimi kullanma

Devralınan denetiminizi, temel sınıf denetimini `ctlClock`sınadığınız şekilde test edebilirsiniz: Projeyi derlemek için F5 tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın. Daha fazla bilgi için [nasıl yapılır: UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)'un çalışma zamanı davranışını test edin.

Denetiminizi kullanmak üzere yerleştirmek için bir form üzerinde barındırmanıza gerek duyarsınız. Standart bir bileşik denetimde olduğu gibi, devralınan bir bileşik denetim tek başına olamaz ve bir formda ya da başka bir kapsayıcıda barındırılmalıdır. Daha büyük bir işlevsellik derinliğine sahipolduğundan,testetmekiçinekkodgereklidir.`ctlAlarmClock` Bu yordamda, işlevselliğini `ctlAlarmClock`test etmek için basit bir program yazacaksınız. `AlarmTime` Özelliğini ayarlamakvegöstermekiçinkodyazacaksınızveonunkendiişlevlerinitestedecektir.`ctlAlarmClock`

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>Denetimi derlemek ve test formuna eklemek için

1. Çözüm Gezgini ' de, **ctlClockLib**' a sağ tıklayın ve ardından **Oluştur**' a tıklayın.

2. Çözüme yeni bir **Windows uygulaması** projesi ekleyin ve bunu `Test`adlandırın.

3. Çözüm Gezgini, test projeniz için **Başvurular** düğümüne sağ tıklayın. Başvuru Ekle iletişim kutusunu göstermek için **Başvuru Ekle** ' ye tıklayın. Etiketli **Projeler**sekmesine tıklayın. Projeniz proje adı altında listelenir. `ctlClockLib` Başvuruyu test projesine eklemek için projeye çift tıklayın.

4. Çözüm Gezgini ' de **Test**' e sağ tıklayın ve ardından **Oluştur**' a tıklayın.

5. **Araç kutusunda** **ctlClockLib Components** düğümünü genişletin.

6. Formunuza bir kopyasını `ctlAlarmClock` eklemek için ctlAlarmClock öğesine çift tıklayın.

7. **Araç kutusunda**, formunuza bir <xref:System.Windows.Forms.DateTimePicker> denetim eklemek için **DateTimePicker** ' ı bulup çift tıklayın ve ardından **etiket**' e çift tıklayarak bir <xref:System.Windows.Forms.Label> denetim ekleyin.

8. Denetimleri form üzerinde uygun bir yerde konumlandırmak için fareyi kullanın.

9. Bu denetimlerin özelliklerini aşağıdaki şekilde ayarlayın.

    |Denetim|Özellik|Değer|
    |-------------|--------------|-----------|
    |`label1`|**Metin**|`(blank space)`|
    ||**Ad**|`lblTest`|
    |`dateTimePicker1`|**Ad**|`dtpTest`|
    ||**Formatını**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. Tasarımcıda **dtpTest**öğesine çift tıklayın.

     **Kod Düzenleyicisi** olarak `private void dtpTest_ValueChanged`açılır.

11. Kodu aşağıdakine benzer olacak şekilde değiştirin.

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. Çözüm Gezgini ' de **Test**' e sağ tıklayın ve ardından **Başlangıç projesi olarak ayarla**' ya tıklayın.

13. Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**.

     Test programı başlar. `ctlAlarmClock` Denetimde geçerli saatin güncelleştirildiğini ve başlangıç saatinin <xref:System.Windows.Forms.DateTimePicker> denetimde gösterildiğini unutmayın.

14. Saatin dakikalarının görüntülendiği yere tıklayın. <xref:System.Windows.Forms.DateTimePicker>

15. Klavyeyi kullanarak, tarafından `ctlAlarmClock`gösterilen geçerli saatten bir dakika daha büyük bir değer ayarlayın.

     Uyarı ayarının zamanı içinde `lblTest`gösterilir. Uyarı ayarı zamanına ulaşmak için, görüntülenecek sürenin bekleyin. Görünen süre, alarmın ayarlandığı zamana ulaştığında, `lblAlarm` Flash olur.

16. Tıklayarak `btnAlarmOff`uyarıyı kapatın. Şimdi uyarıyı sıfırlayabilirsiniz.

     Bu izlenecek yol, bir dizi temel kavramı kapsamıştır. Bir bileşik denetim kapsayıcısına denetimleri ve bileşenleri birleştirerek bileşik bir denetim oluşturmayı öğrendiniz. Denetime Özellik eklemeyi ve özel işlevsellik uygulamak için kod yazmayı öğrendiniz. Son bölümde, belirli bir bileşik denetimin işlevselliğini devralma yoluyla genişletmeyi ve bu yöntemleri geçersiz kılarak ana bilgisayar yöntemlerinin işlevselliğini değiştirmeyi öğrendiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
- [Nasıl yapılır: Araç kutusu öğelerini Seç Iletişim kutusunda bir denetim görüntüle](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [İzlenecek yol: Görsel ile Windows Forms denetiminden devralmaC#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
