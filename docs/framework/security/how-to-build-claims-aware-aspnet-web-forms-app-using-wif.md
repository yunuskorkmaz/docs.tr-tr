---
title: "Nasıl yapılır: WIF kullanarak talep kullanan ASP.NET Web Forms uygulaması oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: d5b81e20ed1b39c7750329718729905484eb7fa1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a><span data-ttu-id="56094-102">Nasıl yapılır: WIF kullanarak talep kullanan ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="56094-102">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="56094-103">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="56094-103">Applies To</span></span>  
  
-   <span data-ttu-id="56094-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="56094-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="56094-105">ASP.NET® Web formları</span><span class="sxs-lookup"><span data-stu-id="56094-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="56094-106">Özet</span><span class="sxs-lookup"><span data-stu-id="56094-106">Summary</span></span>  
 <span data-ttu-id="56094-107">Bu yöntem basit talep kullanan ASP.NET Web Forms uygulaması oluşturmak için ayrıntılı adım adım yordamlar verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="56094-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET Web Forms application.</span></span> <span data-ttu-id="56094-108">Ayrıca, federe kimlik doğrulaması başarılı uygulama için basit talep kullanan ASP.NET Web Forms uygulamayı test etme için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="56094-108">It also provides instructions for how to test the simple claims-aware ASP.NET Web Forms application for successful implementation of federated authentication.</span></span> <span data-ttu-id="56094-109">Bu yöntem bir güvenlik belirteci hizmeti (STS) oluşturmak için ayrıntılı yönergeler sahip değil ve bir STS zaten yapılandırmış olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="56094-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="56094-110">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="56094-110">Contents</span></span>  
  
-   <span data-ttu-id="56094-111">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="56094-111">Objectives</span></span>  
  
-   <span data-ttu-id="56094-112">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="56094-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="56094-113">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="56094-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="56094-114">2. adım – ASP.NET Web Forms uygulaması talep tabanlı kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="56094-114">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="56094-115">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="56094-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="56094-116">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="56094-116">Objectives</span></span>  
  
-   <span data-ttu-id="56094-117">ASP.NET Web Forms uygulaması talep tabanlı kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="56094-117">Configure ASP.NET Web Forms application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="56094-118">Başarılı talep kullanan ASP.NET Web Forms uygulamayı test etme</span><span class="sxs-lookup"><span data-stu-id="56094-118">Test successful claims-aware ASP.NET Web Forms application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="56094-119">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="56094-119">Summary of Steps</span></span>  
  
-   <span data-ttu-id="56094-120">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="56094-120">Step 1 – Create Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="56094-121">2. adım – ASP.NET Web Forms uygulaması federe kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="56094-121">Step 2 – Configure ASP.NET Web Forms Application for Federated Authentication</span></span>  
  
-   <span data-ttu-id="56094-122">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="56094-122">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="56094-123">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="56094-123">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="56094-124">Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="56094-124">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="56094-125">Basit bir ASP.NET uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="56094-125">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="56094-126">Visual Studio'yu başlatın ve tıklatın **dosya**, **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="56094-126">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="56094-127">İçinde **yeni proje** penceresinde tıklatın **ASP.NET Web Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="56094-127">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="56094-128">İçinde **adı**, girin `TestApp` ve basın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="56094-128">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a><span data-ttu-id="56094-129">2. adım – ASP.NET Web Forms uygulaması talep tabanlı kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="56094-129">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="56094-130">Bu adımda yapılandırma girişlere ekleyeceksiniz *Web.config* talep kullanan ASP.NET Web Forms uygulamanızın yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="56094-130">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET Web Forms application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a><span data-ttu-id="56094-131">ASP.NET uygulama talep tabanlı kimlik doğrulaması için yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="56094-131">To configure ASP.NET application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="56094-132">Aşağıdaki yapılandırma bölümü girdileri eklemek *Web.config* yapılandırma dosyası hemen sonra  **\<configuration >** açılış öğe:</span><span class="sxs-lookup"><span data-stu-id="56094-132">Add the following configuration section entries to the *Web.config* configuration file immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  <span data-ttu-id="56094-133">Ekleme bir  **\<konumu >** uygulamanın Federasyon meta verilerine erişim sağlayan öğe:</span><span class="sxs-lookup"><span data-stu-id="56094-133">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3.  <span data-ttu-id="56094-134">İçinde aşağıdaki yapılandırma girdileri eklemek  **\<system.web >** kullanıcıları reddedecek şekilde öğeleri yerel kimlik doğrulamasını devre dışı ve kimlik doğrulamasını yönetmek WIF etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="56094-134">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  <span data-ttu-id="56094-135">Ekleme bir  **\<system.webServer >** şirket dışı kimlik doğrulaması modülleri tanımlar öğesi.</span><span class="sxs-lookup"><span data-stu-id="56094-135">Add a **\<system.webServer>** element that defines the modules for federated authentication.</span></span> <span data-ttu-id="56094-136">Unutmayın *PublicKeyToken* özniteliği aynı olmalıdır *PublicKeyToken* için öznitelik  **\<configSections >** daha önce eklenen girdileri:</span><span class="sxs-lookup"><span data-stu-id="56094-136">Note that the *PublicKeyToken* attribute must be the same as the *PublicKeyToken* attribute for the **\<configSections>** entries added earlier:</span></span>  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5.  <span data-ttu-id="56094-137">Aşağıdaki Windows Identity Foundation, ASP.NET uygulamanızın URL ve bağlantı noktası numarası değerleri eşleştiğinden emin olun ve ilgili yapılandırma girdileri eklemek  **\<AudienceUri >** girişi **bölgesi**  özniteliği  **\<wsFederation >** öğesi ve **yanıt** özniteliği  **\<wsFederation >**öğesi.</span><span class="sxs-lookup"><span data-stu-id="56094-137">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="56094-138">Ayrıca emin **veren** değer uygun güvenlik belirteci hizmeti (STS) URL'nizi.</span><span class="sxs-lookup"><span data-stu-id="56094-138">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
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
  
6.  <span data-ttu-id="56094-139">Başvuru ekleme <xref:System.IdentityModel> derleme.</span><span class="sxs-lookup"><span data-stu-id="56094-139">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
7.  <span data-ttu-id="56094-140">Hiçbir hata bulunmadığından emin olmak için çözüm derleyin.</span><span class="sxs-lookup"><span data-stu-id="56094-140">Compile the solution to make sure there are no errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="56094-141">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="56094-141">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="56094-142">Bu adımda ASP.NET Web Forms uygulamanızı talep tabanlı kimlik doğrulaması için yapılandırılmış test.</span><span class="sxs-lookup"><span data-stu-id="56094-142">In this step you will test your ASP.NET Web Forms application configured for claims-based authentication.</span></span> <span data-ttu-id="56094-143">Basit bir sınama gerçekleştirmek için güvenlik belirteci hizmeti (STS) tarafından verilen belirteç talep görüntüler kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="56094-143">To perform a basic test, you will add code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a><span data-ttu-id="56094-144">Talep tabanlı kimlik doğrulaması için ASP.NET Web formu uygulamanızı test etmek için</span><span class="sxs-lookup"><span data-stu-id="56094-144">To test your ASP.NET Web Form application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="56094-145">Açık **Default.aspx** altında dosya **TestApp** proje ve varolan biçimlendirme aşağıdaki biçimlendirme ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="56094-145">Open the **Default.aspx** file under the **TestApp** project and replace its existing markup with the following markup:</span></span>  
  
    ```  
    %@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head id="Head1" runat="server">  
        <title></title>  
    </head>  
    <body>  
        <h1><asp:label ID="signedIn" runat="server" /></h1>  
        <asp:label ID="claimType" runat="server" />  
        <asp:label ID="claimValue" runat="server" />  
        <asp:label ID="claimValueType" runat="server" />  
        <asp:label ID="claimSubjectName" runat="server" />  
        <asp:label ID="claimIssuer" runat="server" />  
    </body>  
    </html>  
    ```  
  
2.  <span data-ttu-id="56094-146">Kaydet **Default.aspx**ve kendi kod adlı dosyanın arkasındaki açın **Default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="56094-146">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56094-147">**Default.aspx.cs** altındaki gizlenebilir **Default.aspx** Çözüm Gezgini'nde.</span><span class="sxs-lookup"><span data-stu-id="56094-147">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="56094-148">Varsa **Default.aspx.cs** görünür durumda değilse genişletin **Default.aspx** yanında üçgen tıklayarak.</span><span class="sxs-lookup"><span data-stu-id="56094-148">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
3.  <span data-ttu-id="56094-149">Varolan kodla **Page_Load** yöntemi **Default.aspx.cs** aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="56094-149">Replace the existing code in the **Page_Load** method of **Default.aspx.cs** with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.IdentityModel;  
    using System.Security.Claims;  
    using System.Threading;  
    using System.Web.UI;  
  
    namespace TestApp  
    {  
        public partial class _Default : System.Web.UI.Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    signedIn.Text = "You are signed in.";  
  
                    foreach (Claim claim in claimsPrincipal.Claims)  
                    {  
                        claimType.Text = claim.Type;  
                        claimValue.Text = claim.Value;  
                        claimValueType.Text = claim.ValueType;  
                        claimSubjectName.Text = claim.Subject.Name;  
                        claimIssuer.Text = claim.Issuer;  
                    }  
                }  
                else  
                {  
                    signedIn.Text = "You are not signed in.";  
                }  
            }  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="56094-150">Kaydet **Default.aspx.cs**ve çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="56094-150">Save **Default.aspx.cs**, and build the solution.</span></span>  
  
5.  <span data-ttu-id="56094-151">Tuşlarına basarak çözümü çalıştırın **F5** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="56094-151">Run the solution by pressing the **F5** key.</span></span>  
  
6.  <span data-ttu-id="56094-152">İçin güvenlik belirteci hizmeti tarafından verilen belirteç talep görüntüler sayfa sunulacaktır.</span><span class="sxs-lookup"><span data-stu-id="56094-152">You should be presented with the page that displays the claims in the token that was issued to you by the Security Token Service.</span></span>
