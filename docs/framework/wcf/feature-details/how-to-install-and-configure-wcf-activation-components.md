---
title: 'Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma'
description: Windows Vista 'da, HTTP üzerinden iletişim kurmayan WCF hizmetlerini barındırmak için Windows Işlem etkinleştirme hizmeti 'ni (WAS) ayarlamayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 085a69421f0aa7b763bd2222820ced4b4a7e1c81
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557872"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="a5539-103">Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a5539-103">How to: Install and Configure WCF Activation Components</span></span>

<span data-ttu-id="a5539-104">Bu konuda, Windows Vista 'da HTTP ağ protokolleri üzerinden iletişim kurmayan Windows Communication Foundation (WCF) hizmetlerini barındırmak için Windows Işlem etkinleştirme hizmeti 'ni (WAS olarak da bilinir) ayarlamak için gereken adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a5539-104">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="a5539-105">Aşağıdaki bölümlerde bu yapılandırma için adımlar ana hatlarıyla verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a5539-105">The following sections outline the steps for this configuration:</span></span>

- <span data-ttu-id="a5539-106">WCF etkinleştirme bileşenlerini yükleme (veya yüklemesini onaylama).</span><span class="sxs-lookup"><span data-stu-id="a5539-106">Install (or confirm the installation of) the WCF activation components.</span></span>

- <span data-ttu-id="a5539-107">' İ HTTP olmayan bir protokolü destekleyecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a5539-107">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="a5539-108">Aşağıdaki yordam, TCP Etkinleştirmesi için Windows Vista 'Yı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a5539-108">The following procedure configures Windows Vista for TCP activation.</span></span>

<span data-ttu-id="a5539-109">WAS 'yi yükledikten ve yapılandırdıktan sonra, ile ilgili HTTP olmayan bir uç nokta sunan bir WCF hizmeti oluşturma yordamları için bkz. [nasıl yapılır: ' de BIR WCF hizmetini barındırma](how-to-host-a-wcf-service-in-was.md) .</span><span class="sxs-lookup"><span data-stu-id="a5539-109">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>

## <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="a5539-110">WCF HTTP olmayan etkinleştirme bileşenlerini yüklemek için</span><span class="sxs-lookup"><span data-stu-id="a5539-110">To install the WCF non-HTTP activation components</span></span>

1. <span data-ttu-id="a5539-111">**Başlat** düğmesine tıklayın ve ardından **Denetim Masası**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a5539-111">Click the **Start** button, and then click **Control Panel**.</span></span>

2. <span data-ttu-id="a5539-112">**Programlar**' a ve ardından **Programlar ve Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a5539-112">Click **Programs**, and then click **Programs and Features**.</span></span>

3. <span data-ttu-id="a5539-113">**Görevler** menüsünde, **Windows özelliklerini aç veya kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a5539-113">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>

4. <span data-ttu-id="a5539-114">WinFX düğümünü bulun, seçin ve genişletin.</span><span class="sxs-lookup"><span data-stu-id="a5539-114">Find the WinFX node, select and then expand it.</span></span>

5. <span data-ttu-id="a5539-115">**WCF HTTP olmayan etkinleştirme bileşenleri** kutusunu seçin ve ayarı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a5539-115">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>

## <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="a5539-116">Yapılandırmasını TCP etkinleştirmesini destekleyecek şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="a5539-116">To configure the WAS to support TCP activation</span></span>

1. <span data-ttu-id="a5539-117">Net. TCP etkinleştirmesini desteklemek için, önce varsayılan Web sitesinin bir net. TCP bağlantı noktasına bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5539-117">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="a5539-118">Bunu, IIS 7,0 yönetim araç takımı ile yüklenen Appcmd.exe kullanarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5539-118">You can do this by using Appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="a5539-119">Yönetici düzeyinde bir komut Istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a5539-119">In an administrator-level Command Prompt window, run the following command.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="a5539-120">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="a5539-120">This command is a single line of text.</span></span> <span data-ttu-id="a5539-121">Bu komut, TCP bağlantı noktası 808 ' de dinleme yapan varsayılan Web sitesine bir net. TCP site bağlaması ekleyerek herhangi bir ana bilgisayar adı ekler.</span><span class="sxs-lookup"><span data-stu-id="a5539-121">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>

2. <span data-ttu-id="a5539-122">Bir sitedeki tüm uygulamalar ortak bir net. TCP bağlamasını paylaşır, ancak her uygulama net. TCP desteğini tek tek etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="a5539-122">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="a5539-123">Uygulama için net. TCP 'yi etkinleştirmek üzere yönetici düzeyinde bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a5539-123">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > <span data-ttu-id="a5539-124">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="a5539-124">This command is a single line of text.</span></span> <span data-ttu-id="a5539-125">Bu komut,/ \<*WCF Application*> uygulamasına hem hem de kullanılarak erişilmesini sağlar `http://localhost/<WCF Application>` `net.tcp://localhost/<WCF Application>` .</span><span class="sxs-lookup"><span data-stu-id="a5539-125">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>

     <span data-ttu-id="a5539-126">Bu örnek için eklemiş olduğunuz net. TCP site bağlamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="a5539-126">Remove the net.tcp site binding you added for this sample.</span></span>

     <span data-ttu-id="a5539-127">Kolaylık olması halinde, örnek dizinde bulunan RemoveNetTcpSiteBinding. cmd adlı bir toplu iş dosyasında aşağıdaki iki adım uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a5539-127">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="a5539-128">Yönetici düzeyinde bir komut Istemi penceresinde aşağıdaki komutu çalıştırarak, etkin protokoller listesinden net. TCP ' i kaldırın.</span><span class="sxs-lookup"><span data-stu-id="a5539-128">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="a5539-129">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="a5539-129">This command is a single line of text.</span></span>

    2. <span data-ttu-id="a5539-130">Yükseltilmiş bir komut Istemi penceresinde aşağıdaki komutu çalıştırarak net. TCP site bağlamasını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="a5539-130">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="a5539-131">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="a5539-131">This command is a single line of text.</span></span>

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="a5539-132">Etkin protokoller listesinden net. TCP 'yi kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="a5539-132">To remove net.tcp from the list of enabled protocols</span></span>

1. <span data-ttu-id="a5539-133">Etkin protokoller listesinden net. TCP ' yi kaldırmak için, yönetici düzeyinde bir komut Istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a5539-133">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > <span data-ttu-id="a5539-134">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="a5539-134">This command is a single line of text.</span></span>

## <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="a5539-135">Net. TCP site bağlamasını kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="a5539-135">To remove the net.tcp site binding</span></span>

1. <span data-ttu-id="a5539-136">Net. TCP site bağlamasını kaldırmak için aşağıdaki komutu yönetici düzeyinde bir komut Istemi penceresinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a5539-136">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="a5539-137">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="a5539-137">This command is a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5539-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5539-138">See also</span></span>

- [<span data-ttu-id="a5539-139">TCP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a5539-139">TCP Activation</span></span>](../samples/tcp-activation.md)
- [<span data-ttu-id="a5539-140">MSMQ Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a5539-140">MSMQ Activation</span></span>](../samples/msmq-activation.md)
- [<span data-ttu-id="a5539-141">NamedPipe Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a5539-141">NamedPipe Activation</span></span>](../samples/namedpipe-activation.md)
- <span data-ttu-id="a5539-142">[Windows Server App Fabric barındırma özellikleri](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a5539-142">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
