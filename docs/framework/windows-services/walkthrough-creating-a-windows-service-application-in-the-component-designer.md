---
title: 'İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmet Uygulaması Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Service applications, walkthroughs
- Windows Service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
manager: douge
ms.openlocfilehash: c33b8badcacd4e228d70f8e770d4bf27144c29eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520519"
---
# <a name="walkthrough-creating-a-windows-service-application-in-the-component-designer"></a>İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmet Uygulaması Oluşturma
Bu makalede, bir olay günlüğü iletileri Yazar Visual Studio'da basit bir Windows hizmet uygulaması oluşturmak gösterilmiştir. Hizmetinizi oluşturmak için gerçekleştirdiğiniz temel adımlar şunlardır:  
  
1.  [Bir hizmet oluşturma](#BK_CreateProject) kullanarak **Windows hizmeti** proje şablonu ve yapılandırın. Bu şablon, devraldığı sizin için bir sınıf oluşturur <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> ve hizmeti başlatmak için kod gibi temel hizmeti kodu çoğunu yazar.  
  
2.  [Hizmete özellik ekleme](#BK_WriteCode) için <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yordamları ve yeniden tanımlamak istediğiniz diğer yöntemleri geçersiz kılın.  
  
3.  [Hizmet durumu ayarı](#BK_SetStatus). Varsayılan olarak, hizmetler ile oluşturulan <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> yalnızca bir alt kümesini kullanılabilir durumu bayrakları uygular. Hizmet başlatma, duraklatma veya durdurmak için bir uzun sürüyorsa, durum değerleri Beklemede Başlat veya Durdur Beklemede üzerinde bir işlemi çalıştığını göstermek için gibi uygulayabilirsiniz.  
  
4.  [Yükleyici hizmetine ekleme](#BK_AddInstallers) hizmet uygulamanız için.  
  
5.  (İsteğe bağlı) [Ayarlanan başlangıç parametreleri](#BK_StartupParameters), varsayılan başlangıç bağımsız değişkenleri belirtin ve hizmetinizi el ile başlattığınızda, varsayılan ayarları geçersiz kılacak olanağı verir.  
  
6.  [Hizmet oluşturma](#BK_Build).  
  
7.  [Hizmeti yükleme](#BK_Install) yerel makine üzerinde.  
  
8.  Windows Hizmet Denetimi Yöneticisi'ne erişmek ve [başlatma ve hizmet çalıştırma](#BK_StartService).  
  
9. [Bir Windows hizmeti kaldırma](#BK_Uninstall).  
  
> [!WARNING]
>  Bu izlenecek yol için gerekli olan Windows Hizmetleri proje şablonu Visual Studio'nun Express sürümünde bulunmamaktadır.  
  
 [!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]  
  
<a name="BK_CreateProject"></a>   
## <a name="creating-a-service"></a>Hizmet Oluşturma  
 Başlamak için projeyi oluşurun ve hizmetin düzgün çalışması için gerekli değerleri ayarlayın.  
  
#### <a name="to-create-and-configure-your-service"></a>Hizmetinizi oluşturmak ve yapılandırmak için  
  
1.  Menü çubuğunda, Visual Studio'da seçin **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
2.  Visual Basic veya Visual C# proje şablonları listesinden seçip **Windows hizmeti**ve proje adı **MyNewService**. Seçin **Tamam**.  
  
     Proje şablonu otomatik olarak adında bir bileşen sınıfı ekler `Service1` devraldığı <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.  
  
3.  Üzerinde **Düzenle** menüsünde seçin **bulma ve değiştirme**, **dosyalarda Bul** (klavye: Ctrl + Shift + F). Tüm oluşumlarını değiştirme `Service1` için `MyNewService`. Örnekleri service1.cs dosyasını, Program.cs ve Service1.Designer.cs (veya .vb eşdeğerlerine) bulabilirsiniz.  
  
4.  İçinde **özellikleri** penceresi **service1.cs dosyasını [tasarım]** veya **Service1.vb [tasarım]** ayarlayın <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> ve **(ad)** özelliği için `Service1` için **MyNewService**, zaten ayarlanmışsa.  
  
5.  Çözüm Gezgini'nde, yeniden adlandırma **service1.cs dosyasını** için **MyNewService.cs**, veya **Service1.vb** için **MyNewService.vb**.  
  
<a name="BK_WriteCode"></a>   
## <a name="adding-features-to-the-service"></a>Hizmete Özellik Ekleme  
 Bu bölümde, Windows hizmeti için özel bir olay günlüğü ekleyin. Olay günlükleri, Windows hizmetleri ile hiçbir şekilde ilişkili değildir. Burada <xref:System.Diagnostics.EventLog> bileşeni Bileşen Ekle, bir Windows hizmeti için tür bir örnek olarak kullanılır.  
  
#### <a name="to-add-custom-event-log-functionality-to-your-service"></a>Hizmetinize özelleştirilmiş olay günlüğü işlevselliği eklemek için  
  
1.  İçinde **Çözüm Gezgini**, bağlam menüsünü açın **MyNewService.cs** veya **MyNewService.vb**ve ardından **Görünüm Tasarımcısı**.  
  
2.  Gelen **bileşenleri** bölümünü **araç**, sürükleyin bir <xref:System.Diagnostics.EventLog> bileşenini tasarımcıya.  
  
3.  İçinde **Çözüm Gezgini**, bağlam menüsünü açın **MyNewService.cs** veya **MyNewService.vb**ve ardından **görünümü kodu**.  
  
4.  İçin bir bildirim eklemek **eventLog** nesnesinde `MyNewService` sağ bildirir satırından sonra bir sınıf `components` değişkeni:  
  
     [!code-csharp[VbRadconService#16](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#16)]
     [!code-vb[VbRadconService#16](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#16)]  
  
5.  Ekle veya özel bir olay günlüğü tanımlamak için oluşturucu düzenleyin:  
  
     [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
     [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]  
  
#### <a name="to-define-what-occurs-when-the-service-starts"></a>Hizmet başlatıldığında ne olacağını tanımlamak için  
  
-   Kod Düzenleyicisi'nde bulun <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodun proje oluşturduğunuzda otomatik olarak geçersiz kılındı ve kodu aşağıdakilerle değiştirin. Hizmet çalışmaya başladığında bu olay günlüğüne bir giriş ekler:  
  
     [!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
     [!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]  
  
     Bir hizmet uygulaması genellikle yoklar veya bir şey sistemde izler uzun süreli olacak şekilde tasarlanmıştır. İzleme ayarlanır <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi. Ancak, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> gerçekten izleme yapmaz. <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Yöntemi hizmetin işlemi başladıktan sonra işletim sistemine döndürmesi gerekir. Sonsuza kadar döngü veya engelleme gerçekleştirmemelidir. Basit yoklama mekanizması kurmak için kullanabilirsiniz <xref:System.Timers.Timer?displayProperty=nameWithType> bileşen şekilde: içinde <xref:System.ServiceProcess.ServiceBase.OnStart%2A> bileşeni parametreleri ayarlayın ve ardından yöntemi <xref:System.Timers.Timer.Enabled%2A> özelliğine `true`. Düzenli aralıklarla, aynı zamanda hizmetiniz izlemeyi yapabileceği olayları kodunuzda süreölçer başlatır. Bunu yapmak için aşağıdaki kodu kullanabilirsiniz:  
  
    ```csharp  
    // Set up a timer to trigger every minute.  
    System.Timers.Timer timer = new System.Timers.Timer();  
    timer.Interval = 60000; // 60 seconds  
    timer.Elapsed += new System.Timers.ElapsedEventHandler(this.OnTimer);  
    timer.Start();  
    ```  
  
    ```vb  
    ' Set up a timer to trigger every minute.  
    Dim timer As System.Timers.Timer = New System.Timers.Timer()  
    timer.Interval = 60000 ' 60 seconds  
    AddHandler timer.Elapsed, AddressOf Me.OnTimer  
    timer.Start()  
    ```  
     Üye değişkeni sınıfına ekleyin. Olay günlüğüne yazmak için sonraki olay tanımlayıcı içerecektir.

    ```csharp
    private int eventId = 1;
    ```

    ```vb
    Private eventId As Integer = 1
    ```

     Süreölçer olayı işlemek için kodu ekleyin:  
  
    ```csharp  
    public void OnTimer(object sender, System.Timers.ElapsedEventArgs args)  
    {  
        // TODO: Insert monitoring activities here.  
        eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId++);  
    }  
    ```  
  
    ```vb  
    Private Sub OnTimer(sender As Object, e As Timers.ElapsedEventArgs)  
        ' TODO: Insert monitoring activities here.  
        eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId)  
        eventId = eventId + 1  
    End Sub  
    ```  
  
     Tüm iş ana iş parçacığında çalıştırmak yerine arka plan iş parçacıklarını kullanarak görevleri isteyebilirsiniz. Bu örneği için bkz: <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> başvuru sayfası.  
  
#### <a name="to-define-what-occurs-when-the-service-is-stopped"></a>Hizmet durdurulduğunda ne olacağını tanımlamak için  
  
-   Kodunu değiştir <xref:System.ServiceProcess.ServiceBase.OnStop%2A> aşağıdaki yöntemi. Hizmet durdurulduğunda bu olay günlüğüne bir giriş ekler:  
  
     [!code-csharp[VbRadconService#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
     [!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]  
  
 Sonraki bölümde kılmanız <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, ve <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> bileşeniniz için ek işleme tanımlamak için yöntemleri.  
  
#### <a name="to-define-other-actions-for-the-service"></a>Hizmete ilişkin diğer eylemleri tanımlamak için  
  
-   İşlemek istediğiniz yöntemi bulun ve onu gerçekleştirilmesini istediğiniz tanımlamak için geçersiz.  
  
     Aşağıdaki kod, nasıl kılabilirsiniz gösterir <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> yöntemi:  
  
     [!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
     [!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]  
  
 Bazı özel eylemler bir Windows hizmeti tarafından yüklendiğinde ortaya zorunda <xref:System.Configuration.Install.Installer> sınıfı. Visual Studio, bu yükleyicileri bir Windows hizmeti için özel olarak oluşturabilir ve sonra da projenize ekleyebilir.  
  
<a name="BK_SetStatus"></a>   
## <a name="setting-service-status"></a>Ayar hizmet durumu  
 Kullanıcılar bir hizmet doğru şekilde çalışıp çalışmadığını yapıp yapmadığını Hizmetleri için hizmet denetimi yöneticisi, kendi durumlarını bildirebilir. Varsayılan olarak, devralınan Hizmetleri <xref:System.ServiceProcess.ServiceBase> durdurulmuş, duraklatılmış ve çalıştıran sınırlı sayıda durum ayarları dahil olmak üzere, rapor. Bunun başlatmak için Başlat bekleme durumu raporlamak faydalı olabilir ancak bir hizmet biraz uzun sürerse. Pencerelere çağıran kodu ekleyerek bekleyen başlatmak ve durdurmak bekleyen durum ayarlarını uygulayabilirsiniz [artırılmış işlevi](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx).  
  
#### <a name="to-implement-service-pending-status"></a>Hizmet Durumu Beklemede uygulamak için  
  
1.  Ekleme bir `using` deyimi veya `Imports` bildirimine <xref:System.Runtime.InteropServices?displayProperty=nameWithType> MyNewService.cs veya MyNewService.vb dosyasındaki ad alanı:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    ```  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    ```  
  
2.  Bildirmek için MyNewService.cs için aşağıdaki kodu ekleyin `ServiceState` değerleri ve bir platform kullanacağınız durumu için bir yapı çağırma çağrısı eklemek için:  
  
    ```csharp  
    public enum ServiceState  
      {  
          SERVICE_STOPPED = 0x00000001,  
          SERVICE_START_PENDING = 0x00000002,  
          SERVICE_STOP_PENDING = 0x00000003,  
          SERVICE_RUNNING = 0x00000004,  
          SERVICE_CONTINUE_PENDING = 0x00000005,  
          SERVICE_PAUSE_PENDING = 0x00000006,  
          SERVICE_PAUSED = 0x00000007,  
      }  
  
      [StructLayout(LayoutKind.Sequential)]  
      public struct ServiceStatus  
      {  
          public int dwServiceType;  
          public ServiceState dwCurrentState;  
          public int dwControlsAccepted;  
          public int dwWin32ExitCode;  
          public int dwServiceSpecificExitCode;  
          public int dwCheckPoint;  
          public int dwWaitHint;  
      };  
    ```  
  
    ```vb  
    Public Enum ServiceState  
        SERVICE_STOPPED = 1  
        SERVICE_START_PENDING = 2  
        SERVICE_STOP_PENDING = 3  
        SERVICE_RUNNING = 4  
        SERVICE_CONTINUE_PENDING = 5  
        SERVICE_PAUSE_PENDING = 6  
        SERVICE_PAUSED = 7  
    End Enum  
  
    <StructLayout(LayoutKind.Sequential)>  
    Public Structure ServiceStatus  
        Public dwServiceType As Long  
        Public dwCurrentState As ServiceState  
        Public dwControlsAccepted As Long  
        Public dwWin32ExitCode As Long  
        Public dwServiceSpecificExitCode As Long  
        Public dwCheckPoint As Long  
        Public dwWaitHint As Long  
    End Structure  
    ```  
  
3.  Şimdi `MyNewService` sınıfı, bildirme [artırılmış işlevi](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) platformu kullanarak çağırın:  
  
    ```csharp  
    [DllImport("advapi32.dll", SetLastError=true)]  
            private static extern bool SetServiceStatus(IntPtr handle, ref ServiceStatus serviceStatus);  
    ```  
  
    ```vb  
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean  
    ```  
  
4.  Başlangıç bekleme durumu uygulamak için aşağıdaki kodu başlangıcına ekleyin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi:  
  
    ```csharp  
    // Update the service state to Start Pending.  
    ServiceStatus serviceStatus = new ServiceStatus();  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING;  
    serviceStatus.dwWaitHint = 100000;  
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);  
    ```  
  
    ```vb  
    ' Update the service state to Start Pending.  
    Dim serviceStatus As ServiceStatus = New ServiceStatus()  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING  
    serviceStatus.dwWaitHint = 100000  
    SetServiceStatus(Me.ServiceHandle, serviceStatus)  
    ```  
  
5.  Sonunda çalıştırmaya durumunu ayarlamak için kod ekleme <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi.  
  
    ```csharp
    // Update the service state to Running.  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING;  
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);  
    ```  
  
    ```vb  
    ' Update the service state to Running.  
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING  
    SetServiceStatus(Me.ServiceHandle, serviceStatus)  
    ```  
  
6.  (İsteğe bağlı) İçin bu yordamı yineleyin <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemi.  
  
> [!CAUTION]
>  [Hizmet Denetim Yöneticisi](http://msdn.microsoft.com/library/windows/desktop/ms685150.aspx) kullanan `dwWaitHint` ve `dwCheckpoint` üyeleri [SERVICE_STATUS yapısı](http://msdn.microsoft.com/library/windows/desktop/ms685996.aspx) başlatmak veya kapatmak bir Windows hizmeti için ne kadar süre belirlemek için. Varsa, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemlerini çalıştırma uzun, hizmetiniz daha fazla zaman çağırarak isteyebilir [artırılmış](http://msdn.microsoft.com/library/windows/desktop/ms686241.aspx) yeniden ile bir artırılır `dwCheckPoint` değeri.  
  
<a name="BK_AddInstallers"></a>   
## <a name="adding-installers-to-the-service"></a>Hizmete yükleyici ekleme  
 Bir Windows hizmeti çalıştırmadan önce hangi hizmet denetimi Yöneticisi ile kaydeder yüklemeniz gerekir. Kayıt ayrıntıları ele projenize yükleyicileri ekleyebilirsiniz.  
  
#### <a name="to-create-the-installers-for-your-service"></a>Hizmetinize ilişkin yükleyicileri oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, bağlam menüsünü açın **MyNewService.cs** veya **MyNewService.vb**ve ardından **Görünüm Tasarımcısı**.  
  
2.  Hizmetin herhangi bir içeriğini değil de, hizmetin kendisini seçmek için tasarımcının arka planına tıklayın.  
  
3.  (Sağ penceresi içinde bir işaretleme aygıtı kullanıyorsanız) Tasarımcı penceresinin bağlam menüsünü açın ve ardından **Yükleyici Ekle**.  
  
     Varsayılan olarak, projenize iki yükleyici içeren bir bileşen sınıfı eklenir. Bileşen adlı **ProjectInstaller**ve içerdiği yükleyiciler hizmetiniz için yükleyici ve yükleyici hizmeti için işlem ilişkili.  
  
4.  İçinde **tasarım** görüntüleme **ProjectInstaller**, seçin **Serviceınstaller1** bir Visual C# projesi için veya **Serviceınstaller1** görsel için Temel projesi.  
  
5.  İçinde **özellikleri** penceresinde emin olun <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliği ayarlanmış **MyNewService**.  
  
6.  Ayarlama **açıklama** "Örnek hizmeti" gibi bazı metinleri özelliğine. Bu metin hizmetleri penceresinde görüntülenir ve kullanıcının Hizmeti'ni tanımlamak ve hangi amaçla kullanıldığına anlamanıza yardımcı olur.  
  
7.  Ayarlama <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> Hizmetleri penceresinde görüntülenmesini istediğiniz metin özelliğine **adı** sütun. Örneğin, "MyNewService görünen ad" girebilirsiniz. Bu ad farklı olabilir <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> sistem tarafından kullanılan ad özelliği (örneğin, kullandığınızda `net start` hizmetinizi başlatmak için komut).  
  
8.  Ayarlama <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğine <xref:System.ServiceProcess.ServiceStartMode.Automatic>.  
  
     ![Bir Windows hizmeti için yükleyici özelliklerini](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")  
  
9. Tasarımcıda seçin **ServiceProcessInstaller1** bir Visual C# projesi için veya **ServiceProcessInstaller1** Visual Basic projesinde için. Ayarlama <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> özelliğine <xref:System.ServiceProcess.ServiceAccount.LocalSystem>. Bu, hizmetin yerel hizmet hesabına yüklenmesi ve çalıştırılmasını sağlayacaktır.  
  
    > [!IMPORTANT]
    >  <xref:System.ServiceProcess.ServiceAccount.LocalSystem> Hesabının olay günlüğüne yazma yeteneği dahil olmak üzere geniş izinlere sahip. Bu hesabı kullanırken dikkatli olun; kötü amaçlı yazılımlardan gelecek saldırı riskinizi arttırabilir. Diğer görevler için kullanmayı <xref:System.ServiceProcess.ServiceAccount.LocalService> yerel bilgisayardaki bir ayrıcalıklı olmayan kullanıcı görevi görür ve herhangi bir uzak sunucuya anonim kimlik bilgileri gösterir, hesap. Bu örnek kullanmaya çalışırsa, başarısız <xref:System.ServiceProcess.ServiceAccount.LocalService> , olay günlüğüne yazma izni gerektiği için hesap.  
  
     Yükleyiciler hakkında daha fazla bilgi için bkz: [nasıl yapılır: Hizmet uygulamanız için yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
<a name="BK_StartupParameters"></a>   
## <a name="set-startup-parameters"></a>Başlangıç parametreleri ayarlama  
 Başka bir yürütülebilir dosyayı gibi bir Windows hizmeti, komut satırı bağımsız değişkenleri veya başlangıç parametreleri kabul edebilir. İşlem Başlangıç parametreleri için kod eklediğinizde, kullanıcılar Windows Denetim Masası'ndaki Hizmetler penceresini kullanarak kendi özel başlangıç parametreleri ile hizmetinizi başlatabilirsiniz. Ancak, bu başlangıç parametreleri hizmet bir sonraki başlatılışında kalıcı değildir. Başlangıç parametreleri kalıcı olarak ayarlamak için bunları kayıt defterinde, bu yordamda gösterildiği şekilde ayarlayabilirsiniz.  
  
> [!NOTE]
>  Başlangıç parametreleri eklemek karar vermeden önce bilgi hizmetinize geçirmek için en iyi yolu olup olmadığını göz önünde bulundurun. Başlangıç parametreleri kullanımı kolay olmasına rağmen ve için ayrıştırma ve kullanıcıların kolayca bunları kılabilirsiniz, bulmak ve belgeleri kullanmak kullanıcılar için daha zor olabilir. Genellikle, hizmetiniz birden fazla birkaç başlangıç parametreleri gerektiriyorsa, kayıt defteri veya bir yapılandırma dosyası kullanmayı düşünmelisiniz. Her Windows hizmeti kayıt defterinde HKLM\System\CurrentControlSet\services altında olan bir giriş var. Hizmetin anahtarında kullandığınız **parametreleri** hizmetinize erişmek bilgileri depolamak için alt anahtar. Uygulama yapılandırma dosyaları bir Windows hizmeti için diğer programları türler için yaptığınız şekilde kullanabilirsiniz. Örnek kod, bkz: <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.  
  
#### <a name="adding-startup-parameters"></a>Başlangıç parametreleri ekleme  
  
1.  İçinde `Main` yöntemi Program.cs veya MyNewService.Designer.vb, bir komut satırı bağımsız değişkeni ekleyin:  
  
```csharp  
static void Main(string[] args)
{
    ServiceBase[] ServicesToRun = new ServiceBase[] { new MyNewService(args) };
    ServiceBase.Run(ServicesToRun);
}
```  
  
```vb
Shared Sub Main(ByVal cmdArgs() As String)
    Dim ServicesToRun() As System.ServiceProcess.ServiceBase = New System.ServiceProcess.ServiceBase() {New MyNewServiceVB(cmdArgs)}
    System.ServiceProcess.ServiceBase.Run(ServicesToRun)
End Sub
```  
  
2.  Değişiklik `MyNewService` şekilde Oluşturucusu:  
  
```csharp  
public MyNewService(string[] args)
{
    InitializeComponent();
    string eventSourceName = "MySource";
    string logName = "MyNewLog";
    if (args.Count() > 0) 
    {
        eventSourceName = args[0];
    }
    if (args.Count() > 1)
    {
        logName = args[1];
    }
    eventLog1 = new System.Diagnostics.EventLog();
    if (!System.Diagnostics.EventLog.SourceExists(eventSourceName))
    {
        System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName);
    }
    eventLog1.Source = eventSourceName;
    eventLog1.Log = logName;        
}
```  
  
```vb  
Public Sub New(ByVal cmdArgs() As String)
    InitializeComponent()
    Dim eventSourceName As String = "MySource"
    Dim logName As String = "MyNewLog"
    If (cmdArgs.Count() > 0) Then
        eventSourceName = cmdArgs(0)
    End If
    If (cmdArgs.Count() > 1) Then
        logName = cmdArgs(1)
    End If
    eventLog1 = New System.Diagnostics.EventLog()
    If (Not System.Diagnostics.EventLog.SourceExists(eventSourceName)) Then
        System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName)
    End If
    eventLog1.Source = eventSourceName
    eventLog1.Log = logName
End Sub  
```  
  
Bu kodu sağlanan başlangıç parametreleri göre olay kaynağı ve günlük adını ayarlar ya da bağımsız değişkenler sağlandıysa varsayılan değerleri kullanır.  
  
3. Komut satırı bağımsız değişkenlerini belirtmek için aşağıdaki kodu ekleyin `ProjectInstaller` ProjectInstaller.cs veya ProjectInstaller.vb sınıfında:  
  
```csharp  
protected override void OnBeforeInstall(IDictionary savedState)
{
    string parameter = "MySource1\" \"MyLogFile1";
    Context.Parameters["assemblypath"] = "\"" + Context.Parameters["assemblypath"] + "\" \"" + parameter + "\"";
    base.OnBeforeInstall(savedState);
}
```

```vb  
Protected Overrides Sub OnBeforeInstall(ByVal savedState As IDictionary)
    Dim parameter As String = "MySource1"" ""MyLogFile1"
    Context.Parameters("assemblypath") = """" + Context.Parameters("assemblypath") + """ """ + parameter + """"
    MyBase.OnBeforeInstall(savedState)
End Sub  
```  
  
Bu kod değiştirir **ImagePath** varsayılan parametre değerleri ekleyerek Windows hizmeti için genelde yürütülebilir dosyanın tam yolunu içeren bir kayıt defteri anahtarı. Tırnak işaretleri yolun geçici (ve tek tek her parametre çevresinde) hizmetinin doğru şekilde başlatmak için gereklidir. Bu Windows hizmeti için başlangıç parametreleri değiştirmek için kullanıcılar verilen parametrelerini değiştirebilirsiniz **ImagePath** kayıt defteri anahtarı, programlı olarak değiştirin ve kullanıcılara işlevselliği kullanıma sunmak için daha iyi şekilde olmasına rağmen bir kolay şekilde (örneğin, bir yönetim veya yapılandırma yardımcı programı).  
  
<a name="BK_Build"></a>   
## <a name="building-the-service"></a>Hizmet oluşturma  
  
#### <a name="to-build-your-service-project"></a>Hizmet projenizi yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**projeniz için bağlam menüsünü açın ve ardından **özellikleri**. Özellik sayfaları projeniz için görünür.  
  
2.  Uygulama sekmesinde de **Başlangıç nesnesi** listesinde, seçin **MyNewService.Program**.  
  
3.  İçinde **Çözüm Gezgini**projeniz için bağlam menüsünü açın ve ardından **yapı** Projeyi derlemek için (klavye: Ctrl + Shift + B).  
  
<a name="BK_Install"></a>   
## <a name="installing-the-service"></a>Hizmetini yükleme  
 Windows hizmeti oluşturduğunuza göre yükleyebilirsiniz. Bir Windows hizmeti yüklemek için üzerinde yüklemekte bilgisayarda yönetici kimlik bilgileri olmalıdır.  
  
#### <a name="to-install-a-windows-service"></a>Bir Windows hizmetini yüklemek için  
  
1.  Windows 7 ve Windows Server ' açık **Geliştirici komut istemi** altında **Visual Studio Araçları** içinde **Başlat** menüsü. Windows 8 veya Windows 8.1 belirleyin **Visual Studio Araçları** döşemesinin **Başlat** ekran ve geliştirici komut istemini yönetici kimlik bilgileriyle çalıştırın. (Fare kullanıyorsanız, sağ tıklayın **Geliştirici komut istemi**ve ardından **yönetici olarak çalıştır**.)  
  
2.  Komut İstemi penceresinde projenizin çıktısını içeren klasöre gidin. Örneğin, Belgelerim klasörünüzün altında Visual Studio 2013\Projects\MyNewService\bin\Debug yoluna gidin.  
  
3.  Aşağıdaki komutu girin:  
  
    ```  
    installutil.exe MyNewService.exe  
    ```  
  
     Hizmet başarılı bir şekilde yüklenirse, installutil.exe durumu başarılı olarak bildirir. Sistem InstallUtil.exe bulamadı, bilgisayarınızda yüklü olduğundan emin olun. Bu aracı, klasöre .NET Framework ile kurulmuş `%WINDIR%\Microsoft.NET\Framework[64]\` *framework_version*. Örneğin, .NET Framework 4, 4.5, 4.5.1 ve 4.5.2 32-bit sürümü için varsayılan yolu olan `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.  
  
     İnstallutil.exe işlem hatası bildirirse, nedenini bulmak için yükleme günlüğüne bakın. Varsayılan olarak günlük hizmeti yürütülebilir dosyası ile aynı klasörde şeklindedir. Yükleme başarısız <xref:System.ComponentModel.RunInstallerAttribute> sınıfı mevcut değil `ProjectInstaller` sınıfı, aksi takdirde özniteliği ayarlanmamış `true`, aksi takdirde `ProjectInstaller` sınıfı değil `public`.  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
<a name="BK_StartService"></a>   
## <a name="starting-and-running-the-service"></a>Başlangıç ve hizmet çalışıyor  
  
#### <a name="to-start-and-stop-your-service"></a>Hizmetinizi başlatmak ve durdurmak için  
  
1.  Windows'da açmak **Başlat** ekran veya **Başlat** menü ve türü `services.msc`.  
  
     Artık görmelisiniz **MyNewService** listelenen **Hizmetleri** penceresi.  
  
     ![MyNewService Hizmetleri penceresinde. ] (../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG "WindowsServices_ServicesWindow")  
  
2.  İçinde **Hizmetleri** penceresinde, hizmetiniz için kısayol menüsünü açın ve ardından **Başlat**.  
  
3.  Hizmet için kısayol menüsünü açın ve ardından **durdurmak**.  
  
4.  (İsteğe bağlı) Komut satırından komutları kullanabilirsiniz `net start``ServiceName` ve `net stop``ServiceName` hizmetinizi durdurup başlatın.  
  
#### <a name="to-verify-the-event-log-output-of-your-service"></a>Hizmetinizin olay günlüğü çıktısını doğrulamak için  
  
1.  Visual Studio'da açın **Sunucu Gezgini** (klavye: Ctrl + Alt + S) ve erişim **olay günlüklerini** yerel bilgisayar düğümü.  
  
2.  Listesine bulun **MyNewLog** (veya **MyLogFile1**, komut satırı bağımsız değişkenleri eklemek için isteğe bağlı yordamı kullandıysanız) genişletin. Girdiler görmeniz gerekir (başlatma ve durdurma) iki işlemleri hizmetinizin gerçekleştirdiği.  
  
     ![Olay günlüğü girişleri görmek için Olay Görüntüleyicisi'ni kullanın. ] (../../../docs/framework/windows-services/media/windowsservices-eventviewer.PNG "WindowsServices_EventViewer")  
  
<a name="BK_Uninstall"></a>   
## <a name="uninstalling-a-windows-service"></a>Bir Windows hizmetini kaldırma  
  
#### <a name="to-uninstall-your-service"></a>Hizmetinizi kaldırmak için  
  
1.  Yönetici kimlik bilgileriyle bir geliştirici komut istemi açın.  
  
2.  Komut İstemi penceresinde projenizin çıktısını içeren klasöre gidin. Örneğin, Belgelerim klasörünüzün altında Visual Studio 2013\Projects\MyNewService\bin\Debug yoluna gidin.  
  
3.  Aşağıdaki komutu girin:  
  
    ```  
    installutil.exe /u MyNewService.exe  
    ```  
  
     Hizmet başarıyla kaldırırsa, installutil.exe hizmetinizin başarıyla kaldırıldığını size bildirir. Daha fazla bilgi için bkz: [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Diğerleri Windows hizmeti yüklemek için kullanabileceğiniz bir tek başına Kurulum programı oluşturabilirsiniz, ancak ek adımlar gerektirir. ClickOnce Windows hizmetlerini desteklemediğinden, Yayımlama Sihirbazı'nı kullanamazsınız. Microsoft'u sağlamadığı InstallShield'ın tam sürümünü kullanabilirsiniz. InstallShield hakkında daha fazla bilgi için bkz: [InstallShield Limited Edition](/visualstudio/deployment/installshield-limited-edition). Aynı zamanda [Windows Installer XML araç takımı](http://go.microsoft.com/fwlink/?LinkId=249067) bir Windows hizmeti için bir yükleyici oluşturmak üzere.  
  
 Kullanımını keşfedebilirsiniz bir <xref:System.ServiceProcess.ServiceController> bileşeni yüklü olan hizmet komutlar göndermenizi sağlar.  
  
 Uygulama çalıştığında bir olay günlüğü oluşturmak yerine, uygulama yüklenirken bir olay günlüğü oluşturmak için bir yükleyici kullanabilirsiniz. Ayrıca, uygulama kaldırıldığında olay günlüğü de yükleyici tarafından silinecektir. Daha fazla bilgi için bkz: <xref:System.Diagnostics.EventLogInstaller> başvuru sayfası.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamaları](../../../docs/framework/windows-services/index.md)  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Hizmetleri (Windows)](http://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)
