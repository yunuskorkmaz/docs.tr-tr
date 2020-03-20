---
title: İstemci Kimliğine Bürünme
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 10a8d243b3f053879f183864e955d9260c07865b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183606"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="de885-102">İstemci Kimliğine Bürünme</span><span class="sxs-lookup"><span data-stu-id="de885-102">Impersonating the Client</span></span>
<span data-ttu-id="de885-103">Kimliğe Bürünme örneği, hizmetin arayan adına sistem kaynaklarına erişebilmeleri için servisteki arayan uygulamasının nasıl taklit edilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="de885-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="de885-104">Bu örnek [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) örneğine dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="de885-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="de885-105">Hizmet ve istemci yapılandırma dosyaları [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) örneği ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="de885-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de885-106">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="de885-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="de885-107">Hizmet kodu, hizmetteki `Add` yöntemin aşağıdaki örnek kodda gösterildiği <xref:System.ServiceModel.OperationBehaviorAttribute> gibi kullanarak arayanın kimliğine büründiyi olacak şekilde değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="de885-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="de885-108">Sonuç olarak, yürütme iş parçacığının güvenlik bağlamı `Add` yönteme girmeden önce arayanın kimliğine göre değiştirilir ve yöntemden çıkarken döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="de885-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="de885-109">Aşağıdaki `DisplayIdentityInformation` örnek kodda gösterilen yöntem, arayanın kimliğini görüntüleyen bir yardımcı program işlevidir.</span><span class="sxs-lookup"><span data-stu-id="de885-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
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
  
 <span data-ttu-id="de885-110">Hizmetteki yöntem, `Subtract` aşağıdaki örnek kodda gösterildiği gibi zorunlu çağrıları kullanarak arayanın kimliğine bürünmüş olur.</span><span class="sxs-lookup"><span data-stu-id="de885-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="de885-111">Bu durumda, arayanın tüm arama için taklit olmadığını, yalnızca aramanın bir bölümü için taklit edildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="de885-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="de885-112">Genel olarak, en küçük kapsam için taklit tüm işlem için taklit etmek tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="de885-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="de885-113">Diğer yöntemler arayanın kimliğine bürünmez.</span><span class="sxs-lookup"><span data-stu-id="de885-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="de885-114">İstemci kodu, kimliğe bürünme <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>düzeyini ' olarak ayarlamak üzere değiştirildi</span><span class="sxs-lookup"><span data-stu-id="de885-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="de885-115">İstemci, numaralandırmayı kullanarak <xref:System.Security.Principal.TokenImpersonationLevel> hizmet tarafından kullanılacak kimliğe bürünme düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="de885-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="de885-116">Numaralandırma <xref:System.Security.Principal.TokenImpersonationLevel.None>aşağıdaki değerleri destekler: , <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>ve .</span><span class="sxs-lookup"><span data-stu-id="de885-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="de885-117">Windows ALA'ları kullanılarak korunan yerel makinedeki bir sistem kaynağına erişirken bir erişim denetimi <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>gerçekleştirmek için, kimliğe bürünme düzeyi aşağıdaki örnek kodda gösterildiği gibi ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="de885-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="de885-118">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="de885-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="de885-119">Hizmeti ve istemciyi kapatmak için her konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="de885-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de885-120">Hizmet, idari bir hesap altında çalışmalı veya çalıştığı hesabın `http://localhost:8000/ServiceModelSamples` URI'yi HTTP katmanına kaydetme hakkı verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="de885-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="de885-121">Bu tür [haklar, Httpcfg.exe aracını](/windows/win32/http/httpcfg-exe)kullanarak bir [Namespace Rezervasyonu](/windows/win32/http/namespace-reservations-registrations-and-routing) ayarlayarak verilebilir.</span><span class="sxs-lookup"><span data-stu-id="de885-121">Such rights can be granted by setting up a [Namespace Reservation](/windows/win32/http/namespace-reservations-registrations-and-routing) using the [Httpcfg.exe tool](/windows/win32/http/httpcfg-exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de885-122">Windows Server 2003 çalıştıran bilgisayarlarda, kimliğe bürünme yalnızca Host.exe uygulaması Kimliğe Bürünme ayrıcalığına sahipse desteklenir.</span><span class="sxs-lookup"><span data-stu-id="de885-122">On computers running Windows Server 2003, impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="de885-123">(Varsayılan olarak, yalnızca yöneticiler bu izne sahiptir.) Bu ayrıcalığı bir hesaba eklemek için hizmet, Yönetim Araçları'na gidin, Yerel Güvenlik **İlkesi'ni**açın, **Yerel** **İlkeler'i**açın, **Kullanıcı Hakları Ataması'nı**tıklatın ve Kimlik **Doğrulama'dan sonra İstemcili'yi taklit** etmeyi seçin ve kullanıcı veya grup eklemek için **Özellikleri** çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="de885-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="de885-124">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="de885-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="de885-125">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="de885-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="de885-126">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="de885-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="de885-127">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="de885-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="de885-128">Hizmetin arayanın kimliğine büründiyi göstermek için istemciyi, hizmetin altında çalıştırdığı hesaptan farklı bir hesap altında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="de885-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="de885-129">Bunu yapmak için, komut istemi, yazın:</span><span class="sxs-lookup"><span data-stu-id="de885-129">To do so, at the command prompt, type:</span></span>  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="de885-130">Daha sonra bir parola istenir.</span><span class="sxs-lookup"><span data-stu-id="de885-130">You are then prompted for a password.</span></span> <span data-ttu-id="de885-131">Daha önce belirttiğiniz hesabın parolasını girin.</span><span class="sxs-lookup"><span data-stu-id="de885-131">Enter the password for the account you previously specified.</span></span>  
  
5. <span data-ttu-id="de885-132">İstemciyi çalıştırdığınızda, farklı kimlik bilgileriyle çalıştırmadan önce ve sonra kimliği not edin.</span><span class="sxs-lookup"><span data-stu-id="de885-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
