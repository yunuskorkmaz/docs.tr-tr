---
title: Kimliğe Bürünme ve Geri Alma
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
ms.openlocfilehash: 7eecc7d6cb3fa4cc1c1bd971d36f9d3ca47a7144
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555688"
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="219ff-102">Kimliğe Bürünme ve Geri Alma</span><span class="sxs-lookup"><span data-stu-id="219ff-102">Impersonating and Reverting</span></span>

> [!NOTE]
> <span data-ttu-id="219ff-103">Bu makale Windows için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="219ff-103">This article applies to Windows.</span></span>
>
> <span data-ttu-id="219ff-104">ASP.NET Core hakkında bilgi için bkz. [ASP.NET Core Security](/aspnet/core/security/).</span><span class="sxs-lookup"><span data-stu-id="219ff-104">For information about ASP.NET Core, see [ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="219ff-105">Bazen bir Windows hesabının kimliğine bürünmek için bir Windows hesabı belirteci edinmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="219ff-105">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="219ff-106">Örneğin, ASP.NET tabanlı uygulamanızın farklı zamanlarda birkaç kullanıcı adına işlem yapması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="219ff-106">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="219ff-107">Uygulamanız Internet Information Services (IIS) tarafından bir yöneticiyi temsil eden bir belirteci kabul edebilir, bu kullanıcının kimliğine bürünerek bir işlem gerçekleştirir ve önceki kimliğe geri dönebilir.</span><span class="sxs-lookup"><span data-stu-id="219ff-107">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="219ff-108">Daha sonra, IIS 'den daha az haklara sahip bir kullanıcıyı temsil eden bir belirteç kabul edebilir, bazı işlemler gerçekleştirebilir ve yeniden döndürülür.</span><span class="sxs-lookup"><span data-stu-id="219ff-108">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="219ff-109">Uygulamanızın IIS tarafından geçerli iş parçacığına eklenmemiş bir Windows hesabı kimliğine bürünmesi gereken durumlarda, bu hesabın belirtecini alıp hesabı etkinleştirmek için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="219ff-109">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="219ff-110">Bunu aşağıdaki görevleri gerçekleştirerek yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="219ff-110">You can do this by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="219ff-111">Yönetilmeyen **LogonUser** yöntemine bir çağrı yaparak belirli bir kullanıcı için hesap belirteci alın.</span><span class="sxs-lookup"><span data-stu-id="219ff-111">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="219ff-112">Bu yöntem .NET temel sınıf kitaplığında değildir, ancak yönetilmeyen **advapi32.dll**bulunur.</span><span class="sxs-lookup"><span data-stu-id="219ff-112">This method is not in the .NET base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="219ff-113">Yönetilmeyen koddaki yöntemlere erişim gelişmiş bir işlemdir ve bu tartışmanın kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="219ff-113">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="219ff-114">Daha fazla bilgi için bkz. [yönetilmeyen kodla birlikte çalışma](../../framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="219ff-114">For more information, see [Interoperating with Unmanaged Code](../../framework/interop/index.md).</span></span> <span data-ttu-id="219ff-115">**LogonUser** yöntemi ve **advapi32.dll**hakkında daha fazla bilgi için Platform SDK belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="219ff-115">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2. <span data-ttu-id="219ff-116">, Belirteci geçirerek **WindowsIdentity** sınıfının yeni bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="219ff-116">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="219ff-117">Aşağıdaki kod, `hToken` bir Windows belirtecini temsil eden bu çağrıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="219ff-117">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. <span data-ttu-id="219ff-118"><xref:System.Security.Principal.WindowsImpersonationContext>Aşağıdaki kodda gösterildiği gibi, sınıfının yeni bir örneğini oluşturarak ve onu başlatılmış sınıfın yöntemiyle başlatarak kimliğe bürünme işlemini başlatın <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="219ff-118">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. <span data-ttu-id="219ff-119">Artık taklit etmeniz gerekmiyorsa, <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> aşağıdaki kodda gösterildiği gibi, kimliğe bürünme özelliğini dönüştürmek için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="219ff-119">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="219ff-120">Güvenilen kod zaten <xref:System.Security.Principal.WindowsPrincipal> iş parçacığına bir nesne iliştirmişse, bir hesap belirteci almaz, **kimliğe bürünme**örnek yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="219ff-120">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="219ff-121">Bu, yalnızca iş parçacığındaki **WindowsPrincipal** nesnesi, işlemin Şu anda yürütülmekte olduğu bir kullanıcıyı temsil ettiğinde yararlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="219ff-121">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="219ff-122">Örneğin, Windows kimlik doğrulaması açık ve kimliğe bürünme kapalı ASP.NET kullanarak bu durumla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="219ff-122">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="219ff-123">Bu durumda, işlem Internet Information Services (IIS) ' de yapılandırılmış bir hesap altında çalışıyor, geçerli sorumlusu ise sayfaya erişen Windows kullanıcısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="219ff-123">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="219ff-124">**Kimliğe bürünme** ve **geri alma** seçeneklerinin **Principal** <xref:System.Security.Principal.IPrincipal> geçerli çağrı bağlamıyla ilişkili asıl nesne () değişikliklerini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="219ff-124">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="219ff-125">Bunun yerine, kimliğe bürünme ve geri döndürme geçerli işletim sistemi işlemiyle ilişkili belirteci değiştirir.</span><span class="sxs-lookup"><span data-stu-id="219ff-125">Rather, impersonation and reverting change the token associated with the current operating system process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="219ff-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="219ff-126">See also</span></span>

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [<span data-ttu-id="219ff-127">Asıl ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="219ff-127">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="219ff-128">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="219ff-128">Interoperating with Unmanaged Code</span></span>](../../framework/interop/index.md)
- [<span data-ttu-id="219ff-129">ASP.NET Core güvenliği</span><span class="sxs-lookup"><span data-stu-id="219ff-129">ASP.NET Core Security</span></span>](/aspnet/core/security/)
