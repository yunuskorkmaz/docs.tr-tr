---
title: 'Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 1b99908c1b83bb0d75e295b7a12e8c5933fe86a1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650120"
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="24560-102">Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma</span><span class="sxs-lookup"><span data-stu-id="24560-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="24560-103">Bu örnek, bir Windows Communication Foundation (WCF) programı olarak uygulanan liste tabanlı yayımlama-abone olma deseni gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="24560-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24560-104">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="24560-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="24560-105">Microsoft Patterns ve uygulamalar yayında liste tabanlı yayımlama-abone olma tasarım deseni açıklanan [tümleştirme desenleri](https://go.microsoft.com/fwlink/?LinkId=95894).</span><span class="sxs-lookup"><span data-stu-id="24560-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](https://go.microsoft.com/fwlink/?LinkId=95894).</span></span> <span data-ttu-id="24560-106">Yayımlama-abone olma deseni bir koleksiyon bir bilgi konuya abone olduğunuz alıcıların bilgi geçirir.</span><span class="sxs-lookup"><span data-stu-id="24560-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="24560-107">Liste tabanlı yayımlama-abone ol aboneleri listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="24560-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="24560-108">Bilgi paylaşmak için olduğunda, bir kopyasını listedeki her aboneye gönderilir.</span><span class="sxs-lookup"><span data-stu-id="24560-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="24560-109">Bu örnek, dinamik bir liste tabanlı gösterir. burada istemciler abone olmak veya abonelikten gerektiği sıklıkta desen, yayımlama-abonelik.</span><span class="sxs-lookup"><span data-stu-id="24560-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="24560-110">Liste tabanlı yayımlama-abone olma örnek, bir istemci, hizmet ve veri kaynağı program oluşur.</span><span class="sxs-lookup"><span data-stu-id="24560-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="24560-111">Birden fazla istemci ve çalışan birden fazla veri kaynağı program olabilir.</span><span class="sxs-lookup"><span data-stu-id="24560-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="24560-112">İstemciler hizmete abone, bildirimleri alabilir ve aboneliği.</span><span class="sxs-lookup"><span data-stu-id="24560-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="24560-113">Veri kaynağı programları tüm geçerli abonelerle paylaşılan hizmet bilgi gönderin.</span><span class="sxs-lookup"><span data-stu-id="24560-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="24560-114">Bu örnek, istemci ve veri kaynağını programlar (.exe dosyaları) ve hizmet Internet Information Services (IIS) barındırılan bir kitaplık (.dll).</span><span class="sxs-lookup"><span data-stu-id="24560-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="24560-115">İstemci ve veri kaynağı etkinliği masaüstünde görünür.</span><span class="sxs-lookup"><span data-stu-id="24560-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="24560-116">Hizmet, çift yönlü iletişimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="24560-116">The service uses duplex communication.</span></span> <span data-ttu-id="24560-117">`ISampleContract` Hizmet sözleşmesini eşleştirilmiştir ile bir `ISampleClientCallback` geri çağırma anlaşması.</span><span class="sxs-lookup"><span data-stu-id="24560-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="24560-118">Hizmet, katılma veya aboneleri listesinin bırakın hangi istemcilerin kullanın, abone ve aboneliği kaldırma hizmet işlemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="24560-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="24560-119">Ayrıca hizmeti uygulayan `PublishPriceChange` hizmet yeni bilgiler sağlamak için veri kaynağı program çağıran hizmet işlemi.</span><span class="sxs-lookup"><span data-stu-id="24560-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="24560-120">İstemci programı uygulayan `PriceChange` tüm aboneler bir fiyat değişikliği bildirmek için hizmeti çağıran hizmet işlemi.</span><span class="sxs-lookup"><span data-stu-id="24560-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
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
  
 <span data-ttu-id="24560-121">Hizmet .NET Framework olayı ile ilgili yeni bilgiler tüm aboneler bildirmek için mekanizması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="24560-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="24560-122">Bir istemci hizmeti çağıran abone tarafından katıldığında, bir olay işleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="24560-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="24560-123">İstemci çıktığında, olay işleyicisi olay aboneliğini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="24560-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="24560-124">Bir veri kaynağı bir fiyat değişikliği bildirmek için hizmet çağırdığında, hizmet olayını başlatır.</span><span class="sxs-lookup"><span data-stu-id="24560-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="24560-125">Bu, hizmetin bir abone ve yürütülecek olay işleyicilerini neden her istemci için her örneği çağırır.</span><span class="sxs-lookup"><span data-stu-id="24560-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="24560-126">Her bir olay işleyicisi, geri çağırma işlevi aracılığıyla kendi istemci bilgileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="24560-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
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
        //The previous price change event handler is unregistered.  
  
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
  
 <span data-ttu-id="24560-127">Örneği çalıştırdığında, çeşitli istemciler başlatın.</span><span class="sxs-lookup"><span data-stu-id="24560-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="24560-128">İstemciler hizmete abone olun.</span><span class="sxs-lookup"><span data-stu-id="24560-128">The clients subscribe to the service.</span></span> <span data-ttu-id="24560-129">Ardından bilgi hizmetine gönderir. veri kaynağı programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="24560-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="24560-130">Hizmet bilgileri tüm abonelerine geçirir.</span><span class="sxs-lookup"><span data-stu-id="24560-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="24560-131">Her istemci konsol bilgi alındı onaylayan üzerinde etkinliği görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24560-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="24560-132">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="24560-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="24560-133">Ayarlama ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="24560-133">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="24560-134">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="24560-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="24560-135">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="24560-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="24560-136">Örneği aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="24560-136">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="24560-137">Test hizmeti aşağıdaki adresi girerek bir tarayıcı kullanarak erişebilirsiniz: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="24560-137">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="24560-138">Yanıtta bir onay sayfası gösterilmelidir.</span><span class="sxs-lookup"><span data-stu-id="24560-138">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="24560-139">\Client\bin Client.exe çalıştırma\\, dile özgü klasörü altında.</span><span class="sxs-lookup"><span data-stu-id="24560-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="24560-140">İstemci etkinliği istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="24560-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="24560-141">Çeşitli istemciler başlatın.</span><span class="sxs-lookup"><span data-stu-id="24560-141">Launch several clients.</span></span>  
  
3. <span data-ttu-id="24560-142">\Datasource\bin DataSource.exe çalıştırma\\, dile özgü klasörü altında.</span><span class="sxs-lookup"><span data-stu-id="24560-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="24560-143">Veri kaynak etkinliği konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="24560-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="24560-144">Veri kaynağı bilgilerini hizmetine gönderir. sonra her bir istemciye geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="24560-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="24560-145">İstemci, veri kaynağı ve hizmet programlarını iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="24560-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="24560-146">Makineler arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="24560-146">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="24560-147">Hizmet Makine'yi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="24560-147">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="24560-148">Hizmeti makinede ServiceModelSamples adlı sanal bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24560-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="24560-149">Toplu iş dosyası Setupvroot.bat gelen [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) disk dizini ve sanal dizin oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24560-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="24560-150">Hizmet program dosyaları %SystemDrive%\Inetpub\wwwroot\servicemodelsamples hizmeti makinede ServiceModelSamples sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="24560-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="24560-151">\Bin dizinine dosyaları eklemeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="24560-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="24560-152">Test bir tarayıcı kullanarak istemci makine hizmete erişebilir.</span><span class="sxs-lookup"><span data-stu-id="24560-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="24560-153">İstemci makineleri ayarlama:</span><span class="sxs-lookup"><span data-stu-id="24560-153">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="24560-154">İstemci makineler için dile özgü klasörü altında \client\bin\ klasöründen istemci program dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="24560-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="24560-155">Her istemci yapılandırma dosyasında adresi uç nokta tanımı hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="24560-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="24560-156">"Localhost" yönelik tüm başvuruları adresindeki bir tam etki alanı adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="24560-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="24560-157">Veri kaynağı Makine'yi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="24560-157">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="24560-158">Veri kaynak makineye \datasource\bin\ klasöründen dile özgü klasörü altında veri kaynağı program dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="24560-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="24560-159">Veri kaynağı yapılandırma dosyasında adresi uç nokta tanımı hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="24560-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="24560-160">"Localhost" yönelik tüm başvuruları adresindeki bir tam etki alanı adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="24560-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="24560-161">İstemci makinelerinde Client.exe bir komut istemi'nden başlatın.</span><span class="sxs-lookup"><span data-stu-id="24560-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="24560-162">Veri kaynak makinede Datasource.exe bir komut istemi'nden başlatın.</span><span class="sxs-lookup"><span data-stu-id="24560-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="24560-163">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="24560-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="24560-164">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="24560-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="24560-165">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="24560-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="24560-166">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="24560-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
