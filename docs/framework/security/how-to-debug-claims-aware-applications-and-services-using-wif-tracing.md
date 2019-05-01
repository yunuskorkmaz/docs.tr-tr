---
title: 'Nasıl yapılır: WIF İzleme Kullanarak Talep Kullanan Uygulama ve Hizmetlerde Hata Ayıklama'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: 43fa859aa84189817dffe74ecd72253ab9b82585
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940497"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a><span data-ttu-id="f5aca-102">Nasıl yapılır: WIF İzleme Kullanarak Talep Kullanan Uygulama ve Hizmetlerde Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f5aca-102">How To: Debug Claims-Aware Applications And Services Using WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="f5aca-103">Uygulanan Öğe</span><span class="sxs-lookup"><span data-stu-id="f5aca-103">Applies To</span></span>  
  
- <span data-ttu-id="f5aca-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="f5aca-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="f5aca-105">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="f5aca-105">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>  
  
- <span data-ttu-id="f5aca-106">WIF uygulamalarında hata ayıklama ve sorun giderme</span><span class="sxs-lookup"><span data-stu-id="f5aca-106">Troubleshooting and Debugging WIF Applications</span></span>  
  
## <a name="summary"></a><span data-ttu-id="f5aca-107">Özet</span><span class="sxs-lookup"><span data-stu-id="f5aca-107">Summary</span></span>  
 <span data-ttu-id="f5aca-108">İzlemeyi analiz etmek nasıl izleme Görüntüleyicisi aracı kullanarak kaydeder ve bu'nasıl yapılır WIF izlemeyi yapılandırma, izleme günlükleri toplamak gerekli adımlar açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5aca-108">This How-To describes required steps for how to configure WIF tracing, collect trace logs, and how to analyze the trace logs using Trace Viewer tool.</span></span> <span data-ttu-id="f5aca-109">Bu izleme girişleri WIF ilgili sorunları gidermek için gerekli eylemleri için genel eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5aca-109">It provides general mapping for trace entries to actions needed to troubleshoot issues related to WIF.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="f5aca-110">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="f5aca-110">Contents</span></span>  
  
- <span data-ttu-id="f5aca-111">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="f5aca-111">Objectives</span></span>  
  
- <span data-ttu-id="f5aca-112">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="f5aca-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="f5aca-113">1. adım – WIF Web.config yapılandırma dosyası kullanarak izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f5aca-113">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
- <span data-ttu-id="f5aca-114">2. adım: WIF izleme dosyaları izleme Görüntüleyicisi aracı kullanarak analiz edin</span><span class="sxs-lookup"><span data-stu-id="f5aca-114">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
- <span data-ttu-id="f5aca-115">3. adım – WIF düzeltmek için çözümleri tanımla ilgili sorunlar</span><span class="sxs-lookup"><span data-stu-id="f5aca-115">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
- <span data-ttu-id="f5aca-116">İlgili öğeler</span><span class="sxs-lookup"><span data-stu-id="f5aca-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="f5aca-117">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="f5aca-117">Objectives</span></span>  
  
- <span data-ttu-id="f5aca-118">WIF izlemeyi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f5aca-118">Configure WIF tracing.</span></span>  
  
- <span data-ttu-id="f5aca-119">Görünüm izleme izleme Görüntüleyicisi Aracı'nda günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f5aca-119">View trace logs in the Trace Viewer tool.</span></span>  
  
- <span data-ttu-id="f5aca-120">WIF tanımlamak ilgili sorunları izleme günlüğüne kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f5aca-120">Identify WIF related issues in the trace logs.</span></span>  
  
- <span data-ttu-id="f5aca-121">Uygulama WIF düzeltici eylemler ilgili sorunları izleme günlükleri bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="f5aca-121">Apply corrective actions to WIF related issues found in the trace logs.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="f5aca-122">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="f5aca-122">Summary of Steps</span></span>  
  
- <span data-ttu-id="f5aca-123">1. adım – WIF Web.config yapılandırma dosyası kullanarak izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f5aca-123">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
- <span data-ttu-id="f5aca-124">2. adım: WIF izleme dosyaları izleme Görüntüleyicisi aracı kullanarak analiz edin</span><span class="sxs-lookup"><span data-stu-id="f5aca-124">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
- <span data-ttu-id="f5aca-125">3. adım – WIF düzeltmek için çözümleri tanımla ilgili sorunlar</span><span class="sxs-lookup"><span data-stu-id="f5aca-125">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="f5aca-126">1. adım – WIF Web.config yapılandırma dosyası kullanarak izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f5aca-126">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
 <span data-ttu-id="f5aca-127">Bu adımda, yapılandırma bölümlerine değişiklikleri ekleyeceksiniz *Web.config* olaylarını izleme ve izleme günlüğüne saklamak WIF etkinleştirme dosya.</span><span class="sxs-lookup"><span data-stu-id="f5aca-127">In this step, you will add changes to configuration sections in the *Web.config* file that enable WIF to trace its events and store them in a trace log.</span></span>  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="f5aca-128">Web.config yapılandırma dosyası kullanarak WIF izlemeyi yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="f5aca-128">To configure WIF tracing using Web.config configuration file</span></span>  
  
1. <span data-ttu-id="f5aca-129">Açın **Web.config** veya **App.config** yapılandırma dosyası içinde bulunan çift tıklayarak Visual Studio düzenleyicisinde **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="f5aca-129">Open the root **Web.config** or **App.config** configuration file in the Visual Studio editor by double clicking on it in **Solution Explorer**.</span></span> <span data-ttu-id="f5aca-130">Çözümünüzü yoksa **Web.config** veya **App.config** yapılandırma dosyasında, çözüm üzerinde sağ tıklayarak ekleyin **Çözüm Gezgini** tıklayıp **Ekleme**, ardından **yeni öğe...** .</span><span class="sxs-lookup"><span data-stu-id="f5aca-130">If your solution does not have **Web.config** or **App.config** configuration file, add it by right clicking on the solution in the **Solution Explorer** and clicking **Add**, then clicking **New Item…**.</span></span> <span data-ttu-id="f5aca-131">Üzerinde **yeni öğe** iletişim kutusunda, **uygulama yapılandırma dosyası** için **App.config** veya **Web yapılandırma dosyası** için**Web.config** listesi ve **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="f5aca-131">On the **New Item** dialog, Select **Application Configuration File** for **App.config** or **Web Configuration File** for **Web.config** from the list and click **OK**.</span></span>  
  
2. <span data-ttu-id="f5aca-132">Yapılandırma dosyası içinde aşağıdaki gibi yapılandırma girdileri eklemek  **\<yapılandırma >** düğüm yapılandırma dosyasının sonunda:</span><span class="sxs-lookup"><span data-stu-id="f5aca-132">Add the configuration entries similar to the following to the configuration file inside **\<configuration>** node at the end of the configuration file:</span></span>  
  
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
  
3. <span data-ttu-id="f5aca-133">Yukarıdaki yapılandırma ayrıntılı izleme olayları oluşturmak ve bunları oturum WIF bildirir *WIFTrace.e2e* dosya.</span><span class="sxs-lookup"><span data-stu-id="f5aca-133">The above configuration instructs WIF to generate verbose trace events and log them into *WIFTrace.e2e* file.</span></span> <span data-ttu-id="f5aca-134">Değerleri için tam bir listesi için **switchValue** değiştirmek, aşağıdaki konuda bulunan izleme düzeyini tabloya bakın: [İzlemeyi Yapılandırma](../wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="f5aca-134">For a complete list of values for the **switchValue** switch, refer to the Trace Level table found in the following topic: [Configuring Tracing](../wcf/diagnostics/tracing/configuring-tracing.md).</span></span>  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a><span data-ttu-id="f5aca-135">2. adım: WIF izleme dosyaları izleme Görüntüleyicisi aracı kullanarak analiz edin</span><span class="sxs-lookup"><span data-stu-id="f5aca-135">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
 <span data-ttu-id="f5aca-136">Bu adımda, WIF izleme günlükleri analiz etmek için izleme Görüntüleyicisi aracı (SvcTraceViewer.exe) kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5aca-136">In this step, you will use the Trace Viewer Tool (SvcTraceViewer.exe) to analyze WIF trace logs.</span></span>  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a><span data-ttu-id="f5aca-137">İzleme Görüntüleyicisi aracı (SvcTraceViewer.exe) kullanarak WIF izleme günlükleri analiz etmek için</span><span class="sxs-lookup"><span data-stu-id="f5aca-137">To analyze WIF trace logs using Trace Viewer tool (SvcTraceViewer.exe)</span></span>  
  
1. <span data-ttu-id="f5aca-138">İzleme Görüntüleyicisi aracı (SvcTraceViewer.exe), Windows SDK'ın bir parçası olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="f5aca-138">Trace Viewer tool (SvcTraceViewer.exe) ships as part of the Windows SDK.</span></span> <span data-ttu-id="f5aca-139">Windows SDK'yı henüz yüklemediyseniz, buradan indirebilirsiniz: [Windows SDK'sı](https://www.microsoft.com/download/en/details.aspx?id=8279).</span><span class="sxs-lookup"><span data-stu-id="f5aca-139">If you haven’t already installed the Windows SDK, you can download it here: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).</span></span>  
  
2. <span data-ttu-id="f5aca-140">İzleme Görüntüleyicisi aracı (SvcTraceViewer.exe) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f5aca-140">Run the Trace Viewer tool (SvcTraceViewer.exe).</span></span> <span data-ttu-id="f5aca-141">Genellikle kullanılabilir **Bin** yükleme yolunun klasör.</span><span class="sxs-lookup"><span data-stu-id="f5aca-141">It is typically available in the **Bin** folder of the installation path.</span></span>  
  
3. <span data-ttu-id="f5aca-142">WIF izleme günlük dosyası, örneğin, seçerek WIFTrace.e2e açın **dosya**, **Aç...**</span><span class="sxs-lookup"><span data-stu-id="f5aca-142">Open the WIF trace log file, for example, WIFTrace.e2e by selecting **File**, **Open…**</span></span> <span data-ttu-id="f5aca-143">seçenek menüde veya bu adı kullanıyor **Ctrl + O** kısayol.</span><span class="sxs-lookup"><span data-stu-id="f5aca-143">option in the menu or using the **Ctrl+O** shortcut.</span></span> <span data-ttu-id="f5aca-144">İzleme günlük dosyası izleme Görüntüleyicisi aracı açılır.</span><span class="sxs-lookup"><span data-stu-id="f5aca-144">The trace log file opens in the Trace Viewer tool.</span></span>  
  
4. <span data-ttu-id="f5aca-145">Girdileri gözden **etkinlik** sekmesi. Her girdi, bir etkinlik sayısı, günlüğe kaydedilen izlemeleri sayısı, süresi etkinliği ve kendi başlangıç ve bitiş zaman damgası içermelidir.</span><span class="sxs-lookup"><span data-stu-id="f5aca-145">Review entries in the **Activity** tab. Each entry should contain an activity number, the number of traces that were logged, duration of the activity and its start and end timestamps.</span></span>  
  
5. <span data-ttu-id="f5aca-146">Tıklayarak **etkinlik** sekmesi. Ayrıntılı izleme girişleri aracının ana alanında görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5aca-146">Click on the **Activity** tab. You should see detailed trace entries in the main area of the tool.</span></span> <span data-ttu-id="f5aca-147">Kullanım **düzeyi** menüsünde belirli düzeyde izleme, örneğin filtre uygulamak için açılır liste: **Tüm**, **uyarı**, **hataları**, **bilgi**vb.</span><span class="sxs-lookup"><span data-stu-id="f5aca-147">Use the **Level** dropdown list on the menu to filter specific level of traces, for example: **All**, **Warning**, **Errors**, **Information**, etc.</span></span>  
  
6. <span data-ttu-id="f5aca-148">Belirli izleme girişleri alt alanında aracı ayrıntıları görüntülemek için tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f5aca-148">Click on specific trace entries to review the details in the lower area of the tool.</span></span> <span data-ttu-id="f5aca-149">Ayrıntıları kullanarak görüntülenebilir **biçimlendirilmiş** ve **XML** karşılık gelen sekmelerini seçerek görünümü.</span><span class="sxs-lookup"><span data-stu-id="f5aca-149">The details can be viewed using **Formatted** and **XML** view by choosing corresponding tabs.</span></span>  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="f5aca-150">3. adım – WIF düzeltmek için çözümleri tanımla ilgili sorunlar</span><span class="sxs-lookup"><span data-stu-id="f5aca-150">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
 <span data-ttu-id="f5aca-151">Bu adımda WIF izleme günlüğü ve izleme Görüntüleyicisi Aracı'nı kullanarak belirlenmiş WIF ilgili sorunlara yönelik çözümler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5aca-151">In this step, you can identify solutions for WIF-related issues identified by using the WIF trace log and Trace Viewer tool.</span></span> <span data-ttu-id="f5aca-152">Genel özetler WIF eşleme ilgili olası bir çözüm ya da sorunu gidermek için gerekli eylemleri için özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="f5aca-152">It outlines general mapping of WIF related exceptions to potential solutions or required actions to troubleshoot the issue.</span></span>  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="f5aca-153">WIF düzeltmek için çözümleri tanımlamak için ilgili sorunlar</span><span class="sxs-lookup"><span data-stu-id="f5aca-153">To identify solutions to fix WIF related issues</span></span>  
  
1. <span data-ttu-id="f5aca-154">Aşağıdaki tabloda WIF özel durumlar ve sorunları düzeltmek için gerekli eylemleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="f5aca-154">Review the following table of WIF exceptions and the required actions to correct the issues.</span></span>  
  
|<span data-ttu-id="f5aca-155">**Hata Kimliği**</span><span class="sxs-lookup"><span data-stu-id="f5aca-155">**Error ID**</span></span>|<span data-ttu-id="f5aca-156">**Hata iletisi**</span><span class="sxs-lookup"><span data-stu-id="f5aca-156">**Error Message**</span></span>|<span data-ttu-id="f5aca-157">**Hatayı düzeltmek eylem gerekli**</span><span class="sxs-lookup"><span data-stu-id="f5aca-157">**Action needed to fix the error**</span></span>|  
|-|-|-|  
|<span data-ttu-id="f5aca-158">ID4175</span><span class="sxs-lookup"><span data-stu-id="f5aca-158">ID4175</span></span>|<span data-ttu-id="f5aca-159">Güvenlik belirteci veren IssuerNameRegistry tarafından tanınmadı.</span><span class="sxs-lookup"><span data-stu-id="f5aca-159">The issuer of the security token was not recognized by the IssuerNameRegistry.</span></span>  <span data-ttu-id="f5aca-160">Bu veren güvenlik belirteçleri kabul etmek için geçerli bir verenin adı döndürülecek IssuerNameRegistry yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f5aca-160">To accept security tokens from this issuer, configure the IssuerNameRegistry to return a valid name for this issuer.</span></span>|<span data-ttu-id="f5aca-161">Bu hata, bir parmak izi MMC ek bileşeninden kopyalayıp yapıştırarak kaynaklanabilir *Web.config* dosya.</span><span class="sxs-lookup"><span data-stu-id="f5aca-161">This error can be caused by copying a thumbprint from the MMC snap-in and pasting it into the *Web.config* file.</span></span> <span data-ttu-id="f5aca-162">Özellikle, sertifika Özellikler penceresinden kopyalarken metin dizesinde yazdırılamayan ekstra bir karakter alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5aca-162">Specifically, you can get an extra non-printable character in the text string when copying from the certificate properties window.</span></span> <span data-ttu-id="f5aca-163">Bu ek karakter parmak izi eşleşme başarısız olmasına neden olur. Parmak izi doğru bir şekilde kopyalamak için yordam şu yolda bulunabilir: [talep tabanlı çoklu oturum açma-üzerinde Web uygulamaları ve Microsoft Azure için](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).</span><span class="sxs-lookup"><span data-stu-id="f5aca-163">This extra character causes the thumbprint match to fail.The procedure for correctly copying the thumbprint can be found at [Claims-Based Single Sign-On for the Web and Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).</span></span>|  
  
## <a name="related-items"></a><span data-ttu-id="f5aca-164">İlgili öğeler</span><span class="sxs-lookup"><span data-stu-id="f5aca-164">Related Items</span></span>  
  
- [<span data-ttu-id="f5aca-165">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma</span><span class="sxs-lookup"><span data-stu-id="f5aca-165">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
