---
description: 'Daha fazla bilgi edinin: Federasyon örneği'
title: Federasyon Örneği
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: a85a290988b6cbb4b30a1098f3558ec34ead1d50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704088"
---
# <a name="federation-sample"></a><span data-ttu-id="2b1fb-103">Federasyon Örneği</span><span class="sxs-lookup"><span data-stu-id="2b1fb-103">Federation Sample</span></span>

<span data-ttu-id="2b1fb-104">Bu örnekte, Federasyon güvenliği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-104">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="2b1fb-105">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2b1fb-105">Sample Details</span></span>  

 <span data-ttu-id="2b1fb-106">Windows Communication Foundation (WCF), aracılığıyla Federe güvenlik mimarileri dağıtmaya yönelik destek sağlar `wsFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="2b1fb-106">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="2b1fb-107">, `wsFederationHttpBinding` İstek/yanıt iletişimi için temel alınan aktarım mekanizması olarak http kullanımını ve kodlama için Tel biçimi olarak Text/XML ' i içeren, güvenli, güvenilir ve birlikte çalışabilen bir bağlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-107">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="2b1fb-108">WCF 'de Federasyon hakkında daha fazla bilgi için bkz. [Federasyon](../feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="2b1fb-108">For more information about Federation in WCF, see [Federation](../feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="2b1fb-109">Senaryo 4 parçadan oluşur:</span><span class="sxs-lookup"><span data-stu-id="2b1fb-109">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="2b1fb-110">Kitaplığı hizmeti</span><span class="sxs-lookup"><span data-stu-id="2b1fb-110">BookStore service</span></span>  
  
- <span data-ttu-id="2b1fb-111">Kitaplığı STS</span><span class="sxs-lookup"><span data-stu-id="2b1fb-111">BookStore STS</span></span>  
  
- <span data-ttu-id="2b1fb-112">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="2b1fb-112">HomeRealm STS</span></span>  
  
- <span data-ttu-id="2b1fb-113">Kitaplığı Istemcisi</span><span class="sxs-lookup"><span data-stu-id="2b1fb-113">BookStore Client</span></span>  
  
 <span data-ttu-id="2b1fb-114">Kitaplığı hizmeti iki işlemi destekler `BrowseBooks` `BuyBook` .</span><span class="sxs-lookup"><span data-stu-id="2b1fb-114">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="2b1fb-115">İşlem için anonim erişime izin verir `BrowseBooks` , ancak işleme erişmek için kimliği doğrulanmış erişim gerektirir `BuyBooks` .</span><span class="sxs-lookup"><span data-stu-id="2b1fb-115">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="2b1fb-116">Kimlik doğrulaması, kitaplığı STS tarafından verilen belirtecin biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-116">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="2b1fb-117">Kitaplığı hizmeti için yapılandırma dosyası, istemcileri ile kitaplığı STS 'ye yönlendirir `wsFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="2b1fb-117">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="2b1fb-118">Bu durumda, daha sonra, istemcilerin HomeRealm STS tarafından verilen bir belirteç kullanarak kimlik doğrulaması yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-118">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="2b1fb-119">Yine, kitaplığı STS 'nin yapılandırma dosyası, istemcileri ile HomeRealm STS 'ye işaret eder `wsFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="2b1fb-119">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="2b1fb-120">İşleme erişirken olay sırası `BuyBook` aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2b1fb-120">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="2b1fb-121">İstemci, Windows kimlik bilgilerini kullanarak HomeRealm STS 'nin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-121">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="2b1fb-122">HomeRealm STS, kitaplığı STS ' de kimlik doğrulaması için kullanılabilecek bir belirteç yayınlar.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-122">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="2b1fb-123">İstemci, HomeRealm STS tarafından verilen belirteci kullanarak kitaplığı STS 'de kimlik doğrulaması yapar.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-123">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="2b1fb-124">Kitaplığı STS, kitaplığı hizmetinde kimlik doğrulaması yapmak için kullanılabilecek bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-124">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="2b1fb-125">İstemci, kitaplığı STS tarafından verilen belirteci kullanarak Kitaplığı hizmeti için kimlik doğrulaması yapar.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-125">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="2b1fb-126">İstemci `BuyBook` işleme erişir.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-126">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="2b1fb-127">Bu örneği ayarlama ve çalıştırma hakkında aşağıdaki yönergelere bakın.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-127">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b1fb-128">Bu örneği çalıştırmak için **Wwwroot** dizinine yazma izinleriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-128">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2b1fb-129">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="2b1fb-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2b1fb-130">SDK komut penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-130">Open the SDK command window.</span></span> <span data-ttu-id="2b1fb-131">Örnek yolda Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-131">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="2b1fb-132">Bu, örnek için gereken sanal dizinleri oluşturur ve uygun izinlere sahip gerekli sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-132">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2b1fb-133">Setup.bat Batch dosyası bir Windows SDK komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-133">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="2b1fb-134">MSSDK ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-134">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="2b1fb-135">Bu ortam değişkeni bir Windows SDK komut Istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-135">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="2b1fb-136">Windows Vista 'da, kurulum IIS Yönetici betikleri kullandığından, IIS 6,0 yönetim uyumluluğuna emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-136">On Windows Vista, you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="2b1fb-137">Windows Vista 'da kurulum betiğini çalıştırmak için yönetici ayrıcalıkları gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-137">Running the set-up script on Windows Vista requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="2b1fb-138">Visual Studio 'da FederationSample. sln ' yi açın ve **derleme** menüsünden **çözüm oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-138">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="2b1fb-139">Bu, ortak proje dosyalarını, kitaplığı hizmeti, kitaplığı STS, HomeRealm STS 'yi oluşturur ve bunları IIS 'de dağıtır.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-139">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="2b1fb-140">Bu Ayrıca, kitaplığı istemci uygulamasını oluşturur ve çalıştırılabilir BookStoreClient.exe FederationSample\BookStoreClient\bin\Debug klasörüne koyar.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-140">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="2b1fb-141">BookStoreClient.exe çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-141">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="2b1fb-142">BookStoreClient penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-142">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="2b1fb-143">Kitaplarda bulunan kitaplara **gözatıp**' ye tıklayarak kitapçığa gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-143">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="2b1fb-144">Belirli bir kitabı satın almak için listeden kitabı seçin ve **kitabı satın al**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-144">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="2b1fb-145">Uygulama başlatılır ve Barındırmerealm güvenlik belirteci hizmeti ile Windows kimlik doğrulamasını kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-145">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="2b1fb-146">Örnek, kullanıcıların $15 veya daha az bir kitap satın almasını sağlamak üzere yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-146">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="2b1fb-147">$15 'den daha fazla maliyet satın alma girişimi, istemcinin kitap mağazası hizmetinden bir erişim reddedildi iletisi almasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-147">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2b1fb-148">Örnek, bir satın alma işleminden sonra kullanıcının kredi limitini güncelleştirmez.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-148">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="2b1fb-149">Kullanıcıların (Sabit) kredi limiti içindeki kitapları tekrar tekrar satın alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-149">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="2b1fb-150">Temizlemek için</span><span class="sxs-lookup"><span data-stu-id="2b1fb-150">To clean up</span></span>  
  
1. <span data-ttu-id="2b1fb-151">Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-151">Run Cleanup.bat.</span></span> <span data-ttu-id="2b1fb-152">Bu, ayarlama sırasında oluşturulan sanal dizinleri siler ve kurulum sırasında yüklenen sertifikaları da kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-152">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2b1fb-153">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-153">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2b1fb-154">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2b1fb-155">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2b1fb-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2b1fb-156">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2b1fb-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
