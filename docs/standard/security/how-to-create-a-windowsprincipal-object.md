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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f77d86e2ade841b715fc4bea8350d4e043bcb91b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581797"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Nasıl yapılır: WindowsPrincipal Nesnesi Oluşturma
Oluşturmanın iki yolu vardır bir <xref:System.Security.Principal.WindowsPrincipal> nesnesi, olup kod sürekli bağlı olarak rol tabanlı doğrulama gerçekleştirmelisiniz veya yalnızca bir kez gerçekleştirmeniz gerekir.  
  
 Rol tabanlı doğrulama kodu art arda gerçekleştirmeniz gerekirse, aşağıdaki yordamlardan birini ilk yükü daha azdır üretir. Kod gerektiği zaman yalnızca bir kez oluşturabilir, rol tabanlı doğrulamaları yapmak bir <xref:System.Security.Principal.WindowsPrincipal> ikinci aşağıdaki yordamlardan birini kullanarak nesne.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>Yinelenen doğrulama için WindowsPrincipal nesnesi oluşturmak için  
  
1.  Çağrı <xref:System.AppDomain.SetPrincipalPolicy%2A> yöntemi <xref:System.AppDomain> statik tarafından döndürülen nesne <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> yöntemi geçirme özelliği, bir <xref:System.Security.Principal.PrincipalPolicy> yeni ilke olmaması gerektiğini gösteren numaralandırma değeri. Desteklenen değerler <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, ve <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>. Aşağıdaki kod, bu yöntem çağrısı gösterir.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  İlke ile ayarlama, statik kullanmak <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> geçerli Windows kullanıcısı yalıtır asıl almak için özellik. Özelliği döndürme türü olduğundan <xref:System.Security.Principal.IPrincipal>, sonucu atamalısınız bir <xref:System.Security.Principal.WindowsPrincipal> türü. Aşağıdaki kod yeni bir başlatır <xref:System.Security.Principal.WindowsPrincipal> nesnesi için geçerli iş parçacığı ile ilişkili asıl değeri.  
  
    ```csharp  
    WindowsPrincipal MyPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim MyPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  Asıl nesne oluşturduğunuzda doğrulamak için birkaç yöntemden birini kullanabilirsiniz.  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>Tek bir doğrulama için WindowsPrincipal nesnesi oluşturmak için  
  
1.  Yeni bir başlatma <xref:System.Security.Principal.WindowsIdentity> statik çağırarak nesne <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> geçerli Windows hesabının sorgular ve bu hesabı hakkında bilgi yeni oluşturulan kimlik nesnesine yerleştirir yöntemi. Aşağıdaki kod yeni bir oluşturur <xref:System.Security.Principal.WindowsIdentity> nesne ve geçerli kimliği doğrulanmış kullanıcının başlatır.  
  
    ```csharp  
    WindowsIdentity MyIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim MyIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  Yeni bir <xref:System.Security.Principal.WindowsPrincipal> nesne ve değerini geçirin <xref:System.Security.Principal.WindowsIdentity> önceki adımda oluşturulan nesne.  
  
    ```csharp  
    WindowsPrincipal MyPrincipal = new WindowsPrincipal(MyIdentity);  
    ```  
  
    ```vb  
    Dim MyPrincipal As New WindowsPrincipal(MyIdentity)  
    ```  
  
3.  Asıl nesne oluşturduğunuzda doğrulamak için birkaç yöntemden birini kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorumlu ve Kimlik Nesneleri](../../../docs/standard/security/principal-and-identity-objects.md)
