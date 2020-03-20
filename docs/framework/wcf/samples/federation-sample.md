---
title: Federasyon Örneği
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 9ec462f88c0e3a039b7f288554be3e28f13ece08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144675"
---
# <a name="federation-sample"></a><span data-ttu-id="40f89-102">Federasyon Örneği</span><span class="sxs-lookup"><span data-stu-id="40f89-102">Federation Sample</span></span>
<span data-ttu-id="40f89-103">Bu örnek federe güvenliği gösteriyor.</span><span class="sxs-lookup"><span data-stu-id="40f89-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="40f89-104">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="40f89-104">Sample Details</span></span>  
 <span data-ttu-id="40f89-105">Windows Communication Foundation (WCF), federe güvenlik mimarilerinin dağıtılamı için destek `wsFederationHttpBinding`sağlar.</span><span class="sxs-lookup"><span data-stu-id="40f89-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="40f89-106">İstek/yanıt iletişimi `wsFederationHttpBinding` için temel aktarım mekanizması olarak HTTP'nin kullanımını ve kodlama için tel biçimi olarak Metin/XML'i içeren güvenli, güvenilir ve birlikte çalışabilir bir bağlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="40f89-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="40f89-107">WCF'deki Federasyon hakkında daha fazla bilgi için [Federasyon'a](../../../../docs/framework/wcf/feature-details/federation.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="40f89-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="40f89-108">Senaryo 4 parçadan oluşur:</span><span class="sxs-lookup"><span data-stu-id="40f89-108">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="40f89-109">BookStore hizmeti</span><span class="sxs-lookup"><span data-stu-id="40f89-109">BookStore service</span></span>  
  
- <span data-ttu-id="40f89-110">Kitapçı STS</span><span class="sxs-lookup"><span data-stu-id="40f89-110">BookStore STS</span></span>  
  
- <span data-ttu-id="40f89-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="40f89-111">HomeRealm STS</span></span>  
  
- <span data-ttu-id="40f89-112">Kitabevi İstemcisi</span><span class="sxs-lookup"><span data-stu-id="40f89-112">BookStore Client</span></span>  
  
 <span data-ttu-id="40f89-113">BookStore hizmeti iki işlemi `BrowseBooks` `BuyBook`destekler ve .</span><span class="sxs-lookup"><span data-stu-id="40f89-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="40f89-114">`BrowseBooks` Bu işlem için anonim erişim sağlar, ancak `BuyBooks` operasyona erişmek için kimlik doğrulaması erişim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="40f89-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="40f89-115">Kimlik doğrulaması BookStore STS tarafından verilen bir belirteç biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="40f89-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="40f89-116">BookStore Hizmeti için yapılandırma dosyası, istemcileri BookStore `wsFederationHttpBinding`STS'ye işaret eder.</span><span class="sxs-lookup"><span data-stu-id="40f89-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="40f89-117">BookStore STS daha sonra istemcilerin HomeRealm STS tarafından verilen bir belirteç kullanarak kimlik doğrulamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="40f89-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="40f89-118">Yine, BookStore STS için yapılandırma dosyası kullanarak HomeRealm STS istemcileri `wsFederationHttpBinding`puan.</span><span class="sxs-lookup"><span data-stu-id="40f89-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="40f89-119">`BuyBook` İşleme erişirken olayların sırası aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="40f89-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="40f89-120">İstemci, Windows kimlik bilgilerini kullanarak HomeRealm STS'ye kimlik doğrulaması yaptı.</span><span class="sxs-lookup"><span data-stu-id="40f89-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="40f89-121">HomeRealm STS, BookStore STS'ye kimlik doğrulamak için kullanılabilecek bir belirteç yayınlar.</span><span class="sxs-lookup"><span data-stu-id="40f89-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="40f89-122">İstemci, HomeRealm STS tarafından verilen belirteci kullanarak BookStore STS'ye doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="40f89-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="40f89-123">BookStore STS, BookStore Hizmeti'nin kimliğini doğrulamak için kullanılabilecek bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="40f89-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="40f89-124">İstemci, BookStore STS tarafından verilen belirteci kullanarak BookStore hizmetine kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="40f89-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="40f89-125">İstemci işlem `BuyBook` erişimi.</span><span class="sxs-lookup"><span data-stu-id="40f89-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="40f89-126">Bu örneğin nasıl ayarlanıp çalıştırılabildiğini ilgili aşağıdaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="40f89-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40f89-127">Bu örneği çalıştırmak için **wwwroot** dizinine yazma izinlerine sahip olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="40f89-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="40f89-128">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="40f89-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="40f89-129">SDK komut penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="40f89-129">Open the SDK command window.</span></span> <span data-ttu-id="40f89-130">Örnek yolda Kurulum.bat'ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="40f89-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="40f89-131">Bu, örnek için gereken sanal dizinleri oluşturur ve gerekli sertifikaları uygun izinlerle yükler.</span><span class="sxs-lookup"><span data-stu-id="40f89-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="40f89-132">Setup.bat toplu dosyası, Windows SDK Komut İstemi'nden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="40f89-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="40f89-133">MSSDK ortamı değişkeninin SDK'nın yüklendiği dizine işaret etmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="40f89-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="40f89-134">Bu ortam değişkeni otomatik olarak bir Windows SDK Komut İstemi içinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="40f89-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="40f89-135">Windows Vista'da, kurulum IIS yönetici komut dosyalarını kullandığından IIS 6.0 Yönetim Uyumluluğunun yüklü olduğundan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="40f89-135">On Windows Vista, you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="40f89-136">Windows Vista'da kurulum komut dosyasının çalıştırılması için yönetici ayrıcalıkları gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="40f89-136">Running the set-up script on Windows Vista requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="40f89-137">Visual Studio'da FederationSample.sln'yi açın ve **Yapı** menüsünden **Çözüm Oluştur'u** seçin.</span><span class="sxs-lookup"><span data-stu-id="40f89-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="40f89-138">Bu ortak proje dosyaları, Kitabevi hizmeti, Kitabevi STS, HomeRealm STS oluşturur ve IIS bunları dağıtır.</span><span class="sxs-lookup"><span data-stu-id="40f89-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="40f89-139">Bu da Kitabevi istemci uygulaması oluşturur ve yürütülebilir BookStoreClient.exe'yi FederationSample\BookStoreClient\bin\Debug klasörüne yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="40f89-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="40f89-140">BookStoreClient.exe'yi çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="40f89-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="40f89-141">BookStoreClient penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="40f89-141">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="40f89-142">**Kitaplara Gözat'ı**tıklayarak kitapçıda bulunan kitaplara göz atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40f89-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="40f89-143">Belirli bir kitabı satın almak için, listedeki kitabı seçin ve **Kitap Satın Al'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="40f89-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="40f89-144">Uygulama başlatılır ve HomeRealm Güvenlik Belirteç Hizmeti ile Windows kimlik doğrulaması kullanarak kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="40f89-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="40f89-145">Örnek, kullanıcıların 15 ABD doları veya daha az maliyetli kitap satın almasına olanak sağlayacak şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="40f89-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="40f89-146">15 TL'den fazla maliyetli kitap satın almaya çalışmak, istemcinin Book Store Hizmeti'nden Erişim Reddedilen bir ileti almasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="40f89-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="40f89-147">Örnek, bir satın alma işleminden sonra kullanıcının kredi limitini güncelleştirmez.</span><span class="sxs-lookup"><span data-stu-id="40f89-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="40f89-148">Kullanıcının (sabit) kredi limiti dahilinde sürekli olarak kitap satın alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40f89-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="40f89-149">Temizlemek için</span><span class="sxs-lookup"><span data-stu-id="40f89-149">To clean up</span></span>  
  
1. <span data-ttu-id="40f89-150">Cleanup'ı çalıştır.yarasa.</span><span class="sxs-lookup"><span data-stu-id="40f89-150">Run Cleanup.bat.</span></span> <span data-ttu-id="40f89-151">Bu, kurulum sırasında oluşturulan sanal dizinleri siler ve kurulum sırasında yüklenen sertifikaları da kaldırır.</span><span class="sxs-lookup"><span data-stu-id="40f89-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="40f89-152">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="40f89-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="40f89-153">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="40f89-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="40f89-154">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="40f89-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="40f89-155">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="40f89-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
