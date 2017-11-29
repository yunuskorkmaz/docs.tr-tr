---
title: "Nasıl yapılır: Görüntü WIF kullanarak durumunda imzalı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 494e67b39187a2a38f29f994e17051430d90f708
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-display-signed-in-status-using-wif"></a><span data-ttu-id="20e65-102">Nasıl yapılır: Görüntü WIF kullanarak durumunda imzalı</span><span class="sxs-lookup"><span data-stu-id="20e65-102">How To: Display Signed In Status Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="20e65-103">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="20e65-103">Applies To</span></span>  
  
-   <span data-ttu-id="20e65-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span><span class="sxs-lookup"><span data-stu-id="20e65-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span></span>  
  
-   <span data-ttu-id="20e65-105">ASP.NET® Web formları</span><span class="sxs-lookup"><span data-stu-id="20e65-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="20e65-106">Özet</span><span class="sxs-lookup"><span data-stu-id="20e65-106">Summary</span></span>  
 <span data-ttu-id="20e65-107">Bu konuda, oturum WIF etkinleştirilmiş ASP.NET uygulamasının durumu görüntülemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="20e65-107">This topic describes how to display the sign in status in a WIF-enabled ASP.NET application.</span></span> <span data-ttu-id="20e65-108">WIF, talep kullanan, uygulama ve yönetme kimlik doğrulama ve yetkilendirme için uygulama kaynaklarını yapmak için mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="20e65-108">WIF provides the mechanism for making your application claims-aware, and managing authentication and authorization for application resources.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="20e65-109">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="20e65-109">Contents</span></span>  
  
-   <span data-ttu-id="20e65-110">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="20e65-110">Overview</span></span>  
  
-   <span data-ttu-id="20e65-111">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="20e65-111">Summary of Steps</span></span>  
  
-   <span data-ttu-id="20e65-112">1. adım – kimlik yüklemek ve erişim uzantısı</span><span class="sxs-lookup"><span data-stu-id="20e65-112">Step 1 – Install the Identity and Access Extension</span></span>  
  
-   <span data-ttu-id="20e65-113">Adım 2 – bir bağlı olan taraf ASP.NET uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="20e65-113">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
-   <span data-ttu-id="20e65-114">Adım 3 – kullanıcıların kimliklerini doğrulamak için etkinleştir yerel geliştirme STS</span><span class="sxs-lookup"><span data-stu-id="20e65-114">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
-   <span data-ttu-id="20e65-115">4. adım – oturum durumunu görüntülemek için ASP.NET uygulamanızın değiştirme</span><span class="sxs-lookup"><span data-stu-id="20e65-115">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
-   <span data-ttu-id="20e65-116">5. adım – WIF ve ASP.NET uygulamanızın arasında tümleştirme Test</span><span class="sxs-lookup"><span data-stu-id="20e65-116">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="overview"></a><span data-ttu-id="20e65-117">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="20e65-117">Overview</span></span>  
 <span data-ttu-id="20e65-118">Bu konu, WIF kullanarak basit bir talep kullanan uygulama oluşturma ve kolay bir kullanıcı veya oturum eşleşmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="20e65-118">This topic demonstrates how to create a simple claims-aware application using WIF and how to easily display whether a user is signed in or not.</span></span> <span data-ttu-id="20e65-119">Kimlik ve erişim Visual Studio uzantısı bulunan yerel geliştirme STS aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="20e65-119">The following steps use the Local Development STS that is included with the Identity and Access Visual Studio Extension.</span></span> <span data-ttu-id="20e65-120">Yerel geliştirme STS talepler uygulamanıza tümleştirmek için basit bir yöntem sağlamak bir test ve geliştirme ortamı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="20e65-120">The Local Development STS is intended for a testing and development environment to provide a simple method of integrating claims into your application.</span></span> <span data-ttu-id="20e65-121">Bunu hiçbir zaman bir üretim ortamında gerçek kimlik doğrulaması gerçekleştirmez ve kimlik bilgileri gerekli değil olarak kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20e65-121">It should never be used in a production environment, as it does not perform real authentication and credentials are not required.</span></span> <span data-ttu-id="20e65-122">Ancak, kesinlik temelli kod aşağıdaki adımlarda gerçek kimlik doğrulaması kullanılarak üretime hazır bir uygulama için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="20e65-122">However, the imperative code in the following steps is the same for a production-ready application using real authentication.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="20e65-123">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="20e65-123">Summary of Steps</span></span>  
  
-   <span data-ttu-id="20e65-124">1. adım – kimlik yüklemek ve erişim uzantısı</span><span class="sxs-lookup"><span data-stu-id="20e65-124">Step 1 – Install the Identity and Access Extension</span></span>  
  
-   <span data-ttu-id="20e65-125">Adım 2 – bir bağlı olan taraf ASP.NET uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="20e65-125">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
-   <span data-ttu-id="20e65-126">Adım 3 – kullanıcıların kimliklerini doğrulamak için etkinleştir yerel geliştirme STS</span><span class="sxs-lookup"><span data-stu-id="20e65-126">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
-   <span data-ttu-id="20e65-127">4. adım – oturum durumunu görüntülemek için ASP.NET uygulamanızın değiştirme</span><span class="sxs-lookup"><span data-stu-id="20e65-127">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
-   <span data-ttu-id="20e65-128">5. adım – WIF ve ASP.NET uygulamanızın arasında tümleştirme Test</span><span class="sxs-lookup"><span data-stu-id="20e65-128">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="step-1--install-the-identity-and-access-extension"></a><span data-ttu-id="20e65-129">1. adım – kimlik yüklemek ve erişim uzantısı</span><span class="sxs-lookup"><span data-stu-id="20e65-129">Step 1 – Install the Identity and Access Extension</span></span>  
 <span data-ttu-id="20e65-130">Bu adım, Visual Studio 2012 için kimlik ve erişim uzantısının nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20e65-130">This step describes how to configure the Identity and Access extension to Visual Studio 2012.</span></span> <span data-ttu-id="20e65-131">Bu uzantı STS uç ile iletişim kurmak için uygulamanızın yapılandırma işlemini otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="20e65-131">This extension automates the process of configuring your application to communicate with STS endpoints.</span></span>  
  
#### <a name="to-install-the-identity-and-access-extension"></a><span data-ttu-id="20e65-132">Kimlik ve erişim uzantıyı yüklemek için</span><span class="sxs-lookup"><span data-stu-id="20e65-132">To install the Identity and Access extension</span></span>  
  
1.  <span data-ttu-id="20e65-133">Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.</span><span class="sxs-lookup"><span data-stu-id="20e65-133">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="20e65-134">Visual Studio'da sırasıyla **Araçları** tıklatıp **Uzantı Yöneticisi**.</span><span class="sxs-lookup"><span data-stu-id="20e65-134">In Visual Studio, click **Tools** and click **Extension Manager**.</span></span> <span data-ttu-id="20e65-135">**Uzantı Yöneticisi** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="20e65-135">The **Extension Manager** window appears.</span></span>  
  
3.  <span data-ttu-id="20e65-136">İçinde **Uzantı Yöneticisi**, tıklatın **çevrimiçi uzantıları** sol menüden seçip **Visual Studio Galerisi**.</span><span class="sxs-lookup"><span data-stu-id="20e65-136">In **Extension Manager**, click **Online Extensions** from the left menu, then select **Visual Studio Gallery**.</span></span>  
  
4.  <span data-ttu-id="20e65-137">Sağ üst köşesindeki **Uzantı Yöneticisi**, arama *kimlik ve erişim*.</span><span class="sxs-lookup"><span data-stu-id="20e65-137">In the top right corner of **Extension Manager**, search for *Identity and Access*.</span></span>  
  
5.  <span data-ttu-id="20e65-138">**Kimlik ve erişim** öğesi, arama sonuçlarında görünür.</span><span class="sxs-lookup"><span data-stu-id="20e65-138">The **Identity and Access** item will appear in the search results.</span></span> <span data-ttu-id="20e65-139">Onu tıklayın ve ardından **karşıdan**.</span><span class="sxs-lookup"><span data-stu-id="20e65-139">Click it, and then click **Download**.</span></span>  
  
6.  <span data-ttu-id="20e65-140">**Yükleyip** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="20e65-140">The **Download and Install** dialog appears.</span></span> <span data-ttu-id="20e65-141">Lisans şartlarını kabul ediyorsanız, tıklatın **yükleme**.</span><span class="sxs-lookup"><span data-stu-id="20e65-141">If you agree with the license terms, click **Install**.</span></span>  
  
7.  <span data-ttu-id="20e65-142">Zaman **kimlik ve erişim** uzantı yükleme tamamlandı, Visual Studio'yu Yönetici modunda yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="20e65-142">When the **Identity and Access** extension has finished installing, restart Visual Studio in administrator mode.</span></span>  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a><span data-ttu-id="20e65-143">Adım 2 – bir bağlı olan taraf ASP.NET uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="20e65-143">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
 <span data-ttu-id="20e65-144">Bu adım, bir bağlı olan taraf WIF ile tümleştirecek ASP.NET Web Forms uygulaması oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="20e65-144">This step describes how to create a relying party ASP.NET Web Forms application that will integrate with WIF.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="20e65-145">Basit bir ASP.NET uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="20e65-145">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="20e65-146">Visual Studio'yu başlatın ve tıklatın **dosya**, **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="20e65-146">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="20e65-147">İçinde **yeni proje** penceresinde tıklatın **ASP.NET Web Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="20e65-147">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="20e65-148">İçinde **adı**, girin `TestApp` ve basın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="20e65-148">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a><span data-ttu-id="20e65-149">Adım 3 – kullanıcıların kimliklerini doğrulamak için etkinleştir yerel geliştirme STS</span><span class="sxs-lookup"><span data-stu-id="20e65-149">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
 <span data-ttu-id="20e65-150">Bu adım, uygulamanızda yerel geliştirme STS etkinleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="20e65-150">This step describes how to enable Local Development STS in your application.</span></span> <span data-ttu-id="20e65-151">Visual Studio için kimlik ve erişim uzantısını kullanarak yerel geliştirme STS etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="20e65-151">Local Development STS is enabled by using the Identity and Access extension for Visual Studio.</span></span>  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a><span data-ttu-id="20e65-152">ASP.NET uygulamanızı yerel geliştirme STS etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="20e65-152">To enable Local Development STS in your ASP.NET application</span></span>  
  
1.  <span data-ttu-id="20e65-153">Visual Studio'da sağ **TestApp** altında proje **Çözüm Gezgini**seçeneğini belirleyip **kimlik ve erişim**.</span><span class="sxs-lookup"><span data-stu-id="20e65-153">In Visual Studio, right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
2.  <span data-ttu-id="20e65-154">**Kimlik ve erişim** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="20e65-154">The **Identity and Access** window appears.</span></span> <span data-ttu-id="20e65-155">Altında **sağlayıcıları**seçin **yerel geliştirme STS ile uygulamanızı Test**, ardından **Uygula**.</span><span class="sxs-lookup"><span data-stu-id="20e65-155">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a><span data-ttu-id="20e65-156">4. adım – oturum durumunu görüntülemek için ASP.NET uygulamanızın değiştirme</span><span class="sxs-lookup"><span data-stu-id="20e65-156">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
 <span data-ttu-id="20e65-157">Bu adım, geçerli kullanıcının oturum açtığı olup olmadığını dinamik olarak görüntülemek için ASP.NET uygulamanızın değiştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="20e65-157">This step describes how to modify your ASP.NET application to dynamically display whether the current user is signed in.</span></span> <span data-ttu-id="20e65-158">STS sağlayıcınız yapılandırıldıktan sonra WIF gelen talepleri işler.</span><span class="sxs-lookup"><span data-stu-id="20e65-158">Once your STS provider has been configured, WIF handles the incoming claims.</span></span> <span data-ttu-id="20e65-159">Şimdi kimlik doğrulaması sonucu görüntülemek için uygulamanızın kod yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="20e65-159">Now you need to configure your application’s code to display the result of the authentication.</span></span>  
  
#### <a name="to-display-sign-in-status"></a><span data-ttu-id="20e65-160">Oturum durumunu görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="20e65-160">To display sign in status</span></span>  
  
1.  <span data-ttu-id="20e65-161">Visual Studio'da açın **Default.aspx** altında dosya **TestApp** projesi.</span><span class="sxs-lookup"><span data-stu-id="20e65-161">In Visual Studio, open the **Default.aspx** file under the **TestApp** project.</span></span>  
  
2.  <span data-ttu-id="20e65-162">Varolan biçimlendirmede Değiştir **Default.aspx** aşağıdaki biçimlendirme dosyasıyla:</span><span class="sxs-lookup"><span data-stu-id="20e65-162">Replace the existing markup in the **Default.aspx** file with the following markup:</span></span>  
  
    ```  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3.  <span data-ttu-id="20e65-163">Kaydet **Default.aspx**ve kendi kod adlı dosyanın arkasındaki açın **Default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="20e65-163">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20e65-164">**Default.aspx.cs** altındaki gizlenebilir **Default.aspx** Çözüm Gezgini'nde.</span><span class="sxs-lookup"><span data-stu-id="20e65-164">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="20e65-165">Varsa **Default.aspx.cs** görünür durumda değilse genişletin **Default.aspx** yanında üçgen tıklayarak.</span><span class="sxs-lookup"><span data-stu-id="20e65-165">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
4.  <span data-ttu-id="20e65-166">Varolan kodla **Default.aspx.cs** aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="20e65-166">Replace the existing code in **Default.aspx.cs** with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="20e65-167">Kaydet **Default.aspx.cs**ve uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="20e65-167">Save **Default.aspx.cs**, and build the application.</span></span>  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a><span data-ttu-id="20e65-168">5. adım – WIF ve ASP.NET uygulamanızın arasında tümleştirme Test</span><span class="sxs-lookup"><span data-stu-id="20e65-168">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
 <span data-ttu-id="20e65-169">Bu adım, WIF ve ASP.NET uygulamanızın arasında tümleştirme test nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="20e65-169">This step describes how you can test the integration between WIF and your ASP.NET application.</span></span>  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a><span data-ttu-id="20e65-170">WIF ve ASP.NET arasında tümleştirme sınamak için</span><span class="sxs-lookup"><span data-stu-id="20e65-170">To test the integration between WIF and ASP.NET</span></span>  
  
1.  <span data-ttu-id="20e65-171">Visual Studio'da basın **F5** uygulamanızı hata ayıklama başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="20e65-171">In Visual Studio, press **F5** to start debugging your application.</span></span> <span data-ttu-id="20e65-172">Herhangi bir hata bulunursa, yeni bir tarayıcı penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="20e65-172">If no errors are found, a new browser window will open.</span></span>  
  
2.  <span data-ttu-id="20e65-173">Tarayıcı sessizce isteğiniz STS yönlendirir ve Default.aspx sayfasında açılır fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20e65-173">You may notice that the browser silently redirects your request to the STS, and then opens the Default.aspx page.</span></span> <span data-ttu-id="20e65-174">WIF düzgün şekilde yapılandırılmışsa, aşağıdaki metni görüntüle sitesini görmeniz gerekir: **", oturumunuz"**.</span><span class="sxs-lookup"><span data-stu-id="20e65-174">If WIF is properly configured, you should see the site display the following text: **"You are signed in"**.</span></span>
