---
title: "Kimliğe Bürünme ve Geri Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 869b9aadfa236a39d9807062e61046922e382d13
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="f4e44-102">Kimliğe Bürünme ve Geri Alma</span><span class="sxs-lookup"><span data-stu-id="f4e44-102">Impersonating and Reverting</span></span>
<span data-ttu-id="f4e44-103">Bazen bir Windows hesabı kimliğine bürünmek üzere bir Windows hesabı belirteci edinmek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f4e44-103">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="f4e44-104">Örneğin, ASP.NET tabanlı uygulamanız farklı zamanlarda birkaç kullanıcı adına hareket gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f4e44-104">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="f4e44-105">Uygulamanız yönetici Internet Information Services (IIS) temsil eden bir belirteci kabul, o kullanıcının kimliğine bürün, bir işlem gerçekleştirmek ve önceki kimliğine geri dönülemiyor.</span><span class="sxs-lookup"><span data-stu-id="f4e44-105">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="f4e44-106">Ardından, daha az haklarına sahip bir kullanıcı temsil eden IIS uygulamasından bir belirteç kabul, başka bir işlem gerçekleştirmek ve yeniden geri.</span><span class="sxs-lookup"><span data-stu-id="f4e44-106">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="f4e44-107">Burada, uygulamanızın geçerli iş parçacığına IIS tarafından bağlı olmayan bir Windows hesabı bürünmelidir durumlarda, bu hesabın belirtecini almak ve hesabını etkinleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4e44-107">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="f4e44-108">Aşağıdaki görevleri gerçekleştirerek bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f4e44-108">You can do this by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="f4e44-109">Yönetilmeyen bir çağrı yaparak belirli bir kullanıcı için bir hesap belirteci almak **LogonUser** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f4e44-109">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="f4e44-110">Bu yöntem .NET Framework temel sınıf kitaplığı'nda değildir, ancak bulunduğu yönetilmeyen olarak **advapi32.dll**.</span><span class="sxs-lookup"><span data-stu-id="f4e44-110">This method is not in the .NET Framework base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="f4e44-111">Yönetilmeyen kod yöntemlerinde erişme İleri düzey bir işlemdir ve bu tartışma kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="f4e44-111">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="f4e44-112">Daha fazla bilgi için bkz: [yönetilmeyen kod ile birlikte çalışma](../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="f4e44-112">For more information, see [Interoperating with Unmanaged Code](../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="f4e44-113">Hakkında daha fazla bilgi için **LogonUser** yöntemi ve **advapi32.dll**, Platform SDK belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="f4e44-113">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2.  <span data-ttu-id="f4e44-114">Yeni bir örneğini oluşturmak **WindowsIdentity** sınıfı, belirteç geçirme.</span><span class="sxs-lookup"><span data-stu-id="f4e44-114">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="f4e44-115">Aşağıdaki kod bu çağrıyı gösterir nerede `hToken` Windows belirteci temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f4e44-115">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  <span data-ttu-id="f4e44-116">Kimliğe bürünme yeni bir örneğini oluşturarak başlayın <xref:System.Security.Principal.WindowsImpersonationContext> sınıfı ve onunla başlatma <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> başlatılmış sınıfının aşağıdaki kodda gösterildiği gibi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f4e44-116">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  <span data-ttu-id="f4e44-117">Artık kimliğine bürünmek gerektiğinde, çağrı <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> aşağıdaki kodda gösterildiği gibi kimliğe bürünme dönmek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f4e44-117">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    MyImpersonation.Undo();  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="f4e44-118">Kodu zaten eklenmiş güvenilen bir <xref:System.Security.Principal.WindowsPrincipal> nesne için iş parçacığı, örnek yöntemi çağırabilirsiniz **bürünme**, bir hesap belirteci olmaz.</span><span class="sxs-lookup"><span data-stu-id="f4e44-118">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="f4e44-119">Bu yalnızca ne zaman yararlı olduğunu unutmayın **WindowsPrincipal** iş parçacığı nesnesinde altında işlemi şu anda yürütülmekte olan bir başka bir kullanıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f4e44-119">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="f4e44-120">Örneğin, ASP.NET açık Windows kimlik doğrulaması ve kimliğe bürünme özelliğini devre dışı kullanarak bu durum karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4e44-120">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="f4e44-121">Bu durumda, işlem sayfaya erişimi Windows kullanıcısı geçerli sorumlu temsil ederken, Internet Information Services (IIS) yapılandırılmış bir hesap altında çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="f4e44-121">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="f4e44-122">Tipleri unutmayın **bürünme** ya da **geri** değişiklikleri **asıl** nesne (<xref:System.Security.Principal.IPrincipal>) geçerli çağrı bağlamla ilişkili.</span><span class="sxs-lookup"><span data-stu-id="f4e44-122">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="f4e44-123">Bunun yerine, kimliğe bürünme ve geri döndürülüyor değişiklik belirteci geçerli işletim sistemi işlemle ilişkili...</span><span class="sxs-lookup"><span data-stu-id="f4e44-123">Rather, impersonation and reverting change the token associated with the current operating system process..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4e44-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4e44-124">See Also</span></span>  
 <xref:System.Security.Principal.WindowsIdentity>  
 <xref:System.Security.Principal.WindowsImpersonationContext>  
 [<span data-ttu-id="f4e44-125">Sorumlu ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="f4e44-125">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)  
 [<span data-ttu-id="f4e44-126">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="f4e44-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
