---
title: Federasyon Örneği
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 00cb9a13a01687fb41f1d5c09f277d582f706e3b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594692"
---
# <a name="federation-sample"></a><span data-ttu-id="99185-102">Federasyon Örneği</span><span class="sxs-lookup"><span data-stu-id="99185-102">Federation Sample</span></span>
<span data-ttu-id="99185-103">Bu örnekte, Federasyon güvenliği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="99185-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="99185-104">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="99185-104">Sample Details</span></span>  
 <span data-ttu-id="99185-105">Windows Communication Foundation (WCF), aracılığıyla Federe güvenlik mimarileri dağıtmaya yönelik destek sağlar `wsFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="99185-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="99185-106">, `wsFederationHttpBinding` İstek/yanıt iletişimi için temel alınan aktarım mekanizması olarak http kullanımını ve kodlama için Tel biçimi olarak Text/XML ' i içeren, güvenli, güvenilir ve birlikte çalışabilen bir bağlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="99185-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="99185-107">WCF 'de Federasyon hakkında daha fazla bilgi için bkz. [Federasyon](../feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="99185-107">For more information about Federation in WCF, see [Federation](../feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="99185-108">Senaryo 4 parçadan oluşur:</span><span class="sxs-lookup"><span data-stu-id="99185-108">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="99185-109">Kitaplığı hizmeti</span><span class="sxs-lookup"><span data-stu-id="99185-109">BookStore service</span></span>  
  
- <span data-ttu-id="99185-110">Kitaplığı STS</span><span class="sxs-lookup"><span data-stu-id="99185-110">BookStore STS</span></span>  
  
- <span data-ttu-id="99185-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="99185-111">HomeRealm STS</span></span>  
  
- <span data-ttu-id="99185-112">Kitaplığı Istemcisi</span><span class="sxs-lookup"><span data-stu-id="99185-112">BookStore Client</span></span>  
  
 <span data-ttu-id="99185-113">Kitaplığı hizmeti iki işlemi destekler `BrowseBooks` `BuyBook` .</span><span class="sxs-lookup"><span data-stu-id="99185-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="99185-114">İşlem için anonim erişime izin verir `BrowseBooks` , ancak işleme erişmek için kimliği doğrulanmış erişim gerektirir `BuyBooks` .</span><span class="sxs-lookup"><span data-stu-id="99185-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="99185-115">Kimlik doğrulaması, kitaplığı STS tarafından verilen belirtecin biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="99185-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="99185-116">Kitaplığı hizmeti için yapılandırma dosyası, istemcileri ile kitaplığı STS 'ye yönlendirir `wsFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="99185-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="99185-117">Bu durumda, daha sonra, istemcilerin HomeRealm STS tarafından verilen bir belirteç kullanarak kimlik doğrulaması yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="99185-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="99185-118">Yine, kitaplığı STS 'nin yapılandırma dosyası, istemcileri ile HomeRealm STS 'ye işaret eder `wsFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="99185-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="99185-119">İşleme erişirken olay sırası `BuyBook` aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="99185-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="99185-120">İstemci, Windows kimlik bilgilerini kullanarak HomeRealm STS 'nin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="99185-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="99185-121">HomeRealm STS, kitaplığı STS ' de kimlik doğrulaması için kullanılabilecek bir belirteç yayınlar.</span><span class="sxs-lookup"><span data-stu-id="99185-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="99185-122">İstemci, HomeRealm STS tarafından verilen belirteci kullanarak kitaplığı STS 'de kimlik doğrulaması yapar.</span><span class="sxs-lookup"><span data-stu-id="99185-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="99185-123">Kitaplığı STS, kitaplığı hizmetinde kimlik doğrulaması yapmak için kullanılabilecek bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="99185-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="99185-124">İstemci, kitaplığı STS tarafından verilen belirteci kullanarak Kitaplığı hizmeti için kimlik doğrulaması yapar.</span><span class="sxs-lookup"><span data-stu-id="99185-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="99185-125">İstemci `BuyBook` işleme erişir.</span><span class="sxs-lookup"><span data-stu-id="99185-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="99185-126">Bu örneği ayarlama ve çalıştırma hakkında aşağıdaki yönergelere bakın.</span><span class="sxs-lookup"><span data-stu-id="99185-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99185-127">Bu örneği çalıştırmak için **Wwwroot** dizinine yazma izinleriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="99185-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="99185-128">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="99185-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="99185-129">SDK komut penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="99185-129">Open the SDK command window.</span></span> <span data-ttu-id="99185-130">Örnek yolda Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="99185-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="99185-131">Bu, örnek için gereken sanal dizinleri oluşturur ve uygun izinlere sahip gerekli sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="99185-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="99185-132">Setup. bat toplu iş dosyası bir Windows SDK komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="99185-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="99185-133">MSSDK ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="99185-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="99185-134">Bu ortam değişkeni bir Windows SDK komut Istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="99185-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="99185-135">Windows Vista 'da, kurulum IIS Yönetici betikleri kullandığından, IIS 6,0 yönetim uyumluluğuna emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="99185-135">On Windows Vista, you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="99185-136">Windows Vista 'da kurulum betiğini çalıştırmak için yönetici ayrıcalıkları gerekir.</span><span class="sxs-lookup"><span data-stu-id="99185-136">Running the set-up script on Windows Vista requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="99185-137">Visual Studio 'da FederationSample. sln ' yi açın ve **derleme** menüsünden **çözüm oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="99185-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="99185-138">Bu, ortak proje dosyalarını, kitaplığı hizmeti, kitaplığı STS, HomeRealm STS 'yi oluşturur ve bunları IIS 'de dağıtır.</span><span class="sxs-lookup"><span data-stu-id="99185-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="99185-139">Bu Ayrıca, kitaplığı istemci uygulamasını oluşturur ve Boosample\bookstoreclient\bin\debug klasörüne yürütülebilir BookStoreClient. exe ' yi koyar.</span><span class="sxs-lookup"><span data-stu-id="99185-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="99185-140">BookStoreClient. exe ' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="99185-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="99185-141">BookStoreClient penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="99185-141">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="99185-142">Kitaplarda bulunan kitaplara **gözatıp**' ye tıklayarak kitapçığa gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99185-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="99185-143">Belirli bir kitabı satın almak için listeden kitabı seçin ve **kitabı satın al**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="99185-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="99185-144">Uygulama başlatılır ve Barındırmerealm güvenlik belirteci hizmeti ile Windows kimlik doğrulamasını kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="99185-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="99185-145">Örnek, kullanıcıların $15 veya daha az bir kitap satın almasını sağlamak üzere yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="99185-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="99185-146">$15 'den daha fazla maliyet satın alma girişimi, istemcinin kitap mağazası hizmetinden bir erişim reddedildi iletisi almasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="99185-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="99185-147">Örnek, bir satın alma işleminden sonra kullanıcının kredi limitini güncelleştirmez.</span><span class="sxs-lookup"><span data-stu-id="99185-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="99185-148">Kullanıcıların (Sabit) kredi limiti içindeki kitapları tekrar tekrar satın alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99185-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="99185-149">Temizlemek için</span><span class="sxs-lookup"><span data-stu-id="99185-149">To clean up</span></span>  
  
1. <span data-ttu-id="99185-150">Cleanup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="99185-150">Run Cleanup.bat.</span></span> <span data-ttu-id="99185-151">Bu, ayarlama sırasında oluşturulan sanal dizinleri siler ve kurulum sırasında yüklenen sertifikaları da kaldırır.</span><span class="sxs-lookup"><span data-stu-id="99185-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="99185-152">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="99185-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="99185-153">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="99185-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="99185-154">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="99185-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="99185-155">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="99185-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
