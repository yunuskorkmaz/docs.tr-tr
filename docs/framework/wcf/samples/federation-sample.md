---
title: Federasyon Örneği
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: bc2c28300d9bfc3c30388f8d13e05a23a9f37287
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311467"
---
# <a name="federation-sample"></a><span data-ttu-id="a2c4e-102">Federasyon Örneği</span><span class="sxs-lookup"><span data-stu-id="a2c4e-102">Federation Sample</span></span>
<span data-ttu-id="a2c4e-103">Bu örnek, Federasyon güvenlik gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="a2c4e-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="a2c4e-104">Sample Details</span></span>  
 <span data-ttu-id="a2c4e-105">Windows Communication Foundation (WCF), Federal güvenlik mimariler aracılığıyla dağıtmak için destek sağlar `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="a2c4e-106">`wsFederationHttpBinding` Kullanımını HTTP temel aktarma mekanizması olarak istek/yanıt iletişim ve metin/XML olarak kodlamak için kablo biçimini içeren bir güvenli, güvenilir ve birlikte çalışabilen bağlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="a2c4e-107">Wcf'de Federasyon hakkında daha fazla bilgi için bkz: [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="a2c4e-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="a2c4e-108">Senaryo 4 parçalarını oluşur:</span><span class="sxs-lookup"><span data-stu-id="a2c4e-108">The scenario is made up of 4 pieces:</span></span>  
  
-   <span data-ttu-id="a2c4e-109">Hizmet Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="a2c4e-109">BookStore service</span></span>  
  
-   <span data-ttu-id="a2c4e-110">STS kitaplığı</span><span class="sxs-lookup"><span data-stu-id="a2c4e-110">BookStore STS</span></span>  
  
-   <span data-ttu-id="a2c4e-111">STS HomeRealm</span><span class="sxs-lookup"><span data-stu-id="a2c4e-111">HomeRealm STS</span></span>  
  
-   <span data-ttu-id="a2c4e-112">İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="a2c4e-112">BookStore Client</span></span>  
  
 <span data-ttu-id="a2c4e-113">İki işlem kitaplığı hizmet destekler `BrowseBooks` ve `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="a2c4e-114">Anonim erişime izin veren `BrowseBooks` işlemi, ancak erişim için kimliği doğrulanmış erişim gerektiren `BuyBooks` işlemi.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="a2c4e-115">Kimlik doğrulama Kitaplığı'nı STS tarafından verilen belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="a2c4e-116">Kitaplığı STS kullanarak istemcileri kitaplığı hizmeti için yapılandırma dosyasını işaret `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="a2c4e-117">Kitaplığı STS, ardından istemcilerin HomeRealm STS tarafından verilen bir belirteç kullanarak kimlik doğrulaması gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="a2c4e-118">Yapılandırma dosyası kitaplığı STS HomeRealm STS kullanarak istemcileri yeniden işaret `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="a2c4e-119">Erişirken olayların sırasını `BuyBook` işlemi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a2c4e-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="a2c4e-120">İstemci, Windows kimlik bilgilerini kullanarak HomeRealm STS'ye kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="a2c4e-121">HomeRealm STS kitaplığı STS'ye kimlik doğrulaması için kullanılabilecek bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="a2c4e-122">İstemci Kitaplığı sts'ye HomeRealm STS tarafından verilen belirteci kullanarak kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="a2c4e-123">Kitaplığı STS kitaplığı hizmete kimlik doğrulaması için kullanılabilecek bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="a2c4e-124">İstemci Kitaplığı hizmet kitaplığı STS tarafından verilen belirteci kullanarak kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="a2c4e-125">İstemcisinin eriştiği `BuyBook` işlemi.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="a2c4e-126">Ayarlanmış ve bu örneği çalıştırmak hakkında aşağıdaki yönergelere bakın.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2c4e-127">Yazma izinlerine sahip olmalıdır **wwwroot** Bu örneği çalıştırmak için dizin.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a2c4e-128">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a2c4e-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a2c4e-129">SDK komut penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-129">Open the SDK command window.</span></span> <span data-ttu-id="a2c4e-130">Örnek yolunda Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="a2c4e-131">Bu örnek için gerekli sanal dizinler oluşturur ve uygun izinlere sahip gerekli sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a2c4e-132">Setup.bat toplu iş dosyası, bir Windows SDK Komut İstemi'nden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="a2c4e-133">MSSDK ortam değişkeni'nın SDK'ın yüklendiği dizini gösterecek gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="a2c4e-134">Bu ortam değişkeni, bir Windows SDK komut istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="a2c4e-135">Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], ayarlama, IIS Yöneticisi betikleri kullandığından, IIS 6.0 Yönetim uyumluluğu yüklü emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="a2c4e-136">Kurulum betiği çalıştırma [!INCLUDE[wv](../../../../includes/wv-md.md)] yönetici ayrıcalıkları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="a2c4e-137">Visual Studio'da FederationSample.sln açın ve seçin **Çözümü Derle** gelen **derleme** menüsü.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="a2c4e-138">Bu kitaplığı hizmet kitaplığı STS, HomeRealm STS, ortak proje dosyalarını oluşturur ve bunları IIS içinde dağıtır.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="a2c4e-139">Bu ayrıca kitaplığı istemci uygulaması oluşturur ve yürütülebilir BookStoreClient.exe FederationSample\BookStoreClient\bin\Debug klasörüne yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="a2c4e-140">BookStoreClient.exe çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="a2c4e-141">BookStoreClient penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-141">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="a2c4e-142">Tıklayarak kitaplığı içinde kullanılabilir olan kitapları göz atabilirsiniz **Gözat Books**.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="a2c4e-143">Belirli bir kitap satın almak için kitabı listeden seçin ve **satın kitap**.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="a2c4e-144">Uygulama başlatıldığında ve HomeRealm güvenlik belirteci hizmeti ile Windows kimlik doğrulaması kullanarak kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="a2c4e-145">, 15 ABD Doları maliyet kitapların satın almak kullanıcılara izin verecek şekilde yapılandırılmış ya da daha az örnektir.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="a2c4e-146">Birden çok erişim reddedildi iletisi kitap Store hizmetten alma istemci sonuçları 15 ABD Doları maliyet kitapların satın çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a2c4e-147">Örnek kullanıcının kredi limiti, satın almanızdan sonra güncelleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="a2c4e-148">Art arda kullanıcının (sabit) kredi sınırına içinde books satın alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="a2c4e-149">Temizlemek için</span><span class="sxs-lookup"><span data-stu-id="a2c4e-149">To clean up</span></span>  
  
1. <span data-ttu-id="a2c4e-150">CleanUp.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-150">Run Cleanup.bat.</span></span> <span data-ttu-id="a2c4e-151">Bu yedekleme kümesi sırasında oluşturulan sanal dizinleri siler ve Kurulum sırasında yüklenen sertifikaların da kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a2c4e-152">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a2c4e-153">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a2c4e-154">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a2c4e-155">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a2c4e-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
