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
ms.openlocfilehash: 89b7036215cb7998222e280ceef02073d455a1b2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705944"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="e857f-102">Asıl Nesneyi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="e857f-102">Replacing a Principal Object</span></span>
<span data-ttu-id="e857f-103">Kimlik doğrulama hizmetleri sağlayan uygulamalar, belirli bir iş parçacığının **asıl** nesnesini (<xref:System.Security.Principal.IPrincipal>) değiştirmek zorunda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e857f-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="e857f-104">Ayrıca, güvenlik sistemi, kötü amaçlı olarak eklenmiş, yanlış bir **asıl öğe** , doğru olmayan bir kimlik veya rol belirterek uygulamanızın güvenliğini tehlikeye atarak **asıl** nesneleri değiştirme özelliğini korumaya yardımcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e857f-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="e857f-105">Bu nedenle, **asıl** nesneleri değiştirme olanağına sahip olan uygulamalara asıl denetim için <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> nesnesi verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e857f-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="e857f-106">(Rol tabanlı güvenlik denetimleri gerçekleştirmek veya **asıl** nesneler oluşturmak için bu iznin gerekli olmadığını unutmayın.)</span><span class="sxs-lookup"><span data-stu-id="e857f-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
 <span data-ttu-id="e857f-107">Şu görevleri gerçekleştirerek geçerli **asıl** nesne değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="e857f-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="e857f-108">Yeni bir **asıl** nesne ve ilişkili **Identity** nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e857f-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2. <span data-ttu-id="e857f-109">Yeni **Principal** nesnesini çağrı bağlamına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e857f-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e857f-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="e857f-110">Example</span></span>  
 <span data-ttu-id="e857f-111">Aşağıdaki örnek, bir genel Principal nesnesinin nasıl oluşturulduğunu ve bir iş parçacığının asıl öğesini ayarlamak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e857f-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e857f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e857f-112">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [<span data-ttu-id="e857f-113">Sorumlu ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="e857f-113">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
