---
title: Windows 7 SP1 'e .NET Framework yüklemesi
description: Windows 7 SP1 'e .NET Framework yüklemeyi öğrenin.
ms.date: 04/18/2019
ms.openlocfilehash: 900b38110626a93f37829045a8676ea87101d7e9
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899093"
---
# <a name="install-the-net-framework-on-windows-7-sp1-and-windows-server-2008-r2"></a><span data-ttu-id="adb36-103">Windows 7 SP1 ve Windows Server 2008 R2’de .NET Framework Yükleme</span><span class="sxs-lookup"><span data-stu-id="adb36-103">Install the .NET Framework on Windows 7 SP1 and Windows Server 2008 R2</span></span>

<span data-ttu-id="adb36-104">.NET Framework Windows üzerinde birçok uygulama çalıştırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="adb36-104">The .NET Framework is required to run many applications on Windows.</span></span> <span data-ttu-id="adb36-105">Yüklemek için aşağıdaki yönergeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="adb36-105">You can use the following instructions to install it.</span></span> <span data-ttu-id="adb36-106">Bir uygulamayı çalıştırmayı ve makinenizde aşağıdaki iletişim kutusunu görmenizi tamamladıktan sonra bu sayfada ulaşmış olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="adb36-106">You may have arrived on this page after trying to run an application and seeing the following dialog on your machine.</span></span>

![Bu uygulama başlatılamadı](./media/this-application-could-not-be-started.png)

<span data-ttu-id="adb36-108">Bu yönergeler, ihtiyacınız olan .NET Framework sürümlerini yüklemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="adb36-108">These instructions will help you install the .NET Framework versions you need.</span></span> <span data-ttu-id="adb36-109">[.NET Framework 4,8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) en son sürümdür.</span><span class="sxs-lookup"><span data-stu-id="adb36-109">The [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) is the latest version.</span></span> <span data-ttu-id="adb36-110">Windows 7 SP1 ve Windows Server 2008 R2 'de desteklenir ve [Windows 10 mayıs 2019 güncelleştirmesine](https://support.microsoft.com/help/4028685/windows-10-get-the-update)dahildir.</span><span class="sxs-lookup"><span data-stu-id="adb36-110">It is supported on Windows 7 SP1 and Windows Server 2008 R2 and is included with [Windows 10 May 2019 Update](https://support.microsoft.com/help/4028685/windows-10-get-the-update).</span></span>

## <a name="net-framework-48"></a><span data-ttu-id="adb36-111"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="adb36-111">.NET Framework 4.8</span></span>

> [!div class="button"]
> [<span data-ttu-id="adb36-112">.NET Framework 4.8'i İndirin</span><span class="sxs-lookup"><span data-stu-id="adb36-112">Download .NET Framework 4.8</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

<span data-ttu-id="adb36-113">[.NET Framework 4,8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) , .NET Framework 4,0 veya üzeri için oluşturulmuş uygulamaları çalıştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="adb36-113">The [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) can be used to run applications built for .NET Framework 4.0 or later.</span></span>

### <a name="offline-installer"></a><span data-ttu-id="adb36-114">Çevrimdışı yükleyici</span><span class="sxs-lookup"><span data-stu-id="adb36-114">Offline installer</span></span>

<span data-ttu-id="adb36-115">Windows 7 ' de .NET Framework için çevrimdışı yükleme yaparken öncelikle hedef makineye en son [Microsoft kök sertifika yetkilisi 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) ' nin yüklü olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="adb36-115">When doing an offline install for .NET Framework on Windows 7, you'll first need to make sure that the latest [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) has been installed on the target machine.</span></span>

<span data-ttu-id="adb36-116">_certmgr.exe_ aracı bir sertifikayı yüklemeyi otomatikleştirebilir ve Visual Studio 'dan veya Windows SDK elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="adb36-116">The _certmgr.exe_ tool can automate installing a certificate and is obtained from Visual Studio or the Windows SDK.</span></span> <span data-ttu-id="adb36-117">Aşağıdaki komut, .NET Framework yükleyicisini çalıştırmadan önce sertifikayı yüklemek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="adb36-117">The following command is used to install the certificate before running the .NET Framework installer:</span></span>

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

## <a name="net-framework-35"></a><span data-ttu-id="adb36-118">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="adb36-118">.NET Framework 3.5</span></span>

<span data-ttu-id="adb36-119">[3,5 .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) , Windows 7 ' ye dahildir.</span><span class="sxs-lookup"><span data-stu-id="adb36-119">The [.NET Framework 3.5](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) is included with Windows 7.</span></span>

<span data-ttu-id="adb36-120">.NET Framework 3,5 ile 3,5 .NET Framework 1,0 için oluşturulmuş uygulamaları destekler.</span><span class="sxs-lookup"><span data-stu-id="adb36-120">The .NET Framework 3.5 supports apps built for .NET Framework 1.0 through 3.5.</span></span>

## <a name="help"></a><span data-ttu-id="adb36-121">Yardım</span><span class="sxs-lookup"><span data-stu-id="adb36-121">Help</span></span>

<span data-ttu-id="adb36-122">.NET Framework yüklü olan doğru sürümü alamazsanız, [Yardım Için Microsoft 'a başvurabilirsiniz](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help) .</span><span class="sxs-lookup"><span data-stu-id="adb36-122">You can [contact Microsoft for help](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help) if you cannot get the correct version of the .NET Framework installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="adb36-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adb36-123">See also</span></span>

- [<span data-ttu-id="adb36-124">.NET Framework indirin</span><span class="sxs-lookup"><span data-stu-id="adb36-124">Download the .NET Framework</span></span>](https://dotnet.microsoft.com/download)
- [<span data-ttu-id="adb36-125">Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="adb36-125">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
- [<span data-ttu-id="adb36-126">Geliştiriciler için .NET Framework yüklemesi</span><span class="sxs-lookup"><span data-stu-id="adb36-126">Install the .NET Framework for developers</span></span>](guide-for-developers.md)
