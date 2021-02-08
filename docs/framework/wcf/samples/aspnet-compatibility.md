---
description: 'Daha fazla bilgi edinin: ASP.NET uyumluluğu'
title: ASP.NET Uyumluluğu
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: a5685481a16d87715d4fc9096055af5be479f459
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778860"
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="de877-103">ASP.NET Uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="de877-103">ASP.NET Compatibility</span></span>

<span data-ttu-id="de877-104">Bu örnek, Windows Communication Foundation (WCF) ' de ASP.NET uyumluluk modunun nasıl etkinleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="de877-104">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="de877-105">ASP.NET uyumluluk modunda çalışan hizmetler, ASP.NET uygulama ardışık düzenine tam olarak katılır ve dosya/URL yetkilendirmesi, oturum durumu ve sınıf gibi ASP.NET özelliklerden yararlanalabilirler <xref:System.Web.HttpContext> .</span><span class="sxs-lookup"><span data-stu-id="de877-105">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="de877-106"><xref:System.Web.HttpContext>Sınıfı, tanımlama bilgilerine, oturumlara ve diğer ASP.NET özelliklerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="de877-106">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="de877-107">Bu mod, bağlamaların HTTP aktarımını kullanmasını gerektirir ve hizmetin kendisi IIS 'de barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="de877-107">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>

<span data-ttu-id="de877-108">Bu örnekte, istemci bir konsol uygulaması (yürütülebilir) ve hizmet Internet Information Services (IIS) içinde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="de877-108">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="de877-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="de877-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="de877-110">Bu örnek, çalıştırmak için bir .NET Framework 4 uygulama havuzu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="de877-110">This sample requires a .NET Framework 4 application pool in order to run.</span></span> <span data-ttu-id="de877-111">Yeni bir uygulama havuzu oluşturmak veya varsayılan uygulama havuzunu değiştirmek için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="de877-111">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>

1. <span data-ttu-id="de877-112">**Denetim Masası 'nı** açın.</span><span class="sxs-lookup"><span data-stu-id="de877-112">Open **Control Panel**.</span></span>  <span data-ttu-id="de877-113">**Sistem ve güvenlik** başlığı altında **Yönetimsel Araçlar** uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="de877-113">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="de877-114">**Internet Information Services (IIS) Yöneticisi** uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="de877-114">Open the **Internet Information Services (IIS) Manager** applet.</span></span>

2. <span data-ttu-id="de877-115">**Bağlantılar** bölmesinde TreeView ' ı genişletin.</span><span class="sxs-lookup"><span data-stu-id="de877-115">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="de877-116">**Uygulama havuzları** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="de877-116">Select the **Application Pools** node.</span></span>

3. <span data-ttu-id="de877-117">Varsayılan uygulama havuzunu .NET Framework 4 ' ü kullanacak şekilde ayarlamak için (mevcut sitelerde uyumsuzluk sorunlarına neden olabilir), **DefaultAppPool** liste öğesine sağ tıklayın ve **temel ayarlar...** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="de877-117">To set the default application pool to use .NET Framework 4 (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="de877-118">**.NET Framework sürüm** çekmeyi, **.NET Framework v 4.0.30128** (veya üzeri) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="de877-118">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>

4. <span data-ttu-id="de877-119">.NET Framework 4 kullanan yeni bir uygulama havuzu oluşturmak için (diğer uygulamaların uyumluluğunu korumak için), **uygulama havuzları** düğümüne sağ tıklayın ve **Uygulama Havuzu Ekle...** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="de877-119">To create a new application pool that uses .NET Framework 4 (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="de877-120">Yeni uygulama havuzunu adlandırın ve **.NET Framework sürüm** çekmeyi **.NET Framework v 4.0.30128** (veya üzeri) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="de877-120">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="de877-121">Aşağıdaki kurulum adımlarını çalıştırdıktan sonra, **servicemodelsamples** uygulamasına sağ tıklayın ve **Uygulamayı Yönet**, **Gelişmiş ayarlar..**. seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="de877-121">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="de877-122">**Uygulama havuzunu** yeni uygulama havuzuna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="de877-122">Set the **Application Pool** to the new application pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de877-123">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="de877-123">The samples may already be installed on your computer.</span></span> <span data-ttu-id="de877-124">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="de877-124">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="de877-125">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="de877-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="de877-126">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="de877-126">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`

<span data-ttu-id="de877-127">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md)Başlarken ' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="de877-127">This sample is based on the [Getting Started](getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="de877-128">`ICalculator`Sözleşme, `ICalculatorSession` çalışan bir sonuç tutarken bir dizi işlemin gerçekleştirilmesine izin veren sözleşme olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="de877-128">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>

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

<span data-ttu-id="de877-129">Bu hizmet, bir hesaplama gerçekleştirmek için birden çok hizmet işlemi çağrılıp her bir istemci için özelliği kullanarak durumu korur.</span><span class="sxs-lookup"><span data-stu-id="de877-129">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="de877-130">İstemci çağırarak geçerli sonucu alabilir `Result` ve çağırarak sıfıra sıfır sonucunu temizleyebilir `Clear` .</span><span class="sxs-lookup"><span data-stu-id="de877-130">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>

<span data-ttu-id="de877-131">Hizmet, her istemci oturumu için sonucu depolamak üzere ASP.NET oturumunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="de877-131">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="de877-132">Bu, hizmetin, her istemci için çalışan sonucu hizmete birden çok çağrıda korumasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="de877-132">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>

> [!NOTE]
> <span data-ttu-id="de877-133">ASP.NET oturum durumu ve WCF oturumları çok farklı şeylere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="de877-133">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="de877-134">WCF oturumları hakkında ayrıntılar için bkz. [oturum](session.md) .</span><span class="sxs-lookup"><span data-stu-id="de877-134">See [Session](session.md) for details on WCF sessions.</span></span>

<span data-ttu-id="de877-135">Hizmetin ASP.NET oturum durumu üzerinde bir intimate bağımlılığı vardır ve ASP.NET uyumluluk modunun düzgün şekilde çalışmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="de877-135">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="de877-136">Bu gereksinimler özniteliği uygulanarak bildirimli olarak ifade edilir `AspNetCompatibilityRequirements` .</span><span class="sxs-lookup"><span data-stu-id="de877-136">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>

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

<span data-ttu-id="de877-137">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="de877-137">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="de877-138">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="de877-138">Press ENTER in the client window to shut down the client.</span></span>

```console
0, + 100, - 50, * 17.65, / 2 = 441.25
Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="de877-139">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="de877-139">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="de877-140">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="de877-140">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="de877-141">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="de877-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="de877-142">Çözüm oluşturulduktan sonra, ServiceModelSamples uygulamasını IIS 7,0 ' de ayarlamak için Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="de877-142">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="de877-143">ServiceModelSamples dizini artık bir IIS 7,0 uygulaması olarak görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="de877-143">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="de877-144">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="de877-144">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="de877-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de877-145">See also</span></span>

- <span data-ttu-id="de877-146">[AppFabric barındırma ve kalıcılık örnekleri](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="de877-146">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
