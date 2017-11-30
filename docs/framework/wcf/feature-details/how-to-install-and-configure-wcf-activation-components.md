---
title: "Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77dec85ee12250080fc487d120749892a148ef17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="1fd82-102">Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1fd82-102">How to: Install and Configure WCF Activation Components</span></span>
<span data-ttu-id="1fd82-103">Bu konu Windows İşlem Etkinleştirme Hizmeti (WAS olarak da bilinir) ayarlamak için gereken adımları açıklar [!INCLUDE[wv](../../../../includes/wv-md.md)] ana bilgisayara [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ağ protokolleri HTTP üzerinden iletişim kurmazlar Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="1fd82-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on [!INCLUDE[wv](../../../../includes/wv-md.md)] to host [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="1fd82-104">Aşağıdaki bölümlerde bu yapılandırma için adımlar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1fd82-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="1fd82-105">Yükleme (veya yüklemesini onaylamak) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] etkinleştirme bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="1fd82-105">Install (or confirm the installation of) the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] activation components.</span></span>  
  
-   <span data-ttu-id="1fd82-106">Bir HTTP olmayan protokolünü destekleyen WAS yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="1fd82-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="1fd82-107">Aşağıdaki yordamda [!INCLUDE[wv](../../../../includes/wv-md.md)] TCP etkinleştirme için.</span><span class="sxs-lookup"><span data-stu-id="1fd82-107">The following procedure configures [!INCLUDE[wv](../../../../includes/wv-md.md)] for TCP activation.</span></span>  
  
 <span data-ttu-id="1fd82-108">Yükleme ve WAS yapılandırma gördükten sonra [nasıl yapılır: bir WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) oluşturmak için yordamlar için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet WAS kullanan bir HTTP olmayan uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="1fd82-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that exposes an non-HTTP endpoint that employs WAS.</span></span>  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="1fd82-109">WCF HTTP olmayan etkinleştirme bileşenlerini yüklemek için</span><span class="sxs-lookup"><span data-stu-id="1fd82-109">To install the WCF non-HTTP activation components</span></span>  
  
1.  <span data-ttu-id="1fd82-110">Tıklatın **Başlat** düğmesine tıklayın ve ardından **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="1fd82-110">Click the **Start** button, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="1fd82-111">Tıklatın **programları**ve ardından **programlar ve Özellikler**.</span><span class="sxs-lookup"><span data-stu-id="1fd82-111">Click **Programs**, and then click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="1fd82-112">Üzerinde **görevleri** menüsünde tıklatın **kapatma Windows özelliklerini aç veya Kapat**.</span><span class="sxs-lookup"><span data-stu-id="1fd82-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>  
  
4.  <span data-ttu-id="1fd82-113">Bul [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] düğümünü seçin ve genişletin.</span><span class="sxs-lookup"><span data-stu-id="1fd82-113">Find the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] node, select and then expand it.</span></span>  
  
5.  <span data-ttu-id="1fd82-114">Seçin **WCF Http olmayan etkinleştirme bileşenleri** kutusuna ve bu ayarı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1fd82-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="1fd82-115">WAS TCP etkinleştirilmesini destekleyecek şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="1fd82-115">To configure the WAS to support TCP activation</span></span>  
  
1.  <span data-ttu-id="1fd82-116">NET.TCP etkinleştirmeyi desteklemek için varsayılan Web sitesi ilk net.tcp bağlantı noktasına bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1fd82-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="1fd82-117">İle yüklenen Appcmd.exe kullanarak bunu yapabilirsiniz [!INCLUDE[iisver](../../../../includes/iisver-md.md)] yönetim araç takımı.</span><span class="sxs-lookup"><span data-stu-id="1fd82-117">You can do this by using Appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="1fd82-118">Bir yönetici düzeyi komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1fd82-118">In an administrator-level Command Prompt window, run the following command.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1fd82-119">Bu komut, metnin tek bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="1fd82-119">This command is a single line of text.</span></span> <span data-ttu-id="1fd82-120">Bu komut net.tcp site bağlaması herhangi bir ana bilgisayar adı ile 808 numaralı TCP bağlantı noktasını dinleme varsayılan Web sitesine ekler.</span><span class="sxs-lookup"><span data-stu-id="1fd82-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>  
  
2.  <span data-ttu-id="1fd82-121">Bir sitedeki tüm uygulamaları ortak net.tcp bağlama paylaşmak rağmen her uygulama net.tcp desteğini ayrı ayrı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fd82-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="1fd82-122">Uygulama için NET.TCP etkinleştirmek için bir yönetici düzeyi komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1fd82-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1fd82-123">Bu komut, metnin tek bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="1fd82-123">This command is a single line of text.</span></span> <span data-ttu-id="1fd82-124">Bu komut etkinleştirir /\<*WCF uygulaması*> hem http://localhost kullanılarak erişilmesi için uygulama*/\<WCF uygulaması >* ve net.tcp:// localhost /*\<WCF uygulaması >*.</span><span class="sxs-lookup"><span data-stu-id="1fd82-124">This command enables the /\<*WCF Application*> application to be accessed using both http://localhost*/\<WCF Application>* and net.tcp://localhost/*\<WCF Application>*.</span></span>  
  
     <span data-ttu-id="1fd82-125">Eklediğiniz net.tcp site bağlaması Bu örnek için kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1fd82-125">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="1fd82-126">Kolaylık, aşağıdaki iki adımdan örnek dizininde bulunan RemoveNetTcpSiteBinding.cmd adlı bir toplu iş dosyası uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1fd82-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="1fd82-127">NET.TCP, bir yönetici düzeyi komut istemi penceresinde aşağıdaki komutu çalıştırarak etkin protokoller listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1fd82-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="1fd82-128">Bu komut, metnin tek bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="1fd82-128">This command is a single line of text.</span></span>  
  
    2.  <span data-ttu-id="1fd82-129">Net.tcp site bağlaması, yükseltilmiş bir komut istemi penceresinde aşağıdaki komutu çalıştırarak kaldırın:</span><span class="sxs-lookup"><span data-stu-id="1fd82-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="1fd82-130">Bu komut, metnin tek bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="1fd82-130">This command is a single line of text.</span></span>  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="1fd82-131">NET.TCP etkin protokoller listesinden kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="1fd82-131">To remove net.tcp from the list of enabled protocols</span></span>  
  
1.  <span data-ttu-id="1fd82-132">NET.TCP etkin protokoller listesinden kaldırmak için bir yönetici düzeyi komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1fd82-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1fd82-133">Bu komut, metnin tek bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="1fd82-133">This command is a single line of text.</span></span>  
  
### <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="1fd82-134">Net.tcp site bağlaması kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="1fd82-134">To remove the net.tcp site binding</span></span>  
  
1.  <span data-ttu-id="1fd82-135">Bağlama net.tcp sitesini kaldırmak için yönetici düzeyi komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1fd82-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1fd82-136">Bu komut, metnin tek bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="1fd82-136">This command is a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fd82-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1fd82-137">See Also</span></span>  
 [<span data-ttu-id="1fd82-138">TCP etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1fd82-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [<span data-ttu-id="1fd82-139">MSMQ etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1fd82-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)  
 [<span data-ttu-id="1fd82-140">NamedPipe etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1fd82-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)  
 [<span data-ttu-id="1fd82-141">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="1fd82-141">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
