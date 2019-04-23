---
title: 'Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: c63b249cf16100f0b18d622fdecd7cd375df83d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297765"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a>Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma

Bu konuda, bir Windows hizmeti tarafından barındırılan bir Windows Communication Foundation (WCF) hizmet oluşturma için gerekli temel adımlar açıklanmaktadır. Senaryo, uzun süre çalışan, Internet Information Services (IIS) dışında iletisi etkin olmayan güvenli bir ortamda barındırılan bir WCF Hizmeti seçeneğini barındıran yönetilen Windows hizmeti olarak etkindir. Hizmet ömrü, bunun yerine işletim sistemi tarafından denetlenir. Barındırma bu seçenek, tüm Windows sürümlerinde kullanılabilir.

Windows Hizmetleri Microsoft.ManagementConsole.SnapIn Microsoft Yönetim Konsolu (MMC) ile yönetilen ve sistem önyüklendiğinde otomatik olarak başlatılmasını yapılandırılabilir. Bu barındırma seçeneği, yönetilen bir Windows hizmeti olarak bir WCF hizmetini barındıran ve böylece işlem ömrü hizmetin Windows Hizmetleri için Hizmet Denetimi Yöneticisi (SCM) tarafından denetlenen uygulama etki alanı (AppDomain) kaydetme oluşur.

Hizmet kodunu bir hizmet uygulaması hizmet sözleşmesi ve bir Windows hizmet sınıfı bir yükleyici sınıfı içerir. Hizmet uygulaması sınıfı `CalculatorService`, bir WCF hizmeti. `CalculatorWindowsService` Bir Windows hizmetidir. Bir Windows hizmeti olarak nitelemek için sınıf devraldığı `ServiceBase` ve uygulayan `OnStart` ve `OnStop` yöntemleri. İçinde `OnStart`, <xref:System.ServiceModel.ServiceHost> için oluşturulan `CalculatorService` yazın ve açılır. İçinde `OnStop`, hizmeti durdurulur ve atıldı. Konak, uygulama ayarlarında yapılandırılan hizmet ana bilgisayarı için temel adres sağlamaktan sorumludur. Devralınan Yükleyici sınıfı <xref:System.Configuration.Install.Installer>, program tarafından Installutil.exe aracı bir Windows hizmeti olarak yüklenmesini sağlar.

## <a name="construct-the-service-and-provide-the-hosting-code"></a>Hizmet oluşturmak ve barındırma kodu sağlayın

1. Yeni bir Visual Studio oluşturma **konsol uygulaması** adlı proje **hizmet**.

2. Program.cs adını da için yeniden adlandırın.

3. Ad alanına değiştirme `Microsoft.ServiceModel.Samples`.

4. Aşağıdaki derlemelere başvurular ekleyin:

    - System.ServiceModel.dll

    - System.ServiceProcess.dll

    - System.Configuration.Install.dll

5. Aşağıdaki using deyimlerini adını da.

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. Tanımlama `ICalculator` aşağıdaki kodda gösterildiği gibi hizmet sözleşmesi.

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. Adlı bir sınıf içinde hizmet sözleşmesini uygulama `CalculatorService` aşağıdaki kodda gösterildiği gibi.

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. Adlı yeni bir sınıf oluşturma `CalculatorWindowsService` öğesinden devralan <xref:System.ServiceProcess.ServiceBase> sınıfı. Adlı bir yerel değişken ekleme `serviceHost` başvurusuna <xref:System.ServiceModel.ServiceHost> örneği. Tanımlama `Main` çağıran yöntemi `ServiceBase.Run(new CalculatorWindowsService)`

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> oluşturarak ve yeni açma yöntemi <xref:System.ServiceModel.ServiceHost> örneği aşağıdaki kodda gösterildiği gibi.

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemi kapanış <xref:System.ServiceModel.ServiceHost> aşağıdaki kodda gösterildiği gibi.

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. Adlı yeni bir sınıf oluşturma `ProjectInstaller` öğesinden devralan <xref:System.Configuration.Install.Installer> ve ile işaretlenen <xref:System.ComponentModel.RunInstallerAttribute> kümesine `true`. Bu, Installutil.exe aracı tarafından yüklenecek Windows hizmeti sağlar.

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. Kaldırma `Service` projeyi oluşturduğunuzda oluşturulan sınıf.

13. Uygulama yapılandırma dosyası projeye ekleyin. Dosyanın içeriğini aşağıdaki yapılandırma XML ile değiştirin.

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

     Sağ tıklayın App.config dosyasında **Çözüm Gezgini** seçip **özellikleri**. Altında **çıkış dizinine Kopyala** seçin **yeniyse Kopyala**.

     Bu örnek, uç noktaları yapılandırma dosyasında açıkça belirtir. Hizmet için uç nokta eklemezseniz, çalışma zamanı varsayılan uç noktalar ekler. Bu örnekte, hizmetin sahip olduğu bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kümesine `true`, hizmetinizin etkin meta veri yayımlama de vardır. Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

## <a name="install-and-run-the-service"></a>Yükleme ve hizmet çalıştırma

1. Çözümü oluşturmak için yapı `Service.exe` yürütülebilir.

2. Visual Studio için geliştirici komut istemi açın ve proje dizinine gidin. Tür `installutil bin\service.exe` Windows hizmetini yüklemek için komut isteminde.

     Tür `services.msc` Hizmet Denetim Yöneticisi (SCM) erişmek için komut isteminde. Windows hizmeti Hizmetleri'nde "WCFWindowsServiceSample" görünmelidir. Windows Hizmeti çalışıyorsa WCF hizmeti yalnızca istemcilere yanıt verebilir. Hizmeti başlatmak için SCM ve Seç "Başlat" veya türü sağ **net Başlat WCFWindowsServiceSample** komut isteminde.

3. Hizmete değişiklik yaparsanız, öncelikle durdurmak ve bunu kaldırın. Hizmeti durdurun, SCM hizmete sağ tıklayın ve "Durdur" seçin veya **türü net stop WCFWindowsServiceSample** komut isteminde. Windows hizmetini durdurun ve ardından bir istemci çalıştırın gerçekleştiriyorsanız bir <xref:System.ServiceModel.EndpointNotFoundException> istemci hizmeti erişmeye çalışırken özel durum oluşur. Windows hizmet türünü kaldırma **InstallUtil /u bin\service.exe** komut isteminde.

## <a name="example"></a>Örnek

Bu konuda kullanılan kod tam listesi verilmiştir:

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

Gibi bir "Kendi kendine barındırma" seçeneği, Windows hizmet barındırma ortamını bazı barındırma kodu uygulamanın bir parçası yazılması gerekir. Hizmet, bir konsol uygulaması olarak uygulanır ve kendi barındırma kodunu içerir. Windows İşlem Etkinleştirme Hizmeti (WAS) barındıran Internet Information Services (IIS) gibi diğer barındırma ortamlarında yazmak, geliştiriciler için ise gerekli değildir kod barındırma.

## <a name="see-also"></a>Ayrıca bkz.

- [Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)
- [Yönetilen Bir Uygulamada Barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)
- [Barındırma Hizmetleri](../../../../docs/framework/wcf/hosting-services.md)
- [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)