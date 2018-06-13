---
title: Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 3a4d771c3f2d5e7e6ec4fd6a1e229548e063a6d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489774"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="36f26-102">Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="36f26-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>
<span data-ttu-id="36f26-103">Bu konuda, Windows İşlem Etkinleştirme Hizmeti (WAS olarak da bilinir) için gerekli adımlar açıklanmaktadır [!INCLUDE[wv](../../../../includes/wv-md.md)] Windows Communication Foundation (WCF) barındırmak için HTTP üzerinden iletişim kurmazlar Hizmetleri protokolleri ağ.</span><span class="sxs-lookup"><span data-stu-id="36f26-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in [!INCLUDE[wv](../../../../includes/wv-md.md)] to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="36f26-104">Aşağıdaki bölümlerde bu yapılandırma için adımlar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="36f26-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="36f26-105">Yükleme (veya yüklemesini onaylamak) gerekli WCF etkinleştirme bileşenlerini.</span><span class="sxs-lookup"><span data-stu-id="36f26-105">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
-   <span data-ttu-id="36f26-106">Kullanmak istediğiniz ağ protokolü bağlamaları ile WAS site oluşturun veya varolan bir site için yeni bir protokol bağlama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="36f26-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
-   <span data-ttu-id="36f26-107">Hizmetlerinizin barındırmak ve gerekli ağ protokolleri kullanmak bu uygulamayı etkinleştirmek için bir uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="36f26-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
-   <span data-ttu-id="36f26-108">Bir HTTP olmayan uç noktasını kullanıma sunar bir WCF Hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="36f26-108">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="36f26-109">Bir Site ile HTTP olmayan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="36f26-109">Configuring a Site with Non-HTTP bindings</span></span>  
 <span data-ttu-id="36f26-110">Bir HTTP olmayan bağlama WAS ile kullanmak için site bağlaması için WAS yapılandırma eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="36f26-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="36f26-111">WAS yapılandırma deposu %windir%\system32\inetsrv\config dizininde bulunan applicationHost.config dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="36f26-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="36f26-112">Bu yapılandırma deposu WAS ve IIS 7.0 tarafından paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="36f26-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="36f26-113">applicationHost.config herhangi bir standart metin düzenleyicisi (Not Defteri gibi) ile açılmış bir XML metin dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="36f26-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="36f26-114">Ancak, [!INCLUDE[iisver](../../../../includes/iisver-md.md)] komut satırı yapılandırma aracını (appcmd.exe) olan HTTP olmayan site bağlamaları eklemek için tercih edilen yol.</span><span class="sxs-lookup"><span data-stu-id="36f26-114">However, the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="36f26-115">Aşağıdaki komutu (Bu komutu tek bir satır olarak girilir) appcmd.exe kullanarak varsayılan Web sitesi net.tcp site bağlaması ekler.</span><span class="sxs-lookup"><span data-stu-id="36f26-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="36f26-116">Bu komut, aşağıda applicationHost.config dosyasında belirtilen satırı ekleyerek, varsayılan Web sitesine yeni net.tcp bağlama ekler.</span><span class="sxs-lookup"><span data-stu-id="36f26-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="36f26-117">HTTP olmayan protokolleri kullanmak üzere bir uygulama etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="36f26-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  
 <span data-ttu-id="36f26-118">Etkinleştirmek veya tek tek ağ protocolsat uygulama düzeyinde devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36f26-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="36f26-119">Aşağıdaki komut, çalışan bir uygulama için hem HTTP hem de net.tcp protokollerini etkinleştirmek verilmektedir `Default Web Site`.</span><span class="sxs-lookup"><span data-stu-id="36f26-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="36f26-120">Etkin protokoller listesinde de ayarlanabilir \<applicationDefaults > ApplicationHost.config dosyasında depolanan sitenin XML yapılandırma öğesidir.</span><span class="sxs-lookup"><span data-stu-id="36f26-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="36f26-121">Aşağıdaki XML kodunu applicationHost.config öğesinden hem HTTP hem de HTTP olmayan protokolleri bağlı bir site gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="36f26-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="36f26-122">HTTP olmayan protokolleri desteklemek için gereken ek yapılandırma yorumlarla belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="36f26-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
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
  
 <span data-ttu-id="36f26-123">Aşağıdaki hata için HTTP olmayan etkinleştirme WAS kullanarak bir hizmet etkinleştirmeyi dener ve yüklenmediğinde veya WAS yapılandırılmış görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="36f26-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```Output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="36f26-124">WAS için olun bu hatayı görürseniz HTTP olmayan etkinleştirme yüklenmeli ve düzgün şekilde yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="36f26-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="36f26-125">Daha fazla bilgi için bkz: [nasıl yapılır: yükleme ve yapılandırma WCF etkinleştirme bileşenlerini](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="36f26-125">For more information, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="36f26-126">Bir WCF Hizmeti o kullanır, HTTP olmayan etkinleştirme için oluşturma</span><span class="sxs-lookup"><span data-stu-id="36f26-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  
 <span data-ttu-id="36f26-127">Yükleme ve WAS yapılandırma adımlarını gerçekleştirdikten sonra (bkz [nasıl yapılır: yükleme ve yapılandırma WCF etkinleştirme bileşenlerini](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), bir hizmetin WAS etkinleştirme IIS'de barındırılan bir hizmet yapılandırmaya benzer için yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="36f26-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="36f26-128">WAS etkinleştirilmiş WCF hizmeti oluşturma hakkında ayrıntılı yönergeler için bkz: [nasıl yapılır: bir WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span><span class="sxs-lookup"><span data-stu-id="36f26-128">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36f26-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36f26-129">See Also</span></span>  
 [<span data-ttu-id="36f26-130">Windows İşlem Etkinleştirme Hizmetinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="36f26-130">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)  
 [<span data-ttu-id="36f26-131">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="36f26-131">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
