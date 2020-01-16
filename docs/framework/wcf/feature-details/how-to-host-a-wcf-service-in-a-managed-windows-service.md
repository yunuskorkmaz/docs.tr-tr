---
title: 'Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: 698a5134683341fedf2a37f7d6383770e14c232c
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964798"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a>Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma

Bu konuda, bir Windows hizmeti tarafından barındırılan Windows Communication Foundation (WCF) hizmeti oluşturmak için gereken temel adımlar özetlenmektedir. Bu senaryo, ileti etkinleştirilmemiş güvenli bir ortamda Internet Information Services (IIS) dışında barındırılan, uzun süre çalışan bir WCF hizmeti olan yönetilen Windows hizmeti barındırma seçeneği tarafından etkinleştirilir. Hizmetin kullanım ömrü, işletim sistemi tarafından bunun yerine denetlenir. Bu barındırma seçeneği Windows 'un tüm sürümlerinde kullanılabilir.

Windows Hizmetleri, Microsoft Yönetim Konsolu 'nda (MMC) Microsoft. ManagementConsole. Snapın ile yönetilebilir ve sistem önyüklendiğinde otomatik olarak başlayacak şekilde yapılandırılabilir. Bu barındırma seçeneği, hizmet işlem ömrünün Windows Hizmetleri için hizmet denetimi Yöneticisi (SCM) tarafından denetlenmesi için bir WCF hizmetini yönetilen bir Windows hizmeti olarak barındıran uygulama etki alanını (AppDomain) kaydetmeden oluşur.

Hizmet kodu, hizmet sözleşmesinin bir hizmet uygulamasını, bir Windows hizmeti sınıfını ve bir yükleyici sınıfını içerir. Hizmet uygulama sınıfı `CalculatorService`, bir WCF hizmetidir. `CalculatorWindowsService` bir Windows hizmetidir. Bir Windows hizmeti olarak nitelendirmek için, sınıf `ServiceBase` devralır ve `OnStart` ve `OnStop` yöntemlerini uygular. `OnStart`, `CalculatorService` türü için <xref:System.ServiceModel.ServiceHost> oluşturulur ve açılır. `OnStop`, hizmet durdurulur ve bırakıldı. Ana bilgisayar Ayrıca, uygulama ayarlarında yapılandırılan hizmet ana bilgisayarı için bir temel adres sağlamaktan da sorumludur. <xref:System.Configuration.Install.Installer>devralan Yükleyici sınıfı, programın InstallUtil. exe aracı tarafından bir Windows hizmeti olarak yüklenmesine izin verir.

## <a name="construct-the-service-and-provide-the-hosting-code"></a>Hizmeti oluşturun ve barındırma kodunu sağlayın

1. **Hizmeti**adlı yeni bir Visual Studio **konsol uygulaması** projesi oluşturun.

2. Program.cs olarak yeniden adlandırın.

3. Ad alanını `Microsoft.ServiceModel.Samples`değiştirin.

4. Aşağıdaki derlemelere başvurular ekleyin:

    - System.ServiceModel.dll

    - System. ServiceProcess. dll

    - System.Configuration.Install.dll

5. Aşağıdaki using deyimlerini Service.cs öğesine ekleyin.

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. Aşağıdaki kodda gösterildiği gibi `ICalculator` hizmet sözleşmesini tanımlayın.

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. Hizmet sözleşmesini, aşağıdaki kodda gösterildiği gibi `CalculatorService` adlı bir sınıfta uygulayın.

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. <xref:System.ServiceProcess.ServiceBase> sınıfından devralan `CalculatorWindowsService` adlı yeni bir sınıf oluşturun. <xref:System.ServiceModel.ServiceHost> örneğine başvurmak için `serviceHost` adlı bir yerel değişken ekleyin. `ServiceBase.Run(new CalculatorWindowsService)` çağıran `Main` yöntemi tanımlayın

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. Aşağıdaki kodda gösterildiği gibi yeni bir <xref:System.ServiceModel.ServiceHost> örneği oluşturup açarak <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> yöntemini geçersiz kılın.

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. Aşağıdaki kodda gösterildiği gibi <xref:System.ServiceModel.ServiceHost> kapatan <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemini geçersiz kılın.

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. <xref:System.Configuration.Install.Installer> devralan ve `true`<xref:System.ComponentModel.RunInstallerAttribute> ayarlanmış olarak işaretlenen `ProjectInstaller` adlı yeni bir sınıf oluşturun. Bu, Windows hizmetinin InstallUtil. exe aracı tarafından yüklenmesine izin verir.

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. Projeyi oluştururken oluşturulan `Service` sınıfını kaldırın.

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

     **Çözüm Gezgini** App. config dosyasına sağ tıklayın ve **Özellikler**' i seçin. **Çıkış Dizinine Kopyala** ' nın altında **, daha yeniyse kopyala**' yı seçin.

     Bu örnek, yapılandırma dosyasındaki uç noktaları açıkça belirtir. Hizmete herhangi bir uç nokta eklemediğiniz takdirde, çalışma zamanı sizin için varsayılan uç noktaları ekler. Bu örnekte, hizmet `true`olarak ayarlanmış <xref:System.ServiceModel.Description.ServiceMetadataBehavior> sahip olduğundan, hizmetiniz yayımlama meta verilerini de etkinleştirdi. Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.

## <a name="install-and-run-the-service"></a>Hizmeti yükleyip çalıştırın

1. `Service.exe` çalıştırılabiliri oluşturmak için çözümü oluşturun.

2. Visual Studio için Geliştirici Komut İstemi açın ve proje dizinine gidin. Windows hizmetini yüklemek için komut istemine `installutil bin\service.exe` yazın.

     Service Control Manager 'a (SCM) erişmek için komut istemine `services.msc` yazın. Windows hizmeti hizmetlerde "WCFWindowsServiceSample" olarak görünmelidir. WCF hizmeti yalnızca Windows hizmeti çalışıyorsa istemcilere yanıt verebilir. Hizmeti başlatmak için SCM 'de sağ tıklayın ve "Başlat" ı seçin veya komut istemine **net start WCFWindowsServiceSample** yazın.

3. Hizmette değişiklik yaparsanız, önce onu durdurup kaldırmanız gerekir. Hizmeti durdurmak için SCM 'de hizmete sağ tıklayın ve "Durdur" seçeneğini belirleyin veya komut istemine **net stop WCFWindowsServiceSample yazın** . Windows hizmetini durdurup bir istemciyi çalıştırırsanız, istemci hizmete erişmeyi denediğinde bir <xref:System.ServiceModel.EndpointNotFoundException> özel durum oluştuğunu unutmayın. Windows hizmet türü **InstallUtil/u bin\service.exe** komutunu komut istemine kaldırmak için.

## <a name="example"></a>Örnek

Aşağıda, bu konunun kullandığı kodun tamamen bir listesi verilmiştir:

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

"Kendi kendine barındırma" seçeneğinde olduğu gibi, Windows hizmeti barındırma ortamı, bazı barındırma kodunun uygulamanın bir parçası olarak yazılmasını gerektirir. Hizmet bir konsol uygulaması olarak uygulanır ve kendi barındırma kodunu içerir. Internet Information Services (IIS) içinde barındırılan Windows Işlem etkinleştirme hizmeti (WAS) gibi diğer barındırma ortamlarında, geliştiricilerin barındırma kodunu yazması gerekli değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)
- [Yönetilen Bir Uygulamada Barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)
- [Barındırma Hizmetleri](../../../../docs/framework/wcf/hosting-services.md)
- [Windows Server App Fabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
