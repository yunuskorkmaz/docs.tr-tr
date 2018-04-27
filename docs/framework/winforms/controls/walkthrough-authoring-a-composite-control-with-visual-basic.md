---
title: 'İzlenecek yol: Visual Basic İle Bileşik Denetim Yazma'
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
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 71d1da2767ca15c4f78a4297d916f735a0ad604c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a>İzlenecek yol: Visual Basic İle Bileşik Denetim Yazma
Bileşik denetimler olarak özel grafik arabirimler oluşturulabilir yeniden ve bir yol sağlar. Bileşik Denetim aslında bir görsel gösterimi ile bileşenidir. Bu nedenle, bir veya daha fazla Windows Forms denetimleri, bileşenleri veya kullanıcı girişini doğrulama, görüntü özelliklerini değiştirme veya yazar tarafından gerekli diğer görevleri gerçekleştirme işlevselliğini genişletebildiği kod bloklarını oluşabilir. Bileşik denetimler, diğer denetimler aynı şekilde Windows Forms'ta yerleştirilebilir. Bu kılavuzun ilk bölümünde oluşturduğunuz adlı basit bir bileşik denetim `ctlClock`. İzlenecek yol ikinci bölümünde, işlevselliğini genişletmek `ctlClock` devralma yoluyla.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adı ayarlayabilir ve varsayılan bileşen doğru ad alanında olduğundan emin olmak için adı belirtin.  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>CtlClockLib denetim kitaplığı ve ctlClock denetimi oluşturmak için  
  
1.  Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje** açmak için **yeni proje** iletişim kutusu.  
  
2.  Visual Basic projeleri listesinden seçin **Windows Denetim Kitaplığı** proje şablonu, türü `ctlClockLib` içinde **adı** kutusuna ve ardından **Tamam**.  
  
     Proje adı `ctlClockLib`, kök ad alanı için varsayılan olarak da atanmış. Kök ad derleme bileşenlerinde adlarını nitelemek için kullanılır. Örneğin, iki derleme adlı bileşenleri sağlarsanız `ctlClock`, belirtebilirsiniz, `ctlClock` bileşenini kullanarak `ctlClockLib.ctlClock.`  
  
3.  Çözüm Gezgini'nde sağ **UserControl1.vb**ve ardından **yeniden adlandırma**. Dosya adını değiştirmek `ctlClock.vb`. Tıklatın **Evet** düğmesini code öğesi "UserControl1" yapılan tüm başvuruları yeniden adlandırmak istediğiniz sorulduğunda.  
  
    > [!NOTE]
    >  Varsayılan olarak, bileşik denetim devraldığı <xref:System.Windows.Forms.UserControl> sistem tarafından sağlanan sınıfı. <xref:System.Windows.Forms.UserControl> Sınıf tarafından tüm bileşik denetimler gerekli işlevselliği sunar ve standart yöntemleri ve özellikleri uygular.  
  
4.  Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Windows ekleme denetimleri ve bileşenleri bileşik denetim için  
 Görsel bir arabirim bileşik denetim önemli bir parçasıdır. Bu görsel arabirimi bir veya daha fazla Windows denetimleri Tasarımcı yüzeyine eklenmesi tarafından uygulanır. Aşağıdaki örnekte Windows denetimleri bileşik denetime birleştirme ve işlevselliği uygulamak için kod yazma.  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Bir etiket ve bir Zamanlayıcı, bileşik denetim eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlClock.vb**ve ardından **Görünüm Tasarımcısı**.  
  
2.  Araç kutusunda genişletin **ortak denetimler** düğümü ve çift tıklatarak **etiket**.  
  
     A <xref:System.Windows.Forms.Label> adlı Denetim `Label1` Tasarımcı yüzeyine denetiminizde eklenir.  
  
3.  Tasarımcısı'nda tıklayın **Label1**. Özellikler penceresinde aşağıdaki özellikleri ayarlayın.  
  
    |Özellik|Değiştirin|  
    |--------------|---------------|  
    |**Ad**|`lblDisplay`|  
    |**Metin**|`(blank space)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  İçinde **araç**, genişletin **bileşenleri** düğümü ve çift tıklatarak **Zamanlayıcı**.  
  
     Çünkü bir <xref:System.Windows.Forms.Timer> bir bileşen olan çalışma zamanında görsel gösterimi bulunmaz. Bu nedenle, Tasarımcı yüzeyine, ancak yerine tasarımcıda bileşeni (tasarımcı yüzeyine altındaki bir Tepsisi) denetimleriyle görünmez.  
  
5.  Bileşen Tasarımcısı'nda tıklayın **Süreölçer1**ve ardından <xref:System.Windows.Forms.Timer.Interval%2A> özelliğine `1000` ve <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğine `True`.  
  
     <xref:System.Windows.Forms.Timer.Interval%2A> Özelliği ile Zamanlayıcı bileşeni işaretlerini sıklığı denetler. Her zaman `Timer1` çizgilerine, bunu çalışan kodu `Timer1_Tick` olay. Aralık çizgilerine arasındaki milisaniye sayısını temsil eder.  
  
6.  Bileşen tasarımcısında çift **Süreölçer1** gitmek için `Timer1_Tick` olayı `ctlClock`.  
  
7.  Aşağıdaki kod örneği benzer şekilde kodu değiştirin. Gelen erişim değiştiricisi değiştirdiğinizden emin olun `Private` için `Protected`.  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     Bu kod gösterilecek geçerli saati neden olacak `lblDisplay`. Çünkü aralığı `Timer1` ayarlandı `1000`, böylece her saniye geçerli saati güncelleştiriliyor her bin milisaniyede bu olay meydana gelir.  
  
8.  Geçersiz kılınabilir olacak şekilde değiştirin. Daha fazla bilgi için aşağıdaki "Devralan bir kullanıcı denetimi" bölümüne bakın.  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="adding-properties-to-the-composite-control"></a>Bileşik Denetim Özellikler ekleme  
 Saat denetiminizi şimdi yalıtan bir <xref:System.Windows.Forms.Label> denetim ve <xref:System.Windows.Forms.Timer> bileşeni, her biri kendi devralınmış özellikler kümesi. Bu denetimlerin ayrı ayrı özellikler denetiminizi sonraki kullanıcılara erişilemeyecek olsa da, oluşturabilir ve uygun kod bloklarını yazarak özel özelliklerini ortaya. Aşağıdaki yordamda, arka plan ve metin rengini değiştirmek kullanıcının denetiminizi özellikler ekleyeceksiniz.  
  
#### <a name="to-add-a-property-to-your-composite-control"></a>Bir özellik için bileşik denetim eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlClock.vb**ve ardından **görünümü kodu**.  
  
     Kod Düzenleyicisi'ni denetlemek için açılır.  
  
2.  Bulun `Public Class ctlClock` deyimi. Altında aşağıdaki kodu yazın.  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     Bu deyimler oluşturmak üzere olduğunuz özelliklerinin değerlerini depolamak için kullanacağı özel değişkenler oluşturun.  
  
3.  Adım 2 ' değişken bildirimleri altına aşağıdaki kodu ekleyin.  
  
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
  
     Önceki kod iki özel özellikler yapar `ClockForeColor` ve `ClockBackColor`, çağırma tarafından bu denetimin sonraki kullanıcıların kullanımına `Property` deyimi. `Get` Ve `Set` deyimleri, depolama ve alma, işlevselliği uygulamak için kodu yanı sıra özellik değeri, özellik için uygun için sağlar.  
  
4.  Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="testing-the-control"></a>Denetim test etme  
 Denetimleri tek başına projeleri değildir; bir kapsayıcıda barındırılmalıdır. Denetimin çalışma zamanı davranışını sınama ve özellikleriyle birlikte çalışma **UserControl Test kapsayıcısı**. Daha fazla bilgi için bkz: [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-your-control"></a>Denetim sınamak için  
  
1.  Projeyi derlemek ve denetiminizin çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.  
  
2.  Test kapsayıcının özellik kılavuzunda seçin `ClockBackColor` özelliği ve renk paletini görüntülemek için açılan oku tıklatın.  
  
3.  Bir renk tıklayarak seçin.  
  
     Denetim arka plan rengini seçtiğiniz renge dönüşür.  
  
4.  Doğrulamak için benzer bir olay dizisi kullanmak `ClockForeColor` özelliği beklendiği gibi çalışmıyor.  
  
5.  Tıklatın **kapatmak** kapatmak için **UserControl Test kapsayıcısı**.  
  
     Bu bölümde ve önceki bölümlerde, bileşenleri ve Windows denetimleri nasıl birleştirileceğini gördünüz kodla ve paketleme bileşik denetim biçiminde özel işlevsellik sağlar. Bileşik Denetim ve onu tamamlandıktan sonra Denetim test etme özelliklerinde kullanıma sunmak öğrendiniz. Sonraki bölümde nasıl kullanarak bir devralınan bileşik denetim oluşturulacağını öğreneceksiniz `ctlClock` temel olarak.  
  
## <a name="inheriting-from-a-composite-control"></a>Bileşik denetimden devralma  
 Önceki bölümlerde Windows denetimleri, bileşenleri ve kod yeniden kullanılabilir bileşik denetimlere birleştirmek öğrendiniz. Bileşik Denetim artık bağlı diğer denetimleri oluşturulabilir temel olarak kullanılabilir. Sınıf bir taban sınıftan türetme işlemi adlı *devralma*. Bu bölümde, adlı bileşik denetim oluşturacak `ctlAlarmClock`. Bu denetim kendi üst denetiminden türetilen `ctlClock`. İşlevlerini genişletmek öğreneceksiniz `ctlClock` üst yöntemleri geçersiz kılma ve yeni yöntemleri ve özellikleri ekleyerek.  
  
 Devralınan bir denetim oluşturmanın ilk adımı, üst öğesinden türetilen olmaktır. Bu eylem tüm özellikleri, yöntemleri ve üst denetim grafik özelliklere sahip yeni bir denetim oluşturur, ancak aynı zamanda yeni veya değiştirilmiş işlevselliği eklenmesi için bir temel olarak çalışabilir.  
  
#### <a name="to-create-the-inherited-control"></a>Devralınan denetimi oluşturmak için  
  
1.  Çözüm Gezgini'nde sağ **ctlClockLib**, işaret **Ekle**ve ardından **kullanıcı denetimi**.  
  
     **Yeni Öğe Ekle** iletişim kutusu açılır.  
  
2.  Seçin **devralınan kullanıcı denetimi** şablonu.  
  
3.  İçinde **adı** kutusuna `ctlAlarmClock.vb`ve ardından **Ekle**.  
  
     **Devralma Seçici** iletişim kutusu görüntülenir.  
  
4.  Altında **bileşen adı**, çift **ctlClock**.  
  
5.  Çözüm Gezgini'nde geçerli projeleri göz atın.  
  
    > [!NOTE]
    >  Dosya adında **ctlAlarmClock.vb** geçerli projeye eklendi.  
  
### <a name="adding-the-alarm-properties"></a>Uyarı Özellikler ekleme  
 Özellikler devralınan bir denetimi için bileşik denetim eklenen aynı şekilde eklenir. Şimdi özelliği bildiriminin sözdizimi denetiminize iki özellik eklemek için kullanacağınız: `AlarmTime`, tarih ve saat uyarı olduğu kapalı, Git değerini depolar ve `AlarmSet`, hangi uyarı ayarlanıp ayarlanmadığını gösterilir.  
  
##### <a name="to-add-properties-to-your-composite-control"></a>Bileşik denetiminizi özellikleri eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlAlarmClock**ve ardından **görünümü kodu**.  
  
2.  Sınıf bildirimi olarak görünür ctlAlarmClock denetiminin bulun `Public Class ctlAlarmClock`.  Sınıf bildiriminde aşağıdaki kodu ekleyin.  
  
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
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a>Denetim grafik arabirimine ekleme  
 Devralınan denetiminizi öğesinden devralınan denetlemek için aynı olan bir görsel arabirimine sahiptir. Aynı bağlı denetimler, üst denetim olarak sahip, ancak özellikle sunulan sürece bağlı denetimlerin özelliklerini kullanılabilir olmaz. Herhangi bir bileşik denetimi eklediğiniz gibi aynı şekilde devralınan bir bileşik denetim grafik arabirimine ekleyebilir. Uyarı saatin visual arabirimine eklemeye devam etmek için uyarı uyarabilir yükleyen yanar bir etiket denetimi ekleyeceksiniz.  
  
##### <a name="to-add-the-label-control"></a>Etiket denetimi eklemek için  
  
1.  Çözüm Gezgini'nde sağ **ctlAlarmClock**, tıklatıp **Görünüm Tasarımcısı**.  
  
     Tasarımcı `ctlAlarmClock` ana pencerede açar.  
  
2.  Tıklatın `lblDisplay` (denetimin görüntüleme bölümü) ve Özellikler penceresini görüntüleyin.  
  
    > [!NOTE]
    >  Tüm özellikleri görüntülenir, ancak bunlar soluklaştırılır. Bu bu özellikleri için yerel gösterir `lblDisplay` ve değiştirilemez veya Özellikler penceresinde erişilebilir. Varsayılan olarak, bu bileşik denetim içinde yer alan denetimleridir `Private`, ve bunların özelliklerini herhangi bir yolla erişilemiyor.  
  
    > [!NOTE]
    >  Bileşik denetiminizin sonraki kullanıcıların iç denetimlerinden erişmesini isterseniz, bunları olarak bildirin `Public` veya `Protected`. Bu, ayarlamak ve uygun kodu kullanarak bileşik denetim içinde yer alan denetimlerin özelliklerini değiştirmek olanak tanır.  
  
3.  Ekleme bir <xref:System.Windows.Forms.Label> denetimi için bileşik denetim.  
  
4.  Fareyle sürükleyin <xref:System.Windows.Forms.Label> kutusunu hemen altındaki denetim. Özellikler penceresinde aşağıdaki özellikleri ayarlayın.  
  
    |Özellik|Ayar|  
    |--------------|-------------|  
    |**Ad**|`lblAlarm`|  
    |**Metin**|**Uyarı!**|  
    |**TextAlign**|`MiddleCenter`|  
    |**Görünür**|`False`|  
  
### <a name="adding-the-alarm-functionality"></a>Uyarı işlevsellik ekleme  
 Önceki yordamlarda, özellikleri ve bileşik denetim alarm işlevselliği sağlayacak bir denetim eklendi. Bu yordamda, alarm saati geçerli zamanın karşılaştırmak için kod ekleyeceksiniz ve aynı, ses ve bir alarm flash olmaları durumunda. Geçersiz kılma tarafından `Timer1_Tick` yöntemi `ctlClock` ve ek kod eklemeyi, yeteneğini uzatır `ctlAlarmClock` tüm devralınmış işlevselliğini korurken `ctlClock`.  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a>CtlClock Timer1_Tick yöntemi geçersiz kılmak için  
  
1.  Çözüm Gezgini'nde sağ **ctlAlarmClock.vb**ve ardından **görünümü kodu**.  
  
2.  Bulun `Private blnAlarmSet As Boolean` deyimi. Hemen altında aşağıdaki deyimini ekleyin.  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  Bulun `End Class` sayfanın sonundaki deyimi. Hemen önce `End Class` deyimi, aşağıdaki kodu ekleyin.  
  
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
  
     Bu kod ayrıca çeşitli görevleri gerçekleştirir. `Overrides` Deyimi temel denetiminden devralındı yöntemi yerine bu yöntemi kullanmak için Denetim yönlendirir. Bu yöntem çağrıldığında, geçersiz kılmalar harekete geçirerek yöntemi çağırır `MyBase.Timer1_Tick` deyimi, tüm işlevleri özgün denetiminde birleştirilmiş sağlayarak bu denetimde çoğaltılamaz. Daha sonra uyarı işlevselliği birleştirmek için ek kod çalıştırır. Uyarı oluşur ve bir sesli bip seslerini yanıp sönen bir etiket denetimi görünür.  
  
    > [!NOTE]
    >  Devralınmış olay işleyicisi geçersiz kılmak için olay ile belirtmeniz gerekmez `Handles` anahtar sözcüğü. Olay zaten sayfaya. Geçersiz kılma tek şey işleyicisinin uygulaması.  
  
     Alarm saati denetiminizi neredeyse tamamlandı. Kalan tek şey, devre dışı bırakmak için bir yol uygulamaktır. Bunu yapmak için kod ekleyeceksiniz `lblAlarm_Click` yöntemi.  
  
##### <a name="to-implement-the-shutoff-method"></a>Kesici yöntemi uygulamak için  
  
1.  Çözüm Gezgini'nde sağ **ctlAlarmClock.vb**ve ardından **Görünüm Tasarımcısı**.  
  
2.  Tasarımcıda çift **lblAlarm**. **Kod düzenleyicisinde** açılır `Private Sub lblAlarm_Click` satır.  
  
3.  Bu yöntem, aşağıdaki kodu benzer şekilde değiştirin.  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** projeyi kaydetmek için.  
  
### <a name="using-the-inherited-control-on-a-form"></a>Bir Form üzerinde devralınan denetimi kullanma  
 Taban sınıfı denetim test aynı şekilde, devralınan denetim sınayabilirsiniz `ctlClock`: F5 tuşuna basarak projeyi oluşturun ve denetiminizin Çalıştır **UserControl Test kapsayıcısı**. Daha fazla bilgi için bkz: [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Kullanmak için denetim yerleştirmek için bir form üzerinde barındırmak gerekir. Standart bileşik denetim olarak, devralınan bir bileşik denetim tek başına olamaz ve bir form veya diğer kapsayıcı barındırılması gerekir. Bu yana `ctlAlarmClock` daha derinlemesine sahip işlevselliğini, test için ek kod gereklidir. Bu yordamda işlevselliğini sınamak için basit bir program yazacaksınız `ctlAlarmClock`. Ayarlama ve görüntülemek için kod yazacaksınız `AlarmTime` özelliği `ctlAlarmClock`ve devralınan işlevleri test.  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a>Yapı ve test forma denetim ekleme  
  
1.  Çözüm Gezgini'nde sağ **ctlClockLib**ve ardından **yapı**.  
  
2.  Üzerinde **dosya** menüsündeki **Ekle**ve ardından **yeni proje**.  
  
3.  Yeni bir ekleme **Windows uygulaması** proje çözüme ve adlandırın `Test`.  
  
     **Test** proje çözüm Gezgini'ne eklenir.  
  
4.  Çözüm Gezgini'nde sağ `Test` proje düğümünü ve ardından **Başvuru Ekle** görüntülemek için **Başvuru Ekle** iletişim kutusu.  
  
5.  Etiketli sekmesini **projeleri**. Proje **ctlClockLib** altında listelenen **proje adı**. Çift **ctlClockLib** test projesinin başvuru eklemek için.  
  
6.  Çözüm Gezgini'nde sağ **Test**ve ardından **yapı**.  
  
7.  İçinde **araç**, genişletin **ctlClockLib bileşenleri** düğümü.  
  
8.  Çift **ctlAlarmClock** örneği eklemek için `ctlAlarmClock` formunuza.  
  
9. İçinde **araç**, bulun ve çift tıklatın **DateTimePicker** eklemek için bir <xref:System.Windows.Forms.DateTimePicker> formunuza denetlemek ve ardından ekleyin bir <xref:System.Windows.Forms.Label> çift tıklatarak denetim **etiket**.  
  
10. Denetimleri form üzerinde uygun bir konuma yerleştirmek için fare kullanın.  
  
11. Bu denetimlerin özelliklerini aşağıdaki şekilde ayarlayın.  
  
    |Denetim|Özellik|Değer|  
    |-------------|--------------|-----------|  
    |`label1`|**Metin**|`(blank space)`|  
    ||**Ad**|`lblTest`|  
    |`dateTimePicker1`|**Ad**|`dtpTest`|  
    ||**Biçimi**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. Tasarımcıda çift **dtpTest**.  
  
     **Kod düzenleyicisinde** açılır `Private Sub dtpTest_ValueChanged`.  
  
13. Aşağıdakine benzer şekilde kodu değiştirin.  
  
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
  
15. Üzerinde **hata ayıklama** menüsünde tıklatın **hata ayıklamayı Başlat**.  
  
     Test program başlar. Geçerli saat içinde güncelleştirilir Not `ctlAlarmClock` denetimi ve başlangıç saatini gösterildiği <xref:System.Windows.Forms.DateTimePicker> denetim.  
  
16. Tıklatın <xref:System.Windows.Forms.DateTimePicker> saat, dakika görüntülendiği.  
  
17. Klavye kullanılarak ayarlanan bir dakika tarafından gösterilen geçerli saatten büyük bir değer dakika `ctlAlarmClock`.  
  
     Uyarı ayarı süredir gösterilen `lblTest`. Uyarı ayarı zaman ulaşmak görüntülenen bir süre bekleyin. Görüntülenen saati alarmı ayarlamak saatine ulaştığında, bip sesi ve `lblAlarm` flash.  
  
18. Tıklayarak alarmı devre dışı bırakma `lblAlarm`. Uyarı artık sıfırlayabilir.  
  
     Bu kılavuz temel kavramları sayısı ele. Bileşik Denetim kapsayıcıya denetimleri ve bileşenleri birleştiren bileşik denetim oluşturmak öğrendiniz. Denetiminize özellikleri ekleyin ve özel işlevsellik uygulamak için kod yazma öğrendiniz. Son bölümünde devralma yoluyla belirli bir bileşik denetim işlevselliğini genişletmek ve bu yöntemi geçersiz kılarak konak yöntemleri işlevselliğini alter öğrendiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Nasıl yapılır: Bileşik Denetimler Yazma](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [Bileşen geliştirme izlenecek yollar](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
