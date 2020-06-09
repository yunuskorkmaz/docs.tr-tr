---
title: İstemci Kimliğine Bürünme
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: b5272d8b4dbac60e14fe87accbb08a2073ed65ab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594640"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="fda58-102">İstemci Kimliğine Bürünme</span><span class="sxs-lookup"><span data-stu-id="fda58-102">Impersonating the Client</span></span>
<span data-ttu-id="fda58-103">Kimliğe bürünme örneği, hizmetin çağıran adına sistem kaynaklarına erişebilmesi için çağıran uygulamanın nasıl taklit edilebilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fda58-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="fda58-104">Bu örnek, [self-Host](self-host.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="fda58-104">This sample is based on the [Self-Host](self-host.md) sample.</span></span> <span data-ttu-id="fda58-105">Hizmet ve istemci yapılandırma dosyaları, [self-Host](self-host.md) örneğindeki ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="fda58-105">The service and client configuration files are the same as that of the [Self-Host](self-host.md) sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fda58-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="fda58-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fda58-107">Hizmet kodu, `Add` hizmette yöntemi <xref:System.ServiceModel.OperationBehaviorAttribute> Aşağıdaki örnek kodda gösterildiği gibi kullanarak çağıran tarafından taklit edilecek şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fda58-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="fda58-108">Sonuç olarak, çalışan iş parçacığının güvenlik bağlamı, `Add` yöntemi girmeden ve yönteminden çıkmadan geri döndürülmeden önce çağıranın kimliğine bürünülecek.</span><span class="sxs-lookup"><span data-stu-id="fda58-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="fda58-109">`DisplayIdentityInformation`Aşağıdaki örnek kodda gösterilen yöntemi, arayanın kimliğini gösteren bir yardımcı programdır.</span><span class="sxs-lookup"><span data-stu-id="fda58-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
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
  
 <span data-ttu-id="fda58-110">`Subtract`Hizmetindeki yöntemi, aşağıdaki örnek kodda gösterildiği gibi, çağrıyı yapanın zorunlu çağrıları kullanarak taklit eder.</span><span class="sxs-lookup"><span data-stu-id="fda58-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="fda58-111">Bu durumda çağıranın tüm çağrı için kimliğe bürünmediğini ancak yalnızca çağrının bir bölümü için kimliğe bürünülmüş olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fda58-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="fda58-112">Genel olarak, en küçük kapsam için kimliğe bürünme işleminin tamamı için kimliğe bürünme tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="fda58-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="fda58-113">Diğer yöntemler çağıranın kimliğine bürünemez.</span><span class="sxs-lookup"><span data-stu-id="fda58-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="fda58-114">İstemci kodu, kimliğe bürünme düzeyini olarak ayarlanacak şekilde değiştirilmiştir <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> .</span><span class="sxs-lookup"><span data-stu-id="fda58-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="fda58-115">İstemci, sabit listesini kullanarak hizmet tarafından kullanılacak kimliğe bürünme düzeyini belirtir <xref:System.Security.Principal.TokenImpersonationLevel> .</span><span class="sxs-lookup"><span data-stu-id="fda58-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="fda58-116">Sabit listesi şu değerleri destekler: <xref:System.Security.Principal.TokenImpersonationLevel.None> , <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> , <xref:System.Security.Principal.TokenImpersonationLevel.Identification> <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> ve <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> .</span><span class="sxs-lookup"><span data-stu-id="fda58-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="fda58-117">Windows ACL 'Leri kullanılarak korunan yerel makinedeki bir sistem kaynağına erişirken erişim denetimi gerçekleştirmek için, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> Aşağıdaki örnek kodda gösterildiği gibi kimliğe bürünme düzeyi olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fda58-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="fda58-118">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fda58-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="fda58-119">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fda58-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fda58-120">Hizmetin bir yönetim hesabı altında çalışması veya altında çalıştığı hesaba, URI 'yi HTTP katmanıyla kaydetmek için haklar verilmelidir `http://localhost:8000/ServiceModelSamples` .</span><span class="sxs-lookup"><span data-stu-id="fda58-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="fda58-121">Bu tür haklar, [Httpcfg. exe aracı](/windows/win32/http/httpcfg-exe)kullanılarak bir [ad alanı ayırması](/windows/win32/http/namespace-reservations-registrations-and-routing) ayarlanarak verilebilir.</span><span class="sxs-lookup"><span data-stu-id="fda58-121">Such rights can be granted by setting up a [Namespace Reservation](/windows/win32/http/namespace-reservations-registrations-and-routing) using the [Httpcfg.exe tool](/windows/win32/http/httpcfg-exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fda58-122">Windows Server 2003 çalıştıran bilgisayarlarda, kimliğe bürünme yalnızca Host. exe uygulamasının kimliğe bürünme ayrıcalığına sahip olması durumunda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fda58-122">On computers running Windows Server 2003, impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="fda58-123">(Varsayılan olarak, yalnızca Yöneticiler bu izne sahiptir.) Bu ayrıcalığı hizmetin çalıştığı bir hesaba eklemek için, **Yönetimsel Araçlar**' a gidin, **yerel güvenlik ilkesi**' ni açın, **Yerel Ilkeler**' i açın, **Kullanıcı hakları ataması**' nı seçin ve **kimlik doğrulamasından sonra istemcinin özelliklerini al** ' ı seçin ve **Özellikler** ' i çift tıklatarak bir kullanıcı veya grup ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fda58-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fda58-124">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fda58-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fda58-125">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fda58-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fda58-126">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fda58-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fda58-127">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fda58-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="fda58-128">Hizmetin çağıran tarafından taklit olduğunu göstermek için, istemciyi hizmetin altında çalıştığı farklı bir hesap altında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fda58-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="fda58-129">Bunu yapmak için, komut isteminde şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="fda58-129">To do so, at the command prompt, type:</span></span>  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="fda58-130">Daha sonra parola girmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="fda58-130">You are then prompted for a password.</span></span> <span data-ttu-id="fda58-131">Daha önce belirttiğiniz hesabın parolasını girin.</span><span class="sxs-lookup"><span data-stu-id="fda58-131">Enter the password for the account you previously specified.</span></span>  
  
5. <span data-ttu-id="fda58-132">İstemcisini çalıştırdığınızda, kimliği farklı kimlik bilgileriyle çalıştırmadan önce ve sonra kimliği aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="fda58-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
