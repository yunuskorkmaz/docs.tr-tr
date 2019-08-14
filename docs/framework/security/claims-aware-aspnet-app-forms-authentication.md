---
title: 'Nasıl yapılır: Forms Tabanlı Kimlik Doğrulaması Kullanarak Talep Kullanan ASP.NET Uygulaması Derleme'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: 75db96a621d7863ef445efb24814111b34da6960
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971843"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a><span data-ttu-id="a2b6a-102">Nasıl yapılır: Forms Tabanlı Kimlik Doğrulaması Kullanarak Talep Kullanan ASP.NET Uygulaması Derleme</span><span class="sxs-lookup"><span data-stu-id="a2b6a-102">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>

## <a name="applies-to"></a><span data-ttu-id="a2b6a-103">Uygulanan Öğe</span><span class="sxs-lookup"><span data-stu-id="a2b6a-103">Applies To</span></span>

- <span data-ttu-id="a2b6a-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="a2b6a-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="a2b6a-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="a2b6a-105">ASP.NET® Web Forms</span></span>

## <a name="summary"></a><span data-ttu-id="a2b6a-106">Özet</span><span class="sxs-lookup"><span data-stu-id="a2b6a-106">Summary</span></span>

<span data-ttu-id="a2b6a-107">Bu nasıl yapılır, Forms kimlik doğrulaması kullanan basit bir talep kullanan ASP.NET Web Forms uygulaması oluşturmaya yönelik ayrıntılı adım adım yordamlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Forms authentication.</span></span> <span data-ttu-id="a2b6a-108">Ayrıca, bir kullanıcı form kimlik doğrulamasıyla oturum açtığında taleplerin sunulduğunu doğrulamak için uygulamanın nasıl test alınacağını belirten yönergeler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in with Forms authentication.</span></span>

## <a name="contents"></a><span data-ttu-id="a2b6a-109">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="a2b6a-109">Contents</span></span>

- <span data-ttu-id="a2b6a-110">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="a2b6a-110">Objectives</span></span>

- <span data-ttu-id="a2b6a-111">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a2b6a-111">Overview</span></span>

- <span data-ttu-id="a2b6a-112">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="a2b6a-112">Summary of Steps</span></span>

- <span data-ttu-id="a2b6a-113">1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="a2b6a-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="a2b6a-114">2\. adım – Forms kimlik doğrulamasını kullanarak talepler için ASP.NET Web Forms uygulamasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a2b6a-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>

- <span data-ttu-id="a2b6a-115">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="a2b6a-115">Step 3 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="a2b6a-116">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="a2b6a-116">Objectives</span></span>

- <span data-ttu-id="a2b6a-117">Forms kimlik doğrulaması kullanarak talepler için bir ASP.NET Web Forms uygulaması yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a2b6a-117">Configure an ASP.NET Web Forms application for claims using Forms authentication</span></span>

- <span data-ttu-id="a2b6a-118">Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamasını test etme</span><span class="sxs-lookup"><span data-stu-id="a2b6a-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>

## <a name="overview"></a><span data-ttu-id="a2b6a-119">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a2b6a-119">Overview</span></span>

<span data-ttu-id="a2b6a-120">.NET 4,5 ' de, WıF ve talep tabanlı yetkilendirme, Framework 'ün ayrılmaz bir parçası olarak eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="a2b6a-121">Daha önce, bir ASP.net kullanıcısının taleplerini istediyseniz, WIF 'yi yüklemeli ve ardından arabirimleri veya `Thread.CurrentPrincipal` `HttpContext.Current.User`gibi Principal nesnelerine atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="a2b6a-122">Artık talepler, bu Principal nesneleri tarafından otomatik olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-122">Now, claims are served automatically by these Principal objects.</span></span>

<span data-ttu-id="a2b6a-123">Forms kimlik doğrulaması, form tarafından kimliği doğrulanan tüm kullanıcılar otomatik olarak bunlarla ilişkili talepler içerdiğinden, .NET 4,5 ' a dahil benefited.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-123">Forms authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Forms automatically have claims associated with them.</span></span> <span data-ttu-id="a2b6a-124">Bu talepleri, nasıl gösterildiği gibi, Forms kimlik doğrulaması kullanan bir ASP.NET uygulamasında hemen kullanmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-124">You can begin using these claims immediately in an ASP.NET application that uses Forms authentication, as this How-To demonstrates.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="a2b6a-125">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="a2b6a-125">Summary of Steps</span></span>

- <span data-ttu-id="a2b6a-126">1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="a2b6a-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="a2b6a-127">2\. adım – Forms kimlik doğrulamasını kullanarak talepler için ASP.NET Web Forms uygulamasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a2b6a-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>

- <span data-ttu-id="a2b6a-128">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="a2b6a-128">Step 3 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="a2b6a-129">1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="a2b6a-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

<span data-ttu-id="a2b6a-130">Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>

### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="a2b6a-131">Basit bir ASP.NET uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a2b6a-131">To create a simple ASP.NET application</span></span>

1. <span data-ttu-id="a2b6a-132">Visual Studio 'Yu başlatın ve **Dosya**, **Yeni**ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-132">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>

2. <span data-ttu-id="a2b6a-133">**Yeni proje** penceresinde, **ASP.NET Web Forms uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>

3. <span data-ttu-id="a2b6a-134">**Ad**alanına girin `TestApp` ve **Tamam**' a basın.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-134">In **Name**, enter `TestApp` and press **OK**.</span></span>

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="a2b6a-135">2\. adım – Forms kimlik doğrulamasını kullanarak talepler için ASP.NET Web Forms uygulamasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a2b6a-135">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>

<span data-ttu-id="a2b6a-136">Bu adımda, *Web. config* yapılandırma dosyasına bir yapılandırma girişi ekleyecek ve bir hesabın talep bilgilerini görüntülemesi için *default. aspx* dosyasını düzenleyecaksınız.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-136">In this step you will add a configuration entry to the *Web.config* configuration file and edit the *Default.aspx* file to display claims information for an account.</span></span>

### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a><span data-ttu-id="a2b6a-137">Forms kimlik doğrulamasını kullanarak talepler için ASP.NET uygulamasını yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="a2b6a-137">To configure ASP.NET application for claims using Forms authentication</span></span>

1. <span data-ttu-id="a2b6a-138">*Default. aspx* dosyasında, varolan biçimlendirmeyi aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a2b6a-138">In the *Default.aspx* file, replace the existing markup with the following:</span></span>

    ```aspx
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

    <span data-ttu-id="a2b6a-139">Bu adım, *varsayılan. aspx* sayfanıza, Forms kimlik doğrulamasından alınan taleplerle doldurulacak bir GridView denetimi ekler.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-139">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Forms authentication.</span></span>

2. <span data-ttu-id="a2b6a-140">*Default. aspx* dosyasını kaydedin, sonra *default.aspx.cs*adlı arka plan kod dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-140">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="a2b6a-141">Mevcut kodu şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a2b6a-141">Replace the existing code with the following:</span></span>

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

    <span data-ttu-id="a2b6a-142">Yukarıdaki kod, Forms kimlik doğrulaması tarafından tanımlanan kullanıcılar da dahil olmak üzere kimliği doğrulanmış bir kullanıcı hakkında talepler görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-142">The above code will display claims about an authenticated user, including users identified by Forms authentication.</span></span>

## <a name="step-3--test-your-solution"></a><span data-ttu-id="a2b6a-143">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="a2b6a-143">Step 3 – Test Your Solution</span></span>

<span data-ttu-id="a2b6a-144">Bu adımda, ASP.NET Web Forms uygulamanızı test edecek ve Kullanıcı form kimlik doğrulamasıyla oturum açtığında taleplerin sunulduğunu doğrulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-144">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="a2b6a-145">Forms kimlik doğrulaması kullanarak ASP.NET Web Forms uygulamanızı talepler için test etme</span><span class="sxs-lookup"><span data-stu-id="a2b6a-145">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>

1. <span data-ttu-id="a2b6a-146">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-146">Press **F5** to build and run the application.</span></span> <span data-ttu-id="a2b6a-147">Sayfanın sağ üst kısmındaki, **kayıt** ve **oturum açma** bağlantılarına sahip *default. aspx*ile sunulmalısınız.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-147">You should be presented with *Default.aspx*, which has **Register** and **Log in** links in the top right of the page.</span></span> <span data-ttu-id="a2b6a-148">**Kaydol**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-148">Click **Register**.</span></span>

2. <span data-ttu-id="a2b6a-149">**Kaydet** sayfasında, bir kullanıcı hesabı oluşturun ve ardından **Kaydet**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-149">On the **Register** page, create a user account, and then click **Register**.</span></span> <span data-ttu-id="a2b6a-150">Hesabınız, form kimlik doğrulaması kullanılarak oluşturulur ve oturumunuz otomatik olarak açılır.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-150">Your account will be created using Forms authentication, and you will be automatically signed in.</span></span>

3. <span data-ttu-id="a2b6a-151">Giriş sayfasına yönlendirildikten sonra, **talep** başlığının altında yer alan **veren**, **OriginalIssuer**, **Type**, **Value**ve **ValueType** talep bilgilerini içeren bir tablo görmeniz gerekir. hesabı.</span><span class="sxs-lookup"><span data-stu-id="a2b6a-151">After you have been redirected to the home page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span>
