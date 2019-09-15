---
title: 'Nasıl yapılır: WIF İzleme Kullanarak Talep Kullanan Uygulama ve Hizmetlerde Hata Ayıklama'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: 604ebf5ad71197f6614ffa45b6d7c181d474e1aa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990474"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a><span data-ttu-id="3a5cd-102">Nasıl yapılır: WIF İzleme Kullanarak Talep Kullanan Uygulama ve Hizmetlerde Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3a5cd-102">How To: Debug Claims-Aware Applications And Services Using WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="3a5cd-103">Uygulanan Öğe</span><span class="sxs-lookup"><span data-stu-id="3a5cd-103">Applies To</span></span>  
  
- <span data-ttu-id="3a5cd-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="3a5cd-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="3a5cd-105">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="3a5cd-105">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>  
  
- <span data-ttu-id="3a5cd-106">WıF uygulamalarında sorun giderme ve hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="3a5cd-106">Troubleshooting and Debugging WIF Applications</span></span>  
  
## <a name="summary"></a><span data-ttu-id="3a5cd-107">Özet</span><span class="sxs-lookup"><span data-stu-id="3a5cd-107">Summary</span></span>  
 <span data-ttu-id="3a5cd-108">Bu nasıl yapılır, WıF izlemenin nasıl yapılandırılacağı, İzleme günlüklerinin toplanması ve izleme günlüklerini Izleme Görüntüleyicisi aracını kullanarak nasıl analiz edileceği için gereken adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-108">This How-To describes required steps for how to configure WIF tracing, collect trace logs, and how to analyze the trace logs using Trace Viewer tool.</span></span> <span data-ttu-id="3a5cd-109">WıF ile ilgili sorunları gidermek için gereken eylemlere izleme girişleri için genel eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-109">It provides general mapping for trace entries to actions needed to troubleshoot issues related to WIF.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="3a5cd-110">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="3a5cd-110">Contents</span></span>  
  
- <span data-ttu-id="3a5cd-111">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="3a5cd-111">Objectives</span></span>  
  
- <span data-ttu-id="3a5cd-112">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="3a5cd-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="3a5cd-113">Adım 1 – Web. config yapılandırma dosyasını kullanarak WıF Izlemeyi yapılandırın</span><span class="sxs-lookup"><span data-stu-id="3a5cd-113">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
- <span data-ttu-id="3a5cd-114">2\. adım – Izleme Görüntüleyicisi aracını kullanarak WıF Izleme dosyalarını çözümleme</span><span class="sxs-lookup"><span data-stu-id="3a5cd-114">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
- <span data-ttu-id="3a5cd-115">3\. adım – Ilgili sorunları gidermek için çözümleri tanımla</span><span class="sxs-lookup"><span data-stu-id="3a5cd-115">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
- <span data-ttu-id="3a5cd-116">İlgili öğeler</span><span class="sxs-lookup"><span data-stu-id="3a5cd-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="3a5cd-117">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="3a5cd-117">Objectives</span></span>  
  
- <span data-ttu-id="3a5cd-118">WıF izlemeyi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-118">Configure WIF tracing.</span></span>  
  
- <span data-ttu-id="3a5cd-119">İzleme günlüklerini Izleme Görüntüleyicisi aracında görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-119">View trace logs in the Trace Viewer tool.</span></span>  
  
- <span data-ttu-id="3a5cd-120">İzleme günlüklerinde WıF ile ilgili sorunları belirler.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-120">Identify WIF related issues in the trace logs.</span></span>  
  
- <span data-ttu-id="3a5cd-121">İzleme günlüklerinde ilgili sorun yaşıyorsanız WIF düzeltme eylemleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-121">Apply corrective actions to WIF related issues found in the trace logs.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="3a5cd-122">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="3a5cd-122">Summary of Steps</span></span>  
  
- <span data-ttu-id="3a5cd-123">Adım 1 – Web. config yapılandırma dosyasını kullanarak WıF Izlemeyi yapılandırın</span><span class="sxs-lookup"><span data-stu-id="3a5cd-123">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
- <span data-ttu-id="3a5cd-124">2\. adım – Izleme Görüntüleyicisi aracını kullanarak WıF Izleme dosyalarını çözümleme</span><span class="sxs-lookup"><span data-stu-id="3a5cd-124">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
- <span data-ttu-id="3a5cd-125">3\. adım – Ilgili sorunları gidermek için çözümleri tanımla</span><span class="sxs-lookup"><span data-stu-id="3a5cd-125">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="3a5cd-126">Adım 1 – Web. config yapılandırma dosyasını kullanarak WıF Izlemeyi yapılandırın</span><span class="sxs-lookup"><span data-stu-id="3a5cd-126">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
 <span data-ttu-id="3a5cd-127">Bu adımda, *Web. config* dosyasındaki yapılandırma bölümlerine değişiklikler ekleyerek, olaylarının izlenmesini ve bir izleme günlüğünde depolanmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-127">In this step, you will add changes to configuration sections in the *Web.config* file that enable WIF to trace its events and store them in a trace log.</span></span>  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="3a5cd-128">Web. config yapılandırma dosyasını kullanarak WıF izlemeyi yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="3a5cd-128">To configure WIF tracing using Web.config configuration file</span></span>  
  
1. <span data-ttu-id="3a5cd-129">**Çözüm Gezgini**içinde çift tıklayarak kök **Web. config** veya **app. config** yapılandırma dosyasını Visual Studio düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-129">Open the root **Web.config** or **App.config** configuration file in the Visual Studio editor by double clicking on it in **Solution Explorer**.</span></span> <span data-ttu-id="3a5cd-130">Çözümünüz **Web. config** veya **app. config** yapılandırma dosyasına sahip değilse, **Çözüm Gezgini** çözüme sağ tıklayıp **Ekle**' ye tıklayın ve ardından **Yeni öğe... öğesine**tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-130">If your solution does not have **Web.config** or **App.config** configuration file, add it by right clicking on the solution in the **Solution Explorer** and clicking **Add**, then clicking **New Item…**.</span></span> <span data-ttu-id="3a5cd-131">**Yeni öğe** iletişim kutusunda, listeden **app. config** veya Web **. config** Için **Web yapılandırma dosyası** Için **uygulama yapılandırma dosyası** ' nı seçin ve **Tamam**' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-131">On the **New Item** dialog, Select **Application Configuration File** for **App.config** or **Web Configuration File** for **Web.config** from the list and click **OK**.</span></span>  
  
2. <span data-ttu-id="3a5cd-132">Yapılandırma dosyasının sonundaki yapılandırma  **\<>** düğümü içindeki yapılandırma dosyasına benzer yapılandırma girdilerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3a5cd-132">Add the configuration entries similar to the following to the configuration file inside **\<configuration>** node at the end of the configuration file:</span></span>  
  
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
  
3. <span data-ttu-id="3a5cd-133">Yukarıdaki yapılandırma, WıF 'nin ayrıntılı izleme olayları oluşturmasını ve bunları *Wiftrace. e2e* dosyasında oturum açmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-133">The above configuration instructs WIF to generate verbose trace events and log them into *WIFTrace.e2e* file.</span></span> <span data-ttu-id="3a5cd-134">**SwitchValue** anahtarı için değerlerin tamamen listesi için, aşağıdaki konuda bulunan izleme düzeyi tablosuna bakın: [Izleme yapılandırılıyor](../wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="3a5cd-134">For a complete list of values for the **switchValue** switch, refer to the Trace Level table found in the following topic: [Configuring Tracing](../wcf/diagnostics/tracing/configuring-tracing.md).</span></span>  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a><span data-ttu-id="3a5cd-135">2\. adım – Izleme Görüntüleyicisi aracını kullanarak WıF Izleme dosyalarını çözümleme</span><span class="sxs-lookup"><span data-stu-id="3a5cd-135">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
 <span data-ttu-id="3a5cd-136">Bu adımda, WıF izleme günlüklerini çözümlemek için Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe) kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-136">In this step, you will use the Trace Viewer Tool (SvcTraceViewer.exe) to analyze WIF trace logs.</span></span>  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a><span data-ttu-id="3a5cd-137">Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe) kullanarak WıF izleme günlüklerini çözümlemek için</span><span class="sxs-lookup"><span data-stu-id="3a5cd-137">To analyze WIF trace logs using Trace Viewer tool (SvcTraceViewer.exe)</span></span>  
  
1. <span data-ttu-id="3a5cd-138">İzleme Görüntüleyicisi Aracı (SvcTraceViewer. exe) Windows SDK bir parçası olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-138">Trace Viewer tool (SvcTraceViewer.exe) ships as part of the Windows SDK.</span></span> <span data-ttu-id="3a5cd-139">Windows SDK henüz yüklemediyseniz, buradan indirebilirsiniz: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).</span><span class="sxs-lookup"><span data-stu-id="3a5cd-139">If you haven’t already installed the Windows SDK, you can download it here: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).</span></span>  
  
2. <span data-ttu-id="3a5cd-140">Izleme Görüntüleyici aracını (SvcTraceViewer. exe) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-140">Run the Trace Viewer tool (SvcTraceViewer.exe).</span></span> <span data-ttu-id="3a5cd-141">Genellikle yükleme yolunun **bin** klasöründe bulunur.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-141">It is typically available in the **Bin** folder of the installation path.</span></span>  
  
3. <span data-ttu-id="3a5cd-142">WıF izleme günlük dosyasını açın, örneğin, **Dosya**, **Aç..** . öğesini seçerek wiftrace. e2e.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-142">Open the WIF trace log file, for example, WIFTrace.e2e by selecting **File**, **Open…**</span></span> <span data-ttu-id="3a5cd-143">menüsünde veya **CTRL + O** kısayolunu kullanarak seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-143">option in the menu or using the **Ctrl+O** shortcut.</span></span> <span data-ttu-id="3a5cd-144">İzleme günlüğü dosyası Izleme Görüntüleyici aracında açılır.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-144">The trace log file opens in the Trace Viewer tool.</span></span>  
  
4. <span data-ttu-id="3a5cd-145">**Etkinlik** sekmesindeki girişleri gözden geçirin. Her giriş bir etkinlik numarası, günlüğe kaydedilen izleme sayısı, etkinliğin süresi ve başlangıç ve bitiş zaman damgaları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-145">Review entries in the **Activity** tab. Each entry should contain an activity number, the number of traces that were logged, duration of the activity and its start and end timestamps.</span></span>  
  
5. <span data-ttu-id="3a5cd-146">**Etkinlik** sekmesine tıklayın. Aracının ana alanında ayrıntılı izleme girişleri görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-146">Click on the **Activity** tab. You should see detailed trace entries in the main area of the tool.</span></span> <span data-ttu-id="3a5cd-147">Belirli izleme düzeyini filtrelemek için menüdeki **düzey** açılan listesini kullanın, örneğin: **Tümü**, **Uyarı**, **hatalar**, **bilgiler**vb.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-147">Use the **Level** dropdown list on the menu to filter specific level of traces, for example: **All**, **Warning**, **Errors**, **Information**, etc.</span></span>  
  
6. <span data-ttu-id="3a5cd-148">Aracın alt alanındaki ayrıntıları gözden geçirmek için belirli izleme girişlerine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-148">Click on specific trace entries to review the details in the lower area of the tool.</span></span> <span data-ttu-id="3a5cd-149">Ayrıntılar, ilgili sekmeler seçilerek **biçimlendirilen** ve **XML** görünümü kullanılarak görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-149">The details can be viewed using **Formatted** and **XML** view by choosing corresponding tabs.</span></span>  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="3a5cd-150">3\. adım – Ilgili sorunları gidermek için çözümleri tanımla</span><span class="sxs-lookup"><span data-stu-id="3a5cd-150">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
 <span data-ttu-id="3a5cd-151">Bu adımda, WıF izleme günlüğü ve Izleme Görüntüleyicisi Aracı kullanılarak tanımlanan WıF ile ilgili sorunların çözümlerini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-151">In this step, you can identify solutions for WIF-related issues identified by using the WIF trace log and Trace Viewer tool.</span></span> <span data-ttu-id="3a5cd-152">Sorunu gidermek için, olası çözümlerin veya gerekli eylemlerin genel eşleştirmesiyle ilgili genel eşlemeyi özetler.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-152">It outlines general mapping of WIF related exceptions to potential solutions or required actions to troubleshoot the issue.</span></span>  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="3a5cd-153">WıF ile ilgili sorunları gidermeye yönelik çözümleri belirlemek için</span><span class="sxs-lookup"><span data-stu-id="3a5cd-153">To identify solutions to fix WIF related issues</span></span>  
  
1. <span data-ttu-id="3a5cd-154">Sorunları düzeltmek için aşağıdaki WıF özel durumları ve gerekli eylemleri tablosunu inceleyin.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-154">Review the following table of WIF exceptions and the required actions to correct the issues.</span></span>  
  
|<span data-ttu-id="3a5cd-155">**Hata KIMLIĞI**</span><span class="sxs-lookup"><span data-stu-id="3a5cd-155">**Error ID**</span></span>|<span data-ttu-id="3a5cd-156">**Hata Iletisi**</span><span class="sxs-lookup"><span data-stu-id="3a5cd-156">**Error Message**</span></span>|<span data-ttu-id="3a5cd-157">**Hatayı onarmak için gereken eylem**</span><span class="sxs-lookup"><span data-stu-id="3a5cd-157">**Action needed to fix the error**</span></span>|  
|-|-|-|  
|<span data-ttu-id="3a5cd-158">ID4175</span><span class="sxs-lookup"><span data-stu-id="3a5cd-158">ID4175</span></span>|<span data-ttu-id="3a5cd-159">Güvenlik belirtecini veren ıssuernameregyıpu tarafından tanınmadı.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-159">The issuer of the security token was not recognized by the IssuerNameRegistry.</span></span>  <span data-ttu-id="3a5cd-160">Bu verenin güvenlik belirteçlerini kabul etmek için, ıssuernameregyıpı ' yi bu veren için geçerli bir ad döndürecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-160">To accept security tokens from this issuer, configure the IssuerNameRegistry to return a valid name for this issuer.</span></span>|<span data-ttu-id="3a5cd-161">Bu hata, MMC ek bileşeninden bir parmak izi kopyalanarak ve *Web. config* dosyasına yapıştırılarak meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-161">This error can be caused by copying a thumbprint from the MMC snap-in and pasting it into the *Web.config* file.</span></span> <span data-ttu-id="3a5cd-162">Özellikle, sertifika özellikleri penceresinden kopyalama yaparken metin dizesinde yazdırılabilir bir ek karakter alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-162">Specifically, you can get an extra non-printable character in the text string when copying from the certificate properties window.</span></span> <span data-ttu-id="3a5cd-163">Bu ek karakter, parmak izinin başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-163">This extra character causes the thumbprint match to fail.</span></span> <span data-ttu-id="3a5cd-164">Parmak izini doğru şekilde kopyalama yordamı, [Web Için talep tabanlı çoklu oturum açma ve Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="3a5cd-164">The procedure for correctly copying the thumbprint can be found at [Claims-Based Single Sign-On for the Web and Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).</span></span>|  
  
## <a name="related-items"></a><span data-ttu-id="3a5cd-165">İlgili öğeler</span><span class="sxs-lookup"><span data-stu-id="3a5cd-165">Related Items</span></span>  
  
- [<span data-ttu-id="3a5cd-166">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma</span><span class="sxs-lookup"><span data-stu-id="3a5cd-166">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
