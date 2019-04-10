---
title: İstemci Kimliğine Bürünme
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: bd03ddb2478d8f9938a8c89c04f536a81e9e24da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202475"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="3d709-102">İstemci Kimliğine Bürünme</span><span class="sxs-lookup"><span data-stu-id="3d709-102">Impersonating the Client</span></span>
<span data-ttu-id="3d709-103">Kimliğe bürünme örneği, hizmet adına çağıran sistem kaynaklarına erişebilmesi çağıran uygulama hizmetine bürünülecek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3d709-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="3d709-104">Bu örnek dayanır [barındırma](../../../../docs/framework/wcf/samples/self-host.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="3d709-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="3d709-105">Hizmet ve istemci yapılandırma dosyalarını, aynı olan [barındırma](../../../../docs/framework/wcf/samples/self-host.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="3d709-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d709-106">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="3d709-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3d709-107">Hizmet kodu değiştirilmiş gibi `Add` yöntemi hizmet kimliğine bürünür, çağrıyı <xref:System.ServiceModel.OperationBehaviorAttribute> aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="3d709-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="3d709-108">Sonuç olarak, çalışan bir iş parçacığı güvenlik bağlamında girmeden önce çağıranın kimliğine bürünüp moduna `Add` yöntemi yönteminden çıkılıyor üzerinde geri alındığı bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="3d709-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="3d709-109">`DisplayIdentityInformation` Aşağıdaki örnek kodda gösterilen çağıranının kimliğini görüntüler bir yardımcı program işlevi yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="3d709-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
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
  
 <span data-ttu-id="3d709-110">`Subtract` Hizmet yöntemi, kesinlik temelli çağrı aşağıdaki örnek kodda gösterildiği gibi çağrıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3d709-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="3d709-111">Bu durumda arayan için tüm arama temsili değildir ancak yalnızca bir kısmını arama için Kimliğine bürünülen unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3d709-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="3d709-112">Genel olarak, en küçük kapsam için kimliğine bürünmek için tüm işlem kimliğine bürünmek için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="3d709-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="3d709-113">Diğer yöntemleri çağıran kimliğine bürünme.</span><span class="sxs-lookup"><span data-stu-id="3d709-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="3d709-114">Kimliğe bürünme düzeyini ayarlamak için istemci kodu değiştirilmiş <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span><span class="sxs-lookup"><span data-stu-id="3d709-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="3d709-115">İstemcinin kimliğe bürünme düzeyi kullanarak hizmeti tarafından kullanılacak belirtir <xref:System.Security.Principal.TokenImpersonationLevel> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="3d709-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="3d709-116">Numaralandırma aşağıdaki değerlerini destekler: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> ve <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span><span class="sxs-lookup"><span data-stu-id="3d709-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="3d709-117">Yerel makinedeki Windows ACL'leri kullanarak korumalı bir sistem kaynağını erişirken bir erişim denetimi gerçekleştirmek için kimliğe bürünme düzeyi ayarlanmalıdır <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="3d709-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="3d709-118">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3d709-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="3d709-119">Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3d709-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d709-120">Bir yönetici hesabı altında ya da çalışan hizmet gerekir veya altında çalıştığı hesabı kaydetme hakkı verilmesi `http://localhost:8000/ServiceModelSamples` URI HTTP katman.</span><span class="sxs-lookup"><span data-stu-id="3d709-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="3d709-121">Oluşturarak bu hakların verilmesi bir [Namespace ayırma](https://go.microsoft.com/fwlink/?LinkId=95012) kullanarak [Httpcfg.exe aracı](https://go.microsoft.com/fwlink/?LinkId=95010).</span><span class="sxs-lookup"><span data-stu-id="3d709-121">Such rights can be granted by setting up a [Namespace Reservation](https://go.microsoft.com/fwlink/?LinkId=95012) using the [Httpcfg.exe tool](https://go.microsoft.com/fwlink/?LinkId=95010).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d709-122">Çalıştıran bilgisayarlarda [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], kimliğe bürünme, yalnızca Host.exe uygulamanın kimliğe bürünme ayrıcalık varsa desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3d709-122">On computers running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="3d709-123">(Varsayılan olarak, yalnızca Yöneticiler bu izne sahip.) Hizmet olarak çalıştığı bir hesabın bu ayrıcalığı eklemek için Git **Yönetimsel Araçlar**açın **yerel güvenlik ilkesi**açın **yerel ilkeler**, tıklayın**Kullanıcı hakları ataması**seçip **kimlik doğrulamasından sonra istemcinin özelliklerini al** ve çift **özellikleri** bir kullanıcı veya grup eklemek için.</span><span class="sxs-lookup"><span data-stu-id="3d709-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3d709-124">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="3d709-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3d709-125">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d709-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="3d709-126">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d709-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="3d709-127">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d709-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="3d709-128">Hizmet, çağıranın kimliğine bürünür göstermek için İstemci hizmetinin altında çalışmakta olduğu olandan farklı bir hesap altında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3d709-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="3d709-129">Komut isteminde Bunu yapmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="3d709-129">To do so, at the command prompt, type:</span></span>  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="3d709-130">Ardından, bir parola istenir.</span><span class="sxs-lookup"><span data-stu-id="3d709-130">You are then prompted for a password.</span></span> <span data-ttu-id="3d709-131">Daha önce belirtilen hesap için parolayı girin.</span><span class="sxs-lookup"><span data-stu-id="3d709-131">Enter the password for the account you previously specified.</span></span>  
  
5.  <span data-ttu-id="3d709-132">İstemci çalıştırdığınızda, önce ve sonra onu farklı kimlik bilgileri ile çalıştırma kimliğini not edin.</span><span class="sxs-lookup"><span data-stu-id="3d709-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
