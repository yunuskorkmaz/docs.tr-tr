---
title: ".NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yükleme"
description: ".NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yüklemek öğrenin."
author: rlander
ms.author: mairaw
keywords: ".NET framework, yükleme"
ms.date: 05/26/2017
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 67cda1d5-c6g4-4eb5-93e6-4f478de07ff7
ms.openlocfilehash: 85a3cada074714c24015d90c26d94551f4f411f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="902d7-104">.NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yükleme</span><span class="sxs-lookup"><span data-stu-id="902d7-104">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="902d7-105">Windows 10, Windows 8.1 ve Windows 8 uygulama çalıştırmak için .NET Framework 3.5 gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="902d7-105">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="902d7-106">Önceki Windows sürümleri için bu yönergeleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="902d7-106">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="902d7-107">İsteğe bağlı olarak .NET Framework 3.5 yükleyin</span><span class="sxs-lookup"><span data-stu-id="902d7-107">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="902d7-108">.NET Framework 3.5 gerektiren bir uygulama çalıştırmayı denerseniz aşağıdaki yapılandırma iletişim kutusu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="902d7-108">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="902d7-109">Seçin **bu özelliği yüklemek** .NET Framework 3.5 etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="902d7-109">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="902d7-110">Bu seçenek, bir Internet bağlantısı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="902d7-110">This option requires an Internet connection.</span></span>

![.NET framework yükleme iletişim kutusu](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="902d7-112">Denetim Masası'ndaki .NET Framework 3.5 etkinleştir</span><span class="sxs-lookup"><span data-stu-id="902d7-112">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="902d7-113">.NET Framework 3.5 Windows Denetim Masası'ndan etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="902d7-113">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="902d7-114">Bu seçenek, bir Internet bağlantısı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="902d7-114">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="902d7-115">Windows Windows tuşuna ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) klavyenizde "Windows özellikleri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="902d7-115">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="902d7-116">**Kapatma Windows özelliklerini aç veya Kapat** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="902d7-116">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="902d7-117">Seçin **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir)** onay kutusu, select **Tamam**ve istenirse, bilgisayarınızı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="902d7-117">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![.NET ile Denetim Masası'nı yükleme](./media/dotnet-control-panel.png)

   <span data-ttu-id="902d7-119">Alt öğeler için seçmeniz gerekmez **Windows Communication Foundation (WCF) HTTP etkinleştirmesi** ve **Windows Communication Foundation (WCF) HTTP olmayan etkinleştirme** geliştiriciyseniz sürece veya Bu işlevselliği gerektiren Sunucu Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="902d7-119">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>
