---
title: 'Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma'
description: Bir Windows hizmeti tarafından barındırılan bir WCF hizmeti oluşturmayı öğrenin. Bu barındırma seçeneği Windows 'un tüm sürümlerinde kullanılabilir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: 4e07aa7aac82fae5cfd1bfc759ef724cf87a873a
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246942"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a>Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma

Bu konuda, bir Windows hizmeti tarafından barındırılan Windows Communication Foundation (WCF) hizmeti oluşturmak için gereken temel adımlar özetlenmektedir. Bu senaryo, ileti etkinleştirilmemiş güvenli bir ortamda Internet Information Services (IIS) dışında barındırılan, uzun süre çalışan bir WCF hizmeti olan yönetilen Windows hizmeti barındırma seçeneği tarafından etkinleştirilir. Hizmetin kullanım ömrü, işletim sistemi tarafından bunun yerine denetlenir. Bu barındırma seçeneği Windows 'un tüm sürümlerinde kullanılabilir.

Windows Hizmetleri, Microsoft Yönetim Konsolu 'nda (MMC) Microsoft. ManagementConsole. Snapın ile yönetilebilir ve sistem önyüklendiğinde otomatik olarak başlayacak şekilde yapılandırılabilir. Bu barındırma seçeneği, hizmet işlem ömrünün Windows Hizmetleri için hizmet denetimi Yöneticisi (SCM) tarafından denetlenmesi için bir WCF hizmetini yönetilen bir Windows hizmeti olarak barındıran uygulama etki alanını (AppDomain) kaydetmeden oluşur.

Hizmet kodu, hizmet sözleşmesinin bir hizmet uygulamasını, bir Windows hizmeti sınıfını ve bir yükleyici sınıfını içerir. Hizmet uygulama sınıfı, `CalculatorService` BIR WCF hizmetidir. , `CalculatorWindowsService` Bir Windows hizmetidir. Bir Windows hizmeti olarak nitelendirmek için, sınıfı öğesinden devralır `ServiceBase` ve `OnStart` ve yöntemlerini uygular `OnStop` . İçinde `OnStart` , <xref:System.ServiceModel.ServiceHost> türü için oluşturulur `CalculatorService` ve açılır. `OnStop`' De, hizmet durdurulur ve bırakıldı. Ana bilgisayar Ayrıca, uygulama ayarlarında yapılandırılan hizmet ana bilgisayarı için bir temel adres sağlamaktan da sorumludur. ' Den devralan Yükleyici sınıfı <xref:System.Configuration.Install.Installer> , programın Installutil.exe aracı tarafından bir Windows hizmeti olarak yüklenmesine izin verir.

## <a name="construct-the-service-and-provide-the-hosting-code"></a>Hizmeti oluşturun ve barındırma kodunu sağlayın

1. **Hizmeti**adlı yeni bir Visual Studio **konsol uygulaması** projesi oluşturun.

2. Program.cs olarak yeniden adlandırın.

3. Ad alanını olarak değiştirin `Microsoft.ServiceModel.Samples` .

4. Aşağıdaki derlemelere başvurular ekleyin:

    - System.ServiceModel.dll

    - System.ServiceProcess.dll

    - System.Configuration.Install.dll

5. Aşağıdaki using deyimlerini Service.cs öğesine ekleyin.

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. `ICalculator`Hizmet sözleşmesini aşağıdaki kodda gösterildiği gibi tanımlayın.

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. Hizmet sözleşmesini `CalculatorService` aşağıdaki kodda gösterildiği gibi adlı bir sınıfta uygulayın.

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. Sınıfından devralan adlı yeni bir sınıf oluşturun `CalculatorWindowsService` <xref:System.ServiceProcess.ServiceBase> . Örneğe başvurmak için adlı bir yerel değişken ekleyin `serviceHost` <xref:System.ServiceModel.ServiceHost> . `Main`Çağıran yöntemi tanımlayın`ServiceBase.Run(new CalculatorWindowsService)`

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>Aşağıdaki kodda gösterildiği gibi yeni bir örnek oluşturup açarak yöntemi geçersiz kılın <xref:System.ServiceModel.ServiceHost> .

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. <xref:System.ServiceProcess.ServiceBase.OnStop%2A>Aşağıdaki kodda gösterildiği gibi, öğesini kapatan yöntemini geçersiz kılın <xref:System.ServiceModel.ServiceHost> .

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. `ProjectInstaller`' Den devralan ve ' den ' a işaretlenmiş olarak işaretlenen yeni bir sınıf oluşturun <xref:System.Configuration.Install.Installer> <xref:System.ComponentModel.RunInstallerAttribute> `true` . Bu, Windows hizmetinin Installutil.exe aracı tarafından yüklenmesine izin verir.

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. `Service`Projeyi oluştururken oluşturulan sınıfı kaldırın.

13. Projeye bir uygulama yapılandırma dosyası ekleyin. Dosyanın içeriğini aşağıdaki yapılandırma XML ile değiştirin.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.serviceModel>    <services>
          <!-- This section is optional with the new configuration model
               introduced in .NET Framework 4. -->
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"
                   behaviorConfiguration="CalculatorServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
            <endpoint address=""
                      binding="wsHttpBinding"
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />
          </service>
        </services>
        <behaviors>
          <serviceBehaviors>
            <behavior name="CalculatorServiceBehavior">
              <serviceMetadata httpGetEnabled="true"/>
              <serviceDebug includeExceptionDetailInFaults="False"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>
      </system.serviceModel>
    </configuration>
    ```

     **Çözüm Gezgini** App.config dosyasına sağ tıklayın ve **Özellikler**' i seçin. **Çıkış Dizinine Kopyala** ' nın altında **, daha yeniyse kopyala**' yı seçin.

     Bu örnek, yapılandırma dosyasındaki uç noktaları açıkça belirtir. Hizmete herhangi bir uç nokta eklemediğiniz takdirde, çalışma zamanı sizin için varsayılan uç noktaları ekler. Bu örnekte, hizmetin <xref:System.ServiceModel.Description.ServiceMetadataBehavior> olarak ayarlanmış olması nedeniyle `true` hizmetinize yayımlama meta verileri de etkinleştirilmiştir. Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../simplified-configuration.md) ve Basitleştirilmiş yapılandırma.

## <a name="install-and-run-the-service"></a>Hizmeti yükleyip çalıştırın

1. Yürütülebilir dosyayı oluşturmak için çözümü oluşturun `Service.exe` .

2. Visual Studio için Geliştirici Komut İstemi açın ve proje dizinine gidin. `installutil bin\service.exe`Windows hizmetini yüklemek için komut istemine yazın.

     `services.msc`Service Control Manager 'a (SCM) erişmek için komut istemine yazın. Windows hizmeti hizmetlerde "WCFWindowsServiceSample" olarak görünmelidir. WCF hizmeti yalnızca Windows hizmeti çalışıyorsa istemcilere yanıt verebilir. Hizmeti başlatmak için SCM 'de sağ tıklayın ve "Başlat" ı seçin veya komut istemine **net start WCFWindowsServiceSample** yazın.

3. Hizmette değişiklik yaparsanız, önce onu durdurup kaldırmanız gerekir. Hizmeti durdurmak için SCM 'de hizmete sağ tıklayın ve "Durdur" seçeneğini belirleyin veya komut istemine **net stop WCFWindowsServiceSample yazın** . Windows hizmetini durdurup bir istemciyi çalıştırırsanız, <xref:System.ServiceModel.EndpointNotFoundException> istemci hizmete erişmeye çalıştığında bir özel durum oluşur. Windows hizmet türü **InstallUtil/u bin\service.exe** kaldırmak için komut isteminde.

## <a name="example"></a>Örnek

Aşağıda, bu konunun kullandığı kodun tamamen bir listesi verilmiştir:

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

"Kendi kendine barındırma" seçeneğinde olduğu gibi, Windows hizmeti barındırma ortamı, bazı barındırma kodunun uygulamanın bir parçası olarak yazılmasını gerektirir. Hizmet bir konsol uygulaması olarak uygulanır ve kendi barındırma kodunu içerir. Internet Information Services (IIS) içinde barındırılan Windows Işlem etkinleştirme hizmeti (WAS) gibi diğer barındırma ortamlarında, geliştiricilerin barındırma kodunu yazması gerekli değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Basitleştirilmiş Yapılandırma](../simplified-configuration.md)
- [Yönetilen Bir Uygulamada Barındırma](hosting-in-a-managed-application.md)
- [Barındırma Hizmetleri](../hosting-services.md)
- [Windows Server App Fabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
