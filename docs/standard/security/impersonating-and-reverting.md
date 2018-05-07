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
ms.openlocfilehash: 40fef0ccbdf73580c5662fc76ed4335e587b9fbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="impersonating-and-reverting"></a>Kimliğe Bürünme ve Geri Alma
Bazen bir Windows hesabı kimliğine bürünmek üzere bir Windows hesabı belirteci edinmek gerekebilir. Örneğin, ASP.NET tabanlı uygulamanız farklı zamanlarda birkaç kullanıcı adına hareket gerekebilir. Uygulamanız yönetici Internet Information Services (IIS) temsil eden bir belirteci kabul, o kullanıcının kimliğine bürün, bir işlem gerçekleştirmek ve önceki kimliğine geri dönülemiyor. Ardından, daha az haklarına sahip bir kullanıcı temsil eden IIS uygulamasından bir belirteç kabul, başka bir işlem gerçekleştirmek ve yeniden geri.  
  
 Burada, uygulamanızın geçerli iş parçacığına IIS tarafından bağlı olmayan bir Windows hesabı bürünmelidir durumlarda, bu hesabın belirtecini almak ve hesabını etkinleştirmek için kullanın. Aşağıdaki görevleri gerçekleştirerek bunu yapabilirsiniz:  
  
1.  Yönetilmeyen bir çağrı yaparak belirli bir kullanıcı için bir hesap belirteci almak **LogonUser** yöntemi. Bu yöntem .NET Framework temel sınıf kitaplığı'nda değildir, ancak bulunduğu yönetilmeyen olarak **advapi32.dll**. Yönetilmeyen kod yöntemlerinde erişme İleri düzey bir işlemdir ve bu tartışma kapsamı dışındadır. Daha fazla bilgi için bkz: [yönetilmeyen kod ile birlikte çalışma](../../../docs/framework/interop/index.md). Hakkında daha fazla bilgi için **LogonUser** yöntemi ve **advapi32.dll**, Platform SDK belgelerine bakın.  
  
2.  Yeni bir örneğini oluşturmak **WindowsIdentity** sınıfı, belirteç geçirme. Aşağıdaki kod bu çağrıyı gösterir nerede `hToken` Windows belirteci temsil eder.  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  Kimliğe bürünme yeni bir örneğini oluşturarak başlayın <xref:System.Security.Principal.WindowsImpersonationContext> sınıfı ve onunla başlatma <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> başlatılmış sınıfının aşağıdaki kodda gösterildiği gibi yöntemi.  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  Artık kimliğine bürünmek gerektiğinde, çağrı <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> aşağıdaki kodda gösterildiği gibi kimliğe bürünme dönmek yöntemi.  
  
    ```csharp  
    MyImpersonation.Undo();  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 Kodu zaten eklenmiş güvenilen bir <xref:System.Security.Principal.WindowsPrincipal> nesne için iş parçacığı, örnek yöntemi çağırabilirsiniz **bürünme**, bir hesap belirteci olmaz. Bu yalnızca ne zaman yararlı olduğunu unutmayın **WindowsPrincipal** iş parçacığı nesnesinde altında işlemi şu anda yürütülmekte olan bir başka bir kullanıcı temsil eder. Örneğin, ASP.NET açık Windows kimlik doğrulaması ve kimliğe bürünme özelliğini devre dışı kullanarak bu durum karşılaşabilirsiniz. Bu durumda, işlem sayfaya erişimi Windows kullanıcısı geçerli sorumlu temsil ederken, Internet Information Services (IIS) yapılandırılmış bir hesap altında çalışıyor.  
  
 Tipleri unutmayın **bürünme** ya da **geri** değişiklikleri **asıl** nesne (<xref:System.Security.Principal.IPrincipal>) geçerli çağrı bağlamla ilişkili. Bunun yerine, kimliğe bürünme ve geri döndürülüyor değişiklik belirteci geçerli işletim sistemi işlemle ilişkili...  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Principal.WindowsIdentity>  
 <xref:System.Security.Principal.WindowsImpersonationContext>  
 [Sorumlu ve Kimlik Nesneleri](../../../docs/standard/security/principal-and-identity-objects.md)  
 [Yönetilmeyen Kod ile Birlikte Çalışma](../../../docs/framework/interop/index.md)
