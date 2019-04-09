---
title: 'Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: bcd725963986d8a70584409e1ef15c42f04f0033
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199225"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="7b960-102">Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7b960-102">How to: Install and Configure WCF Activation Components</span></span>
<span data-ttu-id="7b960-103">Bu konuda Windows İşlem Etkinleştirme Hizmeti (WAS olarak da bilinir) ' için gereken adımları açıklar [!INCLUDE[wv](../../../../includes/wv-md.md)] Windows Communication Foundation (WCF) barındırmak için HTTP üzerinden iletişim kurmazlar Hizmetleri protokolleri ağ.</span><span class="sxs-lookup"><span data-stu-id="7b960-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on [!INCLUDE[wv](../../../../includes/wv-md.md)] to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="7b960-104">Aşağıdaki bölümlerde, bu yapılandırmanın adımları özetlemektedir:</span><span class="sxs-lookup"><span data-stu-id="7b960-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="7b960-105">Yükleme (veya yüklenmesini onaylayın) WCF etkinleştirme bileşenlerini.</span><span class="sxs-lookup"><span data-stu-id="7b960-105">Install (or confirm the installation of) the WCF activation components.</span></span>  
  
-   <span data-ttu-id="7b960-106">WAS olmayan HTTP protokolü destekleyecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="7b960-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="7b960-107">Aşağıdaki yordam yapılandırır [!INCLUDE[wv](../../../../includes/wv-md.md)] TCP Etkinleştirmesi için.</span><span class="sxs-lookup"><span data-stu-id="7b960-107">The following procedure configures [!INCLUDE[wv](../../../../includes/wv-md.md)] for TCP activation.</span></span>  
  
 <span data-ttu-id="7b960-108">Yükleme ve yapılandırma WAS gördükten sonra [nasıl yapılır: Was'ta WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) yordamları WAS kullanan bir HTTP olmayan uç noktasını kullanıma sunan bir WCF hizmeti oluşturma.</span><span class="sxs-lookup"><span data-stu-id="7b960-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="7b960-109">WCF HTTP olmayan etkinleştirme bileşenlerini yükleme</span><span class="sxs-lookup"><span data-stu-id="7b960-109">To install the WCF non-HTTP activation components</span></span>  
  
1.  <span data-ttu-id="7b960-110">Tıklayın **Başlat** düğmesine ve ardından **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="7b960-110">Click the **Start** button, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="7b960-111">Tıklayın **programlar**ve ardından **programlar ve Özellikler**.</span><span class="sxs-lookup"><span data-stu-id="7b960-111">Click **Programs**, and then click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="7b960-112">Üzerinde **görevleri** menüsünde tıklatın **kapatma Windows özelliklerini aç veya Kapat**.</span><span class="sxs-lookup"><span data-stu-id="7b960-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>  
  
4.  <span data-ttu-id="7b960-113">Bulma [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] düğümünü seçin ve genişletin.</span><span class="sxs-lookup"><span data-stu-id="7b960-113">Find the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] node, select and then expand it.</span></span>  
  
5.  <span data-ttu-id="7b960-114">Seçin **WCF Http olmayan etkinleştirme bileşenlerini** kutusuna ve bu ayarı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="7b960-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="7b960-115">WAS TCP etkinleştirilmesini destekleyecek şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="7b960-115">To configure the WAS to support TCP activation</span></span>  
  
1.  <span data-ttu-id="7b960-116">NET.TCP etkinleştirmeyi desteklemek için varsayılan Web sitesi ilk net.tcp bağlantı noktasına bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b960-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="7b960-117">İle birlikte yüklenen Appcmd.exe kullanarak bunu yapabilirsiniz [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Yönetimi araç.</span><span class="sxs-lookup"><span data-stu-id="7b960-117">You can do this by using Appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="7b960-118">Bir yönetici düzeyinde komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7b960-118">In an administrator-level Command Prompt window, run the following command.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="7b960-119">Tek metin satırı komutudur.</span><span class="sxs-lookup"><span data-stu-id="7b960-119">This command is a single line of text.</span></span> <span data-ttu-id="7b960-120">Bu komut, varsayılan Web sitesine herhangi bir ana bilgisayar adı ile 808 numaralı TCP bağlantı noktasını dinleyen bir net.tcp site bağlaması ekler.</span><span class="sxs-lookup"><span data-stu-id="7b960-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>  
  
2.  <span data-ttu-id="7b960-121">Bir sitedeki tüm uygulamaları genel net.tcp bağlama paylaşsa da her uygulama net.tcp destek ayrı ayrı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b960-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="7b960-122">Uygulama için NET.TCP etkinleştirmek için bir yönetici düzeyinde komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7b960-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="7b960-123">Tek metin satırı komutudur.</span><span class="sxs-lookup"><span data-stu-id="7b960-123">This command is a single line of text.</span></span> <span data-ttu-id="7b960-124">Bu komut etkinleştirir /\<*WCF uygulaması*> her ikisi de kullanılarak erişilecektir uygulama `http://localhost/<WCF Application>` ve `net.tcp://localhost/<WCF Application>`.</span><span class="sxs-lookup"><span data-stu-id="7b960-124">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>
  
     <span data-ttu-id="7b960-125">Eklediğiniz net.tcp site bağlaması için bu örnek kaldırın.</span><span class="sxs-lookup"><span data-stu-id="7b960-125">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="7b960-126">Bir kolaylık olarak örnek dizinde yer RemoveNetTcpSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki iki adımı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7b960-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="7b960-127">NET.TCP, bir yönetici düzeyinde komut istemi penceresinde aşağıdaki komutu çalıştırarak etkin protokoller listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="7b960-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="7b960-128">Tek metin satırı komutudur.</span><span class="sxs-lookup"><span data-stu-id="7b960-128">This command is a single line of text.</span></span>  
  
    2.  <span data-ttu-id="7b960-129">Net.tcp site bağlaması, yükseltilmiş bir komut istemi penceresinde aşağıdaki komutu çalıştırarak kaldırın:</span><span class="sxs-lookup"><span data-stu-id="7b960-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="7b960-130">Tek metin satırı komutudur.</span><span class="sxs-lookup"><span data-stu-id="7b960-130">This command is a single line of text.</span></span>  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="7b960-131">NET.TCP etkin protokoller listesinden kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="7b960-131">To remove net.tcp from the list of enabled protocols</span></span>  
  
1.  <span data-ttu-id="7b960-132">NET.TCP etkin protokoller listesinden kaldırmak için bir yönetici düzeyinde komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7b960-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="7b960-133">Tek metin satırı komutudur.</span><span class="sxs-lookup"><span data-stu-id="7b960-133">This command is a single line of text.</span></span>  
  
### <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="7b960-134">Net.tcp site bağlaması kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="7b960-134">To remove the net.tcp site binding</span></span>  
  
1.  <span data-ttu-id="7b960-135">Bağlama net.tcp siteyi kaldırmak için bir yönetici düzeyinde komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7b960-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="7b960-136">Tek metin satırı komutudur.</span><span class="sxs-lookup"><span data-stu-id="7b960-136">This command is a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b960-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b960-137">See also</span></span>

- [<span data-ttu-id="7b960-138">TCP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="7b960-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [<span data-ttu-id="7b960-139">MSMQ Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="7b960-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)
- [<span data-ttu-id="7b960-140">NamedPipe Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="7b960-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)
- [<span data-ttu-id="7b960-141">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="7b960-141">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
