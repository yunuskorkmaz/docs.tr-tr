---
title: 'Nasıl yapılır: Uygulama Etki Alanını Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb7223d2356ebec54ddd64dee514f1c8785e2d17
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921575"
---
# <a name="how-to-configure-an-application-domain"></a>Nasıl yapılır: Uygulama Etki Alanını Yapılandırma
<xref:System.AppDomainSetup> Sınıfını kullanarak yeni bir uygulama etki alanı için yapılandırma bilgileriyle ortak dil çalışma zamanı sağlayabilirsiniz. Kendi uygulama etki alanlarınızı oluştururken en önemli özellik ' dir <xref:System.AppDomainSetup.ApplicationBase%2A>. Diğer **AppDomainSetup** özellikleri, genellikle belirli bir uygulama etki alanını yapılandırmak için çalışma zamanı konakları tarafından kullanılır.  
  
 **ApplicationBase** özelliği, uygulamanın kök dizinini tanımlar. Çalışma zamanının bir tür isteğini karşılaması gerektiğinde, **ApplicationBase** özelliği tarafından belirtilen dizinde türü içeren derlemeyi yoklamalar.  
  
> [!NOTE]
> Yeni bir uygulama etki alanı, oluşturucunun yalnızca **ApplicationBase** özelliğini devralır.  
  
 Aşağıdaki örnek, **AppDomainSetup** sınıfının bir örneğini oluşturur, yeni bir uygulama etki alanı oluşturmak için bu sınıfı kullanır, bilgileri konsola yazar ve ardından uygulama etki alanını kaldırır.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama etki alanlarıyla programlama](application-domains.md#programming-with-application-domains)
- [Uygulama Etki Alanlarını Kullanma](../../../docs/framework/app-domains/use.md)
