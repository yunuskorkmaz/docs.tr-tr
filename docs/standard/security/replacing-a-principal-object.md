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
# <a name="replacing-a-principal-object"></a>Asıl Nesneyi Değiştirme
Kimlik doğrulama hizmetleri sağlayan uygulamalar, belirli bir iş parçacığının **asıl** nesnesini (<xref:System.Security.Principal.IPrincipal>) değiştirmek zorunda olmalıdır. Ayrıca, güvenlik sistemi, kötü amaçlı olarak eklenmiş, yanlış bir **asıl öğe** , doğru olmayan bir kimlik veya rol belirterek uygulamanızın güvenliğini tehlikeye atarak **asıl** nesneleri değiştirme özelliğini korumaya yardımcı olmalıdır. Bu nedenle, **asıl** nesneleri değiştirme olanağına sahip olan uygulamalara asıl denetim için <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> nesnesi verilmelidir. (Rol tabanlı güvenlik denetimleri gerçekleştirmek veya **asıl** nesneler oluşturmak için bu iznin gerekli olmadığını unutmayın.)  
  
 Şu görevleri gerçekleştirerek geçerli **asıl** nesne değiştirilebilir:  
  
1. Yeni bir **asıl** nesne ve ilişkili **Identity** nesnesi oluşturun.  
  
2. Yeni **Principal** nesnesini çağrı bağlamına ekleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir genel Principal nesnesinin nasıl oluşturulduğunu ve bir iş parçacığının asıl öğesini ayarlamak için nasıl kullanılacağını gösterir.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [Sorumlu ve Kimlik Nesneleri](../../../docs/standard/security/principal-and-identity-objects.md)
