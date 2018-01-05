---
title: "Asıl Nesneyi Değiştirme"
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
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c53064ae12889df09b5259fbb7c8159cfdcd07aa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="369f8-102">Asıl Nesneyi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="369f8-102">Replacing a Principal Object</span></span>
<span data-ttu-id="369f8-103">Kimlik doğrulama hizmetleri sağlayan uygulamalar sağlayabilmelidir değiştirmek **asıl** nesne (<xref:System.Security.Principal.IPrincipal>) belirli bir iş parçacığı için.</span><span class="sxs-lookup"><span data-stu-id="369f8-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="369f8-104">Ayrıca, güvenlik sistemi değiştirme olanağı korunmasına yardımcı olmak gerekir **asıl** çünkü nesneleri bir kötü amaçlı olarak ekli, yanlış **asıl** , uygulamanız tarafından güvenliği tehlikeye atar bir doğru kimlik veya rol beyanda bulunma.</span><span class="sxs-lookup"><span data-stu-id="369f8-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="369f8-105">Bu nedenle, uygulamaları gerektiren değiştirme olanağı **asıl** nesneleri verilmelidir <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> asıl denetimi için nesnesi.</span><span class="sxs-lookup"><span data-stu-id="369f8-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="369f8-106">(Bu izni rol tabanlı güvenlik denetimleri yapmak için veya oluşturmak için gerekli olmadığını unutmayın **asıl** nesneleri.)</span><span class="sxs-lookup"><span data-stu-id="369f8-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
 <span data-ttu-id="369f8-107">Geçerli **asıl** nesnesi, aşağıdaki görevleri gerçekleştirerek değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="369f8-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="369f8-108">Değiştirme oluşturma **asıl** nesne ve ilişkili **kimlik** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="369f8-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2.  <span data-ttu-id="369f8-109">Yeni attach **asıl** çağrısı bağlam nesnesi.</span><span class="sxs-lookup"><span data-stu-id="369f8-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="369f8-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="369f8-110">Example</span></span>  
 <span data-ttu-id="369f8-111">Aşağıdaki örnek, genel bir asıl nesne oluşturma ve bir iş parçacığı asıl ayarlamak için kullanma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="369f8-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="369f8-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="369f8-112">See Also</span></span>  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
 [<span data-ttu-id="369f8-113">Sorumlu ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="369f8-113">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
