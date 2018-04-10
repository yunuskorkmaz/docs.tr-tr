---
title: .NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yükleme
description: .NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yüklemek öğrenin.
author: rlander
ms.author: mairaw
ms.date: 03/30/2018
ms.topic: article
ms.prod: .net-framework
ms.workload:
- dotnet
ms.openlocfilehash: 09c4f81da76bb6608c3e579c442cf686ffab1688
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="52957-103">.NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yükleme</span><span class="sxs-lookup"><span data-stu-id="52957-103">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="52957-104">Windows 10, Windows 8.1 ve Windows 8 uygulama çalıştırmak için .NET Framework 3.5 gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="52957-104">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="52957-105">Önceki Windows sürümleri için bu yönergeleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52957-105">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="52957-106">İsteğe bağlı olarak .NET Framework 3.5 yükleyin</span><span class="sxs-lookup"><span data-stu-id="52957-106">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="52957-107">.NET Framework 3.5 gerektiren bir uygulama çalıştırmayı denerseniz aşağıdaki yapılandırma iletişim kutusu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52957-107">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="52957-108">Seçin **bu özelliği yüklemek** .NET Framework 3.5 etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="52957-108">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="52957-109">Bu seçenek, bir Internet bağlantısı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="52957-109">This option requires an Internet connection.</span></span>

![.NET framework yükleme iletişim kutusu](./media/dotnet-framework-installation-dialog.jpg)

### <a name="why-am-i-getting-this-pop-up"></a><span data-ttu-id="52957-111">Neden bu açılır alıyorum?</span><span class="sxs-lookup"><span data-stu-id="52957-111">Why am I getting this pop-up?</span></span>

<span data-ttu-id="52957-112">.NET Framework Microsoft tarafından oluşturulan ve uygulamaları çalıştırmak için bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="52957-112">The .NET Framework is created by Microsoft and provides an environment for running applications.</span></span> <span data-ttu-id="52957-113">Farklı sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="52957-113">There are different versions available.</span></span> <span data-ttu-id="52957-114">Birçok şirket .NET Framework kullanılarak çalıştırmak için uygulamalarını geliştirmek ve belirli bir sürümü bu uygulamaları hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52957-114">Many companies develop their apps to run using the .NET Framework, and these apps target a specific version.</span></span> <span data-ttu-id="52957-115">Bu açılır pencere görürseniz, .NET Framework sürüm 3.5 gerektiren bir uygulamayı çalıştırmak çalıştığınız, ancak bu sürümü, sisteminizde yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="52957-115">If you see this pop-up, you're trying to run an application that requires the .NET Framework version 3.5, but that version is not installed on your system.</span></span>

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="52957-116">Denetim Masası'ndaki .NET Framework 3.5 etkinleştir</span><span class="sxs-lookup"><span data-stu-id="52957-116">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="52957-117">.NET Framework 3.5 Windows Denetim Masası'ndan etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52957-117">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="52957-118">Bu seçenek, bir Internet bağlantısı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="52957-118">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="52957-119">Windows Windows tuşuna ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) klavyenizde "Windows özellikleri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="52957-119">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="52957-120">**Kapatma Windows özelliklerini aç veya Kapat** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="52957-120">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="52957-121">Seçin **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir)** onay kutusu, select **Tamam**ve istenirse, bilgisayarınızı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="52957-121">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![.NET ile Denetim Masası'nı yükleme](./media/dotnet-control-panel.png)

   <span data-ttu-id="52957-123">Alt öğeler için seçmeniz gerekmez **Windows Communication Foundation (WCF) HTTP etkinleştirmesi** ve **Windows Communication Foundation (WCF) HTTP olmayan etkinleştirme** geliştiriciyseniz sürece veya Bu işlevselliği gerektiren Sunucu Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="52957-123">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a><span data-ttu-id="52957-124">.NET Framework 3.5 yükleme sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="52957-124">Troubleshoot the installation of the .NET Framework 3.5</span></span>

<span data-ttu-id="52957-125">Yükleme sırasında hata 0x800f0906, 0x800f0907, 0x800f081f veya 0x800F0922 bakın; bu durumda, karşılaşabileceğiniz [.NET Framework 3.5 yükleme hatası: 0x800f0906, 0x800f0907 veya 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) bunları gidermek nasıl görmek için sorunları.</span><span class="sxs-lookup"><span data-stu-id="52957-125">During installation, you may encounter error 0x800f0906, 0x800f0907, 0x800f081f, or 0x800F0922, in which case refer to [.NET Framework 3.5 installation error: 0x800f0906, 0x800f0907, or 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) to see how to resolve these issues.</span></span>

<span data-ttu-id="52957-126">Yükleme sorununuzu hala çözümlenemiyor veya bir Internet bağlantısı yoksa, Windows yükleme medyasını kullanarak yüklemeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52957-126">If you still can't resolve your installation issue or you don't have an Internet connection, you can try installing it using your Windows installation media.</span></span> <span data-ttu-id="52957-127">Daha fazla bilgi için bkz: [Dağıtım Görüntüsü Bakımı ve Yönetimi (DISM) kullanarak .NET Framework 3.5 dağıtmak](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism).</span><span class="sxs-lookup"><span data-stu-id="52957-127">For more information, see [Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism).</span></span> <span data-ttu-id="52957-128">Yükleme medyasının yoksa bkz [yükleme medyasını oluşturmak için Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span><span class="sxs-lookup"><span data-stu-id="52957-128">If you don't have the installation media, see [Create installation media for Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span></span>
