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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3bc5b4a9bef51ac1591bdeb21651cee624d552b2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45592977"
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="538cb-102">Kimliğe Bürünme ve Geri Alma</span><span class="sxs-lookup"><span data-stu-id="538cb-102">Impersonating and Reverting</span></span>
<span data-ttu-id="538cb-103">Bazen bir Windows hesabı kimliğine bürünmek üzere Windows hesabı belirteç edinme gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="538cb-103">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="538cb-104">Örneğin, ASP.NET tabanlı uygulamanız farklı zamanlarda birden çok kullanıcı adına hareket gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="538cb-104">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="538cb-105">Uygulamanızı yönetici Internet Information Services (IIS) temsil eden bir belirteci kabul edin, bu kullanıcının kimliğine bürün, bir işlemi gerçekleştirmek ve önceki kimliğine geri dönülemiyor.</span><span class="sxs-lookup"><span data-stu-id="538cb-105">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="538cb-106">Ardından, daha az haklarına sahip bir kullanıcıyı temsil eden IIS belirtecinden kabul, başka bir işlem gerçekleştirmek ve yeniden geri.</span><span class="sxs-lookup"><span data-stu-id="538cb-106">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="538cb-107">Geçerli iş parçacığı için IIS tarafından bağlı olmayan bir Windows hesabı, uygulamanız nerede bürünmelidir durumlarda, bu hesabın belirteç almalı ve hesabını etkinleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="538cb-107">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="538cb-108">Aşağıdaki görevleri gerçekleştirerek bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="538cb-108">You can do this by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="538cb-109">Belirli bir kullanıcı için bir hesap belirteci yönetilmeyen bir çağrı yaparak alma **LogonUser** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="538cb-109">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="538cb-110">Bu yöntem .NET Framework temel sınıf kitaplığı'nda değildir, ancak bulunan yönetilmeyen olarak **advapi32.dll**.</span><span class="sxs-lookup"><span data-stu-id="538cb-110">This method is not in the .NET Framework base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="538cb-111">Yönetilmeyen kod yöntemleri erişme, İleri düzey bir işlemdir ve bu tartışma kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="538cb-111">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="538cb-112">Daha fazla bilgi için [yönetilmeyen kod ile birlikte çalışma](../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="538cb-112">For more information, see [Interoperating with Unmanaged Code](../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="538cb-113">Hakkında daha fazla bilgi için **LogonUser** yöntemi ve **advapi32.dll**, Platform SDK belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="538cb-113">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2.  <span data-ttu-id="538cb-114">Yeni bir örneğini oluşturma **WindowsIdentity** belirtece geçirerek sınıfı.</span><span class="sxs-lookup"><span data-stu-id="538cb-114">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="538cb-115">Aşağıdaki kod, bu çağrıyı gösterir. burada `hToken` Windows belirteci temsil eder.</span><span class="sxs-lookup"><span data-stu-id="538cb-115">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  <span data-ttu-id="538cb-116">Kimliğe bürünme, yeni bir örneğini oluşturarak başlayın <xref:System.Security.Principal.WindowsImpersonationContext> sınıfı ve onunla başlatma <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> başlatılmış sınıfının, aşağıdaki kodda gösterildiği yöntemi.</span><span class="sxs-lookup"><span data-stu-id="538cb-116">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  <span data-ttu-id="538cb-117">Artık bürünülecek gerektiğinde, çağrı <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> kimliğe bürünme, aşağıdaki kodda gösterildiği şekilde geri dönmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="538cb-117">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    MyImpersonation.Undo();  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="538cb-118">Kodu zaten eklenmiş güvenilen bir <xref:System.Security.Principal.WindowsPrincipal> nesne iş parçacığı için örnek yöntemi çağırabilirsiniz **doğrulamasından**, bir hesap belirteci almaz.</span><span class="sxs-lookup"><span data-stu-id="538cb-118">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="538cb-119">Bu yalnızca ne zaman yararlı olduğuna dikkat edin **WindowsPrincipal** iş parçacığında nesnesini temsil eden görevli işlemin şu anda Yürütülüyor bir başka bir kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="538cb-119">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="538cb-120">Örneğin, Windows kimlik doğrulaması açık ve kapalı kimliğe bürünme ASP.NET kullanarak bu durumla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="538cb-120">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="538cb-121">Bu durumda, işlem geçerli sorumlu sayfa erişiyor Windows kullanıcı temsil ederken, Internet Information Services (IIS) içinde yapılandırılmış bir hesap altında çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="538cb-121">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="538cb-122">Diğerinden unutmayın **doğrulamasından** ya da **geri** değişiklikleri **asıl** nesne (<xref:System.Security.Principal.IPrincipal>) geçerli çağrı bağlamla ilişkili.</span><span class="sxs-lookup"><span data-stu-id="538cb-122">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="538cb-123">Bunun yerine, kimliğe bürünme ve geri alma değişikliği belirtecin geçerli işletim sistemi işlemle ilişkili...</span><span class="sxs-lookup"><span data-stu-id="538cb-123">Rather, impersonation and reverting change the token associated with the current operating system process..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="538cb-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="538cb-124">See also</span></span>

- <xref:System.Security.Principal.WindowsIdentity>  
- <xref:System.Security.Principal.WindowsImpersonationContext>  
- [<span data-ttu-id="538cb-125">Sorumlu ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="538cb-125">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)  
- [<span data-ttu-id="538cb-126">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="538cb-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
