---
title: ".NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yükleme"
description: ".NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yüklemek öğrenin."
author: rlander
ms.author: mairaw
ms.date: 11/27/2017
ms.topic: article
ms.prod: .net-framework
ms.workload:
- dotnet
ms.openlocfilehash: e81008eca3019860789db548d40998a7a7565d31
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2018
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="32fbc-103">.NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yükleme</span><span class="sxs-lookup"><span data-stu-id="32fbc-103">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="32fbc-104">Windows 10, Windows 8.1 ve Windows 8 uygulama çalıştırmak için .NET Framework 3.5 gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="32fbc-104">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="32fbc-105">Önceki Windows sürümleri için bu yönergeleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32fbc-105">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="32fbc-106">İsteğe bağlı olarak .NET Framework 3.5 yükleyin</span><span class="sxs-lookup"><span data-stu-id="32fbc-106">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="32fbc-107">.NET Framework 3.5 gerektiren bir uygulama çalıştırmayı denerseniz aşağıdaki yapılandırma iletişim kutusu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32fbc-107">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="32fbc-108">Seçin **bu özelliği yüklemek** .NET Framework 3.5 etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="32fbc-108">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="32fbc-109">Bu seçenek, bir Internet bağlantısı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="32fbc-109">This option requires an Internet connection.</span></span>

![.NET framework yükleme iletişim kutusu](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="32fbc-111">Denetim Masası'ndaki .NET Framework 3.5 etkinleştir</span><span class="sxs-lookup"><span data-stu-id="32fbc-111">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="32fbc-112">.NET Framework 3.5 Windows Denetim Masası'ndan etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32fbc-112">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="32fbc-113">Bu seçenek, bir Internet bağlantısı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="32fbc-113">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="32fbc-114">Windows Windows tuşuna ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) klavyenizde "Windows özellikleri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="32fbc-114">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="32fbc-115">**Kapatma Windows özelliklerini aç veya Kapat** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="32fbc-115">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="32fbc-116">Seçin **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir)** onay kutusu, select **Tamam**ve istenirse, bilgisayarınızı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="32fbc-116">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![.NET ile Denetim Masası'nı yükleme](./media/dotnet-control-panel.png)

   <span data-ttu-id="32fbc-118">Alt öğeler için seçmeniz gerekmez **Windows Communication Foundation (WCF) HTTP etkinleştirmesi** ve **Windows Communication Foundation (WCF) HTTP olmayan etkinleştirme** geliştiriciyseniz sürece veya Bu işlevselliği gerektiren Sunucu Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="32fbc-118">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a><span data-ttu-id="32fbc-119">.NET Framework 3.5 yükleme sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="32fbc-119">Troubleshoot the installation of the .NET Framework 3.5</span></span>

<span data-ttu-id="32fbc-120">Yükleme sırasında hata 0x800f0906, 0x800f0907, 0x800f081f veya 0x800F0922 bakın; bu durumda, karşılaşabileceğiniz [.NET Framework 3.5 yükleme hatası: 0x800f0906, 0x800f0907 veya 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) bunları gidermek nasıl görmek için sorunları.</span><span class="sxs-lookup"><span data-stu-id="32fbc-120">During installation, you may encounter error 0x800f0906, 0x800f0907, 0x800f081f, or 0x800F0922, in which case refer to [.NET Framework 3.5 installation error: 0x800f0906, 0x800f0907, or 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) to see how to resolve these issues.</span></span>

<span data-ttu-id="32fbc-121">Önceki makalede açıklanan yöntemlerden herhangi birini başarısız olursa veya bir Internet bağlantısı yoksa, Windows yükleme medyasını kullanmak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="32fbc-121">If any of the methods discussed in the previous article fail or if you don't have an Internet connection, it's necessary to use your Windows installation media.</span></span> <span data-ttu-id="32fbc-122">Daha fazla bilgi için bkz: [Dağıtım Görüntüsü Bakımı ve Yönetimi (DISM) kullanarak .NET Framework 3.5 dağıtmak](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism).</span><span class="sxs-lookup"><span data-stu-id="32fbc-122">For more information, see [Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism).</span></span> <span data-ttu-id="32fbc-123">Yükleme medyasının yoksa bkz [yükleme medyasını oluşturmak için Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span><span class="sxs-lookup"><span data-stu-id="32fbc-123">If you don't have the installation media, see [Create installation media for Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span></span>
