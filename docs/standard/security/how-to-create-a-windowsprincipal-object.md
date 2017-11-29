---
title: "Nasıl yapılır: WindowsPrincipal Nesnesi Oluşturma"
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
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f35c7382138c92a5f6618e388b070251516b7b0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="dbd86-102">Nasıl yapılır: WindowsPrincipal Nesnesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="dbd86-102">How to: Create a WindowsPrincipal Object</span></span>
<span data-ttu-id="dbd86-103">Oluşturmanın iki yolu vardır bir <xref:System.Security.Principal.WindowsPrincipal> nesnesi, olup kod sürekli bağlı olarak rol tabanlı doğrulama gerçekleştirmelisiniz veya yalnızca bir kez gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbd86-103">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
 <span data-ttu-id="dbd86-104">Rol tabanlı doğrulama kodu art arda gerçekleştirmeniz gerekirse, aşağıdaki yordamlardan birini ilk yükü daha azdır üretir.</span><span class="sxs-lookup"><span data-stu-id="dbd86-104">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="dbd86-105">Kod gerektiği zaman yalnızca bir kez oluşturabilir, rol tabanlı doğrulamaları yapmak bir <xref:System.Security.Principal.WindowsPrincipal> ikinci aşağıdaki yordamlardan birini kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="dbd86-105">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="dbd86-106">Yinelenen doğrulama için WindowsPrincipal nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="dbd86-106">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1.  <span data-ttu-id="dbd86-107">Çağrı <xref:System.AppDomain.SetPrincipalPolicy%2A> yöntemi <xref:System.AppDomain> statik tarafından döndürülen nesne <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> yöntemi geçirme özelliği, bir <xref:System.Security.Principal.PrincipalPolicy> yeni ilke olmaması gerektiğini gösteren numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="dbd86-107">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="dbd86-108">Desteklenen değerler <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, ve <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="dbd86-108">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="dbd86-109">Aşağıdaki kod, bu yöntem çağrısı gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbd86-109">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  <span data-ttu-id="dbd86-110">İlke ile ayarlama, statik kullanmak <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> geçerli Windows kullanıcısı yalıtır asıl almak için özellik.</span><span class="sxs-lookup"><span data-stu-id="dbd86-110">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="dbd86-111">Özelliği döndürme türü olduğundan <xref:System.Security.Principal.IPrincipal>, sonucu atamalısınız bir <xref:System.Security.Principal.WindowsPrincipal> türü.</span><span class="sxs-lookup"><span data-stu-id="dbd86-111">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="dbd86-112">Aşağıdaki kod yeni bir başlatır <xref:System.Security.Principal.WindowsPrincipal> nesnesi için geçerli iş parçacığı ile ilişkili asıl değeri.</span><span class="sxs-lookup"><span data-stu-id="dbd86-112">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal MyPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim MyPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  <span data-ttu-id="dbd86-113">Asıl nesne oluşturduğunuzda doğrulamak için birkaç yöntemden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbd86-113">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="dbd86-114">Tek bir doğrulama için WindowsPrincipal nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="dbd86-114">To create a WindowsPrincipal object for a single validation</span></span>  
  
1.  <span data-ttu-id="dbd86-115">Yeni bir başlatma <xref:System.Security.Principal.WindowsIdentity> statik çağırarak nesne <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> geçerli Windows hesabının sorgular ve bu hesabı hakkında bilgi yeni oluşturulan kimlik nesnesine yerleştirir yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dbd86-115">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="dbd86-116">Aşağıdaki kod yeni bir oluşturur <xref:System.Security.Principal.WindowsIdentity> nesne ve geçerli kimliği doğrulanmış kullanıcının başlatır.</span><span class="sxs-lookup"><span data-stu-id="dbd86-116">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity MyIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim MyIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  <span data-ttu-id="dbd86-117">Yeni bir <xref:System.Security.Principal.WindowsPrincipal> nesne ve değerini geçirin <xref:System.Security.Principal.WindowsIdentity> önceki adımda oluşturulan nesne.</span><span class="sxs-lookup"><span data-stu-id="dbd86-117">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal MyPrincipal = new WindowsPrincipal(MyIdentity);  
    ```  
  
    ```vb  
    Dim MyPrincipal As New WindowsPrincipal(MyIdentity)  
    ```  
  
3.  <span data-ttu-id="dbd86-118">Asıl nesne oluşturduğunuzda doğrulamak için birkaç yöntemden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbd86-118">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd86-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbd86-119">See Also</span></span>  
 [<span data-ttu-id="dbd86-120">Asıl ve kimlik nesneleri</span><span class="sxs-lookup"><span data-stu-id="dbd86-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
