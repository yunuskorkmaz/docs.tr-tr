---
title: 'Nasıl yapılır: WIF Kullanarak Oturum Açmış Durumu Gösterme'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: e44dc80260e46b81ac723ada32085390a18a153a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945695"
---
# <a name="how-to-display-signed-in-status-using-wif"></a><span data-ttu-id="c7702-102">Nasıl yapılır: WIF Kullanarak Oturum Açmış Durumu Gösterme</span><span class="sxs-lookup"><span data-stu-id="c7702-102">How To: Display Signed In Status Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="c7702-103">Uygulanan Öğe</span><span class="sxs-lookup"><span data-stu-id="c7702-103">Applies To</span></span>  
  
- <span data-ttu-id="c7702-104">Microsoft® Windows® Identity Foundation (WıF) 4,5</span><span class="sxs-lookup"><span data-stu-id="c7702-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span></span>  
  
- <span data-ttu-id="c7702-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="c7702-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="c7702-106">Özet</span><span class="sxs-lookup"><span data-stu-id="c7702-106">Summary</span></span>  
 <span data-ttu-id="c7702-107">Bu konu, bir WıF-Enabled ASP.NET uygulamasında oturum açma durumunun nasıl görüntüleneceğini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7702-107">This topic describes how to display the sign in status in a WIF-enabled ASP.NET application.</span></span> <span data-ttu-id="c7702-108">WıF, uygulamanızı talep kullanan hale getirme ve uygulama kaynakları için kimlik doğrulama ve Yetkilendirmeyi Yönetme mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7702-108">WIF provides the mechanism for making your application claims-aware, and managing authentication and authorization for application resources.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="c7702-109">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="c7702-109">Contents</span></span>  
  
- <span data-ttu-id="c7702-110">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c7702-110">Overview</span></span>  
  
- <span data-ttu-id="c7702-111">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="c7702-111">Summary of Steps</span></span>  
  
- <span data-ttu-id="c7702-112">1\. Adım – kimlik ve erişim uzantısını yükler</span><span class="sxs-lookup"><span data-stu-id="c7702-112">Step 1 – Install the Identity and Access Extension</span></span>  
  
- <span data-ttu-id="c7702-113">2\. adım – bağlı olan taraf ASP.NET uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7702-113">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
- <span data-ttu-id="c7702-114">3\. adım – kullanıcıların kimliğini doğrulamak için yerel geliştirme STS 'yi etkinleştirin</span><span class="sxs-lookup"><span data-stu-id="c7702-114">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
- <span data-ttu-id="c7702-115">4\. adım – oturum açma durumunu göstermek için ASP.NET uygulamanızı değiştirme</span><span class="sxs-lookup"><span data-stu-id="c7702-115">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
- <span data-ttu-id="c7702-116">5\. adım – WıF ve ASP.NET uygulamanız arasındaki tümleştirmeyi test edin</span><span class="sxs-lookup"><span data-stu-id="c7702-116">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="overview"></a><span data-ttu-id="c7702-117">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c7702-117">Overview</span></span>  
 <span data-ttu-id="c7702-118">Bu konuda, WıF kullanılarak basit bir talep kullanan uygulama oluşturma ve bir kullanıcının oturum açmış olup olmadığını kolayca görüntüleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c7702-118">This topic demonstrates how to create a simple claims-aware application using WIF and how to easily display whether a user is signed in or not.</span></span> <span data-ttu-id="c7702-119">Aşağıdaki adımlarda, Identity ve Access Visual Studio uzantısına dahil olan yerel geliştirme STS 'si kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7702-119">The following steps use the Local Development STS that is included with the Identity and Access Visual Studio Extension.</span></span> <span data-ttu-id="c7702-120">Yerel geliştirme STS, bir test ve geliştirme ortamına, talepleri uygulamanızla tümleştirmeyle ilgili basit bir yöntem sağlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c7702-120">The Local Development STS is intended for a testing and development environment to provide a simple method of integrating claims into your application.</span></span> <span data-ttu-id="c7702-121">Bu, gerçek kimlik doğrulaması gerçekleştirmediğinden ve kimlik bilgilerinin gerekli olmadığından, bir üretim ortamında asla kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7702-121">It should never be used in a production environment, as it does not perform real authentication and credentials are not required.</span></span> <span data-ttu-id="c7702-122">Ancak, aşağıdaki adımlarda zorunlu kod, gerçek kimlik doğrulaması kullanan üretime yönelik bir uygulama için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c7702-122">However, the imperative code in the following steps is the same for a production-ready application using real authentication.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="c7702-123">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="c7702-123">Summary of Steps</span></span>  
  
- <span data-ttu-id="c7702-124">1\. Adım – kimlik ve erişim uzantısını yükler</span><span class="sxs-lookup"><span data-stu-id="c7702-124">Step 1 – Install the Identity and Access Extension</span></span>  
  
- <span data-ttu-id="c7702-125">2\. adım – bağlı olan taraf ASP.NET uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7702-125">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
- <span data-ttu-id="c7702-126">3\. adım – kullanıcıların kimliğini doğrulamak için yerel geliştirme STS 'yi etkinleştirin</span><span class="sxs-lookup"><span data-stu-id="c7702-126">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
- <span data-ttu-id="c7702-127">4\. adım – oturum açma durumunu göstermek için ASP.NET uygulamanızı değiştirme</span><span class="sxs-lookup"><span data-stu-id="c7702-127">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
- <span data-ttu-id="c7702-128">5\. adım – WıF ve ASP.NET uygulamanız arasındaki tümleştirmeyi test edin</span><span class="sxs-lookup"><span data-stu-id="c7702-128">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="step-1--install-the-identity-and-access-extension"></a><span data-ttu-id="c7702-129">1\. Adım – kimlik ve erişim uzantısını yükler</span><span class="sxs-lookup"><span data-stu-id="c7702-129">Step 1 – Install the Identity and Access Extension</span></span>  
 <span data-ttu-id="c7702-130">Bu adım, kimlik ve erişim uzantısının Visual Studio 2012 ' a nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7702-130">This step describes how to configure the Identity and Access extension to Visual Studio 2012.</span></span> <span data-ttu-id="c7702-131">Bu uzantı, uygulamanızı STS uç noktalarıyla iletişim kuracak şekilde yapılandırma sürecini otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="c7702-131">This extension automates the process of configuring your application to communicate with STS endpoints.</span></span>  
  
### <a name="to-install-the-identity-and-access-extension"></a><span data-ttu-id="c7702-132">Kimliği ve erişim uzantısını yüklemek için</span><span class="sxs-lookup"><span data-stu-id="c7702-132">To install the Identity and Access extension</span></span>  
  
1. <span data-ttu-id="c7702-133">Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.</span><span class="sxs-lookup"><span data-stu-id="c7702-133">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2. <span data-ttu-id="c7702-134">Visual Studio 'da **Araçlar** ' a tıklayın ve **Uzantı Yöneticisi**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7702-134">In Visual Studio, click **Tools** and click **Extension Manager**.</span></span> <span data-ttu-id="c7702-135">**Uzantı Yöneticisi** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c7702-135">The **Extension Manager** window appears.</span></span>  
  
3. <span data-ttu-id="c7702-136">**Uzantı Yöneticisi**'nde sol menüden **çevrimiçi uzantılar** ' a tıklayın ve ardından **Visual Studio Galerisi**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="c7702-136">In **Extension Manager**, click **Online Extensions** from the left menu, then select **Visual Studio Gallery**.</span></span>  
  
4. <span data-ttu-id="c7702-137">**Uzantı yöneticisinin**sağ üst köşesinde *kimlik ve erişim*' i arayın.</span><span class="sxs-lookup"><span data-stu-id="c7702-137">In the top right corner of **Extension Manager**, search for *Identity and Access*.</span></span>  
  
5. <span data-ttu-id="c7702-138">**Kimlik ve erişim** öğesi arama sonuçlarında görünür.</span><span class="sxs-lookup"><span data-stu-id="c7702-138">The **Identity and Access** item will appear in the search results.</span></span> <span data-ttu-id="c7702-139">Tıklayın ve ardından **İndir**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7702-139">Click it, and then click **Download**.</span></span>  
  
6. <span data-ttu-id="c7702-140">**İndir ve yükle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c7702-140">The **Download and Install** dialog appears.</span></span> <span data-ttu-id="c7702-141">Lisans koşullarını kabul ediyorsanız, **yükler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7702-141">If you agree with the license terms, click **Install**.</span></span>  
  
7. <span data-ttu-id="c7702-142">**Kimlik ve erişim** uzantısının yüklenmesi tamamlandığında, Visual Studio 'yu yönetici modunda yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="c7702-142">When the **Identity and Access** extension has finished installing, restart Visual Studio in administrator mode.</span></span>  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a><span data-ttu-id="c7702-143">2\. adım – bağlı olan taraf ASP.NET uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7702-143">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
 <span data-ttu-id="c7702-144">Bu adımda, WıF ile tümleştirilecek bir bağlı olan taraf ASP.NET Web Forms uygulamasının nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7702-144">This step describes how to create a relying party ASP.NET Web Forms application that will integrate with WIF.</span></span>  
  
### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="c7702-145">Basit bir ASP.NET uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c7702-145">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="c7702-146">Visual Studio 'Yu başlatın ve **Dosya**, **Yeni**ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7702-146">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="c7702-147">**Yeni proje** penceresinde, **ASP.NET Web Forms uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7702-147">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="c7702-148">**Ad**alanına girin `TestApp` ve **Tamam**' a basın.</span><span class="sxs-lookup"><span data-stu-id="c7702-148">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a><span data-ttu-id="c7702-149">3\. adım – kullanıcıların kimliğini doğrulamak için yerel geliştirme STS 'yi etkinleştirin</span><span class="sxs-lookup"><span data-stu-id="c7702-149">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
 <span data-ttu-id="c7702-150">Bu adımda, uygulamanızda yerel geliştirme STS 'nin nasıl etkinleştirileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="c7702-150">This step describes how to enable Local Development STS in your application.</span></span> <span data-ttu-id="c7702-151">Yerel geliştirme STS, Visual Studio için kimlik ve erişim uzantısı kullanılarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c7702-151">Local Development STS is enabled by using the Identity and Access extension for Visual Studio.</span></span>  
  
### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a><span data-ttu-id="c7702-152">ASP.NET uygulamanızda yerel geliştirme STS 'sini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="c7702-152">To enable Local Development STS in your ASP.NET application</span></span>  
  
1. <span data-ttu-id="c7702-153">Visual Studio 'da, **Çözüm Gezgini**altında **TestApp** projesine sağ tıklayın **ve ardından kimlik ve erişim**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="c7702-153">In Visual Studio, right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
2. <span data-ttu-id="c7702-154">**Kimlik ve erişim** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c7702-154">The **Identity and Access** window appears.</span></span> <span data-ttu-id="c7702-155">**Sağlayıcılar**bölümünde, **yerel geliştirme sts 'Si Ile uygulamanızı test et**' i seçin ve **Uygula**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7702-155">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a><span data-ttu-id="c7702-156">4\. adım – oturum açma durumunu göstermek için ASP.NET uygulamanızı değiştirme</span><span class="sxs-lookup"><span data-stu-id="c7702-156">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
 <span data-ttu-id="c7702-157">Bu adımda, geçerli kullanıcının oturum açmış olup olmadığını dinamik olarak göstermek için ASP.NET uygulamanızın nasıl değiştirileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="c7702-157">This step describes how to modify your ASP.NET application to dynamically display whether the current user is signed in.</span></span> <span data-ttu-id="c7702-158">STS sağlayıcınız yapılandırıldıktan sonra, gelen talepleri işler.</span><span class="sxs-lookup"><span data-stu-id="c7702-158">Once your STS provider has been configured, WIF handles the incoming claims.</span></span> <span data-ttu-id="c7702-159">Şimdi, kimlik doğrulamasının sonucunu göstermek için uygulamanızın kodunu yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7702-159">Now you need to configure your application’s code to display the result of the authentication.</span></span>  
  
### <a name="to-display-sign-in-status"></a><span data-ttu-id="c7702-160">Oturum açma durumunu görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c7702-160">To display sign in status</span></span>  
  
1. <span data-ttu-id="c7702-161">Visual Studio 'da **TestApp** projesi altındaki **default. aspx** dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="c7702-161">In Visual Studio, open the **Default.aspx** file under the **TestApp** project.</span></span>  
  
2. <span data-ttu-id="c7702-162">**Default. aspx** dosyasındaki mevcut biçimlendirmeyi aşağıdaki biçimlendirme ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c7702-162">Replace the existing markup in the **Default.aspx** file with the following markup:</span></span>  
  
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
  
3. <span data-ttu-id="c7702-163">**Default. aspx**' i kaydedin ve sonra kodu **default.aspx.cs**adlı dosyanın arkasında açın.</span><span class="sxs-lookup"><span data-stu-id="c7702-163">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c7702-164">**Default.aspx.cs** , Çözüm Gezgini içinde **default. aspx** altında gizlenebilir.</span><span class="sxs-lookup"><span data-stu-id="c7702-164">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="c7702-165">**Default.aspx.cs** görünür değilse, bunun yanındaki üçgene tıklayarak **default. aspx** ' i genişletin.</span><span class="sxs-lookup"><span data-stu-id="c7702-165">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
4. <span data-ttu-id="c7702-166">**Default.aspx.cs** içindeki mevcut kodu şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c7702-166">Replace the existing code in **Default.aspx.cs** with the following code:</span></span>  
  
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
  
5. <span data-ttu-id="c7702-167">**Default.aspx.cs**kaydedin ve uygulamayı derleyin.</span><span class="sxs-lookup"><span data-stu-id="c7702-167">Save **Default.aspx.cs**, and build the application.</span></span>  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a><span data-ttu-id="c7702-168">5\. adım – WıF ve ASP.NET uygulamanız arasındaki tümleştirmeyi test edin</span><span class="sxs-lookup"><span data-stu-id="c7702-168">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
 <span data-ttu-id="c7702-169">Bu adım, WıF ve ASP.NET uygulamanız arasındaki tümleştirmeyi nasıl test kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7702-169">This step describes how you can test the integration between WIF and your ASP.NET application.</span></span>  
  
### <a name="to-test-the-integration-between-wif-and-aspnet"></a><span data-ttu-id="c7702-170">WIF ve ASP.NET arasındaki tümleştirmeyi test etmek için</span><span class="sxs-lookup"><span data-stu-id="c7702-170">To test the integration between WIF and ASP.NET</span></span>  
  
1. <span data-ttu-id="c7702-171">Visual Studio 'da, uygulamanızda hata ayıklamayı başlatmak için **F5** ' e basın.</span><span class="sxs-lookup"><span data-stu-id="c7702-171">In Visual Studio, press **F5** to start debugging your application.</span></span> <span data-ttu-id="c7702-172">Herhangi bir hata bulunmazsa yeni bir tarayıcı penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="c7702-172">If no errors are found, a new browser window will open.</span></span>  
  
2. <span data-ttu-id="c7702-173">Tarayıcının isteğinizi sessizce yeniden yönlendirdiğine ve ardından default. aspx sayfasını açmasını fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7702-173">You may notice that the browser silently redirects your request to the STS, and then opens the Default.aspx page.</span></span> <span data-ttu-id="c7702-174">WıF düzgün yapılandırıldıysa, sitenin aşağıdaki metni görüntülemesini görmeniz gerekir: **"Oturumunuz açıldı"** .</span><span class="sxs-lookup"><span data-stu-id="c7702-174">If WIF is properly configured, you should see the site display the following text: **"You are signed in"**.</span></span>
