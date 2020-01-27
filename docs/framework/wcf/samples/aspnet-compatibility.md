---
title: ASP.NET Uyumluluğu
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: 1f1690cdd1a880c852abc04ea8e4958bae2c5432
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728025"
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="956de-102">ASP.NET Uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="956de-102">ASP.NET Compatibility</span></span>

<span data-ttu-id="956de-103">Bu örnek, Windows Communication Foundation (WCF) ' de ASP.NET uyumluluk modunun nasıl etkinleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="956de-103">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="956de-104">ASP.NET uyumluluk modunda çalışan hizmetler, ASP.NET uygulama ardışık düzenine tam olarak katılır ve dosya/URL yetkilendirmesi, oturum durumu ve <xref:System.Web.HttpContext> sınıfı gibi ASP.NET özelliklerden yararlanalabilirler.</span><span class="sxs-lookup"><span data-stu-id="956de-104">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="956de-105"><xref:System.Web.HttpContext> sınıfı, tanımlama bilgilerine, oturumlara ve diğer ASP.NET özelliklerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="956de-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="956de-106">Bu mod, bağlamaların HTTP aktarımını kullanmasını gerektirir ve hizmetin kendisi IIS 'de barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="956de-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>

<span data-ttu-id="956de-107">Bu örnekte, istemci bir konsol uygulaması (yürütülebilir) ve hizmet Internet Information Services (IIS) içinde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="956de-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="956de-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="956de-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="956de-109">Bu örnek, çalıştırmak için bir .NET Framework 4 uygulama havuzu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="956de-109">This sample requires a .NET Framework 4 application pool in order to run.</span></span> <span data-ttu-id="956de-110">Yeni bir uygulama havuzu oluşturmak veya varsayılan uygulama havuzunu değiştirmek için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="956de-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>

1. <span data-ttu-id="956de-111">**Denetim Masası**'nı açın.</span><span class="sxs-lookup"><span data-stu-id="956de-111">Open **Control Panel**.</span></span>  <span data-ttu-id="956de-112">**Sistem ve güvenlik** başlığı altında **Yönetimsel Araçlar** uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="956de-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="956de-113">**Internet Information Services (IIS) Yöneticisi** uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="956de-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>

2. <span data-ttu-id="956de-114">**Bağlantılar** bölmesinde TreeView ' ı genişletin.</span><span class="sxs-lookup"><span data-stu-id="956de-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="956de-115">**Uygulama havuzları** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="956de-115">Select the **Application Pools** node.</span></span>

3. <span data-ttu-id="956de-116">Varsayılan uygulama havuzunu .NET Framework 4 ' ü kullanacak şekilde ayarlamak için (mevcut sitelerde uyumsuzluk sorunlarına neden olabilir), **DefaultAppPool** liste öğesine sağ tıklayın ve **temel ayarlar...** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="956de-116">To set the default application pool to use .NET Framework 4 (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="956de-117">**.NET Framework sürüm** çekmeyi, **.NET Framework v 4.0.30128** (veya üzeri) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="956de-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>

4. <span data-ttu-id="956de-118">.NET Framework 4 kullanan yeni bir uygulama havuzu oluşturmak için (diğer uygulamaların uyumluluğunu korumak için), **uygulama havuzları** düğümüne sağ tıklayın ve **Uygulama Havuzu Ekle...** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="956de-118">To create a new application pool that uses .NET Framework 4 (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="956de-119">Yeni uygulama havuzunu adlandırın ve **.NET Framework sürüm** çekmeyi **.NET Framework v 4.0.30128** (veya üzeri) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="956de-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="956de-120">Aşağıdaki kurulum adımlarını çalıştırdıktan sonra, **servicemodelsamples** uygulamasına sağ tıklayın ve **Uygulamayı Yönet**, **Gelişmiş ayarlar..** . seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="956de-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="956de-121">**Uygulama havuzunu** yeni uygulama havuzuna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="956de-121">Set the **Application Pool** to the new application pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="956de-122">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="956de-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="956de-123">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="956de-123">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="956de-124">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="956de-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="956de-125">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="956de-125">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`

<span data-ttu-id="956de-126">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md)Başlarken ' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="956de-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="956de-127">`ICalculator` sözleşmesi, çalışan bir sonuç tutarken bir dizi işlemin gerçekleştirilmesine izin veren `ICalculatorSession` sözleşmesi olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="956de-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>

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

<span data-ttu-id="956de-128">Bu hizmet, bir hesaplama gerçekleştirmek için birden çok hizmet işlemi çağrılıp her bir istemci için özelliği kullanarak durumu korur.</span><span class="sxs-lookup"><span data-stu-id="956de-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="956de-129">İstemci, `Result` çağırarak geçerli sonucu alabilir ve `Clear`çağırarak sonucu sıfıra temizleyebilir.</span><span class="sxs-lookup"><span data-stu-id="956de-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>

<span data-ttu-id="956de-130">Hizmet, her istemci oturumu için sonucu depolamak üzere ASP.NET oturumunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="956de-130">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="956de-131">Bu, hizmetin, her istemci için çalışan sonucu hizmete birden çok çağrıda korumasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="956de-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>

> [!NOTE]
> <span data-ttu-id="956de-132">ASP.NET oturum durumu ve WCF oturumları çok farklı şeylere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="956de-132">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="956de-133">WCF oturumları hakkında ayrıntılar için bkz. [oturum](../../../../docs/framework/wcf/samples/session.md) .</span><span class="sxs-lookup"><span data-stu-id="956de-133">See [Session](../../../../docs/framework/wcf/samples/session.md) for details on WCF sessions.</span></span>

<span data-ttu-id="956de-134">Hizmetin ASP.NET oturum durumu üzerinde bir intimate bağımlılığı vardır ve ASP.NET uyumluluk modunun düzgün şekilde çalışmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="956de-134">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="956de-135">Bu gereksinimler `AspNetCompatibilityRequirements` özniteliği uygulanarak bildirimli olarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="956de-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>

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

<span data-ttu-id="956de-136">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="956de-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="956de-137">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="956de-137">Press ENTER in the client window to shut down the client.</span></span>

```console
0, + 100, - 50, * 17.65, / 2 = 441.25
Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="956de-138">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="956de-138">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="956de-139">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="956de-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="956de-140">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="956de-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="956de-141">Çözüm derlendikten sonra, ServiceModelSamples uygulamasını IIS 7,0 ' de ayarlamak için Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="956de-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="956de-142">ServiceModelSamples dizini artık bir IIS 7,0 uygulaması olarak görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="956de-142">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="956de-143">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="956de-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="956de-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="956de-144">See also</span></span>

- <span data-ttu-id="956de-145">[AppFabric barındırma ve kalıcılık örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="956de-145">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
