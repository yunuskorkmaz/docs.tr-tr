---
title: "Federasyon Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a13632318902ce08678a01c3e63b3d12cc2f4f20
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="federation-sample"></a><span data-ttu-id="21737-102">Federasyon Örneği</span><span class="sxs-lookup"><span data-stu-id="21737-102">Federation Sample</span></span>
<span data-ttu-id="21737-103">Bu örnek federe güvenlik gösterir.</span><span class="sxs-lookup"><span data-stu-id="21737-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="21737-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="21737-104">Sample Details</span></span>  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="21737-105">Federasyon güvenlik mimarileri üzerinden dağıtmak için destek sağlar `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="21737-105"> provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="21737-106">`wsFederationHttpBinding` Kullanmayı HTTP temelindeki iletim mekanizması olarak istek/yanıt iletişimi ve Text/XML kodlama için kablo biçiminde içerir güvenli, güvenilir ve birlikte çalışabilir bağlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="21737-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="21737-107">İçinde Federasyon [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bkz: [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="21737-107"> Federation in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="21737-108">Senaryo 4 parçalarını oluşur:</span><span class="sxs-lookup"><span data-stu-id="21737-108">The scenario is made up of 4 pieces:</span></span>  
  
-   <span data-ttu-id="21737-109">Kitap hizmeti</span><span class="sxs-lookup"><span data-stu-id="21737-109">BookStore service</span></span>  
  
-   <span data-ttu-id="21737-110">STS kitaplığı</span><span class="sxs-lookup"><span data-stu-id="21737-110">BookStore STS</span></span>  
  
-   <span data-ttu-id="21737-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="21737-111">HomeRealm STS</span></span>  
  
-   <span data-ttu-id="21737-112">İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="21737-112">BookStore Client</span></span>  
  
 <span data-ttu-id="21737-113">İki işlem kitap hizmeti destekler `BrowseBooks` ve `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="21737-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="21737-114">Anonim erişime izin verir `BrowseBooks` işlemi, ancak erişim için kimlik doğrulamalı erişim gerektiren `BuyBooks` işlemi.</span><span class="sxs-lookup"><span data-stu-id="21737-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="21737-115">Kimlik doğrulama kitaplığı STS tarafından verilmiş bir belirteç biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="21737-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="21737-116">Kitap STS kullanarak istemcileri kitap hizmeti için yapılandırma dosyasını işaret `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="21737-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="21737-117">Kitap STS, ardından istemciler HomeRealm STS tarafından verilmiş bir belirteç kullanarak kimlik doğrulaması gerektirir.</span><span class="sxs-lookup"><span data-stu-id="21737-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="21737-118">Kitap STS için yapılandırma dosyası HomeRealm STS kullanarak istemcileri yeniden işaret `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="21737-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="21737-119">Erişirken olayların sırası `BuyBook` işlemi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="21737-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1.  <span data-ttu-id="21737-120">İstemci, Windows kimlik bilgilerini kullanarak HomeRealm STS kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="21737-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2.  <span data-ttu-id="21737-121">HomeRealm STS kitap STS kimliğini doğrulamak için kullanılan bir belirteci verir.</span><span class="sxs-lookup"><span data-stu-id="21737-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3.  <span data-ttu-id="21737-122">İstemci Kitaplığı HomeRealm STS tarafından verilen belirteç kullanılarak STS kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="21737-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4.  <span data-ttu-id="21737-123">Kitap STS kitap hizmete kimliğini doğrulamak için kullanılan bir belirteci verir.</span><span class="sxs-lookup"><span data-stu-id="21737-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5.  <span data-ttu-id="21737-124">İstemci Kitaplığı hizmeti kitap STS tarafından verilen belirteç kullanarak kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="21737-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6.  <span data-ttu-id="21737-125">İstemcisinin eriştiği `BuyBook` işlemi.</span><span class="sxs-lookup"><span data-stu-id="21737-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="21737-126">Ayarlanmış ve bu örneği çalıştırmak hakkında aşağıdaki yönergelere bakın.</span><span class="sxs-lookup"><span data-stu-id="21737-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21737-127">Yazma izinlerine sahip olmalıdır **wwwroot** Bu örneği çalıştırmak için dizin.</span><span class="sxs-lookup"><span data-stu-id="21737-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="21737-128">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="21737-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="21737-129">SDK komut penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="21737-129">Open the SDK command window.</span></span> <span data-ttu-id="21737-130">Örnek yolunda Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="21737-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="21737-131">Bu örnek için gerekli sanal dizinler oluşturur ve gerekli sertifikaları uygun izinlerle birlikte yükler.</span><span class="sxs-lookup"><span data-stu-id="21737-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="21737-132">Setup.bat toplu iş dosyası, Windows SDK komut isteminden çalıştırılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="21737-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="21737-133">MSSDK ortam değişkeni SDK yüklendiği dizinine işaret gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="21737-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="21737-134">Bu ortam değişkeni, Windows SDK komut istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="21737-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="21737-135">Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], IIS 6.0 Yönetim uyumluluğu kurma IIS Yönetici komut dosyaları kullandığından yüklü emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="21737-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="21737-136">Kurulum komut dosyası çalıştırma [!INCLUDE[wv](../../../../includes/wv-md.md)] yönetici ayrıcalıkları gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="21737-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2.  <span data-ttu-id="21737-137">Visual Studio'da FederationSample.sln açın ve seçin **yapı çözümü** gelen **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="21737-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="21737-138">Bu kitap hizmet, kitap STS, HomeRealm STS, ortak proje dosyalarını oluşturur ve IIS içinde dağıtır.</span><span class="sxs-lookup"><span data-stu-id="21737-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="21737-139">Bu ayrıca kitap istemci uygulaması oluşturur ve yürütülebilir BookStoreClient.exe FederationSample\BookStoreClient\bin\Debug klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="21737-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3.  <span data-ttu-id="21737-140">BookStoreClient.exe çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="21737-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="21737-141">BookStoreClient penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21737-141">The BookStoreClient window is displayed.</span></span>  
  
4.  <span data-ttu-id="21737-142">Tıklayarak kitap kullanılabilir books göz atabilirsiniz **Gözat Books**.</span><span class="sxs-lookup"><span data-stu-id="21737-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5.  <span data-ttu-id="21737-143">Belirli bir kitap satın almak için kitap listeden seçin ve **satın kitap**.</span><span class="sxs-lookup"><span data-stu-id="21737-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="21737-144">Uygulama başlatıldığında ve HomeRealm güvenlik belirteci hizmeti Windows kimlik doğrulaması kullanarak kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="21737-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="21737-145">Örnek $15 maliyet books satın yapmalarına izin vermek için yapılandırılmış veya daha az.</span><span class="sxs-lookup"><span data-stu-id="21737-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="21737-146">Birden çok kitap depolama Hizmeti'nden bir erişim reddedildi iletisi alma istemci $15 sonuçlarında maliyet books satın çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="21737-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="21737-147">Örnek satın alma sonra kullanıcının kredi sınırını güncelleştirmez.</span><span class="sxs-lookup"><span data-stu-id="21737-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="21737-148">Art arda defterleri kullanıcının (sabit) kredi sınırı içinde satın alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21737-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="21737-149">Temizlemek için</span><span class="sxs-lookup"><span data-stu-id="21737-149">To clean up</span></span>  
  
1.  <span data-ttu-id="21737-150">CleanUp.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="21737-150">Run Cleanup.bat.</span></span> <span data-ttu-id="21737-151">Bu yukarı kümesi sırasında oluşturulan sanal dizinleri siler ve Kurulum sırasında yüklenen sertifikaların de kaldırır.</span><span class="sxs-lookup"><span data-stu-id="21737-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="21737-152">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="21737-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="21737-153">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="21737-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="21737-154">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="21737-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="21737-155">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="21737-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  
## <a name="see-also"></a><span data-ttu-id="21737-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21737-156">See Also</span></span>
