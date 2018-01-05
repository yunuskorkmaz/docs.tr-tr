---
title: "Nasıl yapılır: GenericPrincipal ve GenericIdentity Nesneleri Oluşturma"
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
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b10029c8b290ffaaa4a858fe3e5a6315031f1bab
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="79105-102">Nasıl yapılır: GenericPrincipal ve GenericIdentity Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="79105-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>
<span data-ttu-id="79105-103">Kullanabileceğiniz <xref:System.Security.Principal.GenericIdentity> sınıfı ile birlikte <xref:System.Security.Principal.GenericPrincipal> mevcut bir Yetkilendirme düzeni bir Windows etki alanının bağımsız oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="79105-103">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>  
  
### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="79105-104">GenericPrincipal nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="79105-104">To create a GenericPrincipal object</span></span>  
  
1.  <span data-ttu-id="79105-105">Kimlik sınıfının yeni bir örneğini oluşturun ve tutmak istediğiniz adla başlatın.</span><span class="sxs-lookup"><span data-stu-id="79105-105">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="79105-106">Aşağıdaki kod yeni bir oluşturur **Genericıdentity** nesne ve adıyla başlatır `MyUser`.</span><span class="sxs-lookup"><span data-stu-id="79105-106">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>  
  
    ```vb  
    Dim MyIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity MyIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  <span data-ttu-id="79105-107">Yeni bir örneğini oluşturmak **GenericPrincipal** sınıfı ve önceden oluşturulmuş başlatma **Genericıdentity** nesne ve ilişkili istediğiniz rolleri temsil eden bir dize dizisi Bu sorumlu.</span><span class="sxs-lookup"><span data-stu-id="79105-107">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="79105-108">Aşağıdaki kod örneği, bir yönetici rolü ve bir kullanıcı rolü temsil eden bir dize dizisi belirtir.</span><span class="sxs-lookup"><span data-stu-id="79105-108">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="79105-109">**GenericPrincipal** sonra önceki ile başlatılmış **Genericıdentity** ve dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="79105-109">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>  
  
    ```vb  
    Dim MyStringArray As String() = {"Manager", "Teller"}  
    DIm MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
    ```  
  
    ```csharp  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal = new GenericPrincipal(MyIdentity, MyStringArray);  
    ```  
  
3.  <span data-ttu-id="79105-110">Geçerli iş parçacığına asıl eklemek için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="79105-110">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="79105-111">Bu, burada birkaç kez asıl doğrulanması gerekir, uygulamanızı çalıştıran başka bir kod tarafından doğrulanmalıdır veya tarafından doğrulanmalıdır durumlarda faydalıdır bir <xref:System.Security.Permissions.PrincipalPermission> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="79105-111">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="79105-112">Rol tabanlı doğrulama hala asıl nesne üzerinde iş parçacığına eklemeden de gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79105-112">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="79105-113">Daha fazla bilgi için bkz: [asıl nesneyi değiştirme](../../../docs/standard/security/replacing-a-principal-object.md).</span><span class="sxs-lookup"><span data-stu-id="79105-113">For more information, see [Replacing a Principal Object](../../../docs/standard/security/replacing-a-principal-object.md).</span></span>  
  
    ```vb  
    Thread.CurrentPrincipal = MyPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = MyPrincipal;  
    ```  
  
## <a name="example"></a><span data-ttu-id="79105-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="79105-114">Example</span></span>  
 <span data-ttu-id="79105-115">Aşağıdaki kod örneğinde bir örneğini oluşturmak nasıl gösteren bir **GenericPrincipal** ve **Genericıdentity**.</span><span class="sxs-lookup"><span data-stu-id="79105-115">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="79105-116">Bu kod, bu nesnelerin değerlerini konsola görüntüler.</span><span class="sxs-lookup"><span data-stu-id="79105-116">This code displays the values of these objects to the console.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Principal  
Imports System.Threading  
  
Public Class Class1  
  
    Public Shared Sub Main()  
        ' Create generic identity.  
        Dim MyIdentity As New GenericIdentity("MyIdentity")  
  
        ' Create generic principal.  
        Dim MyStringArray As String() =  {"Manager", "Teller"}  
        Dim MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
  
        ' Attach the principal to the current thread.  
        ' This is not required unless repeated validation must occur,  
        ' other code in your application must validate, or the   
        ' PrincipalPermisson object is used.   
        Thread.CurrentPrincipal = MyPrincipal  
  
        ' Print values to the console.  
        Dim Name As String = MyPrincipal.Identity.Name  
        Dim Auth As Boolean = MyPrincipal.Identity.IsAuthenticated  
        Dim IsInRole As Boolean = MyPrincipal.IsInRole("Manager")  
  
        Console.WriteLine("The Name is: {0}", Name)  
        Console.WriteLine("The IsAuthenticated is: {0}", Auth)  
        Console.WriteLine("Is this a Manager? {0}", IsInRole)  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Security.Principal;  
using System.Threading;  
  
public class Class1  
{  
    public static int Main(string[] args)  
    {  
    // Create generic identity.  
    GenericIdentity MyIdentity = new GenericIdentity("MyIdentity");  
  
    // Create generic principal.  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal =   
        new GenericPrincipal(MyIdentity, MyStringArray);  
  
    // Attach the principal to the current thread.  
    // This is not required unless repeated validation must occur,  
    // other code in your application must validate, or the   
    // PrincipalPermisson object is used.   
    Thread.CurrentPrincipal = MyPrincipal;  
  
    // Print values to the console.  
    String Name =  MyPrincipal.Identity.Name;  
    bool Auth =  MyPrincipal.Identity.IsAuthenticated;   
    bool IsInRole =  MyPrincipal.IsInRole("Manager");  
  
    Console.WriteLine("The Name is: {0}", Name);  
    Console.WriteLine("The IsAuthenticated is: {0}", Auth);  
    Console.WriteLine("Is this a Manager? {0}", IsInRole);  
  
    return 0;  
    }  
}  
```  
  
 <span data-ttu-id="79105-117">Uygulama çalıştırıldığında, aşağıdakine benzer bir çıktı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="79105-117">When executed, the application displays output similar to the following.</span></span>  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## <a name="see-also"></a><span data-ttu-id="79105-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79105-118">See Also</span></span>  
 <xref:System.Security.Principal.GenericIdentity>  
 <xref:System.Security.Principal.GenericPrincipal>  
 <xref:System.Security.Permissions.PrincipalPermission>  
 [<span data-ttu-id="79105-119">Sorumlu Nesnesini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="79105-119">Replacing a Principal Object</span></span>](../../../docs/standard/security/replacing-a-principal-object.md)  
 [<span data-ttu-id="79105-120">Sorumlu ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="79105-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
