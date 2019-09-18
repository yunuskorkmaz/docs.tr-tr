---
title: 'Nasıl yapılır: WIF Kullanarak Talep Kullanan ASP.NET MVC Web Uygulaması Derleme'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4d245288b04d8ed3d997bc5572b40c7f8a9334e5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045441"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a><span data-ttu-id="46202-102">Nasıl yapılır: WIF Kullanarak Talep Kullanan ASP.NET MVC Web Uygulaması Derleme</span><span class="sxs-lookup"><span data-stu-id="46202-102">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="46202-103">Uygulanan Öğe</span><span class="sxs-lookup"><span data-stu-id="46202-103">Applies To</span></span>  
  
- <span data-ttu-id="46202-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="46202-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="46202-105">ASP.NET® MVC</span><span class="sxs-lookup"><span data-stu-id="46202-105">ASP.NET® MVC</span></span>  
  
## <a name="summary"></a><span data-ttu-id="46202-106">Özet</span><span class="sxs-lookup"><span data-stu-id="46202-106">Summary</span></span>  
 <span data-ttu-id="46202-107">Bu nasıl yapılır, basit talepler kullanan ASP.NET MVC web uygulaması oluşturmaya yönelik ayrıntılı adım adım yordamlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="46202-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET MVC web application.</span></span> <span data-ttu-id="46202-108">Ayrıca, talep tabanlı kimlik doğrulamasının başarılı bir şekilde uygulanması için basit talep kullanan ASP.NET MVC web uygulamasını test etme hakkında yönergeler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="46202-108">It also provides instructions how to test the simple claims-aware ASP.NET MVC web application for successful implementation of claims-based authentication.</span></span> <span data-ttu-id="46202-109">Bu nasıl yapılır, güvenlik belirteci hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler içermez ve zaten bir STS yapılandırdığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="46202-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="46202-110">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="46202-110">Contents</span></span>  
  
- <span data-ttu-id="46202-111">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="46202-111">Objectives</span></span>  
  
- <span data-ttu-id="46202-112">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="46202-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="46202-113">1\. adım – basit ASP.NET MVC uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="46202-113">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
- <span data-ttu-id="46202-114">2\. adım – ASP.NET MVC uygulamasını talep tabanlı kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="46202-114">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="46202-115">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="46202-115">Step 3 – Test Your Solution</span></span>  
  
- <span data-ttu-id="46202-116">İlgili öğeler</span><span class="sxs-lookup"><span data-stu-id="46202-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="46202-117">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="46202-117">Objectives</span></span>  
  
- <span data-ttu-id="46202-118">Talep tabanlı kimlik doğrulaması için ASP.NET MVC web uygulamasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="46202-118">Configure ASP.NET MVC web application for claims-based authentication</span></span>  
  
- <span data-ttu-id="46202-119">Test başarılı talep kullanan ASP.NET MVC web uygulaması</span><span class="sxs-lookup"><span data-stu-id="46202-119">Test successful claims-aware ASP.NET MVC web application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="46202-120">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="46202-120">Summary of Steps</span></span>  
  
- <span data-ttu-id="46202-121">1\. adım – basit ASP.NET MVC uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="46202-121">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
- <span data-ttu-id="46202-122">2\. adım – ASP.NET MVC uygulamasını talep tabanlı kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="46202-122">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="46202-123">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="46202-123">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a><span data-ttu-id="46202-124">1\. adım – basit ASP.NET MVC uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="46202-124">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
 <span data-ttu-id="46202-125">Bu adımda, yeni bir ASP.NET MVC uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="46202-125">In this step, you will create a new ASP.NET MVC application.</span></span>  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a><span data-ttu-id="46202-126">Basit ASP.NET MVC uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="46202-126">To create simple ASP.NET MVC application</span></span>  
  
1. <span data-ttu-id="46202-127">Visual Studio 'Yu başlatın ve **Dosya**, **Yeni**ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="46202-127">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="46202-128">**Yeni proje** penceresinde, **ASP.NET MVC 3 Web uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="46202-128">In the **New Project** window, click **ASP.NET MVC 3 Web Application**.</span></span>  
  
3. <span data-ttu-id="46202-129">**Ad**alanına girin `TestApp` ve **Tamam**' a basın.</span><span class="sxs-lookup"><span data-stu-id="46202-129">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="46202-130">**Yeni ASP.NET MVC 3 proje** iletişim kutusunda, kullanılabilir şablonlardan **Internet uygulaması** ' nı seçin, **Görünüm altyapısının** **Razor**olarak ayarlandığından emin olun ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="46202-130">In the **New ASP.NET MVC 3 Project** dialog, select **Internet Application** from the available templates, ensure **View Engine** is set to **Razor**, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="46202-131">Yeni proje açıldığında, **Çözüm Gezgini** ' de **TestApp** projesine sağ tıklayın ve **Özellikler** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="46202-131">When the new project opens, right-click the **TestApp** project in **Solution Explorer** and select the **Properties** option.</span></span>  
  
6. <span data-ttu-id="46202-132">Projenin Özellikler sayfasında, sol taraftaki **Web** sekmesine tıklayın ve **yerel IIS Web sunucusu kullan** seçeneğinin işaretli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="46202-132">On the project’s properties page, click on the **Web** tab on the left and ensure that the **Use Local IIS Web Server** option is selected.</span></span>  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="46202-133">2\. adım – ASP.NET MVC uygulamasını talep tabanlı kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="46202-133">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="46202-134">Bu adımda, ASP.NET MVC web uygulamanızın *Web. config* yapılandırma dosyasına, talebe göre haberdar olmak için yapılandırma girdileri ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="46202-134">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET MVC web application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="46202-135">Talep tabanlı kimlik doğrulaması için ASP.NET MVC uygulamasını yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="46202-135">To configure ASP.NET MVC application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="46202-136">Aşağıdaki yapılandırma bölümü tanımlarını *Web. config* yapılandırma dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46202-136">Add the following configuration section definitions to the *Web.config* configuration file.</span></span> <span data-ttu-id="46202-137">Bu, Windows Identity Foundation için gereken yapılandırma bölümlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="46202-137">These define configuration sections required by Windows Identity Foundation.</span></span> <span data-ttu-id="46202-138">Yapılandırma > açma öğesinden hemen sonra  **\<** tanımları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="46202-138">Add the definitions immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. <span data-ttu-id="46202-139">Uygulamanın Federasyon meta verilerine erişim sağlayan bir  **\<konum >** öğesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="46202-139">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3. <span data-ttu-id="46202-140">Kullanıcıları reddetmek, yerel kimlik doğrulamasını devre dışı bırakmak ve kimlik doğrulamasını yönetmek için WIF 'yi etkinleştirmek için  **\<System. Web >** öğelerine aşağıdaki yapılandırma girdilerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46202-140">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. <span data-ttu-id="46202-141">Aşağıdaki Windows Identity Foundation ile ilgili yapılandırma girdilerini ekleyin ve ASP.net uygulamanızın URL 'si ile bağlantı noktası  **\<>** **numarasının,**  **\<** WSFederation > öğesi ve  **\<WSFederation >** öğesinin **Reply** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="46202-141">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="46202-142">Ayrıca, **verenin** değerinin güvenlik belirteci HIZMETI (STS) URL 'nize uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="46202-142">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
5. <span data-ttu-id="46202-143"><xref:System.IdentityModel> Derlemeye başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46202-143">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
6. <span data-ttu-id="46202-144">Hata olduğundan emin olmak için çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="46202-144">Compile the solution to make sure there are errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="46202-145">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="46202-145">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="46202-146">Bu adımda, talep tabanlı kimlik doğrulaması için yapılandırılmış ASP.NET MVC web uygulamanızı test edersiniz.</span><span class="sxs-lookup"><span data-stu-id="46202-146">In this step you will test your ASP.NET MVC web application configured for claims-based authentication.</span></span> <span data-ttu-id="46202-147">Temel test gerçekleştirmek için, güvenlik belirteci hizmeti (STS) tarafından verilen belirteçte talepleri görüntüleyen basit bir kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="46202-147">To perform basic test you will add simple code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="46202-148">Talep tabanlı kimlik doğrulaması için ASP.NET MVC uygulamanızı test etmek için</span><span class="sxs-lookup"><span data-stu-id="46202-148">To test your ASP.NET MVC application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="46202-149">**Çözüm Gezgini**, **denetleyiciler** klasörünü genişletin ve *HomeController.cs* dosyasını düzenleyicide açın.</span><span class="sxs-lookup"><span data-stu-id="46202-149">In the **Solution Explorer**, expand the **Controllers** folder and open *HomeController.cs* file in the editor.</span></span> <span data-ttu-id="46202-150">Aşağıdaki kodu **Dizin** yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="46202-150">Add the following code to the **Index** method:</span></span>  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. <span data-ttu-id="46202-151">**Çözüm Gezgini** , **Görünümler** ' i ve ardından **giriş** klasörleri ' ni genişletin ve ardından düzenleyicide *Index. cshtml* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="46202-151">In the **Solution Explorer** expand **Views** and then **Home** folders and open *Index.cshtml* file in the editor.</span></span> <span data-ttu-id="46202-152">İçeriğini silin ve aşağıdaki biçimlendirmeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="46202-152">Delete its contents and add the following markup:</span></span>  
  
    ```html  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
    ```  
  
3. <span data-ttu-id="46202-153">**F5** tuşuna basarak çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="46202-153">Run the solution by pressing the **F5** key.</span></span>  
  
4. <span data-ttu-id="46202-154">Güvenlik belirteci hizmeti tarafından size verilen belirteçteki talepleri görüntüleyen sayfayla birlikte sunulmalısınız.</span><span class="sxs-lookup"><span data-stu-id="46202-154">You should be presented with the page that displays the claims in the token that was issued to you by Security Token Service.</span></span>  
  
## <a name="related-items"></a><span data-ttu-id="46202-155">İlgili öğeler</span><span class="sxs-lookup"><span data-stu-id="46202-155">Related Items</span></span>  
  
- [<span data-ttu-id="46202-156">Nasıl yapılır: WıF kullanarak talep kullanan ASP.NET Web Forms uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="46202-156">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
