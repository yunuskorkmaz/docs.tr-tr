---
title: Belge Onay İşlemi
description: Bu örnek, bir belge onay işlemi senaryosunda birçok Windows Workflow Foundation ve Windows Communication Foundation özelliği gösterir.
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: 18b4f978e9234daf22395f0d2f6f0889d0edf966
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421416"
---
# <a name="document-approval-process"></a><span data-ttu-id="b7a79-103">Belge Onay İşlemi</span><span class="sxs-lookup"><span data-stu-id="b7a79-103">Document Approval Process</span></span>

<span data-ttu-id="b7a79-104">Bu örnek, birçok Windows Workflow Foundation (WF) ve Windows Communication Foundation (WCF) özelliklerinin birlikte kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-104">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="b7a79-105">Birlikte bir belge onay süreci senaryosu uygular.</span><span class="sxs-lookup"><span data-stu-id="b7a79-105">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="b7a79-106">İstemci uygulaması, belgeleri onay ve onaylama için gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-106">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="b7a79-107">İstemciler arasındaki iletişimleri kolaylaştırmak ve onay işleminin kurallarını zorlamak için bir onay Yöneticisi uygulaması vardır.</span><span class="sxs-lookup"><span data-stu-id="b7a79-107">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="b7a79-108">Onay süreci, çeşitli onay türlerini yürütebilmesi için bir iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="b7a79-108">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="b7a79-109">Tek bir onay, bir çekirdek onayı (bir onaylayanlar kümesinin yüzdesi) ve bir dizideki bir çekirdekte ve tek bir onaydan oluşan karmaşık bir onay işlemi almak için etkinlik vardır.</span><span class="sxs-lookup"><span data-stu-id="b7a79-109">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b7a79-110">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b7a79-111">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b7a79-111">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b7a79-112">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b7a79-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b7a79-113">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b7a79-113">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`

## <a name="sample-details"></a><span data-ttu-id="b7a79-114">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b7a79-114">Sample Details</span></span>

<span data-ttu-id="b7a79-115">Aşağıdaki grafik belge onay süreci iş akışını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="b7a79-115">The following graphic demonstrates the document approval process workflow:</span></span>

![Bir belge onay işlemi iş akışı](./media/document-approval-process/document-approval-process.jpg)

<span data-ttu-id="b7a79-117">İstemci perspektifinden, onay işlemi aşağıdaki gibi çalışır:</span><span class="sxs-lookup"><span data-stu-id="b7a79-117">From the client's perspective, the approval process functions as follows:</span></span>

1. <span data-ttu-id="b7a79-118">İstemci, onay işlem sisteminde bir kullanıcı olarak abone olur.</span><span class="sxs-lookup"><span data-stu-id="b7a79-118">A client subscribes to be a user in the approval process system.</span></span>

2. <span data-ttu-id="b7a79-119">WCF istemcisi, onay Yöneticisi uygulaması tarafından barındırılan bir WCF hizmetine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-119">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>

3. <span data-ttu-id="b7a79-120">İstemciye benzersiz bir kullanıcı KIMLIĞI döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b7a79-120">A unique user ID is returned to the client.</span></span> <span data-ttu-id="b7a79-121">İstemci artık onay işlemlerine katılabilir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-121">The client can now participate in approval processes.</span></span>

4. <span data-ttu-id="b7a79-122">Bir istemci birleştirildikten sonra tek, çekirdek veya karmaşık onay süreçlerini kullanarak bir belgeyi onaya gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-122">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>

5. <span data-ttu-id="b7a79-123">İstemci arabirimindeki bir düğmeye tıkladıktan sonra istemci Iş akışı hizmet ana bilgisayarında bir iş akışı örneği başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="b7a79-123">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>

6. <span data-ttu-id="b7a79-124">İş akışı, onay Yöneticisi uygulamasına bir onay isteği gönderir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-124">The workflow sends an approval request to the approval manager application.</span></span>

7. <span data-ttu-id="b7a79-125">Workflow Manager, bir onay işlemini göstermek için kendi tarafında bir iş akışı başlatır.</span><span class="sxs-lookup"><span data-stu-id="b7a79-125">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>

8. <span data-ttu-id="b7a79-126">Yönetici onayı iş akışı yürütüldükten sonra sonuçlar istemciye geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-126">Once the manager approval workflow executes, the results are sent back to the client.</span></span>

9. <span data-ttu-id="b7a79-127">İstemci sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b7a79-127">The client displays the results.</span></span>

10. <span data-ttu-id="b7a79-128">İstemci bir onay isteği alabilir ve herhangi bir zamanda istek için yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-128">A client may receive an approval request and respond to the request at any point in time.</span></span>

11. <span data-ttu-id="b7a79-129">İstemcide barındırılan bir WCF hizmeti, onay Yöneticisi uygulamasından bir onay isteği alabilir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-129">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>

12. <span data-ttu-id="b7a79-130">Belge bilgileri, gözden geçirilmek üzere istemcisinde sunulur.</span><span class="sxs-lookup"><span data-stu-id="b7a79-130">The document information is presented on the client for review.</span></span>

13. <span data-ttu-id="b7a79-131">Kullanıcı belgeyi onaylayabilir veya reddedebilir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-131">The user can approve or reject the document.</span></span>

14. <span data-ttu-id="b7a79-132">Bir WCF istemcisi, bir onay yanıtını onay Yöneticisi uygulamasına geri göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7a79-132">A WCF client is used to send an approval response back to the approval manager application.</span></span>

<span data-ttu-id="b7a79-133">Onay Yöneticisi uygulamasının görünüm noktasından, onay işlemi aşağıdaki gibi çalışır:</span><span class="sxs-lookup"><span data-stu-id="b7a79-133">From the approval manager application’s point of view, the approval process functions as follows:</span></span>

1. <span data-ttu-id="b7a79-134">İstemci onay işlem sistemine katılmayı ister.</span><span class="sxs-lookup"><span data-stu-id="b7a79-134">A client requests to participate to the approval process system.</span></span>

2. <span data-ttu-id="b7a79-135">Onay yöneticisinde bir WCF hizmeti, onay işlem sisteminin bir parçası olarak bir istek alır.</span><span class="sxs-lookup"><span data-stu-id="b7a79-135">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>

3. <span data-ttu-id="b7a79-136">İstemci için benzersiz bir KIMLIK oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b7a79-136">A unique ID is generated for the client.</span></span> <span data-ttu-id="b7a79-137">Kullanıcı bilgileri bir veritabanında depolanır.</span><span class="sxs-lookup"><span data-stu-id="b7a79-137">The user information is stored in a database.</span></span>

4. <span data-ttu-id="b7a79-138">Benzersiz KIMLIK kullanıcıya geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-138">The unique ID is sent back to the user.</span></span>

5. <span data-ttu-id="b7a79-139">Bir onay isteği alma.</span><span class="sxs-lookup"><span data-stu-id="b7a79-139">An approval request is receive.</span></span> <span data-ttu-id="b7a79-140">Onay Yöneticisi bir onay işlemi yürütür.</span><span class="sxs-lookup"><span data-stu-id="b7a79-140">The approval manager executes an approval process.</span></span>

6. <span data-ttu-id="b7a79-141">Onay Yöneticisi tarafından yeni bir iş akışı başlatılıyor onay isteği alındı.</span><span class="sxs-lookup"><span data-stu-id="b7a79-141">An approval request is received by the approval manager, starting a new workflow.</span></span>

7. <span data-ttu-id="b7a79-142">İsteğin türüne (basit, çekirdek veya karmaşık) bağlı olarak farklı bir etkinlik yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b7a79-142">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>

8. <span data-ttu-id="b7a79-143">İlişki ile gönderme ve alma etkinlikleri, gözden geçirme için istemciye onay isteği göndermek ve yanıtı almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7a79-143">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>

9. <span data-ttu-id="b7a79-144">Onay süreci iş akışının sonucu istemciye gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-144">The result of the approval process workflow is sent to the client.</span></span>

## <a name="using-the-sample"></a><span data-ttu-id="b7a79-145">Örneği kullanma</span><span class="sxs-lookup"><span data-stu-id="b7a79-145">Using the Sample</span></span>

##### <a name="to-set-up-the-database"></a><span data-ttu-id="b7a79-146">Veritabanını ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b7a79-146">To set up the database</span></span>

1. <span data-ttu-id="b7a79-147">Yönetici ayrıcalıklarıyla açılan bir Visual Studio 2010 komut isteminden, bu belgeleyici klasörüne gidin ve Setup. cmd ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-147">From a Visual Studio 2010 command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>

##### <a name="to-set-up-the-application"></a><span data-ttu-id="b7a79-148">Uygulamayı ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b7a79-148">To set up the application</span></span>

1. <span data-ttu-id="b7a79-149">Visual Studio 2010 kullanarak, Belgetapprovalprocess. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-149">Using Visual Studio 2010, open the DocumentApprovalProcess.sln solution file.</span></span>

2. <span data-ttu-id="b7a79-150">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-150">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="b7a79-151">Çözümü çalıştırmak için **Çözüm Gezgini** ApprovalManager projesine sağ tıklayıp sağ tıklama menüsünden **Hata Ayıkla** -> Yeni örnek**Başlat** ' a tıklayarak onay Yöneticisi uygulamasını başlatın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-151">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>

    <span data-ttu-id="b7a79-152">Yöneticinin çıkışının, olduğunu bilmenizi sağlamak için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7a79-152">Wait for the manager’s output to let you know that it is ready.</span></span>

##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="b7a79-153">Tek onay senaryosunu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b7a79-153">To run the single approval scenario</span></span>

1. <span data-ttu-id="b7a79-154">Yönetici izniyle bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-154">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="b7a79-155">Çözümü içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="b7a79-155">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="b7a79-156">ApprovalClient\Bin\Debug klasörüne gidin ve ApprovalClient. exe ' nin iki örneğini yürütün.</span><span class="sxs-lookup"><span data-stu-id="b7a79-156">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="b7a79-157">**Keşfet**' e tıklayın, **abone ol** düğmesi etkin olana kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7a79-157">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="b7a79-158">Herhangi bir Kullanıcı adı yazın ve **abone ol**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-158">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="b7a79-159">Bir istemci için `UserType1` ve diğer türü kullanın `UserType2` .</span><span class="sxs-lookup"><span data-stu-id="b7a79-159">For one client, use `UserType1` and the other type `UserType2`.</span></span>

6. <span data-ttu-id="b7a79-160">`UserType1`İstemcide, açılan menüden tek onay türünü seçin ve bir belge adı ve içerik yazın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-160">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="b7a79-161">**Onay iste**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-161">Click **Request Approval**.</span></span>

7. <span data-ttu-id="b7a79-162">`UserType2`İstemcide onay bekleyen bir belge görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-162">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="b7a79-163">Seçin ve **Onayla** veya **Reddet**' e basın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-163">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="b7a79-164">Sonuçların istemcide gösterilmesi gerekir `UserType1` .</span><span class="sxs-lookup"><span data-stu-id="b7a79-164">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="b7a79-165">Çekirdek onay senaryosunu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b7a79-165">To run the quorum approval scenario</span></span>

1. <span data-ttu-id="b7a79-166">Yönetici izniyle bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-166">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="b7a79-167">Çözümü içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="b7a79-167">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="b7a79-168">ApprovalClient\Bin\Debug klasörüne gidin ve ApprovalClient. exe ' nin üç örneğini yürütün.</span><span class="sxs-lookup"><span data-stu-id="b7a79-168">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="b7a79-169">**Keşfet**' e tıklayın, **abone ol** düğmesi etkin olana kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7a79-169">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="b7a79-170">Herhangi bir Kullanıcı adı yazın ve **abone ol**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-170">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="b7a79-171">Bir istemci kullanımı `UserType1` ve diğer iki tür için `UserType2` .</span><span class="sxs-lookup"><span data-stu-id="b7a79-171">For one client use `UserType1` and the other two type `UserType2`.</span></span>

6. <span data-ttu-id="b7a79-172">`UserType1`İstemcide, açılan menüden çekirdek onay türünü seçin ve bir belge adı ve içerik yazın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-172">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="b7a79-173">**Onay iste**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-173">Click **Request Approval**.</span></span> <span data-ttu-id="b7a79-174">Bu, iki `UserType2` istemcinin belgeyi onaylamasını veya reddetmesini ister.</span><span class="sxs-lookup"><span data-stu-id="b7a79-174">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="b7a79-175">Her iki istemcinin `UserType2` da yanıt vermesi gerekir, ancak belgeyi onaylanacak şekilde yalnızca bir istemci onaylaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-175">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>

7. <span data-ttu-id="b7a79-176">`UserType2`İstemcilerde onay bekleyen bir belge görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-176">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="b7a79-177">Seçin ve **Onayla** veya **Reddet**' e basın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-177">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="b7a79-178">Sonuçların istemcide gösterilmesi gerekir `UserType1` .</span><span class="sxs-lookup"><span data-stu-id="b7a79-178">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="b7a79-179">Karmaşık onay senaryosunu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b7a79-179">To run the complex approval scenario</span></span>

1. <span data-ttu-id="b7a79-180">Yönetici izniyle bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-180">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="b7a79-181">Çözümü içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="b7a79-181">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="b7a79-182">ApprovalClient\Bin\Debug klasörüne gidin ve ApprovalClient. exe ' nin dört örneğini yürütün.</span><span class="sxs-lookup"><span data-stu-id="b7a79-182">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="b7a79-183">**Keşfet**' e tıklayın, **abone ol** düğmesi etkin olana kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7a79-183">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="b7a79-184">Herhangi bir Kullanıcı adı yazın ve **abone ol**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-184">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="b7a79-185">Bir istemci kullanımı için `UserType1` , iki kullanım türü `UserType2` ve son kullanımda `UserType3` .</span><span class="sxs-lookup"><span data-stu-id="b7a79-185">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>

6. <span data-ttu-id="b7a79-186">`UserType1`İstemcide, açılan menüden tek onay türünü seçin ve bir belge adı ve içerik yazın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-186">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="b7a79-187">**Onay iste**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-187">Click **Request Approval**.</span></span>

7. <span data-ttu-id="b7a79-188">`UserType2`İstemcilerde onay bekleyen bir belge görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-188">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="b7a79-189">Seçin ve **Onayla**' ya basın, belge `UserType3` istemciye geçirilir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-189">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>

    <span data-ttu-id="b7a79-190">Belge ilk çekirdek tarafından onaylanırsa `UserType2` , belge `UserType3` istemciye geçirilir.</span><span class="sxs-lookup"><span data-stu-id="b7a79-190">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>

8. <span data-ttu-id="b7a79-191">Belgeyi istemciden onaylayın veya reddedin `UserType3` .</span><span class="sxs-lookup"><span data-stu-id="b7a79-191">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="b7a79-192">Sonuçların istemcide gösterilmesi gerekir `UserType1` .</span><span class="sxs-lookup"><span data-stu-id="b7a79-192">The results should show in the `UserType1` client.</span></span>

##### <a name="to-clean-up"></a><span data-ttu-id="b7a79-193">Temizlemek için</span><span class="sxs-lookup"><span data-stu-id="b7a79-193">To clean up</span></span>

1. <span data-ttu-id="b7a79-194">Visual Studio 2010 komut isteminden, Belgetapprovalprocess klasörüne gidin ve Cleanup. cmd ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b7a79-194">From a Visual Studio 2010 command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>
