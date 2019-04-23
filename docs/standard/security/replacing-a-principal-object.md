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
ms.openlocfilehash: 5f33be207dd6166b16a04844f3d92b6e017d1c7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345449"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="7753d-102">Asıl Nesneyi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="7753d-102">Replacing a Principal Object</span></span>
<span data-ttu-id="7753d-103">Kimlik doğrulama hizmetleri sağlayan uygulamalar sağlayabilmelidir değiştirin **asıl** nesne (<xref:System.Security.Principal.IPrincipal>) belirli bir iş parçacığı için.</span><span class="sxs-lookup"><span data-stu-id="7753d-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="7753d-104">Ayrıca, güvenlik sistemi değiştirme olanağı korumanız gerekir **asıl** çünkü nesneleri bir kötü amaçlı olarak eklenen, yanlış **asıl** uygulamanız tarafından güvenliği tehlikeye atar bir doğru kimlik veya bir rolü beyanda bulunma.</span><span class="sxs-lookup"><span data-stu-id="7753d-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="7753d-105">Bu nedenle, uygulamaları gerektiren değiştirme olanağı **asıl** nesneleri verilmelidir <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> asıl denetim için nesne.</span><span class="sxs-lookup"><span data-stu-id="7753d-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="7753d-106">(Bu izni rol tabanlı güvenlik denetimleri gerçekleştirme veya oluşturmak için gerekli olmadığını unutmayın **asıl** nesneleri.)</span><span class="sxs-lookup"><span data-stu-id="7753d-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
 <span data-ttu-id="7753d-107">Geçerli **asıl** nesne, aşağıdaki görevleri gerçekleştirerek değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="7753d-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="7753d-108">Değiştirme Oluştur **asıl** nesnesini ve ilişkili **kimlik** nesne.</span><span class="sxs-lookup"><span data-stu-id="7753d-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2. <span data-ttu-id="7753d-109">Yeni Ekle **asıl** çağrı bağlam nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7753d-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7753d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="7753d-110">Example</span></span>  
 <span data-ttu-id="7753d-111">Aşağıdaki örnek, genel bir sorumlu nesnesi oluşturun ve bir iş parçacığı sorumlusu ayarlamak için kullanma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7753d-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7753d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7753d-112">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [<span data-ttu-id="7753d-113">Sorumlu ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="7753d-113">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
