---
title: 'Nasıl yapılır: Gelen talepleri dönüştürme'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: 8673b4520d9727ae1aa78ef0bc9f435defb02598
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171328"
---
# <a name="how-to-transform-incoming-claims"></a><span data-ttu-id="cf161-102">Nasıl yapılır: Gelen talepleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="cf161-102">How To: Transform Incoming Claims</span></span>
## <a name="applies-to"></a><span data-ttu-id="cf161-103">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="cf161-103">Applies To</span></span>  
  
-   <span data-ttu-id="cf161-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="cf161-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="cf161-105">ASP.NET® Web formları</span><span class="sxs-lookup"><span data-stu-id="cf161-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="cf161-106">Özet</span><span class="sxs-lookup"><span data-stu-id="cf161-106">Summary</span></span>  
 <span data-ttu-id="cf161-107">Bu yöntem, basit bir talep kullanan ASP.NET Web Forms uygulaması oluşturma ve gelen talepleri dönüştürme için adım adım ayrıntılı yordamları sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf161-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application and transforming incoming claims.</span></span> <span data-ttu-id="cf161-108">Ayrıca, uygulamayı çalıştırdığınızda dönüştürülmüş beyanların sunulduğunu doğrulamak için uygulamayı test etme için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf161-108">It also provides instructions for how to test the application to verify that transformed claims are presented when the application is run.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="cf161-109">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="cf161-109">Contents</span></span>  
  
-   <span data-ttu-id="cf161-110">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="cf161-110">Objectives</span></span>  
  
-   <span data-ttu-id="cf161-111">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cf161-111">Overview</span></span>  
  
-   <span data-ttu-id="cf161-112">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="cf161-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="cf161-113">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf161-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="cf161-114">Adım 2 – uygulama talepleri özel bir ClaimsAuthenticationManager kullanarak dönüştürme</span><span class="sxs-lookup"><span data-stu-id="cf161-114">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="cf161-115">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="cf161-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="cf161-116">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="cf161-116">Objectives</span></span>  
  
-   <span data-ttu-id="cf161-117">Bir ASP.NET Web Forms uygulaması talep tabanlı kimlik doğrulaması için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cf161-117">Configure an ASP.NET Web Forms application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="cf161-118">Bir yönetici rolü talep ekleyerek gelen talepleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="cf161-118">Transform incoming claims by adding an Administrator role claim</span></span>  
  
-   <span data-ttu-id="cf161-119">Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamayı test etme</span><span class="sxs-lookup"><span data-stu-id="cf161-119">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="cf161-120">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cf161-120">Overview</span></span>  
 <span data-ttu-id="cf161-121">WIF sunan adlı bir sınıf <xref:System.Security.Claims.ClaimsAuthenticationManager> kullanıcıların bir bağlı olan taraf (RP) uygulaması verildikleri önce talep değiştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="cf161-121">WIF exposes a class named <xref:System.Security.Claims.ClaimsAuthenticationManager> that enables users to modify claims before they are presented to a relying party (RP) application.</span></span> <span data-ttu-id="cf161-122"><xref:System.Security.Claims.ClaimsAuthenticationManager> Kimlik doğrulama ve temel uygulama kodu arasındaki ayrımı için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="cf161-122">The <xref:System.Security.Claims.ClaimsAuthenticationManager> is useful for separation of concerns between authentication and the underlying application code.</span></span> <span data-ttu-id="cf161-123">Aşağıdaki örnekte, gelen talepleri bir role eklemek gösterilmiştir <xref:System.Security.Claims.ClaimsPrincipal> tarafından RP gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="cf161-123">The example below demonstrates how to add a role to the claims in the incoming <xref:System.Security.Claims.ClaimsPrincipal> that may be required by the RP.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="cf161-124">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="cf161-124">Summary of Steps</span></span>  
  
-   <span data-ttu-id="cf161-125">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf161-125">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="cf161-126">Adım 2 – uygulama talepleri özel bir ClaimsAuthenticationManager kullanarak dönüştürme</span><span class="sxs-lookup"><span data-stu-id="cf161-126">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="cf161-127">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="cf161-127">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="cf161-128">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf161-128">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="cf161-129">Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="cf161-129">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="cf161-130">Basit bir ASP.NET uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cf161-130">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="cf161-131">Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.</span><span class="sxs-lookup"><span data-stu-id="cf161-131">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="cf161-132">Visual Studio'da **dosya**, tıklayın **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="cf161-132">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="cf161-133">İçinde **yeni proje** penceresinde tıklayın **ASP.NET Web Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="cf161-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
4.  <span data-ttu-id="cf161-134">İçinde **adı**, girin `TestApp` basın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="cf161-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
5.  <span data-ttu-id="cf161-135">Sağ **TestApp** altındaki proje **Çözüm Gezgini**, ardından **kimlik ve erişim**.</span><span class="sxs-lookup"><span data-stu-id="cf161-135">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
6.  <span data-ttu-id="cf161-136">**Kimlik ve erişim** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cf161-136">The **Identity and Access** window appears.</span></span> <span data-ttu-id="cf161-137">Altında **sağlayıcıları**seçin **uygulamanızı yerel geliştirme STS'si ile Test**, ardından **Uygula**.</span><span class="sxs-lookup"><span data-stu-id="cf161-137">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
7.  <span data-ttu-id="cf161-138">İçinde *Default.aspx* dosya, var olan bir biçimlendirme aşağıdakiyle değiştirin ve ardından dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="cf161-138">In the *Default.aspx* file, replace the existing markup with the following, then save the file:</span></span>  
  
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
  
8.  <span data-ttu-id="cf161-139">Adlı arka plan kod dosyası açın *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="cf161-139">Open the code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="cf161-140">Ardından dosyayı kaydedin, aşağıdaki varolan kodu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cf161-140">Replace the existing code with the following, then save the file:</span></span>  
  
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
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="cf161-141">Adım 2 – uygulama talepleri özel bir ClaimsAuthenticationManager kullanarak dönüştürme</span><span class="sxs-lookup"><span data-stu-id="cf161-141">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
 <span data-ttu-id="cf161-142">Bu adımda varsayılan işlevler geçersiz kılacak olan <xref:System.Security.Claims.ClaimsAuthenticationManager> gelen sorumlusuna bir yönetici rolü eklemek için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cf161-142">In this step you will override default functionality in the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to add an Administrator role to the incoming Principal.</span></span>  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="cf161-143">Özel ClaimsAuthenticationManager kullanarak talep dönüştürme uygulamak için</span><span class="sxs-lookup"><span data-stu-id="cf161-143">To implement claims transformation using a custom ClaimsAuthenticationManager</span></span>  
  
1.  <span data-ttu-id="cf161-144">Visual Studio'da sağ tıklayın, çözümü tıklayın **Ekle**ve ardından **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="cf161-144">In Visual Studio, right-click the on the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="cf161-145">İçinde **Yeni Proje Ekle** penceresinde **sınıf kitaplığı** gelen **Visual C#** şablonları listesinde, girin `ClaimsTransformation`ve tuşuna **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="cf161-145">In the **Add New Project** window, select **Class Library** from the **Visual C#** templates list, enter `ClaimsTransformation`, and then press **OK**.</span></span> <span data-ttu-id="cf161-146">Yeni proje, çözüm klasörünüzde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cf161-146">The new project will be created in your solution folder.</span></span>  
  
3.  <span data-ttu-id="cf161-147">Sağ **başvuruları** altında **ClaimsTransformation** proje ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="cf161-147">Right-click on **References** under the **ClaimsTransformation** project, and then click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="cf161-148">İçinde **başvuru Yöneticisi** penceresinde **System.IdentityModel**ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="cf161-148">In the **Reference Manager** window, select **System.IdentityModel**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="cf161-149">Açık **Class1.cs**, veya yoksa, sağ **ClaimsTransformation**, tıklayın **Ekle**, ardından **sınıfı...**</span><span class="sxs-lookup"><span data-stu-id="cf161-149">Open **Class1.cs**, or if it doesn’t exist, right-click **ClaimsTransformation**, click **Add**, then click **Class…**</span></span>  
  
6.  <span data-ttu-id="cf161-150">Aşağıdaki kod dosyasına using yönergeleri:</span><span class="sxs-lookup"><span data-stu-id="cf161-150">Add the following using directives to the code file:</span></span>  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  <span data-ttu-id="cf161-151">Aşağıdaki sınıf ve yöntem kod dosyasını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cf161-151">Add the following class and method in the code file.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="cf161-152">Aşağıdaki kod, yalnızca gösterim amaçlıdır; hedeflenen izinlerinizi üretim kodunda doğruladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="cf161-152">The following code is for demonstration purposes only; make sure that you verify your intended permissions in production code.</span></span>  
  
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
  
8.  <span data-ttu-id="cf161-153">Dosyayı kaydedin ve yapı **ClaimsTransformation** proje.</span><span class="sxs-lookup"><span data-stu-id="cf161-153">Save the file and build the **ClaimsTransformation** project.</span></span>  
  
9. <span data-ttu-id="cf161-154">İçinde **TestApp** ASP.NET projesi başvuruları üzerinde sağ tıklayın ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="cf161-154">In your **TestApp** ASP.NET project, right-click on References, and then click **Add Reference**.</span></span>  
  
10. <span data-ttu-id="cf161-155">İçinde **başvuru Yöneticisi** penceresinde **çözüm** sol menüden **ClaimsTransformation** doldurulmuş seçenekleri ve ardından  **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="cf161-155">In the **Reference Manager** window, select **Solution** from the left menu, select **ClaimsTransformation** from the populated options, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="cf161-156">Kök **Web.config** gidin, dosya  **\<system.identityModel >** girişi.</span><span class="sxs-lookup"><span data-stu-id="cf161-156">In the root **Web.config** file, navigate to the **\<system.identityModel>** entry.</span></span> <span data-ttu-id="cf161-157">İçinde  **\<identityConfiguration >** öğeleri eklemek için aşağıdakileri satır ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="cf161-157">Within the **\<identityConfiguration>** elements, add the following line and save the file:</span></span>  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="cf161-158">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="cf161-158">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="cf161-159">Bu adımda ASP.NET Web Forms uygulamanızı test edin ve bir kullanıcı, Forms kimlik doğrulaması ile oturum açtığında beyanların sunulduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="cf161-159">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="cf161-160">Form kimlik doğrulaması kullanarak talep için ASP.NET Web Forms uygulamanızı test etmek için</span><span class="sxs-lookup"><span data-stu-id="cf161-160">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="cf161-161">Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cf161-161">Press **F5** to build and run the application.</span></span> <span data-ttu-id="cf161-162">İle sunulan *Default.aspx*.</span><span class="sxs-lookup"><span data-stu-id="cf161-162">You should be presented with *Default.aspx*.</span></span>  
  
2.  <span data-ttu-id="cf161-163">Üzerinde *Default.aspx* sayfasında, bir tablonun altına görmeniz **bilgisayarınızı talep** içeren başlık **veren**, **OriginalIssuer**, **Türü**, **değer**, ve **ValueType** talep, hesabınız hakkında bilgiler.</span><span class="sxs-lookup"><span data-stu-id="cf161-163">On the *Default.aspx* page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span> <span data-ttu-id="cf161-164">Son satırı aşağıdaki şekilde sunulması:</span><span class="sxs-lookup"><span data-stu-id="cf161-164">The last row should be presented in the following way:</span></span>  
  
    ||||||  
    |-|-|-|-|-|  
    |<span data-ttu-id="cf161-165">YEREL YETKİLİSİ</span><span class="sxs-lookup"><span data-stu-id="cf161-165">LOCAL AUTHORITY</span></span>|<span data-ttu-id="cf161-166">YEREL YETKİLİSİ</span><span class="sxs-lookup"><span data-stu-id="cf161-166">LOCAL AUTHORITY</span></span>|http://schemas.microsoft.com/ws/2008/06/identity/claims/role|<span data-ttu-id="cf161-167">Yönetici</span><span class="sxs-lookup"><span data-stu-id="cf161-167">Admin</span></span>|http://www.w3.org/2001/XMLSchema#string|
