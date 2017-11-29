---
title: "Nasıl yapılır: Belirteç yeniden yürütme algılaması etkinleştir"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: cde32407f072f3d29af4a8d1aae559e46057ae3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-token-replay-detection"></a><span data-ttu-id="b537b-102">Nasıl yapılır: Belirteç yeniden yürütme algılaması etkinleştir</span><span class="sxs-lookup"><span data-stu-id="b537b-102">How To: Enable Token Replay Detection</span></span>
## <a name="applies-to"></a><span data-ttu-id="b537b-103">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="b537b-103">Applies To</span></span>  
  
-   <span data-ttu-id="b537b-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="b537b-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="b537b-105">ASP.NET® Web formları</span><span class="sxs-lookup"><span data-stu-id="b537b-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="b537b-106">Özet</span><span class="sxs-lookup"><span data-stu-id="b537b-106">Summary</span></span>  
 <span data-ttu-id="b537b-107">Bu yöntem, belirteç yeniden yürütme algılaması WIF kullanan bir ASP.NET uygulamasında etkinleştirmek için ayrıntılı adım adım yordamlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b537b-107">This How-To provides detailed step-by-step procedures for enabling token replay detection in an ASP.NET application that uses WIF.</span></span> <span data-ttu-id="b537b-108">Ayrıca, belirteç yeniden yürütme algılaması etkin olduğunu doğrulamak için uygulamayı test etme için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b537b-108">It also provides instructions for how to test the application to verify that token replay detection is enabled.</span></span> <span data-ttu-id="b537b-109">Bu 'Nasıl Yapılır' konusunda bir Güvenlik Belirteci Hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bunun yerine Kimlik ve Erişim aracı ile birlikte gelen Geliştirme STS'si kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b537b-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="b537b-110">Geliştirme STS'si gerçek kimlik doğrulaması yapmaz ve yalnızca test amaçlarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="b537b-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="b537b-111">Bu 'Nasıl Yapılır' konusunu tamamlamak için Kimlik ve Erişim aracını yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b537b-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="b537b-112">Şu konumdan indirilebilir: [kimlik ve erişim aracı](http://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="b537b-112">It can be downloaded from the following location: [Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="b537b-113">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="b537b-113">Contents</span></span>  
  
-   <span data-ttu-id="b537b-114">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="b537b-114">Objectives</span></span>  
  
-   <span data-ttu-id="b537b-115">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b537b-115">Overview</span></span>  
  
-   <span data-ttu-id="b537b-116">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="b537b-116">Summary of Steps</span></span>  
  
-   <span data-ttu-id="b537b-117">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve etkinleştirme yeniden yürütme algılaması</span><span class="sxs-lookup"><span data-stu-id="b537b-117">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="b537b-118">2. adım – çözümünüzü</span><span class="sxs-lookup"><span data-stu-id="b537b-118">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="b537b-119">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="b537b-119">Objectives</span></span>  
  
-   <span data-ttu-id="b537b-120">WIF ve geliştirme STS kimlik ve erişim aracı kullanan basit bir ASP.NET uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b537b-120">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
-   <span data-ttu-id="b537b-121">Belirteç yeniden yürütme algılaması etkinleştirin ve çalışır durumda olduğunu doğrulayın</span><span class="sxs-lookup"><span data-stu-id="b537b-121">Enable token replay detection and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="b537b-122">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b537b-122">Overview</span></span>  
 <span data-ttu-id="b537b-123">Bir istemci istemcinin zaten kullanmış olduğu bir STS belirteci ile bağlı olan taraf için kimlik doğrulaması çalıştığında yeniden gönderme saldırısı oluşur.</span><span class="sxs-lookup"><span data-stu-id="b537b-123">A replay attack occurs when a client attempts to authenticate to a relying party with an STS token that the client has already used.</span></span> <span data-ttu-id="b537b-124">Bu saldırı önlemeye yardımcı olmak için daha önce kullanılan STS belirteç yeniden yürütme algılama önbelleği WIF içerir.</span><span class="sxs-lookup"><span data-stu-id="b537b-124">To help prevent this attack, WIF contains a replay detection cache of previously used STS tokens.</span></span> <span data-ttu-id="b537b-125">Etkinleştirildiğinde, yeniden yürütme algılaması gelen istek belirteci denetler ve belirteç daha önce kullanılan olup olmadığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="b537b-125">When enabled, replay detection checks the token of the incoming request and verifies whether or not the token has been previously used.</span></span> <span data-ttu-id="b537b-126">Belirteç zaten kullanılıyorsa, isteği reddetti ve <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="b537b-126">If the token has been used already, the request is refused and a <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> exception is thrown.</span></span>  
  
 <span data-ttu-id="b537b-127">Aşağıdaki adımlarda, yeniden yürütme algılaması etkinleştirmek için gereken yapılandırma değişikliklerini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b537b-127">The following steps demonstrate the configuration changes required to enable replay detection.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="b537b-128">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="b537b-128">Summary of Steps</span></span>  
  
-   <span data-ttu-id="b537b-129">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve etkinleştirme yeniden yürütme algılaması</span><span class="sxs-lookup"><span data-stu-id="b537b-129">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="b537b-130">2. adım – çözümünüzü</span><span class="sxs-lookup"><span data-stu-id="b537b-130">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a><span data-ttu-id="b537b-131">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve etkinleştirme yeniden yürütme algılaması</span><span class="sxs-lookup"><span data-stu-id="b537b-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
 <span data-ttu-id="b537b-132">Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacak ve değiştirme *Web.config* yeniden yürütme algılaması sağlamak için dosya.</span><span class="sxs-lookup"><span data-stu-id="b537b-132">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable replay detection.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="b537b-133">Basit bir ASP.NET uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b537b-133">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="b537b-134">Visual Studio'yu başlatın ve tıklatın **dosya**, **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="b537b-134">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="b537b-135">İçinde **yeni proje** penceresinde tıklatın **ASP.NET Web Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="b537b-135">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="b537b-136">İçinde **adı**, girin `TestApp` ve basın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="b537b-136">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="b537b-137">Sağ **TestApp** altında proje **Çözüm Gezgini**seçeneğini belirleyip **kimlik ve erişim**.</span><span class="sxs-lookup"><span data-stu-id="b537b-137">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5.  <span data-ttu-id="b537b-138">**Kimlik ve erişim** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b537b-138">The **Identity and Access** window appears.</span></span> <span data-ttu-id="b537b-139">Altında **sağlayıcıları**seçin **yerel geliştirme STS ile uygulamanızı Test**, ardından **Uygula**.</span><span class="sxs-lookup"><span data-stu-id="b537b-139">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6.  <span data-ttu-id="b537b-140">Aşağıdakileri ekleyin  **\<tokenReplayDetection >** öğesine *Web.config* hemen ardından yapılandırma dosyası  **\<System.IdentityModel >** ve  **\<identityConfiguration >** gibi öğeler, gösterilen:</span><span class="sxs-lookup"><span data-stu-id="b537b-140">Add the following **\<tokenReplayDetection>** element to the *Web.config* configuration file immediately following the **\<system.identityModel>** and **\<identityConfiguration>** elements, like shown:</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="b537b-141">2. adım – çözümünüzü</span><span class="sxs-lookup"><span data-stu-id="b537b-141">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="b537b-142">Bu adımda, yeniden yürütme algılaması etkin olduğunu doğrulamak için WIF etkinleştirilmiş ASP.NET uygulamanızı test.</span><span class="sxs-lookup"><span data-stu-id="b537b-142">In this step, you will test your WIF-enabled ASP.NET application to verify that replay detection has been enabled.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a><span data-ttu-id="b537b-143">Yeniden yürütme algılaması için ASP.NET WIF özellikli uygulamanızı test etmek için</span><span class="sxs-lookup"><span data-stu-id="b537b-143">To test your WIF-enabled ASP.NET application for replay detection</span></span>  
  
1.  <span data-ttu-id="b537b-144">Tuşlarına basarak çözümü çalıştırın **F5** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="b537b-144">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="b537b-145">Varsayılan ASP.NET giriş sayfası ile sunulan ve gerekir otomatik olarak kullanıcı adıyla kimlik doğrulaması *Terry*, geliştirme STS tarafından döndürülen varsayılan kullanıcı olduğu.</span><span class="sxs-lookup"><span data-stu-id="b537b-145">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2.  <span data-ttu-id="b537b-146">Tarayıcının basın **geri** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b537b-146">Press the browser’s **Back** button.</span></span> <span data-ttu-id="b537b-147">İle sunulan bir **'/' uygulamasında sunucu hatası** aşağıdaki açıklama sayfasıyla: *ID1062: yeniden yürütme için algılandı: belirteç: 'System.IdentityModel.Tokens.SamlSecurityToken'* , ve ardından bir *onaylama kimliği* ve bir *veren*.</span><span class="sxs-lookup"><span data-stu-id="b537b-147">You should be presented with a **Server Error in ‘/’ Application** page with the following description: *ID1062: Replay has been detected for: Token: 'System.IdentityModel.Tokens.SamlSecurityToken'*, followed by an *AssertionId* and an *Issuer*.</span></span>  
  
     <span data-ttu-id="b537b-148">Bu hata sayfası için görüyorsunuz türünde bir özel durum <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> belirteç yeniden yürütme algılandığında belirtildi.</span><span class="sxs-lookup"><span data-stu-id="b537b-148">You are seeing this error page because an exception of type <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> was thrown when the token replay was detected.</span></span> <span data-ttu-id="b537b-149">Belirtecin ilk sunulduğunda ilk POST isteği yeniden göndermek denediğinizden bu hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="b537b-149">This error occurs because you are attempting to re-send the initial POST request when the token was first presented.</span></span> <span data-ttu-id="b537b-150">**Geri** düğmesi değil davranışlara neden olur bu sunucuya sonraki isteklerde.</span><span class="sxs-lookup"><span data-stu-id="b537b-150">The **Back** button will not cause this behavior on subsequent requests to the server.</span></span>
