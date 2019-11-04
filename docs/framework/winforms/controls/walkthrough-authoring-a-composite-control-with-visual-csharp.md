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
ms.openlocfilehash: c1d9be77550b1255a24120c68f20d25640e0ebdf
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460634"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a>İzlenecek yol: C\# ile bileşik denetim yazma

Bileşik denetimler, özel grafik arabirimlerinin oluşturulup yeniden kullanılabilmesi için bir yol sağlar. Bileşik denetim temelde görsel temsili olan bir bileşendir. Bu nedenle, Kullanıcı girişini doğrulayarak, görüntü özelliklerini değiştirerek veya yazar için gereken diğer görevleri gerçekleştirerek işlevselliği genişletebilen bir veya daha fazla Windows Forms denetimi, bileşeni veya kod bloklarında bulunabilir. Bileşik denetimler Windows Forms diğer denetimlerle aynı şekilde yerleştirilebilir. Bu izlenecek yolun ilk bölümünde `ctlClock`adlı basit bir bileşik denetim oluşturursunuz. İzlenecek yolun ikinci bölümünde devralma yoluyla `ctlClock` işlevlerini uzatamazsınız.

## <a name="create-the-project"></a>Projeyi Oluşturma

Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlamak için adını belirtin ve varsayılan bileşenin doğru ad alanında yer aldığından emin olun.

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>CtlClockLib denetim kitaplığını ve ctlClock denetimini oluşturmak için

1. Visual Studio 'da yeni bir **Windows Forms denetim kitaplığı** projesi oluşturun ve **ctlClockLib**olarak adlandırın.

     `ctlClockLib`proje adı, varsayılan olarak kök ad alanına da atanır. Kök ad alanı, derlemedeki bileşenlerin adlarını nitelemek için kullanılır. Örneğin, iki derleme `ctlClock`adlı bileşenler sağlamışsa, `ctlClock` bileşeninizi `ctlClockLib.ctlClock.` kullanarak belirtebilirsiniz

2. **Çözüm Gezgini**' de, **UserControl1.cs**' a sağ tıklayın ve ardından **Yeniden Adlandır**' a tıklayın. Dosya adını `ctlClock.cs`değiştirin. "UserControl1" kod öğesiyle tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet** düğmesine tıklayın.

    > [!NOTE]
    > Varsayılan olarak, bileşik bir denetim sistem tarafından sunulan <xref:System.Windows.Forms.UserControl> sınıfından devralır. <xref:System.Windows.Forms.UserControl> sınıfı tüm bileşik denetimlerin gerektirdiği işlevselliği sağlar ve standart yöntemler ve özellikler uygular.

3. Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.

## <a name="add-windows-controls-and-components-to-the-composite-control"></a>Bileşik denetime Windows denetimleri ve bileşenleri ekleme

Görsel arabirim, bileşik denetiminizin temel bir parçasıdır. Bu görsel arabirim, tasarımcı yüzeyine bir veya daha fazla Windows denetimi eklenerek uygulanır. Aşağıdaki gösteride, Windows denetimlerini bileşik denetiminizle birleştirirsiniz ve işlevselliği uygulamak için kod yazabilirsiniz.

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Bileşik denetilemenize bir etiket ve süreölçer eklemek için

1. **Çözüm Gezgini**' de, **ctlClock.cs**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

2. **Araç kutusunda** **ortak denetimler** düğümünü genişletin ve ardından **etiket**' e çift tıklayın.

     Tasarımcı yüzeyine `label1` adlı <xref:System.Windows.Forms.Label> bir denetim denetime eklenir.

3. Tasarımcıda **Label1**' ye tıklayın. Özellikler penceresi, aşağıdaki özellikleri ayarlayın.

    |Özellik|Değiştir|
    |--------------|---------------|
    |**Ad**|`lblDisplay`|
    |**Metin**|`(blank space)`|
    |**TextAlign**|`MiddleCenter`|
    |**Yazı tipi. boyutu**|`14`|

4. **Araç kutusunda**, **Bileşenler** düğümünü genişletin ve ardından **Zamanlayıcı**' ya çift tıklayın.

     <xref:System.Windows.Forms.Timer> bir bileşen olduğundan, çalışma zamanında görsel temsili yoktur. Bu nedenle, tasarımcı yüzeyindeki denetimlerde görünmez, ancak **Bileşen tasarımcısında** (tasarımcı yüzeyinin altındaki bir tepsi) değil.

5. **Bileşen tasarımcısında**, **Süreölçer1**' a tıklayın ve ardından <xref:System.Windows.Forms.Timer.Interval%2A> özelliğini `1000` ve <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `true`olarak ayarlayın.

     <xref:System.Windows.Forms.Timer.Interval%2A> özelliği, <xref:System.Windows.Forms.Timer> bileşeni işaret eden sıklığı denetler. Her zaman `timer1` her seferinde, `timer1_Tick` olayında kodu çalıştırır. Aralık, zaman işaretleri arasındaki milisaniye sayısını temsil eder.

6. **Bileşen tasarımcısında**, `ctlClock`için `timer1_Tick` olayına gitmek için **Süreölçer1** öğesine çift tıklayın.

7. Kodu aşağıdaki kod örneğine benzer olacak şekilde değiştirin. `private` erişim değiştiricisini `protected`olarak değiştirdiğinizden emin olun.

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     Bu kod, geçerli saatin `lblDisplay`görüntülenmesine neden olur. `timer1` aralığı `1000`olarak ayarlandığı için, bu olay her bin milisaniyede bir gerçekleşeceğinden, bu nedenle her saniye geçerli saati güncelliyor.

8. Yöntemi, `virtual` anahtar sözcüğüyle geçersiz kılınabilir olacak şekilde değiştirin. Daha fazla bilgi için aşağıdaki "Kullanıcı denetiminden devralma" bölümüne bakın.

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.

## <a name="add-properties-to-the-composite-control"></a>Bileşik denetime özellikler ekleme

Saat denetiminiz artık, her biri kendi kendine ait özellikler kümesiyle bir <xref:System.Windows.Forms.Label> denetimini ve <xref:System.Windows.Forms.Timer> bileşenini kapsüller. Bu denetimlerin tek tek özelliklerine denetiminizin sonraki kullanıcıları tarafından erişilemese de, uygun kod bloklarını yazarak özel özellikler oluşturabilir ve kullanıma sunabilirsiniz. Aşağıdaki yordamda, denetime, kullanıcının arka plan ve metin rengini değiştirmesini sağlayan özellikler ekleyeceksiniz.

### <a name="to-add-a-property-to-your-composite-control"></a>Bileşik denetimi bir özellik eklemek için

1. **Çözüm Gezgini**' de, **ctlClock.cs**' a sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

     Denetiminizin **Kod Düzenleyicisi** açılır.

2. `public partial class ctlClock` ifadesini bulun. Açma küme ayracı (`{)`) altında aşağıdaki kodu yazın.

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     Bu deyimler, oluşturmak üzere olduğunuz özelliklerin değerlerini depolamak için kullanacağınız özel değişkenleri oluşturur.

3. Aşağıdaki kodu adım 2 ' den değişken bildirimlerinin altına girin veya yapıştırın.

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

     Yukarıdaki kod, bu denetimin sonraki kullanıcıları tarafından kullanılabilen `ClockForeColor` ve `ClockBackColor`iki özel özellik oluşturur. `get` ve `set` deyimleri, özellik değerini depolamak ve almak için, özelliği de özelliğine uygun işlevselliği uygulamak için de kod sağlar.

4. Projeyi kaydetmek için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.

## <a name="test-the-control"></a>Denetimi test etme

Denetimler tek başına uygulamalar değildir; Bunlar bir kapsayıcıda barındırılmalıdır. Denetiminizin çalışma zamanı davranışını test edin ve özelliklerini **UserControl Test kapsayıcısı**ile çalıştırın. Daha fazla bilgi için bkz. [nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

### <a name="to-test-your-control"></a>Denetiminizi test etmek için

1. Projeyi derlemek için **F5** tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın.

2. Test kapsayıcısının özellik kılavuzunda `ClockBackColor` özelliğini bulun ve ardından renk paletini göstermek için özelliği seçin.

3. Tıklayarak bir renk seçin.

   Denetiminizin arka plan rengi, seçtiğiniz renge değişir.

4. `ClockForeColor` özelliğinin beklendiği gibi çalıştığını doğrulamak için benzer bir olay dizisi kullanın.

   Bu bölümde ve önceki bölümlerde, bileşik denetim biçiminde özel işlevsellik sağlamak için bileşenlerin ve Windows denetimlerinin kod ve paketleme ile nasıl birleştirilebileceği gördünüz. Birleşik denetidiklerinizin özelliklerini açığa çıkarmak ve tamamlandıktan sonra denetiminizi test etmek için öğrendiniz. Sonraki bölümde, temel olarak `ctlClock` kullanarak devralınan bileşik denetim oluşturmayı öğreneceksiniz.

## <a name="inherit-from-a-composite-control"></a>Bileşik denetimden devralma

Önceki bölümlerde, Windows denetimlerini, bileşenleri ve kodu yeniden kullanılabilir bileşik denetimlere nasıl birleştirebileceğinizi öğrendiniz. Bileşik denetiminiz artık diğer denetimlerin derlenme temeli olarak kullanılabilir. Temel sınıftan bir sınıfın türeme işlemi *Devralma*olarak adlandırılır. Bu bölümde `ctlAlarmClock`adlı bir bileşik denetim oluşturacaksınız. Bu denetim, `ctlClock`üst denetiminden türetilecektir. Üst yöntemleri geçersiz kılarak ve yeni yöntemler ve özellikler ekleyerek `ctlClock` işlevselliğini genişletmeyi öğreneceksiniz.

Devralınan bir denetim oluşturmanın ilk adımı onu üst öğesinden türemektir. Bu eylem, üst denetimin tüm özelliklerine, yöntemlerine ve grafiksel özelliklerine sahip yeni bir denetim oluşturur, ancak yeni veya değiştirilmiş işlevselliğin eklenmesi için temel olarak da davranabilir.

### <a name="to-create-the-inherited-control"></a>Devralınan denetimi oluşturmak için

1. **Çözüm Gezgini**' de, **ctlClockLib**' a sağ tıklayın, **Ekle**' nin üzerine gelin ve **Kullanıcı denetimi**' ne tıklayın.

     **Yeni öğe Ekle** iletişim kutusu açılır.

2. **Devralınan Kullanıcı denetimi** şablonunu seçin.

3. **Ad** kutusuna `ctlAlarmClock.cs`yazın ve ardından **Ekle**' ye tıklayın.

     **Devralma Seçicisi** iletişim kutusu görüntülenir.

4. **Bileşen adı**altında **ctlClock**' ye çift tıklayın.

5. **Çözüm Gezgini**, geçerli projelere göz atabilirsiniz.

    > [!NOTE]
    > Geçerli projeye **ctlAlarmClock.cs** adlı bir dosya eklendi.

### <a name="add-the-alarm-properties"></a>Alarm özelliklerini ekleme

Özellikler, devralınan bir denetime, Birleşik bir denetime eklendikçe aynı şekilde eklenir. Şimdi, denetimizin için iki özellik eklemek üzere özellik bildirimi sözdizimini kullanacaksınız: `AlarmTime`, alarmın bitiş tarihini ve saatini depolayan ve alarmın ayarlandığını belirten `AlarmSet`.

#### <a name="to-add-properties-to-your-composite-control"></a>Bileşik denetimi özellikler eklemek için

1. **Çözüm Gezgini**' de, **ctlAlarmClock**' a sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

2. `public class` ifadesini bulun. Denetiminizin `ctlClockLib.ctlClock`devraldığını unutmayın. Açma küme ayracı (`{)` deyimin altına aşağıdaki kodu yazın.

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

### <a name="add-to-the-graphical-interface-of-the-control"></a>Denetimin grafik arabirimine Ekle

Devralınan denetiminizin devraldığı denetimle özdeş bir görsel arabirimi vardır. Kendi üst denetimiyle aynı bileşen denetimlerine sahip olur, ancak yapısal denetimlerin özellikleri özellikle gösterilmedikleri sürece kullanılamaz. Devralınan bir bileşik denetimin grafik arabirimine, herhangi bir bileşik denetime ekleyeceğiniz şekilde ekleyebilirsiniz. Alarm saatinizin görsel arabirimine eklemeye devam etmek için, alarm bir işlem olduğunda Flash olacak bir etiket denetimi ekleyeceksiniz.

#### <a name="to-add-the-label-control"></a>Etiket denetimi eklemek için

1. **Çözüm Gezgini**' de, **ctlAlarmClock**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

     `ctlAlarmClock` Tasarımcısı ana pencerede açılır.

2. Denetimin görüntüleme bölümüne tıklayın ve Özellikler penceresi görüntüleyin.

    > [!NOTE]
    > Tüm özellikler görüntülenirken, soluk olurlar. Bu özelliklerin `lblDisplay` yerel olduğunu ve Özellikler penceresi değiştirilemeyeceğini veya erişilmeyeceğini gösterir. Varsayılan olarak, bileşik denetimde bulunan denetimler `private`ve özellikleri herhangi bir şekilde erişilebilir değildir.

    > [!NOTE]
    > Bileşik denetiminizin sonraki kullanıcılarının iç denetimlerine erişimi olmasını istiyorsanız, bunları `public` veya `protected`olarak bildirin. Bu, uygun kodu kullanarak bileşik denetilinizin içindeki denetimlerin özelliklerini ayarlamanıza ve değiştirmenize izin verir.

3. Bileşik denetimi denetim <xref:System.Windows.Forms.Label> ekleyin.

4. Fareyi kullanarak, <xref:System.Windows.Forms.Label> denetimini ekran kutusunun hemen altına sürükleyin. Özellikler penceresi, aşağıdaki özellikleri ayarlayın.

    |Özellik|Ayar|
    |--------------|-------------|
    |**Ad**|`lblAlarm`|
    |**Metin**|**Alarm!**|
    |**TextAlign**|`MiddleCenter`|
    |**Görüne**|`false`|

### <a name="add-the-alarm-functionality"></a>Alarm Işlevlerini ekleme

Önceki yordamlarda, bileşik denetiminizdeki alarm işlevselliğini etkinleştiren Özellikler ve bir denetim eklediniz. Bu yordamda, geçerli saati alarm zamanına göre karşılaştırmak için kod ekleyeceksiniz ve aynı ise, bir alarm Flash için de aynı olduğunda. `ctlClock` `timer1_Tick` yöntemini geçersiz kılarak ve buna ek kod ekleyerek, `ctlClock`tüm özelliklerini korurken `ctlAlarmClock` özelliğini genişletebilirsiniz.

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a>CtlClock timer1_Tick yöntemini geçersiz kılmak için

1. **Kod düzenleyicisinde**`private bool blnAlarmSet;` ifadesini bulun. Hemen hemen altına aşağıdaki ifadeyi ekleyin.

    ```csharp
    private bool blnColorTicker;
    ```

2. **Kod Düzenleyicisi**'nde, sınıfın sonundaki kapanış ayracını (`})` bulun. Küme ayracından hemen önce aşağıdaki kodu ekleyin.

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

     Bu kodun eklenmesi birkaç görevi gerçekleştirir. `override` ifade, denetimi temel denetimden devralınan yöntemin yerine bu yöntemi kullanacak şekilde yönlendirir. Bu yöntem çağrıldığında, özgün denetimde dahil edilen tüm işlevlerin Bu denetimde yeniden üretildiğinden emin olmak için `base.timer1_Tick` ifadesini çağırarak geçersiz kıldığından yöntemi çağırır. Daha sonra alarm işlevselliğini birleştirmek için ek kod çalıştırır. Uyarı oluştuğunda yanıp sönen bir etiket denetimi görünür.

     Alarm saati denetiminiz neredeyse tamamlanmıştır. Kalan tek şey, devre dışı bırakmak için bir yol uygulamaktır. Bunu yapmak için `lblAlarm_Click` yöntemine kod ekleyeceksiniz.

#### <a name="to-implement-the-shutoff-method"></a>Shutoff yöntemini uygulamak için

1. **Çözüm Gezgini**' de, **ctlAlarmClock.cs**' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

     Tasarımcı açılır.

2. Denetime düğme ekleyin. Düğmenin özelliklerini aşağıdaki gibi ayarlayın.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|`btnAlarmOff`|
    |**Metin**|**Alarmı devre dışı bırak**|

3. Tasarımcı 'da, **btnAlarmOff**' a çift tıklayın.

     **Kod düzenleyicisi** `private void btnAlarmOff_Click` satırı olarak açılır.

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

### <a name="use-the-inherited-control-on-a-form"></a>Bir form üzerinde devralınan denetimi kullanma

Devralınan denetiminizi, temel sınıf denetimini sınadığınız şekilde test edebilirsiniz, `ctlClock`: **F5** tuşuna basarak projeyi oluşturun ve denetiminizi **UserControl Test kapsayıcısında**çalıştırın. Daha fazla bilgi için bkz. [nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

Denetiminizi kullanmak üzere yerleştirmek için bir form üzerinde barındırmanıza gerek duyarsınız. Standart bir bileşik denetimde olduğu gibi, devralınan bir bileşik denetim tek başına olamaz ve bir formda ya da başka bir kapsayıcıda barındırılmalıdır. `ctlAlarmClock` daha kapsamlı bir işlevselliğe sahip olduğundan, test etmek için ek kod gereklidir. Bu yordamda, `ctlAlarmClock`işlevlerini test etmek için basit bir program yazacaksınız. `ctlAlarmClock``AlarmTime` özelliğini ayarlamak ve göstermek için kod yazacaksınız ve onun kendisine ait işlevlerini test edecektir.

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>Denetimi derlemek ve test formuna eklemek için

1. **Çözüm Gezgini**' de, **ctlClockLib**' a sağ tıklayın ve ardından **Oluştur**' a tıklayın.

2. Çözüme yeni bir **Windows uygulaması** projesi ekleyin ve **Test**edin.

3. **Çözüm Gezgini**, test projeniz için **Başvurular** düğümüne sağ tıklayın. **Başvuru Ekle iletişim kutusunu** göstermek Için **Başvuru Ekle** ' ye tıklayın. Etiketli **Projeler**sekmesine tıklayın. `ctlClockLib` projeniz **Proje adı**altında listelenecektir. Başvuruyu test projesine eklemek için projeye çift tıklayın.

4. **Çözüm Gezgini**' de **Test**' e sağ tıklayın ve ardından **Oluştur**' a tıklayın.

5. **Araç kutusunda** **ctlClockLib Components** düğümünü genişletin.

6. Formunuza bir `ctlAlarmClock` kopyası eklemek için **ctlAlarmClock** öğesine çift tıklayın.

7. **Araç kutusunda** **DateTimePicker** ' ı bulup çift tıklatarak formunuza bir <xref:System.Windows.Forms.DateTimePicker> denetimi ekleyin ve ardından **etikete**çift tıklayarak bir <xref:System.Windows.Forms.Label> denetimi ekleyin.

8. Denetimleri form üzerinde uygun bir yerde konumlandırmak için fareyi kullanın.

9. Bu denetimlerin özelliklerini aşağıdaki şekilde ayarlayın.

    |Denetim|Özellik|Değer|
    |-------------|--------------|-----------|
    |`label1`|**Metin**|`(blank space)`|
    ||**Ad**|`lblTest`|
    |`dateTimePicker1`|**Ad**|`dtpTest`|
    ||**Formatını**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. Tasarımcıda **dtpTest**öğesine çift tıklayın.

     `private void dtpTest_ValueChanged`için **Kod Düzenleyicisi** açılır.

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

12. **Çözüm Gezgini**' de **Test**' e sağ tıklayın ve ardından **Başlangıç projesi olarak ayarla**' ya tıklayın.

13. **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat**' a tıklayın.

     Test programı başlar. `ctlAlarmClock` denetiminde geçerli saatin güncelleştirildiğini ve <xref:System.Windows.Forms.DateTimePicker> denetiminde başlangıç zamanının gösterildiğini unutmayın.

14. Saatin dakikalarının görüntülendiği <xref:System.Windows.Forms.DateTimePicker> tıklatın.

15. Klavyeyi kullanarak, `ctlAlarmClock`tarafından gösterilen geçerli zamandan bir dakika daha büyük bir değer ayarlayın.

     Uyarı ayarının saati `lblTest`gösterilir. Uyarı ayarı zamanına ulaşmak için, görüntülenecek sürenin bekleyin. Görünen süre, alarmın ayarlandığı zamana ulaştığında, `lblAlarm` yanıp sönecektir.

16. `btnAlarmOff`' ye tıklayarak uyarıyı kapatın. Şimdi uyarıyı sıfırlayabilirsiniz.

Bu makalede bir dizi temel kavram ele alınmıştır. Bir bileşik denetim kapsayıcısına denetimleri ve bileşenleri birleştirerek bileşik bir denetim oluşturmayı öğrendiniz. Denetime Özellik eklemeyi ve özel işlevsellik uygulamak için kod yazmayı öğrendiniz. Son bölümde, belirli bir bileşik denetimin işlevselliğini devralma yoluyla genişletmeyi ve bu yöntemleri geçersiz kılarak ana bilgisayar yöntemlerinin işlevselliğini değiştirmeyi öğrendiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
- [Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
