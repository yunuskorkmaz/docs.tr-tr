---
title: "Nasıl yapılır: IIS Tarafından Barındırılan Bir WCF Hizmetini SSL ile Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b16ca5b4cfe615eedd9e532b12f61394806829bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>Nasıl yapılır: IIS Tarafından Barındırılan Bir WCF Hizmetini SSL ile Yapılandırma
Bu konu, HTTP taşıma güvenliği kullanılacak bir IIS tarafından barındırılan bir WCF hizmeti kurmak açıklar. HTTP taşıma güvenliği ile IIS kaydedilmesi için bir SSL sertifikası gerektirir. Bir SSL sertifikası yoksa, bir test sertifikası oluşturmak için IIS kullanabilirsiniz. Sonraki web sitesi için SSL bağlaması eklemek ve web sitesinin kimlik doğrulama özelliklerini yapılandırmanız gerekir. Son olarak, WCF hizmetini HTTPS kullanacak şekilde yapılandırmanız gerekir.  
  
### <a name="creating-a-self-signed-certificate"></a>Otomatik olarak imzalanan sertifika oluşturma  
  
1.  Internet Information Services Yöneticisi (inetmgr.exe) açın ve sol ağaç görünümünde bilgisayarınızın adını seçin. Ekranın sağ tarafta sunucu sertifikası seç  
  
     ![IIS Yöneticisi'ni giriş ekranı](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2.  Sunucu sertifikaları penceresinde tıklatın **otomatik olarak imzalanan sertifika oluştur...** Bağlantı.  
  
     ![Kendi &#45; oluşturma IIS sertifikayla imzalanmış](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3.  Otomatik olarak imzalanan sertifika için bir kolay ad girin ve tıklayın **Tamam**.  
  
     ![Kendi kendini &#45;oluşturun; Sertifika iletişim kutusu imzalı](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")  
  
     Yeni oluşturulan otomatik olarak imzalanan sertifika ayrıntılarını şimdi'nda gösterilen **sunucu sertifikaları** penceresi.  
  
     ![Sunucu sertifikası penceresi](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     Oluşturulan sertifika güvenilen kök sertifika yetkilileri yüklü depolar.  
  
### <a name="add-ssl-binding"></a>SSL bağlaması ekleme  
  
1.  Hala Internet Bilgi Hizmetleri Yöneticisi'nde **siteleri** klasörünü ve ardından **varsayılan Web sitesi** ekranın sol taraftaki ağaç görünümünde klasörü.  
  
2.  Tıklatın **bağlamaları...** Bağlamak **Eylemler** pencerenin üst sağ taraftaki bölümünde bölümünde.  
  
     ![SSL bağlaması ekleme](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3.  Site bağlamaları penceresinde tıklatın **Ekle** düğmesi.  
  
     ![Site bağlamaları iletişim](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4.  İçinde **Site bağlaması Ekle** türü ve yeni imzalanan sertifikanın kolay adını Seç https iletişim kutusunda, oluşturulmuş.  
  
     ![Site bağlama örnek](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>Sanal dizin için SSL yapılandırma  
  
1.  Hala Internet Bilgi Hizmetleri Yöneticisi'nde, WCF güvenli hizmetinizi içeren sanal dizini seçin.  
  
2.  Pencerenin Orta bölmede seçin **SSL ayarları** IIS bölümünde.  
  
     ![Sanal dizin için SSL ayarları](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3.  SSL ayarları bölmesinde seçin **SSL iste** onay kutusunu tıklatıp **Uygula** bağlamak **Eylemler** ekranın sağ taraftaki bölüm.  
  
     ![Sanal dizin SSL ayarları](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>HTTP taşıma güvenliği için WCF hizmetini yapılandırma  
  
1.  WCF hizmet web.config aşağıdaki XML dosyasında gösterildiği gibi taşıma güvenliği kullanmak için HTTP bağlaması yapılandırın.  
  
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
  
2.  Hizmet ve hizmet uç noktası aşağıdaki XML dosyasında gösterildiği gibi belirtin.  
  
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
 HTTP taşıma güvenliği kullanarak bir WCF hizmeti için web.config dosyasının tam bir örnek verilmiştir  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Internet Information Services'te Barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Internet Information Service Barındırma Yönergeleri](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [Internet Information Services Barındırma En İyi Uygulamaları](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Satır İçi Kod Kullanarak IIS Barındırma](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
