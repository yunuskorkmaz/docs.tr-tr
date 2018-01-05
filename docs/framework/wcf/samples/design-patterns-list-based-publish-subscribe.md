---
title: "Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b54982439f621ea504c91c264dde002751ec9185
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="bfaee-102">Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma</span><span class="sxs-lookup"><span data-stu-id="bfaee-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="bfaee-103">Bu örnek olarak uygulanan liste tabanlı yayımlama-abone olma deseni gösterilmektedir bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] program.</span><span class="sxs-lookup"><span data-stu-id="bfaee-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfaee-104">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="bfaee-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bfaee-105">Liste tabanlı yayımlama-abone olma tasarım deseni Microsoft Patterns & yöntemler yayında açıklanan [tümleştirme desenleri](http://go.microsoft.com/fwlink/?LinkId=95894).</span><span class="sxs-lookup"><span data-stu-id="bfaee-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](http://go.microsoft.com/fwlink/?LinkId=95894).</span></span> <span data-ttu-id="bfaee-106">Yayımla-abone olma deseni bir bilgi konuya abone olduğunuz alıcıları koleksiyonu bilgilerini geçirir.</span><span class="sxs-lookup"><span data-stu-id="bfaee-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="bfaee-107">Liste tabanlı yayımlama-abone olma aboneleri listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="bfaee-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="bfaee-108">Bilgi paylaşmak için olduğunda bir kopyasını listedeki her abone gönderilir.</span><span class="sxs-lookup"><span data-stu-id="bfaee-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="bfaee-109">Bu örnek dinamik bir listeye bağlı gösterir, istemcilerin abone veya gerekli sıklıkta aboneliği düzeni yayımlama-abonelik.</span><span class="sxs-lookup"><span data-stu-id="bfaee-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="bfaee-110">Liste tabanlı yayımlama-abone olma örnek, bir istemci, hizmet ve bir veri kaynağı programı oluşur.</span><span class="sxs-lookup"><span data-stu-id="bfaee-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="bfaee-111">Birden fazla istemci ve çalışan birden fazla veri kaynağı program olabilir.</span><span class="sxs-lookup"><span data-stu-id="bfaee-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="bfaee-112">İstemcileri hizmete abone olmak için bildirim almak ve aboneliği.</span><span class="sxs-lookup"><span data-stu-id="bfaee-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="bfaee-113">Veri kaynağı programları ile tüm geçerli aboneleri paylaşılmak üzere hizmet bilgi gönderin.</span><span class="sxs-lookup"><span data-stu-id="bfaee-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="bfaee-114">Bu örnek, istemci ve veri kaynağındaki konsol program (.exe dosyaları) ve hizmet Internet Information Services (IIS) barındırılan bir kitaplık (.dll).</span><span class="sxs-lookup"><span data-stu-id="bfaee-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="bfaee-115">İstemci ve veri kaynağı etkinlik masaüstünde görünür.</span><span class="sxs-lookup"><span data-stu-id="bfaee-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="bfaee-116">Hizmet, çift yönlü iletişimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="bfaee-116">The service uses duplex communication.</span></span> <span data-ttu-id="bfaee-117">`ISampleContract` Hizmet sözleşmesini eşleştirilmiş ile bir `ISampleClientCallback` geri çağırma sözleşme.</span><span class="sxs-lookup"><span data-stu-id="bfaee-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="bfaee-118">Hizmet katılma veya aboneleri listesi ayrılma hangi istemcilerin kullanmak abone ve aboneliği kaldırma hizmet işlemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="bfaee-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="bfaee-119">Ayrıca hizmeti uygulayan `PublishPriceChange` yeni bilgilerle hizmet sağlamak için veri kaynağı programı çağırır hizmet işlemi.</span><span class="sxs-lookup"><span data-stu-id="bfaee-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="bfaee-120">İstemci programı uygulayan `PriceChange` fiyat değişikliği tüm aboneleri bildirmek için hizmet çağrıları hizmet işlemi.</span><span class="sxs-lookup"><span data-stu-id="bfaee-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
```  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,   
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 <span data-ttu-id="bfaee-121">Hizmet .NET Framework olay ilgili yeni bilgiler tüm aboneleri bildirmek için mekanizma olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="bfaee-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="bfaee-122">Bir istemci hizmeti çağıran abone tarafından katıldığında, olay işleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bfaee-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="bfaee-123">Bir istemci ayrıldığında, olay işleyici olaydan aboneliğini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bfaee-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="bfaee-124">Bir veri kaynağı bir fiyat değişikliği bildirmek için hizmet çağırdığında hizmet olayını başlatır.</span><span class="sxs-lookup"><span data-stu-id="bfaee-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="bfaee-125">Bu hizmet bir abone ve bunların olay işleyicileri yürütülecek neden olan her istemci için her bir örneği çağırır.</span><span class="sxs-lookup"><span data-stu-id="bfaee-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="bfaee-126">Her olay işleyicisi bilgileri kendi geri çağırma işlevini istemciye geçirir.</span><span class="sxs-lookup"><span data-stu-id="bfaee-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
```  
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is deregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 <span data-ttu-id="bfaee-127">Örneği çalıştırdığınızda, çeşitli istemciler başlatın.</span><span class="sxs-lookup"><span data-stu-id="bfaee-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="bfaee-128">İstemcilerin hizmetine abone olun.</span><span class="sxs-lookup"><span data-stu-id="bfaee-128">The clients subscribe to the service.</span></span> <span data-ttu-id="bfaee-129">Ardından bilgi hizmetine gönderir veri kaynağı programını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bfaee-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="bfaee-130">Hizmeti hakkında bilgi için tüm aboneleri geçirir.</span><span class="sxs-lookup"><span data-stu-id="bfaee-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="bfaee-131">Her istemci konsol bilgileri alındı onaylayan üzerinde etkinlik görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bfaee-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="bfaee-132">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bfaee-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="bfaee-133">Ayarlamak ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bfaee-133">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="bfaee-134">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bfaee-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bfaee-135">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bfaee-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="bfaee-136">Aynı makinede örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bfaee-136">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="bfaee-137">Test hizmeti aşağıdaki adresini girerek bir tarayıcı kullanarak erişebilirsiniz: http://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="bfaee-137">Test that you can access the service using a browser by entering the following address: http://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="bfaee-138">Bir onay sayfasına yanıtta görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bfaee-138">A confirmation page should be displayed in response.</span></span>  
  
2.  <span data-ttu-id="bfaee-139">\Client\bin Client.exe çalıştırmak\\, dile özgü klasörü altında.</span><span class="sxs-lookup"><span data-stu-id="bfaee-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="bfaee-140">İstemci etkinliği istemci konsol penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bfaee-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="bfaee-141">Çeşitli istemciler başlatın.</span><span class="sxs-lookup"><span data-stu-id="bfaee-141">Launch several clients.</span></span>  
  
3.  <span data-ttu-id="bfaee-142">\Datasource\bin DataSource.exe çalıştırmak\\, dile özgü klasörü altında.</span><span class="sxs-lookup"><span data-stu-id="bfaee-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="bfaee-143">Veri kaynağı etkinliği konsol penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bfaee-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="bfaee-144">Veri kaynağı bilgileri hizmetine gönderir. sonra her bir istemciye geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bfaee-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4.  <span data-ttu-id="bfaee-145">İstemci, veri kaynağı ve hizmet programlarını iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="bfaee-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="bfaee-146">Makine genelinde örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bfaee-146">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="bfaee-147">Hizmet Makine'yi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="bfaee-147">Set up the service machine:</span></span>  
  
    1.  <span data-ttu-id="bfaee-148">Hizmeti makinede ServiceModelSamples adlı bir sanal dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bfaee-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="bfaee-149">Toplu iş dosyası gelen Setupvroot.bat [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) disk dizini ve sanal dizini oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bfaee-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2.  <span data-ttu-id="bfaee-150">Hizmet program dosyalarını %SystemDrive%\Inetpub\wwwroot\servicemodelsamples hizmeti makinede ServiceModelSamples sanal dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bfaee-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="bfaee-151">Dosyaları \bin dizinine eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="bfaee-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3.  <span data-ttu-id="bfaee-152">Test, hizmet bir tarayıcı kullanarak istemci makineden erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bfaee-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2.  <span data-ttu-id="bfaee-153">İstemci makineleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="bfaee-153">Set up the client machines:</span></span>  
  
    1.  <span data-ttu-id="bfaee-154">İstemci makinelerine dile özgü klasörü altındaki \client\bin\ klasöründen istemci program dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bfaee-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2.  <span data-ttu-id="bfaee-155">Her istemci yapılandırma dosyasında hizmetinizin yeni adresi ile eşleşmesi için uç nokta tanımındaki adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bfaee-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="bfaee-156">Tüm başvuruları "localhost" adresi bir tam etki alanı adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bfaee-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3.  <span data-ttu-id="bfaee-157">Veri kaynağı Makine'yi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="bfaee-157">Set up the data source machine:</span></span>  
  
    1.  <span data-ttu-id="bfaee-158">Veri kaynağı program dosyaları \datasource\bin\ klasöründen dile özgü klasörü altında veri kaynak makineye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bfaee-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2.  <span data-ttu-id="bfaee-159">Veri kaynağı yapılandırma dosyasında hizmetinizin yeni adresi ile eşleşmesi için uç nokta tanımındaki adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bfaee-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="bfaee-160">Tüm başvuruları "localhost" adresi bir tam etki alanı adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bfaee-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4.  <span data-ttu-id="bfaee-161">İstemci bilgisayarlarında Client.exe bir komut isteminden başlatın.</span><span class="sxs-lookup"><span data-stu-id="bfaee-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="bfaee-162">Verileri kaynak makinede bir komut isteminden Datasource.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="bfaee-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bfaee-163">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="bfaee-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bfaee-164">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bfaee-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bfaee-165">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="bfaee-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bfaee-166">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="bfaee-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
  
## <a name="see-also"></a><span data-ttu-id="bfaee-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bfaee-167">See Also</span></span>
