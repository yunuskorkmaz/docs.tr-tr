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
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="330e2-102">Nasıl yapılır: WindowsPrincipal Nesnesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="330e2-102">How to: Create a WindowsPrincipal Object</span></span>
<span data-ttu-id="330e2-103">Kodun, tekrar tekrar rol tabanlı doğrulama yapıp gerçekleştirmeyeceğini veya yalnızca bir kez yerine getirmeniz gerektiğini bağlı olarak, <xref:System.Security.Principal.WindowsPrincipal> nesnesi oluşturmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="330e2-103">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
 <span data-ttu-id="330e2-104">Kodun sürekli olarak rol tabanlı doğrulama yapması gerekiyorsa, aşağıdaki yordamların ilki daha az ek yük üretir.</span><span class="sxs-lookup"><span data-stu-id="330e2-104">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="330e2-105">Kodun rol tabanlı doğrulamaları yalnızca bir kez yapması gerektiğinde, aşağıdaki yordamların saniyesini kullanarak bir <xref:System.Security.Principal.WindowsPrincipal> nesnesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="330e2-105">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="330e2-106">Yinelenen doğrulama için bir WindowsPrincipal nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="330e2-106">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1. <span data-ttu-id="330e2-107">Statik <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.AppDomain> nesnesi üzerinde <xref:System.AppDomain.SetPrincipalPolicy%2A> yöntemi çağırın ve yöntemi, yeni ilkenin ne olması gerektiğini belirten bir <xref:System.Security.Principal.PrincipalPolicy> numaralandırma değeri geçirerek.</span><span class="sxs-lookup"><span data-stu-id="330e2-107">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="330e2-108">Desteklenen değerler <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>ve <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="330e2-108">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="330e2-109">Aşağıdaki kod bu yöntem çağrısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="330e2-109">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. <span data-ttu-id="330e2-110">İlke kümesiyle, geçerli Windows kullanıcısını kapsülleyen sorumluyu almak için statik <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="330e2-110">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="330e2-111">Özellik dönüş türü <xref:System.Security.Principal.IPrincipal>olduğundan, sonucu bir <xref:System.Security.Principal.WindowsPrincipal> türüne atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="330e2-111">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="330e2-112">Aşağıdaki kod, geçerli iş parçacığıyla ilişkili asıl değerin değerine yeni bir <xref:System.Security.Principal.WindowsPrincipal> nesnesi başlatır.</span><span class="sxs-lookup"><span data-stu-id="330e2-112">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3. <span data-ttu-id="330e2-113">Asıl nesne oluşturulduğunda, doğrulamak için birkaç yöntemden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="330e2-113">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="330e2-114">Tek bir doğrulama için bir WindowsPrincipal nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="330e2-114">To create a WindowsPrincipal object for a single validation</span></span>  
  
1. <span data-ttu-id="330e2-115">Geçerli Windows hesabını sorgulayan ve bu hesapla ilgili bilgileri yeni oluşturulan kimlik nesnesine yerleştiren statik <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> yöntemini çağırarak yeni bir <xref:System.Security.Principal.WindowsIdentity> nesnesi başlatın.</span><span class="sxs-lookup"><span data-stu-id="330e2-115">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="330e2-116">Aşağıdaki kod yeni bir <xref:System.Security.Principal.WindowsIdentity> nesnesi oluşturur ve onu geçerli kimliği doğrulanmış kullanıcıya başlatır.</span><span class="sxs-lookup"><span data-stu-id="330e2-116">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <span data-ttu-id="330e2-117">Yeni bir <xref:System.Security.Principal.WindowsPrincipal> nesnesi oluşturun ve önceki adımda oluşturulan <xref:System.Security.Principal.WindowsIdentity> nesnesinin değerini geçirin.</span><span class="sxs-lookup"><span data-stu-id="330e2-117">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. <span data-ttu-id="330e2-118">Asıl nesne oluşturulduğunda, doğrulamak için birkaç yöntemden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="330e2-118">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="330e2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="330e2-119">See also</span></span>

- [<span data-ttu-id="330e2-120">Sorumlu ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="330e2-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
