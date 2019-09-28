---
title: 'Nasıl yapılır: GenericPrincipal ve GenericIdentity Nesneleri Oluşturma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1f768242bffe619051779f87e950138ae9fcec6c
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353180"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="26170-102">Nasıl yapılır: GenericPrincipal ve GenericIdentity Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="26170-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>

<span data-ttu-id="26170-103">Bir Windows etki alanından bağımsız olarak bulunan bir yetkilendirme şeması oluşturmak için <xref:System.Security.Principal.GenericIdentity> sınıfını <xref:System.Security.Principal.GenericPrincipal> sınıfıyla birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26170-103">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>

### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="26170-104">GenericPrincipal nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="26170-104">To create a GenericPrincipal object</span></span>

1. <span data-ttu-id="26170-105">Identity sınıfının yeni bir örneğini oluşturun ve onu tutmak istediğiniz adla başlatın.</span><span class="sxs-lookup"><span data-stu-id="26170-105">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="26170-106">Aşağıdaki kod, yeni bir **GenericIdentity** nesnesi oluşturur ve `MyUser` adıyla başlatır.</span><span class="sxs-lookup"><span data-stu-id="26170-106">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. <span data-ttu-id="26170-107">**GenericPrincipal** sınıfının yeni bir örneğini oluşturun ve daha önce oluşturulan **GenericIdentity** nesnesiyle ve bu sorumluya ilişkilendirilmesini istediğiniz rolleri temsil eden dizeler dizisiyle başlatın.</span><span class="sxs-lookup"><span data-stu-id="26170-107">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="26170-108">Aşağıdaki kod örneği, bir yönetici rolünü ve Kullanıcı rolünü temsil eden dizelerin dizisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="26170-108">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="26170-109">**GenericPrincipal** daha sonra önceki **GenericIdentity** ve String dizisi ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="26170-109">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. <span data-ttu-id="26170-110">Geçerli iş parçacığına asıl eklemek için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="26170-110">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="26170-111">Bu, sorumlunun birkaç kez doğrulanması gerektiği durumlarda, uygulamanızda çalışan diğer kod tarafından doğrulanması veya <xref:System.Security.Permissions.PrincipalPermission> nesnesi tarafından doğrulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="26170-111">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="26170-112">Principal nesnesinde, iş parçacığına iliştirmeden rol tabanlı doğrulama işlemi gerçekleştirmeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26170-112">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="26170-113">Daha fazla bilgi için bkz. [Principal nesnesini değiştirme](../../../docs/standard/security/replacing-a-principal-object.md).</span><span class="sxs-lookup"><span data-stu-id="26170-113">For more information, see [Replacing a Principal Object](../../../docs/standard/security/replacing-a-principal-object.md).</span></span>

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a><span data-ttu-id="26170-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="26170-114">Example</span></span>

<span data-ttu-id="26170-115">Aşağıdaki kod örneği, **GenericPrincipal** ve **GenericIdentity**'nin bir örneğinin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="26170-115">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="26170-116">Bu kod, bu nesnelerin değerlerini konsola görüntüler.</span><span class="sxs-lookup"><span data-stu-id="26170-116">This code displays the values of these objects to the console.</span></span>

```vb
Imports System
Imports System.Security.Principal
Imports System.Threading

Public Class Class1

    Public Shared Sub Main()
        ' Create generic identity.
        Dim myIdentity As New GenericIdentity("MyIdentity")

        ' Create generic principal.
        Dim myStringArray As String() =  {"Manager", "Teller"}
        Dim myPrincipal As New GenericPrincipal(myIdentity, myStringArray)

        ' Attach the principal to the current thread.
        ' This is not required unless repeated validation must occur,
        ' other code in your application must validate, or the
        ' PrincipalPermission object is used.
        Thread.CurrentPrincipal = myPrincipal

        ' Print values to the console.
        Dim name As String = myPrincipal.Identity.Name
        Dim auth As Boolean = myPrincipal.Identity.IsAuthenticated
        Dim isInRole As Boolean = myPrincipal.IsInRole("Manager")

        Console.WriteLine("The name is: {0}", name)
        Console.WriteLine("The isAuthenticated is: {0}", auth)
        Console.WriteLine("Is this a Manager? {0}", isInRole)

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
    GenericIdentity myIdentity = new GenericIdentity("MyIdentity");

    // Create generic principal.
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal =
        new GenericPrincipal(myIdentity, myStringArray);

    // Attach the principal to the current thread.
    // This is not required unless repeated validation must occur,
    // other code in your application must validate, or the
    // PrincipalPermission object is used.
    Thread.CurrentPrincipal = myPrincipal;

    // Print values to the console.
    String name =  myPrincipal.Identity.Name;
    bool auth =  myPrincipal.Identity.IsAuthenticated;
    bool isInRole =  myPrincipal.IsInRole("Manager");

    Console.WriteLine("The name is: {0}", name);
    Console.WriteLine("The isAuthenticated is: {0}", auth);
    Console.WriteLine("Is this a Manager? {0}", isInRole);

    return 0;
    }
}
```

<span data-ttu-id="26170-117">Yürütüldüğünde, uygulama aşağıdakine benzer bir çıktı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="26170-117">When executed, the application displays output similar to the following.</span></span>

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a><span data-ttu-id="26170-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26170-118">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [<span data-ttu-id="26170-119">Sorumlu Nesnesini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="26170-119">Replacing a Principal Object</span></span>](../../../docs/standard/security/replacing-a-principal-object.md)
- [<span data-ttu-id="26170-120">Sorumlu ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="26170-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
