---
title: "İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a093c2bfb0d7e60c3edc4a6ab04c8a7b7e38601
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="5ed44-102">İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="5ed44-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="5ed44-103">İş akışı hizmetleri ve istemciler işlemlerde yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="5ed44-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="5ed44-104">Bir hizmet işlemi ortam bir işlemin parçası olmaya yerleştirin bir <xref:System.ServiceModel.Activities.Receive> içinde etkinlik bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5ed44-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="5ed44-105">Tarafından yapılan çağrılar bir <xref:System.ServiceModel.Activities.Send> veya <xref:System.ServiceModel.Activities.SendReply> içinde etkinlik <xref:System.ServiceModel.Activities.TransactedReceiveScope> ortam işlem içinde da yapılır.</span><span class="sxs-lookup"><span data-stu-id="5ed44-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="5ed44-106">Bir iş akışı istemci uygulamasını kullanarak bir ortam işlem oluşturabilirsiniz <xref:System.Activities.Statements.TransactionScope> ortam hareket kullanarak etkinliği ve çağrı hizmet işlemleri.</span><span class="sxs-lookup"><span data-stu-id="5ed44-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="5ed44-107">Bu konu bir iş akışı hizmeti ve katılmak iş akışı istemci işlemleri oluşturmada size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="5ed44-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="5ed44-108">Bir iş akışı hizmeti örneği bir işlem içinde yüklenir ve iş akışı içeren bir <xref:System.Activities.Statements.Persist> etkinlik, iş akışı örneği askıda işlem zaman aşımına uğrayana kadar.</span><span class="sxs-lookup"><span data-stu-id="5ed44-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will hang until the transaction times out.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5ed44-109">Kullandığınız her bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> iş akışı tüm Receives yerleştirmek için önerilen <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="5ed44-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5ed44-110">Kullanırken <xref:System.ServiceModel.Activities.TransactedReceiveScope> ve iletiler geldiğinde yanlış sırayla, iş akışı, ilk bozuk ileti teslim çalışılırken iptal edilecek.</span><span class="sxs-lookup"><span data-stu-id="5ed44-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="5ed44-111">İş akışı boş kalır, iş akışınızı her zaman tutarlı noktası durduruluyor emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ed44-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="5ed44-112">Bu iş akışı iptal önceki Kalıcılık noktası iş akışını yeniden başlatmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5ed44-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="5ed44-113">Paylaşılan bir kitaplık oluşturma</span><span class="sxs-lookup"><span data-stu-id="5ed44-113">Create a shared library</span></span>  
  
1.  <span data-ttu-id="5ed44-114">Yeni bir boş Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5ed44-114">Create a new empty Visual Studio Solution.</span></span>  
  
2.  <span data-ttu-id="5ed44-115">Adlı yeni bir sınıf kitaplığı proje ekleme `Common`.</span><span class="sxs-lookup"><span data-stu-id="5ed44-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="5ed44-116">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5ed44-116">Add references to the following assemblies:</span></span>  
  
    -   <span data-ttu-id="5ed44-117">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="5ed44-117">System.Activities.dll</span></span>  
  
    -   <span data-ttu-id="5ed44-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="5ed44-118">System.ServiceModel.dll</span></span>  
  
    -   <span data-ttu-id="5ed44-119">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="5ed44-119">System.ServiceModel.Activities.dll</span></span>  
  
    -   <span data-ttu-id="5ed44-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="5ed44-120">System.Transactions.dll</span></span>  
  
3.  <span data-ttu-id="5ed44-121">Adlı yeni bir sınıf ekleyin `PrintTransactionInfo` için `Common` projesi.</span><span class="sxs-lookup"><span data-stu-id="5ed44-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="5ed44-122">Bu sınıfın türetildiği <xref:System.Activities.NativeActivity> ve overloads <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5ed44-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="5ed44-123">Bu ortam işlem bilgilerini görüntüler ve bu konuda kullanılan hem hizmet hem de istemci iş akışlarında kullanılan yerel bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="5ed44-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="5ed44-124">Bu etkinlik olarak kullanılabilir hale getirmek çözümü derlemek **ortak** bölümünü **araç**.</span><span class="sxs-lookup"><span data-stu-id="5ed44-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="5ed44-125">İş akışı hizmeti uygulama</span><span class="sxs-lookup"><span data-stu-id="5ed44-125">Implement the workflow service</span></span>  
  
1.  <span data-ttu-id="5ed44-126">Yeni bir ekleme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] adlı iş akışı hizmeti `WorkflowService` için `Common` projesi.</span><span class="sxs-lookup"><span data-stu-id="5ed44-126">Add a new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="5ed44-127">Bu sağ tıklatma yapmak için `Common` proje, select **Ekle**, **yeni öğe...** Seçin **iş akışı** altında **yüklü şablonlar** seçip **WCF iş akışı hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="5ed44-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     <span data-ttu-id="5ed44-128">![Bir iş akışı hizmeti ekleme](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")</span><span class="sxs-lookup"><span data-stu-id="5ed44-128">![Adding a Workflow Service](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")</span></span>  
  
2.  <span data-ttu-id="5ed44-129">Varsayılan silme `ReceiveRequest` ve `SendResponse` etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="5ed44-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3.  <span data-ttu-id="5ed44-130">Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> etkinliğini `Sequential Service` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5ed44-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="5ed44-131">Text özelliğini `"Workflow Service starting ..."` aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5ed44-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="5ed44-132">![WriteLine etkinlik ekleme](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")</span><span class="sxs-lookup"><span data-stu-id="5ed44-132">![Adding a WriteLine activity](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")</span></span>  
  
4.  <span data-ttu-id="5ed44-133">Sürükleme ve bırakma bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> sonra <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5ed44-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="5ed44-134"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik bulunabilir **ileti** bölümünü **araç**.</span><span class="sxs-lookup"><span data-stu-id="5ed44-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="5ed44-135"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik iki bölümden oluşan **isteği** ve **gövde**.</span><span class="sxs-lookup"><span data-stu-id="5ed44-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="5ed44-136">**İsteği** bölüm içerir <xref:System.ServiceModel.Activities.Receive> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5ed44-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="5ed44-137">**Gövde** bölüm, bir işlem içinde bir ileti alındı sonra yürütülecek etkinlikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5ed44-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     <span data-ttu-id="5ed44-138">![TransactedReceiveScope etkinlik ekleme](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TRS")</span><span class="sxs-lookup"><span data-stu-id="5ed44-138">![Adding a TransactedReceiveScope activity](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TRS")</span></span>  
  
5.  <span data-ttu-id="5ed44-139">Seçin <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği ve tıklatın **değişkenleri** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5ed44-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="5ed44-140">Aşağıdaki değişkenler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5ed44-140">Add the following variables.</span></span>  
  
     <span data-ttu-id="5ed44-141">![Değişkenleri TransactedReceiveScope ekleme](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")</span><span class="sxs-lookup"><span data-stu-id="5ed44-141">![Adding Variables to the TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5ed44-142">Varsayılan olarak var olan veri değişken silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ed44-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="5ed44-143">Varolan bir tanıtıcı değişkeni de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ed44-143">You can also use the existing handle variable.</span></span>  
  
6.  <span data-ttu-id="5ed44-144">Sürükleme ve bırakma bir <xref:System.ServiceModel.Activities.Receive> içinde etkinlik **isteği** bölümünü <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5ed44-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="5ed44-145">Aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5ed44-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="5ed44-146">Özellik</span><span class="sxs-lookup"><span data-stu-id="5ed44-146">Property</span></span>|<span data-ttu-id="5ed44-147">Değer</span><span class="sxs-lookup"><span data-stu-id="5ed44-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="5ed44-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="5ed44-148">CanCreateInstance</span></span>|<span data-ttu-id="5ed44-149">TRUE (onay kutusunu işaretleyin)</span><span class="sxs-lookup"><span data-stu-id="5ed44-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="5ed44-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="5ed44-150">OperationName</span></span>|<span data-ttu-id="5ed44-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="5ed44-151">StartSample</span></span>|  
    |<span data-ttu-id="5ed44-152">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="5ed44-152">ServiceContractName</span></span>|<span data-ttu-id="5ed44-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="5ed44-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="5ed44-154">İş akışını aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="5ed44-154">The workflow should look like this:</span></span>  
  
     <span data-ttu-id="5ed44-155">![Alma etkinlik ekleme](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")</span><span class="sxs-lookup"><span data-stu-id="5ed44-155">![Adding a Receive activity](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")</span></span>  
  
7.  <span data-ttu-id="5ed44-156">Tıklatın **tanımlayın...**  bağlamak <xref:System.ServiceModel.Activities.Receive> etkinliği ve aşağıdaki ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="5ed44-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     <span data-ttu-id="5ed44-157">![İleti ayarları alma etkinliğinin ayarı](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="5ed44-157">![Setting message settings for the Recieve activity](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")</span></span>  
  
8.  <span data-ttu-id="5ed44-158">Sürükleme ve bırakma bir <xref:System.Activities.Statements.Sequence> gövde bölümünü etkinliğini <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="5ed44-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="5ed44-159">İçinde <xref:System.Activities.Statements.Sequence> etkinlik sürükleyip iki <xref:System.Activities.Statements.WriteLine> etkinlikleri ve kümesi <xref:System.Activities.Statements.WriteLine.Text%2A> aşağıdaki tabloda gösterildiği gibi özellikler.</span><span class="sxs-lookup"><span data-stu-id="5ed44-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="5ed44-160">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="5ed44-160">Activity</span></span>|<span data-ttu-id="5ed44-161">Değer</span><span class="sxs-lookup"><span data-stu-id="5ed44-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="5ed44-162">1 WriteLine</span><span class="sxs-lookup"><span data-stu-id="5ed44-162">1st WriteLine</span></span>|<span data-ttu-id="5ed44-163">"Hizmet: tamamlanmış alırsınız"</span><span class="sxs-lookup"><span data-stu-id="5ed44-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="5ed44-164">2 WriteLine</span><span class="sxs-lookup"><span data-stu-id="5ed44-164">2nd WriteLine</span></span>|<span data-ttu-id="5ed44-165">"Hizmet: alınan =" + requestMessage</span><span class="sxs-lookup"><span data-stu-id="5ed44-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="5ed44-166">İş akışı gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="5ed44-166">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="5ed44-167">![WriteLine etkinlikleri ekleme](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")</span><span class="sxs-lookup"><span data-stu-id="5ed44-167">![Adding WriteLine activities](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")</span></span>  
  
9. <span data-ttu-id="5ed44-168">Sürükleme ve bırakma `PrintTransactionInfo` etkinlikten saniye sonra <xref:System.Activities.Statements.WriteLine> etkinliğinde **gövde** içinde <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5ed44-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     <span data-ttu-id="5ed44-169">![PrintTransactionInfo ekledikten sonra](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")</span><span class="sxs-lookup"><span data-stu-id="5ed44-169">![After adding PrintTransactionInfo](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")</span></span>  
  
10. <span data-ttu-id="5ed44-170">Sürükleme ve bırakma bir <xref:System.Activities.Statements.Assign> etkinlikten sonra `PrintTransactionInfo` etkinliği ve özelliklerini aşağıdaki tabloya göre ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5ed44-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="5ed44-171">Özellik</span><span class="sxs-lookup"><span data-stu-id="5ed44-171">Property</span></span>|<span data-ttu-id="5ed44-172">Değer</span><span class="sxs-lookup"><span data-stu-id="5ed44-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="5ed44-173">Bitiş</span><span class="sxs-lookup"><span data-stu-id="5ed44-173">To</span></span>|<span data-ttu-id="5ed44-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="5ed44-174">replyMessage</span></span>|  
    |<span data-ttu-id="5ed44-175">Değer</span><span class="sxs-lookup"><span data-stu-id="5ed44-175">Value</span></span>|<span data-ttu-id="5ed44-176">"Hizmet: yanıt gönderme."</span><span class="sxs-lookup"><span data-stu-id="5ed44-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="5ed44-177">Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra <xref:System.Activities.Statements.Assign> etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğine "Hizmet: başlamak yanıt."</span><span class="sxs-lookup"><span data-stu-id="5ed44-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="5ed44-178">İş akışı gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="5ed44-178">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="5ed44-179">![Atama ve WriteLine ekledikten sonra](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")</span><span class="sxs-lookup"><span data-stu-id="5ed44-179">![After adding Assign and WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")</span></span>  
  
12. <span data-ttu-id="5ed44-180">Sağ tıklayın <xref:System.ServiceModel.Activities.Receive> etkinliği ve select **oluşturma SendReply** ve sonra son yapıştırın <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5ed44-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="5ed44-181">Tıklatın **tanımlayın...**  bağlamak `SendReplyToReceive` etkinliği ve aşağıdaki ayarları yapın.</span><span class="sxs-lookup"><span data-stu-id="5ed44-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     <span data-ttu-id="5ed44-182">![Yanıt iletisi ayarları](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="5ed44-182">![Reply message settings](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")</span></span>  
  
13. <span data-ttu-id="5ed44-183">Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra `SendReplyToReceive` etkinliği ve kümesi var. <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğine "Hizmet: yanıt gönderildi."</span><span class="sxs-lookup"><span data-stu-id="5ed44-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="5ed44-184">Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> alt kümesi ve iş akışı etkinlik kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğine "Hizmet: iş akışı sona erer, çıkmak için ENTER tuşuna basın."</span><span class="sxs-lookup"><span data-stu-id="5ed44-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="5ed44-185">Tamamlanmış hizmet iş akışı aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="5ed44-185">The completed service workflow should look like this:</span></span>  
  
     <span data-ttu-id="5ed44-186">![Hizmeti iş akışı tamamlamak](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")</span><span class="sxs-lookup"><span data-stu-id="5ed44-186">![Complete Service Workflow](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")</span></span>  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="5ed44-187">İş akışı istemcisini uygulama</span><span class="sxs-lookup"><span data-stu-id="5ed44-187">Implement the workflow client</span></span>  
  
1.  <span data-ttu-id="5ed44-188">Adlı yeni bir WCF iş akışı uygulama eklemek `WorkflowClient` için `Common` projesi.</span><span class="sxs-lookup"><span data-stu-id="5ed44-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="5ed44-189">Bu sağ tıklatma yapmak için `Common` proje, select **Ekle**, **yeni öğe...** Seçin **iş akışı** altında **yüklü şablonlar** seçip **etkinlik**.</span><span class="sxs-lookup"><span data-stu-id="5ed44-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     <span data-ttu-id="5ed44-190">![Bir etkinlik proje ekleyin](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")</span><span class="sxs-lookup"><span data-stu-id="5ed44-190">![Add an Activity project](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")</span></span>  
  
2.  <span data-ttu-id="5ed44-191">Sürükleme ve bırakma bir <xref:System.Activities.Statements.Sequence> tasarım yüzeyine etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5ed44-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3.  <span data-ttu-id="5ed44-192">İçinde <xref:System.Activities.Statements.Sequence> etkinlik sürükle ve bırak bir <xref:System.Activities.Statements.WriteLine> etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğine `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="5ed44-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="5ed44-193">İş akışı gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="5ed44-193">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="5ed44-194">![WriteLine etkinlik eklemek](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")</span><span class="sxs-lookup"><span data-stu-id="5ed44-194">![Add a WriteLine activity](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")</span></span>  
  
4.  <span data-ttu-id="5ed44-195">Sürükleme ve bırakma bir <xref:System.Activities.Statements.TransactionScope> etkinlikten sonra <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5ed44-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="5ed44-196">Seçin <xref:System.Activities.Statements.TransactionScope> etkinliği, değişkenleri düğmesine tıklayın ve aşağıdaki değişkenleri eklemek tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5ed44-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     <span data-ttu-id="5ed44-197">![TransactionScope değişkenleri eklemek](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")</span><span class="sxs-lookup"><span data-stu-id="5ed44-197">![Add variables to the TransactionScope](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")</span></span>  
  
5.  <span data-ttu-id="5ed44-198">Sürükleme ve bırakma bir <xref:System.Activities.Statements.Sequence> gövdesine etkinlik <xref:System.Activities.Statements.TransactionScope> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5ed44-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6.  <span data-ttu-id="5ed44-199">Sürükleme ve bırakma bir `PrintTransactionInfo` içinde etkinlik<xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="5ed44-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7.  <span data-ttu-id="5ed44-200">Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra `PrintTransactionInfo` etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> "İstemci başına: Gönder" özelliğine.</span><span class="sxs-lookup"><span data-stu-id="5ed44-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="5ed44-201">İş akışı gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="5ed44-201">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="5ed44-202">![Etkinlikler ekleme](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")</span><span class="sxs-lookup"><span data-stu-id="5ed44-202">![Adding activities](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")</span></span>  
  
8.  <span data-ttu-id="5ed44-203">Sürükleme ve bırakma bir <xref:System.ServiceModel.Activities.Send> etkinlikten sonra <xref:System.Activities.Statements.Assign> etkinliği ve aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5ed44-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="5ed44-204">Özellik</span><span class="sxs-lookup"><span data-stu-id="5ed44-204">Property</span></span>|<span data-ttu-id="5ed44-205">Değer</span><span class="sxs-lookup"><span data-stu-id="5ed44-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="5ed44-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="5ed44-206">EndpointConfigurationName</span></span>|<span data-ttu-id="5ed44-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="5ed44-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="5ed44-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="5ed44-208">OperationName</span></span>|<span data-ttu-id="5ed44-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="5ed44-209">StartSample</span></span>|  
    |<span data-ttu-id="5ed44-210">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="5ed44-210">ServiceContractName</span></span>|<span data-ttu-id="5ed44-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="5ed44-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="5ed44-212">İş akışı gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="5ed44-212">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="5ed44-213">![Gönder etkinliği özellikleri ayarlama](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")</span><span class="sxs-lookup"><span data-stu-id="5ed44-213">![Setting the Send activity properties](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")</span></span>  
  
9. <span data-ttu-id="5ed44-214">Tıklatın **tanımlayın...**  bağlamak ve aşağıdaki ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="5ed44-214">Click the **Define...** link and make the following settings:</span></span>  
  
     <span data-ttu-id="5ed44-215">![İleti ayarları etkinlik Gönder](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="5ed44-215">![Send activity message settings](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")</span></span>  
  
10. <span data-ttu-id="5ed44-216">Sağ tıklayın <xref:System.ServiceModel.Activities.Send> etkinliği ve select **oluşturma ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="5ed44-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="5ed44-217"><xref:System.ServiceModel.Activities.ReceiveReply> Etkinlik otomatik olarak yerleştirilecek sonra <xref:System.ServiceModel.Activities.Send> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5ed44-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="5ed44-218">Tanımla...'yı tıklatın bağlantı ReceiveReplyForSend faaliyete ve aşağıdaki ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="5ed44-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     <span data-ttu-id="5ed44-219">![ReceiveForSend ileti ayarları ayarı](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="5ed44-219">![Setting the ReceiveForSend message settings](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")</span></span>  
  
12. <span data-ttu-id="5ed44-220">Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> etkinlik arasında <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğine "İstemci: tamamını göndermek."</span><span class="sxs-lookup"><span data-stu-id="5ed44-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="5ed44-221">Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> etkinlikten sonra <xref:System.ServiceModel.Activities.ReceiveReply> etkinliği ve kümesi kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğine "istemci tarafında: alınan yanıt =" + replyMessage</span><span class="sxs-lookup"><span data-stu-id="5ed44-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="5ed44-222">Sürükleme ve bırakma bir `PrintTransactionInfo` etkinlikten sonra <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5ed44-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="5ed44-223">Sürükleme ve bırakma bir <xref:System.Activities.Statements.WriteLine> kümesi ve iş akışının sonunda etkinlik kendi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "İstemci iş akışı sona erer."</span><span class="sxs-lookup"><span data-stu-id="5ed44-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="5ed44-224">Tamamlanan istemci iş akışı aşağıdaki diyagramda gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="5ed44-224">The completed client workflow should look like the following diagram.</span></span>  
  
     <span data-ttu-id="5ed44-225">![Tamamlanan istemci workfliow](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")</span><span class="sxs-lookup"><span data-stu-id="5ed44-225">![The completed client workfliow](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")</span></span>  
  
16. <span data-ttu-id="5ed44-226">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5ed44-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="5ed44-227">Hizmet Uygulaması Oluştur</span><span class="sxs-lookup"><span data-stu-id="5ed44-227">Create the Service application</span></span>  
  
1.  <span data-ttu-id="5ed44-228">Adlı yeni bir konsol uygulaması projesi eklemek `Service` çözüme.</span><span class="sxs-lookup"><span data-stu-id="5ed44-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="5ed44-229">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5ed44-229">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="5ed44-230">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="5ed44-230">System.Activities.dll</span></span>  
  
    2.  <span data-ttu-id="5ed44-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="5ed44-231">System.ServiceModel.dll</span></span>  
  
    3.  <span data-ttu-id="5ed44-232">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="5ed44-232">System.ServiceModel.Activities.dll</span></span>  
  
2.  <span data-ttu-id="5ed44-233">Oluşturulan Program.cs dosyasının ve aşağıdaki kodu açın:</span><span class="sxs-lookup"><span data-stu-id="5ed44-233">Open the generated Program.cs file and the following code:</span></span>  
  
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
  
3.  <span data-ttu-id="5ed44-234">Aşağıdaki app.config dosyası projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5ed44-234">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="5ed44-235">İstemci uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="5ed44-235">Create the client application</span></span>  
  
1.  <span data-ttu-id="5ed44-236">Adlı yeni bir konsol uygulaması projesi eklemek `Client` çözüme.</span><span class="sxs-lookup"><span data-stu-id="5ed44-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="5ed44-237">System.Activities.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5ed44-237">Add a reference to System.Activities.dll.</span></span>  
  
2.  <span data-ttu-id="5ed44-238">Program.cs dosyasını açın ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5ed44-238">Open the program.cs file and add the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ed44-239">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ed44-239">See Also</span></span>  
 [<span data-ttu-id="5ed44-240">İş akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="5ed44-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="5ed44-241">Windows Communication Foundation işlemleri genel bakış</span><span class="sxs-lookup"><span data-stu-id="5ed44-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)  
 [<span data-ttu-id="5ed44-242">TransactedReceiveScope kullanımı</span><span class="sxs-lookup"><span data-stu-id="5ed44-242">Use of TransactedReceiveScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)
