---
description: 'Daha fazla bilgi edinin: kimliğe bürünme ve geri döndürme'
title: Kimliğe Bürünme ve Geri Alma
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
ms.openlocfilehash: f3e536f87ef5aa09cd727fe9674c7a40f3a09150
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685016"
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="3bfd5-103">Kimliğe Bürünme ve Geri Alma</span><span class="sxs-lookup"><span data-stu-id="3bfd5-103">Impersonating and Reverting</span></span>

> [!NOTE]
> <span data-ttu-id="3bfd5-104">Bu makale Windows için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-104">This article applies to Windows.</span></span>
>
> <span data-ttu-id="3bfd5-105">ASP.NET Core hakkında bilgi için bkz. [ASP.NET Core Security](/aspnet/core/security/).</span><span class="sxs-lookup"><span data-stu-id="3bfd5-105">For information about ASP.NET Core, see [ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="3bfd5-106">Bazen bir Windows hesabının kimliğine bürünmek için bir Windows hesabı belirteci edinmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-106">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="3bfd5-107">Örneğin, ASP.NET tabanlı uygulamanızın farklı zamanlarda birkaç kullanıcı adına işlem yapması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-107">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="3bfd5-108">Uygulamanız Internet Information Services (IIS) tarafından bir yöneticiyi temsil eden bir belirteci kabul edebilir, bu kullanıcının kimliğine bürünerek bir işlem gerçekleştirir ve önceki kimliğe geri dönebilir.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-108">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="3bfd5-109">Daha sonra, IIS 'den daha az haklara sahip bir kullanıcıyı temsil eden bir belirteç kabul edebilir, bazı işlemler gerçekleştirebilir ve yeniden döndürülür.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-109">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="3bfd5-110">Uygulamanızın IIS tarafından geçerli iş parçacığına eklenmemiş bir Windows hesabı kimliğine bürünmesi gereken durumlarda, bu hesabın belirtecini alıp hesabı etkinleştirmek için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-110">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="3bfd5-111">Bunu aşağıdaki görevleri gerçekleştirerek yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3bfd5-111">You can do this by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="3bfd5-112">Yönetilmeyen **LogonUser** yöntemine bir çağrı yaparak belirli bir kullanıcı için hesap belirteci alın.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-112">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="3bfd5-113">Bu yöntem .NET temel sınıf kitaplığında değildir, ancak yönetilmeyen **advapi32.dll** bulunur.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-113">This method is not in the .NET base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="3bfd5-114">Yönetilmeyen koddaki yöntemlere erişim gelişmiş bir işlemdir ve bu tartışmanın kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-114">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="3bfd5-115">Daha fazla bilgi için bkz. [yönetilmeyen kodla birlikte çalışma](../../framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="3bfd5-115">For more information, see [Interoperating with Unmanaged Code](../../framework/interop/index.md).</span></span> <span data-ttu-id="3bfd5-116">**LogonUser** yöntemi ve **advapi32.dll** hakkında daha fazla bilgi için Platform SDK belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-116">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2. <span data-ttu-id="3bfd5-117">, Belirteci geçirerek **WindowsIdentity** sınıfının yeni bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-117">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="3bfd5-118">Aşağıdaki kod, `hToken` bir Windows belirtecini temsil eden bu çağrıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-118">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. <span data-ttu-id="3bfd5-119"><xref:System.Security.Principal.WindowsImpersonationContext>Aşağıdaki kodda gösterildiği gibi, sınıfının yeni bir örneğini oluşturarak ve onu başlatılmış sınıfın yöntemiyle başlatarak kimliğe bürünme işlemini başlatın <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3bfd5-119">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. <span data-ttu-id="3bfd5-120">Artık taklit etmeniz gerekmiyorsa, <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> aşağıdaki kodda gösterildiği gibi, kimliğe bürünme özelliğini dönüştürmek için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-120">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="3bfd5-121">Güvenilen kod zaten <xref:System.Security.Principal.WindowsPrincipal> iş parçacığına bir nesne iliştirmişse, bir hesap belirteci almaz, **kimliğe bürünme** örnek yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-121">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="3bfd5-122">Bu, yalnızca iş parçacığındaki **WindowsPrincipal** nesnesi, işlemin Şu anda yürütülmekte olduğu bir kullanıcıyı temsil ettiğinde yararlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-122">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="3bfd5-123">Örneğin, Windows kimlik doğrulaması açık ve kimliğe bürünme kapalı ASP.NET kullanarak bu durumla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-123">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="3bfd5-124">Bu durumda, işlem Internet Information Services (IIS) ' de yapılandırılmış bir hesap altında çalışıyor, geçerli sorumlusu ise sayfaya erişen Windows kullanıcısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-124">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="3bfd5-125">**Kimliğe bürünme** ve **geri alma** seçeneklerinin  <xref:System.Security.Principal.IPrincipal> geçerli çağrı bağlamıyla ilişkili asıl nesne () değişikliklerini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-125">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="3bfd5-126">Bunun yerine, kimliğe bürünme ve geri döndürme geçerli işletim sistemi işlemiyle ilişkili belirteci değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-126">Rather, impersonation and reverting change the token associated with the current operating system process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bfd5-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bfd5-127">See also</span></span>

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [<span data-ttu-id="3bfd5-128">Asıl ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="3bfd5-128">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="3bfd5-129">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="3bfd5-129">Interoperating with Unmanaged Code</span></span>](../../framework/interop/index.md)
- [<span data-ttu-id="3bfd5-130">ASP.NET Core güvenliği</span><span class="sxs-lookup"><span data-stu-id="3bfd5-130">ASP.NET Core Security</span></span>](/aspnet/core/security/)
