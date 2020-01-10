---
title: Kimliğe Bürünme ve Geri Alma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
ms.openlocfilehash: 14b01ec3ac800abd795e87b641a442df100f102b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706025"
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="5a856-102">Kimliğe Bürünme ve Geri Alma</span><span class="sxs-lookup"><span data-stu-id="5a856-102">Impersonating and Reverting</span></span>
<span data-ttu-id="5a856-103">Bazen bir Windows hesabının kimliğine bürünmek için bir Windows hesabı belirteci edinmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5a856-103">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="5a856-104">Örneğin, ASP.NET tabanlı uygulamanızın farklı zamanlarda birkaç kullanıcı adına işlem yapması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5a856-104">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="5a856-105">Uygulamanız Internet Information Services (IIS) tarafından bir yöneticiyi temsil eden bir belirteci kabul edebilir, bu kullanıcının kimliğine bürünerek bir işlem gerçekleştirir ve önceki kimliğe geri dönebilir.</span><span class="sxs-lookup"><span data-stu-id="5a856-105">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="5a856-106">Daha sonra, IIS 'den daha az haklara sahip bir kullanıcıyı temsil eden bir belirteç kabul edebilir, bazı işlemler gerçekleştirebilir ve yeniden döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5a856-106">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="5a856-107">Uygulamanızın IIS tarafından geçerli iş parçacığına eklenmemiş bir Windows hesabı kimliğine bürünmesi gereken durumlarda, bu hesabın belirtecini alıp hesabı etkinleştirmek için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a856-107">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="5a856-108">Bunu aşağıdaki görevleri gerçekleştirerek yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a856-108">You can do this by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="5a856-109">Yönetilmeyen **LogonUser** yöntemine bir çağrı yaparak belirli bir kullanıcı için hesap belirteci alın.</span><span class="sxs-lookup"><span data-stu-id="5a856-109">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="5a856-110">Bu yöntem .NET Framework temel sınıf kitaplığında değildir, ancak yönetilmeyen **Advapi32. dll**dosyasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="5a856-110">This method is not in the .NET Framework base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="5a856-111">Yönetilmeyen koddaki yöntemlere erişim gelişmiş bir işlemdir ve bu tartışmanın kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="5a856-111">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="5a856-112">Daha fazla bilgi için bkz. [yönetilmeyen kodla birlikte çalışma](../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a856-112">For more information, see [Interoperating with Unmanaged Code](../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="5a856-113">**LogonUser** yöntemi ve **Advapi32. dll**hakkında daha fazla bilgi IÇIN bkz. Platform SDK belgeleri.</span><span class="sxs-lookup"><span data-stu-id="5a856-113">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2. <span data-ttu-id="5a856-114">, Belirteci geçirerek **WindowsIdentity** sınıfının yeni bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5a856-114">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="5a856-115">Aşağıdaki kod bu çağrıyı gösterir; burada `hToken` bir Windows belirtecini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5a856-115">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. <span data-ttu-id="5a856-116"><xref:System.Security.Principal.WindowsImpersonationContext> sınıfının yeni bir örneğini oluşturarak ve onu, aşağıdaki kodda gösterildiği gibi başlatılan sınıfın <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> yöntemiyle başlatarak kimliğe bürünme işlemini başlatın.</span><span class="sxs-lookup"><span data-stu-id="5a856-116">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. <span data-ttu-id="5a856-117">Artık taklit etmeniz gerekmiyorsa, aşağıdaki kodda gösterildiği gibi, kimliğe bürünme özelliğini dönüştürmek için <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="5a856-117">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="5a856-118">Güvenilen kod zaten iş parçacığına bir <xref:System.Security.Principal.WindowsPrincipal> nesnesi iliştirmişse, bir hesap belirteci almaz, **kimliğe bürünme**örnek yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a856-118">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="5a856-119">Bu, yalnızca iş parçacığındaki **WindowsPrincipal** nesnesi, işlemin Şu anda yürütülmekte olduğu bir kullanıcıyı temsil ettiğinde yararlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5a856-119">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="5a856-120">Örneğin, Windows kimlik doğrulaması açık ve kimliğe bürünme kapalı ASP.NET kullanarak bu durumla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a856-120">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="5a856-121">Bu durumda, işlem Internet Information Services (IIS) ' de yapılandırılmış bir hesap altında çalışıyor, geçerli sorumlusu ise sayfaya erişen Windows kullanıcısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5a856-121">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="5a856-122">**Kimliğe bürünme** ve **geri alma** seçeneklerinin geçerli çağrı bağlamıyla ilişkili **asıl** nesne (<xref:System.Security.Principal.IPrincipal>) değişikliklerini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5a856-122">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="5a856-123">Bunun yerine, kimliğe bürünme ve geri döndürme geçerli işletim sistemi işlemiyle ilişkili belirteci değiştirir...</span><span class="sxs-lookup"><span data-stu-id="5a856-123">Rather, impersonation and reverting change the token associated with the current operating system process..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a856-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a856-124">See also</span></span>

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [<span data-ttu-id="5a856-125">Sorumlu ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="5a856-125">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
- [<span data-ttu-id="5a856-126">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="5a856-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
