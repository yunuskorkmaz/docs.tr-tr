---
title: Kimliğe Bürünme ve Geri Alma
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
ms.openlocfilehash: 7eecc7d6cb3fa4cc1c1bd971d36f9d3ca47a7144
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555688"
---
# <a name="impersonating-and-reverting"></a>Kimliğe Bürünme ve Geri Alma

> [!NOTE]
> Bu makale Windows için geçerlidir.
>
> ASP.NET Core hakkında bilgi için bkz. [ASP.NET Core Security](/aspnet/core/security/).

Bazen bir Windows hesabının kimliğine bürünmek için bir Windows hesabı belirteci edinmeniz gerekebilir. Örneğin, ASP.NET tabanlı uygulamanızın farklı zamanlarda birkaç kullanıcı adına işlem yapması gerekebilir. Uygulamanız Internet Information Services (IIS) tarafından bir yöneticiyi temsil eden bir belirteci kabul edebilir, bu kullanıcının kimliğine bürünerek bir işlem gerçekleştirir ve önceki kimliğe geri dönebilir. Daha sonra, IIS 'den daha az haklara sahip bir kullanıcıyı temsil eden bir belirteç kabul edebilir, bazı işlemler gerçekleştirebilir ve yeniden döndürülür.  
  
 Uygulamanızın IIS tarafından geçerli iş parçacığına eklenmemiş bir Windows hesabı kimliğine bürünmesi gereken durumlarda, bu hesabın belirtecini alıp hesabı etkinleştirmek için kullanmanız gerekir. Bunu aşağıdaki görevleri gerçekleştirerek yapabilirsiniz:  
  
1. Yönetilmeyen **LogonUser** yöntemine bir çağrı yaparak belirli bir kullanıcı için hesap belirteci alın. Bu yöntem .NET temel sınıf kitaplığında değildir, ancak yönetilmeyen **advapi32.dll**bulunur. Yönetilmeyen koddaki yöntemlere erişim gelişmiş bir işlemdir ve bu tartışmanın kapsamı dışındadır. Daha fazla bilgi için bkz. [yönetilmeyen kodla birlikte çalışma](../../framework/interop/index.md). **LogonUser** yöntemi ve **advapi32.dll**hakkında daha fazla bilgi için Platform SDK belgelerine bakın.  
  
2. , Belirteci geçirerek **WindowsIdentity** sınıfının yeni bir örneğini oluşturun. Aşağıdaki kod, `hToken` bir Windows belirtecini temsil eden bu çağrıyı gösterir.  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. <xref:System.Security.Principal.WindowsImpersonationContext>Aşağıdaki kodda gösterildiği gibi, sınıfının yeni bir örneğini oluşturarak ve onu başlatılmış sınıfın yöntemiyle başlatarak kimliğe bürünme işlemini başlatın <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> .  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. Artık taklit etmeniz gerekmiyorsa, <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> aşağıdaki kodda gösterildiği gibi, kimliğe bürünme özelliğini dönüştürmek için yöntemini çağırın.  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 Güvenilen kod zaten <xref:System.Security.Principal.WindowsPrincipal> iş parçacığına bir nesne iliştirmişse, bir hesap belirteci almaz, **kimliğe bürünme**örnek yöntemini çağırabilirsiniz. Bu, yalnızca iş parçacığındaki **WindowsPrincipal** nesnesi, işlemin Şu anda yürütülmekte olduğu bir kullanıcıyı temsil ettiğinde yararlı olduğunu unutmayın. Örneğin, Windows kimlik doğrulaması açık ve kimliğe bürünme kapalı ASP.NET kullanarak bu durumla karşılaşabilirsiniz. Bu durumda, işlem Internet Information Services (IIS) ' de yapılandırılmış bir hesap altında çalışıyor, geçerli sorumlusu ise sayfaya erişen Windows kullanıcısını temsil eder.  
  
 **Kimliğe bürünme** ve **geri alma** seçeneklerinin **Principal** <xref:System.Security.Principal.IPrincipal> geçerli çağrı bağlamıyla ilişkili asıl nesne () değişikliklerini unutmayın. Bunun yerine, kimliğe bürünme ve geri döndürme geçerli işletim sistemi işlemiyle ilişkili belirteci değiştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [Asıl ve Kimlik Nesneleri](principal-and-identity-objects.md)
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../framework/interop/index.md)
- [ASP.NET Core güvenliği](/aspnet/core/security/)
