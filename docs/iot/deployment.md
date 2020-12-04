---
title: .NET uygulamalarını Raspberry PI 'ye dağıtma
description: .NET uygulamalarını Raspberry PI 'ye dağıtmayı öğrenin.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
ms.openlocfilehash: 4da558e2cdfc283d21f2a5497cb71dc746109614
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96590049"
---
# <a name="deploy-net-apps-to-raspberry-pi"></a><span data-ttu-id="f582d-103">.NET uygulamalarını Raspberry PI 'ye dağıtma</span><span class="sxs-lookup"><span data-stu-id="f582d-103">Deploy .NET apps to Raspberry Pi</span></span>

<span data-ttu-id="f582d-104">.NET uygulamalarının Raspberry PI 'ye dağıtılması, diğer platformlardan de aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f582d-104">Deployment of .NET apps to Raspberry Pi is identical to that of any other platform.</span></span> <span data-ttu-id="f582d-105">Uygulamanız, *kendi içinde* veya *çerçeveye bağımlı* Dağıtım modları olarak çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f582d-105">Your app can run as *self-contained* or *framework-dependent* deployment modes.</span></span> <span data-ttu-id="f582d-106">Her stratejinin avantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="f582d-106">There are advantages to each strategy.</span></span> <span data-ttu-id="f582d-107">Daha fazla bilgi için bkz. [.NET uygulama yayımlamaya genel bakış](../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="f582d-107">For more information, see [.NET application publishing overview](../core/deploying/index.md).</span></span>

## <a name="deploying-a-framework-dependent-app"></a><span data-ttu-id="f582d-108">Çerçeveye bağımlı uygulama dağıtma</span><span class="sxs-lookup"><span data-stu-id="f582d-108">Deploying a framework-dependent app</span></span>

<span data-ttu-id="f582d-109">Uygulamanızı çerçeveye bağlı bir uygulama olarak dağıtmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="f582d-109">To deploy your app as a framework-dependent app, complete the following steps:</span></span>

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. <span data-ttu-id="f582d-110">[DotNet-Install betiklerini](../core/tools/dotnet-install-script.md)kullanarak .net 'ı Raspberry PI 'ye yüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="f582d-110">Install .NET on the Raspberry Pi using the [dotnet-install scripts](../core/tools/dotnet-install-script.md).</span></span> <span data-ttu-id="f582d-111">Raspberry PI 'deki Bash isteminde aşağıdaki adımları uygulayın (yerel veya SSH):</span><span class="sxs-lookup"><span data-stu-id="f582d-111">Complete the following steps from a Bash prompt on the Raspberry Pi (local or SSH):</span></span>
    1. <span data-ttu-id="f582d-112">.NET yüklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f582d-112">Run the following command to install .NET:</span></span>

        ```bash
        curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin
        ```

        > [!NOTE]
        > <span data-ttu-id="f582d-113">Bu, en son sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f582d-113">This installs the latest version.</span></span> <span data-ttu-id="f582d-114">Belirli bir sürüme ihtiyacınız varsa, sonuna ekleyin `--version <VERSION>` , burada `<VERSION>` belirli derleme sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="f582d-114">If you need a specific version, add `--version <VERSION>` to the end, where `<VERSION>` is the specific build version.</span></span>

    1. <span data-ttu-id="f582d-115">Yol çözünürlüğünü basitleştirmek için bir `DOTNET_ROOT` ortam değişkeni ekleyin ve *. DotNet* dizinini `$PATH` aşağıdaki komutlarla ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f582d-115">To simplify path resolution, add a `DOTNET_ROOT` environment variable and add the *.dotnet* directory to `$PATH` with the following commands:</span></span>

        ```bash
        echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc
        echo 'export PATH=$PATH:$HOME/.dotnet' >> ~/.bashrc
        source ~/.bashrc
        ```

    1. <span data-ttu-id="f582d-116">Aşağıdaki komutla .NET yüklemesini doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="f582d-116">Verify the .NET installation with the following command:</span></span>

        ```dotnetcli
        dotnet --version
        ```

        <span data-ttu-id="f582d-117">Görüntülenmiş sürümü yüklediğiniz sürümle eşleştirdiğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="f582d-117">Verify the displayed version matches the version you installed.</span></span>

1. <span data-ttu-id="f582d-118">Geliştirme ortamına bağlı olarak uygulamayı geliştirme bilgisayarında aşağıdaki şekilde yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="f582d-118">Publish the app on the development computer as follows, depending on development environment.</span></span>
    - <span data-ttu-id="f582d-119">**Visual Studio** kullanıyorsanız, [uygulamayı yerel bir klasöre dağıtın](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="f582d-119">If using **Visual Studio**, [deploy the app to a local folder](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span></span> <span data-ttu-id="f582d-120">Yayımlamadan önce, yayımlama profili özetindeki **Düzenle** ' yi seçin ve **Ayarlar** sekmesini seçin. **Dağıtım modunun** *çerçeveye bağımlı* olarak ayarlandığından ve **hedef çalışma zamanının** *Taşınabilir* olarak ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f582d-120">Before publishing, select **Edit** in the publish profile summary and select the **Settings** tab. Ensure that **Deployment mode** is set to *Framework-dependent* and **Target runtime** is set to *Portable*.</span></span>
    - <span data-ttu-id="f582d-121">**.Net CLI** kullanıyorsanız, [DotNet Publish](../core/tools/dotnet-publish.md) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f582d-121">If using the **.NET CLI**, use the [dotnet publish](../core/tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="f582d-122">Ek bağımsız değişken gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f582d-122">No additional arguments are required.</span></span>

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. <span data-ttu-id="f582d-123">Raspberry PI 'deki Bash isteminde (yerel veya SSH) uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f582d-123">From a Bash prompt on the Raspberry Pi (local or SSH), run the app.</span></span> <span data-ttu-id="f582d-124">Bunu yapmak için, dağıtım klasörünü geçerli dizin olarak ayarlayın ve aşağıdaki komutu yürütün (burada *HelloWorld.dll* uygulamanın giriş noktasıdır):</span><span class="sxs-lookup"><span data-stu-id="f582d-124">To do this, set the deployment folder as the current directory and execute the following command (where *HelloWorld.dll* is the entry point of the app):</span></span>

    ```dotnetcli
    dotnet HelloWorld.dll
    ```

## <a name="deploying-a-self-contained-app"></a><span data-ttu-id="f582d-125">Kendi içinde uygulama dağıtma</span><span class="sxs-lookup"><span data-stu-id="f582d-125">Deploying a self-contained app</span></span>

<span data-ttu-id="f582d-126">Uygulamanızı kendi içinde bulunan bir uygulama olarak dağıtmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="f582d-126">To deploy your app as a self-contained app, complete the following steps:</span></span>

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. <span data-ttu-id="f582d-127">Geliştirme ortamına bağlı olarak uygulamayı geliştirme bilgisayarında aşağıdaki şekilde yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="f582d-127">Publish the app on the development computer as follows, depending on development environment.</span></span>
    - <span data-ttu-id="f582d-128">**Visual Studio** kullanıyorsanız, [uygulamayı yerel bir klasöre dağıtın](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="f582d-128">If using **Visual Studio**, [deploy the app to a local folder](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span></span> <span data-ttu-id="f582d-129">Yayımlamadan önce, yayımlama profili özetindeki **Düzenle** ' yi seçin ve **Ayarlar** sekmesini seçin. **Dağıtım modunun** *kendi içinde* ve **hedef çalışma zamanının** *Linux ARM* olarak ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f582d-129">Before publishing, select **Edit** in the publish profile summary and select the **Settings** tab. Ensure that **Deployment mode** is set to *Self-contained* and **Target runtime** is set to *linux-arm*.</span></span>
    - <span data-ttu-id="f582d-130">**.Net CLI** kullanıyorsanız, [DotNet Publish](../core/tools/dotnet-publish.md) komutunu `-r linux-arm` bağımsız değişkenle kullanın:</span><span class="sxs-lookup"><span data-stu-id="f582d-130">If using the **.NET CLI**, use the [dotnet publish](../core/tools/dotnet-publish.md) command with the `-r linux-arm` argument:</span></span>

        ```dotnetcli
        dotnet publish -r linux-arm
        ```

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. <span data-ttu-id="f582d-131">Raspberry PI 'deki Bash isteminde (yerel veya SSH) uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f582d-131">From a Bash prompt on the Raspberry Pi (local or SSH), run the app.</span></span> <span data-ttu-id="f582d-132">Bunu yapmak için, geçerli dizini dağıtım konumuna ayarlayın ve aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="f582d-132">To do this, set the current directory to the deployment location and complete the following steps:</span></span>
    1. <span data-ttu-id="f582d-133">Yürütülebilir *yürütme* iznini (burada `HelloWorld` yürütülebilir dosya adıdır) verir.</span><span class="sxs-lookup"><span data-stu-id="f582d-133">Give the executable *execute* permission (where `HelloWorld` is the executable file name).</span></span>

        ```bash
        chmod +x HelloWorld
        ```

    1. <span data-ttu-id="f582d-134">Yürütülebilir dosyayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f582d-134">Run the executable.</span></span>

        ```bash
        ./HelloWorld
        ```
