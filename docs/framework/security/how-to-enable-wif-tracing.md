---
title: 'Nasıl yapılır: WIF İzlemeyi Etkinleştirme'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
ms.openlocfilehash: 40349c5aac7634a515b40a9cc1ab5e75492600c4
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971514"
---
# <a name="how-to-enable-wif-tracing"></a><span data-ttu-id="ea4b2-102">Nasıl yapılır: WIF İzlemeyi Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="ea4b2-102">How To: Enable WIF Tracing</span></span>

## <a name="applies-to"></a><span data-ttu-id="ea4b2-103">Uygulanan Öğe</span><span class="sxs-lookup"><span data-stu-id="ea4b2-103">Applies To</span></span>

- <span data-ttu-id="ea4b2-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="ea4b2-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="ea4b2-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="ea4b2-105">ASP.NET® Web Forms</span></span>

## <a name="summary"></a><span data-ttu-id="ea4b2-106">Özet</span><span class="sxs-lookup"><span data-stu-id="ea4b2-106">Summary</span></span>

<span data-ttu-id="ea4b2-107">Bu nasıl yapılır, bir ASP.NET uygulamasında WıF izlemeyi etkinleştirmek için ayrıntılı adım adım yordamlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-107">This How-To provides detailed step-by-step procedures for enabling WIF tracing in an ASP.NET application.</span></span> <span data-ttu-id="ea4b2-108">Ayrıca, İzleme dinleyicisinin ve günlüğün düzgün çalıştığını doğrulamak üzere uygulamayı test eden yönergeler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-108">It also provides instructions testing the application to verify that the trace listener and log are working correctly.</span></span> <span data-ttu-id="ea4b2-109">Bu 'Nasıl Yapılır' konusunda bir Güvenlik Belirteci Hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bunun yerine Kimlik ve Erişim aracı ile birlikte gelen Geliştirme STS'si kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="ea4b2-110">Geliştirme STS'si gerçek kimlik doğrulaması yapmaz ve yalnızca test amaçlarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="ea4b2-111">Bu 'Nasıl Yapılır' konusunu tamamlamak için Kimlik ve Erişim aracını yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="ea4b2-112">Bu, aşağıdaki konumdan indirilebilir: [Kimlik ve erişim aracı](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="ea4b2-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea4b2-113">Pasif uygulamalar için WıF izlemeyi etkinleştirmek, diğer bir deyişle, WS-Federation protokolünü kullanan uygulamalar, uygulamayı hizmet reddi (DoS) saldırılarına veya kötü amaçlı bir tarafa yönelik bilgilerin açığa çıkmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-113">Enabling WIF tracing for passive applications, that is, applications that use the WS-Federation protocol, can potentially expose the application to denial of service (DoS) attacks or to information disclosure to a malicious party.</span></span> <span data-ttu-id="ea4b2-114">Bu, hem pasif RPs hem de pasif stler içerir.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-114">This includes both passive RPs and passive STSes.</span></span> <span data-ttu-id="ea4b2-115">Bu nedenle, bir üretim ortamında pasif RPs veya stler için WıF izlemeyi etkinleştirmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-115">For this reason, we recommend that you not enable WIF tracing for passive RPs or STSes in a production environment.</span></span>

## <a name="contents"></a><span data-ttu-id="ea4b2-116">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="ea4b2-116">Contents</span></span>

- <span data-ttu-id="ea4b2-117">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="ea4b2-117">Objectives</span></span>

- <span data-ttu-id="ea4b2-118">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ea4b2-118">Overview</span></span>

- <span data-ttu-id="ea4b2-119">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="ea4b2-119">Summary of Steps</span></span>

- <span data-ttu-id="ea4b2-120">1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve Izlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="ea4b2-120">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>

- <span data-ttu-id="ea4b2-121">2\. Adım – Çözümünüzü test etme</span><span class="sxs-lookup"><span data-stu-id="ea4b2-121">Step 2 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="ea4b2-122">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="ea4b2-122">Objectives</span></span>

- <span data-ttu-id="ea4b2-123">Kimlik ve erişim aracından WıF ve geliştirme STS 'sini kullanan basit bir ASP.NET uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="ea4b2-123">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>

- <span data-ttu-id="ea4b2-124">İzlemeyi etkinleştirme ve çalıştığını doğrulama</span><span class="sxs-lookup"><span data-stu-id="ea4b2-124">Enable tracing and verify that it is working</span></span>

## <a name="overview"></a><span data-ttu-id="ea4b2-125">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ea4b2-125">Overview</span></span>

<span data-ttu-id="ea4b2-126">İzleme, belirteçler, tanımlama bilgileri, talepler, protokol iletileri ve daha fazlası dahil olmak üzere WıF ile ilgili birçok tür sorunu ayıklamanıza ve gidermenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-126">Tracing enables you to debug and troubleshoot many types of issues with WIF, including tokens, cookies, claims, protocol messages, and more.</span></span> <span data-ttu-id="ea4b2-127">WıF izleme, WCF izlemeye benzerdir; Örneğin, kritik iletilerden tüm iletilere her şeyi görüntüleyen izlemelerin ayrıntı düzeyini seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-127">WIF tracing is similar to WCF tracing; for example, you can choose the verbosity of traces to display everything from critical messages to all messages.</span></span> <span data-ttu-id="ea4b2-128">WıF izlemeleri **. xml** dosyalarında veya hizmet Izleme Görüntüleyicisi Aracı kullanılarak görüntülenebilen **. svclog** dosyalarında oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-128">WIF traces can be generated in **.xml** files or in **.svclog** files that are viewable by using the Service Trace Viewer Tool.</span></span> <span data-ttu-id="ea4b2-129">Bu araç, bilgisayarınızdaki Windows SDK yüklemesi yolunun **bin** dizininde bulunur, örneğin: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-129">This tool is located in the **bin** directory of the Windows SDK install path on your computer, for example: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="ea4b2-130">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="ea4b2-130">Summary of Steps</span></span>

- <span data-ttu-id="ea4b2-131">1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve Izlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="ea4b2-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>

- <span data-ttu-id="ea4b2-132">2\. Adım – Çözümünüzü test etme</span><span class="sxs-lookup"><span data-stu-id="ea4b2-132">Step 2 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a><span data-ttu-id="ea4b2-133">1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve Izlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="ea4b2-133">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>

<span data-ttu-id="ea4b2-134">Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacak ve izlemeyi etkinleştirmek için *Web. config* dosyasını değiştirecaksınız.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-134">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable tracing.</span></span>

### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="ea4b2-135">Basit bir ASP.NET uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ea4b2-135">To create a simple ASP.NET application</span></span>

1. <span data-ttu-id="ea4b2-136">Visual Studio 'Yu başlatın ve **Dosya**, **Yeni**ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-136">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>

2. <span data-ttu-id="ea4b2-137">**Yeni proje** penceresinde, **ASP.NET Web Forms uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-137">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>

3. <span data-ttu-id="ea4b2-138">**Ad**alanına girin `TestApp` ve **Tamam**' a basın.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-138">In **Name**, enter `TestApp` and press **OK**.</span></span>

4. <span data-ttu-id="ea4b2-139">**Çözüm Gezgini**altında **TestApp** projesine sağ tıklayın **ve ardından kimlik ve erişim**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-139">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>

5. <span data-ttu-id="ea4b2-140">**Kimlik ve erişim** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-140">The **Identity and Access** window appears.</span></span> <span data-ttu-id="ea4b2-141">**Sağlayıcılar**bölümünde, **yerel geliştirme sts 'Si Ile uygulamanızı test et**' i seçin ve **Uygula**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-141">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>

6. <span data-ttu-id="ea4b2-142">**C:** sürücüsünün kökündeki adlandırılmış **günlüklerde** aşağıda gösterildiği gibi yeni bir klasör oluşturun: **C:\logs.**</span><span class="sxs-lookup"><span data-stu-id="ea4b2-142">Create a new folder in named **logs** in the root of the **C:** drive, like shown: **C:\logs**</span></span>

7. <span data-ttu-id="ea4b2-143">Aşağıda gösterildiği gibi,  **Kapanış\</configSections >** öğesinin hemen ardından *Web. config* yapılandırma dosyasına aşağıdaki  **\<System. Diagnostics >** öğesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ea4b2-143">Add the following **\<system.diagnostics>** element to the *Web.config* configuration file immediately following the closing **\</configSections>** element, like shown:</span></span>

    ```xml
    <configuration>
        <configSections>
            ...
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
    > <span data-ttu-id="ea4b2-144">Günlük kaydı başlamadan önce **ınitializedata** özniteliğinde belirtilen dizin konumu mevcut olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-144">The directory location specified in the **initializeData** attribute must exist before logging can begin.</span></span> <span data-ttu-id="ea4b2-145">Konum yoksa, hiçbir günlük oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-145">If the location does not exist, no logs will be created.</span></span>

     <span data-ttu-id="ea4b2-146">Yukarıdaki yapılandırma ayarları WıF için **ayrıntılı** izlemeyi etkinleştirir ve elde edilen günlüğü **C:logswif.xml** dosyasına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-146">The configuration settings above will enable **Verbose** tracing for WIF and save the resulting log to the **C:logsWIF.xml** file.</span></span>

## <a name="step-2--test-your-solution"></a><span data-ttu-id="ea4b2-147">2\. Adım – Çözümünüzü test etme</span><span class="sxs-lookup"><span data-stu-id="ea4b2-147">Step 2 – Test Your Solution</span></span>

<span data-ttu-id="ea4b2-148">Bu adımda, günlüklerin kaydedildiğini doğrulamak üzere WıF özellikli ASP.NET uygulamanızı test edersiniz.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-148">In this step, you will test your WIF-enabled ASP.NET application to verify that logs are being recorded.</span></span>

### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a><span data-ttu-id="ea4b2-149">WıF özellikli ASP.NET uygulamanızı başarıyla izleme için sınamak için</span><span class="sxs-lookup"><span data-stu-id="ea4b2-149">To test your WIF-enabled ASP.NET application for successful tracing</span></span>

1. <span data-ttu-id="ea4b2-150">**F5** tuşuna basarak çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-150">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="ea4b2-151">Varsayılan ASP.NET ana sayfası ve geliştirme STS tarafından döndürülen varsayılan kullanıcı olan *Terry*adlı Kullanıcı adı ile otomatik olarak kimlik doğrulaması yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-151">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>

2. <span data-ttu-id="ea4b2-152">Tarayıcı penceresini kapatın ve **C:\logs** klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-152">Close the browser window and then navigate to the **C:\logs** folder.</span></span> <span data-ttu-id="ea4b2-153">Bir metin düzenleyicisi kullanarak **C:\logs\wif.xml** dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-153">Open the **C:\logs\WIF.xml** file using a text editor.</span></span>

3. <span data-ttu-id="ea4b2-154">**WIF. xml** dosyasını inceleyin ve  **\<E2ETraceEvent >** ile başlayan girdileri içerdiğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-154">Inspect the **WIF.xml** file and verify that it contains entries starting with **\<E2ETraceEvent>**.</span></span> <span data-ttu-id="ea4b2-155">Bu izlemeler, **SecurityToken doğrulaması**gibi izlenen etkinliğin açıklamalarını içeren izleme  **\<ecord >** öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ea4b2-155">These traces will contain **\<TraceRecord>** elements with descriptions for the traced activity, such as **Validating SecurityToken**.</span></span>
