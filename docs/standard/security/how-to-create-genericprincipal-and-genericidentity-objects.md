---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: GenericPrincipal ve GenericIdentity nesneleri oluşturma'
title: 'Nasıl yapılır: GenericPrincipal ve GenericIdentity Nesneleri Oluşturma'
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
ms.openlocfilehash: 8c77a9afec7bd166a71abb6af19d8766b02d0523
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685224"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="a7dfe-103">Nasıl yapılır: GenericPrincipal ve GenericIdentity Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7dfe-103">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>

> [!NOTE]
> <span data-ttu-id="a7dfe-104">Bu makale Windows için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a7dfe-104">This article applies to Windows.</span></span>
>
> <span data-ttu-id="a7dfe-105">ASP.NET Core hakkında bilgi için bkz. [ASP.NET Core güvenliğine genel bakış](/aspnet/core/security/).</span><span class="sxs-lookup"><span data-stu-id="a7dfe-105">For information about ASP.NET Core, see [Overview of ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="a7dfe-106"><xref:System.Security.Principal.GenericIdentity> <xref:System.Security.Principal.GenericPrincipal> Bir Windows etki alanından bağımsız olarak bulunan bir yetkilendirme şeması oluşturmak için sınıfını sınıfıyla birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7dfe-106">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>

### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="a7dfe-107">GenericPrincipal nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a7dfe-107">To create a GenericPrincipal object</span></span>

1. <span data-ttu-id="a7dfe-108">Identity sınıfının yeni bir örneğini oluşturun ve onu tutmak istediğiniz adla başlatın.</span><span class="sxs-lookup"><span data-stu-id="a7dfe-108">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="a7dfe-109">Aşağıdaki kod, yeni bir **GenericIdentity** nesnesi oluşturur ve adı ile başlatır `MyUser` .</span><span class="sxs-lookup"><span data-stu-id="a7dfe-109">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. <span data-ttu-id="a7dfe-110">**GenericPrincipal** sınıfının yeni bir örneğini oluşturun ve daha önce oluşturulan **GenericIdentity** nesnesiyle ve bu sorumluya ilişkilendirilmesini istediğiniz rolleri temsil eden dizeler dizisiyle başlatın.</span><span class="sxs-lookup"><span data-stu-id="a7dfe-110">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="a7dfe-111">Aşağıdaki kod örneği, bir yönetici rolünü ve Kullanıcı rolünü temsil eden dizelerin dizisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7dfe-111">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="a7dfe-112">**GenericPrincipal** daha sonra önceki **GenericIdentity** ve String dizisi ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="a7dfe-112">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. <span data-ttu-id="a7dfe-113">Geçerli iş parçacığına asıl eklemek için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7dfe-113">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="a7dfe-114">Bu, sorumlunun birkaç kez doğrulanması gerektiği durumlarda faydalıdır, bu, uygulamanızda çalışan diğer kod tarafından doğrulanması veya bir nesne tarafından doğrulanması gerekir <xref:System.Security.Permissions.PrincipalPermission> .</span><span class="sxs-lookup"><span data-stu-id="a7dfe-114">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="a7dfe-115">Principal nesnesinde, iş parçacığına iliştirmeden rol tabanlı doğrulama işlemi gerçekleştirmeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7dfe-115">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="a7dfe-116">Daha fazla bilgi için bkz. [Principal nesnesini değiştirme](replacing-a-principal-object.md).</span><span class="sxs-lookup"><span data-stu-id="a7dfe-116">For more information, see [Replacing a Principal Object](replacing-a-principal-object.md).</span></span>

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a><span data-ttu-id="a7dfe-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7dfe-117">Example</span></span>

<span data-ttu-id="a7dfe-118">Aşağıdaki kod örneği, **GenericPrincipal** ve **GenericIdentity**'nin bir örneğinin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a7dfe-118">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="a7dfe-119">Bu kod, bu nesnelerin değerlerini konsola görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a7dfe-119">This code displays the values of these objects to the console.</span></span>

```vb
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

<span data-ttu-id="a7dfe-120">Yürütüldüğünde, uygulama aşağıdakine benzer bir çıktı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a7dfe-120">When executed, the application displays output similar to the following.</span></span>

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a><span data-ttu-id="a7dfe-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7dfe-121">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [<span data-ttu-id="a7dfe-122">Asıl Nesneyi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="a7dfe-122">Replacing a Principal Object</span></span>](replacing-a-principal-object.md)
- [<span data-ttu-id="a7dfe-123">Asıl ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="a7dfe-123">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
