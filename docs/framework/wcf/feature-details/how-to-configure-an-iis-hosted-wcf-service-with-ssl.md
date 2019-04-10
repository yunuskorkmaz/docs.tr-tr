---
title: 'Nasıl yapılır: IIS Tarafından Barındırılan Bir WCF Hizmetini SSL ile Yapılandırma'
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: 336c3800fc033cc12bd9c3fe168ae219b72cab91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214124"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>Nasıl yapılır: IIS Tarafından Barındırılan Bir WCF Hizmetini SSL ile Yapılandırma
Bu konu, HTTP aktarım güvenliği kullanılacak bir IIS barındırılan WCF hizmeti kurmak açıklar. HTTP aktarım güvenliği bir SSL sertifikası, IIS ile kayıtlı olması gerekir. Bir SSL sertifikası yoksa, IIS bir test sertifikası oluşturmak için kullanabilirsiniz. Sonraki web sitesine bir SSL bağlaması ekleyin ve web sitesinin kimlik doğrulaması özelliklerini yapılandırmanız gerekir. Son olarak, WCF hizmetini HTTPS kullanacak şekilde yapılandırmanız gerekir.  
  
### <a name="creating-a-self-signed-certificate"></a>Otomatik olarak imzalanan sertifika oluşturma  
  
1.  Internet Information Services Manager (inetmgr.exe) açın ve sol taraftaki ağaç görünümü'nde, bilgisayar adını seçin. Ekranın sağ tarafında sunucu sertifikası seç  
  
     ![IIS Manager giriş ekranı](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2.  Sunucu sertifikaları pencerede **otomatik olarak imzalanan sertifika oluştur...** bağlantı.  
  
     ![Bir kendi kendini oluşturma&#45;IIS sertifikayla imzalanan](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3.  Otomatik olarak imzalanan sertifika için bir kolay ad girin ve tıklayın **Tamam**.  
  
     ![Kendi kendine oluşturmak&#45;imzalı sertifika iletişim kutusu](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")  
  
     Yeni oluşturulan kendinden imzalı bir sertifika ayrıntılarını artık gösterilen **sunucu sertifikaları** penceresi.  
  
     ![Sunucu sertifikası penceresi](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     Oluşturulan sertifika, güvenilen kök sertifika yetkilileri deposunda yüklü depolayın.  
  
### <a name="add-ssl-binding"></a>SSL bağlaması Ekle  
  
1.  Hala Internet Bilgi Hizmetleri Yöneticisi'nde genişletin **siteleri** klasörünü ve ardından **varsayılan Web sitesi** ekranın sol tarafındaki ağaç görünümünde klasörü.  
  
2.  Tıklayın **bağlamaları...** Bağlantısını **eylemleri** pencerenin sağ üst taraftaki bölümünde bölümünde.  
  
     ![Bir SSL bağlaması ekleniyor](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3.  Site bağlamaları pencerede **Ekle** düğmesi.  
  
     ![Site bağlamaları iletişim](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4.  İçinde **Site bağlaması Ekle** türü ve kolay adı, tam otomatik olarak imzalanan sertifika için select https iletişim kutusunda, oluşturulan.  
  
     ![Site bağlama örnek](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>SSL için sanal dizin Yapılandır  
  
1.  Hala Internet Bilgi Hizmetleri Yöneticisi'nde güvenli WCF hizmetinizi içeren sanal dizini seçin.  
  
2.  Pencerenin Orta bölmede seçin **SSL ayarları** IIS bölümünde.  
  
     ![Sanal dizin için SSL ayarları](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3.  SSL ayarları bölmesinde seçin **SSL iste** onay kutusunu tıklatıp **Uygula** bağlantısını **eylemleri** ekranın sağ tarafındaki bölümü.  
  
     ![Sanal dizin SSL ayarları](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>HTTP aktarım güvenliği için WCF hizmetini yapılandırma  
  
1.  WCF'de hizmetin web.config aşağıdaki XML'de gösterildiği aktarım güvenliği kullanılacak HTTP bağlama yapılandırın.  
  
    ```xml  
    <bindings>  
          <basicHttpBinding>  
            <binding name="secureHttpBinding">  
              <security mode="Transport">  
                <transport clientCredentialType="None"/>  
              </security>  
            </binding>  
          </basicHttpBinding>  
    </bindings>  
    ```  
  
2.  Aşağıdaki XML dosyasında gösterildiği gibi hizmet ve hizmet uç noktası belirtin.  
  
    ```xml  
    <services>  
          <service name="MySecureWCFService.Service1">  
            <endpoint address=""  
                      binding="basicHttpBinding"  
                      bindingConfiguration="secureHttpBinding"  
                      contract="MySecureWCFService.IService1"/>  
  
            <endpoint address="mex"  
                      binding="mexHttpsBinding"  
                      contract="IMetadataExchange" />  
          </service>  
    </services>  
    ```  
  
## <a name="example"></a>Örnek  
 HTTP aktarım güvenliği kullanarak bir WCF hizmeti için web.config dosyasının tam bir örnek verilmiştir  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <services>  
      <service name="MySecureWCFService.Service1">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="secureHttpBinding"  
                  contract="MySecureWCFService.IService1"/>  
  
        <endpoint address="mex"  
                  binding="mexHttpsBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="secureHttpBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <!-- To avoid disclosing metadata information, set the value below to false and remove the metadata endpoint above before deployment -->  
          <serviceMetadata httpsGetEnabled="true"/>  
          <!-- To receive exception details in faults for debugging purposes, set the value below to true.  Set to false before deployment to avoid disclosing exception information -->  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
  </system.serviceModel>  
  <system.webServer>  
    <modules runAllManagedModulesForAllRequests="true"/>  
  </system.webServer>  
  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Internet Information Services'te Barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [Internet Information Service Barındırma Yönergeleri](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
- [Internet Information Services Barındırma En İyi Uygulamaları](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [Satır İçi Kod Kullanarak IIS Barındırma](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
