---
title: Visual Studio'da bir Windows hizmeti uygulaması oluşturma
ms.date: 09/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
manager: douge
ms.openlocfilehash: 27acdac5d34b96dd04fec1bb763edec9077ff928
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708724"
---
# <a name="walkthrough-create-a-windows-service-app"></a>İzlenecek yol: bir Windows hizmeti uygulaması oluşturma

Bu makalede, Visual Studio'da bir olay günlüğüne iletiler yazan basit bir Windows hizmeti uygulaması oluşturma işlemini gösterir.

## <a name="create-a-service"></a>Bir hizmet oluşturma

Başlamak için projeyi oluşturmak ve hizmetin düzgün çalışması için gerekli olan değerleri ayarlayın.

1. Visual Studio'da menü çubuğunda, **dosya** > **yeni** > **proje** (veya basın **Ctrl** + **Shift**+**N**) açmak için **yeni proje** iletişim.

2. Bulun ve seçin **Windows hizmeti** proje şablonu. Genişletin **yüklü** > [**Visual C#** veya **Visual Basic**] > **Windows Masaüstü**, veya tür **Windowshizmeti** sağ üst köşedeki arama kutusuna.

   ![Visual Studio'da yeni proje iletişim kutusunda Windows hizmet şablonu](media/new-project-dialog.png)

   > [!NOTE]
   > Görmüyorsanız **Windows hizmeti** şablon yüklemeniz gerekebilir **.NET Masaüstü geliştirmesinden** iş yükü. İçinde **yeni proje** iletişim kutusunda bağlantısına tıklayın **açık Visual Studio yükleyicisi** sol alt. İçinde **Visual Studio yükleyicisi**seçin **.NET masaüstü geliştirme** iş yükü ve ardından **Değiştir**.

3. Projeyi adlandırın **MyNewService**ve ardından **Tamam**.

   Proje şablonu adında bir bileşen sınıfını içeren `Service1` öğesinden devralan <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>. Hizmeti başlatmak için kodu gibi temel hizmet kodunun çoğunu içerir.

## <a name="rename-the-service"></a>Hizmet yeniden adlandır

Hizmet Yeniden Adlandır **Service1** için **MyNewService**.

1. İçinde **tasarım** Service1.cs (veya gt;service1.vb) görünümüne tıklayın bağlantısını **kod görünümüne geçin**. Sağ **Service1** seçip **Yeniden Adlandır** bağlam menüsünden. ENTER **MyNewService** ve tuşuna **Enter** veya **Uygula**.

2. İçinde **özellikleri** penceresi **Service1.cs [Design]** veya **gt;service1.vb [Design]**, değiştirme **ServiceName** değerine**MyNewService**.

3. İçinde **Çözüm Gezgini**, yeniden adlandırma **Service1.cs** için **MyNewService.cs**, veya yeniden adlandırmak **Service1.vb** için  **MyNewService.vb**.

## <a name="add-features-to-the-service"></a>Hizmete özellik ekleme

Bu bölümde, Windows hizmeti için özel bir olay günlüğü ekleyin. Olay günlükleri, Windows hizmetleri ile hiçbir şekilde ilişkili değildir. <xref:System.Diagnostics.EventLog> Bileşen kullanılan bir Windows hizmetine ekleyebileceğiniz bileşen türüne bir örnek burada.

### <a name="add-custom-event-log-functionality"></a>Özel olay günlüğü işlevselliği ekleme

1. İçinde **Çözüm Gezgini**, bağlam menüsünü **MyNewService.cs** veya **MyNewService.vb**ve ardından **Görünüm Tasarımcısı**.

2. Gelen **bileşenleri** bölümünü **araç kutusu**, sürükleyin bir <xref:System.Diagnostics.EventLog> tasarımcıya bileşeni.

3. İçinde **Çözüm Gezgini**, bağlam menüsünü **MyNewService.cs** veya **MyNewService.vb**ve ardından **Kodu Görüntüle**.

4. Özel bir olay günlüğü tanımlamak için oluşturucuyu Düzenle:

   ```csharp
   public MyNewService()
   {
        InitializeComponent();

        eventLog1 = new System.Diagnostics.EventLog();
        if (!System.Diagnostics.EventLog.SourceExists("MySource"))
        {
            System.Diagnostics.EventLog.CreateEventSource(
                "MySource", "MyNewLog");
        }
        eventLog1.Source = "MySource";
        eventLog1.Log = "MyNewLog";
    }
   ```

   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

### <a name="define-what-occurs-when-the-service-starts"></a>Hizmet başlatıldığında ne olacağını tanımlayın

Kod Düzenleyicisi'nde bulun <xref:System.ServiceProcess.ServiceBase.OnStart%2A> projeyi oluşturduğunuzda otomatik olarak geçersiz kılınan yöntemi. Hizmet başlatıldığında, bir giriş olay günlüğüne yazan kod satırını ekleyin:

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

Bir hizmet uygulaması, uzun süre çalışan, genellikle yoklar veya sistemde izleyen bir şey olacak şekilde tasarlanmıştır. İzleme ayarlanır <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi. Ancak, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> aslında izleme yapmaz. <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Yöntemi hizmetin çalışması başladıktan sonra işletim sistemine döndürmesi gerekir. Sonsuza kadar döngü veya engelleme gerçekleştirmemelidir. Basit bir yoklama mekanizması kurmak için kullanabileceğiniz <xref:System.Timers.Timer?displayProperty=nameWithType> aşağıdaki gibi bileşeni: içinde <xref:System.ServiceProcess.ServiceBase.OnStart%2A> bileşen üzerinde parametreleri ayarlayın ve ardından yöntemi <xref:System.Timers.Timer.Enabled%2A> özelliğini `true`. Zamanlayıcı, aynı zamanda hizmetiniz izlemeyi yapabileceği kodunuzda olayları periyodik olarak başlatır. Bunu yapmak için aşağıdaki kodu kullanabilirsiniz:

```csharp
// Set up a timer that triggers every minute.
System.Timers.Timer timer = new System.Timers.Timer();
timer.Interval = 60000; // 60 seconds
timer.Elapsed += new System.Timers.ElapsedEventHandler(this.OnTimer);
timer.Start();
```

```vb
' Set up a timer that triggers every minute.
Dim timer As System.Timers.Timer = New System.Timers.Timer()
timer.Interval = 60000 ' 60 seconds
AddHandler timer.Elapsed, AddressOf Me.OnTimer
timer.Start()
```

Üye değişkeni sınıfına ekleyin. Bu, olay günlüğüne yazmak için sonraki olayı tanımlayıcısını içerir.

```csharp
private int eventId = 1;
```

```vb
Private eventId As Integer = 1
```

Zamanlayıcı olayı işlemek için yeni bir yöntem ekleyin:

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

Tüm iş ana iş parçacığında çalıştırmak yerine arka plan çalışan iş parçacıkları kullanarak görevleri gerçekleştirmek isteyebilirsiniz. Daha fazla bilgi için bkz. <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.

### <a name="define-what-occurs-when-the-service-is-stopped"></a>Hizmet durdurulduğunda ne olacağını tanımlayın

Bir kod satırını ekleyin <xref:System.ServiceProcess.ServiceBase.OnStop%2A> hizmet durdurulduğunda, olay günlüğüne bir giriş ekler yöntemi:

```csharp
eventLog1.WriteEntry("In OnStop.");
```

[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a>Diğer Eylemler için hizmet tanımlama

Geçersiz kılabilirsiniz <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, ve <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> bileşeniniz için ek işlemler tanımlamak için yöntemleri. Aşağıdaki kod nasıl geçersiz gösterir <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> yöntemi:

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

Bazı özel eylemler ile bir Windows hizmeti yüklendiğinde ortaya zorunda <xref:System.Configuration.Install.Installer> sınıfı. Visual Studio, bu yükleyicileri bir Windows hizmeti için özel olarak oluşturabilir ve sonra da projenize ekleyebilir.

## <a name="set-service-status"></a>Hizmet durumunu ayarla

Böylece kullanıcılar bir hizmet doğru şekilde çalışıp çalışmadığını söyleyebilirsiniz Hizmetleri durumlarını hizmet denetimi yöneticisine bildirir. Varsayılan olarak, devralınan Hizmetleri <xref:System.ServiceProcess.ServiceBase> rapor durdurulmuş, duraklatılmış ve çalıştıran sınırlı sayıda dahil olmak üzere durumu ayarları. Bunun başlatmak için bir başlangıç bekleme durumu raporlamak faydalı olabilir ancak bir hizmet biraz uzun sürerse. Windows çağıran kod ekleyerek de bekleyen başlatmak ve durdurmak bekleyen durum ayarlarını uygulayabilirsiniz [artırılmış işlevi](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).

Hizmet Durumu Beklemede uygulamak için:

1. Ekleme bir `using` deyimi veya `Imports` bildirimi <xref:System.Runtime.InteropServices?displayProperty=nameWithType> MyNewService.cs veya MyNewService.vb dosyasında ad alanı:

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. Bildirmek için MyNewService.cs için aşağıdaki kodu ekleyin `ServiceState` değerleri ve platform kullanacağınız durum için bir yapı eklemek için çağrı çağırın:

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

3. Şimdi, `MyNewService` sınıfı, bildirmek [artırılmış işlevi](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) kullanarak [platform çağırma](../interop/consuming-unmanaged-dll-functions.md):

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. Başlangıç bekleme durumu uygulamak için aşağıdaki kodu ekleyin başlangıcına <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi:

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

5. Sonunda çalışan durum için kod ekleyin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi.

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

6. (İsteğe bağlı) İçin bu yordamı yineleyin <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemi.

> [!NOTE]
> [Hizmet Denetimi Yöneticisi](/windows/desktop/Services/service-control-manager) kullanan `dwWaitHint` ve `dwCheckpoint` üyeleri [SERVICE_STATUS yapısı](/windows/desktop/api/winsvc/ns-winsvc-_service_status) bir Windows hizmeti başlatmak veya kapatmak beklenecek ne kadar süre belirlemek için. Varsa, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemleri çalıştırmak uzun, hizmetinizin daha fazla zaman çağırarak isteyebilir [artırılmış](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) yeniden ile bir artımlı `dwCheckPoint` değeri.

## <a name="add-installers-to-the-service"></a>Hizmete yükleyiciler ekleme

Bir Windows hizmeti çalıştırmadan önce Hizmet Denetimi Yöneticisi ile kaydeden yüklemeniz gerekir. Kayıt ayrıntıları işleyen projenize yükleyicileri ekleyebilirsiniz.

1. İçinde **Çözüm Gezgini**, bağlam menüsünü **MyNewService.cs** veya **MyNewService.vb**ve ardından **Görünüm Tasarımcısı**.

2. Hizmetin herhangi bir içeriğini değil de, hizmetin kendisini seçmek için tasarımcının arka planına tıklayın.

3. Tasarımcı penceresini (bir işaretleme penceresi içine sağ kullanıyorsanız) için bağlam menüsünü açın ve ardından **Yükleyici Ekle**.

   Varsayılan olarak, projenize iki yükleyici içeren bir bileşen sınıfı eklenir. Bileşene **ProjectInstaller**ve içerdiği yükleyiciler hizmetinize yükleyici ve yükleyici hizmeti için işlem ilişkili.

4. İçinde **tasarım** görüntüleme **ProjectInstaller**, seçin **Serviceınstaller1** Visual C# proje için veya **Serviceınstaller1** bir görsel için Temel Proje.

5. İçinde **özellikleri** penceresinde emin <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliği **MyNewService**.

6. Ayarlama **açıklama** özelliğini "Örnek hizmeti" gibi şeyler. Bu metin hizmetleri penceresinde görüntülenmesi ve kullanıcının hizmetinizi tanımlamak ve ne için kullanıldığını anlamanıza yardımcı olur.

7. Ayarlama <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> Hizmetleri penceresinde görünmesini istediğiniz metni özelliğini **adı** sütun. Örneğin, "MyNewService görünen ad" girebilirsiniz. Bu ad farklı olabilir <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> sistem tarafından kullanılan ad özelliği (örneğin, kullandığınızda `net start` hizmetinizi başlatmak için komut).

8. Ayarlama <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğini <xref:System.ServiceProcess.ServiceStartMode.Automatic>.

     ![Bir Windows hizmeti için yükleyici özelliklerini](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")

9. Tasarımcısı'nda **ServiceProcessInstaller1** Visual C# proje için veya **ServiceProcessInstaller1** Visual Basic projesi için. Ayarlama <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> özelliğini <xref:System.ServiceProcess.ServiceAccount.LocalSystem>. Bu hizmet yüklü olmasını ve yerel sistem hesabı kullanarak çalıştırılacak neden olur.

    > [!IMPORTANT]
    > <xref:System.ServiceProcess.ServiceAccount.LocalSystem> Hesabının olay günlüğüne yazma olanağı dahil olmak üzere geniş izinlere sahip. Bu hesabı kullanırken dikkatli olun; kötü amaçlı yazılımlardan gelecek saldırı riskinizi arttırabilir. Diğer görevler için kullanmayı <xref:System.ServiceProcess.ServiceAccount.LocalService> hesabı yerel bilgisayarda ayrıcalıklı olmayan kullanıcı olarak davranan ve herhangi bir uzak sunucuya anonim kimlik bilgilerini sunar. Bu örnek kullanmaya çalışırsanız başarısız <xref:System.ServiceProcess.ServiceAccount.LocalService> olay günlüğüne yazma izni gerektiğinden, hesap.

Yükleyiciler hakkında daha fazla bilgi için bkz. [nasıl yapılır: ekleme yükleyiciler hizmetinize uygulama](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).

## <a name="optional-set-startup-parameters"></a>(İsteğe bağlı) Başlangıç parametrelerini ayarlayın

Diğer herhangi bir yürütülebilir gibi bir Windows hizmeti, komut satırı bağımsız değişkenleri veya başlangıç parametreleri kabul edebilir. İşlem Başlangıç parametrelerine kod eklediğinizde, kullanıcılar Windows Denetim Masası'ndaki Hizmetler penceresini kullanarak kendi özel başlatma parametrelerle hizmetinizi başlatabilirsiniz. Ancak, bu başlangıç parametreleri hizmet bir sonraki başlatılışında kalıcı değildir. Başlangıç parametreleri kalıcı olarak ayarlamak için bunları kayıt defterinde, bu yordamda gösterildiği gibi ayarlayabilirsiniz.

> [!NOTE]
> Başlangıç parametreleri eklemek karar vermeden önce hizmetinize bilgi geçirmek için en iyi yolu olup olmadığını göz önünde bulundurun. Başlangıç parametreleri kullanımı kolay olsa ve için ayrıştırma ve kullanıcıların kolayca bunları geçersiz kılabilirsiniz, kullanıcıların keşfetmesi ve kullanması belgeleri daha zor olabilir. Genel olarak, hizmetiniz birkaç taneden fazla yalnızca başlangıç parametre gerektiriyorsa, kayıt defteri veya bir yapılandırma dosyası kullanmayı düşünmelisiniz. Her bir Windows hizmetinde altında kayıt defterinde girişi olmayan **HKLM\System\CurrentControlSet\services**. Hizmet anahtarı altında kullanabileceğiniz **parametreleri** hizmetinizi erişebileceği bilgileri depolamak için alt. Uygulama yapılandırma dosyaları programlar diğer türleri için yaptığınız şekilde bir Windows hizmeti için kullanabilirsiniz. Örnek kod için bkz: <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.

Başlangıç parametreleri eklemek için:

1. İçinde `Main` yöntemi Program.cs veya MyNewService.Designer.vb, hizmet oluşturucuya geçirilecek giriş parametresi ekleyin:

   ```csharp
   static void Main(string[] args)
   {
       ServiceBase[] ServicesToRun;
       ServicesToRun = new ServiceBase[]
       {
           new MyNewService(args)
       };
       ServiceBase.Run(ServicesToRun);
   }
   ```

   ```vb
   Shared Sub Main(ByVal cmdArgs() As String)
       Dim ServicesToRun() As System.ServiceProcess.ServiceBase = New System.ServiceProcess.ServiceBase() {New MyNewServiceVB(cmdArgs)}
       System.ServiceProcess.ServiceBase.Run(ServicesToRun)
   End Sub
   ```

2. Değişiklik `MyNewService` Oluşturucu aşağıdaki gibi:

   ```csharp
   public MyNewService(string[] args)
   {
       InitializeComponent();

        string eventSourceName = "MySource";
        string logName = "MyNewLog";

        if (args.Length > 0)
        {
            eventSourceName = args[0];
        }

        if (args.Length > 1)
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

   Bu kod, sağlanan başlangıç parametreleri göre olay kaynağı ve günlük adını ayarlar veya herhangi bir bağımsız değişken sağlanmadıysa varsayılan değerleri kullanır.

3. Komut satırı bağımsız değişkenlerini belirtmek için aşağıdaki kodu ekleyin. `ProjectInstaller` ProjectInstaller.cs veya ProjectInstaller.vb sınıfı:

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

   Bu kodu değiştirir **ImagePath** genellikle varsayılan parametre değerlerini ekleyerek Windows hizmeti için yürütülebilir dosyanın tam yolunu içeren kayıt defteri anahtarı. Yolun (ve tek tek her parametreyi) tırnak işareti, hizmetin doğru şekilde başlatmak için gereklidir. Bu Windows hizmeti için başlangıç parametreleri değiştirmek için kullanıcıların belirtilen parametrelerle değiştirip **ImagePath** kayıt defteri anahtarı, program aracılığıyla değiştirme ve kullanıcılara işlevselliği göstermek için daha iyi şekilde olmasına rağmen bir kolay bir yolla (örneğin, bir yönetim veya yapılandırma yardımcı programını kullanarak).

## <a name="build-the-service"></a>Derleme hizmeti

1. İçinde **Çözüm Gezgini**, projeniz için bağlam menüsünü açın ve ardından **özellikleri**.

   Projeniz için özellik sayfaları görünür.

2. Üzerinde **uygulama** sekmesinde **Başlangıç nesnesi** listesinde **MyNewService.Program**.

3. İçinde **Çözüm Gezgini**, projeniz için bağlam menüsünü açın ve ardından **derleme** Projeyi derlemek için (veya basın **Ctrl**+**kaydırma**  + **B**).

## <a name="install-the-service"></a>Hizmet yükleme

Windows hizmeti oluşturduğunuza göre bunu yükleyebilirsiniz. Bir Windows hizmetini yüklemek için yükleme yaptığınız bilgisayarda yönetici kimlik bilgileri olmalıdır.

1. Açık **Visual Studio için geliştirici komut istemi** yönetici kimlik bilgilerine sahip. Fare kullanıyorsanız, sağ **VS 2017 için geliştirici komut istemi** içinde Windows Başlat menüsünü ve ardından **daha fazla** > **yönetici olarak çalıştır** .

2. İçinde **Geliştirici komut istemi** penceresinde projenizin çıktısını içeren klasöre gidin (varsayılan olarak, bu *\bin\Debug* projenizin alt).

3. Aşağıdaki komutu girin:

    ```shell
    installutil.exe MyNewService.exe
    ```

    Hizmet başarıyla yüklerse **installutil.exe** başarılı olduğunu bildirir. Sistem bulunamadı, **InstallUtil.exe**, bilgisayarınızda mevcut olduğundan emin olun. Bu araç, .NET Framework klasörüne yüklenir *% windir%\Microsoft.NET\Framework[64]\\[framework sürümü]*. Örneğin, 32-bit sürüm için varsayılan yolu olan *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.

    Varsa **installutil.exe** işlem hata raporları, nedenini bulmak için yükleme günlüğüne bakın. Varsayılan olarak günlük hizmeti yürütülebilir dosyası ile aynı klasörde bulunur. Yükleme başarısız olabilir <xref:System.ComponentModel.RunInstallerAttribute> sınıfı üzerinde mevcut değil `ProjectInstaller` öznitelik olarak ayarlanmazsa, sınıf **true**, veya `ProjectInstaller` sınıfı işaretlenmemiş **genel**.

Daha fazla bilgi için [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).

## <a name="start-and-run-the-service"></a>Başlat ve Çalıştır hizmeti

1. Windows içinde açın **Hizmetleri** masaüstü uygulaması. Basın **Windows**+**R** açmak için **çalıştırma** kutusuna ve ardından girin **services.msc** basın **Enter**  veya **Tamam**.

     Hizmetiniz listede görürsünüz **Hizmetleri**alfabetik olarak ayarladığınız için görünen ada göre gösterilir.

     ![MyNewService Hizmetleri penceresinde.](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG)

2. İçinde **Hizmetleri**, hizmetiniz için kısayol menüsünü açın ve ardından **Başlat**.

3. Hizmeti durdurmak için hizmet için kısayol menüsünü açın ve ardından **Durdur**.

4. (İsteğe bağlı) Komut satırından komutları kullanabilirsiniz `net start ServiceName` ve `net stop ServiceName` hizmetinizi durdurmak ve başlatmak.

### <a name="verify-the-event-log-output-of-your-service"></a>Hizmetinizin olay günlüğü çıktısını doğrulamak

1. Açık **Olay Görüntüleyicisi'ni** türüne başlatarak **Olay Görüntüleyicisi'ni** Windows görev çubuğunda ve sonra arama kutusuna **Olay Görüntüleyicisi'ni** Arama sonuçlarından.

   > [!TIP]
   > Visual Studio'da açıp olay günlüklerini erişebilirsiniz **Sunucu Gezgini** (klavye: **Ctrl**+**Alt**+**S**) ve genişletme **olay günlüklerini** düğüm yerel bilgisayar.

2. İçinde **Olay Görüntüleyicisi'ni**, genişletme **uygulama ve hizmet günlükleri**.

3. Bulun **MyNewLog** (veya **MyLogFile1**, komut satırı bağımsız değişkenleri eklemek için isteğe bağlı yordamı izlediyseniz) genişletin. Hizmetinizi gerçekleştirilen iki eylem (başlatma ve durdurma) girişleri görmeniz gerekir.

     ![Olay günlüğü girişlerini görmek için Olay Görüntüleyicisi'ni kullanın](../../../docs/framework/windows-services/media/windows-service-event-viewer.png)

## <a name="uninstall-the-service"></a>Hizmeti Kaldır

1. Açık **Visual Studio için geliştirici komut istemi** yönetici kimlik bilgilerine sahip.

2. Komut İstemi penceresinde, projenizin çıktısını içeren klasöre gidin.

3. Aşağıdaki komutu girin:

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   Hizmet başarıyla kaldırırsa **installutil.exe** hizmetinizin başarıyla kaldırıldığını bildirir. Daha fazla bilgi için [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).

## <a name="next-steps"></a>Sonraki adımlar

Hizmet oluşturduğunuza göre diğerleri Windows hizmetinizi yüklemek için kullanabileceğiniz tek başına Kurulum programını oluşturmak isteyebilirsiniz. ClickOnce Windows hizmetlerini desteklemiyor, ancak kullanabileceğiniz [WiX Toolset](http://wixtoolset.org/) bir Windows hizmeti için bir yükleyici oluşturmak üzere. Diğer fikir edinmek için bkz: [Yükleyici paketi oluştur](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).

Kullanımını keşfedebilirsiniz bir <xref:System.ServiceProcess.ServiceController> bileşenin yüklediğiniz hizmete komutlar göndermenizi sağlar.

Uygulama çalıştığında bir olay günlüğü oluşturmak yerine, uygulama yüklenirken bir olay günlüğü oluşturmak için bir yükleyici kullanabilirsiniz. Ayrıca, uygulama kaldırıldığında olay günlüğü de yükleyici tarafından silinecektir. Daha fazla bilgi için <xref:System.Diagnostics.EventLogInstaller> başvuru sayfası.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows hizmet uygulamaları](../../../docs/framework/windows-services/index.md)
- [Windows hizmeti uygulamalarına giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [Hizmetleri (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)
