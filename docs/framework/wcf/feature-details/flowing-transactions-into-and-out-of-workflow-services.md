---
title: İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: 272e188b448864450621665f80ea0ab8b0037b37
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185694"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="9a5b7-102">İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="9a5b7-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="9a5b7-103">İş akışı hizmetler ve istemcileri işlemlerine katılabilmesi.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="9a5b7-104">Bir hizmet işlemi bir ortam işlem bir parçası haline getirin bir <xref:System.ServiceModel.Activities.Receive> etkinlik içinde bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="9a5b7-105">Tarafından yapılan tüm çağrıların bir <xref:System.ServiceModel.Activities.Send> veya <xref:System.ServiceModel.Activities.SendReply> etkinliğ <xref:System.ServiceModel.Activities.TransactedReceiveScope> ortam işlem içinde de yapılacaktır.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="9a5b7-106">Bir iş akışı istemci uygulaması kullanarak bir ortam işlem oluşturabilirsiniz <xref:System.Activities.Statements.TransactionScope> ortam işlem kullanarak etkinlik ve arama hizmeti işlemleri.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="9a5b7-107">Bu konuda, bir iş akışı hizmeti ve katılan iş akışı istemci işlemleri oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="9a5b7-108">Bir iş akışı hizmet örneği, bir işlem içinde yüklenir ve iş akışı içeren bir <xref:System.Activities.Statements.Persist> etkinliği iş akışı örneği askıda işlem zaman aşımına uğrayana kadar.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will hang until the transaction times out.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9a5b7-109">Kullandığınız her bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> iş akışı tüm alır yerleştirmek için önerilen <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9a5b7-110">Kullanırken <xref:System.ServiceModel.Activities.TransactedReceiveScope> ve iletiler geldiğinde yanlış sırada, iş akışı, ilk sıra dışında iletisi göndermeyi çalışırken iptal edilecek.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="9a5b7-111">İş akışı boş kalır, iş akışınızı her zaman tutarlı noktası durduruluyor emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="9a5b7-112">Bu, bir önceki Kalıcılık noktasından iş akışını iş akışı durduruldu yeniden başlatmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="9a5b7-113">Paylaşılan bir kitaplık oluşturun</span><span class="sxs-lookup"><span data-stu-id="9a5b7-113">Create a shared library</span></span>  
  
1.  <span data-ttu-id="9a5b7-114">Yeni bir boş Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-114">Create a new empty Visual Studio Solution.</span></span>  
  
2.  <span data-ttu-id="9a5b7-115">Adlı yeni bir sınıf kitaplığı projesi Ekle `Common`.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="9a5b7-116">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-116">Add references to the following assemblies:</span></span>  
  
    -   <span data-ttu-id="9a5b7-117">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="9a5b7-117">System.Activities.dll</span></span>  
  
    -   <span data-ttu-id="9a5b7-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="9a5b7-118">System.ServiceModel.dll</span></span>  
  
    -   <span data-ttu-id="9a5b7-119">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="9a5b7-119">System.ServiceModel.Activities.dll</span></span>  
  
    -   <span data-ttu-id="9a5b7-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="9a5b7-120">System.Transactions.dll</span></span>  
  
3.  <span data-ttu-id="9a5b7-121">Adlı yeni bir sınıf ekleyin `PrintTransactionInfo` için `Common` proje.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="9a5b7-122">Bu sınıf türetilir <xref:System.Activities.NativeActivity> ve aşırı <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="9a5b7-123">Bu ortam işlem hakkında bilgi görüntüler ve bu konuda kullanılan hizmet ve istemci iş akışlarında kullanılan yerel bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="9a5b7-124">Bu etkinlik içinde kullanılabilir hale getirmek için çözümü derleyin **ortak** bölümünü **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="9a5b7-125">Bir iş akışı hizmet ekleme</span><span class="sxs-lookup"><span data-stu-id="9a5b7-125">Implement the workflow service</span></span>  
  
1.  <span data-ttu-id="9a5b7-126">Yeni bir WCF iş akışı adlı hizmet ekleme `WorkflowService` için `Common` proje.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="9a5b7-127">Bu sağ tıklama yapmanız `Common` proje, select **Ekle**, **yeni öğe...** Seçin **iş akışı** altında **yüklü şablonlar** seçip **WCF iş akışı hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Bir iş akışı hizmeti ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2.  <span data-ttu-id="9a5b7-129">Varsayılan silme `ReceiveRequest` ve `SendResponse` etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3.  <span data-ttu-id="9a5b7-130">Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> etkinliğini `Sequential Service` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="9a5b7-131">Text özelliğinin ayarlanacağı ifade `"Workflow Service starting ..."` aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="9a5b7-132">! [İçin sıralı hizmeti activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg) WriteLine etkinlik ekleme</span><span class="sxs-lookup"><span data-stu-id="9a5b7-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4.  <span data-ttu-id="9a5b7-133">Sürükle ve bırak bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> sonra <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="9a5b7-134"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik bulunabilir **Mesajlaşma** bölümünü **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="9a5b7-135"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik iki bölümden oluşan **istek** ve **gövdesi**.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="9a5b7-136">**İstek** bölüm içeren <xref:System.ServiceModel.Activities.Receive> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="9a5b7-137">**Gövdesi** bölümünde bir ileti aldıktan sonra bir işlem içinde çalıştırmak için etkinlikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![TransactedReceiveScope etkinlik ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5.  <span data-ttu-id="9a5b7-139">Seçin <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği ve tıklatın **değişkenleri** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="9a5b7-140">Aşağıdaki değişkenleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-140">Add the following variables.</span></span>  
  
     ![TransactedReceiveScope için değişkenleri ekleniyor](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    >  <span data-ttu-id="9a5b7-142">Varsayılan olarak yoktur veri değişkeni silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="9a5b7-143">Varolan bir tanıtıcı değişkeni de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-143">You can also use the existing handle variable.</span></span>  
  
6.  <span data-ttu-id="9a5b7-144">Sürükle ve bırak bir <xref:System.ServiceModel.Activities.Receive> etkinliğ **istek** bölümünü <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="9a5b7-145">Aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="9a5b7-146">Özellik</span><span class="sxs-lookup"><span data-stu-id="9a5b7-146">Property</span></span>|<span data-ttu-id="9a5b7-147">Değer</span><span class="sxs-lookup"><span data-stu-id="9a5b7-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="9a5b7-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="9a5b7-148">CanCreateInstance</span></span>|<span data-ttu-id="9a5b7-149">TRUE (onay kutusu denetimi)</span><span class="sxs-lookup"><span data-stu-id="9a5b7-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="9a5b7-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="9a5b7-150">OperationName</span></span>|<span data-ttu-id="9a5b7-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="9a5b7-151">StartSample</span></span>|  
    |<span data-ttu-id="9a5b7-152">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="9a5b7-152">ServiceContractName</span></span>|<span data-ttu-id="9a5b7-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="9a5b7-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="9a5b7-154">İş akışı şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-154">The workflow should look like this:</span></span>  
  
     ![Receive etkinlik ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7.  <span data-ttu-id="9a5b7-156">Tıklayın **tanımlayın...**  bağlantısını <xref:System.ServiceModel.Activities.Receive> etkinlik ve şu ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![İleti ayarları alma etkinliğinin ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8.  <span data-ttu-id="9a5b7-158">Sürükle ve bırak bir <xref:System.Activities.Statements.Sequence> gövde bölümünü etkinliğini <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="9a5b7-159">İçinde <xref:System.Activities.Statements.Sequence> etkinliğini sürükleyip iki <xref:System.Activities.Statements.WriteLine> etkinlikleri ve kümesi <xref:System.Activities.Statements.WriteLine.Text%2A> aşağıdaki tabloda gösterildiği gibi özellikleri.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="9a5b7-160">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="9a5b7-160">Activity</span></span>|<span data-ttu-id="9a5b7-161">Değer</span><span class="sxs-lookup"><span data-stu-id="9a5b7-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="9a5b7-162">1 WriteLine</span><span class="sxs-lookup"><span data-stu-id="9a5b7-162">1st WriteLine</span></span>|<span data-ttu-id="9a5b7-163">"Hizmet: Tamamlanan Al"</span><span class="sxs-lookup"><span data-stu-id="9a5b7-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="9a5b7-164">2 WriteLine</span><span class="sxs-lookup"><span data-stu-id="9a5b7-164">2nd WriteLine</span></span>|<span data-ttu-id="9a5b7-165">"Hizmet: Alınan = "+ requestMessage</span><span class="sxs-lookup"><span data-stu-id="9a5b7-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="9a5b7-166">İş akışı gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-166">The workflow should now look like this:</span></span>  
  
     ![WriteLine etkinlik ekledikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="9a5b7-168">Sürükle ve bırak `PrintTransactionInfo` etkinlikten sonra ikinci <xref:System.Activities.Statements.WriteLine> etkinliğinde **gövdesi** içinde <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![PrintTransactionInfo ekledikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="9a5b7-170">Sürükle ve bırak bir <xref:System.Activities.Statements.Assign> etkinlikten sonra `PrintTransactionInfo` etkinlik ve aşağıdaki tabloya göre özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="9a5b7-171">Özellik</span><span class="sxs-lookup"><span data-stu-id="9a5b7-171">Property</span></span>|<span data-ttu-id="9a5b7-172">Değer</span><span class="sxs-lookup"><span data-stu-id="9a5b7-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="9a5b7-173">Bitiş</span><span class="sxs-lookup"><span data-stu-id="9a5b7-173">To</span></span>|<span data-ttu-id="9a5b7-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="9a5b7-174">replyMessage</span></span>|  
    |<span data-ttu-id="9a5b7-175">Değer</span><span class="sxs-lookup"><span data-stu-id="9a5b7-175">Value</span></span>|<span data-ttu-id="9a5b7-176">"Hizmet: Yanıtı gönderiliyor."</span><span class="sxs-lookup"><span data-stu-id="9a5b7-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="9a5b7-177">Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra <xref:System.Activities.Statements.Assign> etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "hizmeti: Yanıt başlar."</span><span class="sxs-lookup"><span data-stu-id="9a5b7-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="9a5b7-178">İş akışı gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-178">The workflow should now look like this:</span></span>  
  
     ![Atama ve WriteLine ekledikten sonra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="9a5b7-180">Sağ tıklayın <xref:System.ServiceModel.Activities.Receive> etkinliği ve select **oluşturma SendReply** ve sonra son yapıştırın <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="9a5b7-181">Tıklayın **tanımlayın...**  bağlantısını `SendReplyToReceive` etkinlik ve şu ayarları yapın.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Yanıt iletisi ayarları](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="9a5b7-183">Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra `SendReplyToReceive` etkinliği ve kümesi sahip <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "hizmeti: Yanıt gönderildi."</span><span class="sxs-lookup"><span data-stu-id="9a5b7-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="9a5b7-184">Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> alt kümesi ve iş akışı etkinlik kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "hizmeti: İş akışı, ENTER tuşuna basın çıkmak için sona erer."</span><span class="sxs-lookup"><span data-stu-id="9a5b7-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="9a5b7-185">Tamamlanmış hizmet iş akışı şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-185">The completed service workflow should look like this:</span></span>  
  
     ![Tam hizmet iş akışı](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="9a5b7-187">İş akışı istemcisini uygulama</span><span class="sxs-lookup"><span data-stu-id="9a5b7-187">Implement the workflow client</span></span>  
  
1.  <span data-ttu-id="9a5b7-188">Adlı yeni bir WCF iş akışı uygulama ekleme `WorkflowClient` için `Common` proje.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="9a5b7-189">Bu sağ tıklama yapmanız `Common` proje, select **Ekle**, **yeni öğe...** Seçin **iş akışı** altında **yüklü şablonlar** seçip **etkinlik**.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Bir etkinlik proje ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2.  <span data-ttu-id="9a5b7-191">Sürükle ve bırak bir <xref:System.Activities.Statements.Sequence> tasarım yüzeyine etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3.  <span data-ttu-id="9a5b7-192">İçinde <xref:System.Activities.Statements.Sequence> etkinliğini sürükleyip bırakma bir <xref:System.Activities.Statements.WriteLine> etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="9a5b7-193">İş akışı gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-193">The workflow should now look like this:</span></span>  
  
     ![WriteLine etkinlik Ekle](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4.  <span data-ttu-id="9a5b7-195">Sürükle ve bırak bir <xref:System.Activities.Statements.TransactionScope> etkinlikten sonra <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="9a5b7-196">Seçin <xref:System.Activities.Statements.TransactionScope> etkinliği, değişkenleri düğmesini tıklatın ve aşağıdaki değişkenleri eklemek tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![TransactionScope için değişkenlerini ekleyin](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5.  <span data-ttu-id="9a5b7-198">Sürükle ve bırak bir <xref:System.Activities.Statements.Sequence> gövdesinin etkinliğini <xref:System.Activities.Statements.TransactionScope> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6.  <span data-ttu-id="9a5b7-199">Sürükle ve bırak bir `PrintTransactionInfo` etkinliğ <xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="9a5b7-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7.  <span data-ttu-id="9a5b7-200">Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra `PrintTransactionInfo` etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "İstemci: Send başlamadan".</span><span class="sxs-lookup"><span data-stu-id="9a5b7-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="9a5b7-201">İş akışı gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-201">The workflow should now look like this:</span></span>  
  
     ![İstemci ekleme: Gönderme işlemleri başlangıcı](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8.  <span data-ttu-id="9a5b7-203">Sürükle ve bırak bir <xref:System.ServiceModel.Activities.Send> etkinlikten sonra <xref:System.Activities.Statements.Assign> etkinlik ve aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="9a5b7-204">Özellik</span><span class="sxs-lookup"><span data-stu-id="9a5b7-204">Property</span></span>|<span data-ttu-id="9a5b7-205">Değer</span><span class="sxs-lookup"><span data-stu-id="9a5b7-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="9a5b7-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="9a5b7-206">EndpointConfigurationName</span></span>|<span data-ttu-id="9a5b7-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="9a5b7-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="9a5b7-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="9a5b7-208">OperationName</span></span>|<span data-ttu-id="9a5b7-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="9a5b7-209">StartSample</span></span>|  
    |<span data-ttu-id="9a5b7-210">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="9a5b7-210">ServiceContractName</span></span>|<span data-ttu-id="9a5b7-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="9a5b7-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="9a5b7-212">İş akışı gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-212">The workflow should now look like this:</span></span>  
  
     ![Send etkinlik özelliklerini ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="9a5b7-214">Tıklayın **tanımlayın...**  bağlayın ve şu ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![İleti ayarları etkinlik Gönder](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="9a5b7-216">Sağ tıklayın <xref:System.ServiceModel.Activities.Send> etkinliği ve select **oluşturma ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="9a5b7-217"><xref:System.ServiceModel.Activities.ReceiveReply> Etkinlik otomatik olarak yerleştirilecek sonra <xref:System.ServiceModel.Activities.Send> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="9a5b7-218">Tanımla... tıklayın ReceiveReplyForSend faaliyete bağlayın ve şu ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![ReceiveForSend ileti ayarları ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="9a5b7-220">Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> arasında etkinliği <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "İstemci: Tam gönderin."</span><span class="sxs-lookup"><span data-stu-id="9a5b7-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="9a5b7-221">Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra <xref:System.ServiceModel.Activities.ReceiveReply> etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "istemci tarafında: Alınan yanıt = "+ replyMessage</span><span class="sxs-lookup"><span data-stu-id="9a5b7-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="9a5b7-222">Sürükle ve bırak bir `PrintTransactionInfo` etkinlikten sonra <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="9a5b7-223">Sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> sonunda kümesi ve iş akışı, etkinlik kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "İstemci iş akışı sona erer."</span><span class="sxs-lookup"><span data-stu-id="9a5b7-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="9a5b7-224">Tamamlanan istemci iş akışı aşağıdaki diyagramda gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![Tamamlanan istemci workfliow](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="9a5b7-226">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="9a5b7-227">Hizmet Uygulaması Oluştur</span><span class="sxs-lookup"><span data-stu-id="9a5b7-227">Create the Service application</span></span>  
  
1.  <span data-ttu-id="9a5b7-228">Adlı yeni bir konsol uygulaması projesi eklemek `Service` çözüm.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="9a5b7-229">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-229">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="9a5b7-230">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="9a5b7-230">System.Activities.dll</span></span>  
  
    2.  <span data-ttu-id="9a5b7-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="9a5b7-231">System.ServiceModel.dll</span></span>  
  
    3.  <span data-ttu-id="9a5b7-232">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="9a5b7-232">System.ServiceModel.Activities.dll</span></span>  
  
2.  <span data-ttu-id="9a5b7-233">Aşağıdaki kod oluşturulan Program.cs dosyasını açın:</span><span class="sxs-lookup"><span data-stu-id="9a5b7-233">Open the generated Program.cs file and the following code:</span></span>  
  
    ```  
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
  
3.  <span data-ttu-id="9a5b7-234">Aşağıdaki app.config dosyasını projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-234">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="9a5b7-235">İstemci uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a5b7-235">Create the client application</span></span>  
  
1.  <span data-ttu-id="9a5b7-236">Adlı yeni bir konsol uygulaması projesi eklemek `Client` çözüm.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="9a5b7-237">System.Activities.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-237">Add a reference to System.Activities.dll.</span></span>  
  
2.  <span data-ttu-id="9a5b7-238">Program.cs dosyasını açın ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-238">Open the program.cs file and add the following code.</span></span>  
  
    ```  
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
  
## <a name="see-also"></a><span data-ttu-id="9a5b7-239">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a5b7-239">See also</span></span>

- [<span data-ttu-id="9a5b7-240">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="9a5b7-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="9a5b7-241">Windows Communication Foundation İşlemleri Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9a5b7-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
