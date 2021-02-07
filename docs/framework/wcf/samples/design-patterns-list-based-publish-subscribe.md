---
description: 'Daha fazla bilgi edinin: tasarım desenleri: List-Based Publish-Subscribe'
title: 'Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: b615da2afa4e6452b62eacae2cc6b61e4c4363dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726747"
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="d98c9-103">Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma</span><span class="sxs-lookup"><span data-stu-id="d98c9-103">Design Patterns: List-Based Publish-Subscribe</span></span>

<span data-ttu-id="d98c9-104">Bu örnek, Windows Communication Foundation (WCF) programı olarak uygulanan liste tabanlı Publish-Subscribe modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-104">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d98c9-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="d98c9-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d98c9-106">Liste tabanlı Publish-Subscribe tasarım deseni, Microsoft desenleri & uygulamalar yayımı, [tümleştirme desenleri](/previous-versions/msp-n-p/ff647309(v=pandp.10))' nde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d98c9-106">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span></span> <span data-ttu-id="d98c9-107">Publish-Subscribe model bilgileri bir bilgi konusuna abone olan bir alıcı koleksiyonuna geçirir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-107">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="d98c9-108">Liste tabanlı yayımlama-abone ol, abonelerin bir listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="d98c9-108">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="d98c9-109">Paylaşılacak bilgiler olduğunda, listedeki her aboneye bir kopya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-109">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="d98c9-110">Bu örnek, istemcilerin abone olabileceği veya aboneliği kaldırmak için gerekli olan dinamik bir liste tabanlı yayımlama-abonelik modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-110">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="d98c9-111">Liste tabanlı Publish-Subscribe örneği bir istemciden, hizmetten ve bir veri kaynağı programından oluşur.</span><span class="sxs-lookup"><span data-stu-id="d98c9-111">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="d98c9-112">Birden fazla istemci ve çalıştıran birden fazla veri kaynağı programı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-112">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="d98c9-113">İstemciler hizmete abone olur, bildirimler alabilir ve aboneliği kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d98c9-113">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="d98c9-114">Veri kaynağı programları, hizmete tüm geçerli aboneler ile paylaşılmak üzere bilgi gönderir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-114">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="d98c9-115">Bu örnekte, istemci ve veri kaynağı konsol programlarıdır (. exe dosyaları) ve hizmet Internet Information Services (IIS) içinde barındırılan bir kitaplıktır (. dll).</span><span class="sxs-lookup"><span data-stu-id="d98c9-115">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="d98c9-116">İstemci ve veri kaynağı etkinliği masaüstünde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-116">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="d98c9-117">Hizmet çift yönlü iletişimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d98c9-117">The service uses duplex communication.</span></span> <span data-ttu-id="d98c9-118">`ISampleContract`Hizmet sözleşmesi bir `ISampleClientCallback` geri çağırma sözleşmesiyle eşleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="d98c9-118">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="d98c9-119">Hizmet, abone ve abonelik kaldırma hizmeti işlemlerini, istemcilerin abone listesini birleştirmek veya abone olmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d98c9-119">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="d98c9-120">Hizmet Ayrıca, `PublishPriceChange` veri kaynağı programının hizmeti yeni bilgi sağlamak üzere çağırdığı hizmet işlemini de uygular.</span><span class="sxs-lookup"><span data-stu-id="d98c9-120">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="d98c9-121">İstemci programı `PriceChange` , hizmetin bir fiyat değişikliğinin tüm abonelerini bilgilendirmek için çağırdığı hizmet işlemini uygular.</span><span class="sxs-lookup"><span data-stu-id="d98c9-121">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="d98c9-122">Hizmet, tüm abonelere yeni bilgiler hakkında bilgilendirmek için mekanizma olarak bir .NET Framework olayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="d98c9-122">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="d98c9-123">Bir istemci, abone 'yı çağırarak hizmete katıldığında bir olay işleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d98c9-123">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="d98c9-124">İstemci ayrıldığında olay işleyicisinin aboneliğini olaydan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d98c9-124">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="d98c9-125">Bir veri kaynağı bir fiyat değişikliğini raporlamak için hizmete çağrı yaptığı zaman, hizmet olayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="d98c9-125">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="d98c9-126">Bu, bir hizmetin her bir örneğini, abone olan her istemci için bir tane çağırır ve olay işleyicilerinin yürütülmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d98c9-126">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="d98c9-127">Her olay işleyicisi, geri çağırma işlevi aracılığıyla bilgileri istemcisine geçirir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-127">Each event handler passes the information to its client through its callback function.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="d98c9-128">Örneği çalıştırdığınızda birkaç istemciyi başlatın.</span><span class="sxs-lookup"><span data-stu-id="d98c9-128">When you run the sample, launch several clients.</span></span> <span data-ttu-id="d98c9-129">İstemciler hizmete abone olur.</span><span class="sxs-lookup"><span data-stu-id="d98c9-129">The clients subscribe to the service.</span></span> <span data-ttu-id="d98c9-130">Ardından, hizmete bilgi gönderen veri kaynağı programını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d98c9-130">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="d98c9-131">Hizmet, bilgileri tüm abonelere geçirir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-131">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="d98c9-132">Her istemci konsolunda, bilgilerin alındığını doğrulayan etkinlik görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d98c9-132">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="d98c9-133">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d98c9-133">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="d98c9-134">Örneği ayarlamak ve derlemek için</span><span class="sxs-lookup"><span data-stu-id="d98c9-134">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="d98c9-135">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d98c9-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d98c9-136">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d98c9-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="d98c9-137">Örneği aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d98c9-137">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="d98c9-138">Aşağıdaki adresi girerek bir tarayıcı kullanarak hizmete erişebilirsiniz: `http://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="d98c9-138">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="d98c9-139">Yanıt olarak bir onay sayfası görüntülenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-139">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="d98c9-140">\ Client\bin \\ ' den dile özgü klasörden Client.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d98c9-140">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="d98c9-141">İstemci etkinliği istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-141">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="d98c9-142">Birkaç istemciyi başlatın.</span><span class="sxs-lookup"><span data-stu-id="d98c9-142">Launch several clients.</span></span>  
  
3. <span data-ttu-id="d98c9-143">\ Datasource\bin \\ ' den dile özgü klasörden Datasource.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d98c9-143">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="d98c9-144">Veri kaynağı etkinliği konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-144">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="d98c9-145">Veri kaynağı hizmete bilgi gönderdiğinde, her istemciye geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-145">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="d98c9-146">İstemci, veri kaynağı ve hizmet programları iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d98c9-146">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="d98c9-147">Örneği makineler arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d98c9-147">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="d98c9-148">Hizmet makinesini ayarlama:</span><span class="sxs-lookup"><span data-stu-id="d98c9-148">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="d98c9-149">Hizmet makinesinde, ServiceModelSamples adlı bir sanal dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d98c9-149">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="d98c9-150">[Windows Communication Foundation Örnekleri Için bir kerelik kurulum yordamından](one-time-setup-procedure-for-the-wcf-samples.md) toplu iş dosyası Setupvroot.bat disk dizini ve sanal dizin oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-150">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="d98c9-151">Hizmet programı dosyalarını%SystemDrive%\Inetpub\wwwroot\servicemodelsamples adresinden hizmet makinesindeki ServiceModelSamples sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d98c9-151">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="d98c9-152">Dosyaları \Bin dizinine dahil ettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d98c9-152">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="d98c9-153">Bir tarayıcı kullanarak hizmete istemci makineden erişebilme sınamasını yapın.</span><span class="sxs-lookup"><span data-stu-id="d98c9-153">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="d98c9-154">İstemci makinelerini ayarlama:</span><span class="sxs-lookup"><span data-stu-id="d98c9-154">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="d98c9-155">İstemci program dosyalarını dile özgü klasör altındaki \client\bin\ klasöründen istemci makinelere kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d98c9-155">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="d98c9-156">Her istemci yapılandırma dosyasında, uç nokta tanımının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d98c9-156">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="d98c9-157">"Localhost" başvurularını, adreste tam etki alanı adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d98c9-157">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="d98c9-158">Veri kaynağı makinesini ayarlama:</span><span class="sxs-lookup"><span data-stu-id="d98c9-158">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="d98c9-159">Veri kaynağı program dosyalarını dile özgü klasör altındaki \datasource\bin\ klasöründen veri kaynağı makinesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d98c9-159">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="d98c9-160">Veri kaynağı yapılandırma dosyasında, uç nokta tanımının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d98c9-160">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="d98c9-161">"Localhost" başvurularını, adreste tam etki alanı adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d98c9-161">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="d98c9-162">İstemci makinelerde, bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="d98c9-162">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="d98c9-163">Veri kaynağı makinesinde, bir komut isteminden Datasource.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="d98c9-163">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d98c9-164">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d98c9-164">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d98c9-165">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d98c9-165">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d98c9-166">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d98c9-166">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d98c9-167">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d98c9-167">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`
