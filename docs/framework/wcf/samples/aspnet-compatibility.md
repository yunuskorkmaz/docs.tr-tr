---
title: ASP.NET Uyumluluğu
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: 521ab07d2a747927a7b26c38221f59de736990b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112534"
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="b21cf-102">ASP.NET Uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="b21cf-102">ASP.NET Compatibility</span></span>
<span data-ttu-id="b21cf-103">Bu örnek, ASP.NET uyumluluk modunun Windows Communication Foundation (WCF) etkinleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="b21cf-103">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="b21cf-104">ASP.NET özellikleri gibi dosya/URL yetkilendirme, oturum durumu ASP.NET modu tam ASP.NET uygulama ardışık düzeninizde katılır ve yapabilirsiniz uyumluluğu çalışan hizmetleri kullanımını ve <xref:System.Web.HttpContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b21cf-104">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="b21cf-105"><xref:System.Web.HttpContext> Sınıfı tanımlama bilgileri, oturumları ve diğer ASP.NET özellikleri erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b21cf-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="b21cf-106">Bu mod, HTTP aktarımı bağlamaları kullanın ve hizmeti IIS'de barındırılan gerekir gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b21cf-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>  
  
 <span data-ttu-id="b21cf-107">Bu örnekte, istemci bir konsol uygulaması (bir yürütülebilir dosya) ve hizmet Internet Information Services (IIS) içinde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="b21cf-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b21cf-108">Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="b21cf-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="b21cf-109">Bu örnek gerektiren bir [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] çalıştırmak için uygulama havuzu.</span><span class="sxs-lookup"><span data-stu-id="b21cf-109">This sample requires a [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] application pool in order to run.</span></span> <span data-ttu-id="b21cf-110">Yeni bir uygulama havuzu oluşturmak veya varsayılan uygulama havuzunu değiştirmek için şu adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="b21cf-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>  

1.  <span data-ttu-id="b21cf-111">**Denetim Masası**'nı açın.</span><span class="sxs-lookup"><span data-stu-id="b21cf-111">Open **Control Panel**.</span></span>  <span data-ttu-id="b21cf-112">Açık **Yönetimsel Araçlar** uygulaması altında **sistem ve güvenlik** başlığı.</span><span class="sxs-lookup"><span data-stu-id="b21cf-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="b21cf-113">Açık **Internet Information Services (IIS) Yöneticisi'ni** uygulaması.</span><span class="sxs-lookup"><span data-stu-id="b21cf-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>  

2.  <span data-ttu-id="b21cf-114">Ağaç görünümünde genişletin **bağlantıları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="b21cf-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="b21cf-115">Seçin **uygulama havuzları** düğümü.</span><span class="sxs-lookup"><span data-stu-id="b21cf-115">Select the **Application Pools** node.</span></span>  

3.  <span data-ttu-id="b21cf-116">Varsayılan uygulama havuzunu kullanmak için ayarlanacak [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (hangi uyumsuzluk sorunlara neden var olan siteler ile), sağ **DefaultAppPool** seçin ve liste öğesi **temel ayarları...** .</span><span class="sxs-lookup"><span data-stu-id="b21cf-116">To set the default application pool to use [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="b21cf-117">Ayarlama **.Net Framework sürümü** aşağı açılır **.Net Framework v4.0.30128** (veya üzeri).</span><span class="sxs-lookup"><span data-stu-id="b21cf-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>  

4.  <span data-ttu-id="b21cf-118">Kullanan yeni bir uygulama havuzu oluşturmak için [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (diğer uygulamalar için uyumluluğu korumak için), sağ **uygulama havuzları** düğümünü seçip alt **uygulama havuzu Ekle...** .</span><span class="sxs-lookup"><span data-stu-id="b21cf-118">To create a new application pool that uses [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="b21cf-119">Yeni uygulama havuzu ad verin ve ayarlayın **.Net Framework sürümü** aşağı açılır **.Net Framework v4.0.30128** (veya üzeri).</span><span class="sxs-lookup"><span data-stu-id="b21cf-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="b21cf-120">Aşağıdaki adımlar Kurulumu çalıştırmayı sonra sağ **ServiceModelSamples** seçin ve uygulama **uygulamasını Yönet**, **Gelişmiş ayarlar...** .</span><span class="sxs-lookup"><span data-stu-id="b21cf-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="b21cf-121">Ayarlama **uygulama havuzu** yeni uygulama havuzu için.</span><span class="sxs-lookup"><span data-stu-id="b21cf-121">Set the **Application Pool** to the new application pool.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b21cf-122">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="b21cf-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b21cf-123">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b21cf-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b21cf-124">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b21cf-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b21cf-125">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b21cf-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 <span data-ttu-id="b21cf-126">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hesaplayıcı hizmet uygular.</span><span class="sxs-lookup"><span data-stu-id="b21cf-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="b21cf-127">`ICalculator` Sözleşme olarak değiştirilmiş `ICalculatorSession` çalışan bir sonuç tutarken gerçekleştirilecek işlemleri bir dizi izin vermek sözleşme.</span><span class="sxs-lookup"><span data-stu-id="b21cf-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculatorSession  
{  
    [OperationContract]  
    void Clear();  
    [OperationContract]  
    void AddTo(double n);  
    [OperationContract]  
    void SubtractFrom(double n);  
    [OperationContract]  
    void MultiplyBy(double n);  
    [OperationContract]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 <span data-ttu-id="b21cf-128">Hizmet durumu, bir hesaplama gerçekleştirmek için birden çok hizmet işlemleri adlandırılır gibi her istemci için özellik kullanarak korur.</span><span class="sxs-lookup"><span data-stu-id="b21cf-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="b21cf-129">İstemci, çağırarak geçerli sonucu alabilirsiniz `Result` ve sonucu çağırarak sıfıra temizleyebilirsiniz `Clear`.</span><span class="sxs-lookup"><span data-stu-id="b21cf-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>  
  
 <span data-ttu-id="b21cf-130">Hizmet, her bir istemci oturumu için sonucunu depolamak için ASP.NET oturum kullanır.</span><span class="sxs-lookup"><span data-stu-id="b21cf-130">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="b21cf-131">Bu, birden çok hizmete çağrı arasında her istemci için çalışan sonucu korumak bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="b21cf-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b21cf-132">ASP.NET oturum durumu ve WCF oturumları çok farklı noktalardır.</span><span class="sxs-lookup"><span data-stu-id="b21cf-132">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="b21cf-133">Bkz: [oturumu](../../../../docs/framework/wcf/samples/session.md) WCF oturumları hakkında ayrıntılı bilgi için.</span><span class="sxs-lookup"><span data-stu-id="b21cf-133">See [Session](../../../../docs/framework/wcf/samples/session.md) for details on WCF sessions.</span></span>
  
 <span data-ttu-id="b21cf-134">Hizmet, ASP.NET oturum durumu tutun bir bağımlılığı ve düzgün çalışması için ASP.NET uyumluluk modunun gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b21cf-134">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="b21cf-135">Bu gereksinimleri uygulayarak bildirimli olarak ifade edilir `AspNetCompatibilityRequirements` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b21cf-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>  
  
```csharp  
[AspNetCompatibilityRequirements(RequirementsMode =  
                       AspNetCompatibilityRequirementsMode.Required)]  
public class CalculatorService : ICalculatorSession  
{  
    double Result  
    {  // store result in AspNet Session  
       get {  
          if (HttpContext.Current.Session["Result"] != null)  
             return (double)HttpContext.Current.Session["Result"];  
          return 0.0D;  
       }  
       set  
       {  
          HttpContext.Current.Session["Result"] = value;  
       }  
    }  
    public void Clear()  
    {  
        Result = 0.0D;  
    }  
    public void AddTo(double n)  
    {  
        Result += n;  
    }  
    public void SubtractFrom(double n)  
    {  
        Result -= n;  
    }  
    public void MultiplyBy(double n)  
    {  
        Result *= n;  
    }  
    public void DivideBy(double n)  
    {  
        Result /= n;  
    }  
    public double Result()  
    {  
        return Result;  
    }  
}  
```
  
 <span data-ttu-id="b21cf-136">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b21cf-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b21cf-137">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b21cf-137">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b21cf-138">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b21cf-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b21cf-139">Gerçekleştirilen mutlaka [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b21cf-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b21cf-140">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b21cf-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b21cf-141">Çözüm oluşturulduktan sonra ServiceModelSamples uygulamada ayarlamak için Setup.bat çalıştırma [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b21cf-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="b21cf-142">ServiceModelSamples dizin artık olarak görünmesi gereken bir [!INCLUDE[iisver](../../../../includes/iisver-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="b21cf-142">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="b21cf-143">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b21cf-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b21cf-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b21cf-144">See also</span></span>

- [<span data-ttu-id="b21cf-145">AppFabric barındırma ve Kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="b21cf-145">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
