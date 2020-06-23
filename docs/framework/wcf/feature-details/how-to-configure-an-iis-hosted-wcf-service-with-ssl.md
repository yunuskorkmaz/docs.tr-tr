---
title: 'Nasıl yapılır: IIS Tarafından Barındırılan Bir WCF Hizmetini SSL ile Yapılandırma'
description: IIS ile barındırılan bir WCF hizmetini, IIS 'ye kayıtlı bir sertifika gerektiren HTTP aktarım güvenliği 'ni kullanmak üzere ayarlamayı öğrenin.
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: 8dc4692863d93e407a122c0ba93ae38323b8b213
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245264"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>Nasıl yapılır: IIS Tarafından Barındırılan Bir WCF Hizmetini SSL ile Yapılandırma
Bu konuda, IIS tarafından barındırılan bir WCF hizmetinin HTTP aktarım güvenliği kullanmak üzere nasıl ayarlanacağı açıklanır. HTTP aktarım güvenliği, IIS 'ye bir SSL sertifikası kaydedilmesini gerektirir. Bir SSL sertifikanız yoksa, bir test sertifikası oluşturmak için IIS kullanabilirsiniz. Daha sonra Web sitesine bir SSL bağlaması eklemeniz ve Web sitesinin kimlik doğrulama özelliklerini yapılandırmanız gerekir. Son olarak, WCF hizmetini HTTPS kullanacak şekilde yapılandırmanız gerekir.  
  
### <a name="creating-a-self-signed-certificate"></a>Otomatik olarak Imzalanan sertifika oluşturma  
  
1. Internet Information Services Yöneticisi 'Ni açın (inetmgr.exe) ve sol taraftaki ağaç görünümünde bilgisayarınızın adını seçin. Ekranın sağ tarafında sunucu sertifikaları ' nı seçin.  
  
     ![IIS Yöneticisi giriş ekranı](media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2. Sunucu sertifikaları penceresinde **otomatik olarak Imzalanan sertifika oluştur...** öğesine tıklayın. Bağlantısının.  
  
     ![IIS ile kendinden&#45;imzalı bir sertifika oluşturma](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3. Otomatik olarak imzalanan sertifika için kolay bir ad girin ve **Tamam 'a**tıklayın.  
  
     ![Kendinden&#45;Imzalı sertifika Iletişim kutusu oluştur](media/mg-mycert.jpg "mg_MyCert")  
  
     Yeni oluşturulan otomatik olarak imzalanan sertifika ayrıntıları artık **sunucu sertifikaları** penceresinde gösteriliyor.  
  
     ![Sunucu sertifikası penceresi](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     Oluşturulan sertifika, güvenilen kök sertifika yetkilileri deposuna yüklenir.  
  
### <a name="add-ssl-binding"></a>SSL bağlaması Ekle  
  
1. Hala Internet Information Services Manager 'da, **siteler** klasörünü ve ardından ekranın sol tarafındaki ağaç görünümünde bulunan **varsayılan Web sitesi** klasörünü genişletin.  
  
2. **Bağlamalar...** öğesine tıklayın. Pencerenin sağ üst kısmında bulunan **Eylemler** bölümündeki bağlantı.  
  
     ![SSL bağlaması ekleme](media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3. Site bağlamaları penceresinde **Ekle** düğmesine tıklayın.  
  
     ![Site bağlamaları Iletişim kutusu](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4. **Site Bağlaması Ekle** iletişim kutusunda, türü için https ' yi ve yeni oluşturduğunuz otomatik olarak imzalanan sertifikanın kolay adını seçin.  
  
     ![Site bağlama örneği](media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>SSL için sanal dizini yapılandırma  
  
1. Hala Internet Information Services Manager 'da, WCF güvenli hizmetinizi içeren sanal dizini seçin.  
  
2. Pencerenin orta bölmesinde IIS bölümünde **SSL ayarları** ' nı seçin.  
  
     ![Sanal dizin için SSL ayarları](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3. SSL ayarları bölmesinde, **SSL gerektir** onay kutusunu seçin ve ekranın sağ tarafındaki **Eylemler** bölümünde **Uygula** bağlantısına tıklayın.  
  
     ![Sanal Dizin SSL ayarları](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>HTTP taşıma güvenliği için WCF hizmetini yapılandırma  
  
1. WCF hizmetinin web.config, HTTP bağlamasını aşağıdaki XML 'de gösterildiği gibi aktarım güvenliği kullanacak şekilde yapılandırın.  
  
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
  
2. Aşağıdaki XML 'de gösterildiği gibi hizmetinizi ve hizmet uç noktasını belirtin.  
  
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
 Aşağıda, HTTP aktarım güvenliği kullanan bir WCF hizmeti için web.config dosyasına ait bir örnek verilmiştir  
  
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

- [Internet Information Services'te Barındırma](hosting-in-internet-information-services.md)
- [Internet Information Service Barındırma Yönergeleri](../samples/internet-information-service-hosting-instructions.md)
- [Internet Information Services Barındırma En İyi Uygulamaları](internet-information-services-hosting-best-practices.md)
- [Satır İçi Kod Kullanarak IIS Barındırma](../samples/iis-hosting-using-inline-code.md)
