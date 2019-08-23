---
title: 'Nasıl yapılır: WIF Kullanarak Talep Kullanan ASP.NET Web Forms Uygulaması Derleme'
ms.date: 03/30/2017
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
author: BrucePerlerMS
ms.openlocfilehash: 82b0649a7324987581cc3c97570a0fc42ffdf6d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941291"
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a><span data-ttu-id="c1dff-102">Nasıl yapılır: WIF Kullanarak Talep Kullanan ASP.NET Web Forms Uygulaması Derleme</span><span class="sxs-lookup"><span data-stu-id="c1dff-102">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="c1dff-103">Uygulanan Öğe</span><span class="sxs-lookup"><span data-stu-id="c1dff-103">Applies To</span></span>  
  
- <span data-ttu-id="c1dff-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="c1dff-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="c1dff-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="c1dff-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="c1dff-106">Özet</span><span class="sxs-lookup"><span data-stu-id="c1dff-106">Summary</span></span>  
 <span data-ttu-id="c1dff-107">Bu nasıl yapılır, basit talep kullanan ASP.NET Web Forms uygulaması oluşturmaya yönelik ayrıntılı adım adım yordamlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1dff-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET Web Forms application.</span></span> <span data-ttu-id="c1dff-108">Ayrıca, Federasyon kimlik doğrulamasının başarılı bir şekilde uygulanması için basit talep kullanan ASP.NET Web Forms uygulamasının nasıl test edildiği hakkında yönergeler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1dff-108">It also provides instructions for how to test the simple claims-aware ASP.NET Web Forms application for successful implementation of federated authentication.</span></span> <span data-ttu-id="c1dff-109">Bu nasıl yapılır, güvenlik belirteci hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler içermez ve zaten bir STS yapılandırdığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="c1dff-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="c1dff-110">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="c1dff-110">Contents</span></span>  
  
- <span data-ttu-id="c1dff-111">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="c1dff-111">Objectives</span></span>  
  
- <span data-ttu-id="c1dff-112">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="c1dff-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="c1dff-113">1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1dff-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
- <span data-ttu-id="c1dff-114">2\. adım – ASP.NET Web Forms uygulamasını talep tabanlı kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c1dff-114">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="c1dff-115">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="c1dff-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="c1dff-116">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="c1dff-116">Objectives</span></span>  
  
- <span data-ttu-id="c1dff-117">Talep tabanlı kimlik doğrulaması için ASP.NET Web Forms uygulamasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c1dff-117">Configure ASP.NET Web Forms application for claims-based authentication</span></span>  
  
- <span data-ttu-id="c1dff-118">Test başarılı talep kullanan ASP.NET Web Forms uygulaması</span><span class="sxs-lookup"><span data-stu-id="c1dff-118">Test successful claims-aware ASP.NET Web Forms application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="c1dff-119">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="c1dff-119">Summary of Steps</span></span>  
  
- <span data-ttu-id="c1dff-120">1\. adım – basit ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1dff-120">Step 1 – Create Simple ASP.NET Web Forms Application</span></span>  
  
- <span data-ttu-id="c1dff-121">2\. adım – Federasyon kimlik doğrulaması için ASP.NET Web Forms uygulamasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c1dff-121">Step 2 – Configure ASP.NET Web Forms Application for Federated Authentication</span></span>  
  
- <span data-ttu-id="c1dff-122">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="c1dff-122">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="c1dff-123">1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1dff-123">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="c1dff-124">Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c1dff-124">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="c1dff-125">Basit bir ASP.NET uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c1dff-125">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="c1dff-126">Visual Studio 'Yu başlatın ve **Dosya**, **Yeni**ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1dff-126">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="c1dff-127">**Yeni proje** penceresinde, **ASP.NET Web Forms uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1dff-127">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="c1dff-128">**Ad**alanına girin `TestApp` ve **Tamam**' a basın.</span><span class="sxs-lookup"><span data-stu-id="c1dff-128">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a><span data-ttu-id="c1dff-129">2\. adım – ASP.NET Web Forms uygulamasını talep tabanlı kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c1dff-129">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="c1dff-130">Bu adımda, ASP.NET Web Forms uygulamanızın *Web. config* yapılandırma dosyasına, talebe göre haberdar olmak için yapılandırma girdileri ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c1dff-130">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET Web Forms application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a><span data-ttu-id="c1dff-131">Talep tabanlı kimlik doğrulaması için ASP.NET uygulamasını yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="c1dff-131">To configure ASP.NET application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="c1dff-132">Yapılandırma > açma öğesinden hemen sonra **aşağıdaki yapılandırma bölümü girdilerini Web. config yapılandırma dosyasına ekleyin: \<**</span><span class="sxs-lookup"><span data-stu-id="c1dff-132">Add the following configuration section entries to the *Web.config* configuration file immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. <span data-ttu-id="c1dff-133">Uygulamanın Federasyon meta verilerine erişim sağlayan bir  **\<konum >** öğesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c1dff-133">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3. <span data-ttu-id="c1dff-134">Kullanıcıları reddetmek, yerel kimlik doğrulamasını devre dışı bırakmak ve kimlik doğrulamasını yönetmek için WIF 'yi etkinleştirmek için  **\<System. Web >** öğelerine aşağıdaki yapılandırma girdilerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c1dff-134">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. <span data-ttu-id="c1dff-135">Federe kimlik doğrulaması için modülleri tanımlayan bir  **\<System. webserver >** öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c1dff-135">Add a **\<system.webServer>** element that defines the modules for federated authentication.</span></span> <span data-ttu-id="c1dff-136">*PublicKeyToken* özniteliğinin, daha önce eklenen  **\<configSections >** girdilerinin *PublicKeyToken* özniteliğiyle aynı olması gerektiğini unutmayın:</span><span class="sxs-lookup"><span data-stu-id="c1dff-136">Note that the *PublicKeyToken* attribute must be the same as the *PublicKeyToken* attribute for the **\<configSections>** entries added earlier:</span></span>  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5. <span data-ttu-id="c1dff-137">Aşağıdaki Windows Identity Foundation ile ilgili yapılandırma girdilerini ekleyin ve ASP.net uygulamanızın URL 'si ile bağlantı noktası  **\<>** numarasının,  **\<** WSFederation > öğesi ve  **\<WSFederation >** öğesinin **Reply** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c1dff-137">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="c1dff-138">Ayrıca, **verenin** değerinin güvenlik belirteci HIZMETI (STS) URL 'nize uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c1dff-138">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
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
            <cookieHandler requireSsl="true" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="true" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
6. <span data-ttu-id="c1dff-139"><xref:System.IdentityModel> Derlemeye başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c1dff-139">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
7. <span data-ttu-id="c1dff-140">Bir hata olmadığından emin olmak için çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="c1dff-140">Compile the solution to make sure there are no errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="c1dff-141">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="c1dff-141">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="c1dff-142">Bu adımda, talep tabanlı kimlik doğrulaması için yapılandırılmış olan ASP.NET Web Forms uygulamanızı test edersiniz.</span><span class="sxs-lookup"><span data-stu-id="c1dff-142">In this step you will test your ASP.NET Web Forms application configured for claims-based authentication.</span></span> <span data-ttu-id="c1dff-143">Temel bir test gerçekleştirmek için, güvenlik belirteci hizmeti (STS) tarafından verilen belirteçte talepleri görüntüleyen bir kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c1dff-143">To perform a basic test, you will add code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a><span data-ttu-id="c1dff-144">Talep tabanlı kimlik doğrulaması için ASP.NET Web formu uygulamanızı test etmek için</span><span class="sxs-lookup"><span data-stu-id="c1dff-144">To test your ASP.NET Web Form application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="c1dff-145">**TestApp** projesi altındaki **default. aspx** dosyasını açın ve var olan işaretlemesini aşağıdaki biçimlendirme ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c1dff-145">Open the **Default.aspx** file under the **TestApp** project and replace its existing markup with the following markup:</span></span>  
  
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
  
2. <span data-ttu-id="c1dff-146">**Default. aspx**' i kaydedin ve sonra kodu **default.aspx.cs**adlı dosyanın arkasında açın.</span><span class="sxs-lookup"><span data-stu-id="c1dff-146">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c1dff-147">**Default.aspx.cs** , Çözüm Gezgini içinde **default. aspx** altında gizlenebilir.</span><span class="sxs-lookup"><span data-stu-id="c1dff-147">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="c1dff-148">**Default.aspx.cs** görünür değilse, bunun yanındaki üçgene tıklayarak **default. aspx** ' i genişletin.</span><span class="sxs-lookup"><span data-stu-id="c1dff-148">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
3. <span data-ttu-id="c1dff-149">**Default.aspx.cs** öğesinin **Page_Load** yöntemindeki mevcut kodu şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c1dff-149">Replace the existing code in the **Page_Load** method of **Default.aspx.cs** with the following code:</span></span>  
  
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
  
4. <span data-ttu-id="c1dff-150">**Default.aspx.cs**kaydedin ve Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="c1dff-150">Save **Default.aspx.cs**, and build the solution.</span></span>  
  
5. <span data-ttu-id="c1dff-151">**F5** tuşuna basarak çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1dff-151">Run the solution by pressing the **F5** key.</span></span>  
  
6. <span data-ttu-id="c1dff-152">Güvenlik belirteci hizmeti tarafından size verilen belirteçteki talepleri görüntüleyen sayfayla birlikte sunulmalısınız.</span><span class="sxs-lookup"><span data-stu-id="c1dff-152">You should be presented with the page that displays the claims in the token that was issued to you by the Security Token Service.</span></span>
