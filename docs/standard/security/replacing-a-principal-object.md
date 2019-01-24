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
ms.openlocfilehash: d5193756861f407315ec82e4419f1d04495c7dd2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606039"
---
# <a name="replacing-a-principal-object"></a>Asıl Nesneyi Değiştirme
Kimlik doğrulama hizmetleri sağlayan uygulamalar sağlayabilmelidir değiştirin **asıl** nesne (<xref:System.Security.Principal.IPrincipal>) belirli bir iş parçacığı için. Ayrıca, güvenlik sistemi değiştirme olanağı korumanız gerekir **asıl** çünkü nesneleri bir kötü amaçlı olarak eklenen, yanlış **asıl** uygulamanız tarafından güvenliği tehlikeye atar bir doğru kimlik veya bir rolü beyanda bulunma. Bu nedenle, uygulamaları gerektiren değiştirme olanağı **asıl** nesneleri verilmelidir <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> asıl denetim için nesne. (Bu izni rol tabanlı güvenlik denetimleri gerçekleştirme veya oluşturmak için gerekli olmadığını unutmayın **asıl** nesneleri.)  
  
 Geçerli **asıl** nesne, aşağıdaki görevleri gerçekleştirerek değiştirilebilir:  
  
1.  Değiştirme Oluştur **asıl** nesnesini ve ilişkili **kimlik** nesne.  
  
2.  Yeni Ekle **asıl** çağrı bağlam nesnesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, genel bir sorumlu nesnesi oluşturun ve bir iş parçacığı sorumlusu ayarlamak için kullanma gösterilmektedir.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [Sorumlu ve Kimlik Nesneleri](../../../docs/standard/security/principal-and-identity-objects.md)
