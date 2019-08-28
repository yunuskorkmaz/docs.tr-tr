---
title: 'Nasıl yapılır: Windows Kimlik Doğrulaması Kullanarak Talep Kullanan ASP.NET Uygulaması Derleme'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 34d6c7916b3035e9896b1dd9d7c7d8b3e7b0fcfc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040991"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a><span data-ttu-id="28cdd-102">Nasıl yapılır: Windows Kimlik Doğrulaması Kullanarak Talep Kullanan ASP.NET Uygulaması Derleme</span><span class="sxs-lookup"><span data-stu-id="28cdd-102">How To: Build Claims-Aware ASP.NET Application Using Windows Authentication</span></span>

## <a name="applies-to"></a><span data-ttu-id="28cdd-103">Uygulanan Öğe</span><span class="sxs-lookup"><span data-stu-id="28cdd-103">Applies To</span></span>

- <span data-ttu-id="28cdd-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="28cdd-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="28cdd-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="28cdd-105">ASP.NET® Web Forms</span></span>

## <a name="summary"></a><span data-ttu-id="28cdd-106">Özet</span><span class="sxs-lookup"><span data-stu-id="28cdd-106">Summary</span></span>

<span data-ttu-id="28cdd-107">Bu nasıl yapılır, Windows kimlik doğrulaması kullanan basit bir talep kullanan ASP.NET Web Forms uygulaması oluşturmaya yönelik ayrıntılı adım adım yordamlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="28cdd-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Windows authentication.</span></span> <span data-ttu-id="28cdd-108">Ayrıca, bir Kullanıcı Windows kimlik doğrulaması kullanarak oturum açtığında taleplerin sunulduğunu doğrulamak için uygulamanın nasıl test alınacağını belirten yönergeler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="28cdd-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in using Windows authentication.</span></span>

## <a name="contents"></a><span data-ttu-id="28cdd-109">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="28cdd-109">Contents</span></span>

- <span data-ttu-id="28cdd-110">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="28cdd-110">Objectives</span></span>

- <span data-ttu-id="28cdd-111">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="28cdd-111">Overview</span></span>

- <span data-ttu-id="28cdd-112">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="28cdd-112">Summary of Steps</span></span>

- <span data-ttu-id="28cdd-113">1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="28cdd-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="28cdd-114">2\. Adım – Windows kimlik doğrulamasını kullanarak talepler için ASP.NET Web Forms uygulamasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="28cdd-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>

- <span data-ttu-id="28cdd-115">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="28cdd-115">Step 3 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="28cdd-116">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="28cdd-116">Objectives</span></span>

- <span data-ttu-id="28cdd-117">Windows kimlik doğrulamasını kullanarak talepler için bir ASP.NET Web Forms uygulaması yapılandırma</span><span class="sxs-lookup"><span data-stu-id="28cdd-117">Configure an ASP.NET Web Forms application for claims using Windows authentication</span></span>

- <span data-ttu-id="28cdd-118">Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamasını test etme</span><span class="sxs-lookup"><span data-stu-id="28cdd-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>

## <a name="overview"></a><span data-ttu-id="28cdd-119">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="28cdd-119">Overview</span></span>

<span data-ttu-id="28cdd-120">.NET 4,5 ' de, WıF ve talep tabanlı yetkilendirme, Framework 'ün ayrılmaz bir parçası olarak eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="28cdd-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="28cdd-121">Daha önce, bir ASP.net kullanıcısının taleplerini istediyseniz, WIF 'yi yüklemeli ve ardından arabirimleri veya `Thread.CurrentPrincipal` `HttpContext.Current.User`gibi Principal nesnelerine atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="28cdd-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="28cdd-122">Artık talepler, bu Principal nesneleri tarafından otomatik olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="28cdd-122">Now, claims are served automatically by these Principal objects.</span></span>

<span data-ttu-id="28cdd-123">Windows kimlik bilgileri tarafından kimlik doğrulaması yapılan tüm kullanıcılar otomatik olarak bunlarla ilişkili talepler içerdiğinden, Windows kimlik doğrulamasının .NET 4,5 ' ye dahil edildiği benefited vardır.</span><span class="sxs-lookup"><span data-stu-id="28cdd-123">Windows authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Windows credentials automatically have claims associated with them.</span></span> <span data-ttu-id="28cdd-124">Bu talepleri, nasıl gösterildiği gibi, Windows kimlik doğrulaması kullanan bir ASP.NET uygulamasında hemen kullanmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28cdd-124">You can begin using these claims immediately in an ASP.NET application that uses Windows authentication, as this How-To demonstrates.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="28cdd-125">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="28cdd-125">Summary of Steps</span></span>

- <span data-ttu-id="28cdd-126">1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="28cdd-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="28cdd-127">2\. Adım – Windows kimlik doğrulamasını kullanarak talepler için ASP.NET Web Forms uygulamasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="28cdd-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>

- <span data-ttu-id="28cdd-128">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="28cdd-128">Step 3 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="28cdd-129">1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="28cdd-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

<span data-ttu-id="28cdd-130">Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="28cdd-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>

### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="28cdd-131">Basit bir ASP.NET uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="28cdd-131">To create a simple ASP.NET application</span></span>

1. <span data-ttu-id="28cdd-132">Visual Studio 'yu başlatın ve ardından **Dosya**, **Yeni**ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="28cdd-132">Start Visual Studio, then click **File**, **New**, and then **Project**.</span></span>

2. <span data-ttu-id="28cdd-133">**Yeni proje** penceresinde, **ASP.NET Web Forms uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="28cdd-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>

3. <span data-ttu-id="28cdd-134">**Ad**alanına girin `TestApp` ve **Tamam**' a basın.</span><span class="sxs-lookup"><span data-stu-id="28cdd-134">In **Name**, enter `TestApp` and press **OK**.</span></span>

4. <span data-ttu-id="28cdd-135">**TestApp** projesi oluşturulduktan sonra **Çözüm Gezgini**' de tıklayın.</span><span class="sxs-lookup"><span data-stu-id="28cdd-135">After the **TestApp** project has been created, click on it in **Solution Explorer**.</span></span> <span data-ttu-id="28cdd-136">Projenin özellikleri **Çözüm Gezgini**aşağıdaki **Özellikler** bölmesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="28cdd-136">The project’s properties will appear in the **Properties** pane below **Solution Explorer**.</span></span> <span data-ttu-id="28cdd-137">**Windows kimlik doğrulama** özelliğini **etkin**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="28cdd-137">Set the **Windows Authentication** property to **Enabled**.</span></span>

    > [!WARNING]
    > <span data-ttu-id="28cdd-138">Windows kimlik doğrulaması, yeni ASP.NET uygulamalarında varsayılan olarak devre dışıdır, bu yüzden el ile etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="28cdd-138">Windows authentication is disabled by default in new ASP.NET applications, so you must manually enable it.</span></span>

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="28cdd-139">2\. Adım – Windows kimlik doğrulamasını kullanarak talepler için ASP.NET Web Forms uygulamasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="28cdd-139">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>

<span data-ttu-id="28cdd-140">Bu adımda, *Web. config* yapılandırma dosyasına bir yapılandırma girişi ekleyecek ve *varsayılan. aspx* dosyasını değiştirerek bir hesabın talep bilgilerini görüntüleyecek şekilde değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28cdd-140">In this step you will add a configuration entry to the *Web.config* configuration file and modify the *Default.aspx* file to display claims information for an account.</span></span>

### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a><span data-ttu-id="28cdd-141">Windows kimlik doğrulamasını kullanarak ASP.NET uygulamasını talepler için yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="28cdd-141">To configure ASP.NET application for claims using Windows authentication</span></span>

1. <span data-ttu-id="28cdd-142">**TestApp** projesinin *default. aspx* dosyasında, varolan biçimlendirmeyi aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="28cdd-142">In the **TestApp** project’s *Default.aspx* file, replace the existing markup with the following:</span></span>

    ```aspx-csharp
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
        <p>
            This page displays the claims associated with a Windows authenticated user.
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

    <span data-ttu-id="28cdd-143">Bu adım, *default. aspx* sayfanıza, Windows kimlik doğrulamasından alınan taleplerle doldurulacak bir GridView denetimi ekler.</span><span class="sxs-lookup"><span data-stu-id="28cdd-143">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Windows authentication.</span></span>

2. <span data-ttu-id="28cdd-144">*Default. aspx* dosyasını kaydedin, sonra *default.aspx.cs*adlı arka plan kod dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="28cdd-144">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="28cdd-145">Mevcut kodu şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="28cdd-145">Replace the existing code with the following:</span></span>

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

    <span data-ttu-id="28cdd-146">Yukarıdaki kodda kimliği doğrulanmış bir kullanıcı hakkında talepler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="28cdd-146">The above code will display claims about an authenticated user.</span></span>

3. <span data-ttu-id="28cdd-147">Uygulamanın kimlik doğrulaması türünü değiştirmek için, projenin kök *Web. config* dosyasının  **\<System. Web >** bölümündeki  **\<Authentication >** bloğunu yalnızca aşağıdakileri içerecek şekilde değiştirin yapılandırma girişi:</span><span class="sxs-lookup"><span data-stu-id="28cdd-147">To change the application’s authentication type, modify the **\<authentication>** block in the **\<system.web>** section of the project’s root *Web.config* file so that it only includes the following configuration entry:</span></span>

    ```xml
    <authentication mode="Windows" />
    ```

4. <span data-ttu-id="28cdd-148">Son olarak, kimlik doğrulamayı zorlamak için aynı *Web. config* dosyasının  **\<System. Web >** bölümündeki  **\<Authorization >** bloğunu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="28cdd-148">Finally, modify the **\<authorization>** block in the **\<system.web>** section of the same *Web.config* file to force authentication:</span></span>

    ```xml
    <authorization>
        <deny users="?" />
    </authorization>
    ```

## <a name="step-3--test-your-solution"></a><span data-ttu-id="28cdd-149">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="28cdd-149">Step 3 – Test Your Solution</span></span>

<span data-ttu-id="28cdd-150">Bu adımda, ASP.NET Web Forms uygulamanızı test edecek ve Kullanıcı Windows kimlik doğrulamasıyla oturum açtığında taleplerin sunulduğunu doğrulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="28cdd-150">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Windows authentication.</span></span>

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="28cdd-151">Windows kimlik doğrulamasını kullanarak ASP.NET Web Forms uygulamanızı talepler için test etme</span><span class="sxs-lookup"><span data-stu-id="28cdd-151">To test your ASP.NET Web Forms application for claims using Windows authentication</span></span>

1. <span data-ttu-id="28cdd-152">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="28cdd-152">Press **F5** to build and run the application.</span></span> <span data-ttu-id="28cdd-153">*Default. aspx*ve Windows hesabınızın adı (etki alanı adı dahil), sayfanın sağ üst kısmında kimliği doğrulanmış kullanıcı olarak gösterilmelidir.</span><span class="sxs-lookup"><span data-stu-id="28cdd-153">You should be presented with *Default.aspx*, and your Windows account name (including domain name) should already appear as the authenticated user in the top right of the page.</span></span> <span data-ttu-id="28cdd-154">Sayfanın içeriği, Windows hesabınızdan alınan taleplerle doldurulmuş bir tablo içermelidir.</span><span class="sxs-lookup"><span data-stu-id="28cdd-154">The page’s content should include a table filled with claims retrieved from your Windows account.</span></span>
