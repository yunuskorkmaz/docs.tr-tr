---
title: Asıl Nesneyi Değiştirme
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET], replacing principal objects
- security [.NET], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
ms.openlocfilehash: fced91aef991bc228e65128d5e8d69e6a46588e5
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557105"
---
# <a name="replacing-a-principal-object"></a>Asıl Nesneyi Değiştirme

Kimlik doğrulama hizmetleri sağlayan uygulamalar, **Principal** <xref:System.Security.Principal.IPrincipal> belirli bir Iş parçacığı için Principal nesnesinin () değiştirilmesini sağlamalıdır. Ayrıca, güvenlik sistemi, kötü amaçlı olarak eklenmiş, yanlış bir **asıl öğe** , doğru olmayan bir kimlik veya rol belirterek uygulamanızın güvenliğini tehlikeye atarak **asıl** nesneleri değiştirme özelliğini korumaya yardımcı olmalıdır. Bu nedenle, **asıl** nesneleri değiştirme olanağına sahip olan uygulamalara <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> asıl denetim nesnesi verilmelidir. (Rol tabanlı güvenlik denetimleri gerçekleştirmek veya **asıl** nesneler oluşturmak için bu iznin gerekli olmadığını unutmayın.)  
  
Şu görevleri gerçekleştirerek geçerli **asıl** nesne değiştirilebilir:  
  
1. Yeni bir **asıl** nesne ve ilişkili **Identity** nesnesi oluşturun.  
  
2. Yeni **Principal** nesnesini çağrı bağlamına ekleyin.  
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, bir genel Principal nesnesinin nasıl oluşturulduğunu ve bir iş parçacığının asıl öğesini ayarlamak için nasıl kullanılacağını gösterir.  
  
[!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
[!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [Asıl ve Kimlik Nesneleri](principal-and-identity-objects.md)
- [ASP.NET Core güvenliği](/aspnet/core/security/)
