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
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59345449"
---
# <a name="replacing-a-principal-object"></a>Asıl Nesneyi Değiştirme
Kimlik doğrulama hizmetleri sağlayan uygulamalar sağlayabilmelidir değiştirin **asıl** nesne (<xref:System.Security.Principal.IPrincipal>) belirli bir iş parçacığı için. Ayrıca, güvenlik sistemi değiştirme olanağı korumanız gerekir **asıl** çünkü nesneleri bir kötü amaçlı olarak eklenen, yanlış **asıl** uygulamanız tarafından güvenliği tehlikeye atar bir doğru kimlik veya bir rolü beyanda bulunma. Bu nedenle, uygulamaları gerektiren değiştirme olanağı **asıl** nesneleri verilmelidir <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> asıl denetim için nesne. (Bu izni rol tabanlı güvenlik denetimleri gerçekleştirme veya oluşturmak için gerekli olmadığını unutmayın **asıl** nesneleri.)  
  
 Geçerli **asıl** nesne, aşağıdaki görevleri gerçekleştirerek değiştirilebilir:  
  
1. Değiştirme Oluştur **asıl** nesnesini ve ilişkili **kimlik** nesne.  
  
2. Yeni Ekle **asıl** çağrı bağlam nesnesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, genel bir sorumlu nesnesi oluşturun ve bir iş parçacığı sorumlusu ayarlamak için kullanma gösterilmektedir.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [Asıl ve Kimlik Nesneleri](../../../docs/standard/security/principal-and-identity-objects.md)
