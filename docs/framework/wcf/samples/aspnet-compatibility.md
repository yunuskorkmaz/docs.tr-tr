---
title: "ASP.NET Uyumluluğu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2c8cf38e65bbc917720b1a1c5b604d81ca536c14
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="c4c58-102">ASP.NET Uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="c4c58-102">ASP.NET Compatibility</span></span>
<span data-ttu-id="c4c58-103">Bu örnek nasıl etkinleştirileceğini göstermektedir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uyumluluk modunda [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c4c58-103">This sample demonstrates how to enable [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Compatibility mode in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="c4c58-104">Çalışan hizmetleri [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uyumluluk modu katılmak tam olarak [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama kanal ve yapabilirsiniz kullanımı [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dosya/URL yetkilendirmesi, oturum durumu gibi özellikleri ve <xref:System.Web.HttpContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c4c58-104">Services running in [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Compatibility mode participate fully in the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application pipeline and can make use of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="c4c58-105"><xref:System.Web.HttpContext> Sınıfı, tanımlama bilgileri, oturumlar ve diğer erişmesine olanak tanır [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] özellikleri.</span><span class="sxs-lookup"><span data-stu-id="c4c58-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] features.</span></span> <span data-ttu-id="c4c58-106">Bu mod HTTP aktarımını bağlamaları kullanın ve hizmet IIS'de barındırılması gerekir gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c4c58-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>  
  
 <span data-ttu-id="c4c58-107">Bu örnekte, istemci bir konsol uygulaması (bir yürütülebilir dosya) ve Internet Information Services (IIS) barındırılan hizmetindeki.</span><span class="sxs-lookup"><span data-stu-id="c4c58-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4c58-108">Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="c4c58-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4c58-109">Bu örnek gerektiren bir [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] çalıştırmak için uygulama havuzu.</span><span class="sxs-lookup"><span data-stu-id="c4c58-109">This sample requires a [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] application pool in order to run.</span></span> <span data-ttu-id="c4c58-110">Yeni bir uygulama havuzu oluşturmak için veya varsayılan uygulama havuzunu değiştirmek için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="c4c58-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>  
>   
>  1.  <span data-ttu-id="c4c58-111">Açık **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="c4c58-111">Open **Control Panel**.</span></span>  <span data-ttu-id="c4c58-112">Açık **Yönetimsel Araçlar** altında uygulaması **sistem ve güvenlik** başlığı.</span><span class="sxs-lookup"><span data-stu-id="c4c58-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="c4c58-113">Açık **Internet Information Services (IIS) Yöneticisi** uygulaması.</span><span class="sxs-lookup"><span data-stu-id="c4c58-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>  
> 2.  <span data-ttu-id="c4c58-114">Treeview içinde genişletin **bağlantıları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="c4c58-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="c4c58-115">Seçin **uygulama havuzları** düğümü.</span><span class="sxs-lookup"><span data-stu-id="c4c58-115">Select the **Application Pools** node.</span></span>  
> 3.  <span data-ttu-id="c4c58-116">Varsayılan uygulama havuzunu kullanmak üzere ayarlamak için [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (hangi uyumsuzluk sorunlara neden olan sitelerle), sağ **DefaultAppPool** liste öğesi ve seçin **temel ayarlar...** .</span><span class="sxs-lookup"><span data-stu-id="c4c58-116">To set the default application pool to use [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="c4c58-117">Ayarlama **.Net Framework sürüm** aşağı açılır **.Net Framework v4.0.30128** (veya üstü).</span><span class="sxs-lookup"><span data-stu-id="c4c58-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>  
> 4.  <span data-ttu-id="c4c58-118">Kullanan yeni bir uygulama havuzu oluşturmak için [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (diğer uygulamalar için uyumluluğu korumak için), sağ **uygulama havuzları** düğümü ve select **uygulama havuzu Ekle...** .</span><span class="sxs-lookup"><span data-stu-id="c4c58-118">To create a new application pool that uses [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="c4c58-119">Yeni uygulama havuzu adını ve ayarlayın **.Net Framework sürüm** aşağı açılır **.Net Framework v4.0.30128** (veya üstü).</span><span class="sxs-lookup"><span data-stu-id="c4c58-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="c4c58-120">Kurulumu çalıştıran altındaki adımları sonra sağ **ServiceModelSamples** seçin ve uygulama **yönetmek uygulama**, **Gelişmiş ayarlar...** .</span><span class="sxs-lookup"><span data-stu-id="c4c58-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="c4c58-121">Ayarlama **uygulama havuzu** yeni bir uygulama havuzu için.</span><span class="sxs-lookup"><span data-stu-id="c4c58-121">Set the **Application Pool** to the new application pool.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c4c58-122">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="c4c58-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c4c58-123">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c4c58-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c4c58-124">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c4c58-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c4c58-125">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c4c58-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 <span data-ttu-id="c4c58-126">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hesap makinesi hizmetinin uygular.</span><span class="sxs-lookup"><span data-stu-id="c4c58-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="c4c58-127">`ICalculator` Sözleşme olarak değiştirildi `ICalculatorSession` çalışan bir sonuç tutarken gerçekleştirilecek işlem kümesi izin vermek sözleşme.</span><span class="sxs-lookup"><span data-stu-id="c4c58-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>  
  
```  
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
  
 <span data-ttu-id="c4c58-128">Hizmet durumu, bir hesaplama gerçekleştirmek için birden çok hizmet işlemleri adlı gibi her bir istemci için özelliğini kullanarak korur.</span><span class="sxs-lookup"><span data-stu-id="c4c58-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="c4c58-129">İstemcisi, çağırarak geçerli sonucu alabilir `Result` ve çağırarak sıfır sonucu temizleyebilirsiniz `Clear`.</span><span class="sxs-lookup"><span data-stu-id="c4c58-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>  
  
 <span data-ttu-id="c4c58-130">Hizmet kullandığı [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] her istemci oturumu için sonucunu depolamak için oturumu.</span><span class="sxs-lookup"><span data-stu-id="c4c58-130">The service uses the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] session to store the result for each client session.</span></span> <span data-ttu-id="c4c58-131">Bu hizmet için birden fazla çağrı boyunca her istemci için çalışan sonuç korumak hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4c58-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="c4c58-132">oturum durumu ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oturumları olan çok farklı işlemler.</span><span class="sxs-lookup"><span data-stu-id="c4c58-132"> session state and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessions are very different things.</span></span>  <span data-ttu-id="c4c58-133">Bkz: [oturum](../../../../docs/framework/wcf/samples/session.md) hakkında ayrıntılı bilgi için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oturumları.</span><span class="sxs-lookup"><span data-stu-id="c4c58-133">See the [Session](../../../../docs/framework/wcf/samples/session.md) for details on [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessions.</span></span>  
  
 <span data-ttu-id="c4c58-134">Hizmet intimate bir bağımlılığı olduğundan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] oturum durumu ve gerektirir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] düzgün çalışması için uyumluluk modunda.</span><span class="sxs-lookup"><span data-stu-id="c4c58-134">The service has an intimate dependency on [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] session state and requires [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] compatibility mode to function correctly.</span></span> <span data-ttu-id="c4c58-135">Bu gereksinimleri uygulayarak bildirimli olarak ifade edilir `AspNetCompatibilityRequirements` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c4c58-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>  
  
```  
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
  
 <span data-ttu-id="c4c58-136">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c4c58-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c4c58-137">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c4c58-137">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c4c58-138">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="c4c58-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c4c58-139">Gerçekleştirilen mutlaka [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4c58-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c4c58-140">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4c58-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c4c58-141">Çözüm oluşturulduktan sonra ServiceModelSamples uygulamada ayarlamak için Setup.bat çalıştırmak [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c4c58-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="c4c58-142">ServiceModelSamples dizin şimdi olarak görünmesi gereken bir [!INCLUDE[iisver](../../../../includes/iisver-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="c4c58-142">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="c4c58-143">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4c58-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c58-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4c58-144">See Also</span></span>  
 [<span data-ttu-id="c4c58-145">AppFabric barındırma ve kalıcılığı örnekleri</span><span class="sxs-lookup"><span data-stu-id="c4c58-145">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
