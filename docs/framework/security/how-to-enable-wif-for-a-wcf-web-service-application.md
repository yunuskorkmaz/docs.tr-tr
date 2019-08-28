---
title: 'Nasıl yapılır: WCF Web Hizmeti Uygulaması için WIF Etkinleştirme'
ms.date: 03/30/2017
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
author: BrucePerlerMS
ms.openlocfilehash: b9fa1f815a962adc0b3c91177021788734b92bb6
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041451"
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a><span data-ttu-id="d9d23-102">Nasıl yapılır: WCF Web Hizmeti Uygulaması için WIF Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="d9d23-102">How To: Enable WIF for a WCF Web Service Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="d9d23-103">Uygulanan Öğe</span><span class="sxs-lookup"><span data-stu-id="d9d23-103">Applies To</span></span>

- <span data-ttu-id="d9d23-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="d9d23-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="d9d23-105">Microsoft® Windows® Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="d9d23-105">Microsoft® Windows® Communication Foundation (WCF)</span></span>

## <a name="summary"></a><span data-ttu-id="d9d23-106">Özet</span><span class="sxs-lookup"><span data-stu-id="d9d23-106">Summary</span></span>

<span data-ttu-id="d9d23-107">Bu 'Nasıl Yapılır' makalesi, bir WCF web hizmetinde WIF'yi etkinleştirmeye yönelik adım adım ayrıntılı yordamları sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9d23-107">This How-To provides detailed step-by-step procedures for enabling WIF in a WCF web service.</span></span> <span data-ttu-id="d9d23-108">Ayrıca, uygulama çalıştırıldığında web hizmetinin beyanları doğru olarak sunduğunu doğrulamak amacıyla uygulamanın nasıl test edileceğine ilişkin yönergeler verilir.</span><span class="sxs-lookup"><span data-stu-id="d9d23-108">It also provides instructions for how to test the application to verify that the web service is correctly presenting claims when the application is run.</span></span> <span data-ttu-id="d9d23-109">Bu 'Nasıl Yapılır' konusunda bir Güvenlik Belirteci Hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bunun yerine Kimlik ve Erişim aracı ile birlikte gelen Geliştirme STS'si kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d9d23-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="d9d23-110">Geliştirme STS'si gerçek kimlik doğrulaması yapmaz ve yalnızca test amaçlarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="d9d23-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="d9d23-111">Bu 'Nasıl Yapılır' konusunu tamamlamak için Kimlik ve Erişim aracını yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9d23-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="d9d23-112">Bu, aşağıdaki konumdan indirilebilir: [Kimlik ve erişim aracı](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="d9d23-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>

## <a name="contents"></a><span data-ttu-id="d9d23-113">İçindekiler</span><span class="sxs-lookup"><span data-stu-id="d9d23-113">Contents</span></span>

- <span data-ttu-id="d9d23-114">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="d9d23-114">Objectives</span></span>

- <span data-ttu-id="d9d23-115">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d9d23-115">Overview</span></span>

- <span data-ttu-id="d9d23-116">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="d9d23-116">Summary of Steps</span></span>

- <span data-ttu-id="d9d23-117">1\. Adım – Basit bir WCF Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9d23-117">Step 1 – Create a Simple WCF Service</span></span>

- <span data-ttu-id="d9d23-118">2\. Adım – WCF Hizmeti İçin Bir İstemci Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9d23-118">Step 2 – Create a Client Application for the WCF Service</span></span>

- <span data-ttu-id="d9d23-119">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="d9d23-119">Step 3 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="d9d23-120">Amaçlar</span><span class="sxs-lookup"><span data-stu-id="d9d23-120">Objectives</span></span>

- <span data-ttu-id="d9d23-121">Verilen belirteçleri gerektiren bir WCF hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9d23-121">Create a WCF service that requires issued tokens</span></span>

- <span data-ttu-id="d9d23-122">STS'den bir belirteç isteyen ve bunu WCF hizmetine aktaran bir WCF istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9d23-122">Create a WCF client that requests a token from an STS and passes it to the WCF service</span></span>

## <a name="overview"></a><span data-ttu-id="d9d23-123">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d9d23-123">Overview</span></span>

<span data-ttu-id="d9d23-124">Bu 'Nasıl Yapılır' makalesi, bir geliştiricinin WCF hizmetleri geliştirirken federasyon kimlik doğrulamasını nasıl kullanabileceğini göstermeyi amaçlar.</span><span class="sxs-lookup"><span data-stu-id="d9d23-124">This How-To is intended to demonstrate how a developer can use federated authentication when developing WCF services.</span></span> <span data-ttu-id="d9d23-125">WCF hizmetlerinde federasyon kullanmanın avantajlarından bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d9d23-125">Some of the benefits of using federation in WCF services include:</span></span>

1. <span data-ttu-id="d9d23-126">Kimlik doğrulamasını WCF hizmet kodunun dışında düzenleme</span><span class="sxs-lookup"><span data-stu-id="d9d23-126">Factoring authentication logic out of WCF service code</span></span>

2. <span data-ttu-id="d9d23-127">Varolan kimlik yönetimi çözümlerini yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="d9d23-127">Re-using existing identity management solutions</span></span>

3. <span data-ttu-id="d9d23-128">Diğer kimlik çözümleri ile birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="d9d23-128">Interoperability with other identity solutions</span></span>

4. <span data-ttu-id="d9d23-129">Esneklik ve gelecekteki değişikliklere uyum kolaylığı</span><span class="sxs-lookup"><span data-stu-id="d9d23-129">Flexibility and resilience to future changes</span></span>

<span data-ttu-id="d9d23-130">WIF ve ilişkili Kimlik ve Erişim aracı, aşağıdaki adımlarda da gösterildiği üzere, federasyon kimlik doğrulamasını kullanarak WCF hizmeti geliştirmeyi ve test etmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d9d23-130">WIF and the associated Identity and Access tool make it easier to develop and test a WCF service using federated authentication, as the following steps demonstrate.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="d9d23-131">Adımların Özeti</span><span class="sxs-lookup"><span data-stu-id="d9d23-131">Summary of Steps</span></span>

- <span data-ttu-id="d9d23-132">1\. Adım – Basit bir WCF Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9d23-132">Step 1 – Create a Simple WCF Service</span></span>

- <span data-ttu-id="d9d23-133">2\. Adım – WCF Hizmeti İçin Bir İstemci Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9d23-133">Step 2 – Create a Client Application for the WCF Service</span></span>

- <span data-ttu-id="d9d23-134">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="d9d23-134">Step 3 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-wcf-service"></a><span data-ttu-id="d9d23-135">1\. Adım – Basit bir WCF Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9d23-135">Step 1 – Create a Simple WCF Service</span></span>

<span data-ttu-id="d9d23-136">Bu adımda, Kimlik ve Erişim aracının içindeki Geliştirme STS'sini kullanan yeni bir WCF hizmeti oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d9d23-136">In this step, you will create a new WCF service that uses the Development STS that is included with the Identity and Access tool.</span></span>

#### <a name="to-create-a-simple-wcf-service"></a><span data-ttu-id="d9d23-137">Basit bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d9d23-137">To create a simple WCF service</span></span>

1. <span data-ttu-id="d9d23-138">Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.</span><span class="sxs-lookup"><span data-stu-id="d9d23-138">Start Visual Studio in elevated mode as administrator.</span></span>

2. <span data-ttu-id="d9d23-139">Visual Studio 'da **Dosya**' ya, **Yeni**' ye ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9d23-139">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="d9d23-140">**Yeni proje** penceresinde, **WCF hizmeti uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9d23-140">In the **New Project** window, click **WCF Service Application**.</span></span>

4. <span data-ttu-id="d9d23-141">**Ad**alanına girin `TestService` ve **Tamam**' a basın.</span><span class="sxs-lookup"><span data-stu-id="d9d23-141">In **Name**, enter `TestService` and press **OK**.</span></span>

5. <span data-ttu-id="d9d23-142">**Çözüm Gezgini**altında **TestService** projesine sağ tıklayın **ve ardından kimlik ve erişim**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d9d23-142">Right-click the **TestService** project under **Solution Explorer**, then select **Identity and Access**.</span></span>

6. <span data-ttu-id="d9d23-143">**Kimlik ve erişim** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d9d23-143">The **Identity and Access** window appears.</span></span> <span data-ttu-id="d9d23-144">**Sağlayıcılar**bölümünde, **yerel geliştirme sts 'Si Ile uygulamanızı test et**' i seçin ve **Uygula**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9d23-144">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span> <span data-ttu-id="d9d23-145">Kimlik ve erişim aracı, *Web. config* dosyasına yapılandırma öğeleri ekleyerek, hizmeti WIF ve yerel geliştirme sts 'ye (**LocalSTS**) dış kimlik doğrulaması yapmak üzere yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d9d23-145">The Identity and Access Tool configures the service to use WIF and to outsource authentication to the local development STS (**LocalSTS**) by adding configuration elements to the *Web.config* file.</span></span>

7. <span data-ttu-id="d9d23-146">*Service1.svc.cs* dosyasında, `using` **System. Security. Claim** ad alanı için bir yönerge ekleyin ve mevcut kodu aşağıdaki kodla değiştirin, ardından dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="d9d23-146">In the *Service1.svc.cs* file, add a `using` directive for the **System.Security.Claims** namespace and replace the existing code with the following, then save the file:</span></span>

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

    <span data-ttu-id="d9d23-147">Yöntemi `ComputeResponse` , **LocalSTS**tarafından verilen çeşitli taleplerin özelliklerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d9d23-147">The `ComputeResponse` method displays the properties of various claims that are issued by **LocalSTS**.</span></span>

8. <span data-ttu-id="d9d23-148">*IService1.cs* dosyasında, var olan kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="d9d23-148">In the *IService1.cs* file, replace the existing code with the following, then save the file:</span></span>

    ```csharp
    [ServiceContract]
    public interface IService1
    {
        [OperationContract]
        string ComputeResponse(string input);
    }
    ```

9. <span data-ttu-id="d9d23-149">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d9d23-149">Build the project.</span></span>

10. <span data-ttu-id="d9d23-150">Hata ayıklayıcıyı başlatmadan hizmeti çalıştırmak için **CTRL-F5** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="d9d23-150">Press **Ctrl-F5** to run the service without starting the debugger.</span></span> <span data-ttu-id="d9d23-151">Hizmet için bir Web sayfası açık olmalıdır ve bildirim alanına (sistem tepsisi) bakarak **LocalSTS** 'nin çalıştığını doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9d23-151">A Web page should open for the service and you can verify that **LocalSTS** is running by looking in the notification area (system tray).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d9d23-152">Bir sonraki adımda istemci uygulamasına hizmet başvurusunu eklediğinizde hem **TestService** hem de **LocalSTS** çalışıyor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9d23-152">Both **TestService** and **LocalSTS** must be running when you add the service reference to the client application in the next step.</span></span>

## <a name="step-2--create-a-client-application-for-the-wcf-service"></a><span data-ttu-id="d9d23-153">2\. Adım – WCF Hizmeti İçin Bir İstemci Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9d23-153">Step 2 – Create a Client Application for the WCF Service</span></span>

<span data-ttu-id="d9d23-154">Bu adımda, önceki adımda oluşturduğunuz WCF hizmeti ile kimlik doğrulamak için Geliştirme STS'sini kullanan bir konsol uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d9d23-154">In this step, you will create a console application that uses the Development STS to authenticate with the WCF service you created in the previous step.</span></span>

#### <a name="to-create-a-client-application"></a><span data-ttu-id="d9d23-155">İstemci uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d9d23-155">To create a client application</span></span>

1. <span data-ttu-id="d9d23-156">Visual Studio 'da çözüme sağ tıklayın, **Ekle**' ye tıklayın ve ardından **Yeni proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9d23-156">In Visual Studio, right-click on the solution, click **Add**, and then click **New Project**.</span></span>

2. <span data-ttu-id="d9d23-157">**Yeni Proje Ekle** penceresinde,  **C# görsel** şablonlar listesinden **konsol uygulaması** ' nı seçin, yazın `Client`ve ardından **Tamam**' a basın.</span><span class="sxs-lookup"><span data-stu-id="d9d23-157">In the **Add New Project** window, select **Console Application** from the **Visual C#** templates list, enter `Client`, and then press **OK**.</span></span> <span data-ttu-id="d9d23-158">Yeni proje, çözüm klasörünüzde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d9d23-158">The new project will be created in your solution folder.</span></span>

3. <span data-ttu-id="d9d23-159">**İstemci** projesi altındaki **Başvurular** ' a sağ tıklayın ve ardından **hizmet başvurusu Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9d23-159">Right-click on **References** under the **Client** project, and then click **Add Service Reference**.</span></span>

4. <span data-ttu-id="d9d23-160">**Hizmet başvurusu Ekle** penceresinde **bul** düğmesinin yanındaki açılan oka tıklayın ve **çözümdeki hizmetler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9d23-160">In the **Add Service Reference** window, click the drop-down arrow on the **Discover** button and click **Services in Solution**.</span></span> <span data-ttu-id="d9d23-161">**Adres** , daha önce oluşturduğunuz WCF hizmeti ile otomatik olarak doldurulur ve **ad alanı** **ServiceReference1**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d9d23-161">The **Address** will automatically populate with the WCF service you created earlier, and the **Namespace** will be set to **ServiceReference1**.</span></span> <span data-ttu-id="d9d23-162">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d9d23-162">Click **OK**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d9d23-163">İstemciye hizmet başvurusunu eklediğinizde hem **TestService** hem de **LocalSTS** çalışıyor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9d23-163">Both **TestService** and **LocalSTS** must be running when you add the service reference to the client.</span></span>

5. <span data-ttu-id="d9d23-164">Visual Studio, WCF hizmeti için proxy sınıfları üretecek ve gerekli tüm başvuru bilgilerini ekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="d9d23-164">Visual Studio will generate proxy classes for the WCF service, and add all of the necessary reference information.</span></span> <span data-ttu-id="d9d23-165">Ayrıca, istemciyi hizmette kimlik doğrulaması yapmak üzere STS 'den bir belirteç alacak şekilde yapılandırmak için *app. config* dosyasına öğe ekler.</span><span class="sxs-lookup"><span data-stu-id="d9d23-165">It will also add elements to the *App.config* file to configure the client to get a token from the STS to authenticate with the service.</span></span> <span data-ttu-id="d9d23-166">Bu işlem tamamlandığında, **program.cs** dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="d9d23-166">When this process is finished, the **Program.cs** file will open.</span></span> <span data-ttu-id="d9d23-167">`using` **System. ServiceModel** ve **Client. ServiceReference1**için bir yönerge ekleyin, **Main** metodunu aşağıdaki kodla değiştirin, sonra dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="d9d23-167">Add a `using` directive for **System.ServiceModel** and another for **Client.ServiceReference1**, replace the **Main** method with the following code, then save the file:</span></span>

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

6. <span data-ttu-id="d9d23-168">*App. config* dosyasını açın ve aşağıdaki XML `<system.serviceModel>` öğesini öğesinin altındaki ilk alt öğe olarak ekleyin, sonra dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="d9d23-168">Open the *App.config* file and add the following XML as the first child element under the `<system.serviceModel>` element, then save the file:</span></span>

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

    <span data-ttu-id="d9d23-169">Bu, sertifika doğrulamayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="d9d23-169">This disables certificate validation.</span></span>

7. <span data-ttu-id="d9d23-170">**TestService** çözümüne sağ tıklayın ve **Başlangıç projelerini ayarla**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9d23-170">Right-click the **TestService** solution and click on **Set StartUp Projects**.</span></span> <span data-ttu-id="d9d23-171">**Başlangıç projesi** Özellik sayfası açılır.</span><span class="sxs-lookup"><span data-stu-id="d9d23-171">The **Startup Project** property page opens.</span></span> <span data-ttu-id="d9d23-172">**Başlangıç projesi** Özellik sayfasında, **birden fazla başlangıç** projesi ' ni seçin ve ardından her proje için **eylem** alanına tıklayın ve açılan menüden **Başlat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d9d23-172">In the **Startup Project** property page, select **Multiple startup projects** then click in the **Action** field for each project and select **Start** from the drop-down menu.</span></span> <span data-ttu-id="d9d23-173">Ayarları kaydetmek için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d9d23-173">Click **OK** to save the settings.</span></span>

8. <span data-ttu-id="d9d23-174">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d9d23-174">Build the solution.</span></span>

## <a name="step-3--test-your-solution"></a><span data-ttu-id="d9d23-175">3\. Adım – Çözümünüzü Test Etme</span><span class="sxs-lookup"><span data-stu-id="d9d23-175">Step 3 – Test Your Solution</span></span>

<span data-ttu-id="d9d23-176">Bu adımda, WIF özelliği etkinleştirilmiş WCF uygulamanızı test edecek ve beyanların sunulduğunu doğrulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d9d23-176">In this step you will test your WIF-enabled WCF application and verify that claims are presented.</span></span>

#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a><span data-ttu-id="d9d23-177">WIF özelliği etkinleştirilmiş WCF uygulamanızı beyanlar açısından test etmek için</span><span class="sxs-lookup"><span data-stu-id="d9d23-177">To test your WIF-enabled WCF application for claims</span></span>

1. <span data-ttu-id="d9d23-178">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d9d23-178">Press **F5** to build and run the application.</span></span> <span data-ttu-id="d9d23-179">Bir konsol penceresi ve aşağıdaki metinle birlikte sunulmalısınız: **Hizmeti çağırmak için ENTER tuşuna basın, uygulamadan çıkmak için başka herhangi bir anahtar:**</span><span class="sxs-lookup"><span data-stu-id="d9d23-179">You should be presented with a console window, and the following text: **Press Enter key to invoke service, any other key to quit application:**</span></span>

2. <span data-ttu-id="d9d23-180">**ENTER**tuşuna basın ve aşağıdaki talep bilgilerinin konsolunda görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="d9d23-180">Press **Enter**, and the following claims information should appear in the console:</span></span>

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
    > <span data-ttu-id="d9d23-181">**ENTER**tuşuna basarak, hem **TestService** hem de **LocalSTS** çalışıyor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9d23-181">Both **TestService** and **LocalSTS** must be running before you press **Enter**.</span></span> <span data-ttu-id="d9d23-182">Hizmet için bir Web sayfası açık olmalıdır ve bildirim alanına (sistem tepsisi) bakarak **LocalSTS** 'nin çalıştığını doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9d23-182">A Web page should open for the service and you can verify that **LocalSTS** is running by looking in the notification area (system tray).</span></span>

3. <span data-ttu-id="d9d23-183">Bu beyanlar konsolda görünüyorsa, WCF hizmetinden beyanları görüntülemek üzere STS ile başarılı bir şekilde kimlik doğrulamışsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="d9d23-183">If these claims appear in the console, you have successfully authenticated with the STS to display claims from the WCF service.</span></span>
