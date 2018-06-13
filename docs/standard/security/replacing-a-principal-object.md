---
title: Asıl Nesneyi Değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94391471fecd92aeadec4da39cdd5b6f80bb6949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581170"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="7b405-102">Asıl Nesneyi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="7b405-102">Replacing a Principal Object</span></span>
<span data-ttu-id="7b405-103">Kimlik doğrulama hizmetleri sağlayan uygulamalar sağlayabilmelidir değiştirmek **asıl** nesne (<xref:System.Security.Principal.IPrincipal>) belirli bir iş parçacığı için.</span><span class="sxs-lookup"><span data-stu-id="7b405-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="7b405-104">Ayrıca, güvenlik sistemi değiştirme olanağı korunmasına yardımcı olmak gerekir **asıl** çünkü nesneleri bir kötü amaçlı olarak ekli, yanlış **asıl** , uygulamanız tarafından güvenliği tehlikeye atar bir doğru kimlik veya rol beyanda bulunma.</span><span class="sxs-lookup"><span data-stu-id="7b405-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="7b405-105">Bu nedenle, uygulamaları gerektiren değiştirme olanağı **asıl** nesneleri verilmelidir <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> asıl denetimi için nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7b405-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="7b405-106">(Bu izni rol tabanlı güvenlik denetimleri yapmak için veya oluşturmak için gerekli olmadığını unutmayın **asıl** nesneleri.)</span><span class="sxs-lookup"><span data-stu-id="7b405-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
 <span data-ttu-id="7b405-107">Geçerli **asıl** nesnesi, aşağıdaki görevleri gerçekleştirerek değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="7b405-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="7b405-108">Değiştirme oluşturma **asıl** nesne ve ilişkili **kimlik** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7b405-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2.  <span data-ttu-id="7b405-109">Yeni attach **asıl** çağrısı bağlam nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7b405-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b405-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b405-110">Example</span></span>  
 <span data-ttu-id="7b405-111">Aşağıdaki örnek, genel bir asıl nesne oluşturma ve bir iş parçacığı asıl ayarlamak için kullanma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7b405-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7b405-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b405-112">See Also</span></span>  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
 [<span data-ttu-id="7b405-113">Sorumlu ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="7b405-113">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
