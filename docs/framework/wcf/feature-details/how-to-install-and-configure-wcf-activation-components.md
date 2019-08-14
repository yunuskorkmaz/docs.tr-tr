---
title: 'Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: aed6cb71ac3ccd7af5423cdb8ccc43133bbe5337
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972037"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="55f1a-102">Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="55f1a-102">How to: Install and Configure WCF Activation Components</span></span>

<span data-ttu-id="55f1a-103">Bu konuda, http ağ protokolleri üzerinden iletişim kurmayan Windows Communication Foundation (WCF) hizmetlerini barındırmak [!INCLUDE[wv](../../../../includes/wv-md.md)] için Windows işlem etkinleştirme hizmeti 'ni (was olarak da bilinir) ayarlamak için gereken adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55f1a-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on [!INCLUDE[wv](../../../../includes/wv-md.md)] to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="55f1a-104">Aşağıdaki bölümlerde bu yapılandırma için adımlar ana hatlarıyla verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="55f1a-104">The following sections outline the steps for this configuration:</span></span>

- <span data-ttu-id="55f1a-105">WCF etkinleştirme bileşenlerini yükleme (veya yüklemesini onaylama).</span><span class="sxs-lookup"><span data-stu-id="55f1a-105">Install (or confirm the installation of) the WCF activation components.</span></span>

- <span data-ttu-id="55f1a-106">' İ HTTP olmayan bir protokolü destekleyecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="55f1a-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="55f1a-107">Aşağıdaki yordam TCP Etkinleştirmesi [!INCLUDE[wv](../../../../includes/wv-md.md)] için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="55f1a-107">The following procedure configures [!INCLUDE[wv](../../../../includes/wv-md.md)] for TCP activation.</span></span>

<span data-ttu-id="55f1a-108">WAS yükledikten ve yapılandırdıktan sonra bkz [. nasıl yapılır: ' De bir WCF hizmeti barındırın, was kullanan HTTP olmayan bir uç noktasını kullanıma sunan bir WCF hizmeti oluşturma yordamlarına was idi](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) .</span><span class="sxs-lookup"><span data-stu-id="55f1a-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>

## <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="55f1a-109">WCF HTTP olmayan etkinleştirme bileşenlerini yüklemek için</span><span class="sxs-lookup"><span data-stu-id="55f1a-109">To install the WCF non-HTTP activation components</span></span>

1. <span data-ttu-id="55f1a-110">**Başlat** düğmesine tıklayın ve ardından **Denetim Masası**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="55f1a-110">Click the **Start** button, and then click **Control Panel**.</span></span>

2. <span data-ttu-id="55f1a-111">**Programlar**' a ve ardından **Programlar ve Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="55f1a-111">Click **Programs**, and then click **Programs and Features**.</span></span>

3. <span data-ttu-id="55f1a-112">**Görevler** menüsünde, **Windows özelliklerini aç veya kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="55f1a-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>

4. <span data-ttu-id="55f1a-113">WinFX düğümünü bulun, seçin ve genişletin.</span><span class="sxs-lookup"><span data-stu-id="55f1a-113">Find the WinFX node, select and then expand it.</span></span>

5. <span data-ttu-id="55f1a-114">**WCF HTTP olmayan etkinleştirme bileşenleri** kutusunu seçin ve ayarı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="55f1a-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>

## <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="55f1a-115">Yapılandırmasını TCP etkinleştirmesini destekleyecek şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="55f1a-115">To configure the WAS to support TCP activation</span></span>

1. <span data-ttu-id="55f1a-116">Net. TCP etkinleştirmesini desteklemek için, önce varsayılan Web sitesinin bir net. TCP bağlantı noktasına bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="55f1a-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="55f1a-117">Bunu, IIS 7,0 yönetim araç takımı ile yüklenen appcmd. exe ' yi kullanarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f1a-117">You can do this by using Appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="55f1a-118">Yönetici düzeyinde bir komut Istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="55f1a-118">In an administrator-level Command Prompt window, run the following command.</span></span>

    ```
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="55f1a-119">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="55f1a-119">This command is a single line of text.</span></span> <span data-ttu-id="55f1a-120">Bu komut, TCP bağlantı noktası 808 ' de dinleme yapan varsayılan Web sitesine bir net. TCP site bağlaması ekleyerek herhangi bir ana bilgisayar adı ekler.</span><span class="sxs-lookup"><span data-stu-id="55f1a-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>

2. <span data-ttu-id="55f1a-121">Bir sitedeki tüm uygulamalar ortak bir net. TCP bağlamasını paylaşır, ancak her uygulama net. TCP desteğini tek tek etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="55f1a-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="55f1a-122">Uygulama için net. TCP 'yi etkinleştirmek üzere yönetici düzeyinde bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="55f1a-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>

    ```
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > <span data-ttu-id="55f1a-123">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="55f1a-123">This command is a single line of text.</span></span> <span data-ttu-id="55f1a-124">Bu\<komut/*WCF uygulama*> uygulamasına hem hem `http://localhost/<WCF Application>` `net.tcp://localhost/<WCF Application>`de kullanılarak erişilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="55f1a-124">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>

     <span data-ttu-id="55f1a-125">Bu örnek için eklemiş olduğunuz net. TCP site bağlamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="55f1a-125">Remove the net.tcp site binding you added for this sample.</span></span>

     <span data-ttu-id="55f1a-126">Kolaylık olması halinde, örnek dizinde bulunan RemoveNetTcpSiteBinding. cmd adlı bir toplu iş dosyasında aşağıdaki iki adım uygulanır.</span><span class="sxs-lookup"><span data-stu-id="55f1a-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="55f1a-127">Yönetici düzeyinde bir komut Istemi penceresinde aşağıdaki komutu çalıştırarak, etkin protokoller listesinden net. TCP ' i kaldırın.</span><span class="sxs-lookup"><span data-stu-id="55f1a-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>

        ```
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="55f1a-128">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="55f1a-128">This command is a single line of text.</span></span>

    2. <span data-ttu-id="55f1a-129">Yükseltilmiş bir komut Istemi penceresinde aşağıdaki komutu çalıştırarak net. TCP site bağlamasını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="55f1a-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>

        ```
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="55f1a-130">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="55f1a-130">This command is a single line of text.</span></span>

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="55f1a-131">Etkin protokoller listesinden net. TCP 'yi kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="55f1a-131">To remove net.tcp from the list of enabled protocols</span></span>

1. <span data-ttu-id="55f1a-132">Etkin protokoller listesinden net. TCP ' yi kaldırmak için, yönetici düzeyinde bir komut Istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="55f1a-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>

    ```
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > <span data-ttu-id="55f1a-133">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="55f1a-133">This command is a single line of text.</span></span>

## <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="55f1a-134">Net. TCP site bağlamasını kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="55f1a-134">To remove the net.tcp site binding</span></span>

1. <span data-ttu-id="55f1a-135">Net. TCP site bağlamasını kaldırmak için aşağıdaki komutu yönetici düzeyinde bir komut Istemi penceresinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="55f1a-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>

    ```
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="55f1a-136">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="55f1a-136">This command is a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="55f1a-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55f1a-137">See also</span></span>

- [<span data-ttu-id="55f1a-138">TCP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="55f1a-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [<span data-ttu-id="55f1a-139">MSMQ Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="55f1a-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)
- [<span data-ttu-id="55f1a-140">NamedPipe Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="55f1a-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)
- [<span data-ttu-id="55f1a-141">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="55f1a-141">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
