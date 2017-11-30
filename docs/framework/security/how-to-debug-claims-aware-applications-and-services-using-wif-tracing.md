---
title: "Nasıl yapılır: Talep kullanan uygulama ve WIF izlemeyi kullanma hizmetleri hata ayıklama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 36cb961345cb724597d8e48ec3be6cbb84df4632
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a><span data-ttu-id="755a4-102">Nasıl yapılır: Talep kullanan uygulama ve WIF izlemeyi kullanma hizmetleri hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="755a4-102">How To: Debug Claims-Aware Applications And Services Using WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="755a4-103">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="755a4-103">Applies To</span></span>  
  
-   <span data-ttu-id="755a4-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="755a4-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="755a4-105">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="755a4-105">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>  
  
-   <span data-ttu-id="755a4-106">Sorun giderme ve WIF uygulamalarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="755a4-106">Troubleshooting and Debugging WIF Applications</span></span>  
  
## <a name="summary"></a><span data-ttu-id="755a4-107">Özet</span><span class="sxs-lookup"><span data-stu-id="755a4-107">Summary</span></span>  
 <span data-ttu-id="755a4-108">Bu yöntem WIF izlemeyi yapılandırmak, izleme günlükleri toplamak gerekli adımlar açıklanır ve izleme Görüntüleyicisi aracı kullanarak izleme analiz etme günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="755a4-108">This How-To describes required steps for how to configure WIF tracing, collect trace logs, and how to analyze the trace logs using Trace Viewer tool.</span></span> <span data-ttu-id="755a4-109">İzleme girişleri WIF ilgili sorunları gidermek için gereken eylemleri için genel eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="755a4-109">It provides general mapping for trace entries to actions needed to troubleshoot issues related to WIF.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="755a4-110">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="755a4-110">Contents</span></span>  
  
-   <span data-ttu-id="755a4-111">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="755a4-111">Objectives</span></span>  
  
-   <span data-ttu-id="755a4-112">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="755a4-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="755a4-113">1. adım – WIF Web.config yapılandırma dosyası kullanarak izlemeyi yapılandırın</span><span class="sxs-lookup"><span data-stu-id="755a4-113">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
-   <span data-ttu-id="755a4-114">2. adım – WIF izleme dosyaları izleme Görüntüleyicisi aracı kullanmak Çözümle</span><span class="sxs-lookup"><span data-stu-id="755a4-114">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
-   <span data-ttu-id="755a4-115">Adım 3 – WIF düzeltmek için çözümleri tanımla ilgili sorunlar</span><span class="sxs-lookup"><span data-stu-id="755a4-115">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
-   <span data-ttu-id="755a4-116">İlgili öğeler</span><span class="sxs-lookup"><span data-stu-id="755a4-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="755a4-117">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="755a4-117">Objectives</span></span>  
  
-   <span data-ttu-id="755a4-118">WIF izlemeyi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="755a4-118">Configure WIF tracing.</span></span>  
  
-   <span data-ttu-id="755a4-119">Görünüm izleme izleme Görüntüleyicisi aracı günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="755a4-119">View trace logs in the Trace Viewer tool.</span></span>  
  
-   <span data-ttu-id="755a4-120">WIF tanımlamak ile ilgili sorunlar izleme günlüğüne kaydeder.</span><span class="sxs-lookup"><span data-stu-id="755a4-120">Identify WIF related issues in the trace logs.</span></span>  
  
-   <span data-ttu-id="755a4-121">Uygulama WIF düzeltme eylemleriyle ilgili sorunları izleme günlüklerine bulundu.</span><span class="sxs-lookup"><span data-stu-id="755a4-121">Apply corrective actions to WIF related issues found in the trace logs.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="755a4-122">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="755a4-122">Summary of Steps</span></span>  
  
-   <span data-ttu-id="755a4-123">1. adım – WIF Web.config yapılandırma dosyası kullanarak izlemeyi yapılandırın</span><span class="sxs-lookup"><span data-stu-id="755a4-123">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
-   <span data-ttu-id="755a4-124">2. adım – WIF izleme dosyaları izleme Görüntüleyicisi aracı kullanmak Çözümle</span><span class="sxs-lookup"><span data-stu-id="755a4-124">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
-   <span data-ttu-id="755a4-125">Adım 3 – WIF düzeltmek için çözümleri tanımla ilgili sorunlar</span><span class="sxs-lookup"><span data-stu-id="755a4-125">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="755a4-126">1. adım – WIF Web.config yapılandırma dosyası kullanarak izlemeyi yapılandırın</span><span class="sxs-lookup"><span data-stu-id="755a4-126">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
 <span data-ttu-id="755a4-127">Bu adımda, değişiklikleri yapılandırma bölümlerinin ekler *Web.config* olaylarına izlemesini ve izleme günlüğüne depolamaya WIF etkinleştirmek dosya.</span><span class="sxs-lookup"><span data-stu-id="755a4-127">In this step, you will add changes to configuration sections in the *Web.config* file that enable WIF to trace its events and store them in a trace log.</span></span>  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="755a4-128">Web.config yapılandırma dosyası kullanarak WIF izlemeyi yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="755a4-128">To configure WIF tracing using Web.config configuration file</span></span>  
  
1.  <span data-ttu-id="755a4-129">Kök açmak **Web.config** veya **App.config** yapılandırma dosyası içinde üzerine çift tıklayarak Visual Studio düzenleyicisinde **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="755a4-129">Open the root **Web.config** or **App.config** configuration file in the Visual Studio editor by double clicking on it in **Solution Explorer**.</span></span> <span data-ttu-id="755a4-130">Çözümünüzü yoksa **Web.config** veya **App.config** yapılandırma dosyası, çözüm üzerinde sağ tıklayarak eklemek **Çözüm Gezgini** tıklatıp **Ekleme**, ardından **yeni öğe...** .</span><span class="sxs-lookup"><span data-stu-id="755a4-130">If your solution does not have **Web.config** or **App.config** configuration file, add it by right clicking on the solution in the **Solution Explorer** and clicking **Add**, then clicking **New Item…**.</span></span> <span data-ttu-id="755a4-131">Üzerinde **yeni öğe** iletişim kutusunda **uygulama yapılandırma dosyası** için **App.config** veya **Web yapılandırma dosyası** için**Web.config** tıklatın ve liste **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="755a4-131">On the **New Item** dialog, Select **Application Configuration File** for **App.config** or **Web Configuration File** for **Web.config** from the list and click **OK**.</span></span>  
  
2.  <span data-ttu-id="755a4-132">İçindeki yapılandırma dosyasının aşağıdakine benzer yapılandırma girdileri eklemek  **\<configuration >** yapılandırma dosyasının sonuna düğümde:</span><span class="sxs-lookup"><span data-stu-id="755a4-132">Add the configuration entries similar to the following to the configuration file inside **\<configuration>** node at the end of the configuration file:</span></span>  
  
    ```xml  
    <system.diagnostics>  
        <sources>  
            <source name="System.IdentityModel" switchValue="Verbose">  
                <listeners>  
                    <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="WIFTrace.e2e"/>  
                </listeners>  
            </source>  
        </sources>  
        <trace autoflush="true"/>  
    </system.diagnostics>  
    ```  
  
3.  <span data-ttu-id="755a4-133">Yukarıdaki yapılandırma ayrıntılı izleme olayları oluşturmak ve bunları oturum WIF bildirir *WIFTrace.e2e* dosya.</span><span class="sxs-lookup"><span data-stu-id="755a4-133">The above configuration instructs WIF to generate verbose trace events and log them into *WIFTrace.e2e* file.</span></span> <span data-ttu-id="755a4-134">Değerleri için tam bir listesi için **switchValue** anahtarı, aşağıdaki konuda bulunan izleme düzeyi tabloya başvurun: [yapılandırma izleme](http://msdn.microsoft.com/library/ms733025.aspx).</span><span class="sxs-lookup"><span data-stu-id="755a4-134">For a complete list of values for the **switchValue** switch, refer to the Trace Level table found in the following topic: [Configuring Tracing](http://msdn.microsoft.com/library/ms733025.aspx).</span></span>  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a><span data-ttu-id="755a4-135">2. adım – WIF izleme dosyaları izleme Görüntüleyicisi aracı kullanmak Çözümle</span><span class="sxs-lookup"><span data-stu-id="755a4-135">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
 <span data-ttu-id="755a4-136">Bu adımda, WIF izleme günlüklerini çözümlemek için izleme Görüntüleyicisi aracı (SvcTraceViewer.exe) kullanır.</span><span class="sxs-lookup"><span data-stu-id="755a4-136">In this step, you will use the Trace Viewer Tool (SvcTraceViewer.exe) to analyze WIF trace logs.</span></span>  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a><span data-ttu-id="755a4-137">İzleme Görüntüleyicisi aracı (SvcTraceViewer.exe) kullanarak WIF izleme günlüklerini çözümlemek için</span><span class="sxs-lookup"><span data-stu-id="755a4-137">To analyze WIF trace logs using Trace Viewer tool (SvcTraceViewer.exe)</span></span>  
  
1.  <span data-ttu-id="755a4-138">İzleme Görüntüleyicisi aracı (SvcTraceViewer.exe) Windows SDK'ın bir parçası olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="755a4-138">Trace Viewer tool (SvcTraceViewer.exe) ships as part of the Windows SDK.</span></span> <span data-ttu-id="755a4-139">Windows SDK'sı henüz yüklemediyseniz, buradan indirebilirsiniz: [Windows SDK](http://www.microsoft.com/download/en/details.aspx?id=8279).</span><span class="sxs-lookup"><span data-stu-id="755a4-139">If you haven’t already installed the Windows SDK, you can download it here: [Windows SDK](http://www.microsoft.com/download/en/details.aspx?id=8279).</span></span>  
  
2.  <span data-ttu-id="755a4-140">İzleme Görüntüleyicisi aracı (SvcTraceViewer.exe) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="755a4-140">Run the Trace Viewer tool (SvcTraceViewer.exe).</span></span> <span data-ttu-id="755a4-141">İçinde kullanılabilir genellikle **Bin** yükleme yolunun klasörü.</span><span class="sxs-lookup"><span data-stu-id="755a4-141">It is typically available in the **Bin** folder of the installation path.</span></span>  
  
3.  <span data-ttu-id="755a4-142">WIF izleme günlük dosyasını seçerek Örneğin, WIFTrace.e2e açmak **dosya**, **Aç...**</span><span class="sxs-lookup"><span data-stu-id="755a4-142">Open the WIF trace log file, for example, WIFTrace.e2e by selecting **File**, **Open…**</span></span> <span data-ttu-id="755a4-143">seçenek menüde veya kullanarak **Ctrl + O** kısayol.</span><span class="sxs-lookup"><span data-stu-id="755a4-143">option in the menu or using the **Ctrl+O** shortcut.</span></span> <span data-ttu-id="755a4-144">İzleme günlük dosyasını izleme Görüntüleyicisi aracı açılır.</span><span class="sxs-lookup"><span data-stu-id="755a4-144">The trace log file opens in the Trace Viewer tool.</span></span>  
  
4.  <span data-ttu-id="755a4-145">Gözden girişlerinde **etkinlik** sekmesi. Her giriş, bir etkinlik numarası, günlüğe kaydedilmiş izlemeleri sayısı, süresi etkinliği ve onun başlangıç ve bitiş tarih damgaları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="755a4-145">Review entries in the **Activity** tab. Each entry should contain an activity number, the number of traces that were logged, duration of the activity and its start and end timestamps.</span></span>  
  
5.  <span data-ttu-id="755a4-146">Tıklayın **etkinlik** sekmesi. Aracının ana alanı ayrıntılı izleme girdiler görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="755a4-146">Click on the **Activity** tab. You should see detailed trace entries in the main area of the tool.</span></span> <span data-ttu-id="755a4-147">Kullanım **düzeyi** açılır liste belirli düzeyi izlemeleri, örneğin filtrelemek için menüsünde: **tüm**, **uyarı**, **hataları**, **Bilgi**, vb.</span><span class="sxs-lookup"><span data-stu-id="755a4-147">Use the **Level** dropdown list on the menu to filter specific level of traces, for example: **All**, **Warning**, **Errors**, **Information**, etc.</span></span>  
  
6.  <span data-ttu-id="755a4-148">Aracı'nın alt alanındaki ayrıntılarını gözden geçirmek için girişleri belirli izleme'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="755a4-148">Click on specific trace entries to review the details in the lower area of the tool.</span></span> <span data-ttu-id="755a4-149">Ayrıntıları kullanılarak görüntülenebilir **biçimlendirilmiş** ve **XML** ilgili sekmeleri seçerek görünümü.</span><span class="sxs-lookup"><span data-stu-id="755a4-149">The details can be viewed using **Formatted** and **XML** view by choosing corresponding tabs.</span></span>  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="755a4-150">Adım 3 – WIF düzeltmek için çözümleri tanımla ilgili sorunlar</span><span class="sxs-lookup"><span data-stu-id="755a4-150">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
 <span data-ttu-id="755a4-151">Bu adımda, WIF izleme günlüğü ve izleme Görüntüleyicisi Aracı'nı kullanarak tanımlanan WIF ilgili sorunların çözümleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="755a4-151">In this step, you can identify solutions for WIF-related issues identified by using the WIF trace log and Trace Viewer tool.</span></span> <span data-ttu-id="755a4-152">Genel özetlenmektedir WIF eşlenmesini ilgili olası çözümleri veya sorunu gidermek için gerekli eylemleri için özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="755a4-152">It outlines general mapping of WIF related exceptions to potential solutions or required actions to troubleshoot the issue.</span></span>  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="755a4-153">WIF düzeltmek için çözümleri tanımlamak için ilgili sorunlar</span><span class="sxs-lookup"><span data-stu-id="755a4-153">To identify solutions to fix WIF related issues</span></span>  
  
1.  <span data-ttu-id="755a4-154">Aşağıdaki tabloda WIF özel durumlar ve sorunları düzeltmek için gerekli eylemleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="755a4-154">Review the following table of WIF exceptions and the required actions to correct the issues.</span></span>  
  
|<span data-ttu-id="755a4-155">**Hata Kimliği**</span><span class="sxs-lookup"><span data-stu-id="755a4-155">**Error ID**</span></span>|<span data-ttu-id="755a4-156">**Hata iletisi**</span><span class="sxs-lookup"><span data-stu-id="755a4-156">**Error Message**</span></span>|<span data-ttu-id="755a4-157">**Hatayı düzeltmek işlem gerekiyor**</span><span class="sxs-lookup"><span data-stu-id="755a4-157">**Action needed to fix the error**</span></span>|  
|-|-|-|  
|<span data-ttu-id="755a4-158">ID4175</span><span class="sxs-lookup"><span data-stu-id="755a4-158">ID4175</span></span>|<span data-ttu-id="755a4-159">Güvenlik belirteci veren IssuerNameRegistry tarafından tanınmadı.</span><span class="sxs-lookup"><span data-stu-id="755a4-159">The issuer of the security token was not recognized by the IssuerNameRegistry.</span></span>  <span data-ttu-id="755a4-160">Bu veren gelen güvenlik belirteçleri kabul etmek için bu veren için geçerli bir ad döndürülecek IssuerNameRegistry yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="755a4-160">To accept security tokens from this issuer, configure the IssuerNameRegistry to return a valid name for this issuer.</span></span>|<span data-ttu-id="755a4-161">Bu hata, bir parmak izi MMC ek bileşeninden kopyalayıp içine yapıştırarak kaynaklanabilir *Web.config* dosya.</span><span class="sxs-lookup"><span data-stu-id="755a4-161">This error can be caused by copying a thumbprint from the MMC snap-in and pasting it into the *Web.config* file.</span></span> <span data-ttu-id="755a4-162">Özellikle, sertifika Özellikler penceresinden kopyalarken metin dizesinde yazdırılamayan fazladan bir karakter alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="755a4-162">Specifically, you can get an extra non-printable character in the text string when copying from the certificate properties window.</span></span> <span data-ttu-id="755a4-163">Bu ek karakter parmak izi eşleşme başarısız olmasına neden olur. Parmak izi doğru kopyalamak için yordam şurada bulunabilir: [http://msdn.microsoft.com/library/ff359102.aspx](http://msdn.microsoft.com/library/ff359102.aspx)</span><span class="sxs-lookup"><span data-stu-id="755a4-163">This extra character causes the thumbprint match to fail.The procedure for correctly copying the thumbprint can be found here: [http://msdn.microsoft.com/library/ff359102.aspx](http://msdn.microsoft.com/library/ff359102.aspx)</span></span>|  
  
## <a name="related-items"></a><span data-ttu-id="755a4-164">İlgili öğeler</span><span class="sxs-lookup"><span data-stu-id="755a4-164">Related Items</span></span>  
  
-   [<span data-ttu-id="755a4-165">İzlemeleri görüntüleme bağıntılı için hizmet izleme görüntüleyicisini kullanma ve sorun giderme</span><span class="sxs-lookup"><span data-stu-id="755a4-165">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](http://msdn.microsoft.com/library/aa751795.aspx)
