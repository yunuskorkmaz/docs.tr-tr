---
title: 'Nasıl yapılır: WIF izlemeyi etkinleştirme'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 459d74f3faf9fab4cba047a87ccff77d193e9026
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399571"
---
# <a name="how-to-enable-wif-tracing"></a><span data-ttu-id="b690e-102">Nasıl yapılır: WIF izlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b690e-102">How To: Enable WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="b690e-103">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="b690e-103">Applies To</span></span>  
  
-   <span data-ttu-id="b690e-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="b690e-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="b690e-105">ASP.NET® Web formları</span><span class="sxs-lookup"><span data-stu-id="b690e-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="b690e-106">Özet</span><span class="sxs-lookup"><span data-stu-id="b690e-106">Summary</span></span>  
 <span data-ttu-id="b690e-107">Bu yöntem, bir ASP.NET uygulamasında WIF izlemeyi etkinleştirmek için ayrıntılı adım adım yordamlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b690e-107">This How-To provides detailed step-by-step procedures for enabling WIF tracing in an ASP.NET application.</span></span> <span data-ttu-id="b690e-108">Günlük doğru şekilde çalıştığını ve ayrıca İzleme dinleyicisi doğrulamak için uygulamayı test etme yönergeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b690e-108">It also provides instructions testing the application to verify that the trace listener and log are working correctly.</span></span> <span data-ttu-id="b690e-109">Bu 'Nasıl Yapılır' konusunda bir Güvenlik Belirteci Hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bunun yerine Kimlik ve Erişim aracı ile birlikte gelen Geliştirme STS'si kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b690e-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="b690e-110">Geliştirme STS'si gerçek kimlik doğrulaması yapmaz ve yalnızca test amaçlarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="b690e-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="b690e-111">Bu 'Nasıl Yapılır' konusunu tamamlamak için Kimlik ve Erişim aracını yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b690e-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="b690e-112">Şu konumdan indirilebilir: [kimlik ve erişim aracı](http://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="b690e-112">It can be downloaded from the following location: [Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b690e-113">Pasif uygulamalar için WIF izlemeyi etkinleştirme, diğer bir deyişle, WS-Federasyon protokolünü kullanan uygulamalar olası sunabilir kötü amaçlı bir tarafa (DoS) hizmet reddi saldırılarını veya bilgilerin açığa çıkmasına uygulama.</span><span class="sxs-lookup"><span data-stu-id="b690e-113">Enabling WIF tracing for passive applications, that is, applications that use the WS-Federation protocol, can potentially expose the application to denial of service (DoS) attacks or to information disclosure to a malicious party.</span></span> <span data-ttu-id="b690e-114">Bu, pasif RPs ve Pasif STSes içerir.</span><span class="sxs-lookup"><span data-stu-id="b690e-114">This includes both passive RPs and passive STSes.</span></span> <span data-ttu-id="b690e-115">Bu nedenle, WIF izleme edilgen RPs veya STSes için bir üretim ortamında etkinleştirmenizi değil öneririz.</span><span class="sxs-lookup"><span data-stu-id="b690e-115">For this reason, we recommend that you not enable WIF tracing for passive RPs or STSes in a production environment.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="b690e-116">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="b690e-116">Contents</span></span>  
  
-   <span data-ttu-id="b690e-117">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="b690e-117">Objectives</span></span>  
  
-   <span data-ttu-id="b690e-118">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b690e-118">Overview</span></span>  
  
-   <span data-ttu-id="b690e-119">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="b690e-119">Summary of Steps</span></span>  
  
-   <span data-ttu-id="b690e-120">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve izlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b690e-120">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
  
-   <span data-ttu-id="b690e-121">2. adım – çözümünüzü</span><span class="sxs-lookup"><span data-stu-id="b690e-121">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="b690e-122">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="b690e-122">Objectives</span></span>  
  
-   <span data-ttu-id="b690e-123">WIF ve geliştirme STS kimlik ve erişim aracı kullanan basit bir ASP.NET uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b690e-123">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
-   <span data-ttu-id="b690e-124">İzlemeyi etkinleştirmek ve çalışır durumda olduğunu doğrulayın</span><span class="sxs-lookup"><span data-stu-id="b690e-124">Enable tracing and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="b690e-125">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b690e-125">Overview</span></span>  
 <span data-ttu-id="b690e-126">İzleme, hata ayıklama ve türlerde WIF belirteçleri, tanımlama bilgileri, talepler, protokol iletilerini ve daha da dahil olmak üzere, sorunları gidermenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b690e-126">Tracing enables you to debug and troubleshoot many types of issues with WIF, including tokens, cookies, claims, protocol messages, and more.</span></span> <span data-ttu-id="b690e-127">WIF izleme WCF izlemeyi benzer; Örneğin, her şeyi kritik iletileri için tüm iletileri görüntülemek için izlemeleri ayrıntı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b690e-127">WIF tracing is similar to WCF tracing; for example, you can choose the verbosity of traces to display everything from critical messages to all messages.</span></span> <span data-ttu-id="b690e-128">WIF izlemeleri oluşturulabilir **.xml** dosyaları veya **.svclog** hizmet izleme Görüntüleyicisi aracı kullanarak görüntülenebilir dosyaları.</span><span class="sxs-lookup"><span data-stu-id="b690e-128">WIF traces can be generated in **.xml** files or in **.svclog** files that are viewable by using the Service Trace Viewer Tool.</span></span> <span data-ttu-id="b690e-129">Bu araç bulunan **bin** Windows SDK yükleme dizini yolu bilgisayarınızda, örneğin: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span><span class="sxs-lookup"><span data-stu-id="b690e-129">This tool is located in the **bin** directory of the Windows SDK install path on your computer, for example: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="b690e-130">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="b690e-130">Summary of Steps</span></span>  
  
-   <span data-ttu-id="b690e-131">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve izlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b690e-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
  
-   <span data-ttu-id="b690e-132">2. adım – çözümünüzü</span><span class="sxs-lookup"><span data-stu-id="b690e-132">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a><span data-ttu-id="b690e-133">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve izlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b690e-133">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
 <span data-ttu-id="b690e-134">Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacak ve değiştirme *Web.config* izlemeyi etkinleştirmek için dosya.</span><span class="sxs-lookup"><span data-stu-id="b690e-134">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable tracing.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="b690e-135">Basit bir ASP.NET uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b690e-135">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="b690e-136">Visual Studio'yu başlatın ve tıklatın **dosya**, **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="b690e-136">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="b690e-137">İçinde **yeni proje** penceresinde tıklatın **ASP.NET Web Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="b690e-137">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="b690e-138">İçinde **adı**, girin `TestApp` ve basın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="b690e-138">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="b690e-139">Sağ **TestApp** altında proje **Çözüm Gezgini**seçeneğini belirleyip **kimlik ve erişim**.</span><span class="sxs-lookup"><span data-stu-id="b690e-139">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5.  <span data-ttu-id="b690e-140">**Kimlik ve erişim** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b690e-140">The **Identity and Access** window appears.</span></span> <span data-ttu-id="b690e-141">Altında **sağlayıcıları**seçin **yerel geliştirme STS ile uygulamanızı Test**, ardından **Uygula**.</span><span class="sxs-lookup"><span data-stu-id="b690e-141">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6.  <span data-ttu-id="b690e-142">Yeni bir klasör oluşturun, adlı **günlükleri** kök **C:** gibi sürücü gösterilen: **C:\logs**</span><span class="sxs-lookup"><span data-stu-id="b690e-142">Create a new folder in named **logs** in the root of the **C:** drive, like shown: **C:\logs**</span></span>  
  
7.  <span data-ttu-id="b690e-143">Aşağıdakileri ekleyin  **\<system.diagnostics >** öğesine *Web.config* hemen kapanış aşağıdaki yapılandırma dosyası  **\</configSections >** öğesi gibi gösterilir:</span><span class="sxs-lookup"><span data-stu-id="b690e-143">Add the following **\<system.diagnostics>** element to the *Web.config* configuration file immediately following the closing **\</configSections>** element, like shown:</span></span>  
  
    ```xml  
    <configuration>  
        <configSections>  
        …  
        </configSections>  
        <system.diagnostics>  
            <sources>  
                <source name="System.IdentityModel" switchValue="Verbose">  
                    <listeners>  
                        <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="C:\logs\WIF.xml" />  
                    </listeners>  
                </source>  
            </sources>  
            <trace autoflush="true" />  
        </system.diagnostics>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b690e-144">Belirtilen dizin konumu **initializeData** günlüğü başlamadan önce özniteliği bulunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b690e-144">The directory location specified in the **initializeData** attribute must exist before logging can begin.</span></span> <span data-ttu-id="b690e-145">Günlük konumu mevcut değilse oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b690e-145">If the location does not exist, no logs will be created.</span></span>  
  
     <span data-ttu-id="b690e-146">Yukarıdaki yapılandırma ayarlarını etkinleştirir **ayrıntılı** WIF için izleme ve sonuçta elde edilen günlüğe kaydetme **C:logsWIF.xml** dosya.</span><span class="sxs-lookup"><span data-stu-id="b690e-146">The configuration settings above will enable **Verbose** tracing for WIF and save the resulting log to the **C:logsWIF.xml** file.</span></span>  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="b690e-147">2. adım – çözümünüzü</span><span class="sxs-lookup"><span data-stu-id="b690e-147">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="b690e-148">Bu adımda, günlükleri kayıtlı olduğunu doğrulamak için WIF etkinleştirilmiş ASP.NET uygulamanızı test.</span><span class="sxs-lookup"><span data-stu-id="b690e-148">In this step, you will test your WIF-enabled ASP.NET application to verify that logs are being recorded.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a><span data-ttu-id="b690e-149">Başarılı izleme için ASP.NET WIF özellikli uygulamanızı test etmek için</span><span class="sxs-lookup"><span data-stu-id="b690e-149">To test your WIF-enabled ASP.NET application for successful tracing</span></span>  
  
1.  <span data-ttu-id="b690e-150">Tuşlarına basarak çözümü çalıştırın **F5** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="b690e-150">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="b690e-151">Varsayılan ASP.NET giriş sayfası ile sunulan ve gerekir otomatik olarak kullanıcı adıyla kimlik doğrulaması *Terry*, geliştirme STS tarafından döndürülen varsayılan kullanıcı olduğu.</span><span class="sxs-lookup"><span data-stu-id="b690e-151">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2.  <span data-ttu-id="b690e-152">Tarayıcı penceresini kapatın ve ardından gidin **C:\logs** klasör.</span><span class="sxs-lookup"><span data-stu-id="b690e-152">Close the browser window and then navigate to the **C:\logs** folder.</span></span> <span data-ttu-id="b690e-153">Açık **C:\logs\WIF.xml** bir metin düzenleyicisi kullanarak dosya.</span><span class="sxs-lookup"><span data-stu-id="b690e-153">Open the **C:\logs\WIF.xml** file using a text editor.</span></span>  
  
3.  <span data-ttu-id="b690e-154">İnceleme **WIF.xml** dosya ve başlayarak girişleri içerdiğini doğrulayın  **\<E2ETraceEvent >**.</span><span class="sxs-lookup"><span data-stu-id="b690e-154">Inspect the **WIF.xml** file and verify that it contains entries starting with **\<E2ETraceEvent>**.</span></span> <span data-ttu-id="b690e-155">Bu izlemeler içerecek  **\<TraceRecord >** izlenen etkinliğinin açıklamalarını öğeleri gibi **doğrulama SecurityToken**.</span><span class="sxs-lookup"><span data-stu-id="b690e-155">These traces will contain **\<TraceRecord>** elements with descriptions for the traced activity, such as **Validating SecurityToken**.</span></span>
