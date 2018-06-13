---
title: 'Nasıl yapılır: Windows kimlik doğrulaması kullanarak talep kullanan ASP.NET uygulaması oluşturma'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2a5dbec2e92d32e45bc0271de04f8c6403f67f90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399801"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a><span data-ttu-id="714b9-102">Nasıl yapılır: Windows kimlik doğrulaması kullanarak talep kullanan ASP.NET uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="714b9-102">How To: Build Claims-Aware ASP.NET Application Using Windows Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="714b9-103">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="714b9-103">Applies To</span></span>  
  
-   <span data-ttu-id="714b9-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="714b9-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="714b9-105">ASP.NET® Web formları</span><span class="sxs-lookup"><span data-stu-id="714b9-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="714b9-106">Özet</span><span class="sxs-lookup"><span data-stu-id="714b9-106">Summary</span></span>  
 <span data-ttu-id="714b9-107">Bu yöntem Windows kimlik doğrulaması kullanan basit bir talep kullanan ASP.NET Web Forms uygulamayı oluşturmak için ayrıntılı adım adım yordamlar verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="714b9-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Windows authentication.</span></span> <span data-ttu-id="714b9-108">Ayrıca, bir kullanıcının Windows kimlik doğrulaması kullanarak oturum açtığında, talep sunulduğundan emin doğrulamak için uygulamayı test etme için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="714b9-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in using Windows authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="714b9-109">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="714b9-109">Contents</span></span>  
  
-   <span data-ttu-id="714b9-110">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="714b9-110">Objectives</span></span>  
  
-   <span data-ttu-id="714b9-111">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="714b9-111">Overview</span></span>  
  
-   <span data-ttu-id="714b9-112">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="714b9-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="714b9-113">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="714b9-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="714b9-114">2. adım – ASP.NET Web Forms uygulaması Windows kimlik doğrulaması kullanarak talep için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="714b9-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="714b9-115">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="714b9-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="714b9-116">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="714b9-116">Objectives</span></span>  
  
-   <span data-ttu-id="714b9-117">Bir ASP.NET Web Forms uygulaması Windows kimlik doğrulaması kullanarak talep için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="714b9-117">Configure an ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
-   <span data-ttu-id="714b9-118">Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamayı test etme</span><span class="sxs-lookup"><span data-stu-id="714b9-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="714b9-119">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="714b9-119">Overview</span></span>  
 <span data-ttu-id="714b9-120">.NET 4.5 WIF ve onun talep tabanlı yetkilendirme Framework'ün ayrılmaz bir parçası dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="714b9-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="714b9-121">Daha önce bir ASP.NET kullanıcı talepleri istediyseniz, WIF yüklemek için gerekli ve ardından cast asıl nesneleri gibi arabirimleri `Thread.CurrentPrincipal` veya `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="714b9-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="714b9-122">Şimdi, talep nesneleri otomatik olarak bu sorumlusu tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="714b9-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="714b9-123">Windows kimlik bilgileri tarafından otomatik olarak kimliği doğrulanmış tüm kullanıcılarının kendileriyle ilişkili talep olduğundan Windows kimlik doğrulaması .NET 4.5 WIF'in eklenmesi benefited.</span><span class="sxs-lookup"><span data-stu-id="714b9-123">Windows authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Windows credentials automatically have claims associated with them.</span></span> <span data-ttu-id="714b9-124">Bu yöntem gösterdiği gibi bu talepler hemen Windows kimlik doğrulaması kullanan bir ASP.NET uygulamasındaki kullanmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="714b9-124">You can begin using these claims immediately in an ASP.NET application that uses Windows authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="714b9-125">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="714b9-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="714b9-126">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="714b9-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="714b9-127">2. adım – ASP.NET Web Forms uygulaması Windows kimlik doğrulaması kullanarak talep için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="714b9-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="714b9-128">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="714b9-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="714b9-129">1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="714b9-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="714b9-130">Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="714b9-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="714b9-131">Basit bir ASP.NET uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="714b9-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="714b9-132">Visual Studio'yu başlatın, ardından **dosya**, **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="714b9-132">Start Visual Studio, then click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="714b9-133">İçinde **yeni proje** penceresinde tıklatın **ASP.NET Web Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="714b9-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="714b9-134">İçinde **adı**, girin `TestApp` ve basın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="714b9-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="714b9-135">Sonra **TestApp** proje oluşturuldu, içinde tıklayın **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="714b9-135">After the **TestApp** project has been created, click on it in **Solution Explorer**.</span></span> <span data-ttu-id="714b9-136">Proje Özellikleri görünür **özellikleri** bölmesinde aşağıdaki **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="714b9-136">The project’s properties will appear in the **Properties** pane below **Solution Explorer**.</span></span> <span data-ttu-id="714b9-137">Ayarlama **Windows kimlik doğrulaması** özelliğine **etkin**.</span><span class="sxs-lookup"><span data-stu-id="714b9-137">Set the **Windows Authentication** property to **Enabled**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="714b9-138">El ile etkinleştirmeniz gerekir böylece Windows kimlik doğrulaması yeni ASP.NET uygulamalarında varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="714b9-138">Windows authentication is disabled by default in new ASP.NET applications, so you must manually enable it.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="714b9-139">2. adım – ASP.NET Web Forms uygulaması Windows kimlik doğrulaması kullanarak talep için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="714b9-139">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
 <span data-ttu-id="714b9-140">Bu adımda, bir yapılandırma girişi ekleyeceksiniz *Web.config* yapılandırma dosyası ve değiştirme *Default.aspx* dosyayı görüntülemek için bir hesap için bilgi talep.</span><span class="sxs-lookup"><span data-stu-id="714b9-140">In this step you will add a configuration entry to the *Web.config* configuration file and modify the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a><span data-ttu-id="714b9-141">Windows kimlik doğrulaması kullanarak talepler için ASP.NET uygulamanızı yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="714b9-141">To configure ASP.NET application for claims using Windows authentication</span></span>  
  
1.  <span data-ttu-id="714b9-142">İçinde **TestApp** projenin *Default.aspx* dosya, varolan biçimlendirme şununla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="714b9-142">In the **TestApp** project’s *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
    ```  
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
  
     <span data-ttu-id="714b9-143">Bu adım bir GridView denetimini ekler, *Default.aspx* talepleri ile doldurulur sayfasında Windows kimlik doğrulamasını alınır.</span><span class="sxs-lookup"><span data-stu-id="714b9-143">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Windows authentication.</span></span>  
  
2.  <span data-ttu-id="714b9-144">Kaydet *Default.aspx* dosya sonra adlı kendi arka plan kodu dosyasını açın *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="714b9-144">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="714b9-145">Var olan kodu aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="714b9-145">Replace the existing code with the following:</span></span>  
  
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
  
     <span data-ttu-id="714b9-146">Yukarıdaki kod kimliği doğrulanmış bir kullanıcı hakkında talepleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="714b9-146">The above code will display claims about an authenticated user.</span></span>  
  
3.  <span data-ttu-id="714b9-147">Uygulamanın kimlik doğrulaması türünü değiştirmek için değiştirmek  **\<kimlik doğrulama >** engelleyin  **\<system.web >** projenin kök bölümünü  *Web.config* yalnızca aşağıdaki yapılandırma girdisi içeren dosya:</span><span class="sxs-lookup"><span data-stu-id="714b9-147">To change the application’s authentication type, modify the **\<authentication>** block in the **\<system.web>** section of the project’s root *Web.config* file so that it only includes the following configuration entry:</span></span>  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4.  <span data-ttu-id="714b9-148">Son olarak, değişiklik  **\<yetkilendirme >** engelleyin  **\<system.web >** aynı bölümünü *Web.config* zorlamak için dosya kimlik doğrulaması:</span><span class="sxs-lookup"><span data-stu-id="714b9-148">Finally, modify the **\<authorization>** block in the **\<system.web>** section of the same *Web.config* file to force authentication:</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="714b9-149">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="714b9-149">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="714b9-150">Bu adımda ASP.NET Web Forms uygulamanızı test etmek ve kullanıcı Windows kimlik doğrulaması ile oturum açtığında, talep sunulduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="714b9-150">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Windows authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="714b9-151">Windows kimlik doğrulaması kullanarak talepler için ASP.NET Web Forms uygulamanızı test etmek için</span><span class="sxs-lookup"><span data-stu-id="714b9-151">To test your ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
1.  <span data-ttu-id="714b9-152">Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="714b9-152">Press **F5** to build and run the application.</span></span> <span data-ttu-id="714b9-153">İle sunulan *Default.aspx*, ve (etki alanı adı dahil), Windows hesap adı zaten üst kimliği doğrulanmış kullanıcı olarak görünmesi gereken sağ sayfasının.</span><span class="sxs-lookup"><span data-stu-id="714b9-153">You should be presented with *Default.aspx*, and your Windows account name (including domain name) should already appear as the authenticated user in the top right of the page.</span></span> <span data-ttu-id="714b9-154">Sayfanın içeriğinin Windows hesabınızdan alınan talep ile doldurulduğu bir tablo içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="714b9-154">The page’s content should include a table filled with claims retrieved from your Windows account.</span></span>
