---
description: 'Hakkında daha fazla bilgi edinin: Iş akışı hizmetleri içine ve dışına akan Işlemler'
title: İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: f39740c45dd70fbc06963b8e842f9a01a0393f7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704972"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="29f0b-103">İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="29f0b-103">Flowing Transactions into and out of Workflow Services</span></span>

<span data-ttu-id="29f0b-104">İş akışı hizmetleri ve istemcileri işlemlere katılabilir.</span><span class="sxs-lookup"><span data-stu-id="29f0b-104">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="29f0b-105">Bir hizmet işleminin bir çevresel işlemin bir parçası haline gelmesi için etkinlik içine bir <xref:System.ServiceModel.Activities.Receive> etkinlik koyun <xref:System.ServiceModel.Activities.TransactedReceiveScope> .</span><span class="sxs-lookup"><span data-stu-id="29f0b-105">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="29f0b-106">Bir veya içindeki bir etkinlik tarafından yapılan tüm çağrılar <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.TransactedReceiveScope> çevresel işlem içinde de yapılır.</span><span class="sxs-lookup"><span data-stu-id="29f0b-106">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="29f0b-107">Bir iş akışı istemci uygulaması <xref:System.Activities.Statements.TransactionScope> , etkinlikleri kullanarak ve ortam işlemini kullanarak hizmet işlemlerini çağıran bir ortam işlemi oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="29f0b-107">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="29f0b-108">Bu konu, işlemlere katılan bir iş akışı hizmeti ve iş akışı istemcisi oluşturma konusunda size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="29f0b-108">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="29f0b-109">Bir iş akışı hizmeti örneği bir işlem içinde yüklenirse ve iş akışı bir etkinlik içeriyorsa <xref:System.Activities.Statements.Persist> , iş akışı örneği işlem zaman aşımına uğrayana kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="29f0b-109">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will block until the transaction times out.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="29f0b-110">Her kullanışınızda, <xref:System.ServiceModel.Activities.TransactedReceiveScope> iş akışına tüm alma işlemleri etkinlikleri içinde yerleştirmeniz önerilir <xref:System.ServiceModel.Activities.TransactedReceiveScope> .</span><span class="sxs-lookup"><span data-stu-id="29f0b-110">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="29f0b-111">Kullanırken <xref:System.ServiceModel.Activities.TransactedReceiveScope> ve iletileri yanlış sırada geldiğinde, ilk sipariş dışı ileti teslim edilmeye çalışılırken iş akışı iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="29f0b-111">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="29f0b-112">İş akışınızın iş akışı kimliği her zaman tutarlı bir durdurma noktasında olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="29f0b-112">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="29f0b-113">Bu, iş akışını önceki bir Kalıcılık noktasından yeniden başlatmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="29f0b-113">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="29f0b-114">Paylaşılan kitaplık oluşturma</span><span class="sxs-lookup"><span data-stu-id="29f0b-114">Create a shared library</span></span>  
  
1. <span data-ttu-id="29f0b-115">Yeni boş bir Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="29f0b-115">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="29f0b-116">Adlı yeni bir sınıf kitaplığı projesi ekleyin `Common` .</span><span class="sxs-lookup"><span data-stu-id="29f0b-116">Add a new class library project called `Common`.</span></span> <span data-ttu-id="29f0b-117">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="29f0b-117">Add references to the following assemblies:</span></span>  
  
    - <span data-ttu-id="29f0b-118">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="29f0b-118">System.Activities.dll</span></span>  
  
    - <span data-ttu-id="29f0b-119">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="29f0b-119">System.ServiceModel.dll</span></span>  
  
    - <span data-ttu-id="29f0b-120">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="29f0b-120">System.ServiceModel.Activities.dll</span></span>  
  
    - <span data-ttu-id="29f0b-121">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="29f0b-121">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="29f0b-122">Projeye adlı yeni bir sınıf ekleyin `PrintTransactionInfo` `Common` .</span><span class="sxs-lookup"><span data-stu-id="29f0b-122">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="29f0b-123">Bu sınıf, öğesinden türetilir <xref:System.Activities.NativeActivity> ve yöntemini aşırı yükler <xref:System.Activities.NativeActivity.Execute%2A> .</span><span class="sxs-lookup"><span data-stu-id="29f0b-123">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="29f0b-124">Bu, ortam işlem hakkındaki bilgileri görüntüleyen ve bu konuda kullanılan hizmet ve istemci iş akışlarında kullanılan yerel bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="29f0b-124">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="29f0b-125">Bu etkinliği **araç kutusunun** **ortak** bölümünde kullanılabilir hale getirmek için çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="29f0b-125">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="29f0b-126">İş akışı hizmetini uygulama</span><span class="sxs-lookup"><span data-stu-id="29f0b-126">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="29f0b-127">Projeye adlı yeni bir WCF Iş akışı hizmeti ekleyin `WorkflowService` `Common` .</span><span class="sxs-lookup"><span data-stu-id="29f0b-127">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="29f0b-128">Bunu yapmak için `Common` projeye tıklayın, **Ekle**, **Yeni öğe...** öğesini seçin, **yüklü şablonlar** altında **Iş akışı** ' nı seçin ve **WCF iş akışı hizmeti**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="29f0b-128">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Iş akışı hizmeti ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="29f0b-130">Varsayılan `ReceiveRequest` ve etkinlikleri silin `SendResponse` .</span><span class="sxs-lookup"><span data-stu-id="29f0b-130">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="29f0b-131">Etkinliği sürükleyip etkinliğe bırakın <xref:System.Activities.Statements.WriteLine> `Sequential Service` .</span><span class="sxs-lookup"><span data-stu-id="29f0b-131">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="29f0b-132">Text özelliğini `"Workflow Service starting ..."` Aşağıdaki örnekte gösterildiği gibi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="29f0b-132">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="29f0b-133">! [Sıralı hizmet etkinliğine bir WriteLine etkinliği ekleme (./Media/flowing-Transactions-Into-and-out-of-Workflow-Services/add-writeline-sequential-service.jpg)</span><span class="sxs-lookup"><span data-stu-id="29f0b-133">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="29f0b-134"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlikten sonra sürükleyip bırakın <xref:System.Activities.Statements.WriteLine> .</span><span class="sxs-lookup"><span data-stu-id="29f0b-134">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="29f0b-135"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlik, **araç kutusunun** **mesajlaşma** bölümünde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="29f0b-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="29f0b-136"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlik, iki bölümden oluşan **Istek** ve **gövdeden** oluşur.</span><span class="sxs-lookup"><span data-stu-id="29f0b-136">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="29f0b-137">**İstek** bölümü <xref:System.ServiceModel.Activities.Receive> etkinliği içerir.</span><span class="sxs-lookup"><span data-stu-id="29f0b-137">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="29f0b-138">**Gövde** bölümü bir ileti alındıktan sonra bir işlem içinde yürütülecek etkinlikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="29f0b-138">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![TransactedReceiveScope etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="29f0b-140">Etkinliği seçin <xref:System.ServiceModel.Activities.TransactedReceiveScope> ve **değişkenler** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="29f0b-140">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="29f0b-141">Aşağıdaki değişkenleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29f0b-141">Add the following variables.</span></span>  
  
     ![TransactedReceiveScope 'a değişken ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > <span data-ttu-id="29f0b-143">Varsayılan olarak bulunan veri değişkenini silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29f0b-143">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="29f0b-144">Ayrıca var olan tanıtıcı değişkenini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29f0b-144">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="29f0b-145">Etkinliğin <xref:System.ServiceModel.Activities.Receive> **istek** bölümü içinde bir etkinliği sürükleyip bırakın <xref:System.ServiceModel.Activities.TransactedReceiveScope> .</span><span class="sxs-lookup"><span data-stu-id="29f0b-145">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="29f0b-146">Aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="29f0b-146">Set the following properties:</span></span>  
  
    |<span data-ttu-id="29f0b-147">Özellik</span><span class="sxs-lookup"><span data-stu-id="29f0b-147">Property</span></span>|<span data-ttu-id="29f0b-148">Değer</span><span class="sxs-lookup"><span data-stu-id="29f0b-148">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="29f0b-149">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="29f0b-149">CanCreateInstance</span></span>|<span data-ttu-id="29f0b-150">True (onay kutusunu işaretleyin)</span><span class="sxs-lookup"><span data-stu-id="29f0b-150">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="29f0b-151">OperationName</span><span class="sxs-lookup"><span data-stu-id="29f0b-151">OperationName</span></span>|<span data-ttu-id="29f0b-152">StartSample</span><span class="sxs-lookup"><span data-stu-id="29f0b-152">StartSample</span></span>|  
    |<span data-ttu-id="29f0b-153">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="29f0b-153">ServiceContractName</span></span>|<span data-ttu-id="29f0b-154">Itransactionsample</span><span class="sxs-lookup"><span data-stu-id="29f0b-154">ITransactionSample</span></span>|  
  
     <span data-ttu-id="29f0b-155">İş akışı şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="29f0b-155">The workflow should look like this:</span></span>  
  
     ![Alma etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="29f0b-157">Etkinlikteki **tanımla...** bağlantısına tıklayın <xref:System.ServiceModel.Activities.Receive> ve aşağıdaki ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="29f0b-157">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Alma etkinliği için ileti ayarlarını ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="29f0b-159">Bir etkinliği sürükleyin ve ' <xref:System.Activities.Statements.Sequence> ın gövde bölümüne bırakın <xref:System.ServiceModel.Activities.TransactedReceiveScope> .</span><span class="sxs-lookup"><span data-stu-id="29f0b-159">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="29f0b-160">Etkinlik içinde <xref:System.Activities.Statements.Sequence> iki etkinliği sürükleyip bırakın <xref:System.Activities.Statements.WriteLine> ve <xref:System.Activities.Statements.WriteLine.Text%2A> Aşağıdaki tabloda gösterildiği gibi özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="29f0b-160">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="29f0b-161">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="29f0b-161">Activity</span></span>|<span data-ttu-id="29f0b-162">Değer</span><span class="sxs-lookup"><span data-stu-id="29f0b-162">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="29f0b-163">1. WriteLine</span><span class="sxs-lookup"><span data-stu-id="29f0b-163">1st WriteLine</span></span>|<span data-ttu-id="29f0b-164">"Hizmet: alma tamamlandı"</span><span class="sxs-lookup"><span data-stu-id="29f0b-164">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="29f0b-165">2. WriteLine</span><span class="sxs-lookup"><span data-stu-id="29f0b-165">2nd WriteLine</span></span>|<span data-ttu-id="29f0b-166">"Hizmet: alındı =" + requestMessage</span><span class="sxs-lookup"><span data-stu-id="29f0b-166">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="29f0b-167">İş akışı artık şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="29f0b-167">The workflow should now look like this:</span></span>  
  
     ![WriteLine etkinlikleri eklendikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="29f0b-169">Etkinliğin `PrintTransactionInfo` gövdesinde bulunan ikinci etkinlikten sonra etkinliği sürükleyip bırakın <xref:System.Activities.Statements.WriteLine>  <xref:System.ServiceModel.Activities.TransactedReceiveScope> .</span><span class="sxs-lookup"><span data-stu-id="29f0b-169">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![PrintTransactionInfo eklendikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="29f0b-171"><xref:System.Activities.Statements.Assign>Etkinlikten sonra bir etkinliği sürükleyip bırakın `PrintTransactionInfo` ve aşağıdaki tabloya göre özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="29f0b-171">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="29f0b-172">Özellik</span><span class="sxs-lookup"><span data-stu-id="29f0b-172">Property</span></span>|<span data-ttu-id="29f0b-173">Değer</span><span class="sxs-lookup"><span data-stu-id="29f0b-173">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="29f0b-174">Amaç</span><span class="sxs-lookup"><span data-stu-id="29f0b-174">To</span></span>|<span data-ttu-id="29f0b-175">replyMessage</span><span class="sxs-lookup"><span data-stu-id="29f0b-175">replyMessage</span></span>|  
    |<span data-ttu-id="29f0b-176">Değer</span><span class="sxs-lookup"><span data-stu-id="29f0b-176">Value</span></span>|<span data-ttu-id="29f0b-177">"Hizmet: Yanıt gönderiliyor."</span><span class="sxs-lookup"><span data-stu-id="29f0b-177">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="29f0b-178"><xref:System.Activities.Statements.WriteLine>Etkinlikten sonra bir etkinliği sürükleyip bırakın <xref:System.Activities.Statements.Assign> ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Service: BEGIN Reply" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="29f0b-178">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="29f0b-179">İş akışı artık şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="29f0b-179">The workflow should now look like this:</span></span>  
  
     ![Assign ve WriteLine eklendikten sonra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="29f0b-181">Etkinliğe sağ tıklayın <xref:System.ServiceModel.Activities.Receive> ve **SendReply oluştur** ' u seçin ve son <xref:System.Activities.Statements.WriteLine> etkinlikten sonra yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="29f0b-181">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="29f0b-182">Etkinlikteki **tanımla...** bağlantısına tıklayın `SendReplyToReceive` ve aşağıdaki ayarları yapın.</span><span class="sxs-lookup"><span data-stu-id="29f0b-182">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Yanıt iletisi ayarları](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="29f0b-184"><xref:System.Activities.Statements.WriteLine>Etkinlikten sonra bir etkinliği sürükleyip bırakın `SendReplyToReceive` ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Service: Reply gönderildi" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="29f0b-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="29f0b-185"><xref:System.Activities.Statements.WriteLine>İş akışının alt kısmındaki bir etkinliği sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Service: Workflow bitiyor, ÇıKMAK için ENTER tuşuna basın" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="29f0b-185">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="29f0b-186">Tamamlanmış hizmet iş akışı şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="29f0b-186">The completed service workflow should look like this:</span></span>  
  
     ![Hizmet Iş akışını doldurun](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="29f0b-188">İş akışı istemcisini uygulama</span><span class="sxs-lookup"><span data-stu-id="29f0b-188">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="29f0b-189">Projeye adlı yeni bir WCF Iş akışı uygulaması ekleyin `WorkflowClient` `Common` .</span><span class="sxs-lookup"><span data-stu-id="29f0b-189">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="29f0b-190">Bunu yapmak için projeye sağ tıklayın `Common` , **Ekle**, **Yeni öğe...** öğesini seçin, **yüklü şablonlar** altında **iş akışı** ' nı seçin ve **etkinlik**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="29f0b-190">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Etkinlik projesi ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="29f0b-192"><xref:System.Activities.Statements.Sequence>Tasarım yüzeyine bir etkinliği sürükleyip bırakın.</span><span class="sxs-lookup"><span data-stu-id="29f0b-192">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="29f0b-193">Etkinlik içinde <xref:System.Activities.Statements.Sequence> bir etkinliği sürükleyip bırakın <xref:System.Activities.Statements.WriteLine> ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini olarak ayarlayın `"Client: Workflow starting"` .</span><span class="sxs-lookup"><span data-stu-id="29f0b-193">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="29f0b-194">İş akışı artık şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="29f0b-194">The workflow should now look like this:</span></span>  
  
     ![WriteLine etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="29f0b-196"><xref:System.Activities.Statements.TransactionScope>Etkinlikten sonra bir etkinliği sürükleyip bırakın <xref:System.Activities.Statements.WriteLine> .</span><span class="sxs-lookup"><span data-stu-id="29f0b-196">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="29f0b-197">Etkinliği seçin <xref:System.Activities.Statements.TransactionScope> , değişkenler düğmesine tıklayın ve aşağıdaki değişkenleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29f0b-197">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![TransactionScope 'a değişken ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="29f0b-199">Etkinliğin gövdesine bir etkinlik sürükleyip bırakın <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="29f0b-199">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="29f0b-200">İçindeki bir etkinliği sürükleyip bırakma `PrintTransactionInfo`<xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="29f0b-200">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7. <span data-ttu-id="29f0b-201"><xref:System.Activities.Statements.WriteLine>Etkinlikten sonra bir etkinliği sürükleyip bırakın `PrintTransactionInfo` ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Client: Send başlatılıyor" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="29f0b-201">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="29f0b-202">İş akışı artık şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="29f0b-202">The workflow should now look like this:</span></span>  
  
     ![Istemci ekleniyor: gönderme etkinlikleri başlatılıyor](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="29f0b-204"><xref:System.ServiceModel.Activities.Send>Etkinlikten sonra bir etkinliği sürükleyip bırakın <xref:System.Activities.Statements.Assign> ve aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="29f0b-204">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="29f0b-205">Özellik</span><span class="sxs-lookup"><span data-stu-id="29f0b-205">Property</span></span>|<span data-ttu-id="29f0b-206">Değer</span><span class="sxs-lookup"><span data-stu-id="29f0b-206">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="29f0b-207">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="29f0b-207">EndpointConfigurationName</span></span>|<span data-ttu-id="29f0b-208">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="29f0b-208">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="29f0b-209">OperationName</span><span class="sxs-lookup"><span data-stu-id="29f0b-209">OperationName</span></span>|<span data-ttu-id="29f0b-210">StartSample</span><span class="sxs-lookup"><span data-stu-id="29f0b-210">StartSample</span></span>|  
    |<span data-ttu-id="29f0b-211">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="29f0b-211">ServiceContractName</span></span>|<span data-ttu-id="29f0b-212">Itransactionsample</span><span class="sxs-lookup"><span data-stu-id="29f0b-212">ITransactionSample</span></span>|  
  
     <span data-ttu-id="29f0b-213">İş akışı artık şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="29f0b-213">The workflow should now look like this:</span></span>  
  
     ![Gönderme etkinliği özelliklerini ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="29f0b-215">**Tanımla...** bağlantısına tıklayın ve aşağıdaki ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="29f0b-215">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Etkinlik iletisi ayarlarını gönder](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="29f0b-217">Etkinliğe sağ tıklayın <xref:System.ServiceModel.Activities.Send> ve **ReceiveReply oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="29f0b-217">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="29f0b-218">Etkinlik <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikten sonra otomatik olarak yerleştirilecek <xref:System.ServiceModel.Activities.Send> .</span><span class="sxs-lookup"><span data-stu-id="29f0b-218">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="29f0b-219">Tanımla... öğesine tıklayın ReceiveReplyForSend etkinliğinin bağlantısını yapın ve aşağıdaki ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="29f0b-219">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![ReceiveForSend ileti ayarlarını ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="29f0b-221"><xref:System.Activities.Statements.WriteLine>Ve etkinlikleri arasında bir etkinlik sürükleyip bırakın <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "istemci: gönderme Tamam" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="29f0b-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="29f0b-222"><xref:System.Activities.Statements.WriteLine>Etkinlikten sonra bir etkinliği sürükleyip bırakın <xref:System.ServiceModel.Activities.ReceiveReply> ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Istemci tarafı: Yanıtla alındı =" + ReplyMessage olarak ayarlayın</span><span class="sxs-lookup"><span data-stu-id="29f0b-222">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="29f0b-223">`PrintTransactionInfo`Etkinlikten sonra bir etkinliği sürükleyip bırakın <xref:System.Activities.Statements.WriteLine> .</span><span class="sxs-lookup"><span data-stu-id="29f0b-223">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="29f0b-224"><xref:System.Activities.Statements.WriteLine>İş akışının sonundaki bir etkinliği sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "istemci iş akışı bitişi" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="29f0b-224">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="29f0b-225">Tamamlanan istemci iş akışı aşağıdaki diyagram gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="29f0b-225">The completed client workflow should look like the following diagram.</span></span>  
  
     ![Tamamlanan istemci iş akışı](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="29f0b-227">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="29f0b-227">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="29f0b-228">Hizmet uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="29f0b-228">Create the Service application</span></span>  
  
1. <span data-ttu-id="29f0b-229">Çözüme adlı yeni bir konsol uygulaması projesi ekleyin `Service` .</span><span class="sxs-lookup"><span data-stu-id="29f0b-229">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="29f0b-230">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="29f0b-230">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="29f0b-231">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="29f0b-231">System.Activities.dll</span></span>  
  
    2. <span data-ttu-id="29f0b-232">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="29f0b-232">System.ServiceModel.dll</span></span>  
  
    3. <span data-ttu-id="29f0b-233">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="29f0b-233">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="29f0b-234">Oluşturulan Program.cs dosyasını ve aşağıdaki kodu açın:</span><span class="sxs-lookup"><span data-stu-id="29f0b-234">Open the generated Program.cs file and the following code:</span></span>  
  
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
  
3. <span data-ttu-id="29f0b-235">Aşağıdaki app.config dosyasını projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29f0b-235">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="29f0b-236">İstemci uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="29f0b-236">Create the client application</span></span>  
  
1. <span data-ttu-id="29f0b-237">Çözüme adlı yeni bir konsol uygulaması projesi ekleyin `Client` .</span><span class="sxs-lookup"><span data-stu-id="29f0b-237">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="29f0b-238">System.Activities.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29f0b-238">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="29f0b-239">Program.cs dosyasını açın ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29f0b-239">Open the program.cs file and add the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="29f0b-240">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29f0b-240">See also</span></span>

- [<span data-ttu-id="29f0b-241">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="29f0b-241">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="29f0b-242">Windows Communication Foundation İşlemleri Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="29f0b-242">Windows Communication Foundation Transactions Overview</span></span>](transactions-overview.md)
