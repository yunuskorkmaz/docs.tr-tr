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
# <a name="replacing-a-principal-object"></a>Asıl Nesneyi Değiştirme
Kimlik doğrulama hizmetleri sağlayan uygulamalar sağlayabilmelidir değiştirmek **asıl** nesne (<xref:System.Security.Principal.IPrincipal>) belirli bir iş parçacığı için. Ayrıca, güvenlik sistemi değiştirme olanağı korunmasına yardımcı olmak gerekir **asıl** çünkü nesneleri bir kötü amaçlı olarak ekli, yanlış **asıl** , uygulamanız tarafından güvenliği tehlikeye atar bir doğru kimlik veya rol beyanda bulunma. Bu nedenle, uygulamaları gerektiren değiştirme olanağı **asıl** nesneleri verilmelidir <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> asıl denetimi için nesnesi. (Bu izni rol tabanlı güvenlik denetimleri yapmak için veya oluşturmak için gerekli olmadığını unutmayın **asıl** nesneleri.)  
  
 Geçerli **asıl** nesnesi, aşağıdaki görevleri gerçekleştirerek değiştirilebilir:  
  
1.  Değiştirme oluşturma **asıl** nesne ve ilişkili **kimlik** nesnesi.  
  
2.  Yeni attach **asıl** çağrısı bağlam nesnesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, genel bir asıl nesne oluşturma ve bir iş parçacığı asıl ayarlamak için kullanma gösterilmektedir.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
 [Sorumlu ve Kimlik Nesneleri](../../../docs/standard/security/principal-and-identity-objects.md)
