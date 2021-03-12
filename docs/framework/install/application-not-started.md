---
title: "' Bu uygulama başlatılamadı ' sorunlarını giderme"
description: "' Bu uygulama başlatılamadı ' iletişim kutusu görürseniz yapılacaklar hakkında bilgi edinin."
ms.date: 09/05/2019
ms.openlocfilehash: 92055bf40500eba4f7c892d11af12d8e675ddd5d
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605249"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a><span data-ttu-id="ead83-103">' Bu uygulama başlatılamadı ' hata iletisiyle ilgili sorun giderme</span><span class="sxs-lookup"><span data-stu-id="ead83-103">Troubleshooting a 'This application could not be started' error message</span></span>

<span data-ttu-id="ead83-104">.NET Framework için geliştirilen uygulamalar genellikle sisteminize belirli bir .NET Framework sürümünün yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ead83-104">Applications that are developed for .NET Framework typically require that a specific version of .NET Framework be installed on your system.</span></span> <span data-ttu-id="ead83-105">Bazı durumlarda, yüklü bir sürüm ya da beklenen .NET Framework sürümü olmadan bir uygulamayı çalıştırmayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ead83-105">In some cases, you may attempt to run an application without either an installed version or the expected version of .NET Framework present.</span></span> <span data-ttu-id="ead83-106">Bu genellikle aşağıdaki gibi bir hata iletişim kutusu üretir:</span><span class="sxs-lookup"><span data-stu-id="ead83-106">This often produces an error dialog box like the following:</span></span>

![Bu uygulama başlatılamadı](media/application-not-started/app-could-not-be-started.png)

<span data-ttu-id="ead83-108">Bu hata genellikle aşağıdaki koşullardan birini gösterir:</span><span class="sxs-lookup"><span data-stu-id="ead83-108">This error typically indicates one of the following conditions:</span></span>

- <span data-ttu-id="ead83-109">Sisteminizdeki bir .NET Framework yüklemesi bozuk hale geldi.</span><span class="sxs-lookup"><span data-stu-id="ead83-109">A .NET Framework installation on your system has become corrupted.</span></span>

- <span data-ttu-id="ead83-110">Uygulamanız için gereken .NET Framework sürümü algılanamıyor.</span><span class="sxs-lookup"><span data-stu-id="ead83-110">The version of .NET Framework needed by your application cannot be detected.</span></span>

<span data-ttu-id="ead83-111">Uygulamanızı çalıştırabilmeniz için bu sorunu gidermek üzere şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="ead83-111">To address this issue so that you can run your application, do the following:</span></span>

1. <span data-ttu-id="ead83-112">[.NET Framework onarım aracını indirin (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span><span class="sxs-lookup"><span data-stu-id="ead83-112">Download the [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span></span> <span data-ttu-id="ead83-113">Yükleme tamamlandığında araç otomatik olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="ead83-113">The tool runs automatically when the download completes.</span></span>

1. <span data-ttu-id="ead83-114">.NET Framework onarım aracı aşağıdaki şekilde gösterilen ek işlemleri önerirse, **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="ead83-114">If the .NET Framework Repair Tool recommends any additional action, such as those shown in the following figure, select **Next**.</span></span>

   ![Onarım Aracı önerilen değişiklikler](media/application-not-started/repair-tool-recommended-changes.png)

1. <span data-ttu-id="ead83-116">.NET Framework onarım araçları, değişikliklerin tamamlandığını göstermek için aşağıdaki şekilde gösterilen bir iletişim kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ead83-116">The .NET Framework Repair Tools displays a dialog box shown in the following figure to indicate that changes are complete.</span></span> <span data-ttu-id="ead83-117">Uygulamanızı yeniden çalıştırmayı deneirken iletişim kutusunu açık bırakın.</span><span class="sxs-lookup"><span data-stu-id="ead83-117">Leave the dialog box open while you to try rerun your application.</span></span> <span data-ttu-id="ead83-118">.NET Framework Onarım Aracı bozuk bir .NET Framework yüklemesi tanımlamışsa ve düzeltiyorsa bu başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ead83-118">This should succeed if the .NET Framework Repair Tool has identified and corrected a corrupted .NET Framework installation.</span></span>

   ![Araç değişikliklerini onarma Tamam](media/application-not-started/repair-tool-changes-complete.png)

1. <span data-ttu-id="ead83-120">Uygulamanız başarıyla çalışırsa, **son** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ead83-120">If your application runs successfully, select the **Finish** button.</span></span> <span data-ttu-id="ead83-121">Aksi takdirde, **İleri** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ead83-121">Otherwise, select the **Next** button.</span></span>

1. <span data-ttu-id="ead83-122">**İleri** düğmesini seçtiyseniz, .NET Framework onarım aracı aşağıdaki gibi bir iletişim kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ead83-122">If you selected the **Next** button, the .NET Framework Repair Tool displays a dialog box like the following.</span></span> <span data-ttu-id="ead83-123">Tanılama bilgilerini Microsoft 'a göndermek için **son** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ead83-123">Select the **Finish** button to send diagnostic information to Microsoft.</span></span>

   ![Sorun çözümlenemiyor](media/application-not-started/repair-tool-no-resolution.png)

1. <span data-ttu-id="ead83-125">Uygulamayı hala çalıştıramıyorum, aşağıdaki tabloda gösterildiği gibi, Windows sürümünüz tarafından desteklenen .NET Framework en son sürümünü yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ead83-125">If you still cannot run the application, install the latest version of .NET Framework that's supported by your version of Windows, as shown in the following table.</span></span>

   |<span data-ttu-id="ead83-126">Windows sürümü</span><span class="sxs-lookup"><span data-stu-id="ead83-126">Windows version</span></span>|<span data-ttu-id="ead83-127">.NET Framework yükleme</span><span class="sxs-lookup"><span data-stu-id="ead83-127">.NET Framework installation</span></span>|
   |---|---|
   |<span data-ttu-id="ead83-128">Windows 10 yıldönümü güncelleştirmesi ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="ead83-128">Windows 10 Anniversary Update and later versions</span></span>|[<span data-ttu-id="ead83-129">.NET Framework 4,8 çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="ead83-129">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="ead83-130">Windows 10, Windows 10 Kasım güncelleştirmesi</span><span class="sxs-lookup"><span data-stu-id="ead83-130">Windows 10, Windows 10 November Update</span></span>|[<span data-ttu-id="ead83-131">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="ead83-131">.NET Framework 4.6.2</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |<span data-ttu-id="ead83-132">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="ead83-132">Windows 8.1</span></span>|[<span data-ttu-id="ead83-133">.NET Framework 4,8 çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="ead83-133">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="ead83-134">Windows 8</span><span class="sxs-lookup"><span data-stu-id="ead83-134">Windows 8</span></span>|[<span data-ttu-id="ead83-135">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="ead83-135">.NET Framework 4.6.1</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |<span data-ttu-id="ead83-136">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="ead83-136">Windows 7 SP1</span></span>|[<span data-ttu-id="ead83-137">.NET Framework 4,8 çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="ead83-137">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="ead83-138">Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="ead83-138">Windows Vista SP2</span></span>|[<span data-ttu-id="ead83-139">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="ead83-139">.NET Framework 4.6</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > <span data-ttu-id="ead83-140">.NET Framework 4,8, Windows 10 Mayıs 2019 güncelleştirme ' ye önceden yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ead83-140">.NET Framework 4.8 is preinstalled on Windows 10 May 2019 Update.</span></span>

1. <span data-ttu-id="ead83-141">Uygulamayı başlatmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="ead83-141">Attempt to launch the application.</span></span>

1. <span data-ttu-id="ead83-142">Bazı durumlarda, aşağıdaki gibi bir iletişim kutusu görebilirsiniz. .NET Framework 3,5 yüklemenizi ister.</span><span class="sxs-lookup"><span data-stu-id="ead83-142">In some cases, you may see a dialog box like the following, which asks you to install .NET Framework 3.5.</span></span> <span data-ttu-id="ead83-143">.NET Framework 3,5 yüklemek için **Bu özelliği indir ve yükle** ' yi seçip uygulamayı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="ead83-143">Select **Download and install this feature** to install .NET Framework 3.5, then launch the application again.</span></span>

   ![.NET Framework 3,5 ' i yüklemek için önerilen Windows özellikleri iletişim kutusu](media/application-not-started/install-3-5.png)

## <a name="see-also"></a><span data-ttu-id="ead83-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ead83-145">See also</span></span>

- [<span data-ttu-id="ead83-146">.NET Framework sistem gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="ead83-146">.NET Framework System Requirements</span></span>](../get-started/system-requirements.md)
- [<span data-ttu-id="ead83-147">.NET Framework Yükleme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ead83-147">.NET Framework installation guide</span></span>](index.md)
- [<span data-ttu-id="ead83-148">Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="ead83-148">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
