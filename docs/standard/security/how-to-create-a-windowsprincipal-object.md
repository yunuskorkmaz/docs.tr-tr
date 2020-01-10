---
title: 'Nasıl yapılır: WindowsPrincipal Nesnesi Oluşturma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
ms.openlocfilehash: d409c0e9a2a6564e5fb16e4e2c72ab661ae2d5ce
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706168"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Nasıl yapılır: WindowsPrincipal Nesnesi Oluşturma
Kodun, tekrar tekrar rol tabanlı doğrulama yapıp gerçekleştirmeyeceğini veya yalnızca bir kez yerine getirmeniz gerektiğini bağlı olarak, <xref:System.Security.Principal.WindowsPrincipal> nesnesi oluşturmanın iki yolu vardır.  
  
 Kodun sürekli olarak rol tabanlı doğrulama yapması gerekiyorsa, aşağıdaki yordamların ilki daha az ek yük üretir. Kodun rol tabanlı doğrulamaları yalnızca bir kez yapması gerektiğinde, aşağıdaki yordamların saniyesini kullanarak bir <xref:System.Security.Principal.WindowsPrincipal> nesnesi oluşturabilirsiniz.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>Yinelenen doğrulama için bir WindowsPrincipal nesnesi oluşturmak için  
  
1. Statik <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.AppDomain> nesnesi üzerinde <xref:System.AppDomain.SetPrincipalPolicy%2A> yöntemi çağırın ve yöntemi, yeni ilkenin ne olması gerektiğini belirten bir <xref:System.Security.Principal.PrincipalPolicy> numaralandırma değeri geçirerek. Desteklenen değerler <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>ve <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>. Aşağıdaki kod bu yöntem çağrısını gösterir.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. İlke kümesiyle, geçerli Windows kullanıcısını kapsülleyen sorumluyu almak için statik <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> özelliğini kullanın. Özellik dönüş türü <xref:System.Security.Principal.IPrincipal>olduğundan, sonucu bir <xref:System.Security.Principal.WindowsPrincipal> türüne atamalısınız. Aşağıdaki kod, geçerli iş parçacığıyla ilişkili asıl değerin değerine yeni bir <xref:System.Security.Principal.WindowsPrincipal> nesnesi başlatır.  
  
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
  
1. Geçerli Windows hesabını sorgulayan ve bu hesapla ilgili bilgileri yeni oluşturulan kimlik nesnesine yerleştiren statik <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> yöntemini çağırarak yeni bir <xref:System.Security.Principal.WindowsIdentity> nesnesi başlatın. Aşağıdaki kod yeni bir <xref:System.Security.Principal.WindowsIdentity> nesnesi oluşturur ve onu geçerli kimliği doğrulanmış kullanıcıya başlatır.  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. Yeni bir <xref:System.Security.Principal.WindowsPrincipal> nesnesi oluşturun ve önceki adımda oluşturulan <xref:System.Security.Principal.WindowsIdentity> nesnesinin değerini geçirin.  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. Asıl nesne oluşturulduğunda, doğrulamak için birkaç yöntemden birini kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorumlu ve Kimlik Nesneleri](../../../docs/standard/security/principal-and-identity-objects.md)
