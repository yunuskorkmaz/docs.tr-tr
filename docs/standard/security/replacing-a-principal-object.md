---
description: 'Hakkında daha fazla bilgi edinin: asıl nesneyi değiştirme'
title: Asıl Nesneyi Değiştirme
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET], replacing principal objects
- security [.NET], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
ms.openlocfilehash: 3f413a3b0824cef9f28454bf109d40556f61c26b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684990"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="2eb63-103">Asıl Nesneyi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="2eb63-103">Replacing a Principal Object</span></span>

<span data-ttu-id="2eb63-104">Kimlik doğrulama hizmetleri sağlayan uygulamalar,  <xref:System.Security.Principal.IPrincipal> belirli bir Iş parçacığı için Principal nesnesinin () değiştirilmesini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2eb63-104">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="2eb63-105">Ayrıca, güvenlik sistemi, kötü amaçlı olarak eklenmiş, yanlış bir **asıl öğe** , doğru olmayan bir kimlik veya rol belirterek uygulamanızın güvenliğini tehlikeye atarak **asıl** nesneleri değiştirme özelliğini korumaya yardımcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2eb63-105">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="2eb63-106">Bu nedenle, **asıl** nesneleri değiştirme olanağına sahip olan uygulamalara <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> asıl denetim nesnesi verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2eb63-106">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="2eb63-107">(Rol tabanlı güvenlik denetimleri gerçekleştirmek veya **asıl** nesneler oluşturmak için bu iznin gerekli olmadığını unutmayın.)</span><span class="sxs-lookup"><span data-stu-id="2eb63-107">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
<span data-ttu-id="2eb63-108">Şu görevleri gerçekleştirerek geçerli **asıl** nesne değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="2eb63-108">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="2eb63-109">Yeni bir **asıl** nesne ve ilişkili **Identity** nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2eb63-109">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2. <span data-ttu-id="2eb63-110">Yeni **Principal** nesnesini çağrı bağlamına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2eb63-110">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2eb63-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2eb63-111">Example</span></span>

<span data-ttu-id="2eb63-112">Aşağıdaki örnek, bir genel Principal nesnesinin nasıl oluşturulduğunu ve bir iş parçacığının asıl öğesini ayarlamak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2eb63-112">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
[!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
[!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2eb63-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2eb63-113">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [<span data-ttu-id="2eb63-114">Asıl ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="2eb63-114">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="2eb63-115">ASP.NET Core güvenliği</span><span class="sxs-lookup"><span data-stu-id="2eb63-115">ASP.NET Core Security</span></span>](/aspnet/core/security/)
