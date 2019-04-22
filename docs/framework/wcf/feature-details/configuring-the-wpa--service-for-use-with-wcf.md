---
title: Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: a4c331465087c6910cb67a71d2153e08f82a6cd6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147712"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="15ca1-102">Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="15ca1-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>
<span data-ttu-id="15ca1-103">Bu konu, Windows İşlem Etkinleştirme Hizmeti (WAS olarak da bilinir) ' için gerekli adımları açıklar. [!INCLUDE[wv](../../../../includes/wv-md.md)] Windows Communication Foundation (WCF) barındırmak için HTTP üzerinden iletişim kurmazlar Hizmetleri protokolleri ağ.</span><span class="sxs-lookup"><span data-stu-id="15ca1-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in [!INCLUDE[wv](../../../../includes/wv-md.md)] to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="15ca1-104">Aşağıdaki bölümlerde, bu yapılandırmanın adımları özetlemektedir:</span><span class="sxs-lookup"><span data-stu-id="15ca1-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="15ca1-105">Yükleme (veya yüklenmesini onaylayın) gerekli WCF etkinleştirme bileşenlerini.</span><span class="sxs-lookup"><span data-stu-id="15ca1-105">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
-   <span data-ttu-id="15ca1-106">Kullanmak istediğiniz ağ protokolü bağlamaları ile WAS site oluşturma veya mevcut bir site için yeni bir protokol bağlama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="15ca1-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
-   <span data-ttu-id="15ca1-107">Hizmetlerinizi barındırmak ve bu uygulamayı gerekli ağ protokolleri kullanmak üzere etkinleştirmek için bir uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="15ca1-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
-   <span data-ttu-id="15ca1-108">HTTP olmayan uç noktasını kullanıma sunar bir WCF Hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="15ca1-108">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="15ca1-109">Bir Site ile HTTP olmayan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="15ca1-109">Configuring a Site with Non-HTTP bindings</span></span>  
 <span data-ttu-id="15ca1-110">Bir HTTP olmayan bağlama WAS ile kullanmak için bir site bağlaması için WAS yapılandırma eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="15ca1-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="15ca1-111">WAS yapılandırma mağazada %windir%\system32\inetsrv\config dizininde bulunan applicationHost.config dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="15ca1-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="15ca1-112">Bu yapılandırma deposu WAS ve IIS 7.0 tarafından paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="15ca1-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="15ca1-113">applicationHost.config standart bir metin düzenleyicisinde (Not Defteri gibi) ile açılmış bir XML metin dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="15ca1-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="15ca1-114">Ancak, [!INCLUDE[iisver](../../../../includes/iisver-md.md)] komut satırı Yapılandırma Aracı (appcmd.exe), HTTP olmayan site bağlamaları Ekle tercih edilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="15ca1-114">However, the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="15ca1-115">Aşağıdaki komutu (Bu komut, tek bir satır olarak girilir) appcmd.exe kullanarak varsayılan Web sitesi net.tcp site bağlaması ekler.</span><span class="sxs-lookup"><span data-stu-id="15ca1-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="15ca1-116">Bu komut, yeni net.tcp bağlama applicationHost.config dosyasına aşağıda belirtilen satır ekleyerek varsayılan Web sitesine ekler.</span><span class="sxs-lookup"><span data-stu-id="15ca1-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="15ca1-117">HTTP olmayan protokolleri kullanmak üzere bir uygulama etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="15ca1-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  
 <span data-ttu-id="15ca1-118">Etkinleştirmek veya tek tek ağ protocolsat uygulama düzeyinde devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15ca1-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="15ca1-119">Aşağıdaki komutu çalışan bir uygulama için hem HTTP hem de net.tcp protokolleri etkinleştirme gösterir `Default Web Site`.</span><span class="sxs-lookup"><span data-stu-id="15ca1-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="15ca1-120">Etkin protokoller listesinde de ayarlanabilir \<applicationDefaults > ApplicationHost.config dosyasında depolanan sitenin XML yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="15ca1-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="15ca1-121">Aşağıdaki XML kodunu applicationHost.config'den hem HTTP hem de HTTP olmayan protokolleri için ilişkili bir site gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="15ca1-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="15ca1-122">HTTP olmayan protokolleri desteklemek için gereken ek yapılandırma yorumlarla çağırılır.</span><span class="sxs-lookup"><span data-stu-id="15ca1-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
    <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
    </application>  
       <bindings>  
            //The following two lines are added by the command.  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile   
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging   
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults   
      applicationPool="DefaultAppPool"   
      //The following line is inserted by the command.  
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 <span data-ttu-id="15ca1-123">HTTP olmayan etkinleştirme için WAS'ı kullanarak hizmeti etkinleştirin dener ve yüklenmediğinde veya WAS yapılandırılmış şu hatayı görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="15ca1-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="15ca1-124">WAS için emin olun. Bu hatayı görürseniz, HTTP olmayan etkinleştirme yüklü ve düzgün yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="15ca1-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="15ca1-125">Daha fazla bilgi için [nasıl yapılır: WCF etkinleştirme bileşenlerini yükleme ve yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="15ca1-125">For more information, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="15ca1-126">Bir WCF hizmeti, kullanan olan HTTP olmayan etkinleştirme için oluşturma</span><span class="sxs-lookup"><span data-stu-id="15ca1-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  
 <span data-ttu-id="15ca1-127">Yükleme ve WAS'ta yapılandırma adımlarını gerçekleştirdikten sonra (bkz [nasıl yapılır: Yükleme ve yapılandırma WCF etkinleştirme bileşenlerini](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), bir hizmetin WAS etkinleştirme IIS'de barındırılan bir hizmet yapılandırmaya benzer için yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="15ca1-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="15ca1-128">WAS etkinleştirilmiş WCF hizmeti oluşturma hakkında ayrıntılı yönergeler için bkz: [nasıl yapılır: Was'ta WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span><span class="sxs-lookup"><span data-stu-id="15ca1-128">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15ca1-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15ca1-129">See also</span></span>

- [<span data-ttu-id="15ca1-130">Windows İşlem Etkinleştirme Hizmetinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="15ca1-130">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)
- [<span data-ttu-id="15ca1-131">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="15ca1-131">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
