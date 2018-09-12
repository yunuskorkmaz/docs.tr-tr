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
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514468"
---
# <a name="impersonating-and-reverting"></a>Kimliğe Bürünme ve Geri Alma
Bazen bir Windows hesabı kimliğine bürünmek üzere Windows hesabı belirteç edinme gerekebilir. Örneğin, ASP.NET tabanlı uygulamanız farklı zamanlarda birden çok kullanıcı adına hareket gerekebilir. Uygulamanızı yönetici Internet Information Services (IIS) temsil eden bir belirteci kabul edin, bu kullanıcının kimliğine bürün, bir işlemi gerçekleştirmek ve önceki kimliğine geri dönülemiyor. Ardından, daha az haklarına sahip bir kullanıcıyı temsil eden IIS belirtecinden kabul, başka bir işlem gerçekleştirmek ve yeniden geri.  
  
 Geçerli iş parçacığı için IIS tarafından bağlı olmayan bir Windows hesabı, uygulamanız nerede bürünmelidir durumlarda, bu hesabın belirteç almalı ve hesabını etkinleştirmek için kullanın. Aşağıdaki görevleri gerçekleştirerek bunu yapabilirsiniz:  
  
1.  Belirli bir kullanıcı için bir hesap belirteci yönetilmeyen bir çağrı yaparak alma **LogonUser** yöntemi. Bu yöntem .NET Framework temel sınıf kitaplığı'nda değildir, ancak bulunan yönetilmeyen olarak **advapi32.dll**. Yönetilmeyen kod yöntemleri erişme, İleri düzey bir işlemdir ve bu tartışma kapsamı dışındadır. Daha fazla bilgi için [yönetilmeyen kod ile birlikte çalışma](../../../docs/framework/interop/index.md). Hakkında daha fazla bilgi için **LogonUser** yöntemi ve **advapi32.dll**, Platform SDK belgelerine bakın.  
  
2.  Yeni bir örneğini oluşturma **WindowsIdentity** belirtece geçirerek sınıfı. Aşağıdaki kod, bu çağrıyı gösterir. burada `hToken` Windows belirteci temsil eder.  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  Kimliğe bürünme, yeni bir örneğini oluşturarak başlayın <xref:System.Security.Principal.WindowsImpersonationContext> sınıfı ve onunla başlatma <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> başlatılmış sınıfının, aşağıdaki kodda gösterildiği yöntemi.  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  Artık bürünülecek gerektiğinde, çağrı <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> kimliğe bürünme, aşağıdaki kodda gösterildiği şekilde geri dönmek için yöntemi.  
  
    ```csharp  
    MyImpersonation.Undo();  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 Kodu zaten eklenmiş güvenilen bir <xref:System.Security.Principal.WindowsPrincipal> nesne iş parçacığı için örnek yöntemi çağırabilirsiniz **doğrulamasından**, bir hesap belirteci almaz. Bu yalnızca ne zaman yararlı olduğuna dikkat edin **WindowsPrincipal** iş parçacığında nesnesini temsil eden görevli işlemin şu anda Yürütülüyor bir başka bir kullanıcı. Örneğin, Windows kimlik doğrulaması açık ve kapalı kimliğe bürünme ASP.NET kullanarak bu durumla karşılaşabilirsiniz. Bu durumda, işlem geçerli sorumlu sayfa erişiyor Windows kullanıcı temsil ederken, Internet Information Services (IIS) içinde yapılandırılmış bir hesap altında çalışıyor.  
  
 Diğerinden unutmayın **doğrulamasından** ya da **geri** değişiklikleri **asıl** nesne (<xref:System.Security.Principal.IPrincipal>) geçerli çağrı bağlamla ilişkili. Bunun yerine, kimliğe bürünme ve geri alma değişikliği belirtecin geçerli işletim sistemi işlemle ilişkili...  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Principal.WindowsIdentity>  
- <xref:System.Security.Principal.WindowsImpersonationContext>  
- [Sorumlu ve Kimlik Nesneleri](../../../docs/standard/security/principal-and-identity-objects.md)  
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../docs/framework/interop/index.md)
