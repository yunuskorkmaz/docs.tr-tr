---
title: İstemci Kimliğine Bürünme
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: e9e85729b10d1c992a22f6c0bea65dfd1e21e7e4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742558"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="e8b97-102">İstemci Kimliğine Bürünme</span><span class="sxs-lookup"><span data-stu-id="e8b97-102">Impersonating the Client</span></span>
<span data-ttu-id="e8b97-103">Kimliğe bürünme örneği, hizmetin çağıran adına sistem kaynaklarına erişebilmesi için çağıran uygulamanın nasıl taklit edilebilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8b97-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="e8b97-104">Bu örnek, [self-Host](../../../../docs/framework/wcf/samples/self-host.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8b97-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="e8b97-105">Hizmet ve istemci yapılandırma dosyaları, [self-Host](../../../../docs/framework/wcf/samples/self-host.md) örneğindeki ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e8b97-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8b97-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="e8b97-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e8b97-107">Hizmet kodu, hizmet üzerindeki `Add` yöntemi, aşağıdaki örnek kodda gösterildiği gibi <xref:System.ServiceModel.OperationBehaviorAttribute> kullanarak çağıranı kimliğine bürünür gibi değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e8b97-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    Console.WriteLine("Received Add({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="e8b97-108">Sonuç olarak, yürütülen iş parçacığının güvenlik bağlamı, `Add` yöntemine girmeden önce çağıranın kimliğine bürünmek ve yöntemden çıkmadan geri döndürülmek üzere çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e8b97-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="e8b97-109">Aşağıdaki örnek kodda gösterilen `DisplayIdentityInformation` yöntemi, arayanın kimliğini görüntüleyen bir yardımcı programdır.</span><span class="sxs-lookup"><span data-stu-id="e8b97-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
```csharp
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tThread Identity            :{0}",  
         WindowsIdentity.GetCurrent().Name);  
    Console.WriteLine("\t\tThread Identity level  :{0}",   
         WindowsIdentity.GetCurrent().ImpersonationLevel);  
    Console.WriteLine("\t\thToken                     :{0}",  
         WindowsIdentity.GetCurrent().Token.ToString());  
    return;  
}  
```  
  
 <span data-ttu-id="e8b97-110">Hizmetindeki `Subtract` yöntemi, aşağıdaki örnek kodda gösterildiği gibi, çağrıyı yapanın zorunlu çağrıları kullanarak taklit eder.</span><span class="sxs-lookup"><span data-stu-id="e8b97-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
```csharp
public double Subtract(double n1, double n2)  
{  
    double result = n1 - n2;  
    Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    Console.WriteLine("Before impersonating");  
    DisplayIdentityInformation();  
  
    if (ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Impersonation ||  
        ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Delegation)  
    {  
        // Impersonate.  
        using (ServiceSecurityContext.Current.WindowsIdentity.Impersonate())  
        {  
            // Make a system call in the caller's context and ACLs   
            // on the system resource are enforced in the caller's context.   
            Console.WriteLine("Impersonating the caller imperatively");  
            DisplayIdentityInformation();  
        }  
    }  
    else  
    {  
        Console.WriteLine("ImpersonationLevel is not high enough to perform this operation.");  
    }  
  
    Console.WriteLine("After reverting");  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="e8b97-111">Bu durumda çağıranın tüm çağrı için kimliğe bürünmediğini ancak yalnızca çağrının bir bölümü için kimliğe bürünülmüş olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e8b97-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="e8b97-112">Genel olarak, en küçük kapsam için kimliğe bürünme işleminin tamamı için kimliğe bürünme tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="e8b97-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="e8b97-113">Diğer yöntemler çağıranın kimliğine bürünemez.</span><span class="sxs-lookup"><span data-stu-id="e8b97-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="e8b97-114">İstemci kodu, kimliğe bürünme düzeyini <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>olarak ayarlanacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e8b97-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="e8b97-115">İstemci, <xref:System.Security.Principal.TokenImpersonationLevel> numaralandırması kullanarak hizmet tarafından kullanılacak kimliğe bürünme düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8b97-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="e8b97-116">Sabit listesi şu değerleri destekler: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> ve <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span><span class="sxs-lookup"><span data-stu-id="e8b97-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="e8b97-117">Windows ACL 'Leri kullanılarak korunan yerel makinedeki bir sistem kaynağına erişirken erişim denetimi gerçekleştirmek için, aşağıdaki örnek kodda gösterildiği gibi kimliğe bürünme düzeyi <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8b97-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="e8b97-118">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e8b97-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="e8b97-119">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e8b97-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8b97-120">Hizmet bir yönetici hesabı altında çalışmalıdır veya altında çalıştığı hesaba HTTP katmanıyla `http://localhost:8000/ServiceModelSamples` URI 'sini kaydetmek için haklar verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e8b97-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="e8b97-121">Bu tür haklar, [Httpcfg. exe aracı](/windows/win32/http/httpcfg-exe)kullanılarak bir [ad alanı ayırması](/windows/win32/http/namespace-reservations-registrations-and-routing) ayarlanarak verilebilir.</span><span class="sxs-lookup"><span data-stu-id="e8b97-121">Such rights can be granted by setting up a [Namespace Reservation](/windows/win32/http/namespace-reservations-registrations-and-routing) using the [Httpcfg.exe tool](/windows/win32/http/httpcfg-exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8b97-122">Windows Server 2003 çalıştıran bilgisayarlarda, kimliğe bürünme yalnızca Host. exe uygulamasının kimliğe bürünme ayrıcalığına sahip olması durumunda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e8b97-122">On computers running Windows Server 2003, impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="e8b97-123">(Varsayılan olarak, yalnızca Yöneticiler bu izne sahiptir.) Bu ayrıcalığı hizmetin çalıştığı bir hesaba eklemek için, **Yönetimsel Araçlar**' a gidin, **yerel güvenlik ilkesi**' ni açın, **Yerel Ilkeler**' i açın, **Kullanıcı hakları ataması**' nı seçin ve **kimlik doğrulamasından sonra istemcinin özelliklerini al** ' ı seçin ve **Özellikler** ' i çift tıklatarak bir kullanıcı veya grup ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e8b97-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e8b97-124">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e8b97-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e8b97-125">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e8b97-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e8b97-126">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e8b97-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e8b97-127">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e8b97-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="e8b97-128">Hizmetin çağıran tarafından taklit olduğunu göstermek için, istemciyi hizmetin altında çalıştığı farklı bir hesap altında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e8b97-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="e8b97-129">Bunu yapmak için, komut isteminde şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="e8b97-129">To do so, at the command prompt, type:</span></span>  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="e8b97-130">Daha sonra parola girmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="e8b97-130">You are then prompted for a password.</span></span> <span data-ttu-id="e8b97-131">Daha önce belirttiğiniz hesabın parolasını girin.</span><span class="sxs-lookup"><span data-stu-id="e8b97-131">Enter the password for the account you previously specified.</span></span>  
  
5. <span data-ttu-id="e8b97-132">İstemcisini çalıştırdığınızda, kimliği farklı kimlik bilgileriyle çalıştırmadan önce ve sonra kimliği aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="e8b97-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
