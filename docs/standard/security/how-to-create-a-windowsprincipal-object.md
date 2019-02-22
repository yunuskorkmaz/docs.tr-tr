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
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="5a35b-102">Nasıl yapılır: WindowsPrincipal nesnesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a35b-102">How to: Create a WindowsPrincipal Object</span></span>
<span data-ttu-id="5a35b-103">Oluşturmanın iki yolu vardır. bir <xref:System.Security.Principal.WindowsPrincipal> nesne, rol tabanlı doğrulama gerçekleştirmeniz olup kod tekrar tekrar gerekir bağlı olarak veya yalnızca bir kez gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a35b-103">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
 <span data-ttu-id="5a35b-104">Kod tekrar tekrar rol tabanlı doğrulama gerçekleştirmesi gerekiyorsa, aşağıdaki yordamlardan birini ilk daha az ek yük oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5a35b-104">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="5a35b-105">Kod gerektiğinde yalnızca bir kez oluşturabilir, rol tabanlı doğrulamaları yapmak bir <xref:System.Security.Principal.WindowsPrincipal> ikinci aşağıdaki yordamlardan birini kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="5a35b-105">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="5a35b-106">Yinelenen doğrulama için WindowsPrincipal nesnesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a35b-106">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1.  <span data-ttu-id="5a35b-107">Çağrı <xref:System.AppDomain.SetPrincipalPolicy%2A> metodunda <xref:System.AppDomain> statik tarafından döndürülen nesne <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> yöntemi geçirme özelliği, bir <xref:System.Security.Principal.PrincipalPolicy> yeni ilke olmaması gerektiğini gösteren bir numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="5a35b-107">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="5a35b-108">Desteklenen değerler şunlardır: <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, ve <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="5a35b-108">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="5a35b-109">Aşağıdaki kod, bu yöntem çağrısının gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a35b-109">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  <span data-ttu-id="5a35b-110">İlkeyle ayarlama, statik <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> kapsülleyen geçerli Windows kullanıcısının asıl almak için özellik.</span><span class="sxs-lookup"><span data-stu-id="5a35b-110">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="5a35b-111">Özelliği döndürme türü olduğundan <xref:System.Security.Principal.IPrincipal>, sonucu dönüştürmelisiniz bir <xref:System.Security.Principal.WindowsPrincipal> türü.</span><span class="sxs-lookup"><span data-stu-id="5a35b-111">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="5a35b-112">Aşağıdaki kodu yeni başlatır <xref:System.Security.Principal.WindowsPrincipal> değerine geçerli iş parçacığıyla ilişkilendirilmiş sorumlusu nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5a35b-112">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  <span data-ttu-id="5a35b-113">Asıl nesne oluşturulduğunda bunu doğrulamak için birkaç yöntemden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a35b-113">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="5a35b-114">Tek bir doğrulama için WindowsPrincipal nesnesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a35b-114">To create a WindowsPrincipal object for a single validation</span></span>  
  
1.  <span data-ttu-id="5a35b-115">Yeni bir başlatma <xref:System.Security.Principal.WindowsIdentity> statik çağırarak <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> yöntemi geçerli Windows hesabını sorgular ve bu hesabı hakkında bilgi yeni oluşturulan kimlik nesnesi içine yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="5a35b-115">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="5a35b-116">Aşağıdaki kod yeni bir oluşturur <xref:System.Security.Principal.WindowsIdentity> nesne ve kimliği doğrulanmış geçerli kullanıcının başlatır.</span><span class="sxs-lookup"><span data-stu-id="5a35b-116">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  <span data-ttu-id="5a35b-117">Yeni bir <xref:System.Security.Principal.WindowsPrincipal> nesne ve değerini geçirin <xref:System.Security.Principal.WindowsIdentity> önceki adımda oluşturulan nesne.</span><span class="sxs-lookup"><span data-stu-id="5a35b-117">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3.  <span data-ttu-id="5a35b-118">Asıl nesne oluşturulduğunda bunu doğrulamak için birkaç yöntemden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a35b-118">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a35b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a35b-119">See also</span></span>

- [<span data-ttu-id="5a35b-120">Sorumlu ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="5a35b-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
