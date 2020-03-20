---
title: 'Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 7342b3702338d5cd1fcc27d80e4e70cee019cc22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144766"
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="bbf51-102">Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma</span><span class="sxs-lookup"><span data-stu-id="bbf51-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="bbf51-103">Bu örnek, Windows Communication Foundation (WCF) programı olarak uygulanan Liste tabanlı Yayımla-Abone oltasını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bbf51-104">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="bbf51-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bbf51-105">Liste tabanlı Yayımla-Abone Ol tasarım deseni, Microsoft Desenleri & Uygulamaları yayını, [Tümleştirme Desenleri'nde](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10))açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bbf51-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span></span> <span data-ttu-id="bbf51-106">Yayımla-Abone Ol deseni bilgileri bir bilgi konusuna abone olan alıcılar koleksiyonuna aktarıyor.</span><span class="sxs-lookup"><span data-stu-id="bbf51-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="bbf51-107">Liste tabanlı publish-subscribe, abonelerin listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="bbf51-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="bbf51-108">Paylaşılaca bilgi olduğunda, listedeki her aboneye bir kopya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="bbf51-109">Bu örnek, istemcilerin gerektiği sıklıkta abone olabileceği veya aboneliğini kaldırabileceği dinamik bir liste tabanlı yayımlama-abone olta sıcağı gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="bbf51-110">Liste tabanlı Yayımla-Abone Ol örneği bir istemci, bir hizmet ve bir veri kaynağı programından oluşur.</span><span class="sxs-lookup"><span data-stu-id="bbf51-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="bbf51-111">Birden fazla istemci ve birden fazla veri kaynağı programı çalışıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="bbf51-112">İstemciler hizmete abone, bildirim alır ve aboneliğini iptal eder.</span><span class="sxs-lookup"><span data-stu-id="bbf51-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="bbf51-113">Veri kaynağı programlar, mevcut tüm abonelerle paylaşılmak üzere hizmete bilgi gönderir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="bbf51-114">Bu örnekte, istemci ve veri kaynağı konsol programlarıdır (.exe dosyaları) ve hizmet Internet Information Services (IIS) barındırılan bir kitaplıktır (.dll).</span><span class="sxs-lookup"><span data-stu-id="bbf51-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="bbf51-115">İstemci ve veri kaynağı etkinliği masaüstünde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="bbf51-116">Hizmet çift yönlü iletişim kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbf51-116">The service uses duplex communication.</span></span> <span data-ttu-id="bbf51-117">Hizmet `ISampleContract` sözleşmesi bir `ISampleClientCallback` geri arama sözleşmesiyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="bbf51-118">Hizmet, istemcilerin abone listesine katılmak veya abone listesini bırakmak için kullandıkları Abone Ol ve Aboneliği Kaldır hizmet işlemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="bbf51-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="bbf51-119">Hizmet ayrıca, veri `PublishPriceChange` kaynağı programının hizmete yeni bilgiler sağlamak için çağırdığı hizmet işlemini de uygular.</span><span class="sxs-lookup"><span data-stu-id="bbf51-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="bbf51-120">İstemci programı, `PriceChange` hizmetin tüm abonelere fiyat değişikliğini bildirmesini gerektirdiği hizmet işlemini uygular.</span><span class="sxs-lookup"><span data-stu-id="bbf51-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
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
  
 <span data-ttu-id="bbf51-121">Hizmet, tüm aboneleri yeni bilgiler hakkında bilgilendirmek için bir .NET Framework olayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbf51-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="bbf51-122">Bir istemci Abone'yi arayarak hizmete katıldığında, bir olay işleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbf51-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="bbf51-123">İstemci ayrıldığında, olay işleyicisinin aboneliğini olaydan iptal eder.</span><span class="sxs-lookup"><span data-stu-id="bbf51-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="bbf51-124">Bir veri kaynağı hizmeti fiyat değişikliğini bildirmek için aradığında, hizmet olayı yükseltir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="bbf51-125">Bu, abone olan her istemci için bir hizmetin her örneğini çağırır ve olay işleyicilerinin yürütülmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="bbf51-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="bbf51-126">Her olay işleyicisi, geri arama işlevi aracılığıyla bilgileri istemcisine iletir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
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
  
 <span data-ttu-id="bbf51-127">Örneği çalıştırdığınızda, birkaç istemci başlatın.</span><span class="sxs-lookup"><span data-stu-id="bbf51-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="bbf51-128">Müşteriler hizmete abone dir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-128">The clients subscribe to the service.</span></span> <span data-ttu-id="bbf51-129">Ardından, hizmete bilgi gönderen veri kaynağı programını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bbf51-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="bbf51-130">Hizmet tüm abonelere bilgi aktarıyor.</span><span class="sxs-lookup"><span data-stu-id="bbf51-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="bbf51-131">Her istemci konsolunda bilgilerin alındığını onaylayan etkinliği görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbf51-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="bbf51-132">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bbf51-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="bbf51-133">Örneği ayarlamak ve oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bbf51-133">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="bbf51-134">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="bbf51-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="bbf51-135">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="bbf51-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="bbf51-136">Numuneyi aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bbf51-136">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="bbf51-137">Aşağıdaki adresi girerek bir tarayıcı kullanarak hizmete erişebileceğinizi test edin: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="bbf51-137">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="bbf51-138">Yanıt olarak bir onay sayfası görüntülenmelidir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-138">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="bbf51-139">İstemci.exe'yi dile\\özgü klasörün altından \client\bin'den çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bbf51-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="bbf51-140">İstemci etkinliği istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="bbf51-141">Birkaç müşteri başlatın.</span><span class="sxs-lookup"><span data-stu-id="bbf51-141">Launch several clients.</span></span>  
  
3. <span data-ttu-id="bbf51-142">Datasource.exe'yi dile özgü\\klasörün altından \datasource\bin'den çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bbf51-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="bbf51-143">Veri kaynağı etkinliği konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="bbf51-144">Veri kaynağı hizmete bilgi gönderdikten sonra, her istemciye aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bbf51-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="bbf51-145">İstemci, veri kaynağı ve hizmet programları iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="bbf51-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="bbf51-146">Numuneyi makineler arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bbf51-146">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="bbf51-147">Servis makinesini ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="bbf51-147">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="bbf51-148">Servis makinesinde ServiceModelSamples adlı sanal bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bbf51-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="bbf51-149">Windows Communication Foundation Samples için [Tek Seferlik Kurulum Yordamı'ndan](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) kurulum dosyası Setupvroot.bat disk dizini ve sanal dizini oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="bbf51-150">Hizmet programı dosyalarını %SystemDrive%\Inetpub\wwwroot\servicemodelsamples'ten serviceModelSamples sanal dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bbf51-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="bbf51-151">Dosyaları \bin dizinine eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="bbf51-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="bbf51-152">Bir tarayıcı kullanarak istemci makineden hizmete erişebileceğinizi test edin.</span><span class="sxs-lookup"><span data-stu-id="bbf51-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="bbf51-153">İstemci makinelerini ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="bbf51-153">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="bbf51-154">İstemci programı dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci makinelerine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bbf51-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="bbf51-155">Her istemci yapılandırma dosyasında, hizmetinyeni adresiyle eşleşecek şekilde uç nokta tanımının adres değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bbf51-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="bbf51-156">"Localhost" için yapılan başvuruları adreste tam nitelikli bir etki alanı adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bbf51-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="bbf51-157">Veri kaynak makinesini ayarlama:</span><span class="sxs-lookup"><span data-stu-id="bbf51-157">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="bbf51-158">Veri kaynağı program dosyalarını dile özgü klasörün altındaki \datasource\bin\ klasöründen veri kaynağı makinesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bbf51-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="bbf51-159">Veri kaynağı yapılandırma dosyasında, hizmetinyeni adresiyle eşleşecek şekilde uç nokta tanımının adres değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bbf51-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="bbf51-160">"Localhost" için yapılan başvuruları adreste tam nitelikli bir etki alanı adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bbf51-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="bbf51-161">İstemci makinelerinde, Client.exe komut isteminden başlatın.</span><span class="sxs-lookup"><span data-stu-id="bbf51-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="bbf51-162">Veri kaynağı makinesinde, Datasource.exe'yi komut isteminden başlatın.</span><span class="sxs-lookup"><span data-stu-id="bbf51-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bbf51-163">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="bbf51-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bbf51-164">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bbf51-164">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bbf51-165">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="bbf51-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bbf51-166">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbf51-166">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
