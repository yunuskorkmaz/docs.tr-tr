---
title: 'Nasıl yapılır: WIF Kullanarak Oturum Açmış Durumu Gösterme'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: 6d81bd2023886799f939fc9851db516a00aa92df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742444"
---
# <a name="how-to-display-signed-in-status-using-wif"></a><span data-ttu-id="9b05a-102">Nasıl yapılır: WIF Kullanarak Oturum Açmış Durumu Gösterme</span><span class="sxs-lookup"><span data-stu-id="9b05a-102">How To: Display Signed In Status Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="9b05a-103">Uygulanan Öğe</span><span class="sxs-lookup"><span data-stu-id="9b05a-103">Applies To</span></span>  
  
- <span data-ttu-id="9b05a-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span><span class="sxs-lookup"><span data-stu-id="9b05a-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span></span>  
  
- <span data-ttu-id="9b05a-105">ASP.NET® Web formları</span><span class="sxs-lookup"><span data-stu-id="9b05a-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="9b05a-106">Özet</span><span class="sxs-lookup"><span data-stu-id="9b05a-106">Summary</span></span>  
 <span data-ttu-id="9b05a-107">Bu konuda, oturum durumu WIF özelliği etkinleştirilmiş bir ASP.NET uygulamasında görüntülenecek açıklar.</span><span class="sxs-lookup"><span data-stu-id="9b05a-107">This topic describes how to display the sign in status in a WIF-enabled ASP.NET application.</span></span> <span data-ttu-id="9b05a-108">WIF, talep kullanan, uygulama ve yönetme kimlik doğrulaması ve yetkilendirme için uygulama kaynakları oluşturmaya yönelik bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b05a-108">WIF provides the mechanism for making your application claims-aware, and managing authentication and authorization for application resources.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="9b05a-109">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="9b05a-109">Contents</span></span>  
  
- <span data-ttu-id="9b05a-110">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9b05a-110">Overview</span></span>  
  
- <span data-ttu-id="9b05a-111">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="9b05a-111">Summary of Steps</span></span>  
  
- <span data-ttu-id="9b05a-112">1\. adım – yükleme kimlik ve erişim uzantısı</span><span class="sxs-lookup"><span data-stu-id="9b05a-112">Step 1 – Install the Identity and Access Extension</span></span>  
  
- <span data-ttu-id="9b05a-113">2\. adım – bir bağlı olan taraf ASP.NET uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="9b05a-113">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
- <span data-ttu-id="9b05a-114">Adım 3 – kullanıcıların kimliğini doğrulamak için etkinleştirme yerel geliştirme</span><span class="sxs-lookup"><span data-stu-id="9b05a-114">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
- <span data-ttu-id="9b05a-115">4\. adım: ASP.NET uygulamanız oturum durumu görüntülemek için değiştirin</span><span class="sxs-lookup"><span data-stu-id="9b05a-115">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
- <span data-ttu-id="9b05a-116">5\. adım – WIF ve ASP.NET uygulamanız arasındaki tümleştirme testi</span><span class="sxs-lookup"><span data-stu-id="9b05a-116">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="overview"></a><span data-ttu-id="9b05a-117">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9b05a-117">Overview</span></span>  
 <span data-ttu-id="9b05a-118">Bu konuda, WIF kullanarak talep kullanan uygulama oluşturmak nasıl ve nasıl kolayca veya bir kullanıcı oturumu açıkken eşleşmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9b05a-118">This topic demonstrates how to create a simple claims-aware application using WIF and how to easily display whether a user is signed in or not.</span></span> <span data-ttu-id="9b05a-119">Kimlik ve erişim Visual Studio uzantısı dahil olan yerel geliştirme STS'si aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="9b05a-119">The following steps use the Local Development STS that is included with the Identity and Access Visual Studio Extension.</span></span> <span data-ttu-id="9b05a-120">Yerel geliştirme STS'si talep uygulamanızla tümleştirmenin basit bir yöntem sağlamak amacıyla bir test ve geliştirme ortamı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9b05a-120">The Local Development STS is intended for a testing and development environment to provide a simple method of integrating claims into your application.</span></span> <span data-ttu-id="9b05a-121">Hiçbir zaman bir üretim ortamında gerçek kimlik doğrulaması gerçekleştirmez ve kimlik bilgileri gerekli değil olarak kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b05a-121">It should never be used in a production environment, as it does not perform real authentication and credentials are not required.</span></span> <span data-ttu-id="9b05a-122">Ancak, kesinlik temelli kod aşağıdaki adımlarda gerçek kimlik doğrulaması kullanarak üretime hazır bir uygulama için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9b05a-122">However, the imperative code in the following steps is the same for a production-ready application using real authentication.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="9b05a-123">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="9b05a-123">Summary of Steps</span></span>  
  
- <span data-ttu-id="9b05a-124">1\. adım – yükleme kimlik ve erişim uzantısı</span><span class="sxs-lookup"><span data-stu-id="9b05a-124">Step 1 – Install the Identity and Access Extension</span></span>  
  
- <span data-ttu-id="9b05a-125">2\. adım – bir bağlı olan taraf ASP.NET uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="9b05a-125">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
- <span data-ttu-id="9b05a-126">Adım 3 – kullanıcıların kimliğini doğrulamak için etkinleştirme yerel geliştirme</span><span class="sxs-lookup"><span data-stu-id="9b05a-126">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
- <span data-ttu-id="9b05a-127">4\. adım: ASP.NET uygulamanız oturum durumu görüntülemek için değiştirin</span><span class="sxs-lookup"><span data-stu-id="9b05a-127">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
- <span data-ttu-id="9b05a-128">5\. adım – WIF ve ASP.NET uygulamanız arasındaki tümleştirme testi</span><span class="sxs-lookup"><span data-stu-id="9b05a-128">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="step-1--install-the-identity-and-access-extension"></a><span data-ttu-id="9b05a-129">1\. adım – yükleme kimlik ve erişim uzantısı</span><span class="sxs-lookup"><span data-stu-id="9b05a-129">Step 1 – Install the Identity and Access Extension</span></span>  
 <span data-ttu-id="9b05a-130">Bu adımda, Visual Studio 2012 için kimlik ve erişim uzantısının nasıl yapılandırılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="9b05a-130">This step describes how to configure the Identity and Access extension to Visual Studio 2012.</span></span> <span data-ttu-id="9b05a-131">Bu uzantı STS uç noktaları ile iletişim kurmak için uygulamanızı yapılandırma işlemi otomatik hale getirir.</span><span class="sxs-lookup"><span data-stu-id="9b05a-131">This extension automates the process of configuring your application to communicate with STS endpoints.</span></span>  
  
### <a name="to-install-the-identity-and-access-extension"></a><span data-ttu-id="9b05a-132">Kimlik ve erişim uzantıyı yüklemek için</span><span class="sxs-lookup"><span data-stu-id="9b05a-132">To install the Identity and Access extension</span></span>  
  
1. <span data-ttu-id="9b05a-133">Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.</span><span class="sxs-lookup"><span data-stu-id="9b05a-133">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2. <span data-ttu-id="9b05a-134">Visual Studio'da **Araçları** tıklatıp **Uzantı Yöneticisi**.</span><span class="sxs-lookup"><span data-stu-id="9b05a-134">In Visual Studio, click **Tools** and click **Extension Manager**.</span></span> <span data-ttu-id="9b05a-135">**Uzantı Yöneticisi** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9b05a-135">The **Extension Manager** window appears.</span></span>  
  
3. <span data-ttu-id="9b05a-136">İçinde **Uzantı Yöneticisi**, tıklayın **çevrimiçi uzantılara** seçip sol menüden **Visual Studio Galerisi**.</span><span class="sxs-lookup"><span data-stu-id="9b05a-136">In **Extension Manager**, click **Online Extensions** from the left menu, then select **Visual Studio Gallery**.</span></span>  
  
4. <span data-ttu-id="9b05a-137">Sağ üst köşesindeki içinde **Uzantı Yöneticisi**, arama *kimlik ve erişim*.</span><span class="sxs-lookup"><span data-stu-id="9b05a-137">In the top right corner of **Extension Manager**, search for *Identity and Access*.</span></span>  
  
5. <span data-ttu-id="9b05a-138">**Kimlik ve erişim** öğesi, arama sonuçlarında görünür.</span><span class="sxs-lookup"><span data-stu-id="9b05a-138">The **Identity and Access** item will appear in the search results.</span></span> <span data-ttu-id="9b05a-139">Tıklayın ve ardından **indirme**.</span><span class="sxs-lookup"><span data-stu-id="9b05a-139">Click it, and then click **Download**.</span></span>  
  
6. <span data-ttu-id="9b05a-140">**Yükleyip** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9b05a-140">The **Download and Install** dialog appears.</span></span> <span data-ttu-id="9b05a-141">Lisans şartlarını kabul ediyorsanız tıklayın **yükleme**.</span><span class="sxs-lookup"><span data-stu-id="9b05a-141">If you agree with the license terms, click **Install**.</span></span>  
  
7. <span data-ttu-id="9b05a-142">Zaman **kimlik ve erişim** uzantı yükleme tamamlandığında, Visual Studio'yu Yönetici modunda yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="9b05a-142">When the **Identity and Access** extension has finished installing, restart Visual Studio in administrator mode.</span></span>  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a><span data-ttu-id="9b05a-143">2\. adım – bir bağlı olan taraf ASP.NET uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="9b05a-143">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
 <span data-ttu-id="9b05a-144">Bu adım, bağlı olan taraf WIF ile tümleştirilecek bir ASP.NET Web Forms uygulaması oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="9b05a-144">This step describes how to create a relying party ASP.NET Web Forms application that will integrate with WIF.</span></span>  
  
### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="9b05a-145">Basit bir ASP.NET uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9b05a-145">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="9b05a-146">Visual Studio'yu başlatın ve tıklayın **dosya**, **yeni**, ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="9b05a-146">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="9b05a-147">İçinde **yeni proje** penceresinde tıklayın **ASP.NET Web Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="9b05a-147">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="9b05a-148">İçinde **adı**, girin `TestApp` basın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="9b05a-148">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a><span data-ttu-id="9b05a-149">Adım 3 – kullanıcıların kimliğini doğrulamak için etkinleştirme yerel geliştirme</span><span class="sxs-lookup"><span data-stu-id="9b05a-149">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
 <span data-ttu-id="9b05a-150">Bu adım, uygulamanızı yerel geliştirme STS'si etkinleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="9b05a-150">This step describes how to enable Local Development STS in your application.</span></span> <span data-ttu-id="9b05a-151">Yerel geliştirme STS'si kimlik ve erişim uzantısı için Visual Studio aracılığıyla etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9b05a-151">Local Development STS is enabled by using the Identity and Access extension for Visual Studio.</span></span>  
  
### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a><span data-ttu-id="9b05a-152">ASP.NET uygulamanızı yerel geliştirme STS'si etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="9b05a-152">To enable Local Development STS in your ASP.NET application</span></span>  
  
1. <span data-ttu-id="9b05a-153">Visual Studio'da sağ **TestApp** altındaki proje **Çözüm Gezgini**, ardından **kimlik ve erişim**.</span><span class="sxs-lookup"><span data-stu-id="9b05a-153">In Visual Studio, right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
2. <span data-ttu-id="9b05a-154">**Kimlik ve erişim** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9b05a-154">The **Identity and Access** window appears.</span></span> <span data-ttu-id="9b05a-155">Altında **sağlayıcıları**seçin **uygulamanızı yerel geliştirme STS'si ile Test**, ardından **Uygula**.</span><span class="sxs-lookup"><span data-stu-id="9b05a-155">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a><span data-ttu-id="9b05a-156">4\. adım: ASP.NET uygulamanız oturum durumu görüntülemek için değiştirin</span><span class="sxs-lookup"><span data-stu-id="9b05a-156">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
 <span data-ttu-id="9b05a-157">Bu adım, ASP.NET uygulamanızı, geçerli kullanıcının oturum açtığı olmadığını dinamik olarak görüntülenecek değiştirmeniz açıklar.</span><span class="sxs-lookup"><span data-stu-id="9b05a-157">This step describes how to modify your ASP.NET application to dynamically display whether the current user is signed in.</span></span> <span data-ttu-id="9b05a-158">WIF, STS sağlayıcınız yapılandırıldıktan sonra gelen talepleri işler.</span><span class="sxs-lookup"><span data-stu-id="9b05a-158">Once your STS provider has been configured, WIF handles the incoming claims.</span></span> <span data-ttu-id="9b05a-159">Şimdi, kimlik doğrulaması sonucu görüntülemek için uygulamanızın kod yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b05a-159">Now you need to configure your application’s code to display the result of the authentication.</span></span>  
  
### <a name="to-display-sign-in-status"></a><span data-ttu-id="9b05a-160">Oturum durumunu görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="9b05a-160">To display sign in status</span></span>  
  
1. <span data-ttu-id="9b05a-161">Visual Studio'da açın **Default.aspx** altında dosya **TestApp** proje.</span><span class="sxs-lookup"><span data-stu-id="9b05a-161">In Visual Studio, open the **Default.aspx** file under the **TestApp** project.</span></span>  
  
2. <span data-ttu-id="9b05a-162">Mevcut biçimlendirmeyi Değiştir **Default.aspx** aşağıdaki işaretlemeyle dosyası:</span><span class="sxs-lookup"><span data-stu-id="9b05a-162">Replace the existing markup in the **Default.aspx** file with the following markup:</span></span>  
  
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
  
3. <span data-ttu-id="9b05a-163">Kaydet **Default.aspx**ve ardından adlı dosyanın arkasındaki kodunu açın **Default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="9b05a-163">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b05a-164">**Default.aspx.cs** altındaki gizlenebilir **Default.aspx** Çözüm Gezgini'nde.</span><span class="sxs-lookup"><span data-stu-id="9b05a-164">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="9b05a-165">Varsa **Default.aspx.cs** görünür durumda değilse genişletin **Default.aspx** yanında üçgeni tıklayarak.</span><span class="sxs-lookup"><span data-stu-id="9b05a-165">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
4. <span data-ttu-id="9b05a-166">Varolan kodda değiştirin **Default.aspx.cs** aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="9b05a-166">Replace the existing code in **Default.aspx.cs** with the following code:</span></span>  
  
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
  
5. <span data-ttu-id="9b05a-167">Kaydet **Default.aspx.cs**ve uygulamayı derleyin.</span><span class="sxs-lookup"><span data-stu-id="9b05a-167">Save **Default.aspx.cs**, and build the application.</span></span>  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a><span data-ttu-id="9b05a-168">5\. adım – WIF ve ASP.NET uygulamanız arasındaki tümleştirme testi</span><span class="sxs-lookup"><span data-stu-id="9b05a-168">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
 <span data-ttu-id="9b05a-169">Bu adımda, WIF ve ASP.NET uygulamanızı arasında tümleştirmeyi nasıl sınayıp doğrulayabileceğiniz açıklanır.</span><span class="sxs-lookup"><span data-stu-id="9b05a-169">This step describes how you can test the integration between WIF and your ASP.NET application.</span></span>  
  
### <a name="to-test-the-integration-between-wif-and-aspnet"></a><span data-ttu-id="9b05a-170">WIF ve ASP.NET arasındaki tümleştirmeden test etmek için</span><span class="sxs-lookup"><span data-stu-id="9b05a-170">To test the integration between WIF and ASP.NET</span></span>  
  
1. <span data-ttu-id="9b05a-171">Visual Studio'da **F5** uygulamanızı hata ayıklama başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="9b05a-171">In Visual Studio, press **F5** to start debugging your application.</span></span> <span data-ttu-id="9b05a-172">Hiçbir hata bulunamazsa, yeni bir tarayıcı penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="9b05a-172">If no errors are found, a new browser window will open.</span></span>  
  
2. <span data-ttu-id="9b05a-173">Tarayıcı sessizce isteğiniz STS'ye yönlendirir ve ardından Default.aspx sayfasında açılır fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b05a-173">You may notice that the browser silently redirects your request to the STS, and then opens the Default.aspx page.</span></span> <span data-ttu-id="9b05a-174">WIF düzgün şekilde yapılandırılmışsa, aşağıdaki metni görüntüle sitesini görmeniz gerekir: **"Oturum"** .</span><span class="sxs-lookup"><span data-stu-id="9b05a-174">If WIF is properly configured, you should see the site display the following text: **"You are signed in"**.</span></span>
