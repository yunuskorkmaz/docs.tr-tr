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
ms.openlocfilehash: 65fd078b6be9dbcdfc03e34285d70a6bfe42d87b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581784"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a>Nasıl yapılır: GenericPrincipal ve GenericIdentity Nesneleri Oluşturma
Kullanabileceğiniz <xref:System.Security.Principal.GenericIdentity> sınıfı ile birlikte <xref:System.Security.Principal.GenericPrincipal> mevcut bir Yetkilendirme düzeni bir Windows etki alanının bağımsız oluşturmasını sağlar.  
  
### <a name="to-create-a-genericprincipal-object"></a>GenericPrincipal nesnesi oluşturmak için  
  
1.  Kimlik sınıfının yeni bir örneğini oluşturun ve tutmak istediğiniz adla başlatın. Aşağıdaki kod yeni bir oluşturur **Genericıdentity** nesne ve adıyla başlatır `MyUser`.  
  
    ```vb  
    Dim MyIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity MyIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  Yeni bir örneğini oluşturmak **GenericPrincipal** sınıfı ve önceden oluşturulmuş başlatma **Genericıdentity** nesne ve ilişkili istediğiniz rolleri temsil eden bir dize dizisi Bu sorumlu. Aşağıdaki kod örneği, bir yönetici rolü ve bir kullanıcı rolü temsil eden bir dize dizisi belirtir. **GenericPrincipal** sonra önceki ile başlatılmış **Genericıdentity** ve dize dizisi.  
  
    ```vb  
    Dim MyStringArray As String() = {"Manager", "Teller"}  
    DIm MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
    ```  
  
    ```csharp  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal = new GenericPrincipal(MyIdentity, MyStringArray);  
    ```  
  
3.  Geçerli iş parçacığına asıl eklemek için aşağıdaki kodu kullanın. Bu, burada birkaç kez asıl doğrulanması gerekir, uygulamanızı çalıştıran başka bir kod tarafından doğrulanmalıdır veya tarafından doğrulanmalıdır durumlarda faydalıdır bir <xref:System.Security.Permissions.PrincipalPermission> nesnesi. Rol tabanlı doğrulama hala asıl nesne üzerinde iş parçacığına eklemeden de gerçekleştirebilirsiniz. Daha fazla bilgi için bkz: [asıl nesneyi değiştirme](../../../docs/standard/security/replacing-a-principal-object.md).  
  
    ```vb  
    Thread.CurrentPrincipal = MyPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = MyPrincipal;  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde bir örneğini oluşturmak nasıl gösteren bir **GenericPrincipal** ve **Genericıdentity**. Bu kod, bu nesnelerin değerlerini konsola görüntüler.  
  
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
  
 Uygulama çalıştırıldığında, aşağıdakine benzer bir çıktı görüntüler.  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Principal.GenericIdentity>  
 <xref:System.Security.Principal.GenericPrincipal>  
 <xref:System.Security.Permissions.PrincipalPermission>  
 [Sorumlu Nesnesini Değiştirme](../../../docs/standard/security/replacing-a-principal-object.md)  
 [Sorumlu ve Kimlik Nesneleri](../../../docs/standard/security/principal-and-identity-objects.md)
