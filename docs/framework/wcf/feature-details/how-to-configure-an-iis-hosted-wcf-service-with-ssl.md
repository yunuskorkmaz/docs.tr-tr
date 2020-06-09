---
title: 'Nasıl yapılır: IIS Tarafından Barındırılan Bir WCF Hizmetini SSL ile Yapılandırma'
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: fb3e87021c3dce1172250f33fd302916920af74d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597234"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="f1bc7-102">Nasıl yapılır: IIS Tarafından Barındırılan Bir WCF Hizmetini SSL ile Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f1bc7-102">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="f1bc7-103">Bu konuda, IIS tarafından barındırılan bir WCF hizmetinin HTTP aktarım güvenliği kullanmak üzere nasıl ayarlanacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-103">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="f1bc7-104">HTTP aktarım güvenliği, IIS 'ye bir SSL sertifikası kaydedilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-104">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="f1bc7-105">Bir SSL sertifikanız yoksa, bir test sertifikası oluşturmak için IIS kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-105">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="f1bc7-106">Daha sonra Web sitesine bir SSL bağlaması eklemeniz ve Web sitesinin kimlik doğrulama özelliklerini yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-106">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="f1bc7-107">Son olarak, WCF hizmetini HTTPS kullanacak şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-107">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="f1bc7-108">Otomatik olarak Imzalanan sertifika oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1bc7-108">Creating a Self-Signed Certificate</span></span>  
  
1. <span data-ttu-id="f1bc7-109">Internet Information Services Yöneticisi 'Ni (inetmgr. exe) açın ve sol ağaç görünümünde bilgisayarınızın adını seçin.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-109">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="f1bc7-110">Ekranın sağ tarafında sunucu sertifikaları ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-110">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="f1bc7-111">![IIS Yöneticisi giriş ekranı](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="f1bc7-111">![IIS Manager Home Screen](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2. <span data-ttu-id="f1bc7-112">Sunucu sertifikaları penceresinde **otomatik olarak Imzalanan sertifika oluştur...** öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-112">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="f1bc7-113">Bağlantısının.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-113">Link.</span></span>  
  
     <span data-ttu-id="f1bc7-114">![IIS ile kendinden&#45;imzalı bir sertifika oluşturma](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="f1bc7-114">![Creating a self&#45;signed certificate with IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3. <span data-ttu-id="f1bc7-115">Otomatik olarak imzalanan sertifika için kolay bir ad girin ve **Tamam 'a**tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-115">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="f1bc7-116">![Kendinden&#45;Imzalı sertifika Iletişim kutusu oluştur](media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="f1bc7-116">![Create Self&#45;Signed Certificate Dialog](media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="f1bc7-117">Yeni oluşturulan otomatik olarak imzalanan sertifika ayrıntıları artık **sunucu sertifikaları** penceresinde gösteriliyor.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-117">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="f1bc7-118">![Sunucu sertifikası penceresi](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="f1bc7-118">![Server Certificate Window](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="f1bc7-119">Oluşturulan sertifika, güvenilen kök sertifika yetkilileri deposuna yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-119">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="f1bc7-120">SSL bağlaması Ekle</span><span class="sxs-lookup"><span data-stu-id="f1bc7-120">Add SSL Binding</span></span>  
  
1. <span data-ttu-id="f1bc7-121">Hala Internet Information Services Manager 'da, **siteler** klasörünü ve ardından ekranın sol tarafındaki ağaç görünümünde bulunan **varsayılan Web sitesi** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-121">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2. <span data-ttu-id="f1bc7-122">**Bağlamalar...** öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-122">Click the **Bindings….**</span></span> <span data-ttu-id="f1bc7-123">Pencerenin sağ üst kısmında bulunan **Eylemler** bölümündeki bağlantı.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-123">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="f1bc7-124">![SSL bağlaması ekleme](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="f1bc7-124">![Adding an SSL binding](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3. <span data-ttu-id="f1bc7-125">Site bağlamaları penceresinde **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-125">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="f1bc7-126">![Site bağlamaları Iletişim kutusu](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="f1bc7-126">![Site Bindings Dialog](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4. <span data-ttu-id="f1bc7-127">**Site Bağlaması Ekle** iletişim kutusunda, türü için https ' yi ve yeni oluşturduğunuz otomatik olarak imzalanan sertifikanın kolay adını seçin.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-127">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="f1bc7-128">![Site bağlama örneği](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="f1bc7-128">![Site binding example](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="f1bc7-129">SSL için sanal dizini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f1bc7-129">Configure Virtual Directory for SSL</span></span>  
  
1. <span data-ttu-id="f1bc7-130">Hala Internet Information Services Manager 'da, WCF güvenli hizmetinizi içeren sanal dizini seçin.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-130">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2. <span data-ttu-id="f1bc7-131">Pencerenin orta bölmesinde IIS bölümünde **SSL ayarları** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-131">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="f1bc7-132">![Sanal dizin için SSL ayarları](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="f1bc7-132">![SSL Settings for virtual directory](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3. <span data-ttu-id="f1bc7-133">SSL ayarları bölmesinde, **SSL gerektir** onay kutusunu seçin ve ekranın sağ tarafındaki **Eylemler** bölümünde **Uygula** bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-133">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="f1bc7-134">![Sanal Dizin SSL ayarları](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="f1bc7-134">![Virtual directory SSL settings](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="f1bc7-135">HTTP taşıma güvenliği için WCF hizmetini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f1bc7-135">Configure WCF Service for HTTP Transport Security</span></span>  
  
1. <span data-ttu-id="f1bc7-136">WCF hizmetinin Web. config dosyasında, HTTP bağlamasını aşağıdaki XML 'de gösterildiği gibi aktarım güvenliği kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-136">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
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
  
2. <span data-ttu-id="f1bc7-137">Aşağıdaki XML 'de gösterildiği gibi hizmetinizi ve hizmet uç noktasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-137">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="f1bc7-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1bc7-138">Example</span></span>  
 <span data-ttu-id="f1bc7-139">Aşağıda, HTTP aktarım güvenliği kullanan bir WCF hizmeti için Web. config dosyasının tamamı bir örneği verilmiştir</span><span class="sxs-lookup"><span data-stu-id="f1bc7-139">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f1bc7-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1bc7-140">See also</span></span>

- [<span data-ttu-id="f1bc7-141">Internet Information Services'te Barındırma</span><span class="sxs-lookup"><span data-stu-id="f1bc7-141">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="f1bc7-142">Internet Information Service Barındırma Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f1bc7-142">Internet Information Service Hosting Instructions</span></span>](../samples/internet-information-service-hosting-instructions.md)
- [<span data-ttu-id="f1bc7-143">Internet Information Services Barındırma En İyi Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="f1bc7-143">Internet Information Services Hosting Best Practices</span></span>](internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="f1bc7-144">Satır İçi Kod Kullanarak IIS Barındırma</span><span class="sxs-lookup"><span data-stu-id="f1bc7-144">IIS Hosting Using Inline Code</span></span>](../samples/iis-hosting-using-inline-code.md)
