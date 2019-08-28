---
title: Belge Onay İşlemi
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: 20167cd1c06c2ae57dfe48fd07ab3a0e2adf9927
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038234"
---
# <a name="document-approval-process"></a><span data-ttu-id="fffd7-102">Belge Onay İşlemi</span><span class="sxs-lookup"><span data-stu-id="fffd7-102">Document Approval Process</span></span>

<span data-ttu-id="fffd7-103">Bu örnek, birçok Windows Workflow Foundation (WF) ve Windows Communication Foundation (WCF) özelliklerinin birlikte kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-103">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="fffd7-104">Birlikte bir belge onay süreci senaryosu uygular.</span><span class="sxs-lookup"><span data-stu-id="fffd7-104">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="fffd7-105">İstemci uygulaması, belgeleri onay ve onaylama için gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-105">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="fffd7-106">İstemciler arasındaki iletişimleri kolaylaştırmak ve onay işleminin kurallarını zorlamak için bir onay Yöneticisi uygulaması vardır.</span><span class="sxs-lookup"><span data-stu-id="fffd7-106">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="fffd7-107">Onay süreci, çeşitli onay türlerini yürütebilmesi için bir iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="fffd7-107">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="fffd7-108">Tek bir onay, bir çekirdek onayı (bir onaylayanlar kümesinin yüzdesi) ve bir dizideki bir çekirdekte ve tek bir onaydan oluşan karmaşık bir onay işlemi almak için etkinlik vardır.</span><span class="sxs-lookup"><span data-stu-id="fffd7-108">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fffd7-109">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fffd7-110">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fffd7-110">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="fffd7-111">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="fffd7-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fffd7-112">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fffd7-112">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`

## <a name="sample-details"></a><span data-ttu-id="fffd7-113">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fffd7-113">Sample Details</span></span>

<span data-ttu-id="fffd7-114">Aşağıdaki grafik belge onay süreci iş akışını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="fffd7-114">The following graphic demonstrates the document approval process workflow:</span></span>

![Bir belge onay işlemi iş akışı](./media/document-approval-process/document-approval-process.jpg)

<span data-ttu-id="fffd7-116">İstemci perspektifinden, onay işlemi aşağıdaki gibi çalışır:</span><span class="sxs-lookup"><span data-stu-id="fffd7-116">From the client's perspective, the approval process functions as follows:</span></span>

1. <span data-ttu-id="fffd7-117">İstemci, onay işlem sisteminde bir kullanıcı olarak abone olur.</span><span class="sxs-lookup"><span data-stu-id="fffd7-117">A client subscribes to be a user in the approval process system.</span></span>

2. <span data-ttu-id="fffd7-118">WCF istemcisi, onay Yöneticisi uygulaması tarafından barındırılan bir WCF hizmetine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-118">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>

3. <span data-ttu-id="fffd7-119">İstemciye benzersiz bir kullanıcı KIMLIĞI döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fffd7-119">A unique user ID is returned to the client.</span></span> <span data-ttu-id="fffd7-120">İstemci artık onay işlemlerine katılabilir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-120">The client can now participate in approval processes.</span></span>

4. <span data-ttu-id="fffd7-121">Bir istemci birleştirildikten sonra tek, çekirdek veya karmaşık onay süreçlerini kullanarak bir belgeyi onaya gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-121">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>

5. <span data-ttu-id="fffd7-122">İstemci arabirimindeki bir düğmeye tıkladıktan sonra istemci Iş akışı hizmet ana bilgisayarında bir iş akışı örneği başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="fffd7-122">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>

6. <span data-ttu-id="fffd7-123">İş akışı, onay Yöneticisi uygulamasına bir onay isteği gönderir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-123">The workflow sends an approval request to the approval manager application.</span></span>

7. <span data-ttu-id="fffd7-124">Workflow Manager, bir onay işlemini göstermek için kendi tarafında bir iş akışı başlatır.</span><span class="sxs-lookup"><span data-stu-id="fffd7-124">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>

8. <span data-ttu-id="fffd7-125">Yönetici onayı iş akışı yürütüldükten sonra sonuçlar istemciye geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-125">Once the manager approval workflow executes, the results are sent back to the client.</span></span>

9. <span data-ttu-id="fffd7-126">İstemci sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fffd7-126">The client displays the results.</span></span>

10. <span data-ttu-id="fffd7-127">İstemci bir onay isteği alabilir ve herhangi bir zamanda istek için yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-127">A client may receive an approval request and respond to the request at any point in time.</span></span>

11. <span data-ttu-id="fffd7-128">İstemcide barındırılan bir WCF hizmeti, onay Yöneticisi uygulamasından bir onay isteği alabilir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-128">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>

12. <span data-ttu-id="fffd7-129">Belge bilgileri, gözden geçirilmek üzere istemcisinde sunulur.</span><span class="sxs-lookup"><span data-stu-id="fffd7-129">The document information is presented on the client for review.</span></span>

13. <span data-ttu-id="fffd7-130">Kullanıcı belgeyi onaylayabilir veya reddedebilir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-130">The user can approve or reject the document.</span></span>

14. <span data-ttu-id="fffd7-131">Bir WCF istemcisi, bir onay yanıtını onay Yöneticisi uygulamasına geri göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fffd7-131">A WCF client is used to send an approval response back to the approval manager application.</span></span>

<span data-ttu-id="fffd7-132">Onay Yöneticisi uygulamasının görünüm noktasından, onay işlemi aşağıdaki gibi çalışır:</span><span class="sxs-lookup"><span data-stu-id="fffd7-132">From the approval manager application’s point of view, the approval process functions as follows:</span></span>

1. <span data-ttu-id="fffd7-133">İstemci onay işlem sistemine katılmayı ister.</span><span class="sxs-lookup"><span data-stu-id="fffd7-133">A client requests to participate to the approval process system.</span></span>

2. <span data-ttu-id="fffd7-134">Onay yöneticisinde bir WCF hizmeti, onay işlem sisteminin bir parçası olarak bir istek alır.</span><span class="sxs-lookup"><span data-stu-id="fffd7-134">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>

3. <span data-ttu-id="fffd7-135">İstemci için benzersiz bir KIMLIK oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fffd7-135">A unique ID is generated for the client.</span></span> <span data-ttu-id="fffd7-136">Kullanıcı bilgileri bir veritabanında depolanır.</span><span class="sxs-lookup"><span data-stu-id="fffd7-136">The user information is stored in a database.</span></span>

4. <span data-ttu-id="fffd7-137">Benzersiz KIMLIK kullanıcıya geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-137">The unique ID is sent back to the user.</span></span>

5. <span data-ttu-id="fffd7-138">Bir onay isteği alma.</span><span class="sxs-lookup"><span data-stu-id="fffd7-138">An approval request is receive.</span></span> <span data-ttu-id="fffd7-139">Onay Yöneticisi bir onay işlemi yürütür.</span><span class="sxs-lookup"><span data-stu-id="fffd7-139">The approval manager executes an approval process.</span></span>

6. <span data-ttu-id="fffd7-140">Onay Yöneticisi tarafından yeni bir iş akışı başlatılıyor onay isteği alındı.</span><span class="sxs-lookup"><span data-stu-id="fffd7-140">An approval request is received by the approval manager, starting a new workflow.</span></span>

7. <span data-ttu-id="fffd7-141">İsteğin türüne (basit, çekirdek veya karmaşık) bağlı olarak farklı bir etkinlik yürütülür.</span><span class="sxs-lookup"><span data-stu-id="fffd7-141">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>

8. <span data-ttu-id="fffd7-142">İlişki ile gönderme ve alma etkinlikleri, gözden geçirme için istemciye onay isteği göndermek ve yanıtı almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fffd7-142">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>

9. <span data-ttu-id="fffd7-143">Onay süreci iş akışının sonucu istemciye gönderilir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-143">The result of the approval process workflow is sent to the client.</span></span>

## <a name="using-the-sample"></a><span data-ttu-id="fffd7-144">Örneği kullanma</span><span class="sxs-lookup"><span data-stu-id="fffd7-144">Using the Sample</span></span>

##### <a name="to-set-up-the-database"></a><span data-ttu-id="fffd7-145">Veritabanını ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="fffd7-145">To set up the database</span></span>

1. <span data-ttu-id="fffd7-146">Yönetici ayrıcalıklarıyla açılan bir Visual Studio 2010 komut isteminden, bu belgeleyici klasörüne gidin ve Setup. cmd ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-146">From a Visual Studio 2010 command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>

##### <a name="to-set-up-the-application"></a><span data-ttu-id="fffd7-147">Uygulamayı ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="fffd7-147">To set up the application</span></span>

1. <span data-ttu-id="fffd7-148">Visual Studio 2010 kullanarak, Belgetapprovalprocess. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-148">Using Visual Studio 2010, open the DocumentApprovalProcess.sln solution file.</span></span>

2. <span data-ttu-id="fffd7-149">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-149">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="fffd7-150">Çözümü çalıştırmak için **Çözüm Gezgini** ApprovalManager projesine sağ tıklayıp sağ tıklama menüsünden **Hata Ayıkla**->yeni örnek**Başlat** ' a tıklayarak onay Yöneticisi uygulamasını başlatın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-150">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>

    <span data-ttu-id="fffd7-151">Yöneticinin çıkışının, olduğunu bilmenizi sağlamak için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="fffd7-151">Wait for the manager’s output to let you know that it is ready.</span></span>

##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="fffd7-152">Tek onay senaryosunu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fffd7-152">To run the single approval scenario</span></span>

1. <span data-ttu-id="fffd7-153">Yönetici izniyle bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-153">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="fffd7-154">Çözümü içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="fffd7-154">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="fffd7-155">ApprovalClient\Bin\Debug klasörüne gidin ve ApprovalClient. exe ' nin iki örneğini yürütün.</span><span class="sxs-lookup"><span data-stu-id="fffd7-155">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="fffd7-156">**Keşfet**' e tıklayın, **abone ol** düğmesi etkin olana kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="fffd7-156">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="fffd7-157">Herhangi bir Kullanıcı adı yazın ve **abone ol**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-157">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="fffd7-158">Bir istemci için ve diğer `UserType1` türü `UserType2`kullanın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-158">For one client, use `UserType1` and the other type `UserType2`.</span></span>

6. <span data-ttu-id="fffd7-159">`UserType1` İstemcide, açılan menüden tek onay türünü seçin ve bir belge adı ve içerik yazın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-159">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="fffd7-160">**Onay iste**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-160">Click **Request Approval**.</span></span>

7. <span data-ttu-id="fffd7-161">`UserType2` İstemcide onay bekleyen bir belge görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-161">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="fffd7-162">Seçin ve **Onayla** veya **Reddet**' e basın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-162">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="fffd7-163">Sonuçların `UserType1` istemcide gösterilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-163">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="fffd7-164">Çekirdek onay senaryosunu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fffd7-164">To run the quorum approval scenario</span></span>

1. <span data-ttu-id="fffd7-165">Yönetici izniyle bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-165">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="fffd7-166">Çözümü içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="fffd7-166">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="fffd7-167">ApprovalClient\Bin\Debug klasörüne gidin ve ApprovalClient. exe ' nin üç örneğini yürütün.</span><span class="sxs-lookup"><span data-stu-id="fffd7-167">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="fffd7-168">**Keşfet**' e tıklayın, **abone ol** düğmesi etkin olana kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="fffd7-168">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="fffd7-169">Herhangi bir Kullanıcı adı yazın ve **abone ol**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-169">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="fffd7-170">Bir istemci kullanımı `UserType1` ve diğer iki tür `UserType2`için.</span><span class="sxs-lookup"><span data-stu-id="fffd7-170">For one client use `UserType1` and the other two type `UserType2`.</span></span>

6. <span data-ttu-id="fffd7-171">`UserType1` İstemcide, açılan menüden çekirdek onay türünü seçin ve bir belge adı ve içerik yazın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-171">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="fffd7-172">**Onay iste**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-172">Click **Request Approval**.</span></span> <span data-ttu-id="fffd7-173">Bu, iki `UserType2` istemcinin belgeyi onaylamasını veya reddetmesini ister.</span><span class="sxs-lookup"><span data-stu-id="fffd7-173">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="fffd7-174">Her iki `UserType2` istemcinin da yanıt vermesi gerekir, ancak belgeyi onaylanacak şekilde yalnızca bir istemci onaylaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-174">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>

7. <span data-ttu-id="fffd7-175">`UserType2` İstemcilerde onay bekleyen bir belge görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-175">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="fffd7-176">Seçin ve **Onayla** veya **Reddet**' e basın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-176">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="fffd7-177">Sonuçların `UserType1` istemcide gösterilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-177">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="fffd7-178">Karmaşık onay senaryosunu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fffd7-178">To run the complex approval scenario</span></span>

1. <span data-ttu-id="fffd7-179">Yönetici izniyle bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-179">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="fffd7-180">Çözümü içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="fffd7-180">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="fffd7-181">ApprovalClient\Bin\Debug klasörüne gidin ve ApprovalClient. exe ' nin dört örneğini yürütün.</span><span class="sxs-lookup"><span data-stu-id="fffd7-181">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="fffd7-182">**Keşfet**' e tıklayın, **abone ol** düğmesi etkin olana kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="fffd7-182">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="fffd7-183">Herhangi bir Kullanıcı adı yazın ve **abone ol**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-183">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="fffd7-184">Bir istemci kullanımı `UserType1`için, iki kullanım türü `UserType2`ve son kullanımda `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="fffd7-184">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>

6. <span data-ttu-id="fffd7-185">`UserType1` İstemcide, açılan menüden tek onay türünü seçin ve bir belge adı ve içerik yazın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-185">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="fffd7-186">**Onay iste**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-186">Click **Request Approval**.</span></span>

7. <span data-ttu-id="fffd7-187">`UserType2` İstemcilerde onay bekleyen bir belge görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-187">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="fffd7-188">Seçin ve **Onayla**' ya basın, belge `UserType3` istemciye geçirilir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-188">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>

    <span data-ttu-id="fffd7-189">Belge ilk `UserType2` çekirdek tarafından onaylanırsa, belge `UserType3` istemciye geçirilir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-189">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>

8. <span data-ttu-id="fffd7-190">Belgeyi `UserType3` istemciden onaylayın veya reddedin.</span><span class="sxs-lookup"><span data-stu-id="fffd7-190">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="fffd7-191">Sonuçların `UserType1` istemcide gösterilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fffd7-191">The results should show in the `UserType1` client.</span></span>

##### <a name="to-clean-up"></a><span data-ttu-id="fffd7-192">Temizlemek için</span><span class="sxs-lookup"><span data-stu-id="fffd7-192">To clean up</span></span>

1. <span data-ttu-id="fffd7-193">Visual Studio 2010 komut isteminden, Belgetapprovalprocess klasörüne gidin ve Cleanup. cmd ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fffd7-193">From a Visual Studio 2010 command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>
