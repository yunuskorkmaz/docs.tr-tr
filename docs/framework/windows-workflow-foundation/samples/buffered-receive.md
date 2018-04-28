---
title: Arabelleğe alma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: abec64433d10a23dca6186c6c9a553bbed12a017
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="buffered-receive"></a><span data-ttu-id="3b045-102">Arabelleğe alma</span><span class="sxs-lookup"><span data-stu-id="3b045-102">Buffered Receive</span></span>
<span data-ttu-id="3b045-103">Bu örnek, ayarlama ve Windows Workflow Foundation (WF) arabellekli alma özelliği yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b045-103">This sample demonstrates how to set up and configure the buffered receive feature in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="3b045-104">Arabelleğe alma iletilerin alındığını sırası hakkında endişelenmenize gerek olmadan bir iş akışı oluşturmak iş akışı Yazar verir.</span><span class="sxs-lookup"><span data-stu-id="3b045-104">Buffered receive allows the workflow author to create a workflow without having to worry about the order in which messages are received.</span></span> <span data-ttu-id="3b045-105">Arabellekli alma özelliği, yerel olarak iletileri arabelleğe alır ve iş akışı almaya hazır olduğunda bunları sunar.</span><span class="sxs-lookup"><span data-stu-id="3b045-105">The buffered receive feature buffers messages locally and delivers them when the workflow is ready to receive them.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3b045-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="3b045-106">Demonstrates</span></span>  
 <span data-ttu-id="3b045-107">Düzen dışı ileti işleme arabelleğe almak kullanarak Mesajlaşma etkinlikleriyle.</span><span class="sxs-lookup"><span data-stu-id="3b045-107">Out-of-order message processing using buffered receive with messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3b045-108">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b045-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3b045-109">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3b045-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3b045-110">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="3b045-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3b045-111">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3b045-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a><span data-ttu-id="3b045-112">Tartışma</span><span class="sxs-lookup"><span data-stu-id="3b045-112">Discussion</span></span>  
 <span data-ttu-id="3b045-113">Bu örnekte, bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti kullanılarak gerçekleştirilir [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ve bir dizi <xref:System.ServiceModel.Activities.Receive> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="3b045-113">In this sample, a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service is implemented using [!INCLUDE[wf1](../../../../includes/wf1-md.md)] and has a sequence of <xref:System.ServiceModel.Activities.Receive> activities.</span></span> <span data-ttu-id="3b045-114">Bu iş akışını iş akışı bir kredi onaylanması için üç bildirimleri burada bekliyor basit kredi onay işlemi modeller.</span><span class="sxs-lookup"><span data-stu-id="3b045-114">This workflow models a simple loan approval process where the workflow expects three notifications for a loan to be approved.</span></span> <span data-ttu-id="3b045-115">A [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci uygulaması ne hizmet bekliyor ters sırada üç bağlantılı bildirim gönderir.</span><span class="sxs-lookup"><span data-stu-id="3b045-115">A [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client application sends three correlated notifications in the reverse order of what the service expects.</span></span> <span data-ttu-id="3b045-116">Arabellekli alma özelliği hizmeti açık olduğu için her düzen dışı ileti hizmeti arabelleğe ve iş akışı, almaya hazır olduğunda işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3b045-116">Because the buffered receive feature is turned on at the service, each out-of-order message is buffered at the service and processed as the workflow becomes ready to receive it.</span></span>  
  
 <span data-ttu-id="3b045-117">Arabellekli alma özellik gerektirir <xref:System.ServiceModel.Activities.ReceiveContent> bağlama, bu nedenle hizmet Destek'ten kullanan <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="3b045-117">The buffered receive feature requires <xref:System.ServiceModel.Activities.ReceiveContent> support from the binding, therefore the service uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="3b045-118">Varsayılanların kullanıldığı şekilde özel yapılandırma bağlama için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3b045-118">No special configuration is required for the binding, so the defaults are used.</span></span>  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 <span data-ttu-id="3b045-119">Hizmet ayrıca hizmeti kullandığınız için meta verileri gösterir <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="3b045-119">The service also exposes metadata for the service using <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span></span>  
  
 <span data-ttu-id="3b045-120">Benzer şekilde, istemci uç noktası kullanılarak yapılandırılmış <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="3b045-120">Similarly, the client endpoint is configured using <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="3b045-121">İstemci kodu ve yapılandırma oluşturulur kullanarak **hizmet Başvurusu Ekle** Visual Studio özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="3b045-121">The client code and configuration is generated by using the **Add Service Reference** feature of Visual Studio.</span></span> <span data-ttu-id="3b045-122">Aşağıdaki örnek, App.config dosyasında oluşturulan istemci uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="3b045-122">The following example is the generated client endpoint in the App.config file.</span></span>  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 <span data-ttu-id="3b045-123">Bu örnek, aşağıdaki Windows bileşenleri etkin olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3b045-123">This sample requires that the following Windows components are enabled:</span></span>  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]<span data-ttu-id="3b045-124"> Yönetim uyumluluğu, metatabanı ve yapılandırma uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="3b045-124"> Management Compatibility, Metabase, and Configuration Compatibility</span></span>  
  
3.  <span data-ttu-id="3b045-125">World Wide Web Hizmetleri, uygulama geliştirme özellikleri ve ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3b045-125">World Wide Web Services, Application Development Features, and ASP.NET</span></span>  
  
4.  <span data-ttu-id="3b045-126">Microsoft Message sıraları (MSMQ) sunucusu</span><span class="sxs-lookup"><span data-stu-id="3b045-126">Microsoft Message Queues (MSMQ) Server</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="3b045-127">Ayarlamak ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3b045-127">To set up, and build the sample</span></span>  
  
1.  <span data-ttu-id="3b045-128">Konumunda bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi, ASP.NET yazarak kaydolun `aspnet_regiis –I` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3b045-128">At a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by typing `aspnet_regiis –I` and press ENTER.</span></span>  
  
2.  <span data-ttu-id="3b045-129">Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yönetici olarak.</span><span class="sxs-lookup"><span data-stu-id="3b045-129">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an Administrator.</span></span>  
  
3.  <span data-ttu-id="3b045-130">LoanService.sln açın.</span><span class="sxs-lookup"><span data-stu-id="3b045-130">Open LoanService.sln.</span></span>  
  
4.  <span data-ttu-id="3b045-131">LoanService proje için sanal dizini oluşturmak isterseniz, seçin sorulduğunda **Evet**.</span><span class="sxs-lookup"><span data-stu-id="3b045-131">When asked if you would like to create the virtual directories for the LoanService project, select **Yes**.</span></span>  
  
#### <a name="to-set-up-the-service-queues"></a><span data-ttu-id="3b045-132">Hizmet sıralarını ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="3b045-132">To set up the service queues</span></span>  
  
1.  <span data-ttu-id="3b045-133">Kuyruklar oluşturur ve Service1.xamlx içinde tanımlanan hizmet etkinleştirir LoanClient uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3b045-133">Press F5 to run the LoanClient application that creates the queues and activates the service defined in Service1.xamlx.</span></span>  
  
2.  <span data-ttu-id="3b045-134">Açık **Bilgisayar Yönetimi** Compmgmt.msc bir komut isteminden çalıştırarak konsol.</span><span class="sxs-lookup"><span data-stu-id="3b045-134">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
3.  <span data-ttu-id="3b045-135">İçinde **Bilgisayar Yönetimi** genişletin **hizmet**, **uygulamaları**, **Message Queuing**, **özel sıralar** .</span><span class="sxs-lookup"><span data-stu-id="3b045-135">In the **Computer Management** console, expand **Service**, **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
4.  <span data-ttu-id="3b045-136">Loanservice/service1.xamlx sıranın sağ tıklatıp **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="3b045-136">Right-click the loanservice/service1.xamlx queue and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="3b045-137">Seçin **güvenlik** sekmesini tıklatın ve eklemek **herkes alır ileti**, **iletiye** ve **iletisi gönder** izinleri.</span><span class="sxs-lookup"><span data-stu-id="3b045-137">Select the **Security** tab, and add **Everyone Receives Message**, **Peek Message** and **Send Message** permissions.</span></span>  
  
6.  <span data-ttu-id="3b045-138">Açık [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="3b045-138">Open the [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Manager.</span></span>  
  
7.  <span data-ttu-id="3b045-139">Gözat **Server**, **siteleri**, **varsayılan Web sitesi**, **özel**, **LoanService** ve seçin **Gelişmiş Seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="3b045-139">Browse to **Server**, **Sites**, **Default Web site**, **Private**, **LoanService** and select **Advanced Options**</span></span>  
  
8.  <span data-ttu-id="3b045-140">Değişiklik **etkin protokoller** olmasını **http**, **net.msmq**.</span><span class="sxs-lookup"><span data-stu-id="3b045-140">Change the **Enabled Protocols** to be **http**, **net.msmq**.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="3b045-141">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3b045-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="3b045-142">Gözat http://localhost/private/loanservice/service1.xamlx hizmetinin çalıştığından emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="3b045-142">Browse to http://localhost/private/loanservice/service1.xamlx to ensure that the service is running.</span></span>  
  
2.  <span data-ttu-id="3b045-143">LoanClient uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3b045-143">Press F5 to run the LoanClient application.</span></span> <span data-ttu-id="3b045-144">İş akışı tamamlandığında, bir out.txt dosyası ileti değişimi sonucunu içeren C:\Inbox kaydedilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b045-144">Once the workflow is complete, an out.txt file should be saved to C:\Inbox that contains the result of the message exchange.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="3b045-145">Temizlemek için</span><span class="sxs-lookup"><span data-stu-id="3b045-145">To clean up</span></span>  
  
1.  <span data-ttu-id="3b045-146">Açık **Bilgisayar Yönetimi** Compmgmt.msc bir komut isteminden çalıştırarak konsol.</span><span class="sxs-lookup"><span data-stu-id="3b045-146">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
2.  <span data-ttu-id="3b045-147">Genişletme **hizmet** ve **uygulamaları**, **Message Queuing**, **özel sıralar**.</span><span class="sxs-lookup"><span data-stu-id="3b045-147">Expand **Service** and **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
3.  <span data-ttu-id="3b045-148">Loanservice/service1.xamlx kuyruğu silin.</span><span class="sxs-lookup"><span data-stu-id="3b045-148">Delete the loanservice/service1.xamlx queue.</span></span>  
  
4.  <span data-ttu-id="3b045-149">C:\Inbox dizini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3b045-149">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3b045-150">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b045-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3b045-151">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3b045-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3b045-152">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="3b045-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3b045-153">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3b045-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
