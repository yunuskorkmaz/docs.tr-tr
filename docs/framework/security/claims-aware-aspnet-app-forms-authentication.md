---
title: 'Nasıl yapılır: Forms tabanlı kimlik doğrulaması kullanarak talep kullanan ASP.NET uygulaması derleme'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: 8dab5cfbcf14707699e6672017f5f80db232f01d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47110443"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a><span data-ttu-id="c645d-102">Nasıl yapılır: Forms tabanlı kimlik doğrulaması kullanarak talep kullanan ASP.NET uygulaması derleme</span><span class="sxs-lookup"><span data-stu-id="c645d-102">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="c645d-103">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="c645d-103">Applies To</span></span>  
  
-   <span data-ttu-id="c645d-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="c645d-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="c645d-105">ASP.NET® Web formları</span><span class="sxs-lookup"><span data-stu-id="c645d-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="c645d-106">Özet</span><span class="sxs-lookup"><span data-stu-id="c645d-106">Summary</span></span>  
 <span data-ttu-id="c645d-107">Bu nasıl yapılır, Forms kimlik doğrulaması kullanan basit bir talep kullanan ASP.NET Web Forms uygulaması oluşturmak için adım adım ayrıntılı yordamları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c645d-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Forms authentication.</span></span> <span data-ttu-id="c645d-108">Ayrıca, bir kullanıcı, Forms kimlik doğrulaması ile oturum açtığında beyanların sunulduğunu doğrulamak için uygulamayı test etme için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c645d-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="c645d-109">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="c645d-109">Contents</span></span>  
  
-   <span data-ttu-id="c645d-110">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="c645d-110">Objectives</span></span>  
  
-   <span data-ttu-id="c645d-111">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c645d-111">Overview</span></span>  
  
-   <span data-ttu-id="c645d-112">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="c645d-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="c645d-113">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c645d-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="c645d-114">2. adım: ASP.NET Web Forms uygulaması için form kimlik doğrulaması kullanarak talep yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c645d-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="c645d-115">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="c645d-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="c645d-116">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="c645d-116">Objectives</span></span>  
  
-   <span data-ttu-id="c645d-117">Bir ASP.NET Web Forms uygulaması için form kimlik doğrulaması kullanarak talep yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c645d-117">Configure an ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
-   <span data-ttu-id="c645d-118">Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamayı test etme</span><span class="sxs-lookup"><span data-stu-id="c645d-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="c645d-119">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c645d-119">Overview</span></span>  
 <span data-ttu-id="c645d-120">WIF ve kendi beyana dayalı yetkilendirme, .NET 4.5 içinde Framework ayrılmaz bir parçası dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c645d-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="c645d-121">Daha önce bir ASP.NET kullanıcı gelen talepleri istediyseniz, WIF yüklemek için gerekli ve ardından atama asıl nesneleri gibi arabirimleri `Thread.CurrentPrincipal` veya `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="c645d-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="c645d-122">Artık, talep nesneleri otomatik olarak bu sorumlusu tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="c645d-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="c645d-123">Forms tarafından otomatik olarak kimliği doğrulanmış tüm kullanıcılar kendileriyle ilişkili talep olduğundan form kimlik doğrulaması .NET 4.5 WIF'ın eklenmesi benefited.</span><span class="sxs-lookup"><span data-stu-id="c645d-123">Forms authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Forms automatically have claims associated with them.</span></span> <span data-ttu-id="c645d-124">Bu nasıl yapılır gösterildiği gibi bu talepler form kimlik doğrulaması kullanan bir ASP.NET uygulamasında hemen kullanmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c645d-124">You can begin using these claims immediately in an ASP.NET application that uses Forms authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="c645d-125">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="c645d-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="c645d-126">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c645d-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="c645d-127">2. adım: ASP.NET Web Forms uygulaması için form kimlik doğrulaması kullanarak talep yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c645d-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="c645d-128">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="c645d-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="c645d-129">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c645d-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="c645d-130">Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c645d-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="c645d-131">Basit bir ASP.NET uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c645d-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="c645d-132">Visual Studio'yu başlatın ve tıklayın **dosya**, **yeni**, ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="c645d-132">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="c645d-133">İçinde **yeni proje** penceresinde tıklayın **ASP.NET Web Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="c645d-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="c645d-134">İçinde **adı**, girin `TestApp` basın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c645d-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="c645d-135">2. adım: ASP.NET Web Forms uygulaması için form kimlik doğrulaması kullanarak talep yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c645d-135">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
 <span data-ttu-id="c645d-136">Bu adımda, bir yapılandırma girişi için ekler *Web.config* yapılandırma dosyası ve düzenleme *Default.aspx* dosyayı görüntülemek için bir hesap için bilgileri talep.</span><span class="sxs-lookup"><span data-stu-id="c645d-136">In this step you will add a configuration entry to the *Web.config* configuration file and edit the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a><span data-ttu-id="c645d-137">Form kimlik doğrulaması kullanarak talep için ASP.NET uygulamanızı yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="c645d-137">To configure ASP.NET application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="c645d-138">İçinde *Default.aspx* dosya, var olan bir biçimlendirme aşağıdakiyle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c645d-138">In the *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Forms authenticated user.          
        </p>  
        <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
     <span data-ttu-id="c645d-139">Bu adım için bir GridView denetimi ekler, *Default.aspx* talepleri ile doldurulacak sayfa Forms kimlik doğrulamasını alınır.</span><span class="sxs-lookup"><span data-stu-id="c645d-139">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Forms authentication.</span></span>  
  
2.  <span data-ttu-id="c645d-140">Kaydet *Default.aspx* dosya sonra adlı arka plan kod dosyasını açabilir *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="c645d-140">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="c645d-141">Varolan kodu aşağıdakiyle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c645d-141">Replace the existing code with the following:</span></span>  
  
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
  
                if (claimsPrincipal != null)  
                {  
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                    this.ClaimsGridView.DataBind();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="c645d-142">Yukarıdaki kod, form kimlik doğrulaması tarafından tanımlanan kullanıcılar dahil olmak üzere, kimliği doğrulanmış bir kullanıcı hakkında talepleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c645d-142">The above code will display claims about an authenticated user, including users identified by Forms authentication.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="c645d-143">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="c645d-143">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="c645d-144">Bu adımda ASP.NET Web Forms uygulamanızı test edin ve bir kullanıcı, Forms kimlik doğrulaması ile oturum açtığında beyanların sunulduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="c645d-144">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="c645d-145">Form kimlik doğrulaması kullanarak talep için ASP.NET Web Forms uygulamanızı test etmek için</span><span class="sxs-lookup"><span data-stu-id="c645d-145">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="c645d-146">Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c645d-146">Press **F5** to build and run the application.</span></span> <span data-ttu-id="c645d-147">İle sunulan *Default.aspx*, sahip olduğu **kaydetme** ve **oturum** üst bağlantılar sayfasının sağ.</span><span class="sxs-lookup"><span data-stu-id="c645d-147">You should be presented with *Default.aspx*, which has **Register** and **Log in** links in the top right of the page.</span></span> <span data-ttu-id="c645d-148">Tıklayın **kaydetme**.</span><span class="sxs-lookup"><span data-stu-id="c645d-148">Click **Register**.</span></span>  
  
2.  <span data-ttu-id="c645d-149">Üzerinde **kaydetme** sayfasında bir kullanıcı hesabı oluşturun ve ardından **kaydetme**.</span><span class="sxs-lookup"><span data-stu-id="c645d-149">On the **Register** page, create a user account, and then click **Register**.</span></span> <span data-ttu-id="c645d-150">Hesabınız, form kimlik doğrulaması kullanılarak oluşturulur ve size otomatik olarak oturum açacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c645d-150">Your account will be created using Forms authentication, and you will be automatically signed in.</span></span>  
  
3.  <span data-ttu-id="c645d-151">Giriş sayfasına yönlendirildiniz sonra bir tablo altındaki görmelisiniz **bilgisayarınızı talep** içeren başlık **veren**, **OriginalIssuer**, **Türü**, **değer**, ve **ValueType** talep, hesabınız hakkında bilgiler.</span><span class="sxs-lookup"><span data-stu-id="c645d-151">After you have been redirected to the home page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span>
