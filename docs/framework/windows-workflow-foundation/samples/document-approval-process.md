---
title: Belge onay işlemi
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 45a6a6b2cd3bf790c8170cef6a6111ee7dd0b27b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="document-approval-process"></a><span data-ttu-id="fe235-102">Belge onay işlemi</span><span class="sxs-lookup"><span data-stu-id="fe235-102">Document Approval Process</span></span>
<span data-ttu-id="fe235-103">Bu örnek çok sayıda Windows Workflow Foundation (WF), kullanımını gösterir ve [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] özellikleri birlikte.</span><span class="sxs-lookup"><span data-stu-id="fe235-103">This sample demonstrates the use of many Windows Workflow Foundation (WF) and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] features together.</span></span> <span data-ttu-id="fe235-104">Birlikte bir belge onay işlemi senaryosu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fe235-104">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="fe235-105">Bir istemci uygulaması onay için belge gönderme ve belgeleri onaylayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe235-105">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="fe235-106">Onay Yöneticisi uygulamanın istemciler arasındaki iletişimi kolaylaştırmak için ve onay işlemi kurallarını zorunlu tutmak için bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe235-106">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="fe235-107">Onay, onay çeşitli türlerde yürütebilir bir iş akışı işlemidir.</span><span class="sxs-lookup"><span data-stu-id="fe235-107">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="fe235-108">Etkinlikleri tek bir onay, çekirdek onay (onaylayanlar kümesi yüzdesi) ve çekirdek ve bir sırada tek onay oluşan bir karmaşık onay işlemi almak için mevcut.</span><span class="sxs-lookup"><span data-stu-id="fe235-108">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fe235-109">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe235-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fe235-110">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fe235-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fe235-111">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="fe235-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fe235-112">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fe235-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a><span data-ttu-id="fe235-113">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="fe235-113">Sample Details</span></span>  
 <span data-ttu-id="fe235-114">Aşağıdaki grafikte belge onay işlem akışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fe235-114">The following graphic demonstrates the document approval process workflow.</span></span>  
  
 <span data-ttu-id="fe235-115">![Bir belge onay işlemi iş akışını](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")</span><span class="sxs-lookup"><span data-stu-id="fe235-115">![A document approval process workflow](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")</span></span>  
  
 <span data-ttu-id="fe235-116">İstemcinin açısından bakıldığında, onay işlemini işlevleri gibi:</span><span class="sxs-lookup"><span data-stu-id="fe235-116">From the client's perspective, the approval process functions as follows:</span></span>  
  
1.  <span data-ttu-id="fe235-117">Bir istemci, bir kullanıcının onay işlemi sistemde olması için abone olur.</span><span class="sxs-lookup"><span data-stu-id="fe235-117">A client subscribes to be a user in the approval process system.</span></span>  
  
2.  <span data-ttu-id="fe235-118">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcinin gönderdiği için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] onay Yöneticisi uygulaması tarafından barındırılan hizmeti.</span><span class="sxs-lookup"><span data-stu-id="fe235-118">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client sends to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted by the approval manager application.</span></span>  
  
3.  <span data-ttu-id="fe235-119">Benzersiz bir kullanıcı kimliği istemciye döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fe235-119">A unique user ID is returned to the client.</span></span> <span data-ttu-id="fe235-120">İstemci onayı işlemlerde şimdi katılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe235-120">The client can now participate in approval processes.</span></span>  
  
4.  <span data-ttu-id="fe235-121">Birleştirilmiş sonra bir istemci onayı tek kullanarak, çekirdek veya karmaşık onay işlemleri için bir belge gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="fe235-121">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>  
  
5.  <span data-ttu-id="fe235-122">İstemcinin arabiriminde düğmesine tıklandığında, bir iş akışı örneği iş akışı hizmeti ana bilgisayarı istemci olarak başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="fe235-122">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>  
  
6.  <span data-ttu-id="fe235-123">İş akışı onay manager uygulaması için bir onay isteği gönderir.</span><span class="sxs-lookup"><span data-stu-id="fe235-123">The workflow sends an approval request to the approval manager application.</span></span>  
  
7.  <span data-ttu-id="fe235-124">İş Akışı Yöneticisi iş akışı bir onay işlemini temsil edecek şekilde kendi tarafında başlatır.</span><span class="sxs-lookup"><span data-stu-id="fe235-124">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>  
  
8.  <span data-ttu-id="fe235-125">Yöneticisi Onayı iş akışı yürütür sonra sonuçları istemcisine geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="fe235-125">Once the manager approval workflow executes, the results are sent back to the client.</span></span>  
  
9. <span data-ttu-id="fe235-126">İstemci sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fe235-126">The client displays the results.</span></span>  
  
10. <span data-ttu-id="fe235-127">Bir istemci, bir onay isteği alır ve herhangi bir noktada isteğine zamanında yanıt.</span><span class="sxs-lookup"><span data-stu-id="fe235-127">A client may receive an approval request and respond to the request at any point in time.</span></span>  
  
11. <span data-ttu-id="fe235-128">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci üzerinde barındırılan hizmeti, bir onay isteği onayı manager uygulamasından alabilir.</span><span class="sxs-lookup"><span data-stu-id="fe235-128">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted on the client can receive an approval request from the approval manager application.</span></span>  
  
12. <span data-ttu-id="fe235-129">Belge bilgilerini gözden geçirme için istemcide sunulur.</span><span class="sxs-lookup"><span data-stu-id="fe235-129">The document information is presented on the client for review.</span></span>  
  
13. <span data-ttu-id="fe235-130">Kullanıcı onaylayabilir veya belgeyi reddeder.</span><span class="sxs-lookup"><span data-stu-id="fe235-130">The user can approve or reject the document.</span></span>  
  
14. <span data-ttu-id="fe235-131">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, bir onay yanıtı onay Yöneticisi uygulamaya geri göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe235-131">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client is used to send an approval response back to the approval manager application.</span></span>  
  
 <span data-ttu-id="fe235-132">Onay Yöneticisi uygulamanın açısından bakıldığında, onay işlemini işlevleri gibi:</span><span class="sxs-lookup"><span data-stu-id="fe235-132">From the approval manager application’s point of view, the approval process functions as follows:</span></span>  
  
1.  <span data-ttu-id="fe235-133">Bir istemci onay işlemi sisteme katılmak ister.</span><span class="sxs-lookup"><span data-stu-id="fe235-133">A client requests to participate to the approval process system.</span></span>  
  
2.  <span data-ttu-id="fe235-134">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] onay Yöneticisi hizmeti isteği onaylama işlemi sisteminin bir parçası olarak alır.</span><span class="sxs-lookup"><span data-stu-id="fe235-134">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service on the approval manager receives a request to be part of the approval process system.</span></span>  
  
3.  <span data-ttu-id="fe235-135">Benzersiz bir kimliği istemci için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fe235-135">A unique ID is generated for the client.</span></span> <span data-ttu-id="fe235-136">Kullanıcı bilgilerini bir veritabanında depolanır.</span><span class="sxs-lookup"><span data-stu-id="fe235-136">The user information is stored in a database.</span></span>  
  
4.  <span data-ttu-id="fe235-137">Benzersiz kimliği kullanıcıya geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="fe235-137">The unique ID is sent back to the user.</span></span>  
  
5.  <span data-ttu-id="fe235-138">Bir onay isteği alma ' dir.</span><span class="sxs-lookup"><span data-stu-id="fe235-138">An approval request is receive.</span></span> <span data-ttu-id="fe235-139">Onay Yöneticisi bir onay işlemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="fe235-139">The approval manager executes an approval process.</span></span>  
  
6.  <span data-ttu-id="fe235-140">Yeni bir iş akışı başlatma onay Yöneticisi tarafından bir onay isteği alındı.</span><span class="sxs-lookup"><span data-stu-id="fe235-140">An approval request is received by the approval manager, starting a new workflow.</span></span>  
  
7.  <span data-ttu-id="fe235-141">İstek (Basit, çekirdek veya karmaşık) türüne bağlı olarak farklı bir etkinliğe yürütülür.</span><span class="sxs-lookup"><span data-stu-id="fe235-141">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>  
  
8.  <span data-ttu-id="fe235-142">Gönderme ve alma etkinlikleri bağıntı ile istemci gözden geçirme için onay isteği gönderin ve yanıt almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe235-142">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>  
  
9. <span data-ttu-id="fe235-143">Onay işlemi iş akışını sonucunu istemciye gönderilir.</span><span class="sxs-lookup"><span data-stu-id="fe235-143">The result of the approval process workflow is sent to the client.</span></span>  
  
## <a name="using-the-sample"></a><span data-ttu-id="fe235-144">Örnek kullanma</span><span class="sxs-lookup"><span data-stu-id="fe235-144">Using the Sample</span></span>  
  
##### <a name="to-set-up-the-database"></a><span data-ttu-id="fe235-145">Veritabanını ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="fe235-145">To set up the database</span></span>  
  
1.  <span data-ttu-id="fe235-146">Gelen bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemini yönetici ayrıcalıklarıyla açıldı, bu DocumentApprovalProcess klasörüne gidin ve Setup.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fe235-146">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>  
  
##### <a name="to-set-up-the-application"></a><span data-ttu-id="fe235-147">Uygulamayı kurmak için</span><span class="sxs-lookup"><span data-stu-id="fe235-147">To set up the application</span></span>  
  
1.  <span data-ttu-id="fe235-148">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], DocumentApprovalProcess.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="fe235-148">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DocumentApprovalProcess.sln solution file.</span></span>  
  
2.  <span data-ttu-id="fe235-149">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fe235-149">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="fe235-150">Çözümü çalıştırmak için ApprovalManager projeye sağ tıklayarak onay Yöneticisi uygulama Başlat **Çözüm Gezgini** tıklatıp **hata ayıklama**->**Başlat**  sağ tıklatma menüsünden Yeni örneği.</span><span class="sxs-lookup"><span data-stu-id="fe235-150">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>  
  
     <span data-ttu-id="fe235-151">Yöneticinin çıkış hazır olduğunu size bildirmek bekleyin.</span><span class="sxs-lookup"><span data-stu-id="fe235-151">Wait for the manager’s output to let you know that it is ready.</span></span>  
  
##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="fe235-152">Tek onay senaryo çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fe235-152">To run the single approval scenario</span></span>  
  
1.  <span data-ttu-id="fe235-153">Yönetici izni olan bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="fe235-153">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="fe235-154">Çözüm içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="fe235-154">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="fe235-155">ApprovalClient\Bin\Debug klasöre gidin ve ApprovalClient.exe iki örneğini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fe235-155">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="fe235-156">Tıklatın **Bul**, bekle **abone** düğmesi etkin.</span><span class="sxs-lookup"><span data-stu-id="fe235-156">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="fe235-157">Herhangi bir kullanıcı adı yazın ve'ı tıklatın **abone**.</span><span class="sxs-lookup"><span data-stu-id="fe235-157">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="fe235-158">Bir istemci için kullanmak `UserType1` ve diğer tür `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="fe235-158">For one client, use `UserType1` and the other type `UserType2`.</span></span>  
  
6.  <span data-ttu-id="fe235-159">İçinde `UserType1` tek onay açılan menüden yazıp bir belge adı ve içerik istemci, seçin.</span><span class="sxs-lookup"><span data-stu-id="fe235-159">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="fe235-160">Tıklatın **isteği onay**.</span><span class="sxs-lookup"><span data-stu-id="fe235-160">Click **Request Approval**.</span></span>  
  
7.  <span data-ttu-id="fe235-161">İçinde `UserType2` istemci, onay bekleyen bir belge görünür.</span><span class="sxs-lookup"><span data-stu-id="fe235-161">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="fe235-162">Seçip basın **onaylama** veya **Reddet**.</span><span class="sxs-lookup"><span data-stu-id="fe235-162">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="fe235-163">Sonuçları göstermesi gerekir `UserType1` istemci.</span><span class="sxs-lookup"><span data-stu-id="fe235-163">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="fe235-164">Çekirdek onay senaryo çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fe235-164">To run the quorum approval scenario</span></span>  
  
1.  <span data-ttu-id="fe235-165">Yönetici izni olan bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="fe235-165">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="fe235-166">Çözüm içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="fe235-166">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="fe235-167">ApprovalClient\Bin\Debug klasöre gidin ve ApprovalClient.exe üç örneklerini yürütün.</span><span class="sxs-lookup"><span data-stu-id="fe235-167">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="fe235-168">Tıklatın **Bul**, bekle **abone** düğmesi etkin.</span><span class="sxs-lookup"><span data-stu-id="fe235-168">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="fe235-169">Herhangi bir kullanıcı adı yazın ve'ı tıklatın **abone**.</span><span class="sxs-lookup"><span data-stu-id="fe235-169">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="fe235-170">Bir istemci için kullanmak `UserType1` ve diğer iki tür `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="fe235-170">For one client use `UserType1` and the other two type `UserType2`.</span></span>  
  
6.  <span data-ttu-id="fe235-171">İçinde `UserType1` çekirdek onay açılan menüden yazıp bir belge adı ve içerik istemci, seçin.</span><span class="sxs-lookup"><span data-stu-id="fe235-171">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="fe235-172">Tıklatın **isteği onay**.</span><span class="sxs-lookup"><span data-stu-id="fe235-172">Click **Request Approval**.</span></span> <span data-ttu-id="fe235-173">Bu isteyen iki `UserType2` istemcileri onaylayın ya da belge reddedin.</span><span class="sxs-lookup"><span data-stu-id="fe235-173">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="fe235-174">Her ikisi de while `UserType2` istemcilerin gerekir yanıt, yalnızca bir istemci belge, onaylanması için onaylamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe235-174">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>  
  
7.  <span data-ttu-id="fe235-175">İçinde `UserType2` istemciler, onay bekleyen bir belge görünür.</span><span class="sxs-lookup"><span data-stu-id="fe235-175">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="fe235-176">Seçip basın **onaylama** veya **Reddet**.</span><span class="sxs-lookup"><span data-stu-id="fe235-176">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="fe235-177">Sonuçları göstermesi gerekir `UserType1` istemci.</span><span class="sxs-lookup"><span data-stu-id="fe235-177">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="fe235-178">Karmaşık onay senaryo çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fe235-178">To run the complex approval scenario</span></span>  
  
1.  <span data-ttu-id="fe235-179">Yönetici izni olan bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="fe235-179">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="fe235-180">Çözüm içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="fe235-180">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="fe235-181">ApprovalClient\Bin\Debug klasöre gidin ve ApprovalClient.exe dört örneklerini yürütün.</span><span class="sxs-lookup"><span data-stu-id="fe235-181">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="fe235-182">Tıklatın **Bul**, bekle **abone** düğmesi etkin.</span><span class="sxs-lookup"><span data-stu-id="fe235-182">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="fe235-183">Herhangi bir kullanıcı adı yazın ve'ı tıklatın **abone**.</span><span class="sxs-lookup"><span data-stu-id="fe235-183">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="fe235-184">Bir istemci için kullanmak `UserType1`, iki tür kullanıyor `UserType2`ve son kullanımda `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="fe235-184">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>  
  
6.  <span data-ttu-id="fe235-185">İçinde `UserType1` tek onay açılan menüden yazıp bir belge adı ve içerik istemci, seçin.</span><span class="sxs-lookup"><span data-stu-id="fe235-185">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="fe235-186">Tıklatın **isteği onay**.</span><span class="sxs-lookup"><span data-stu-id="fe235-186">Click **Request Approval**.</span></span>  
  
7.  <span data-ttu-id="fe235-187">İçinde `UserType2` istemciler, onay bekleyen bir belge görünür.</span><span class="sxs-lookup"><span data-stu-id="fe235-187">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="fe235-188">Seçip basın **onaylama**, belge geçirilir `UserType3` istemci.</span><span class="sxs-lookup"><span data-stu-id="fe235-188">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>  
  
     <span data-ttu-id="fe235-189">Belge ilk tarafından onaylanırsa `UserType2` çekirdek, belge için geçirilir `UserType3` istemci.</span><span class="sxs-lookup"><span data-stu-id="fe235-189">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>  
  
8.  <span data-ttu-id="fe235-190">Onaylama veya reddetme belgeden `UserType3` istemci.</span><span class="sxs-lookup"><span data-stu-id="fe235-190">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="fe235-191">Sonuçları göstermesi gerekir `UserType1` istemci.</span><span class="sxs-lookup"><span data-stu-id="fe235-191">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-clean-up"></a><span data-ttu-id="fe235-192">Temizlemek için</span><span class="sxs-lookup"><span data-stu-id="fe235-192">To clean up</span></span>  
  
1.  <span data-ttu-id="fe235-193">Gelen bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi, DocumentApprovalProcess klasörüne gidin ve Cleanup.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fe235-193">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>