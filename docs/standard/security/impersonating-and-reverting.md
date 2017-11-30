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
ms.openlocfilehash: 4d1bd053cacc677ca66fc2e2a9e14620e1d3a8b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Asıl ve kimlik nesneleri](../../../docs/standard/security/principal-and-identity-objects.md)  
 [Yönetilmeyen kod ile birlikte çalışma](../../../docs/framework/interop/index.md)
