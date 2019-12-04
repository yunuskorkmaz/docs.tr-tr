---
title: Federasyon Örneği
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 271790e08476533fc1d83e22c5a0daf2f1eaa42a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716934"
---
# <a name="federation-sample"></a><span data-ttu-id="e1d6c-102">Federasyon Örneği</span><span class="sxs-lookup"><span data-stu-id="e1d6c-102">Federation Sample</span></span>
<span data-ttu-id="e1d6c-103">Bu örnekte, Federasyon güvenliği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="e1d6c-104">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e1d6c-104">Sample Details</span></span>  
 <span data-ttu-id="e1d6c-105">Windows Communication Foundation (WCF) `wsFederationHttpBinding`aracılığıyla Federal Güvenlik mimarilerini dağıtmaya yönelik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="e1d6c-106">`wsFederationHttpBinding`, istek/yanıt iletişimi için temel alınan aktarım mekanizması olarak HTTP kullanımını ve kodlama için Tel biçimi olarak metin/XML kullanımını içeren güvenli, güvenilir ve birlikte çalışabilen bir bağlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="e1d6c-107">WCF 'de Federasyon hakkında daha fazla bilgi için bkz. [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="e1d6c-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="e1d6c-108">Senaryo 4 parçadan oluşur:</span><span class="sxs-lookup"><span data-stu-id="e1d6c-108">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="e1d6c-109">Kitaplığı hizmeti</span><span class="sxs-lookup"><span data-stu-id="e1d6c-109">BookStore service</span></span>  
  
- <span data-ttu-id="e1d6c-110">Kitaplığı STS</span><span class="sxs-lookup"><span data-stu-id="e1d6c-110">BookStore STS</span></span>  
  
- <span data-ttu-id="e1d6c-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="e1d6c-111">HomeRealm STS</span></span>  
  
- <span data-ttu-id="e1d6c-112">Kitaplığı Istemcisi</span><span class="sxs-lookup"><span data-stu-id="e1d6c-112">BookStore Client</span></span>  
  
 <span data-ttu-id="e1d6c-113">Kitaplığı hizmeti, `BrowseBooks` ve `BuyBook`iki işlemi destekler.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="e1d6c-114">`BrowseBooks` işleme anonim erişimine izin verir, ancak `BuyBooks` işlemine erişmek için kimliği doğrulanmış erişim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="e1d6c-115">Kimlik doğrulaması, kitaplığı STS tarafından verilen belirtecin biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="e1d6c-116">Kitaplığı hizmeti için yapılandırma dosyası, istemcileri `wsFederationHttpBinding`kullanarak kitaplara yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="e1d6c-117">Bu durumda, daha sonra, istemcilerin HomeRealm STS tarafından verilen bir belirteç kullanarak kimlik doğrulaması yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="e1d6c-118">Yine, kitaplığı STS için yapılandırma dosyası, istemcileri `wsFederationHttpBinding`kullanarak HomeRealm STS 'ye yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="e1d6c-119">`BuyBook` işlemine erişirken olayların sırası aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e1d6c-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="e1d6c-120">İstemci, Windows kimlik bilgilerini kullanarak HomeRealm STS 'nin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="e1d6c-121">HomeRealm STS, kitaplığı STS ' de kimlik doğrulaması için kullanılabilecek bir belirteç yayınlar.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="e1d6c-122">İstemci, HomeRealm STS tarafından verilen belirteci kullanarak kitaplığı STS 'de kimlik doğrulaması yapar.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="e1d6c-123">Kitaplığı STS, kitaplığı hizmetinde kimlik doğrulaması yapmak için kullanılabilecek bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="e1d6c-124">İstemci, kitaplığı STS tarafından verilen belirteci kullanarak Kitaplığı hizmeti için kimlik doğrulaması yapar.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="e1d6c-125">İstemci `BuyBook` işlemine erişir.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="e1d6c-126">Bu örneği ayarlama ve çalıştırma hakkında aşağıdaki yönergelere bakın.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1d6c-127">Bu örneği çalıştırmak için **Wwwroot** dizinine yazma izinleriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e1d6c-128">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e1d6c-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e1d6c-129">SDK komut penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-129">Open the SDK command window.</span></span> <span data-ttu-id="e1d6c-130">Örnek yolda Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="e1d6c-131">Bu, örnek için gereken sanal dizinleri oluşturur ve uygun izinlere sahip gerekli sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e1d6c-132">Setup. bat toplu iş dosyası bir Windows SDK komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="e1d6c-133">MSSDK ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="e1d6c-134">Bu ortam değişkeni bir Windows SDK komut Istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="e1d6c-135">[!INCLUDE[wv](../../../../includes/wv-md.md)], kurulum 'un IIS Yönetici betikleri kullandığından, IIS 6,0 yönetim uyumluluğuna emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="e1d6c-136">[!INCLUDE[wv](../../../../includes/wv-md.md)] kurulum betiğini çalıştırmak için yönetici ayrıcalıkları gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="e1d6c-137">Visual Studio 'da FederationSample. sln ' yi açın ve **derleme** menüsünden **çözüm oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="e1d6c-138">Bu, ortak proje dosyalarını, kitaplığı hizmeti, kitaplığı STS, HomeRealm STS 'yi oluşturur ve bunları IIS 'de dağıtır.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="e1d6c-139">Bu Ayrıca, kitaplığı istemci uygulamasını oluşturur ve Boosample\bookstoreclient\bin\debug klasörüne yürütülebilir BookStoreClient. exe ' yi koyar.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="e1d6c-140">BookStoreClient. exe ' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="e1d6c-141">BookStoreClient penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-141">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="e1d6c-142">Kitaplarda bulunan kitaplara **gözatıp**' ye tıklayarak kitapçığa gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="e1d6c-143">Belirli bir kitabı satın almak için listeden kitabı seçin ve **kitabı satın al**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="e1d6c-144">Uygulama başlatılır ve Barındırmerealm güvenlik belirteci hizmeti ile Windows kimlik doğrulamasını kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="e1d6c-145">Örnek, kullanıcıların $15 veya daha az bir kitap satın almasını sağlamak üzere yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="e1d6c-146">$15 'den daha fazla maliyet satın alma girişimi, istemcinin kitap mağazası hizmetinden bir erişim reddedildi iletisi almasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e1d6c-147">Örnek, bir satın alma işleminden sonra kullanıcının kredi limitini güncelleştirmez.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="e1d6c-148">Kullanıcıların (Sabit) kredi limiti içindeki kitapları tekrar tekrar satın alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="e1d6c-149">Temizlemek için</span><span class="sxs-lookup"><span data-stu-id="e1d6c-149">To clean up</span></span>  
  
1. <span data-ttu-id="e1d6c-150">Cleanup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-150">Run Cleanup.bat.</span></span> <span data-ttu-id="e1d6c-151">Bu, ayarlama sırasında oluşturulan sanal dizinleri siler ve kurulum sırasında yüklenen sertifikaları da kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e1d6c-152">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e1d6c-153">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-153">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e1d6c-154">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e1d6c-155">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e1d6c-155">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
