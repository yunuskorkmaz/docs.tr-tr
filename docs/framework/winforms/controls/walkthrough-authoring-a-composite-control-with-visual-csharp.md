---
title: 'İzlenecek yol: Visual C# İle Bileşik Denetim Yazma'
ms.date: 03/30/2017
dev_langs:
- CSharp
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ad9aad026a1a6a1266845736d7651db77fd5d5c
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546730"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a>İzleme: C ile Bileşik Kontrol Yazma\#

Bileşik denetimler, özel grafik arabirimlerinin oluşturulup yeniden kullanılabileceğini niçin sağlar. Bileşik denetim aslında görsel gösterimi olan bir bileşendir. Bu nedenle, kullanıcı girişini doğrulayarak, görüntü özelliklerini değiştirerek veya yazarın gerektirdiği diğer görevleri gerçekleştirerek işlevselliği genişletebilecek bir veya daha fazla Windows Forms denetimi, bileşenleri veya kod bloklarından oluşabilir. Bileşik denetimler, Windows Formlar'a diğer denetimler gibi yerleştirilebilir. Bu izbin ilk bölümünde, '. `ctlClock` Gözden geçirme nin ikinci bölümünde, devralma `ctlClock` yoluyla işlevselliğini genişletirsiniz.

## <a name="create-the-project"></a>Proje oluşturma

Yeni bir proje oluşturduğunuzda, kök ad alanını, derleme adını ve proje adını ayarlamak ve varsayılan bileşenin doğru ad alanında olmasını sağlamak için adını belirtirsiniz.

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>ctlClockLib denetim kitaplığını ve ctlClock denetimini oluşturmak için

1. Visual Studio'da, yeni bir **Windows Forms Control Library** projesi oluşturun ve adını **CtlClockLib**olarak adlandırın.

     Proje adı, `ctlClockLib`varsayılan olarak kök ad alanına da atanır. Kök ad alanı, derlemedeki bileşenlerin adlarını nitelemek için kullanılır. Örneğin, iki derleme adlandırılmış `ctlClock`bileşenler sağlıyorsa, bileşeninizi `ctlClock``ctlClockLib.ctlClock.`

2. **Çözüm Gezgini'nde**, **UserControl1.cs**sağ tıklatın ve sonra **Yeniden Adlandır'ı**tıklatın. Dosya adını `ctlClock.cs`' la değiştirin "UserControl1" kod öğesine yapılan tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet** düğmesini tıklatın.

    > [!NOTE]
    > Varsayılan olarak, bileşik denetim sistem <xref:System.Windows.Forms.UserControl> tarafından sağlanan sınıftan devralır. Sınıf, <xref:System.Windows.Forms.UserControl> tüm bileşik denetimler tarafından gerekli işlevselliği sağlar ve standart yöntem ve özellikleri uygular.

3. **Dosya** menüsünde, projeyi kaydetmek için **Tümlerini Kaydet'i** tıklatın.

## <a name="add-windows-controls-and-components-to-the-composite-control"></a>Bileşik Denetime Windows Denetimleri ve Bileşenleri Ekleme

Görsel arayüz, bileşik denetiminizin önemli bir parçasıdır. Bu görsel arabirim, tasarımcı yüzeyine bir veya daha fazla Windows denetimi nin eklenmesiyle uygulanır. Aşağıdaki gösteride, Windows denetimlerini bileşik denetiminize dahil eder ve işlevselliği uygulamak için kod yazarsınız.

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Bileşik denetiminize Etiket ve Zamanlayıcı eklemek için

1. **Çözüm Gezgini'nde**, **ctlClock.cs**sağ tıklatın ve ardından **Tasarımcıyı Görüntüle'yi**tıklatın.

2. Araç **Kutusunda,** Ortak **Denetimler** düğümlerini genişletin ve ardından **Etiket'i**çift tıklatın.

     Tasarımcı <xref:System.Windows.Forms.Label> yüzeyindeki denetiminize adlandırılmış `label1` bir denetim eklenir.

3. Tasarımcıda **label1'e**tıklayın. Özellikler penceresinde aşağıdaki özellikleri ayarlayın.

    |Özellik|Şununla değiştirin|
    |--------------|---------------|
    |**Adı**|`lblDisplay`|
    |**Metin**|`(blank space)`|
    |**Textalign**|`MiddleCenter`|
    |**Yazı Tipi.Boyut**|`14`|

4. Araç **Kutusunda,** **Bileşenler** düğümlerini genişletin ve ardından **Zamanlayıcı'yı**çift tıklatın.

     A <xref:System.Windows.Forms.Timer> bir bileşen olduğundan, çalışma zamanında görsel gösterimi yoktur. Bu nedenle, tasarımcı yüzeyindeki denetimlerde değil, Bileşen **Tasarımcısı'nda** (tasarımcı yüzeyinin alt kısmında ki tepsi) görünür.

5. Bileşen **Tasarımcısı'** nda **timer1'i**tıklatın <xref:System.Windows.Forms.Timer.Interval%2A> ve `1000` sonra <xref:System.Windows.Forms.Timer.Enabled%2A> özelliği `true`ve özelliği .

     Özellik, <xref:System.Windows.Forms.Timer.Interval%2A> bileşenin <xref:System.Windows.Forms.Timer> işleme sıklığını denetler. Her `timer1` işleninher, `timer1_Tick` olaydaki kodu çalıştırıyor. Aralık, keneler arasındaki milisaniye sayısını gösterir.

6. Bileşen **Tasarımcısı,** çift **tıklatma zamanlayıcı1** `timer1_Tick` için etkinliğe gitmek için `ctlClock`.

7. Kodu, aşağıdaki kod örneğine benzeyecek şekilde değiştirin. Erişim değiştiriciyi ' den `private` ' `protected`e değiştirdiğinizden emin olun

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     Bu kod, geçerli saatin 'de `lblDisplay`gösterilmesine neden olur. Aralığı `timer1` ayarlandı çünkü `1000`, Bu olay her bin milisaniye meydana gelecek, böylece her saniye geçerli zamanı güncelleştirerek.

8. Yöntemi anahtar kelimeyle geçersiz kılınacak şekilde değiştirin. `virtual` Daha fazla bilgi için aşağıdaki "Kullanıcı Denetiminden Devralma" bölümüne bakın.

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. **Dosya** menüsünde, projeyi kaydetmek için **Tümlerini Kaydet'i** tıklatın.

## <a name="add-properties-to-the-composite-control"></a>Bileşik Denetime Özellikler Ekleme

Saat denetiminiz artık her biri <xref:System.Windows.Forms.Label> kendi <xref:System.Windows.Forms.Timer> doğal özelliklerine sahip bir denetim ve bileşeni kapsüller. Bu denetimlerin tek tek özellikleri denetiminizin sonraki kullanıcıları tarafından erişilemese de, uygun kod bloklarını yazarak özel özellikler oluşturabilir ve ortaya çıkarabilirsiniz. Aşağıdaki yordamda, denetiminize kullanıcının arka plan ve metnin rengini değiştirmesini sağlayan özellikler eklersiniz.

### <a name="to-add-a-property-to-your-composite-control"></a>Bileşik denetiminize özellik eklemek için

1. **Çözüm Gezgini'nde**, **ctlClock.cs**sağ tıklatın ve ardından **Kodu Görüntüle'yi**tıklatın.

     Denetiminiz için **Kod Düzenleyicisi** açılır.

2. İfadeyi `public partial class ctlClock` bulun. Açılış ayracının`{)`altında ( , aşağıdaki kodu yazın.

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     Bu ifadeler, oluşturmak üzere olduğunuz özelliklerin değerlerini depolamak için kullanacağınız özel değişkenleri oluşturur.

3. Adım 2'den değişken bildirimleri altında aşağıdaki kodu girin veya yapıştırın.

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

     Önceki kod iki özel özellik `ClockForeColor` `ClockBackColor`yapar ve bu denetimin sonraki kullanıcıları tarafından kullanılabilir. Ve `get` `set` ifadeler depolama ve özellik değerinin alınması yanı sıra özellik için uygun işlevselliği uygulamak için kod sağlar.

4. **Dosya** menüsünde, projeyi kaydetmek için **Tümlerini Kaydet'i** tıklatın.

## <a name="test-the-control"></a>Denetimi Test Edin

Denetimler tek başına uygulamalar değildir; bir konteynerde barındırılmalıdır. Denetiminizin çalışma zamanı davranışını test edin ve **özelliklerini UserControl Test Kapsayıcısı**ile çalıştırın. Daha fazla bilgi için [bkz: UserControl'un Çalışma Zamanı Davranışını Test Edin.](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

### <a name="to-test-your-control"></a>Denetiminizi test etmek için

1. Projeyi oluşturmak ve denetiminizi **UserControl Test**Konteyneri'nde çalıştırmak için **F5** tuşuna basın.

2. Test kapsayıcısının özellik ızgarasında, `ClockBackColor` özelliği bulun ve ardından renk paletini görüntülemek için özelliği seçin.

3. Tıklatarak bir renk seçin.

   Denetiminizin arka plan rengi seçtiğiniz renge dönüşür.

4. `ClockForeColor` Özelliğin beklendiği gibi çalıştığını doğrulamak için benzer bir olaylar dizisi kullanın.

   Bu bölümde ve önceki bölümlerde, bileşenlerin ve Windows denetimlerinin bileşik denetim biçiminde özel işlevsellik sağlamak için kod ve paketlemeyle nasıl birleştirilebildiğini gördünüz. Bileşik denetiminizdeki özellikleri ve denetiminizi tamamlandıktan sonra nasıl sınayabileceğinizi öğrendiniz. Bir sonraki bölümde, temel olarak kullanarak `ctlClock` devralınan bir bileşik denetimin nasıl oluşturacağınızı öğreneceksiniz.

## <a name="inherit-from-a-composite-control"></a>Bileşik Denetimden Devralma

Önceki bölümlerde, Windows denetimlerini, bileşenlerini ve kodu yeniden kullanılabilir bileşik denetimlerde nasıl birleştirdiğinizi öğrendiniz. Kompozit denetiminiz artık diğer denetimlerin üzerine inşa edilebilen bir üs olarak kullanılabilir. Bir taban sınıftan bir sınıf türetme *işlemine devralma*denir. Bu bölümde, '. `ctlAlarmClock` Bu denetim, üst denetiminden `ctlClock`türetilecek. Üst yöntemleri geçersiz `ctlClock` kılarak ve yeni yöntemler ve özellikler ekleyerek işlevselliğini genişletmeyi öğreneceksiniz.

Devralınan bir denetim oluşturmanın ilk adımı, onu üst öğesinden elde etmektir. Bu eylem, üst denetimin tüm özelliklerine, yöntemlerine ve grafik özelliklerine sahip, ancak yeni veya değiştirilmiş işlevselliğin eklenmesi için bir temel olarak da hareket edebilen yeni bir denetim oluşturur.

### <a name="to-create-the-inherited-control"></a>Devralınan denetimi oluşturmak için

1. **Çözüm Gezgini'nde**, **ctlClockLib'e**sağ tıklayın , **Ekle'ye**işaret edin ve ardından **Kullanıcı Denetimi'ni**tıklatın.

     **Yeni Öğe Ekle** iletişim kutusu açılır.

2. **Devralınan Kullanıcı Denetimi** şablonu'nu seçin.

3. **Ad** kutusuna, `ctlAlarmClock.cs`''yı yazın ve sonra **Ekle'yi**tıklatın.

     **Kalıtım Seçici** iletişim kutusu görüntülenir.

4. **Bileşen Adı**altında , çift tıklayın **ctlClock**.

5. **Solution**Explorer'da, geçerli projelere göz atın.

    > [!NOTE]
    > Geçerli projeye **ctlAlarmClock.cs** adlı bir dosya eklendi.

### <a name="add-the-alarm-properties"></a>Alarm Özelliklerini Ekle

Özellikler, bir bileşik denetime eklendikleri şekilde devralınan denetime eklenir. Şimdi, denetiminize iki özellik eklemek için özellik bildirimi `AlarmTime`sözdizimini kullanacaksınız: alarmın çalma tarihi ve saatinin değerini depolayacak ve `AlarmSet`alarmın ayarlanıp ayarlanmadığını gösterir.

#### <a name="to-add-properties-to-your-composite-control"></a>Bileşik denetiminize özellikler eklemek için

1. **Çözüm Gezgini'nde** **ctlAlarmClock'a**sağ tıklayın ve ardından **Kodu Görüntüle'yi**tıklatın.

2. İfadeyi `public class` bulun. Denetiminizin 'den `ctlClockLib.ctlClock`devraldığına dikkat edin. Açılış ayracının`{)` altında (deyim, aşağıdaki kodu yazın).

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

### <a name="add-to-the-graphical-interface-of-the-control"></a>Denetimin Grafik Arabirimine Ekle

Devralınan denetiminiz, devraldığı denetimle aynı görsel bir arabirime sahiptir. Ana denetimiyle aynı kurucu denetimlere sahiptir, ancak özellikle maruz kalmadıkça kurucu denetimlerin özellikleri kullanılamaz. Kalıtsal bir bileşik denetimin grafik arabirimine, herhangi bir bileşik denetime eklediğiniz şekilde ekleyebilirsiniz. Çalar saatinizin görsel arabirimine eklemeye devam etmek için, alarm çalarken yanıp sönen bir etiket denetimi eklersiniz.

#### <a name="to-add-the-label-control"></a>Etiket denetimini eklemek için

1. **Çözüm Gezgini'nde** **ctlAlarmClock'u**sağ tıklatın ve ardından **Tasarımcıyı Görüntüle'yi**tıklatın.

     Tasarımcı ana `ctlAlarmClock` pencerede açılır.

2. Denetimin görüntü bölümünü tıklatın ve Özellikler penceresini görüntüleyin.

    > [!NOTE]
    > Tüm özellikler görüntülenirken, soluk olarak görüntülenirler. Bu, bu özelliklerin `lblDisplay` özellikler penceresine özgü olduğunu ve değiştirilemeyeceğini veya erişilemeyeceğini gösterir. Varsayılan olarak, bileşik denetimde `private`bulunan denetimler ve özellikleri hiçbir şekilde erişilebilir değildir.

    > [!NOTE]
    > Bileşik denetiminizin sonraki kullanıcılarının iç denetimlerine erişebilmesini `public` istiyorsanız, bunları 'veya ' olarak `protected`bildirin Bu, uygun kodu kullanarak bileşik denetiminizde bulunan denetimlerin özelliklerini ayarlamanızı ve değiştirmenizi sağlar.

3. Bileşik <xref:System.Windows.Forms.Label> denetiminize bir denetim ekleyin.

4. Fareyi kullanarak, <xref:System.Windows.Forms.Label> denetimi ekran kutusunun hemen altına sürükleyin. Özellikler penceresinde aşağıdaki özellikleri ayarlayın.

    |Özellik|Ayar|
    |--------------|-------------|
    |**Adı**|`lblAlarm`|
    |**Metin**|**Alarm!**|
    |**Textalign**|`MiddleCenter`|
    |**Visible**|`false`|

### <a name="add-the-alarm-functionality"></a>Alarm İşlevselliği Ekle

Önceki yordamlarda, bileşik denetiminizde alarm işlevselliği sağlayacak özellikler ve denetim eklediniz. Bu yordamda, geçerli saati alarm süresiyle karşılaştırmak ve aynıysalar bir alarmı yanıp sarılacak kod eklersiniz. `timer1_Tick` Yöntemini geçersiz kılarak `ctlClock` ve buna ek kod ekleyerek, `ctlAlarmClock` `ctlClock`tüm doğal işlevselliğini korurken yeteneğini genişletirsiniz.

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a>ctlClock timer1_Tick yöntemini geçersiz kılmak için

1. `private bool blnAlarmSet;` Kod **Düzenleyicisi'nde,** deyimi bulun. Hemen altında, aşağıdaki ifadeyi ekleyin.

    ```csharp
    private bool blnColorTicker;
    ```

2. Kod **Düzenleyicisi'nde**kapanış`})` ayracını (sınıfın sonunda) bulun. Ayraçtan hemen önce, aşağıdaki kodu ekleyin.

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

     Bu kodun eklenmesi birkaç görevi gerçekleştirir. İfade, `override` temel denetimden devralınan yöntem yerine bu yöntemi kullanma denetimini yönlendirir. Bu yöntem çağrıldığında, `base.timer1_Tick` deyimi çağırarak geçersiz kılarak geçersiz kıldığında, özgün denetime dahil edilen tüm işlevlerin bu denetimde çoğaltılmasını sağlar. Daha sonra alarm işlevselliğini birleştirmek için ek kod çalışır. Alarm oluştuğunda yanıp sönen bir etiket denetimi görüntülenir.

     Çalar saat kontrolünüz neredeyse tamamlandı. Geriye kalan tek şey onu kapatmak için bir yol uygulamaktır. Bunu yapmak için yönteme `lblAlarm_Click` kod eklersiniz.

#### <a name="to-implement-the-shutoff-method"></a>Kapatma yöntemini uygulamak için

1. **Solution Explorer'da**, **ctlAlarmClock.cs**sağ tıklatın ve ardından **Tasarımcıyı Görüntüle'yi**tıklatın.

     Tasarımcı açılıyor.

2. Denetime bir düğme ekleyin. Düğmenin özelliklerini aşağıdaki gibi ayarlayın.

    |Özellik|Değer|
    |--------------|-----------|
    |**Adı**|`btnAlarmOff`|
    |**Metin**|**Alarmı Devre Dışı**|

3. Tasarımcı olarak, çift tıklayın **btnAlarmOff**.

     **Kod Düzenleyicisi** `private void btnAlarmOff_Click` satıra açılır.

4. Bu yöntemi, aşağıdaki koda benzeyecek şekilde değiştirin.

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. **Dosya** menüsünde, projeyi kaydetmek için **Tümlerini Kaydet'i** tıklatın.

### <a name="use-the-inherited-control-on-a-form"></a>Formda Devralınan Denetimi Kullanma

Devralınan denetiminizi, temel sınıf denetimini test `ctlClock`ettiğiniz gibi test edebilirsiniz: Projeyi oluşturmak ve denetiminizi **UserControl Test**Kapsayıcısı'nda çalıştırmak için **F5** tuşuna basın. Daha fazla bilgi için [bkz: UserControl'un Çalışma Zamanı Davranışını Test Edin.](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

Denetiminizi kullanmak için kullanmak için bir formda barındırmanız gerekir. Standart bileşik denetimde olduğu gibi, devralınan bileşik denetim tek başına duramaz ve bir form veya başka bir kapsayıcıda barındırılmalıdır. Daha `ctlAlarmClock` fazla işlevsellik derinliği olduğundan, bunu sınamak için ek kod gereklidir. Bu yordamda, işlevselliğini test etmek için `ctlAlarmClock`basit bir program yazacaktır. 'nin özelliğini `AlarmTime` `ctlAlarmClock`ayarlamak ve görüntülemek için kod yazar sınız ve doğal işlevlerini sınarsınız.

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>Denetiminizi oluşturmak ve bir test formuna eklemek için

1. **Çözüm Gezgini'nde** **ctlClockLib'i**sağ tıklatın ve ardından **Oluştur'u**tıklatın.

2. Çözüme yeni bir **Windows Forms Application** projesi ekleyin ve **test**adını.

3. **Çözüm Gezgini'nde,** test projeniz için **Başvurular** düğümüne sağ tıklayın. **Başvuru Ekle** iletişim kutusunu görüntülemek için Başvuru **Ekle'yi** tıklatın. **Projeler**etiketli sekmeyi tıklatın. Projeniz `ctlClockLib` **Proje Adı**altında listelenecektir. Test projesine başvuru eklemek için projeyi çift tıklatın.

4. **Çözüm Gezgini'nde**, **Test'i**sağ tıklatın ve sonra **Oluştur'u**tıklatın.

5. **Toolbox'ta** **ctlClockLib Components** düğümlerini genişletin.

6. Formunuza bir kopyasını eklemek `ctlAlarmClock` için **ctlAlarmClock'u** çift tıklatın.

7. Araç **Kutusu'nda,** formunuza bir <xref:System.Windows.Forms.DateTimePicker> denetim eklemek için **DateTimePicker'ı** bulun <xref:System.Windows.Forms.Label> ve çift tıklatın ve ardından **Etiket'i**çift tıklatarak bir denetim ekleyin.

8. Formüzerinde uygun bir yerde kontrolleri konumlandırmak için fareyi kullanın.

9. Bu denetimlerin özelliklerini aşağıdaki şekilde ayarlayın.

    |Denetim|Özellik|Değer|
    |-------------|--------------|-----------|
    |`label1`|**Metin**|`(blank space)`|
    ||**Adı**|`lblTest`|
    |`dateTimePicker1`|**Adı**|`dtpTest`|
    ||**Biçimlendir**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. Tasarımcı, **çift dtpTest**tıklayın.

     **Kod Düzenleyicisi'** ye `private void dtpTest_ValueChanged`'

11. Kodu aşağıdakilere benzeyecek şekilde değiştirin.

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. **Çözüm Gezgini'nde**, **Test'i**sağ tıklatın ve ardından Başlangıç Projesi **olarak ayarla'yı**tıklatın.

13. **Hata ayıkla** menüsünde **Hata Ayıklamayı Başlat**’a tıklayın.

     Test programı başlıyor. Geçerli saatin `ctlAlarmClock` denetimde güncelleştirilediğini ve başlangıç zamanının <xref:System.Windows.Forms.DateTimePicker> denetimde gösterildiğini unutmayın.

14. Saat <xref:System.Windows.Forms.DateTimePicker> dakikalarının görüntülendiği yeri tıklatın.

15. Klavyeyi kullanarak, dakikalar için bir değer `ctlAlarmClock`ayarlayın.

     Alarm ayarı için zaman `lblTest`' içinde gösterilir. Alarm ayar süresine ulaşmak için görüntülenen zamanı bekleyin. Görüntülenen süre alarmın ayarlandığı zamana ulaştığında, `lblAlarm` görüntülenir.

16. Tıklayarak `btnAlarmOff`alarmı kapatın. Artık alarmı sıfırlayabilirsiniz.

Bu makalede, bir dizi temel kavram ele alınmıştır. Denetimleri ve bileşenleri bir bileşik denetim kapsayıcısı içinde birleştirerek bileşik denetim oluşturmayı öğrendiniz. Denetiminize özellikler eklemeyi ve özel işlevselliği uygulamak için kod yazmayı öğrendiniz. Son bölümde, belirli bir bileşik denetimin işlevselliğini devralma yoluyla genişletmeyi ve bu yöntemleri geçersiz kılarak ana bilgisayar yöntemlerinin işlevselliğini değiştirmeyi öğrendiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
- [Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
