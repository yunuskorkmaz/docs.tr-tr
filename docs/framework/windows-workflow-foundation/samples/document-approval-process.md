---
title: Belge Onay İşlemi
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: dfc2e0a12d053733823427ac50066b1e4a0f97aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770405"
---
# <a name="document-approval-process"></a><span data-ttu-id="ee51c-102">Belge Onay İşlemi</span><span class="sxs-lookup"><span data-stu-id="ee51c-102">Document Approval Process</span></span>
<span data-ttu-id="ee51c-103">Bu örnek, birlikte birçok Windows Workflow Foundation (WF) ve Windows Communication Foundation (WCF) özelliklerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-103">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="ee51c-104">Birlikte bir belge onay işlemi senaryosu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="ee51c-104">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="ee51c-105">Bir istemci uygulaması, belgeler için onay gönderin ve onaylayın belgeleri.</span><span class="sxs-lookup"><span data-stu-id="ee51c-105">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="ee51c-106">Kurallar onay işlemi uygular ve istemciler arasındaki iletişimi kolaylaştırmak için bir onay Yöneticisi uygulaması yok.</span><span class="sxs-lookup"><span data-stu-id="ee51c-106">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="ee51c-107">Onay, onay çeşitli yürütebilen bir iş akışı işlemidir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-107">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="ee51c-108">Etkinlikler, tek bir onay, çekirdek onay (onaylayanlara kümesini yüzdesi) ve bir çekirdek ve dizideki tek onay içeren bir karmaşık bir onay işlemi mevcut.</span><span class="sxs-lookup"><span data-stu-id="ee51c-108">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="ee51c-109">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="ee51c-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ee51c-110">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ee51c-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ee51c-111">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ee51c-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee51c-112">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ee51c-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a><span data-ttu-id="ee51c-113">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="ee51c-113">Sample Details</span></span>  
 <span data-ttu-id="ee51c-114">Aşağıdaki grafikte belge onay işlemi iş akışı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ee51c-114">The following graphic demonstrates the document approval process workflow:</span></span>  
  
 ![Bir belge onay işlemi iş akışı](./media/document-approval-process/document-approval-process.jpg)  
  
 <span data-ttu-id="ee51c-116">İstemcinin açısından bakıldığında, onay işlemi işlevleri gibi:</span><span class="sxs-lookup"><span data-stu-id="ee51c-116">From the client's perspective, the approval process functions as follows:</span></span>  
  
1. <span data-ttu-id="ee51c-117">Bir istemci, bir kullanıcı onayı işlemi sistemde olacak şekilde abone olur.</span><span class="sxs-lookup"><span data-stu-id="ee51c-117">A client subscribes to be a user in the approval process system.</span></span>  
  
2. <span data-ttu-id="ee51c-118">Bir WCF istemcisi onay Yöneticisi uygulama tarafından barındırılan bir WCF hizmetine gönderir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-118">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>  
  
3. <span data-ttu-id="ee51c-119">Benzersiz bir kullanıcı kimliği, istemciye döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ee51c-119">A unique user ID is returned to the client.</span></span> <span data-ttu-id="ee51c-120">İstemci, artık onay işlemde katılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-120">The client can now participate in approval processes.</span></span>  
  
4. <span data-ttu-id="ee51c-121">Birleştirilmiş sonra bir istemci bir belge onay tek kullanarak, çekirdek veya karmaşık onaylama işlemlerini gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee51c-121">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>  
  
5. <span data-ttu-id="ee51c-122">İstemcinin arabiriminde bir düğmeye tıkladı, bir iş akışı örneği iş akışı hizmeti ana bilgisayarı istemci olarak başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="ee51c-122">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>  
  
6. <span data-ttu-id="ee51c-123">İş akışı, onay manager uygulaması için bir onay isteği gönderir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-123">The workflow sends an approval request to the approval manager application.</span></span>  
  
7. <span data-ttu-id="ee51c-124">İş Akışı Yöneticisi, bir onay işlemi temsil etmek için kendi tarafında bir iş akışı başlatır.</span><span class="sxs-lookup"><span data-stu-id="ee51c-124">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>  
  
8. <span data-ttu-id="ee51c-125">Yönetici onayı iş akışı yürüten sonra sonuçları istemciye geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-125">Once the manager approval workflow executes, the results are sent back to the client.</span></span>  
  
9. <span data-ttu-id="ee51c-126">İstemci, sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ee51c-126">The client displays the results.</span></span>  
  
10. <span data-ttu-id="ee51c-127">Bir istemci, bir onay isteği alır ve herhangi bir noktada isteğine zamanında yanıt.</span><span class="sxs-lookup"><span data-stu-id="ee51c-127">A client may receive an approval request and respond to the request at any point in time.</span></span>  
  
11. <span data-ttu-id="ee51c-128">İstemci üzerinde barındırılan bir WCF hizmeti bir onay isteği onay Yöneticisi uygulamadan alabilir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-128">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>  
  
12. <span data-ttu-id="ee51c-129">Belge bilgilerini gözden geçirme için istemcide sunulur.</span><span class="sxs-lookup"><span data-stu-id="ee51c-129">The document information is presented on the client for review.</span></span>  
  
13. <span data-ttu-id="ee51c-130">Kullanıcı onaylayabileceğiniz veya reddedebileceğiniz belge.</span><span class="sxs-lookup"><span data-stu-id="ee51c-130">The user can approve or reject the document.</span></span>  
  
14. <span data-ttu-id="ee51c-131">Bir WCF istemcisi, bir onay yanıtı onay Yöneticisi uygulamaya göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee51c-131">A WCF client is used to send an approval response back to the approval manager application.</span></span>  
  
 <span data-ttu-id="ee51c-132">Onay Yöneticisi uygulama açısından bakıldığında, onay işlemi işlevleri gibi:</span><span class="sxs-lookup"><span data-stu-id="ee51c-132">From the approval manager application’s point of view, the approval process functions as follows:</span></span>  
  
1. <span data-ttu-id="ee51c-133">Bir istemci, onay işlemi sisteme katılmak ister.</span><span class="sxs-lookup"><span data-stu-id="ee51c-133">A client requests to participate to the approval process system.</span></span>  
  
2. <span data-ttu-id="ee51c-134">Onay Yöneticisi bir WCF hizmeti bir isteği onaylama işlemi sisteminin bir parçası olarak alır.</span><span class="sxs-lookup"><span data-stu-id="ee51c-134">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>  
  
3. <span data-ttu-id="ee51c-135">İstemci için benzersiz bir kimlik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ee51c-135">A unique ID is generated for the client.</span></span> <span data-ttu-id="ee51c-136">Kullanıcı bilgilerini bir veritabanında depolanır.</span><span class="sxs-lookup"><span data-stu-id="ee51c-136">The user information is stored in a database.</span></span>  
  
4. <span data-ttu-id="ee51c-137">Benzersiz kimliği kullanıcıya geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-137">The unique ID is sent back to the user.</span></span>  
  
5. <span data-ttu-id="ee51c-138">Bir onay isteği alma ' dir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-138">An approval request is receive.</span></span> <span data-ttu-id="ee51c-139">Onay Yöneticisi bir onay işlemi yürütür.</span><span class="sxs-lookup"><span data-stu-id="ee51c-139">The approval manager executes an approval process.</span></span>  
  
6. <span data-ttu-id="ee51c-140">Bir onay isteği yeni bir iş akışı başlatılıyorsa onay Yöneticisi tarafından alınır.</span><span class="sxs-lookup"><span data-stu-id="ee51c-140">An approval request is received by the approval manager, starting a new workflow.</span></span>  
  
7. <span data-ttu-id="ee51c-141">(Basit, çekirdek veya karmaşık) istek türüne bağlı olarak farklı bir etkinlik yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ee51c-141">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>  
  
8. <span data-ttu-id="ee51c-142">Gönderme ve alma bağıntı etkinliklerle onay isteğini gözden geçirme için istemci gönderme ve yanıt almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee51c-142">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>  
  
9. <span data-ttu-id="ee51c-143">Onay işlemi iş akışı sonucu istemciye gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-143">The result of the approval process workflow is sent to the client.</span></span>  
  
## <a name="using-the-sample"></a><span data-ttu-id="ee51c-144">Örnek kullanma</span><span class="sxs-lookup"><span data-stu-id="ee51c-144">Using the Sample</span></span>  
  
##### <a name="to-set-up-the-database"></a><span data-ttu-id="ee51c-145">Veritabanı ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ee51c-145">To set up the database</span></span>  
  
1. <span data-ttu-id="ee51c-146">Yönetici ayrıcalıklarıyla açılan bir Visual Studio 2010 Komut isteminde bu DocumentApprovalProcess klasörüne gidin ve Setup.cmd'yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ee51c-146">From a Visual Studio 2010 command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>  
  
##### <a name="to-set-up-the-application"></a><span data-ttu-id="ee51c-147">Uygulamayı kurmak için</span><span class="sxs-lookup"><span data-stu-id="ee51c-147">To set up the application</span></span>  
  
1. <span data-ttu-id="ee51c-148">Visual Studio 2010 kullanarak DocumentApprovalProcess.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="ee51c-148">Using Visual Studio 2010, open the DocumentApprovalProcess.sln solution file.</span></span>  
  
2. <span data-ttu-id="ee51c-149">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="ee51c-149">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="ee51c-150">Çözümü çalıştırmak için ApprovalManager projeye sağ tıklayarak onay Yöneticisi uygulamasını başlatma **Çözüm Gezgini** tıklayıp **hata ayıklama**->**Başlat**  sağ tıklatma menüsünden Yeni bir örneği.</span><span class="sxs-lookup"><span data-stu-id="ee51c-150">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>  
  
     <span data-ttu-id="ee51c-151">Hazır olduğunu bildiren manager'ın çıktı için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="ee51c-151">Wait for the manager’s output to let you know that it is ready.</span></span>  
  
##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="ee51c-152">Tek onayı senaryosu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ee51c-152">To run the single approval scenario</span></span>  
  
1. <span data-ttu-id="ee51c-153">Yönetici izni olan bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="ee51c-153">Open a command prompt with administrator permission.</span></span>  
  
2. <span data-ttu-id="ee51c-154">Çözümü içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="ee51c-154">Navigate to the directory that contains the solution.</span></span>  
  
3. <span data-ttu-id="ee51c-155">ApprovalClient\Bin\Debug klasöre gidin ve iki örneğini ApprovalClient.exe yürütün.</span><span class="sxs-lookup"><span data-stu-id="ee51c-155">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>  
  
4. <span data-ttu-id="ee51c-156">Tıklayın **Bul**, bekle **abone** düğmesi etkinleşir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-156">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5. <span data-ttu-id="ee51c-157">Herhangi bir kullanıcı adı yazın ve tıklayın **abone**.</span><span class="sxs-lookup"><span data-stu-id="ee51c-157">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="ee51c-158">Bir istemci için kullanmak `UserType1` ve diğer tür `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="ee51c-158">For one client, use `UserType1` and the other type `UserType2`.</span></span>  
  
6. <span data-ttu-id="ee51c-159">İçinde `UserType1` tek onay açılan menüden yazıp bir belge adı ve içerik istemci, seçin.</span><span class="sxs-lookup"><span data-stu-id="ee51c-159">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="ee51c-160">Tıklayın **onay isteği**.</span><span class="sxs-lookup"><span data-stu-id="ee51c-160">Click **Request Approval**.</span></span>  
  
7. <span data-ttu-id="ee51c-161">İçinde `UserType2` istemci, onay bekleyen bir belge görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-161">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="ee51c-162">Görseli seçip **onaylama** veya **Reddet**.</span><span class="sxs-lookup"><span data-stu-id="ee51c-162">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="ee51c-163">Sonuçlar göstermesi gerekir `UserType1` istemci.</span><span class="sxs-lookup"><span data-stu-id="ee51c-163">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="ee51c-164">Çekirdek onayı senaryosu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ee51c-164">To run the quorum approval scenario</span></span>  
  
1. <span data-ttu-id="ee51c-165">Yönetici izni olan bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="ee51c-165">Open a command prompt with administrator permission.</span></span>  
  
2. <span data-ttu-id="ee51c-166">Çözümü içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="ee51c-166">Navigate to the directory that contains the solution.</span></span>  
  
3. <span data-ttu-id="ee51c-167">ApprovalClient\Bin\Debug klasöre gidin ve ApprovalClient.exe üç örneği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ee51c-167">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>  
  
4. <span data-ttu-id="ee51c-168">Tıklayın **Bul**, bekle **abone** düğmesi etkinleşir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-168">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5. <span data-ttu-id="ee51c-169">Herhangi bir kullanıcı adı yazın ve tıklayın **abone**.</span><span class="sxs-lookup"><span data-stu-id="ee51c-169">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="ee51c-170">Bir istemci için kullanmak `UserType1` ve diğer iki tür `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="ee51c-170">For one client use `UserType1` and the other two type `UserType2`.</span></span>  
  
6. <span data-ttu-id="ee51c-171">İçinde `UserType1` çekirdek onay açılan menüden yazıp bir belge adı ve içerik istemci, seçin.</span><span class="sxs-lookup"><span data-stu-id="ee51c-171">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="ee51c-172">Tıklayın **onay isteği**.</span><span class="sxs-lookup"><span data-stu-id="ee51c-172">Click **Request Approval**.</span></span> <span data-ttu-id="ee51c-173">Bu isteyen iki `UserType2` istemcileri onaylayabileceğiniz veya belge.</span><span class="sxs-lookup"><span data-stu-id="ee51c-173">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="ee51c-174">Her ikisi de while `UserType2` istemcilerin gerekir yanıt, yalnızca bir istemci onaylanması için belgeyi onaylamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-174">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>  
  
7. <span data-ttu-id="ee51c-175">İçinde `UserType2` istemciler, onay bekleyen bir belge görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-175">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="ee51c-176">Görseli seçip **onaylama** veya **Reddet**.</span><span class="sxs-lookup"><span data-stu-id="ee51c-176">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="ee51c-177">Sonuçlar göstermesi gerekir `UserType1` istemci.</span><span class="sxs-lookup"><span data-stu-id="ee51c-177">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="ee51c-178">Karmaşık onayı senaryosu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ee51c-178">To run the complex approval scenario</span></span>  
  
1. <span data-ttu-id="ee51c-179">Yönetici izni olan bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="ee51c-179">Open a command prompt with administrator permission.</span></span>  
  
2. <span data-ttu-id="ee51c-180">Çözümü içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="ee51c-180">Navigate to the directory that contains the solution.</span></span>  
  
3. <span data-ttu-id="ee51c-181">ApprovalClient\Bin\Debug klasöre gidin ve dört örneklerini ApprovalClient.exe yürütün.</span><span class="sxs-lookup"><span data-stu-id="ee51c-181">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>  
  
4. <span data-ttu-id="ee51c-182">Tıklayın **Bul**, bekle **abone** düğmesi etkinleşir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-182">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5. <span data-ttu-id="ee51c-183">Herhangi bir kullanıcı adı yazın ve tıklayın **abone**.</span><span class="sxs-lookup"><span data-stu-id="ee51c-183">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="ee51c-184">Bir istemci için kullanmak `UserType1`, iki tür kullanan `UserType2`ve son kullanımda `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="ee51c-184">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>  
  
6. <span data-ttu-id="ee51c-185">İçinde `UserType1` tek onay açılan menüden yazıp bir belge adı ve içerik istemci, seçin.</span><span class="sxs-lookup"><span data-stu-id="ee51c-185">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="ee51c-186">Tıklayın **onay isteği**.</span><span class="sxs-lookup"><span data-stu-id="ee51c-186">Click **Request Approval**.</span></span>  
  
7. <span data-ttu-id="ee51c-187">İçinde `UserType2` istemciler, onay bekleyen bir belge görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ee51c-187">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="ee51c-188">Görseli seçip **onaylama**, belge gönderilirse `UserType3` istemci.</span><span class="sxs-lookup"><span data-stu-id="ee51c-188">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>  
  
     <span data-ttu-id="ee51c-189">İlk belge onaylanırsa `UserType2` çekirdek, belge geçirildiğinde `UserType3` istemci.</span><span class="sxs-lookup"><span data-stu-id="ee51c-189">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>  
  
8. <span data-ttu-id="ee51c-190">Onaylama veya reddetme belgeden `UserType3` istemci.</span><span class="sxs-lookup"><span data-stu-id="ee51c-190">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="ee51c-191">Sonuçlar göstermesi gerekir `UserType1` istemci.</span><span class="sxs-lookup"><span data-stu-id="ee51c-191">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-clean-up"></a><span data-ttu-id="ee51c-192">Temizlemek için</span><span class="sxs-lookup"><span data-stu-id="ee51c-192">To clean up</span></span>  
  
1. <span data-ttu-id="ee51c-193">Bir Visual Studio 2010 komut isteminden DocumentApprovalProcess klasöre gidin ve Cleanup.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ee51c-193">From a Visual Studio 2010 command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>
