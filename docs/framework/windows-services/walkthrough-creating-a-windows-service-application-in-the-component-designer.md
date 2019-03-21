---
title: 'Öğretici: Bir Windows hizmeti uygulaması oluşturma'
ms.date: 03/14/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
ms.openlocfilehash: 786b9e28607cced0a15793415ff5fd470b559374
ms.sourcegitcommit: e994e47d3582bf09ae487ecbd53c0dac30aebaf7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58262494"
---
# <a name="tutorial-create-a-windows-service-app"></a>Öğretici: Bir Windows hizmeti uygulaması oluşturma

Bu makalede, olay günlüğüne bir ileti yazar Visual Studio'da bir Windows hizmeti uygulaması oluşturma gösterilmektedir.

## <a name="create-a-service"></a>Bir hizmet oluşturma

Başlamak için projeyi oluşturmak ve hizmetin düzgün çalışması için gerekli değerleri ayarlayın.

1. Visual Studio'dan **dosya** menüsünde **yeni** > **proje** (veya basın **Ctrl** + **Shift**+**N**) açmak için **yeni proje** penceresi.

2. Bulun ve seçin **Windows hizmeti (.NET Framework)** proje şablonu. Bunu bulmak için genişletme **yüklü** ve **Visual C#**  veya **Visual Basic**, ardından **Windows Masaüstü**. Veya, girin *Windows hizmeti* tuşuna basın ve sağ üst köşedeki arama kutusuna **Enter**.

   ![Visual Studio'da yeni proje iletişim kutusunda Windows hizmet şablonu](media/new-project-dialog.png)

   > [!NOTE]
   > Görmüyorsanız **Windows hizmeti** şablon yüklemeniz gerekebilir **.NET Masaüstü geliştirmesinden** iş yükü:
   >  
   > İçinde **yeni proje** iletişim kutusunda **açık Visual Studio yükleyicisi** sol alt. Seçin **.NET masaüstü geliştirme** iş yükü ve ardından **Değiştir**.

3. İçin **adı**, girin *MyNewService*ve ardından **Tamam**.

   **Tasarım** sekmesi görünür (**Service1.cs [Design]** veya **gt;service1.vb [Design]**).
   
   Proje şablonu adında bir bileşen sınıfını içeren `Service1` öğesinden devralan <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>. Hizmeti başlatmak için kodu gibi temel hizmet kodunun çoğunu içerir.

## <a name="rename-the-service"></a>Hizmet yeniden adlandır

Hizmet Yeniden Adlandır **Service1** için **MyNewService**.

1. İçinde **Çözüm Gezgini**seçin **Service1.cs**, veya **Service1.vb**ve **Yeniden Adlandır** kısayol menüsünden. Dosyayı Yeniden Adlandır **MyNewService.cs**, veya **MyNewService.vb**ve tuşuna **girin**

    Kod öğesi için tüm başvuruları yeniden adlandırmak istediğiniz soran bir açılır pencere görünür *Service1*.

2. Açılır pencerede seçin **Evet**.

    ![Yeniden adlandırma istemi](media/windows-service-rename.png "Windows hizmetini yeniden adlandırma, istemi")

2. İçinde **tasarım** sekmesinde **özellikleri** kısayol menüsünden. Gelen **özellikleri** penceresinde değişiklik **ServiceName** değerini *MyNewService*.

    ![Hizmet Özellikleri](media/windows-service-properties.png "Windows hizmet özellikleri")

3. Seçin **Tümünü Kaydet** gelen **dosya** menüsü.


## <a name="add-features-to-the-service"></a>Hizmete özellik ekleme

Bu bölümde, Windows hizmeti için özel bir olay günlüğü ekleyin. <xref:System.Diagnostics.EventLog> Bileşen bir Windows hizmetine ekleyebileceğiniz bileşen türüne bir örnek verilmiştir.

### <a name="add-custom-event-log-functionality"></a>Özel olay günlüğü işlevselliği ekleme

1. İçinde **Çözüm Gezgini**, kısayol menüsünden **MyNewService.cs**, veya **MyNewService.vb**, seçin **Görünüm Tasarımcısı**.

2. İçinde **araç kutusu**, genişletin **bileşenleri**ve ardından sürükleyin **EventLog** bileşeni **Service1.cs [Design]**, veya  **[Design] gt;service1.vb** sekmesi.

3. İçinde **Çözüm Gezgini**, kısayol menüsünden **MyNewService.cs**, veya **MyNewService.vb**, seçin **Kodu Görüntüle**.

4. Bir özel olay günlüğü'nü tanımlayın. İçin C#, var olan düzenleme `MyNewService()` Oluşturucusu; Visual Basic için ekleme `New()` Oluşturucusu:

   ```csharp
   public MyNewService()
   {
        InitializeComponent();

        eventLog1 = new EventLog();
        if (!EventLog.SourceExists("MySource"))
        {
            EventLog.CreateEventSource("MySource", "MyNewLog");
        }
        eventLog1.Source = "MySource";
        eventLog1.Log = "MyNewLog";
    }
   ```

   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. Ekleme bir `using` ifadesine **MyNewService.cs** (zaten mevcut değilse), veya bir `Imports` deyimi **MyNewService.vb**, için <xref:System.Diagnostics?displayProperty=nameWithType> ad alanı:

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. Seçin **Tümünü Kaydet** gelen **dosya** menüsü.

### <a name="define-what-occurs-when-the-service-starts"></a>Hizmet başlatıldığında ne olacağını tanımlayın

Kod düzenleyicisinde **MyNewService.cs** veya **MyNewService.vb**, bulun <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi Projeyi oluşturduğunuzda visual Studio, bir boş yöntem tanımını otomatik olarak oluşturulur. Hizmet başlatıldığında, bir giriş olay günlüğüne yazan kodu ekleyin:

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a>Yoklama

Bir hizmet uygulaması, uzun süre çalışan olacak şekilde tasarlandığından, genellikle yoklar veya izler, ayarlanan sistem <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi. `OnStart` Yöntemi, böylece sistem kilitli değilse hizmetin çalışması başladıktan sonra işletim sistemine döndürmelidir. 

Basit bir yoklama mekanizması kurmak için kullanın <xref:System.Timers.Timer?displayProperty=nameWithType> bileşeni. Süreölçer başlatır bir <xref:System.Timers.Timer.Elapsed> düzenli aralıklarla zaman hizmetinizi yapabilir, izleme olayı. Kullandığınız <xref:System.Timers.Timer> bileşeni aşağıdaki gibi:

- Özelliklerini ayarlama <xref:System.Timers.Timer> bileşeninin `MyNewService.OnStart` yöntemi.
- Çağırarak zamanlayıcıyı başlatmak <xref:System.Timers.Timer.Start%2A> yöntemi.

##### <a name="set-up-the-polling-mechanism"></a>Yoklama mekanizması kurmak ayarlayın.

1. Aşağıdaki kodu ekleyin `MyNewService.OnStart` yoklama mekanizması kurmak için olay:

   ```csharp
   // Set up a timer that triggers every minute.
   Timer timer = new Timer();
   timer.Interval = 60000; // 60 seconds
   timer.Elapsed += new ElapsedEventHandler(this.OnTimer);
   timer.Start();
   ```

   ```vb
   ' Set up a timer that triggers every minute.
   Dim timer As Timer = New Timer()
   timer.Interval = 60000 ' 60 seconds
   AddHandler timer.Elapsed, AddressOf Me.OnTimer
   timer.Start()
   ```

2. Ekleme bir `using` ifadesine **MyNewService.cs**, veya bir `Imports` ifadesine **MyNewService.vb**, için <xref:System.Timers?displayProperty=nameWithType> ad alanı:


   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```


3. İçinde `MyNewService` sınıfı, ekleme `OnTimer` işlemek için gereken yöntemini <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> olay:

   ```csharp
   public void OnTimer(object sender, ElapsedEventArgs args)
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

4. İçinde `MyNewService` sınıfı, bir üye değişkeni ekleyin. Olay günlüğüne yazmak için bir sonraki olay tanıtıcısı aşağıdakileri içerir:

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

Tüm iş ana iş parçacığında çalıştırmak yerine arka plan çalışan iş parçacıkları kullanarak görevler çalıştırabilirsiniz. Daha fazla bilgi için bkz. <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.

### <a name="define-what-occurs-when-the-service-is-stopped"></a>Hizmet durdurulduğunda ne olacağını tanımlayın

Bir kod satırı Ekle <xref:System.ServiceProcess.ServiceBase.OnStop%2A> hizmet durdurulduğunda, olay günlüğüne bir giriş ekler yöntemi:

```csharp
eventLog1.WriteEntry("In OnStop.");
```

[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a>Diğer Eylemler için hizmet tanımlama

Geçersiz kılabilirsiniz <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, ve <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> bileşeniniz için ek işlemler tanımlamak için yöntemleri. 

Aşağıdaki kodda gösterildiği nasıl geçersiz kılmanıza da olanak <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> yönteminde `MyNewService` sınıfı:

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]


## <a name="set-service-status"></a>Hizmet durumunu ayarla

Hizmetleri, kendi durumunu rapor [Hizmet Denetimi Yöneticisi](/windows/desktop/Services/service-control-manager) böylece bir kullanıcı bir hizmet doğru şekilde çalışıp çalışmadığını söyleyebilirsiniz. Varsayılan olarak, bir hizmet öğesinden devralan <xref:System.ServiceProcess.ServiceBase> SERVICE_STOPPED SERVICE_PAUSED ve SERVICE_RUNNING durumu ayarları, sınırlı sayıda raporlar. Bir hizmetin başlatılması biraz zaman alır, SERVICE_START_PENDING durumunu raporlamak kullanışlıdır. 

Windows çağıran kod ekleyerek SERVICE_START_PENDING ve SERVICE_STOP_PENDING durum ayarlarını uygulayabilirsiniz [artırılmış](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) işlevi.


### <a name="implement-service-pending-status"></a>Hizmet durumu bekleyen ekleme

1. Ekleme bir `using` ifadesine **MyNewService.cs**, veya bir `Imports` ifadesine **MyNewService.vb**, için <xref:System.Runtime.InteropServices?displayProperty=nameWithType> ad alanı:

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. Aşağıdaki kodu ekleyin **MyNewService.cs**, veya **MyNewService.vb**bildirmek için `ServiceState` değerleri ve platform kullanacağınız durum için bir yapı eklemek için çağrı çağırın:

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

3. İçinde `MyNewService` sınıfı, bildirmek [artırılmış](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) işlevi kullanarak [platform çağırma](../interop/consuming-unmanaged-dll-functions.md):

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. SERVICE_START_PENDING durum uygulamak için aşağıdaki kodu ekleyin başlangıcına <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi:

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

5. Kod sonuna ekleyin `OnStart` yöntemi SERVICE_RUNNING için durum ayarlanamadı:

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

6. (İsteğe bağlı) Varsa <xref:System.ServiceProcess.ServiceBase.OnStop%2A> bir uzun süre çalışan yöntemdir, bu yordamı yineleyin `OnStop` yöntemi. SERVICE_STOP_PENDING durumu uygulamak ve dönüş önce SERVICE_STOPPED durumu `OnStop` yöntemi çıkar.

   Örneğin:

    ```csharp
    // Update the service state to Stop Pending.
    ServiceStatus serviceStatus = new ServiceStatus();
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING;
    serviceStatus.dwWaitHint = 100000;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);

    // Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Stop Pending.
    Dim serviceStatus As ServiceStatus = New ServiceStatus()
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING
    serviceStatus.dwWaitHint = 100000
    SetServiceStatus(Me.ServiceHandle, serviceStatus)

    ' Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED
    SetServiceStatus(Me.ServiceHandle, serviceStatus)    
    ```

> [!NOTE]
> Hizmet Denetimi Yöneticisi kullanan `dwWaitHint` ve `dwCheckpoint` üyeleri [SERVICE_STATUS yapısı](/windows/desktop/api/winsvc/ns-winsvc-_service_status) bir Windows hizmeti başlatmak veya kapatmak beklenecek ne kadar süre belirlemek için. Varsa, `OnStart` ve `OnStop` yöntemleri çalıştırmak uzun, hizmetinizin daha fazla zaman çağırarak isteyebilir `SetServiceStatus` yeniden ile bir artımlı `dwCheckPoint` değeri.

## <a name="add-installers-to-the-service"></a>Hizmete yükleyiciler ekleme

Çalıştırmadan önce bir Windows hizmeti, hizmet denetimi Yöneticisi ile kaydeden yüklemeniz gerekir. Yükleyiciler, kayıt ayrıntılarını işlemek için projenize ekleyin.

1. İçinde **Çözüm Gezgini**, kısayol menüsünden **MyNewService.cs**, veya **MyNewService.vb**, seçin **Görünüm Tasarımcısı**.

2. İçinde **tasarım** görüntüleyebilir, arka plan alanını seçin ve ardından **Yükleyici Ekle** kısayol menüsünden.

     Varsayılan olarak, Visual Studio adında bir bileşen sınıfını ekler `ProjectInstaller`, projenize iki yükleyici içeriyor. Bu yükleyicilerden hizmetiniz ve hizmetin ilişkili işlem içindir.

4. İçinde **tasarım** görüntüleme **ProjectInstaller**seçin **Serviceınstaller1** bir görsel için C# projesi veya **Serviceınstaller1**Visual Basic projesi için ardından **özellikleri** kısayol menüsünden.

5. İçinde **özellikleri** penceresinde doğrulayın <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliği **MyNewService**.

6. Metne ekleme <xref:System.ServiceProcess.ServiceInstaller.Description%2A> özelliği gibi *örnek hizmeti*. 

     Bu metin görünür **açıklama** sütununun **Hizmetleri** penceresi ve kullanıcının hizmete açıklar.

    ![Hizmetler penceresini hizmet açıklamasında. ](media/windows-service-description.png "Hizmet açıklaması")

7. Metne ekleme <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> özelliği. Örneğin, *MyNewService görünen ad*. 

     Bu metin görünür **görünen ad** sütununun **Hizmetleri** penceresi. Bu ad farklı olabilir <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliği adı Sistem kullanır (örneğin, adı için kullandığınız `net start` hizmetinizi başlatmak için komut).

8. Ayarlama <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğini <xref:System.ServiceProcess.ServiceStartMode.Automatic> aşağı açılan listeden.

9. İşiniz bittiğinde, **özellikleri** windows gibi şu şekilde görünmelidir:

     ![Bir Windows hizmeti için yükleyici özelliklerini](media/windows-service-installer-properties.png "Windows Installer özellikleri hizmet")

9. İçinde **tasarım** görüntüleme **ProjectInstaller**, seçin **ServiceProcessInstaller1** bir görsel için C# projesi veya **ServiceProcessInstaller1**  Visual Basic projesi için ardından **özellikleri** kısayol menüsünden. Ayarlama <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> özelliğini <xref:System.ServiceProcess.ServiceAccount.LocalSystem> aşağı açılan listeden. 

     Bu ayar hizmetini yükler ve yerel sistem hesabı kullanılarak çalıştırılır.

    > [!IMPORTANT]
    > <xref:System.ServiceProcess.ServiceAccount.LocalSystem> Hesabının olay günlüğüne yazma olanağı dahil olmak üzere geniş izinlere sahip. Bu hesabı kullanırken dikkatli olun; kötü amaçlı yazılımlardan gelecek saldırı riskinizi arttırabilir. Diğer görevler için kullanmayı <xref:System.ServiceProcess.ServiceAccount.LocalService> hesabı yerel bilgisayarda ayrıcalıklı olmayan kullanıcı olarak davranan ve herhangi bir uzak sunucuya anonim kimlik bilgilerini sunar. Bu örnek kullanmaya çalışırsanız başarısız <xref:System.ServiceProcess.ServiceAccount.LocalService> olay günlüğüne yazma izni gerektiğinden, hesap.

Yükleyiciler hakkında daha fazla bilgi için bkz. [nasıl yapılır: Hizmet uygulamasına yükleyiciler ekleme](how-to-add-installers-to-your-service-application.md).

## <a name="optional-set-startup-parameters"></a>(İsteğe bağlı) Başlangıç parametrelerini ayarlayın

> [!NOTE]
> Başlangıç parametreleri eklemek karar vermeden önce hizmetinize bilgi geçirmek için en iyi yolu olup olmadığını göz önünde bulundurun. Bunlar, kullanımı kolay ve ayrıştırma ve kullanıcı bir kolayca bunları geçersiz kılabilirsiniz ancak bulmak ve belgeleri kullanmak bir kullanıcı için daha zor olabilir. Genel olarak, hizmetiniz birkaç taneden fazla yalnızca başlangıç parametre gerektiriyorsa, kayıt defteri veya bir yapılandırma dosyası yerine kullanmalısınız. 

Bir Windows hizmeti, komut satırı bağımsız değişkenleri veya başlangıç parametreleri kabul edebilir. İşlem Başlangıç parametrelerine kod eklediğinizde, bir kullanıcı ile kendi özel başlangıç parametreleri hizmet Özellikler penceresindeki hizmetinizi başlatabilirsiniz. Ancak, bu başlangıç parametreleri, hizmetin bir sonraki başlatılışında kalıcı değildir. Başlangıç parametreleri kalıcı olarak ayarlamak için kayıt defterinde ayarlanan.

Her bir Windows hizmeti altında kayıt defteri girdisini sahip **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** alt. Her hizmetin alt anahtarı altında kullanın **parametreleri** hizmetinizi erişebileceği bilgileri depolamak için alt. Uygulama yapılandırma dosyaları programlar diğer türleri için yaptığınız şekilde bir Windows hizmeti için kullanabilirsiniz. Örnek kod için bkz: <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.

### <a name="to-add-startup-parameters"></a>Başlangıç parametreleri eklemek için

1. Seçin **Program.cs**, veya **MyNewService.Designer.vb**, ardından **kodu görüntüle** kısayol menüsünden. İçinde `Main` yöntemi, bir giriş parametresi ekleyin ve hizmet oluşturucuya geçirmek için kodu değiştirin:

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
       Dim ServicesToRun() As System.ServiceProcess.ServiceBase = New System.ServiceProcess.ServiceBase() {New MyNewService(cmdArgs)}
       System.ServiceProcess.ServiceBase.Run(ServicesToRun)
   End Sub
   ```

2. İçinde **MyNewService.cs**, veya **MyNewService.vb**, değiştirme `MyNewService` Oluşturucusu giriş parametresinin şu şekilde işler:

   ```csharp
   using System.Diagnostics;

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

       eventLog1 = new EventLog();

       if (!EventLog.SourceExists(eventSourceName))
       {
           EventLog.CreateEventSource(eventSourceName, logName);
       }

       eventLog1.Source = eventSourceName;
       eventLog1.Log = logName;
   }
   ```

   ```vb
   Imports System.Diagnostics

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
       eventLog1 = New EventLog()
       If (Not EventLog.SourceExists(eventSourceName)) Then
           EventLog.CreateEventSource(eventSourceName, logName)
       End If
       eventLog1.Source = eventSourceName
       eventLog1.Log = logName
   End Sub
   ```

   Bu kod, kullanıcı kaynakları başlangıç parametreleri göre olay kaynağı ve günlük adını ayarlar. Bağımsız değişken sağlanmadıysa varsayılan değerleri kullanır.

3. Komut satırı bağımsız değişkenlerini belirtmek için aşağıdaki kodu ekleyin. `ProjectInstaller` sınıfını **ProjectInstaller.cs**, veya **ProjectInstaller.vb**:

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

   Genellikle, bu değer, Windows hizmeti için yürütülebilir dosyanın tam yolunu içerir. Hizmet doğru bir şekilde kullanıcı yolu ve tek tek her parametre için tırnak işaretleri sağlamanız gerekir. Bir kullanıcının parametrelerini değiştirip **ImagePath** Windows hizmeti için başlangıç parametreleri değiştirmek için kayıt defteri girişi. Ancak, değeri program aracılığıyla değiştirme ve işlevi kullanımı kolay bir şekilde gibi bir yönetim veya yapılandırma yardımcı programını kullanarak ortaya çıkarmak için daha iyi bir yolu olan.


## <a name="build-the-service"></a>Derleme hizmeti

1. İçinde **Çözüm Gezgini**, seçin **özellikleri** için kısayol menüsünden **MyNewService** proje.

   Projeniz için özellik sayfaları görünür.

2. Üzerinde **uygulama** sekmesinde **Başlangıç nesnesi** listesinde **MyNewService.Program**, veya **Sub Main** Visual Basic projeleri için.

3. İçinde projeyi oluşturmak için **Çözüm Gezgini**, seçin **derleme** projeniz için kısayol menüsünden (veya basın **Ctrl**+**Shift** + **B**).

## <a name="install-the-service"></a>Hizmet yükleme

Windows hizmeti oluşturduğunuza göre bunu yükleyebilirsiniz. Bir Windows hizmetini yüklemek için yüklü olduğu bilgisayarda yönetici kimlik bilgileriniz olmalıdır.

1. Açık [Visual Studio için geliştirici komut istemi](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) yönetici kimlik bilgilerine sahip. Windows gelen **Başlat** menüsünde **VS 2017 için geliştirici komut istemi** Visual Studio klasöründe seçip **daha fazla** > **Çalıştır Yönetici** kısayol menüsünden.

2. İçinde **Visual Studio için geliştirici komut istemi** penceresinde projenizin çıktısını içeren klasöre gidin (varsayılan olarak, *\bin\Debug* projenizin alt).

3. Aşağıdaki komutu girin:

    ```shell
    installutil MyNewService.exe
    ```

    Hizmet başarıyla yüklerse, komut başarılı olduğunu bildirir. 

    Sistem bulamazsa *installutil.exe*, bilgisayarınızda mevcut olduğundan emin olun. Bu araç, .NET Framework klasörüne yüklenir *% windir%\Microsoft.NET\Framework[64]\\&lt;framework sürümü&gt;*. Örneğin, 64-bit sürüm için varsayılan yolu olan *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

    Varsa **installutil.exe** işlem başarısız olursa, nedenini bulmak için yükleme günlüğüne bakın. Varsayılan olarak, günlük hizmeti yürütülebilir olarak aynı klasörde olduğu. Yükleme başarısız olabilir: 
    - <xref:System.ComponentModel.RunInstallerAttribute> Sınıfı üzerinde mevcut değilse `ProjectInstaller` sınıfı.
    -  Öznitelik belirlendiğinden `true`. 
    - `ProjectInstaller` Sınıfı değil olarak tanımlanan `public`.

Daha fazla bilgi için [nasıl yapılır: Hizmetleri Yükleme ve kaldırma](how-to-install-and-uninstall-services.md).

## <a name="start-and-run-the-service"></a>Başlat ve Çalıştır hizmeti

1. Windows içinde açın **Hizmetleri** masaüstü uygulaması. Basın **Windows**+**R** açmak için **çalıştırma** kutusuna *services.msc*ve tuşuna **girin** veya **Tamam**.

     Hizmetiniz listede görürsünüz **Hizmetleri**alfabetik olarak ayarladığınız için görünen ada göre gösterilir.

     ![MyNewService Hizmetleri penceresinde.](media/windowsservices-serviceswindow.PNG)

2. Hizmeti başlatmak için **Başlat** hizmetin kısayol menüsünden.

3. Hizmeti durdurmak için seçin **Durdur** hizmetin kısayol menüsünden.

4. (İsteğe bağlı) Komutları komut satırından kullanın **net start &lt;hizmet adı&gt;**  ve **net stop &lt;hizmet adı&gt;**  hizmetinizi durdurmak ve başlatmak.

### <a name="verify-the-event-log-output-of-your-service"></a>Hizmetinizin olay günlüğü çıktısını doğrulamak

1. Windows içinde açın **Olay Görüntüleyicisi'ni** masaüstü uygulaması. Girin *Olay Görüntüleyicisi'ni* çubuğu ve ardından Windows Search'te **Olay Görüntüleyicisi'ni** Arama sonuçlarından.

   > [!TIP]
   > Visual Studio'da açıp olay günlüklerini erişebilirsiniz **Sunucu Gezgini** gelen **görünümü** menü (veya basın **Ctrl**+**Alt** + **S**) ve genişletme **olay günlüklerini** düğüm yerel bilgisayar.

2. İçinde **Olay Görüntüleyicisi'ni**, genişletme **uygulama ve hizmet günlükleri**.

3. Bulun **MyNewLog** (veya **MyLogFile1** komut satırı bağımsız değişkenleri eklemek için yordamı izlediyseniz) genişletin. Hizmetinizi gerçekleştirilen iki eylem (başlatma ve durdurma) girişleri görmeniz gerekir.

     ![Olay günlüğü girişlerini görmek için Olay Görüntüleyicisi'ni kullanın](media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Windows hizmet uygulaması artık ihtiyacınız kalmadığında, kaldırabilirsiniz. 

1. Açık **Visual Studio için geliştirici komut istemi** yönetici kimlik bilgilerine sahip.

2. İçinde **Visual Studio için geliştirici komut istemi** penceresinde projenizin çıktısını içeren klasöre gidin.

3. Aşağıdaki komutu girin:

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   Hizmet başarıyla kaldırırsa, hizmetinizin başarıyla kaldırıldığını komutu bildirir. Daha fazla bilgi için [nasıl yapılır: Hizmetleri Yükleme ve kaldırma](how-to-install-and-uninstall-services.md).

## <a name="next-steps"></a>Sonraki adımlar

Hizmet oluşturduğunuza göre şunları yapabilirsiniz:

- Windows hizmetinizi yüklemek için kullanmak üzere başkalarını için tek başına bir Kurulum programı oluşturun. Kullanım [WiX Toolset](http://wixtoolset.org/) bir Windows hizmeti için bir yükleyici oluşturmak üzere. Diğer fikir edinmek için bkz: [Yükleyici paketi oluştur](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).

- Keşfedin <xref:System.ServiceProcess.ServiceController> bileşenin yüklediğiniz hizmete komutlar göndermenizi sağlar.

- Uygulama çalıştığında bir olay günlüğü oluşturmak yerine, uygulamayı yüklediğinizde, bir olay günlüğü oluşturmak için bir yükleyici kullanın. Uygulamayı kaldırdığınızda olay günlüğü de yükleyici tarafından silindi. Daha fazla bilgi için bkz. <xref:System.Diagnostics.EventLogInstaller>.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows hizmet uygulamaları](index.md)
- [Windows hizmeti uygulamalarına giriş](introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](how-to-debug-windows-service-applications.md)
- [Hizmetleri (Windows)](/windows/desktop/Services/services)
