---
title: 'Nasıl yapılır: WindowsPrincipal nesnesi oluşturma'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3960a7f87f8ac9a09da7222bd0f7a4a01afc4154
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583452"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Nasıl yapılır: WindowsPrincipal nesnesi oluşturma
Oluşturmanın iki yolu vardır. bir <xref:System.Security.Principal.WindowsPrincipal> nesne, rol tabanlı doğrulama gerçekleştirmeniz olup kod tekrar tekrar gerekir bağlı olarak veya yalnızca bir kez gerçekleştirmeniz gerekir.  
  
 Kod tekrar tekrar rol tabanlı doğrulama gerçekleştirmesi gerekiyorsa, aşağıdaki yordamlardan birini ilk daha az ek yük oluşturur. Kod gerektiğinde yalnızca bir kez oluşturabilir, rol tabanlı doğrulamaları yapmak bir <xref:System.Security.Principal.WindowsPrincipal> ikinci aşağıdaki yordamlardan birini kullanarak nesne.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>Yinelenen doğrulama için WindowsPrincipal nesnesi oluşturma  
  
1.  Çağrı <xref:System.AppDomain.SetPrincipalPolicy%2A> metodunda <xref:System.AppDomain> statik tarafından döndürülen nesne <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> yöntemi geçirme özelliği, bir <xref:System.Security.Principal.PrincipalPolicy> yeni ilke olmaması gerektiğini gösteren bir numaralandırma değeri. Desteklenen değerler şunlardır: <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, ve <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>. Aşağıdaki kod, bu yöntem çağrısının gösterir.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  İlkeyle ayarlama, statik <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> kapsülleyen geçerli Windows kullanıcısının asıl almak için özellik. Özelliği döndürme türü olduğundan <xref:System.Security.Principal.IPrincipal>, sonucu dönüştürmelisiniz bir <xref:System.Security.Principal.WindowsPrincipal> türü. Aşağıdaki kodu yeni başlatır <xref:System.Security.Principal.WindowsPrincipal> değerine geçerli iş parçacığıyla ilişkilendirilmiş sorumlusu nesnesi.  
  
    ```csharp  
    WindowsPrincipal myPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  Asıl nesne oluşturulduğunda bunu doğrulamak için birkaç yöntemden birini kullanabilirsiniz.  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>Tek bir doğrulama için WindowsPrincipal nesnesi oluşturma  
  
1.  Yeni bir başlatma <xref:System.Security.Principal.WindowsIdentity> statik çağırarak <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> yöntemi geçerli Windows hesabını sorgular ve bu hesabı hakkında bilgi yeni oluşturulan kimlik nesnesi içine yerleştirir. Aşağıdaki kod yeni bir oluşturur <xref:System.Security.Principal.WindowsIdentity> nesne ve kimliği doğrulanmış geçerli kullanıcının başlatır.  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  Yeni bir <xref:System.Security.Principal.WindowsPrincipal> nesne ve değerini geçirin <xref:System.Security.Principal.WindowsIdentity> önceki adımda oluşturulan nesne.  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3.  Asıl nesne oluşturulduğunda bunu doğrulamak için birkaç yöntemden birini kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorumlu ve Kimlik Nesneleri](../../../docs/standard/security/principal-and-identity-objects.md)
