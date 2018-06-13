---
title: 'Nasıl yapılır: WIF kullanarak talep kullanan ASP.NET MVC Web uygulaması oluşturma'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 146724f31e1d09f09f94d102366539dc79ddfe02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399155"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a><span data-ttu-id="b02d4-102">Nasıl yapılır: WIF kullanarak talep kullanan ASP.NET MVC Web uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b02d4-102">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="b02d4-103">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="b02d4-103">Applies To</span></span>  
  
-   <span data-ttu-id="b02d4-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="b02d4-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="b02d4-105">ASP.NET® MVC</span><span class="sxs-lookup"><span data-stu-id="b02d4-105">ASP.NET® MVC</span></span>  
  
## <a name="summary"></a><span data-ttu-id="b02d4-106">Özet</span><span class="sxs-lookup"><span data-stu-id="b02d4-106">Summary</span></span>  
 <span data-ttu-id="b02d4-107">Bu yöntem, basit talep kullanan ASP.NET MVC web uygulaması oluşturmak için ayrıntılı adım adım yordamlar verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b02d4-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET MVC web application.</span></span> <span data-ttu-id="b02d4-108">Ayrıca basit talep kullanan ASP.NET MVC web uygulaması için talep tabanlı kimlik doğrulaması başarılı uyarlamasını test etme yönergeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b02d4-108">It also provides instructions how to test the simple claims-aware ASP.NET MVC web application for successful implementation of claims-based authentication.</span></span> <span data-ttu-id="b02d4-109">Bu yöntem bir güvenlik belirteci hizmeti (STS) oluşturmak için ayrıntılı yönergeler sahip değil ve bir STS zaten yapılandırmış olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="b02d4-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="b02d4-110">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="b02d4-110">Contents</span></span>  
  
-   <span data-ttu-id="b02d4-111">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="b02d4-111">Objectives</span></span>  
  
-   <span data-ttu-id="b02d4-112">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="b02d4-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="b02d4-113">1. adım – basit ASP.NET MVC uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b02d4-113">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
-   <span data-ttu-id="b02d4-114">2. adım – ASP.NET MVC uygulaması talep tabanlı kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b02d4-114">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="b02d4-115">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="b02d4-115">Step 3 – Test Your Solution</span></span>  
  
-   <span data-ttu-id="b02d4-116">İlgili öğeler</span><span class="sxs-lookup"><span data-stu-id="b02d4-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="b02d4-117">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="b02d4-117">Objectives</span></span>  
  
-   <span data-ttu-id="b02d4-118">ASP.NET MVC web uygulaması talep tabanlı kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b02d4-118">Configure ASP.NET MVC web application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="b02d4-119">Başarılı talep kullanan ASP.NET MVC web uygulamasını test</span><span class="sxs-lookup"><span data-stu-id="b02d4-119">Test successful claims-aware ASP.NET MVC web application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="b02d4-120">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="b02d4-120">Summary of Steps</span></span>  
  
-   <span data-ttu-id="b02d4-121">1. adım – basit ASP.NET MVC uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b02d4-121">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
-   <span data-ttu-id="b02d4-122">2. adım – ASP.NET MVC uygulaması talep tabanlı kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b02d4-122">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="b02d4-123">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="b02d4-123">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a><span data-ttu-id="b02d4-124">1. adım – basit ASP.NET MVC uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b02d4-124">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
 <span data-ttu-id="b02d4-125">Bu adımda, yeni bir ASP.NET MVC uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b02d4-125">In this step, you will create a new ASP.NET MVC application.</span></span>  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a><span data-ttu-id="b02d4-126">Basit bir ASP.NET MVC uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b02d4-126">To create simple ASP.NET MVC application</span></span>  
  
1.  <span data-ttu-id="b02d4-127">Visual Studio'yu başlatın ve tıklatın **dosya**, **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="b02d4-127">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="b02d4-128">İçinde **yeni proje** penceresinde tıklatın **ASP.NET MVC 3 Web uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="b02d4-128">In the **New Project** window, click **ASP.NET MVC 3 Web Application**.</span></span>  
  
3.  <span data-ttu-id="b02d4-129">İçinde **adı**, girin `TestApp` ve basın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="b02d4-129">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="b02d4-130">İçinde **yeni ASP.NET MVC 3 projesinin** iletişim kutusunda **Internet uygulama** kullanılabilir şablonlardan olun **görünüm altyapısı** ayarlanır **Razor**ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="b02d4-130">In the **New ASP.NET MVC 3 Project** dialog, select **Internet Application** from the available templates, ensure **View Engine** is set to **Razor**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="b02d4-131">Yeni proje açıldığında sağ **TestApp** proje **Çözüm Gezgini** seçip **özellikleri** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="b02d4-131">When the new project opens, right-click the **TestApp** project in **Solution Explorer** and select the **Properties** option.</span></span>  
  
6.  <span data-ttu-id="b02d4-132">Projenin Özellikler sayfasında, tıklatın **Web** sekmesinde solda ve emin olun **kullanım yerel IIS Web sunucusu** seçeneği işaretlidir.</span><span class="sxs-lookup"><span data-stu-id="b02d4-132">On the project’s properties page, click on the **Web** tab on the left and ensure that the **Use Local IIS Web Server** option is selected.</span></span>  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="b02d4-133">2. adım – ASP.NET MVC uygulaması talep tabanlı kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b02d4-133">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="b02d4-134">Bu adımda yapılandırma girişlere ekleyeceksiniz *Web.config* talep kullanan yapmak için ASP.NET MVC web uygulamanızın yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="b02d4-134">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET MVC web application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="b02d4-135">ASP.NET MVC uygulaması talep tabanlı kimlik doğrulaması için yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="b02d4-135">To configure ASP.NET MVC application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="b02d4-136">Aşağıdaki yapılandırma bölümüne tanımları eklemek *Web.config* yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="b02d4-136">Add the following configuration section definitions to the *Web.config* configuration file.</span></span> <span data-ttu-id="b02d4-137">Bunlar Windows Identity Foundation tarafından gereken yapılandırma bölümlerinin tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b02d4-137">These define configuration sections required by Windows Identity Foundation.</span></span> <span data-ttu-id="b02d4-138">Tanımları ekleme hemen sonra  **\<configuration >** açılış öğe:</span><span class="sxs-lookup"><span data-stu-id="b02d4-138">Add the definitions immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  <span data-ttu-id="b02d4-139">Ekleme bir  **\<konumu >** uygulamanın Federasyon meta verilerine erişim sağlayan öğe:</span><span class="sxs-lookup"><span data-stu-id="b02d4-139">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3.  <span data-ttu-id="b02d4-140">İçinde aşağıdaki yapılandırma girdileri eklemek  **\<system.web >** kullanıcıları reddedecek şekilde öğeleri yerel kimlik doğrulamasını devre dışı ve kimlik doğrulamasını yönetmek WIF etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="b02d4-140">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  <span data-ttu-id="b02d4-141">Aşağıdaki Windows Identity Foundation, ASP.NET uygulamanızın URL ve bağlantı noktası numarası değerleri eşleştiğinden emin olun ve ilgili yapılandırma girdileri eklemek  **\<AudienceUri >** girişi **bölgesi**  özniteliği  **\<wsFederation >** öğesi ve **yanıt** özniteliği  **\<wsFederation >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="b02d4-141">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="b02d4-142">Ayrıca emin **veren** değer uygun güvenlik belirteci hizmeti (STS) URL'nizi.</span><span class="sxs-lookup"><span data-stu-id="b02d4-142">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
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
  
5.  <span data-ttu-id="b02d4-143">Başvuru ekleme <xref:System.IdentityModel> derleme.</span><span class="sxs-lookup"><span data-stu-id="b02d4-143">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
6.  <span data-ttu-id="b02d4-144">Hataları emin olmak için çözüm derleyin.</span><span class="sxs-lookup"><span data-stu-id="b02d4-144">Compile the solution to make sure there are errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="b02d4-145">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="b02d4-145">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="b02d4-146">Bu adımda talep tabanlı kimlik doğrulaması için yapılandırılmış ASP.NET MVC web uygulamanızı test.</span><span class="sxs-lookup"><span data-stu-id="b02d4-146">In this step you will test your ASP.NET MVC web application configured for claims-based authentication.</span></span> <span data-ttu-id="b02d4-147">Temel test gerçekleştirmek için güvenlik belirteci hizmeti (STS) tarafından verilen belirteç talep görüntüler basit kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b02d4-147">To perform basic test you will add simple code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="b02d4-148">Talep tabanlı kimlik doğrulaması için ASP.NET MVC uygulamanızı test etmek için</span><span class="sxs-lookup"><span data-stu-id="b02d4-148">To test your ASP.NET MVC application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="b02d4-149">İçinde **Çözüm Gezgini**, genişletin **denetleyicileri** klasörü ve açık *HomeController.cs* dosyayı düzenleyicide.</span><span class="sxs-lookup"><span data-stu-id="b02d4-149">In the **Solution Explorer**, expand the **Controllers** folder and open *HomeController.cs* file in the editor.</span></span> <span data-ttu-id="b02d4-150">Aşağıdaki kodu ekleyin **dizin** yöntemi:</span><span class="sxs-lookup"><span data-stu-id="b02d4-150">Add the following code to the **Index** method:</span></span>  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2.  <span data-ttu-id="b02d4-151">İçinde **Çözüm Gezgini** genişletin **görünümleri** ve ardından **giriş** klasörleri ve açık *Index.cshtml* dosyayı düzenleyicide.</span><span class="sxs-lookup"><span data-stu-id="b02d4-151">In the **Solution Explorer** expand **Views** and then **Home** folders and open *Index.cshtml* file in the editor.</span></span> <span data-ttu-id="b02d4-152">İçeriğini silin ve aşağıdaki biçimlendirme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b02d4-152">Delete its contents and add the following markup:</span></span>  
  
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
  
3.  <span data-ttu-id="b02d4-153">Tuşlarına basarak çözümü çalıştırın **F5** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="b02d4-153">Run the solution by pressing the **F5** key.</span></span>  
  
4.  <span data-ttu-id="b02d4-154">İçin güvenlik belirteci hizmeti tarafından verilen belirteç talep görüntüler sayfa sunulacaktır.</span><span class="sxs-lookup"><span data-stu-id="b02d4-154">You should be presented with the page that displays the claims in the token that was issued to you by Security Token Service.</span></span>  
  
## <a name="related-items"></a><span data-ttu-id="b02d4-155">İlgili öğeler</span><span class="sxs-lookup"><span data-stu-id="b02d4-155">Related Items</span></span>  
  
-   [<span data-ttu-id="b02d4-156">Nasıl yapılır: WIF Kullanarak Talep Kullanan ASP.NET Web Forms Uygulaması Derleme</span><span class="sxs-lookup"><span data-stu-id="b02d4-156">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
