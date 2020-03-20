---
title: İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: fe03047dd931d25ec94bbc5e00c479d1b42397bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185273"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="55dae-102">İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="55dae-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="55dae-103">İş akışı hizmetleri ve istemciler hareketlere katılabilir.</span><span class="sxs-lookup"><span data-stu-id="55dae-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="55dae-104">Bir hizmet işleminin ortam hareketinin bir parçası <xref:System.ServiceModel.Activities.Receive> olması için <xref:System.ServiceModel.Activities.TransactedReceiveScope> bir etkinliği bir etkinlik içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="55dae-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="55dae-105">Bir <xref:System.ServiceModel.Activities.Send> veya bir <xref:System.ServiceModel.Activities.SendReply> etkinlik içinde <xref:System.ServiceModel.Activities.TransactedReceiveScope> yapılan tüm aramalar da ortam hareketi içinde yapılacaktır.</span><span class="sxs-lookup"><span data-stu-id="55dae-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="55dae-106">İş akışı istemcisi uygulaması, ortam işlemini <xref:System.Activities.Statements.TransactionScope> kullanarak etkinlik ve çağrı hizmeti işlemlerini kullanarak bir ortam hareketi oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="55dae-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="55dae-107">Bu konu, hareketlere katılan bir iş akışı hizmeti ve iş akışı istemcisi oluşturmakonusunda size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="55dae-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="55dae-108">Bir iş akışı hizmeti örneği bir hareket içinde yüklenirse ve iş akışı bir <xref:System.Activities.Statements.Persist> etkinlik içeriyorsa, iş akışı örneği işlem süreleri bitene kadar engellenir.</span><span class="sxs-lookup"><span data-stu-id="55dae-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will block until the transaction times out.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="55dae-109">Ne zaman bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> kullandığınızda, tüm Alır'yı iş <xref:System.ServiceModel.Activities.TransactedReceiveScope> akışına etkinlikler içinde yerleştirmeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="55dae-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="55dae-110">Kullanma <xref:System.ServiceModel.Activities.TransactedReceiveScope> ve iletiler yanlış sırada geldiğinde, ilk sipariş dışı iletisini teslim etmeye çalışırken iş akışı iptal edilecektir.</span><span class="sxs-lookup"><span data-stu-id="55dae-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="55dae-111">İş akışı boşta kaldığında iş akışınızın her zaman tutarlı bir durdurma noktasında olduğundan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="55dae-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="55dae-112">Bu, iş akışı iptal edilmesi halinde önceki bir kalıcılık noktasından iş akışını yeniden başlatmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="55dae-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="55dae-113">Paylaşılan kitaplık oluşturma</span><span class="sxs-lookup"><span data-stu-id="55dae-113">Create a shared library</span></span>  
  
1. <span data-ttu-id="55dae-114">Yeni bir boş Visual Studio Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="55dae-114">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="55dae-115">'li yeni bir `Common`sınıf kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55dae-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="55dae-116">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="55dae-116">Add references to the following assemblies:</span></span>  
  
    - <span data-ttu-id="55dae-117">Sistem.Etkinlikler.dll</span><span class="sxs-lookup"><span data-stu-id="55dae-117">System.Activities.dll</span></span>  
  
    - <span data-ttu-id="55dae-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="55dae-118">System.ServiceModel.dll</span></span>  
  
    - <span data-ttu-id="55dae-119">Sistem.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="55dae-119">System.ServiceModel.Activities.dll</span></span>  
  
    - <span data-ttu-id="55dae-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="55dae-120">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="55dae-121">`Common` Projeye çağrılan `PrintTransactionInfo` yeni bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55dae-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="55dae-122">Bu sınıf yöntemden <xref:System.Activities.NativeActivity> türetilir ve aşırı yüklenir. <xref:System.Activities.NativeActivity.Execute%2A></span><span class="sxs-lookup"><span data-stu-id="55dae-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```csharp
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
    ```  
  
     <span data-ttu-id="55dae-123">Bu, ortam hareketi yle ilgili bilgileri görüntüleyen ve bu konuda kullanılan hem hizmet hem de istemci iş akışlarında kullanılan yerel bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="55dae-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="55dae-124">Bu etkinliği **Araç Kutusu'nun** **Ortak** bölümünde kullanılabilir hale getirmek için çözüm oluşturun.</span><span class="sxs-lookup"><span data-stu-id="55dae-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="55dae-125">İş akışı hizmetini uygulayın</span><span class="sxs-lookup"><span data-stu-id="55dae-125">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="55dae-126">`Common` Projeye çağrılan `WorkflowService` yeni bir WCF İş Akışı Hizmeti ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55dae-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="55dae-127">Bunu yapmak için `Common` projeyi sağ tıklatın, **Ekle**, **Yeni Öğe ...**, Yüklü **Şablonlar** altında **İş Akışını** seçin ve **WCF İş Akışı Hizmeti'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="55dae-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![İş Akışı Hizmeti Ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="55dae-129">Varsayılan `ReceiveRequest` ve `SendResponse` etkinlikleri silin.</span><span class="sxs-lookup"><span data-stu-id="55dae-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="55dae-130">Bir <xref:System.Activities.Statements.WriteLine> etkinliği sürükleyin `Sequential Service` ve aktiviteye bırakın.</span><span class="sxs-lookup"><span data-stu-id="55dae-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="55dae-131">Metin özelliğini `"Workflow Service starting ..."` aşağıdaki örnekte gösterildiği gibi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="55dae-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="55dae-132">! [Sıralı Hizmet etkinliğine WriteLine etkinliği ekleme(./ortam/akan-hareketler-iş akışı-hizmetler/add-writeline-sequential-service.jpg)</span><span class="sxs-lookup"><span data-stu-id="55dae-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="55dae-133">Etkinlikten <xref:System.Activities.Statements.WriteLine> sonra <xref:System.ServiceModel.Activities.TransactedReceiveScope> bir sürükle ve bırak.</span><span class="sxs-lookup"><span data-stu-id="55dae-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="55dae-134"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik, **Araç Kutusu'nun** **Mesajlaşma** bölümünde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="55dae-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="55dae-135">Etkinlik, **İstek** ve Gövde olmak için iki bölümden oluşmaktadır. **Body** <xref:System.ServiceModel.Activities.TransactedReceiveScope></span><span class="sxs-lookup"><span data-stu-id="55dae-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="55dae-136">**İstek** bölümü <xref:System.ServiceModel.Activities.Receive> etkinliği içerir.</span><span class="sxs-lookup"><span data-stu-id="55dae-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="55dae-137">**Gövde** bölümü, ileti alındıktan sonra bir hareket içinde yürütülecek etkinlikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="55dae-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![TransactedReceiveScope etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="55dae-139"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinliği seçin ve **Değişkenler** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="55dae-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="55dae-140">Aşağıdaki değişkenleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55dae-140">Add the following variables.</span></span>  
  
     ![TransactedReceiveScope'a değişken ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > <span data-ttu-id="55dae-142">Varsayılan olarak var olan veri değişkenini silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55dae-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="55dae-143">Varolan tutamaç değişkenini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55dae-143">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="55dae-144">Etkinliğin İstek <xref:System.ServiceModel.Activities.Receive> bölümündeki bir etkinliği sürükleyin ve bırakın. **Request** <xref:System.ServiceModel.Activities.TransactedReceiveScope></span><span class="sxs-lookup"><span data-stu-id="55dae-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="55dae-145">Aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="55dae-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="55dae-146">Özellik</span><span class="sxs-lookup"><span data-stu-id="55dae-146">Property</span></span>|<span data-ttu-id="55dae-147">Değer</span><span class="sxs-lookup"><span data-stu-id="55dae-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="55dae-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="55dae-148">CanCreateInstance</span></span>|<span data-ttu-id="55dae-149">True (onay kutusunu işaretleyin)</span><span class="sxs-lookup"><span data-stu-id="55dae-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="55dae-150">ThrottledRequests</span><span class="sxs-lookup"><span data-stu-id="55dae-150">OperationName</span></span>|<span data-ttu-id="55dae-151">BaşlangıçÖrneği</span><span class="sxs-lookup"><span data-stu-id="55dae-151">StartSample</span></span>|  
    |<span data-ttu-id="55dae-152">Hizmet Sözleşme Adı</span><span class="sxs-lookup"><span data-stu-id="55dae-152">ServiceContractName</span></span>|<span data-ttu-id="55dae-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="55dae-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="55dae-154">İş akışı aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="55dae-154">The workflow should look like this:</span></span>  
  
     ![Alma etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="55dae-156"><xref:System.ServiceModel.Activities.Receive> Etkinlikte **Tanımla...** bağlantısını tıklatın ve aşağıdaki ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="55dae-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Al etkinliği için ileti ayarlarını ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="55dae-158">Sürükleyin ve <xref:System.Activities.Statements.Sequence> Vücut bölümüne bir <xref:System.ServiceModel.Activities.TransactedReceiveScope>etkinlik bırakın.</span><span class="sxs-lookup"><span data-stu-id="55dae-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="55dae-159"><xref:System.Activities.Statements.Sequence> Etkinlik içinde sürükleyin <xref:System.Activities.Statements.WriteLine> ve iki <xref:System.Activities.Statements.WriteLine.Text%2A> etkinlik bırakın ve aşağıdaki tabloda gösterildiği gibi özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="55dae-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="55dae-160">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="55dae-160">Activity</span></span>|<span data-ttu-id="55dae-161">Değer</span><span class="sxs-lookup"><span data-stu-id="55dae-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="55dae-162">1. WriteLine</span><span class="sxs-lookup"><span data-stu-id="55dae-162">1st WriteLine</span></span>|<span data-ttu-id="55dae-163">"Hizmet: Tamamlanmış Alma"</span><span class="sxs-lookup"><span data-stu-id="55dae-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="55dae-164">2. WriteLine</span><span class="sxs-lookup"><span data-stu-id="55dae-164">2nd WriteLine</span></span>|<span data-ttu-id="55dae-165">"Hizmet: Alınan = " + requestMessage</span><span class="sxs-lookup"><span data-stu-id="55dae-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="55dae-166">İş akışı şimdi şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="55dae-166">The workflow should now look like this:</span></span>  
  
     ![WriteLine etkinliklerini ekledikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="55dae-168">**Aktivitedeki** <xref:System.ServiceModel.Activities.TransactedReceiveScope> Ikinci `PrintTransactionInfo` <xref:System.Activities.Statements.WriteLine> etkinlikten sonra etkinliği sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="55dae-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![PrintTransactionInfo ekledikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="55dae-170">Etkinlikten `PrintTransactionInfo` sonra <xref:System.Activities.Statements.Assign> bir etkinliği sürükleyin ve bırakın ve özelliklerini aşağıdaki tabloya göre ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="55dae-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="55dae-171">Özellik</span><span class="sxs-lookup"><span data-stu-id="55dae-171">Property</span></span>|<span data-ttu-id="55dae-172">Değer</span><span class="sxs-lookup"><span data-stu-id="55dae-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="55dae-173">Alıcı</span><span class="sxs-lookup"><span data-stu-id="55dae-173">To</span></span>|<span data-ttu-id="55dae-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="55dae-174">replyMessage</span></span>|  
    |<span data-ttu-id="55dae-175">Değer</span><span class="sxs-lookup"><span data-stu-id="55dae-175">Value</span></span>|<span data-ttu-id="55dae-176">"Hizmet: Yanıt gönderme."</span><span class="sxs-lookup"><span data-stu-id="55dae-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="55dae-177">Etkinlikten <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.Assign> sonra bir etkinliği sürükleyin <xref:System.Activities.Statements.WriteLine.Text%2A> ve bırakın ve özelliğini "Hizmet: Yanıtla başlat" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="55dae-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="55dae-178">İş akışı şimdi şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="55dae-178">The workflow should now look like this:</span></span>  
  
     ![Atama ve WriteLine ekledikten sonra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="55dae-180">Etkinliği sağ tıklatın ve **SendReply oluştur'u** seçin <xref:System.Activities.Statements.WriteLine> ve son etkinlikten sonra yapıştırın. <xref:System.ServiceModel.Activities.Receive></span><span class="sxs-lookup"><span data-stu-id="55dae-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="55dae-181">`SendReplyToReceive` Etkinlikte **Tanımla...** bağlantısını tıklatın ve aşağıdaki ayarları yapın.</span><span class="sxs-lookup"><span data-stu-id="55dae-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![İleti ayarlarını yanıtla](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="55dae-183">Etkinlikten <xref:System.Activities.Statements.WriteLine> `SendReplyToReceive` sonra bir etkinliği sürükleyin ve <xref:System.Activities.Statements.WriteLine.Text%2A> bırakın ve özelliğini "Hizmet: Gönderilen Yanıt" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="55dae-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="55dae-184">Bir <xref:System.Activities.Statements.WriteLine> etkinliği iş akışının en altında sürükleyin <xref:System.Activities.Statements.WriteLine.Text%2A> ve bırakın ve özelliğini "Hizmet: İş akışı sona erer, çıkmak için ENTER tuşuna basın." olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="55dae-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="55dae-185">Tamamlanan hizmet iş akışı aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="55dae-185">The completed service workflow should look like this:</span></span>  
  
     ![Komple Servis İş Akışı](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="55dae-187">İş akışı istemcisini uygulama</span><span class="sxs-lookup"><span data-stu-id="55dae-187">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="55dae-188">`Common` Projeye çağrılan `WorkflowClient` yeni bir WCF İş Akışı uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55dae-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="55dae-189">Bunu yapmak için `Common` projeyi sağ tıklatın, **Ekle**, **Yeni Öğe ... ,** Yüklü **Şablonlar** altında **İş Akışı'nı** seçin ve **Etkinlik'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="55dae-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Etkinlik projesi ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="55dae-191">Bir <xref:System.Activities.Statements.Sequence> etkinliği tasarım yüzeyine sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="55dae-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="55dae-192">Etkinlik içinde sürükleyin <xref:System.Activities.Statements.WriteLine> ve bir <xref:System.Activities.Statements.WriteLine.Text%2A> etkinliği bırakın ve özelliğini `"Client: Workflow starting"` <xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="55dae-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="55dae-193">İş akışı şimdi şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="55dae-193">The workflow should now look like this:</span></span>  
  
     ![WriteLine etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="55dae-195">Etkinlikten <xref:System.Activities.Statements.WriteLine> sonra <xref:System.Activities.Statements.TransactionScope> bir etkinliği sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="55dae-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="55dae-196"><xref:System.Activities.Statements.TransactionScope> Etkinliği seçin, Değişkenler düğmesini tıklatın ve aşağıdaki değişkenleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55dae-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![TransactionScope'a değişken ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="55dae-198">Bir <xref:System.Activities.Statements.Sequence> etkinliği sürükleyin ve aktivitenin <xref:System.Activities.Statements.TransactionScope> gövdesine bırakın.</span><span class="sxs-lookup"><span data-stu-id="55dae-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="55dae-199">Bir `PrintTransactionInfo` etkinliği sürükleyin ve bırakın<xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="55dae-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7. <span data-ttu-id="55dae-200">Etkinlikten <xref:System.Activities.Statements.WriteLine> `PrintTransactionInfo` sonra bir etkinliği sürükleyin <xref:System.Activities.Statements.WriteLine.Text%2A> ve bırakın ve özelliğini "İstemci: Başlangıç Gönder" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="55dae-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="55dae-201">İş akışı şimdi şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="55dae-201">The workflow should now look like this:</span></span>  
  
     ![İstemci Ekleme: Gönderme etkinliklerini başlangıç](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="55dae-203">Etkinlikten <xref:System.Activities.Statements.Assign> sonra <xref:System.ServiceModel.Activities.Send> bir etkinliği sürükleyin ve bırakın ve aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="55dae-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="55dae-204">Özellik</span><span class="sxs-lookup"><span data-stu-id="55dae-204">Property</span></span>|<span data-ttu-id="55dae-205">Değer</span><span class="sxs-lookup"><span data-stu-id="55dae-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="55dae-206">Endpointconfigurationname</span><span class="sxs-lookup"><span data-stu-id="55dae-206">EndpointConfigurationName</span></span>|<span data-ttu-id="55dae-207">iş akışıServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="55dae-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="55dae-208">ThrottledRequests</span><span class="sxs-lookup"><span data-stu-id="55dae-208">OperationName</span></span>|<span data-ttu-id="55dae-209">BaşlangıçÖrneği</span><span class="sxs-lookup"><span data-stu-id="55dae-209">StartSample</span></span>|  
    |<span data-ttu-id="55dae-210">Hizmet Sözleşme Adı</span><span class="sxs-lookup"><span data-stu-id="55dae-210">ServiceContractName</span></span>|<span data-ttu-id="55dae-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="55dae-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="55dae-212">İş akışı şimdi şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="55dae-212">The workflow should now look like this:</span></span>  
  
     ![Gönder etkinlik özelliklerini ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="55dae-214">**Tanımla...** bağlantısını tıklayın ve aşağıdaki ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="55dae-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Etkinlik iletisi ayarları gönderme](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="55dae-216"><xref:System.ServiceModel.Activities.Send> Etkinliği sağ tıklatın ve **YanıtLa oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="55dae-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="55dae-217">Etkinlik, <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikten <xref:System.ServiceModel.Activities.Send> sonra otomatik olarak yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="55dae-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="55dae-218">Tanımla'yı tıklatın... ReceiveReplyForSend etkinliğinde bağlantı kurun ve aşağıdaki ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="55dae-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![ReceiveForSend ileti ayarlarını ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="55dae-220"><xref:System.Activities.Statements.WriteLine> Bir etkinliği sürükleyin <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "İstemci: Eksiksiz Gönder" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="55dae-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="55dae-221">Etkinlikten <xref:System.Activities.Statements.WriteLine> <xref:System.ServiceModel.Activities.ReceiveReply> sonra bir etkinliği sürükleyin <xref:System.Activities.Statements.WriteLine.Text%2A> ve bırakın ve özelliğini "İstemci tarafına: Alınan yanıt = " + yanıtİletim</span><span class="sxs-lookup"><span data-stu-id="55dae-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="55dae-222">Etkinlikten <xref:System.Activities.Statements.WriteLine> sonra `PrintTransactionInfo` bir etkinliği sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="55dae-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="55dae-223">Bir <xref:System.Activities.Statements.WriteLine> etkinliği iş akışının sonunda sürükleyin ve <xref:System.Activities.Statements.WriteLine.Text%2A> bırakın ve özelliğini "İstemci iş akışı sona erer" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="55dae-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="55dae-224">Tamamlanan istemci iş akışı aşağıdaki diyagram gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="55dae-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![Tamamlanan istemci iş akışı](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="55dae-226">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="55dae-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="55dae-227">Hizmet uygulamasını oluşturma</span><span class="sxs-lookup"><span data-stu-id="55dae-227">Create the Service application</span></span>  
  
1. <span data-ttu-id="55dae-228">Çözüme yeni `Service` bir Konsol Uygulaması projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55dae-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="55dae-229">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="55dae-229">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="55dae-230">Sistem.Etkinlikler.dll</span><span class="sxs-lookup"><span data-stu-id="55dae-230">System.Activities.dll</span></span>  
  
    2. <span data-ttu-id="55dae-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="55dae-231">System.ServiceModel.dll</span></span>  
  
    3. <span data-ttu-id="55dae-232">Sistem.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="55dae-232">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="55dae-233">Oluşturulan Program.cs dosyasını ve aşağıdaki kodu açın:</span><span class="sxs-lookup"><span data-stu-id="55dae-233">Open the generated Program.cs file and the following code:</span></span>  
  
    ```csharp
          static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };
          }  
    ```  
  
3. <span data-ttu-id="55dae-234">Projeye aşağıdaki app.config dosyasını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55dae-234">Add the following app.config file to the project.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="create-the-client-application"></a><span data-ttu-id="55dae-235">İstemci uygulamasını oluşturma</span><span class="sxs-lookup"><span data-stu-id="55dae-235">Create the client application</span></span>  
  
1. <span data-ttu-id="55dae-236">Çözüme yeni `Client` bir Konsol Uygulaması projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55dae-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="55dae-237">System.Activities.dll adresine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55dae-237">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="55dae-238">program.cs dosyasını açın ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55dae-238">Open the program.cs file and add the following code.</span></span>  
  
    ```csharp
    class Program  
    {  

        private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
        static void Main(string[] args)  
        {  
            //Build client  
            Console.WriteLine("Building the client.");  
            WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
            client.Completed = Program.Completed;  
            client.Aborted = Program.Aborted;  
            client.OnUnhandledException = Program.OnUnhandledException;  
            //Wait for service to start  
            Console.WriteLine("Press ENTER once service is started.");  
            Console.ReadLine();  
  
            //Start the client
            Console.WriteLine("Starting the client.");  
            client.Run();  
            syncEvent.WaitOne();  
  
            //Sample complete  
            Console.WriteLine();  
            Console.WriteLine("Client complete. Press ENTER to exit.");  
            Console.ReadLine();  
        }  
  
        private static void Completed(WorkflowApplicationCompletedEventArgs e)  
        {  
            Program.syncEvent.Set();  
        }  
  
        private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
        {  
            Console.WriteLine("Client Aborted: {0}", e.Reason);  
            Program.syncEvent.Set();  
        }  
  
        private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
            return UnhandledExceptionAction.Cancel;  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="55dae-239">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55dae-239">See also</span></span>

- [<span data-ttu-id="55dae-240">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="55dae-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="55dae-241">Windows Communication Foundation İşlemleri Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="55dae-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
