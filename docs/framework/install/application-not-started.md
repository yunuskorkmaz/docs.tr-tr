---
title: Sorun giderme 'Bu uygulama başlatılamadı'
description: "'Bu uygulama başlatılamadı' iletişim kutusunu görürseniz ne yapmanız gerektiğini öğrenin."
ms.date: 09/05/2019
ms.openlocfilehash: 864c6ea23e9a048f060eee39d904bd4377be5084
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965912"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a><span data-ttu-id="83698-103">'Bu uygulama başlatılamadı' hata iletisi hata giderme</span><span class="sxs-lookup"><span data-stu-id="83698-103">Troubleshooting a 'This application could not be started' error message</span></span>

<span data-ttu-id="83698-104">.NET Framework için geliştirilen uygulamalar genellikle .NET Framework'ün belirli bir sürümünün sisteminize yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="83698-104">Applications that are developed for the .NET Framework typically require that a specific version of the .NET Framework be installed on your system.</span></span> <span data-ttu-id="83698-105">Bazı durumlarda, yüklü bir sürümü veya .NET Framework mevcut beklenen sürümü olmadan bir uygulama çalıştırmayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83698-105">In some cases, you may attempt to run an application without either an installed version or the expected version of the .NET Framework present.</span></span> <span data-ttu-id="83698-106">Bu genellikle aşağıdaki gibi bir hata iletişim kutusu üretir:</span><span class="sxs-lookup"><span data-stu-id="83698-106">This often produces an error dialog box like the following:</span></span>

![Bu uygulama başlatılamadı](media/application-not-started/app-could-not-be-started.png)

<span data-ttu-id="83698-108">Bu genellikle aşağıdaki koşullardan birini gösterir:</span><span class="sxs-lookup"><span data-stu-id="83698-108">This typically indicates one of the following conditions:</span></span>

- <span data-ttu-id="83698-109">Sisteminizdeki bir .NET Framework yüklemesi bozuldu.</span><span class="sxs-lookup"><span data-stu-id="83698-109">A .NET Framework installation on your system has become corrupted.</span></span>

- <span data-ttu-id="83698-110">Uygulamanızın gerektirdiği .NET Framework sürümü algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="83698-110">The version of the .NET Framework needed by your application cannot be detected.</span></span>

<span data-ttu-id="83698-111">Başvurunuzu çalıştırabilmeniz için bu sorunu gidermek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="83698-111">To address this issue so that you can run your application, do the following:</span></span>

1. <span data-ttu-id="83698-112">.NET [Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135)indirin.</span><span class="sxs-lookup"><span data-stu-id="83698-112">Download the [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span></span> <span data-ttu-id="83698-113">İndirme tamamlandığında araç otomatik olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="83698-113">The tool runs automatically when the download completes.</span></span>

1. <span data-ttu-id="83698-114">.NET Framework Repair Tool aşağıdaki şekilde gösterilenler gibi ek bir eylem önerirse, **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="83698-114">If the .NET Framework Repair Tool recommends any additional action, such as those shown in the following figure, select **Next**.</span></span>

   ![Önerilen değişiklikler](media/application-not-started/repair-tool-recommended-changes.png)

1. <span data-ttu-id="83698-116">.NET Framework Repair Tools, değişikliklerin tamamolduğunu belirtmek için aşağıdaki şekilde gösterilen bir iletişim kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="83698-116">The .NET Framework Repair Tools displays a dialog box shown in the following figure to indicate that changes are complete.</span></span> <span data-ttu-id="83698-117">Uygulamanızı yeniden çalıştırmayı denerken iletişim kutusunu açık bırakın.</span><span class="sxs-lookup"><span data-stu-id="83698-117">Leave the dialog box open while you to try rerun your application.</span></span> <span data-ttu-id="83698-118">Bu, .NET Framework Repair Tool bozuk bir .NET Framework yüklemesini tanımlayıp düzeltmişse başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83698-118">This should succeed if the .NET Framework Repair Tool has identified and corrected a corrupted .NET Framework installation.</span></span>

   ![Önerilen değişiklikler](media/application-not-started/repair-tool-changes-complete.png)

1. <span data-ttu-id="83698-120">Uygulamanız başarılı bir şekilde **çalışıyorsa, Bitiş** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="83698-120">If your application runs successfully, select the **Finish** button.</span></span> <span data-ttu-id="83698-121">Aksi **takdirde, İleri** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="83698-121">Otherwise, select the **Next** button.</span></span>

1. <span data-ttu-id="83698-122">**Sonraki** düğmesini seçtiyseniz, .NET Framework Repair Tool aşağıdaki gibi bir iletişim kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="83698-122">If you selected the **Next** button, the .NET Framework Repair Tool displays a dialog box like the following.</span></span> <span data-ttu-id="83698-123">Tanı lama bilgilerini Microsoft'a göndermek için **Bitiş** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="83698-123">Select the **Finish** button to send diagnostic information to Microsoft.</span></span>

   ![Sorunu çözemiyor](media/application-not-started/repair-tool-no-resolution.png)

1. <span data-ttu-id="83698-125">Uygulamayı hala çalıştıramıyorsanız, aşağıdaki tabloda gösterildiği gibi .NET Framework'ün Windows sürümünüz tarafından desteklenen en son sürümünü yükleyin.</span><span class="sxs-lookup"><span data-stu-id="83698-125">If you still cannot run the application, install the latest version of the .NET Framework supported by your version of Windows, as shown in the following table.</span></span>

   |<span data-ttu-id="83698-126">Windows sürümü</span><span class="sxs-lookup"><span data-stu-id="83698-126">Windows version</span></span>|<span data-ttu-id="83698-127">.NET Framework kurulumu</span><span class="sxs-lookup"><span data-stu-id="83698-127">.NET Framework installation</span></span>|
   |---|---|
   |<span data-ttu-id="83698-128">Windows 10 Yıldönümü Güncelleştirmesi ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="83698-128">Windows 10 Anniversary Update and later versions</span></span>|[<span data-ttu-id="83698-129">.NET Framework 4.8 Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="83698-129">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="83698-130">Windows 10, Windows 10 Kasım Güncelleştirmesi</span><span class="sxs-lookup"><span data-stu-id="83698-130">Windows 10, Windows 10 November Update</span></span>|[<span data-ttu-id="83698-131">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="83698-131">.NET Framework 4.6.2</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |<span data-ttu-id="83698-132">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="83698-132">Windows 8.1</span></span>|[<span data-ttu-id="83698-133">.NET Framework 4.8 Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="83698-133">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="83698-134">Windows 8</span><span class="sxs-lookup"><span data-stu-id="83698-134">Windows 8</span></span>|[<span data-ttu-id="83698-135">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="83698-135">.NET Framework 4.6.1</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |<span data-ttu-id="83698-136">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="83698-136">Windows 7 SP1</span></span>|[<span data-ttu-id="83698-137">.NET Framework 4.8 Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="83698-137">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="83698-138">Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="83698-138">Windows Vista SP2</span></span>|[<span data-ttu-id="83698-139">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="83698-139">.NET Framework 4.6</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > <span data-ttu-id="83698-140">.NET Framework 4.8, Windows 10 Mayıs 2019 Güncelleştirmesi'nde önceden yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="83698-140">.NET Framework 4.8 is preinstalled on Windows 10 May 2019 Update.</span></span>

1. <span data-ttu-id="83698-141">Uygulamayı başlatmayı dene.</span><span class="sxs-lookup"><span data-stu-id="83698-141">Attempt to launch the application.</span></span>

1. <span data-ttu-id="83698-142">Bazı durumlarda, .NET Framework 3.5'i yüklemenizi isteyen aşağıdaki gibi bir iletişim kutusu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83698-142">In some cases, you may see a dialog box like the following, which asks you to install the .NET Framework 3.5.</span></span> <span data-ttu-id="83698-143">.NET Framework 3.5'i yüklemek için **bu özelliği karşıdan yükleyin ve yükleyin** ve uygulamayı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="83698-143">Select **Download and install this feature** to install the .NET Framework 3.5, then launch the application again.</span></span>

   ![Sorunu çözemiyor](media/application-not-started/install-3-5.png)

## <a name="see-also"></a><span data-ttu-id="83698-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83698-145">See also</span></span>

- [<span data-ttu-id="83698-146">.NET Çerçeve Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="83698-146">.NET Framework System Requirements</span></span>](../get-started/system-requirements.md)
- [<span data-ttu-id="83698-147">.NET Framework kurulum kılavuzu</span><span class="sxs-lookup"><span data-stu-id="83698-147">.NET Framework installation guide</span></span>](index.md)
- [<span data-ttu-id="83698-148">Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="83698-148">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
