---
title: 'Nasıl yapılır: WCF Web hizmeti uygulaması için WIF etkinleştirme'
ms.date: 03/30/2017
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 71897299d68c2f0e43def8e70730ea456d6e9e24
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190260"
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a><span data-ttu-id="62e7f-102">Nasıl yapılır: WCF Web hizmeti uygulaması için WIF etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="62e7f-102">How To: Enable WIF for a WCF Web Service Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="62e7f-103">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="62e7f-103">Applies To</span></span>  
  
-   <span data-ttu-id="62e7f-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="62e7f-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="62e7f-105">Microsoft® Windows® Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="62e7f-105">Microsoft® Windows® Communication Foundation (WCF)</span></span>  
  
## <a name="summary"></a><span data-ttu-id="62e7f-106">Özet</span><span class="sxs-lookup"><span data-stu-id="62e7f-106">Summary</span></span>  
 <span data-ttu-id="62e7f-107">Bu 'Nasıl Yapılır' makalesi, bir WCF web hizmetinde WIF'yi etkinleştirmeye yönelik adım adım ayrıntılı yordamları sağlar.</span><span class="sxs-lookup"><span data-stu-id="62e7f-107">This How-To provides detailed step-by-step procedures for enabling WIF in a WCF web service.</span></span> <span data-ttu-id="62e7f-108">Ayrıca, uygulama çalıştırıldığında web hizmetinin beyanları doğru olarak sunduğunu doğrulamak amacıyla uygulamanın nasıl test edileceğine ilişkin yönergeler verilir.</span><span class="sxs-lookup"><span data-stu-id="62e7f-108">It also provides instructions for how to test the application to verify that the web service is correctly presenting claims when the application is run.</span></span> <span data-ttu-id="62e7f-109">Bu 'Nasıl Yapılır' konusunda bir Güvenlik Belirteci Hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bunun yerine Kimlik ve Erişim aracı ile birlikte gelen Geliştirme STS'si kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62e7f-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="62e7f-110">Geliştirme STS'si gerçek kimlik doğrulaması yapmaz ve yalnızca test amaçlarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="62e7f-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="62e7f-111">Bu 'Nasıl Yapılır' konusunu tamamlamak için Kimlik ve Erişim aracını yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="62e7f-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="62e7f-112">Şu konumdan indirilebilir: [kimlik ve erişim aracı](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="62e7f-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="62e7f-113">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="62e7f-113">Contents</span></span>  
  
-   <span data-ttu-id="62e7f-114">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="62e7f-114">Objectives</span></span>  
  
-   <span data-ttu-id="62e7f-115">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="62e7f-115">Overview</span></span>  
  
-   <span data-ttu-id="62e7f-116">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="62e7f-116">Summary of Steps</span></span>  
  
-   <span data-ttu-id="62e7f-117">1. Adım – Basit bir WCF Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="62e7f-117">Step 1 – Create a Simple WCF Service</span></span>  
  
-   <span data-ttu-id="62e7f-118">2. Adım – WCF Hizmeti İçin Bir İstemci Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="62e7f-118">Step 2 – Create a Client Application for the WCF Service</span></span>  
  
-   <span data-ttu-id="62e7f-119">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="62e7f-119">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="62e7f-120">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="62e7f-120">Objectives</span></span>  
  
-   <span data-ttu-id="62e7f-121">Verilen belirteçleri gerektiren bir WCF hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="62e7f-121">Create a WCF service that requires issued tokens</span></span>  
  
-   <span data-ttu-id="62e7f-122">STS'den bir belirteç isteyen ve bunu WCF hizmetine aktaran bir WCF istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="62e7f-122">Create a WCF client that requests a token from an STS and passes it to the WCF service</span></span>  
  
## <a name="overview"></a><span data-ttu-id="62e7f-123">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="62e7f-123">Overview</span></span>  
 <span data-ttu-id="62e7f-124">Bu 'Nasıl Yapılır' makalesi, bir geliştiricinin WCF hizmetleri geliştirirken federasyon kimlik doğrulamasını nasıl kullanabileceğini göstermeyi amaçlar.</span><span class="sxs-lookup"><span data-stu-id="62e7f-124">This How-To is intended to demonstrate how a developer can use federated authentication when developing WCF services.</span></span> <span data-ttu-id="62e7f-125">WCF hizmetlerinde federasyon kullanmanın avantajlarından bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="62e7f-125">Some of the benefits of using federation in WCF services include:</span></span>  
  
1.  <span data-ttu-id="62e7f-126">Kimlik doğrulamasını WCF hizmet kodunun dışında düzenleme</span><span class="sxs-lookup"><span data-stu-id="62e7f-126">Factoring authentication logic out of WCF service code</span></span>  
  
2.  <span data-ttu-id="62e7f-127">Varolan kimlik yönetimi çözümlerini yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="62e7f-127">Re-using existing identity management solutions</span></span>  
  
3.  <span data-ttu-id="62e7f-128">Diğer kimlik çözümleri ile birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="62e7f-128">Interoperability with other identity solutions</span></span>  
  
4.  <span data-ttu-id="62e7f-129">Esneklik ve gelecekteki değişikliklere uyum kolaylığı</span><span class="sxs-lookup"><span data-stu-id="62e7f-129">Flexibility and resilience to future changes</span></span>  
  
 <span data-ttu-id="62e7f-130">WIF ve ilişkili Kimlik ve Erişim aracı, aşağıdaki adımlarda da gösterildiği üzere, federasyon kimlik doğrulamasını kullanarak WCF hizmeti geliştirmeyi ve test etmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="62e7f-130">WIF and the associated Identity and Access tool make it easier to develop and test a WCF service using federated authentication, as the following steps demonstrate.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="62e7f-131">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="62e7f-131">Summary of Steps</span></span>  
  
-   <span data-ttu-id="62e7f-132">1. Adım – Basit bir WCF Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="62e7f-132">Step 1 – Create a Simple WCF Service</span></span>  
  
-   <span data-ttu-id="62e7f-133">2. Adım – WCF Hizmeti İçin Bir İstemci Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="62e7f-133">Step 2 – Create a Client Application for the WCF Service</span></span>  
  
-   <span data-ttu-id="62e7f-134">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="62e7f-134">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-wcf-service"></a><span data-ttu-id="62e7f-135">1. Adım – Basit bir WCF Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="62e7f-135">Step 1 – Create a Simple WCF Service</span></span>  
 <span data-ttu-id="62e7f-136">Bu adımda, Kimlik ve Erişim aracının içindeki Geliştirme STS'sini kullanan yeni bir WCF hizmeti oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="62e7f-136">In this step, you will create a new WCF service that uses the Development STS that is included with the Identity and Access tool.</span></span>  
  
#### <a name="to-create-a-simple-wcf-service"></a><span data-ttu-id="62e7f-137">Basit bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="62e7f-137">To create a simple WCF service</span></span>  
  
1.  <span data-ttu-id="62e7f-138">Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.</span><span class="sxs-lookup"><span data-stu-id="62e7f-138">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="62e7f-139">Visual Studio'da **dosya**, tıklayın **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-139">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="62e7f-140">İçinde **yeni proje** penceresinde tıklayın **WCF hizmeti uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-140">In the **New Project** window, click **WCF Service Application**.</span></span>  
  
4.  <span data-ttu-id="62e7f-141">İçinde **adı**, girin `TestService` basın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-141">In **Name**, enter `TestService` and press **OK**.</span></span>  
  
5.  <span data-ttu-id="62e7f-142">Sağ **TestService** altındaki proje **Çözüm Gezgini**, ardından **kimlik ve erişim**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-142">Right-click the **TestService** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
6.  <span data-ttu-id="62e7f-143">**Kimlik ve erişim** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="62e7f-143">The **Identity and Access** window appears.</span></span> <span data-ttu-id="62e7f-144">Altında **sağlayıcıları**seçin **uygulamanızı yerel geliştirme STS'si ile Test**, ardından **Uygula**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-144">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span> <span data-ttu-id="62e7f-145">Kimlik ve erişim aracı, hizmeti WIF kullanacak ve kimlik doğrulaması için yerel geliştirme sts'sine yapılandırır (**LocalSTS**) yapılandırma öğelerine ekleyerek *Web.config* dosya.</span><span class="sxs-lookup"><span data-stu-id="62e7f-145">The Identity and Access Tool configures the service to use WIF and to outsource authentication to the local development STS (**LocalSTS**) by adding configuration elements to the *Web.config* file.</span></span>  
  
7.  <span data-ttu-id="62e7f-146">İçinde *gt;service1.svc.cs* ekleyin bir `using` yönergesi **System.Security.Claims** ad alanı ve varolan kodu şu kodla değiştirip dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="62e7f-146">In the *Service1.svc.cs* file, add a `using` directive for the **System.Security.Claims** namespace and replace the existing code with the following, then save the file:</span></span>  
  
    ```csharp  
    public class Service1 : IService1  
    {  
        public string ComputeResponse(string input)  
        {  
            // Get the caller's identity from ClaimsPrincipal.Current  
            ClaimsPrincipal claimsPrincipal = OperationContext.Current.ClaimsPrincipal;  
  
            // Start generating the output  
            StringBuilder builder = new StringBuilder();  
            builder.AppendLine("Computed by ClaimsAwareWebService");  
            builder.AppendLine("Input received from client:" + input);  
  
            if (claimsPrincipal != null)  
            {  
                // Display the claims from the caller. Do not use this code in a production application.  
                ClaimsIdentity identity = claimsPrincipal.Identity as ClaimsIdentity;  
                builder.AppendLine("Client Name:" + identity.Name);  
                builder.AppendLine("IsAuthenticated:" + identity.IsAuthenticated);  
                builder.AppendLine("The service received the following issued claims of the client:");  
  
                // Iterate over the caller’s claims and append to the output  
                foreach (Claim claim in claimsPrincipal.Claims)  
                {  
                    builder.AppendLine("ClaimType :" + claim.Type + "   ClaimValue:" + claim.Value);  
                }  
            }  
  
            return builder.ToString();  
        }  
    }  
    ```  
  
     <span data-ttu-id="62e7f-147">`ComputeResponse` Yöntemi tarafından verilen çeşitli beyanların özelliklerini görüntüler **LocalSTS**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-147">The `ComputeResponse` method displays the properties of various claims that are issued by **LocalSTS**.</span></span>  
  
8.  <span data-ttu-id="62e7f-148">İçinde *Iservice1.cs* dosya, var olan kodu aşağıdakiyle değiştirin ve ardından dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="62e7f-148">In the *IService1.cs* file, replace the existing code with the following, then save the file:</span></span>  
  
    ```csharp  
    [ServiceContract]  
    public interface IService1  
    {  
        [OperationContract]  
        string ComputeResponse(string input);  
    }  
    ```  
  
9. <span data-ttu-id="62e7f-149">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="62e7f-149">Build the project.</span></span>  
  
10. <span data-ttu-id="62e7f-150">Tuşuna **Ctrl-F5** hata ayıklayıcıyı başlatmadan hizmeti çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="62e7f-150">Press **Ctrl-F5** to run the service without starting the debugger.</span></span> <span data-ttu-id="62e7f-151">Hizmet için bir Web sayfası açmak ve doğrulayabilirsiniz **LocalSTS** bildirim alanında (sistem tepsisi) bakarak çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="62e7f-151">A Web page should open for the service and you can verify that **LocalSTS** is running by looking in the notification area (system tray).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="62e7f-152">Her ikisi de **TestService** ve **LocalSTS** sonraki adımda istemci uygulamasına hizmet başvurusunu eklediğinizde, çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="62e7f-152">Both **TestService** and **LocalSTS** must be running when you add the service reference to the client application in the next step.</span></span>  
  
## <a name="step-2--create-a-client-application-for-the-wcf-service"></a><span data-ttu-id="62e7f-153">2. Adım – WCF Hizmeti İçin Bir İstemci Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="62e7f-153">Step 2 – Create a Client Application for the WCF Service</span></span>  
 <span data-ttu-id="62e7f-154">Bu adımda, önceki adımda oluşturduğunuz WCF hizmeti ile kimlik doğrulamak için Geliştirme STS'sini kullanan bir konsol uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="62e7f-154">In this step, you will create a console application that uses the Development STS to authenticate with the WCF service you created in the previous step.</span></span>  
  
#### <a name="to-create-a-client-application"></a><span data-ttu-id="62e7f-155">İstemci uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="62e7f-155">To create a client application</span></span>  
  
1.  <span data-ttu-id="62e7f-156">Visual Studio'da çözüme sağ tıklayın, **Ekle**ve ardından **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-156">In Visual Studio, right-click on the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="62e7f-157">İçinde **Yeni Proje Ekle** penceresinde **konsol uygulaması** gelen **Visual C#** şablonları listesinde, girin `Client`ve tuşuna **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-157">In the **Add New Project** window, select **Console Application** from the **Visual C#** templates list, enter `Client`, and then press **OK**.</span></span> <span data-ttu-id="62e7f-158">Yeni proje, çözüm klasörünüzde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="62e7f-158">The new project will be created in your solution folder.</span></span>  
  
3.  <span data-ttu-id="62e7f-159">Sağ **başvuruları** altında **istemci** proje ve ardından **hizmet Başvurusu Ekle**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-159">Right-click on **References** under the **Client** project, and then click **Add Service Reference**.</span></span>  
  
4.  <span data-ttu-id="62e7f-160">İçinde **hizmet Başvurusu Ekle** penceresinde, aşağı açılan oka tıklayın **bulma** düğmesini tıklatın ve tıklatın **çözüm içerisindeki Hizmetler**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-160">In the **Add Service Reference** window, click the drop-down arrow on the **Discover** button and click **Services in Solution**.</span></span> <span data-ttu-id="62e7f-161">**Adresi** daha önce oluşturduğunuz WCF Hizmeti ile otomatik olarak doldurulur ve **Namespace** ayarlanacak **ServiceReference1**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-161">The **Address** will automatically populate with the WCF service you created earlier, and the **Namespace** will be set to **ServiceReference1**.</span></span> <span data-ttu-id="62e7f-162">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="62e7f-162">Click **OK**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="62e7f-163">Her ikisi de **TestService** ve **LocalSTS** istemciye hizmet başvurusunu eklediğinizde, çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="62e7f-163">Both **TestService** and **LocalSTS** must be running when you add the service reference to the client.</span></span>  
  
5.  <span data-ttu-id="62e7f-164">Visual Studio, WCF hizmeti için proxy sınıfları üretecek ve gerekli tüm başvuru bilgilerini ekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="62e7f-164">Visual Studio will generate proxy classes for the WCF service, and add all of the necessary reference information.</span></span> <span data-ttu-id="62e7f-165">Öğeleri ekleyecektir *App.config* hizmeti ile kimlik doğrulaması STS gelen bir belirteç alacak şekilde istemciyi yapılandırmak için bir dosya.</span><span class="sxs-lookup"><span data-stu-id="62e7f-165">It will also add elements to the *App.config* file to configure the client to get a token from the STS to authenticate with the service.</span></span> <span data-ttu-id="62e7f-166">Bu işlem tamamlandığında **Program.cs** dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="62e7f-166">When this process is finished, the **Program.cs** file will open.</span></span> <span data-ttu-id="62e7f-167">Ekleme bir `using` yönergesi **System.ServiceModel** için başka bir **gt;Client.servicereference1**, değiştirin **ana** şu kod ile ardından yöntemi dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="62e7f-167">Add a `using` directive for **System.ServiceModel** and another for **Client.ServiceReference1**, replace the **Main** method with the following code, then save the file:</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        // Create the client for the service  
        Service1Client client = new Service1Client();  
        Console.WriteLine("-------------WCF Client Application--------------\n");  
  
        while (!ShouldQuitApplication())  
        {  
            try  
            {  
                Console.WriteLine(client.ComputeResponse("Hello World"));  
            }  
            catch (CommunicationException e)  
            {  
                Console.WriteLine(e.Message);  
                Console.WriteLine(e.StackTrace);  
                Exception ex = e.InnerException;  
                while (ex != null)  
                {  
                    Console.WriteLine("===========================");  
                    Console.WriteLine(ex.Message);  
                    Console.WriteLine(ex.StackTrace);  
                    ex = ex.InnerException;  
                }  
            }  
            catch (TimeoutException)  
            {  
                Console.WriteLine("Timed out...");  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("An unexpected exception occurred.");  
                Console.WriteLine(e.StackTrace);  
            }  
        }  
  
        client.Close();  
  
        if (client != null)  
        {  
            client.Abort();  
        }  
    }  
  
    static bool ShouldQuitApplication()  
    {  
        Console.WriteLine("---------------------------------------------------------------------");  
        Console.WriteLine("Press Enter key to invoke service, any other key to quit application:");  
        Console.WriteLine("----------------------------------------------------------------------");  
  
        ConsoleKeyInfo keyInfo = Console.ReadKey();  
        if (keyInfo.Key == ConsoleKey.Enter)  
            return false;  
        return true;  
    }  
    ```  
  
6.  <span data-ttu-id="62e7f-168">Açık *App.config* altına ilk alt öğe olarak aşağıdaki XML'i ekleyin ve dosya `<system.serviceModel>` öğesi, ardından dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="62e7f-168">Open the *App.config* file and add the following XML as the first child element under the `<system.serviceModel>` element, then save the file:</span></span>  
  
    ```xml  
    <behaviors>  
       <endpointBehaviors>  
         <behavior>  
           <clientCredentials>  
             <serviceCertificate>  
               <authentication certificateValidationMode="None"/>  
             </serviceCertificate>  
           </clientCredentials>  
         </behavior>  
       </endpointBehaviors>  
     </behaviors>  
    ```  
  
     <span data-ttu-id="62e7f-169">Bu, sertifika doğrulamayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="62e7f-169">This disables certificate validation.</span></span>  
  
7.  <span data-ttu-id="62e7f-170">Sağ **TestService** çözüm ve tıklayarak **başlangıç projelerini Ayarla**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-170">Right-click the **TestService** solution and click on **Set StartUp Projects**.</span></span> <span data-ttu-id="62e7f-171">**Başlangıç projesi** özellik sayfası açılır.</span><span class="sxs-lookup"><span data-stu-id="62e7f-171">The **Startup Project** property page opens.</span></span> <span data-ttu-id="62e7f-172">İçinde **başlangıç projesi** özellik sayfasında, **birden fazla başlangıç projesi** tıklayın ardından **eylem** alan her bir proje ve seçin için **Başlat** aşağı açılan menüden.</span><span class="sxs-lookup"><span data-stu-id="62e7f-172">In the **Startup Project** property page, select **Multiple startup projects** then click in the **Action** field for each project and select **Start** from the drop-down menu.</span></span> <span data-ttu-id="62e7f-173">Tıklayın **Tamam** ayarları kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="62e7f-173">Click **OK** to save the settings.</span></span>  
  
8.  <span data-ttu-id="62e7f-174">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="62e7f-174">Build the solution.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="62e7f-175">3. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="62e7f-175">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="62e7f-176">Bu adımda, WIF özelliği etkinleştirilmiş WCF uygulamanızı test edecek ve beyanların sunulduğunu doğrulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="62e7f-176">In this step you will test your WIF-enabled WCF application and verify that claims are presented.</span></span>  
  
#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a><span data-ttu-id="62e7f-177">WIF özelliği etkinleştirilmiş WCF uygulamanızı beyanlar açısından test etmek için</span><span class="sxs-lookup"><span data-stu-id="62e7f-177">To test your WIF-enabled WCF application for claims</span></span>  
  
1.  <span data-ttu-id="62e7f-178">Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="62e7f-178">Press **F5** to build and run the application.</span></span> <span data-ttu-id="62e7f-179">Bir konsol penceresi ve şu metnin sunulacaktır: **uygulamadan çıkmak içinse diğer herhangi bir tuşa hizmetini çağırmak için anahtar Enter tuşuna basın:**</span><span class="sxs-lookup"><span data-stu-id="62e7f-179">You should be presented with a console window, and the following text: **Press Enter key to invoke service, any other key to quit application:**</span></span>  
  
2.  <span data-ttu-id="62e7f-180">Tuşuna **Enter**, ve konsolda şu beyan bilgilerinin görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="62e7f-180">Press **Enter**, and the following claims information should appear in the console:</span></span>  
  
    ```  
    Computed by Service1  
    Input received from client: Hello World  
    Client Name: Terry  
    IsAuthenticated: True  
    The service received the following issued claims of the client:  
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name    ClaimValue:Terry  
    ClaimType :http://schema.xmlsoap.org/ws/2005/05/identity/claims/surname    ClaimValue:Adams  
    ClaimType :http://schemas.microsoft.com/ws/2008/06/identity/claims/role    ClaimValue:developer  
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress    ClaimValue:terry@contoso.com  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="62e7f-181">Her ikisi de **TestService** ve **LocalSTS** basmadan önce çalıştırmalıdır **Enter**.</span><span class="sxs-lookup"><span data-stu-id="62e7f-181">Both **TestService** and **LocalSTS** must be running before you press **Enter**.</span></span> <span data-ttu-id="62e7f-182">Hizmet için bir Web sayfası açmak ve doğrulayabilirsiniz **LocalSTS** bildirim alanında (sistem tepsisi) bakarak çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="62e7f-182">A Web page should open for the service and you can verify that **LocalSTS** is running by looking in the notification area (system tray).</span></span>  
  
3.  <span data-ttu-id="62e7f-183">Bu beyanlar konsolda görünüyorsa, WCF hizmetinden beyanları görüntülemek üzere STS ile başarılı bir şekilde kimlik doğrulamışsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="62e7f-183">If these claims appear in the console, you have successfully authenticated with the STS to display claims from the WCF service.</span></span>
