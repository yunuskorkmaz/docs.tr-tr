---
title: 'Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 5aaea5b0def544f8b3e963d71e269592b9b40784
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592352"
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="0982d-102">Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma</span><span class="sxs-lookup"><span data-stu-id="0982d-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="0982d-103">Bu örnek, Windows Communication Foundation (WCF) programı olarak uygulanan liste tabanlı yayımla-abone ol modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0982d-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0982d-104">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="0982d-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0982d-105">Liste tabanlı yayımlama-abone ol tasarım deseni, Microsoft düzenleri & uygulamalar yayımı, [tümleştirme desenleri](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10))' nde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0982d-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span></span> <span data-ttu-id="0982d-106">Yayımla-abone ol, bilgileri bir bilgi konusuna abone olan bir alıcı koleksiyonuna geçirir.</span><span class="sxs-lookup"><span data-stu-id="0982d-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="0982d-107">Liste tabanlı yayımlama-abone ol, abonelerin bir listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="0982d-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="0982d-108">Paylaşılacak bilgiler olduğunda, listedeki her aboneye bir kopya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="0982d-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="0982d-109">Bu örnek, istemcilerin abone olabileceği veya aboneliği kaldırmak için gerekli olan dinamik bir liste tabanlı yayımlama-abonelik modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0982d-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="0982d-110">Liste tabanlı yayımlama-abone olma örneği bir istemciden, hizmetten ve bir veri kaynağı programından oluşur.</span><span class="sxs-lookup"><span data-stu-id="0982d-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="0982d-111">Birden fazla istemci ve çalıştıran birden fazla veri kaynağı programı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0982d-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="0982d-112">İstemciler hizmete abone olur, bildirimler alabilir ve aboneliği kaldırın.</span><span class="sxs-lookup"><span data-stu-id="0982d-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="0982d-113">Veri kaynağı programları, hizmete tüm geçerli aboneler ile paylaşılmak üzere bilgi gönderir.</span><span class="sxs-lookup"><span data-stu-id="0982d-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="0982d-114">Bu örnekte, istemci ve veri kaynağı konsol programlarıdır (. exe dosyaları) ve hizmet Internet Information Services (IIS) içinde barındırılan bir kitaplıktır (. dll).</span><span class="sxs-lookup"><span data-stu-id="0982d-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="0982d-115">İstemci ve veri kaynağı etkinliği masaüstünde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="0982d-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="0982d-116">Hizmet çift yönlü iletişimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="0982d-116">The service uses duplex communication.</span></span> <span data-ttu-id="0982d-117">`ISampleContract`Hizmet sözleşmesi bir `ISampleClientCallback` geri çağırma sözleşmesiyle eşleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="0982d-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="0982d-118">Hizmet, abone ve abonelik kaldırma hizmeti işlemlerini, istemcilerin abone listesini birleştirmek veya abone olmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0982d-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="0982d-119">Hizmet Ayrıca, `PublishPriceChange` veri kaynağı programının hizmeti yeni bilgi sağlamak üzere çağırdığı hizmet işlemini de uygular.</span><span class="sxs-lookup"><span data-stu-id="0982d-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="0982d-120">İstemci programı `PriceChange` , hizmetin bir fiyat değişikliğinin tüm abonelerini bilgilendirmek için çağırdığı hizmet işlemini uygular.</span><span class="sxs-lookup"><span data-stu-id="0982d-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
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
  
 <span data-ttu-id="0982d-121">Hizmet, tüm abonelere yeni bilgiler hakkında bilgilendirmek için mekanizma olarak bir .NET Framework olayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="0982d-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="0982d-122">Bir istemci, abone 'yı çağırarak hizmete katıldığında bir olay işleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0982d-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="0982d-123">İstemci ayrıldığında olay işleyicisinin aboneliğini olaydan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0982d-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="0982d-124">Bir veri kaynağı bir fiyat değişikliğini raporlamak için hizmete çağrı yaptığı zaman, hizmet olayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="0982d-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="0982d-125">Bu, bir hizmetin her bir örneğini, abone olan her istemci için bir tane çağırır ve olay işleyicilerinin yürütülmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="0982d-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="0982d-126">Her olay işleyicisi, geri çağırma işlevi aracılığıyla bilgileri istemcisine geçirir.</span><span class="sxs-lookup"><span data-stu-id="0982d-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
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
  
 <span data-ttu-id="0982d-127">Örneği çalıştırdığınızda birkaç istemciyi başlatın.</span><span class="sxs-lookup"><span data-stu-id="0982d-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="0982d-128">İstemciler hizmete abone olur.</span><span class="sxs-lookup"><span data-stu-id="0982d-128">The clients subscribe to the service.</span></span> <span data-ttu-id="0982d-129">Ardından, hizmete bilgi gönderen veri kaynağı programını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0982d-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="0982d-130">Hizmet, bilgileri tüm abonelere geçirir.</span><span class="sxs-lookup"><span data-stu-id="0982d-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="0982d-131">Her istemci konsolunda, bilgilerin alındığını doğrulayan etkinlik görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0982d-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="0982d-132">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0982d-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="0982d-133">Örneği ayarlamak ve derlemek için</span><span class="sxs-lookup"><span data-stu-id="0982d-133">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="0982d-134">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0982d-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0982d-135">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="0982d-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="0982d-136">Örneği aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0982d-136">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="0982d-137">Aşağıdaki adresi girerek bir tarayıcı kullanarak hizmete erişebilirsiniz: `http://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="0982d-137">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="0982d-138">Yanıt olarak bir onay sayfası görüntülenmelidir.</span><span class="sxs-lookup"><span data-stu-id="0982d-138">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="0982d-139">\ Client\bin \\ ' den dile özgü klasörden Client. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0982d-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="0982d-140">İstemci etkinliği istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0982d-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="0982d-141">Birkaç istemciyi başlatın.</span><span class="sxs-lookup"><span data-stu-id="0982d-141">Launch several clients.</span></span>  
  
3. <span data-ttu-id="0982d-142">\ Datasource\bin \\ ' den, dile özgü klasörün altında DataSource. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0982d-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="0982d-143">Veri kaynağı etkinliği konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0982d-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="0982d-144">Veri kaynağı hizmete bilgi gönderdiğinde, her istemciye geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0982d-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="0982d-145">İstemci, veri kaynağı ve hizmet programları iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="0982d-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="0982d-146">Örneği makineler arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0982d-146">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="0982d-147">Hizmet makinesini ayarlama:</span><span class="sxs-lookup"><span data-stu-id="0982d-147">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="0982d-148">Hizmet makinesinde, ServiceModelSamples adlı bir sanal dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0982d-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="0982d-149">[Windows Communication Foundation Örnekleri Için bir kerelik kurulum yordamından](one-time-setup-procedure-for-the-wcf-samples.md) Setupvroot. bat toplu iş dosyası, disk dizini ve sanal dizin oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0982d-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="0982d-150">Hizmet programı dosyalarını%SystemDrive%\Inetpub\wwwroot\servicemodelsamples adresinden hizmet makinesindeki ServiceModelSamples sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0982d-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="0982d-151">Dosyaları \Bin dizinine dahil ettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0982d-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="0982d-152">Bir tarayıcı kullanarak hizmete istemci makineden erişebilme sınamasını yapın.</span><span class="sxs-lookup"><span data-stu-id="0982d-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="0982d-153">İstemci makinelerini ayarlama:</span><span class="sxs-lookup"><span data-stu-id="0982d-153">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="0982d-154">İstemci program dosyalarını dile özgü klasör altındaki \client\bin\ klasöründen istemci makinelere kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0982d-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="0982d-155">Her istemci yapılandırma dosyasında, uç nokta tanımının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0982d-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="0982d-156">"Localhost" başvurularını, adreste tam etki alanı adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0982d-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="0982d-157">Veri kaynağı makinesini ayarlama:</span><span class="sxs-lookup"><span data-stu-id="0982d-157">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="0982d-158">Veri kaynağı program dosyalarını dile özgü klasör altındaki \datasource\bin\ klasöründen veri kaynağı makinesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0982d-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="0982d-159">Veri kaynağı yapılandırma dosyasında, uç nokta tanımının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0982d-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="0982d-160">"Localhost" başvurularını, adreste tam etki alanı adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0982d-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="0982d-161">İstemci makinelerde, bir komut isteminden Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="0982d-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="0982d-162">Veri kaynağı makinesinde, bir komut isteminden DataSource. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="0982d-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0982d-163">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0982d-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0982d-164">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0982d-164">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0982d-165">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0982d-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0982d-166">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0982d-166">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
