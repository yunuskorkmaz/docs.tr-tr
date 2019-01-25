---
title: 'İzlenecek yol: Visual Basic ile bileşik denetim yazma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
ms.openlocfilehash: e961826f4c33edf59934597734aec36ce301194e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694392"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a>İzlenecek yol: Visual Basic ile bileşik denetim yazma
Bileşik denetimler, özel bir grafik arabirim oluşturulabilir yeniden ve bir yöntemdir. Bileşik Denetim aslında bir görsel bir temsili ile bileşenidir. Bu nedenle, bir veya daha fazla Windows Forms denetimleri, bileşenleri veya kullanıcı girişini doğrulama, görüntü özelliklerini değiştirerek veya yazar tarafından gereken diğer görevleri gerçekleştirme işlevselliğini genişletebildiği kod bloklarını oluşabilir. Bileşik denetimler, diğer denetimlerle aynı şekilde Windows formlarında yerleştirilebilir. Bu kılavuzun ilk bölümünde oluşturduğunuz adlı basit bir bileşik denetim `ctlClock`. İzlenecek yol ikinci kısmında, işlevlerini genişletmek `ctlClock` devralma yoluyla.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlayın ve varsayılan bileşeni doğru ad alanı içinde olmasını sağlamak için adını belirtin.  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>CtlClockLib denetim kitaplığı ve ctlClock denetimi oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje** açmak için **yeni proje** iletişim kutusu.  
  
2.  Visual Basic projelerinin listesinden **Windows Denetim Kitaplığı** proje şablonu, türü `ctlClockLib` içinde **adı** kutusuna ve ardından **Tamam**.  
  
     Proje adı `ctlClockLib`, aynı zamanda kök ad alanı için varsayılan olarak atanır. Kök ad alanı, bileşenleri derleme içindeki adlarını nitelemek için kullanılır. Örneğin, iki derleme adlı bileşenleri sağlarsanız `ctlClock`, belirtebilirsiniz, `ctlClock` bileşenini kullanma `ctlClockLib.ctlClock.`  
  
3.  Çözüm Gezgini'nde sağ **UserControl1.vb**ve ardından **Yeniden Adlandır**. İçin dosya adını değiştirerek `ctlClock.vb`. Tıklayın **Evet** yaptığınız kod öğesi "UserControl1" için tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda düğmesi.  
  
    > [!NOTE]
    >  Bileşik denetim varsayılan olarak, devralınan <xref:System.Windows.Forms.UserControl> sistem tarafından sağlanan sınıfı. <xref:System.Windows.Forms.UserControl> Sınıfı tüm bileşik denetimler tarafından gerekli işlevselliği sunar ve standart yöntemleri ve özellikleri uygular.  
  
4.  Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Windows ekleme denetimleri ve bileşenleri bileşik denetim  
 Görsel bir arabirim, bileşik denetim önemli bir parçasıdır. Bu görsel arabirim Tasarımcı yüzeyine bir veya daha fazla Windows denetimleri eklenmesini tarafından uygulanır. Aşağıdaki örnekte, Windows denetimleri, bileşik denetime eklemek ve işlevselliği uygulamak için kod yazın.  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Bir etiket ve Zamanlayıcı bileşik denetiminize eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlClock.vb**ve ardından **Görünüm Tasarımcısı**.  
  
2.  Araç kutusunda genişletin **ortak denetimleri** düğüm gittikten sonra çift tıklayarak **etiket**.  
  
     A <xref:System.Windows.Forms.Label> adlı Denetim `Label1` Tasarımcı yüzeyinde, denetimi eklenir.  
  
3.  Tasarımcıda **Label1**. Özellikler penceresinde, aşağıdaki özellikleri ayarlayın.  
  
    |Özellik|Değiştirin|  
    |--------------|---------------|  
    |**Ad**|`lblDisplay`|  
    |**Metin**|`(blank space)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  İçinde **araç kutusu**, genişletme **bileşenleri** düğüm gittikten sonra çift tıklayarak **Zamanlayıcı**.  
  
     Çünkü bir <xref:System.Windows.Forms.Timer> bir bileşen çalışma zamanında görsel bir temsili sahiptir. Bu nedenle, denetimlerle Tasarımcı yüzeyine, ancak bunun yerine (tasarımcı yüzeyine alt kısmındaki Tepsisi) Bileşen Tasarımcısı'nda görünmez.  
  
5.  Bileşen Tasarımcısı'nda tıklatın **Süreölçer1**ve ardından <xref:System.Windows.Forms.Timer.Interval%2A> özelliğini `1000` ve <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `True`.  
  
     <xref:System.Windows.Forms.Timer.Interval%2A> Özellik süreölçer bileşeni ile işaretlerini sıklığını denetler. Her zaman `Timer1` saat tıklaması, çalışırken kod `Timer1_Tick` olay. Aralık işaretleri arasındaki milisaniye sayısını temsil eder.  
  
6.  Bileşen Tasarımcısı'nda çift **Süreölçer1** gitmek için `Timer1_Tick` olayı `ctlClock`.  
  
7.  Kodu aşağıdaki kod örneği benzeyecek şekilde değiştirin. Gelen erişim değiştiricisi değiştirdiğinizden emin olun `Private` için `Protected`.  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     Bu kodun geçerli saate göre gösterilecek neden olur `lblDisplay`. Çünkü aralığı `Timer1` ayarlandı `1000`, bu olay, böylece her saniye geçerli saati güncelleştiriliyor her bin milisaniye meydana gelir.  
  
8.  Yöntem geçersiz kılınabilir olacak şekilde değiştirin. Daha fazla bilgi için "Devralan bir kullanıcı denetimi" bölümüne bakın.  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="adding-properties-to-the-composite-control"></a>Bileşik denetime özellik ekleme  
 Saat denetiminiz artık kapsülleyen bir <xref:System.Windows.Forms.Label> denetimi ve bir <xref:System.Windows.Forms.Timer> bileşeni, her biri kendi devralınan özellikler kümesi. Bu denetimlerin özelliklerini bireysel denetiminizin sonraki kullanıcılar için erişilebilir değil ancak oluşturabilir ve uygun blok kod yazarak özel özellikler kullanıma sunar. Aşağıdaki yordamda, metin ve arka plan rengini değiştirmek kullanıcının denetiminize özellikler ekleyeceksiniz.  
  
#### <a name="to-add-a-property-to-your-composite-control"></a>Bileşik denetiminiz için bir özellik eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlClock.vb**ve ardından **kodu görüntüle**.  
  
     Denetiminiz için kod düzenleyicisi açılır.  
  
2.  Bulun `Public Class ctlClock` deyimi. Bunun altında aşağıdaki kodu yazın.  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     Bu deyimler oluşturmak üzere olduğunuz özelliklerinin değerlerini depolamak için kullanılacak özel değişkenleri oluşturun.  
  
3.  Adım 2 ' değişken bildirimlerini altına aşağıdaki kodu ekleyin.  
  
    ```vb  
    ' Declares the name and type of the property.  
    Property ClockBackColor() as Color  
        ' Retrieves the value of the private variable colBColor.  
        Get  
            Return colBColor  
        End Get  
        ' Stores the selected value in the private variable colBColor, and   
        ' updates the background color of the label control lblDisplay.  
        Set(ByVal value as Color)  
            colBColor = value  
            lblDisplay.BackColor = colBColor     
        End Set  
  
    End Property  
    ' Provides a similar set of instructions for the foreground color.  
    Property ClockForeColor() as Color  
        Get  
            Return colFColor  
        End Get  
        Set(ByVal value as Color)  
            colFColor = value  
            lblDisplay.ForeColor = colFColor  
        End Set  
    End Property  
    ```  
  
     Yukarıdaki kod, iki özel özellikler yapar `ClockForeColor` ve `ClockBackColor`, sonraki kullanıcılara çağırarak bu denetimin `Property` deyimi. `Get` Ve `Set` deyimleri, depolama ve alma işlevselliğini uygulamak için kod yanı sıra özellik değeri, özellik için uygun sağlayın.  
  
4.  Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="testing-the-control"></a>Denetimini test etme  
 Denetimler, tek başına projeleri değildir; Bunlar, bir kapsayıcıda barındırılan gerekir. Denetimin çalışma zamanı davranışını sınama ve özellikleriyle birlikte çalışma **UserControl Test kapsayıcısı**. Daha fazla bilgi için [nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-your-control"></a>Denetiminiz test etmek için  
  
1.  Projeyi oluşturmak ve denetim çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.  
  
2.  Test kapsayıcının özellik kılavuzunda seçin `ClockBackColor` özelliği ve ardından renk paletini görüntülemek için açılan oka tıklayın.  
  
3.  Tıklayarak bir renk seçin.  
  
     Denetim arka plan rengi, seçtiğiniz rengine değiştirir.  
  
4.  Doğrulamak için benzer bir olay dizisi kullanan `ClockForeColor` özelliği beklendiği gibi çalışmıyor.  
  
5.  Tıklayın **kapatmak** kapatmak için **UserControl Test kapsayıcısı**.  
  
     Bu bölümde ve önceki bölümlerde, bileşenleri ve Windows denetimleri nasıl birleştirileceğini gördünüz kodla ve paketleme bileşik denetim biçiminde özel işlevsellik sağlamak için. Bileşik Denetim ve denetim, tamamlandıktan sonra test etme özellikleri göstermek öğrendiniz. Sonraki bölümde kullanarak bir devralınan bileşik denetim oluşturmak hakkında bilgi edineceksiniz `ctlClock` temel olarak.  
  
## <a name="inheriting-from-a-composite-control"></a>Bileşik Denetim devralıyor  
 Önceki bölümlerde Windows denetimleri, bileşenleri ve kod yeniden kullanılabilir bileşik denetimler birleştirmek öğrendiniz. Bileşik Denetim artık diğer denetimlerin oluşturulabilir, bir temel olarak kullanılabilir. Sınıf bir taban sınıftan türetme işlemine denir *devralma*. Bu bölümde, adlı bileşik denetim oluşturacaksınız `ctlAlarmClock`. Bu denetim, üst denetiminden elde edilir `ctlClock`. Genişletmek öğreneceksiniz `ctlClock` üst yöntemleri geçersiz kılma ve yeni yöntemleri ve özellikleri ekleme.  
  
 Devralınan bir denetim oluşturmanın ilk adımı, üst öğesinden türetilen sağlamaktır. Bu eylem, tüm özellikleri, yöntemleri ve üst denetimin grafik özelliklerine sahip yeni bir denetim oluşturur, ancak yeni veya değiştirilmiş işlevselliği eklenmesi için temel olarak da hareket.  
  
#### <a name="to-create-the-inherited-control"></a>Devralınan bir denetim oluşturmak için  
  
1.  Çözüm Gezgini'nde sağ **ctlClockLib**, işaret **Ekle**ve ardından **kullanıcı denetimi**.  
  
     **Yeni Öğe Ekle** iletişim kutusu açılır.  
  
2.  Seçin **devralınan kullanıcı denetimi** şablonu.  
  
3.  İçinde **adı** kutusuna `ctlAlarmClock.vb`ve ardından **Ekle**.  
  
     **Devralma Seçici** iletişim kutusu görüntülenir.  
  
4.  Altında **bileşen adı**, çift **ctlClock**.  
  
5.  Çözüm Gezgini içinde geçerli projeleri göz atın.  
  
    > [!NOTE]
    >  Dosya adında **ctlAlarmClock.vb** geçerli projeye eklendi.  
  
### <a name="adding-the-alarm-properties"></a>Uyarı özellikleri ekleme  
 Bileşik denetim için eklenen aynı şekilde, devralınan bir denetim için özellikler eklenir. Şimdi iki özellik denetiminize eklemek için özellik bildirimi sözdizimi kullanır: `AlarmTime`, tarih ve saat alarma olan kapalı, Git değerini depolar ve `AlarmSet`, hangi uyarı ayarlanıp ayarlanmadığını gösterecektir.  
  
##### <a name="to-add-properties-to-your-composite-control"></a>Özellikler birleşik denetiminize eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlAlarmClock**ve ardından **kodu görüntüle**.  
  
2.  Sınıf bildirimi olarak görünür ctlAlarmClock denetimi için bulun `Public Class ctlAlarmClock`.  Sınıf bildiriminde aşağıdaki kodu ekleyin.  
  
    ```vb  
    Private dteAlarmTime As Date  
    Private blnAlarmSet As Boolean  
    ' These properties will be declared as Public to allow future   
    ' developers to access them.  
    Public Property AlarmTime() As Date  
        Get  
            Return dteAlarmTime  
        End Get  
        Set(ByVal value as Date)  
            dteAlarmTime = value  
        End Set  
    End Property  
    Public Property AlarmSet() As Boolean  
        Get  
            Return blnAlarmSet  
        End Get  
        Set(ByVal value as Boolean)  
            blnAlarmSet = value  
        End Set  
    End Property  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a>Grafik arabirimine denetimi ekleme  
 Devralınan denetim devraldığı denetlemek için aynı olan görsel bir arabirim sahiptir. Aynı bağlı denetimler, üst denetim olarak sahiptir, ancak özel olarak sunulan sürece bağlı denetimlerin özelliklerini kullanılabilir olmayacak. Herhangi bir bileşik denetimi olduğu gibi aynı şekilde devralınan bir bileşik denetim grafik arabirimine ekleyebilir. Uyarı Saatin görsel arabirim olarak eklemeye devam etmek için alarm uyarabilir yükleyen yanar etiket denetimi ekleyeceksiniz.  
  
##### <a name="to-add-the-label-control"></a>Etiket denetimi eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlAlarmClock**, tıklatıp **Görünüm Tasarımcısı**.  
  
     Tasarımcı için `ctlAlarmClock` ana penceresinde açılır.  
  
2.  Tıklayın `lblDisplay` (denetiminin görünen kısmı) ve Özellikler penceresini görüntüleyin.  
  
    > [!NOTE]
    >  Tüm özellikler görüntülenir, ancak bunlar soluklaştırılır. Bu, bu özellikleri için yerel gösterir `lblDisplay` ve değiştirilemez veya Özellikler penceresinde erişilebilir. Varsayılan olarak, bu bileşik denetiminde bulunan denetimlerdir `Private`, ve bunların özelliklerini herhangi bir yolla erişilebilir değildir.  
  
    > [!NOTE]
    >  Bileşik denetiminizin sonraki kullanıcıların kendi iç denetimleri erişmesini isterseniz, bunları olarak bildirin `Public` veya `Protected`. Bu, ayarlamak ve uygun kodu kullanarak bileşik denetiminizin içinde yer alan denetimlerin özelliklerini değiştirmek olanak tanır.  
  
3.  Ekleme bir <xref:System.Windows.Forms.Label> denetimi için bileşik denetim.  
  
4.  Fareyle sürükleyin <xref:System.Windows.Forms.Label> görüntüleme kutusunun hemen altındaki denetimi. Özellikler penceresinde, aşağıdaki özellikleri ayarlayın.  
  
    |Özellik|Ayar|  
    |--------------|-------------|  
    |**Ad**|`lblAlarm`|  
    |**Metin**|**Uyarı!**|  
    |**TextAlign**|`MiddleCenter`|  
    |**Görünür**|`False`|  
  
### <a name="adding-the-alarm-functionality"></a>Uyarı işlevsellik ekleme  
 Önceki yordamlarda, özellikleri ve bileşik denetim uyarısı işlevselliği sağlayan bir denetimi eklendi. Bu yordamda, alarm saati geçerli saate karşılaştırmak için kod ekleyeceksiniz ve aynı, ses ve bir uyarı flash olmaları durumunda. Geçersiz kılma tarafından `Timer1_Tick` yöntemi `ctlClock` ve ek kod ekleme, yeteneğini genişletecek `ctlAlarmClock` tüm devralınan işlevselliğini korurken `ctlClock`.  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a>CtlClock Timer1_Tick yöntemi geçersiz kılmak için  
  
1.  Çözüm Gezgini'nde sağ **ctlAlarmClock.vb**ve ardından **kodu görüntüle**.  
  
2.  Bulun `Private blnAlarmSet As Boolean` deyimi. Hemen altında aşağıdaki deyimi ekleyin.  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  Bulun `End Class` sayfanın alt kısmındaki deyimi. Hemen önce `End Class` deyimi, aşağıdaki kodu ekleyin.  
  
    ```vb  
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _  
        As System.EventArgs)  
        ' Calls the Timer1_Tick method of ctlClock.  
        MyBase.Timer1_Tick(sender, e)  
        ' Checks to see if the Alarm is set.  
        If AlarmSet = False Then  
            Exit Sub  
        End If  
        ' If the date, hour, and minute of the alarm time are the same as  
        ' now, flash and beep an alarm.   
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _  
            AlarmTime.Minute = Now.Minute Then  
            ' Sounds an audible beep.  
            Beep()  
            ' Sets lblAlarmVisible to True, and changes the background color based on the   
            ' value of blnColorTicker. The background color of the label will   
            ' flash once per tick of the clock.  
            lblAlarm.Visible = True  
            If blnColorTicker = False Then  
                lblAlarm.BackColor = Color.PeachPuff  
                blnColorTicker = True  
            Else  
                lblAlarm.BackColor = Color.Plum  
                blnColorTicker = False  
            End If  
        Else  
            ' Once the alarm has sounded for a minute, the label is made   
            ' invisible again.  
            lblAlarm.Visible = False  
        End If  
    End Sub  
    ```  
  
     Bu kodu eklenmesi birkaç görev gerçekleştirir. `Overrides` Deyimi temel denetiminden devralındı yöntemi yerine bu yöntemi kullanmak için denetimi yönlendirir. Bu yöntem çağrıldığında, onu geçersiz kılar çağırarak yöntemini çağırır `MyBase.Timer1_Tick` deyimi, tüm işlevlerin özgün denetiminde dahil sağlayarak bu denetimde çoğaltılamaz. Ardından, uyarı işlevselliği eklemek için ek kod çalıştırır. Uyarı oluşur ve sesli bir bip sesi heard yanıp sönen bir etiket denetimi görüntülenir.  
  
    > [!NOTE]
    >  Devralınan bir olay işleyicisi geçersiz kıldıkları için olay ile belirtmek gerekmez `Handles` anahtar sözcüğü. Olay zaten ölçekledikçe. Geçersiz kıldıkları şey işleyicisinin uygulaması.  
  
     Uyarı saat denetiminiz hemen tamamlanır. Kalan tek şey, devre dışı bırakmak için bir yol uygulamaktır. Bunu yapmak için kod ekleyeceksiniz `lblAlarm_Click` yöntemi.  
  
##### <a name="to-implement-the-shutoff-method"></a>Kesici yöntemi uygulamak için  
  
1.  Çözüm Gezgini'nde sağ **ctlAlarmClock.vb**ve ardından **Görünüm Tasarımcısı**.  
  
2.  Tasarımcıda çift **lblAlarm**. **Kod Düzenleyicisi** açılır `Private Sub lblAlarm_Click` satır.  
  
3.  Bu yöntem, aşağıdaki koda benzer şekilde değiştirin.  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
### <a name="using-the-inherited-control-on-a-form"></a>Devralınan Form denetimi kullanma  
 Devralınan denetim temel sınıf denetim test aynı şekilde test edebilirsiniz `ctlClock`: Projeyi oluşturmak ve denetim çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**. Daha fazla bilgi için [nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Denetiminizi kullanmak için koymak için bir form üzerinde barındırmak gerekir. Devralınan bir bileşik denetim standart bileşik denetim gibi tek başına duramaz ve bir form veya diğer kapsayıcı içinde barındırılması gerekir. Bu yana `ctlAlarmClock` daha derinlemesine sahip, işlevselliğini test etmek için ek kod gereklidir. Bu yordamda işlevselliğini test etmek için basit bir program yazacak `ctlAlarmClock`. Ayarlayın ve görüntülemek için kod yazacaksınız `AlarmTime` özelliği `ctlAlarmClock`ve iç işlevleri test eder.  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a>Derleme ve test forma denetim ekleme  
  
1.  Çözüm Gezgini'nde sağ **ctlClockLib**ve ardından **yapı**.  
  
2.  Üzerinde **dosya** menüsünde **Ekle**ve ardından **yeni proje**.  
  
3.  Yeni bir **Windows uygulama** çözüme proje ve adlandırın `Test`.  
  
     **Test** proje çözüm Gezgini'ne eklenir.  
  
4.  Çözüm Gezgini'nde sağ `Test` proje düğümünü ve ardından **Başvuru Ekle** görüntülenecek **Başvuru Ekle** iletişim kutusu.  
  
5.  Etiketli sekmesini **projeleri**. Proje **ctlClockLib** altında listelenen **proje adı**. Çift **ctlClockLib** test projesine başvuru eklenemiyor.  
  
6.  Çözüm Gezgini'nde sağ **Test**ve ardından **yapı**.  
  
7.  İçinde **araç kutusu**, genişletme **ctlClockLib bileşenleri** düğümü.  
  
8.  Çift **ctlAlarmClock** örneğini eklemek için `ctlAlarmClock` formunuza.  
  
9. İçinde **araç kutusu**, bulun ve çift **DateTimePicker** eklemek için bir <xref:System.Windows.Forms.DateTimePicker> Formunuza denetim ve ardından eklemek bir <xref:System.Windows.Forms.Label> denetimi çift tıklayarak **etiketi**.  
  
10. Fare bir kullanışlı yerde form üzerinde denetimleri konumlandırmak için kullanın.  
  
11. Bu denetimin özelliklerini şu şekilde ayarlayın.  
  
    |Denetim|Özellik|Değer|  
    |-------------|--------------|-----------|  
    |`label1`|**Metin**|`(blank space)`|  
    ||**Ad**|`lblTest`|  
    |`dateTimePicker1`|**Ad**|`dtpTest`|  
    ||**Biçim**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. Tasarımcıda çift **dtpTest**.  
  
     **Kod Düzenleyicisi** açılır `Private Sub dtpTest_ValueChanged`.  
  
13. Kodu aşağıdakine benzer şekilde değiştirin.  
  
    ```vb  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. Çözüm Gezgini'nde sağ **Test**ve ardından **başlangıç projesi olarak ayarla**.  
  
15. Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**.  
  
     Test program başlar. Geçerli saat içinde güncelleştirilir Not `ctlAlarmClock` denetimi ve başlangıç saatini gösterildiği <xref:System.Windows.Forms.DateTimePicker> denetimi.  
  
16. Tıklayın <xref:System.Windows.Forms.DateTimePicker> saat, dakika burada görüntülenir.  
  
17. Klavyeyi kullanarak, bir dakika tarafından gösterilen geçerli saatten büyük bir değer dakika ayarlamak `ctlAlarmClock`.  
  
     Uyarı ayar için zaman gösterilen `lblTest`. Uyarı ayarını zaman ulaşmak görüntülenen saat için bekleyin. Görüntülenen tarihten uyarı ayarlanan saate ulaştığında bir bip sesi ve `lblAlarm` flash.  
  
18. Alarmın tıklatarak açın `lblAlarm`. Uyarı artık sıfırlayabilir.  
  
     Bu izlenecek yol, bir dizi temel kavramları kapsamında. Bileşik Denetim kapsayıcıya denetimleri ve Bileşenleri'ni birleştirerek bileşik denetim oluşturulacağını öğrendiniz. Özellikleri denetiminize eklemek ve özel işlevselliği uygulamak üzere kod yazmak için öğrendiniz. Son bölümde, devralma yoluyla belirli bir bileşik denetim işlevlerini genişletmek ve bu yöntemi geçersiz kılarak konak yöntemleri işlevlerini değiştirmek için öğrendiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
- [Nasıl yapılır: Bileşik denetimler yazma](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)
- [Nasıl yapılır: Bir denetimi görüntüleme araç kutusu öğelerini Seç iletişim kutusu](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Bileşen yazma izlenecek yolları](https://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
