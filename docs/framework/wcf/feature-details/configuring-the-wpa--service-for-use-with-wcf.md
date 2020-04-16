---
title: Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 86e50b80d84479ca32b3d4d1fe3f205983640c76
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464163"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="c773a-102">Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c773a-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>
<span data-ttu-id="c773a-103">Bu konu, WINDOWS İletişim Vakfı (WCF) hizmetlerini barındırmak için Windows Vista'da Windows İşlem Etkinleştirme Hizmeti 'ni (WAS olarak da bilinir) ayarlamak için gereken adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="c773a-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="c773a-104">Aşağıdaki bölümlerde bu yapılandırma için adımlar sıralar:</span><span class="sxs-lookup"><span data-stu-id="c773a-104">The following sections outline the steps for this configuration:</span></span>  
  
- <span data-ttu-id="c773a-105">WCF etkinleştirme bileşenlerinin yüklenmesini (veya yüklenmesini onaylayın) gerekli.</span><span class="sxs-lookup"><span data-stu-id="c773a-105">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
- <span data-ttu-id="c773a-106">Kullanmak istediğiniz ağ protokolü bağlayıcıları içeren bir WAS sitesi oluşturun veya varolan bir siteye yeni bir protokol bağlayıcısı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c773a-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
- <span data-ttu-id="c773a-107">Hizmetlerinizi barındıracak ve bu uygulamanın gerekli ağ protokollerini kullanmasını sağlamak için bir uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c773a-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
- <span data-ttu-id="c773a-108">HTTP olmayan bir bitiş noktasını ortaya çıkaran bir WCF hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c773a-108">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="c773a-109">Bir Siteyi HTTP olmayan bağlamalarla yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c773a-109">Configuring a Site with Non-HTTP bindings</span></span>  
 <span data-ttu-id="c773a-110">WAS ile non-HTTP bağlama kullanmak için, site bağlama WAS yapılandırmasına eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c773a-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="c773a-111">WAS için yapılandırma deposu %windir%\system32\inetsrv\config dizininde bulunan applicationHost.config dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="c773a-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="c773a-112">Bu yapılandırma deposu hem WAS hem de IIS 7.0 tarafından paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="c773a-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="c773a-113">applicationHost.config herhangi bir standart metin düzenleyicisi (Not Defteri gibi) ile açılabilir bir XML metin dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="c773a-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="c773a-114">Ancak, IIS 7.0 komut satırı yapılandırma aracı (appcmd.exe) non-HTTP site bağlamaları eklemek için tercih edilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="c773a-114">However, the IIS 7.0 command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="c773a-115">Aşağıdaki komut appcmd.exe kullanarak varsayılan Web sitesine bir net.tcp sitesi bağlama ekler (bu komut tek bir satır olarak girilir).</span><span class="sxs-lookup"><span data-stu-id="c773a-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="c773a-116">Bu komut, applicationHost.config dosyasına aşağıda belirtilen satırı ekleyerek varsayılan Web sitesine yeni net.tcp bağlama ekler.</span><span class="sxs-lookup"><span data-stu-id="c773a-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="c773a-117">Bir Uygulamanın HTTP Dışı Protokolleri Kullanmasını Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="c773a-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  
 <span data-ttu-id="c773a-118">Tek tek ağ protokollerini uygulama düzeyinde etkinleştirebilir veya devre dışı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c773a-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="c773a-119">Aşağıdaki komut, `Default Web Site`'de çalışan bir uygulama için HEM HTTP hem de net.tcp protokollerinin nasıl etkinleştirilen gösteriş olduğunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="c773a-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="c773a-120">Etkin protokollerin listesi applicationDefaults> \<sitenin XML yapılandırmasının ApplicationHost.config depolanan öğesi ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c773a-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="c773a-121">ApplicationHost.config aşağıdaki XML kodu hem HTTP ve non-HTTP protokolleri bağlı bir site göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="c773a-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="c773a-122">HTTP olmayan protokolleri desteklemek için gereken ek yapılandırma açıklamalarla birlikte çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c773a-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
      <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
      </application>  
      <bindings>  
            <!-- The following two lines are added by the command. -->
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
      <!-- The following line is inserted by the command. -->
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 <span data-ttu-id="c773a-123">Bir hizmeti HTTP dışı etkinleştirme için WAS'ı kullanarak etkinleştirmeye çalışırsanız ve WAS'ı yüklemediyseniz ve yapılandırmadıysanız aşağıdaki hatayı görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c773a-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="c773a-124">Bu hatayı görürseniz, HTTP'siz Etkinleştirme için WAS'ın düzgün şekilde yüklendiğinden ve yapılandırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="c773a-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="c773a-125">Daha fazla bilgi için [bkz: WCF Etkinleştirme Bileşenlerini Yükleyin ve Yapılandırın.](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)</span><span class="sxs-lookup"><span data-stu-id="c773a-125">For more information, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="c773a-126">HTTP dışı etkinleştirme için WAS kullanan bir WCF Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c773a-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  
 <span data-ttu-id="c773a-127">WAS'ı yüklemek ve yapılandırmak için adımları gerçekleştirdiğinizde [(bkz. WCF Etkinleştirme Bileşenlerini Nasıl Yükleyin ve Yapılandırın),](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)etkinleştirme için WAS'ı kullanacak bir hizmeti yapılandırmak, IIS'de barındırılan bir hizmeti yapılandırmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="c773a-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="c773a-128">WAS tarafından etkinleştirilen bir WCF hizmeti oluşturma yla ilgili ayrıntılı talimatlar için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)</span><span class="sxs-lookup"><span data-stu-id="c773a-128">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c773a-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c773a-129">See also</span></span>

- [<span data-ttu-id="c773a-130">Windows İşlem Etkinleştirme Hizmetinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="c773a-130">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)
- <span data-ttu-id="c773a-131">[Windows Server App Kumaş Barındırma Özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c773a-131">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
