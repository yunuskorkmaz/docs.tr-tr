---
title: 'Nasıl yapılır: WindowsPrincipal Nesnesi Oluşturma'
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET], creating a WindowsPrincipal object
- security [.NET], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
ms.openlocfilehash: 6cf7153250d2574783515ea53cf99709499d36f9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556212"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Nasıl yapılır: WindowsPrincipal Nesnesi Oluşturma

> [!NOTE]
> Bu makale Windows için geçerlidir.
>
> ASP.NET Core hakkında bilgi için bkz. [ASP.NET Core Security](/aspnet/core/security/).

<xref:System.Security.Principal.WindowsPrincipal>Kodun, tekrar tekrar rol tabanlı doğrulama yapıp gerçekleştirmeyeceğini veya yalnızca bir kez yerine getirmeniz gerektiğini bağlı olarak, bir nesne oluşturmanın iki yolu vardır.  
  
Kodun sürekli olarak rol tabanlı doğrulama yapması gerekiyorsa, aşağıdaki yordamların ilki daha az ek yük üretir. Kodun rol tabanlı doğrulamaları yalnızca bir kez yapması gerektiğinde, <xref:System.Security.Principal.WindowsPrincipal> Aşağıdaki yordamların ikincisini kullanarak bir nesne oluşturabilirsiniz.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>Yinelenen doğrulama için bir WindowsPrincipal nesnesi oluşturmak için  
  
1. <xref:System.AppDomain.SetPrincipalPolicy%2A> <xref:System.AppDomain> Static özelliği tarafından döndürülen nesnede yöntemini çağırın <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> , yöntemi, <xref:System.Security.Principal.PrincipalPolicy> yeni ilkenin ne olması gerektiğini belirten bir numaralandırma değeri geçirerek. Desteklenen değerler <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal> , <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> , ve <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal> . Aşağıdaki kod bu yöntem çağrısını gösterir.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. İlke kümesiyle, <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> geçerli Windows kullanıcısını kapsülleyen sorumluyu almak için static özelliğini kullanın. Özellik dönüş türü olduğundan <xref:System.Security.Principal.IPrincipal> , sonucu bir <xref:System.Security.Principal.WindowsPrincipal> türe atamalısınız. Aşağıdaki kod, <xref:System.Security.Principal.WindowsPrincipal> geçerli iş parçacığıyla ilişkili sorumlu değerine yeni bir nesnesi başlatır.  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. Asıl nesne oluşturulduğunda, doğrulamak için birkaç yöntemden birini kullanabilirsiniz.  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>Tek bir doğrulama için bir WindowsPrincipal nesnesi oluşturmak için  
  
1. <xref:System.Security.Principal.WindowsIdentity> <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> Geçerli Windows hesabını sorgulayan ve bu hesapla ilgili bilgileri yeni oluşturulan kimlik nesnesine yerleştiren statik yöntemini çağırarak yeni bir nesne başlatın. Aşağıdaki kod yeni bir nesne oluşturur <xref:System.Security.Principal.WindowsIdentity> ve bunu geçerli kimliği doğrulanmış kullanıcı için başlatır.  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. Yeni bir <xref:System.Security.Principal.WindowsPrincipal> nesne oluşturun ve <xref:System.Security.Principal.WindowsIdentity> önceki adımda oluşturulan nesnenin değerini geçirin.  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. Asıl nesne oluşturulduğunda, doğrulamak için birkaç yöntemden birini kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Asıl ve Kimlik Nesneleri](principal-and-identity-objects.md)
- [ASP.NET Core güvenliği](/aspnet/core/security/)
