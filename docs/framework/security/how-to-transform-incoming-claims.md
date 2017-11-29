---
title: "Nasıl yapılır: Gelen talep dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: bcf0e640e6b6b45ddb87070c7d6df2fa6dadc834
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-transform-incoming-claims"></a><span data-ttu-id="3b470-102">Nasıl yapılır: Gelen talep dönüştürme</span><span class="sxs-lookup"><span data-stu-id="3b470-102">How To: Transform Incoming Claims</span></span>
## <a name="applies-to"></a><span data-ttu-id="3b470-103">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="3b470-103">Applies To</span></span>  
  
-   <span data-ttu-id="3b470-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="3b470-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="3b470-105">ASP.NET® Web formları</span><span class="sxs-lookup"><span data-stu-id="3b470-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="3b470-106">Özet</span><span class="sxs-lookup"><span data-stu-id="3b470-106">Summary</span></span>  
 <span data-ttu-id="3b470-107">Bu yöntem basit bir talep kullanan ASP.NET Web Forms uygulaması oluşturma ve gelen talepleri dönüştürmek için ayrıntılı adım adım yordamlar verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b470-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application and transforming incoming claims.</span></span> <span data-ttu-id="3b470-108">Ayrıca, uygulamayı çalıştırdığınızda, dönüştürülmüş talep sunulduğundan emin doğrulamak için uygulamayı test etme için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b470-108">It also provides instructions for how to test the application to verify that transformed claims are presented when the application is run.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="3b470-109">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="3b470-109">Contents</span></span>  
  
-   <span data-ttu-id="3b470-110">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="3b470-110">Objectives</span></span>  
  
-   <span data-ttu-id="3b470-111">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3b470-111">Overview</span></span>  
  
-   <span data-ttu-id="3b470-112">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="3b470-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="3b470-113">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="3b470-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="3b470-114">Adım 2 – uygulama talep özel ClaimsAuthenticationManager kullanarak dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="3b470-114">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="3b470-115">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="3b470-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="3b470-116">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="3b470-116">Objectives</span></span>  
  
-   <span data-ttu-id="3b470-117">Bir ASP.NET Web Forms uygulaması talep tabanlı kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3b470-117">Configure an ASP.NET Web Forms application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="3b470-118">Bir yönetici rolü talep ekleyerek gelen talep dönüştürme</span><span class="sxs-lookup"><span data-stu-id="3b470-118">Transform incoming claims by adding an Administrator role claim</span></span>  
  
-   <span data-ttu-id="3b470-119">Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamayı test etme</span><span class="sxs-lookup"><span data-stu-id="3b470-119">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="3b470-120">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3b470-120">Overview</span></span>  
 <span data-ttu-id="3b470-121">WIF sunan adlı bir sınıf <xref:System.Security.Claims.ClaimsAuthenticationManager> bir bağlı olan taraf (RP) uygulamaya verildikleri önce talep değiştirmek kullanıcıların sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b470-121">WIF exposes a class named <xref:System.Security.Claims.ClaimsAuthenticationManager> that enables users to modify claims before they are presented to a relying party (RP) application.</span></span> <span data-ttu-id="3b470-122"><xref:System.Security.Claims.ClaimsAuthenticationManager> Kimlik doğrulaması ve temel uygulama kodu arasında sorunları ayrılması için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b470-122">The <xref:System.Security.Claims.ClaimsAuthenticationManager> is useful for separation of concerns between authentication and the underlying application code.</span></span> <span data-ttu-id="3b470-123">Aşağıdaki örnek, gelen talepleri bir rolü eklemek gösterilmiştir <xref:System.Security.Claims.ClaimsPrincipal> , gereken tarafından RP.</span><span class="sxs-lookup"><span data-stu-id="3b470-123">The example below demonstrates how to add a role to the claims in the incoming <xref:System.Security.Claims.ClaimsPrincipal> that may be required by the RP.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="3b470-124">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="3b470-124">Summary of Steps</span></span>  
  
-   <span data-ttu-id="3b470-125">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="3b470-125">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="3b470-126">Adım 2 – uygulama talep özel ClaimsAuthenticationManager kullanarak dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="3b470-126">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="3b470-127">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="3b470-127">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="3b470-128">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="3b470-128">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="3b470-129">Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="3b470-129">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="3b470-130">Basit bir ASP.NET uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3b470-130">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="3b470-131">Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.</span><span class="sxs-lookup"><span data-stu-id="3b470-131">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="3b470-132">Visual Studio'da sırasıyla **dosya**, tıklatın **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="3b470-132">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="3b470-133">İçinde **yeni proje** penceresinde tıklatın **ASP.NET Web Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="3b470-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
4.  <span data-ttu-id="3b470-134">İçinde **adı**, girin `TestApp` ve basın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="3b470-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
5.  <span data-ttu-id="3b470-135">Sağ **TestApp** altında proje **Çözüm Gezgini**seçeneğini belirleyip **kimlik ve erişim**.</span><span class="sxs-lookup"><span data-stu-id="3b470-135">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
6.  <span data-ttu-id="3b470-136">**Kimlik ve erişim** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3b470-136">The **Identity and Access** window appears.</span></span> <span data-ttu-id="3b470-137">Altında **sağlayıcıları**seçin **yerel geliştirme STS ile uygulamanızı Test**, ardından **Uygula**.</span><span class="sxs-lookup"><span data-stu-id="3b470-137">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
7.  <span data-ttu-id="3b470-138">İçinde *Default.aspx* dosya, varolan biçimlendirme şununla değiştirin ve ardından dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="3b470-138">In the *Default.aspx* file, replace the existing markup with the following, then save the file:</span></span>  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
          <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
8.  <span data-ttu-id="3b470-139">Adlı arka plan kodu dosyasını açın *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="3b470-139">Open the code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="3b470-140">Ardından dosyayı kaydedin aşağıdaki var olan kodu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="3b470-140">Replace the existing code with the following, then save the file:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        public partial class _Default : Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;  
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="3b470-141">Adım 2 – uygulama talep özel ClaimsAuthenticationManager kullanarak dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="3b470-141">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
 <span data-ttu-id="3b470-142">Bu adımda varsayılan işlevleri geçersiz kılar <xref:System.Security.Claims.ClaimsAuthenticationManager> gelen asıl bir yönetici rolü eklemek için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3b470-142">In this step you will override default functionality in the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to add an Administrator role to the incoming Principal.</span></span>  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="3b470-143">Talep dönüştürme özel ClaimsAuthenticationManager kullanarak uygulamak için</span><span class="sxs-lookup"><span data-stu-id="3b470-143">To implement claims transformation using a custom ClaimsAuthenticationManager</span></span>  
  
1.  <span data-ttu-id="3b470-144">Visual Studio'da sağ çözüm üzerinde tıklatın **Ekle**ve ardından **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="3b470-144">In Visual Studio, right-click the on the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="3b470-145">İçinde **Yeni Proje Ekle** penceresinde, seçin **sınıf kitaplığı** gelen **Visual C#** şablonları listesinde, girin `ClaimsTransformation`ve tuşuna basarak **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="3b470-145">In the **Add New Project** window, select **Class Library** from the **Visual C#** templates list, enter `ClaimsTransformation`, and then press **OK**.</span></span> <span data-ttu-id="3b470-146">Yeni proje, çözüm klasörünüzde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3b470-146">The new project will be created in your solution folder.</span></span>  
  
3.  <span data-ttu-id="3b470-147">Sağ **başvuruları** altında **ClaimsTransformation** proje ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="3b470-147">Right-click on **References** under the **ClaimsTransformation** project, and then click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="3b470-148">İçinde **başvuru Yöneticisi** penceresinde, seçin **System.IdentityModel**ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="3b470-148">In the **Reference Manager** window, select **System.IdentityModel**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="3b470-149">Açık **Class1.cs**, veya yoksa, sağ **ClaimsTransformation**, tıklatın **Ekle**, ardından **sınıfı...**</span><span class="sxs-lookup"><span data-stu-id="3b470-149">Open **Class1.cs**, or if it doesn’t exist, right-click **ClaimsTransformation**, click **Add**, then click **Class…**</span></span>  
  
6.  <span data-ttu-id="3b470-150">Aşağıdaki kod dosyasına yönergeleri kullanarak:</span><span class="sxs-lookup"><span data-stu-id="3b470-150">Add the following using directives to the code file:</span></span>  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  <span data-ttu-id="3b470-151">Aşağıdaki sınıf ve yöntemi kod dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3b470-151">Add the following class and method in the code file.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="3b470-152">Aşağıdaki kod, yalnızca tanıtım amaçlıdır; hedeflenen izinlerinizi üretim kodunda doğruladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="3b470-152">The following code is for demonstration purposes only; make sure that you verify your intended permissions in production code.</span></span>  
  
    ```csharp  
    public class ClaimsTransformationModule : ClaimsAuthenticationManager  
    {  
        public override ClaimsPrincipal Authenticate(string resourceName, ClaimsPrincipal incomingPrincipal)  
        {  
            if (incomingPrincipal != null && incomingPrincipal.Identity.IsAuthenticated == true)  
            {  
               ((ClaimsIdentity)incomingPrincipal.Identity).AddClaim(new Claim(ClaimTypes.Role, "Admin"));  
            }  
  
            return incomingPrincipal;  
        }  
    }  
    ```  
  
8.  <span data-ttu-id="3b470-153">Dosyayı kaydedin ve yapı **ClaimsTransformation** projesi.</span><span class="sxs-lookup"><span data-stu-id="3b470-153">Save the file and build the **ClaimsTransformation** project.</span></span>  
  
9. <span data-ttu-id="3b470-154">İçinde **TestApp** ASP.NET proje başvuruları üzerinde sağ tıklayın ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="3b470-154">In your **TestApp** ASP.NET project, right-click on References, and then click **Add Reference**.</span></span>  
  
10. <span data-ttu-id="3b470-155">İçinde **başvuru Yöneticisi** penceresinde, seçin **çözüm** sol menüden seçin **ClaimsTransformation** doldurulan seçenekleri ve ardından  **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="3b470-155">In the **Reference Manager** window, select **Solution** from the left menu, select **ClaimsTransformation** from the populated options, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="3b470-156">Kök **Web.config** dosya, gitmek  **\<System.IdentityModel >** girişi.</span><span class="sxs-lookup"><span data-stu-id="3b470-156">In the root **Web.config** file, navigate to the **\<system.identityModel>** entry.</span></span> <span data-ttu-id="3b470-157">İçinde  **\<identityConfiguration >** öğeler eklemek için aşağıdakileri satır ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="3b470-157">Within the **\<identityConfiguration>** elements, add the following line and save the file:</span></span>  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="3b470-158">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="3b470-158">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="3b470-159">Bu adımda ASP.NET Web Forms uygulamanızı test etmek ve kullanıcı Forms kimlik doğrulaması ile oturum açtığında, talep sunulduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="3b470-159">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="3b470-160">Form kimlik doğrulaması kullanarak talepler için ASP.NET Web Forms uygulamanızı test etmek için</span><span class="sxs-lookup"><span data-stu-id="3b470-160">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="3b470-161">Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3b470-161">Press **F5** to build and run the application.</span></span> <span data-ttu-id="3b470-162">İle sunulan *Default.aspx*.</span><span class="sxs-lookup"><span data-stu-id="3b470-162">You should be presented with *Default.aspx*.</span></span>  
  
2.  <span data-ttu-id="3b470-163">Üzerinde *Default.aspx* sayfasında, bir tablonun altına görmelisiniz **bilgisayarınızı talep** içeren başlık **veren**, **Serileştirilmiştir**, **Türü**, **değeri**, ve **ValueType** , hesabınız hakkında bilgiler talepleri.</span><span class="sxs-lookup"><span data-stu-id="3b470-163">On the *Default.aspx* page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span> <span data-ttu-id="3b470-164">Son satırını aşağıdaki şekilde sunulması gereken:</span><span class="sxs-lookup"><span data-stu-id="3b470-164">The last row should be presented in the following way:</span></span>  
  
    ||||||  
    |-|-|-|-|-|  
    |<span data-ttu-id="3b470-165">YEREL YETKİLİSİ</span><span class="sxs-lookup"><span data-stu-id="3b470-165">LOCAL AUTHORITY</span></span>|<span data-ttu-id="3b470-166">YEREL YETKİLİSİ</span><span class="sxs-lookup"><span data-stu-id="3b470-166">LOCAL AUTHORITY</span></span>|<span data-ttu-id="3b470-167">http://schemas.microsoft.com/ws/2008/06/identity/claims/role</span><span class="sxs-lookup"><span data-stu-id="3b470-167">http://schemas.microsoft.com/ws/2008/06/identity/claims/role</span></span>|<span data-ttu-id="3b470-168">Yönetici</span><span class="sxs-lookup"><span data-stu-id="3b470-168">Admin</span></span>|<span data-ttu-id="3b470-169">http://www.w3.org/2001/XMLSchema#String</span><span class="sxs-lookup"><span data-stu-id="3b470-169">http://www.w3.org/2001/XMLSchema#string</span></span>|
