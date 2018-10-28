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
ms.openlocfilehash: 012f0220afa0e444d68af5998fb2492a03a371d8
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183171"
---
# <a name="how-to-configure-an-application-domain"></a>Nasıl yapılır: Uygulama Etki Alanını Yapılandırma
Ortak dil çalışma zamanı kullanarak yeni bir uygulama etki alanı için yapılandırma bilgilerini sağlayabilir <xref:System.AppDomainSetup> sınıfı. Kendi uygulama etki alanları oluştururken, en önemli özelliği <xref:System.AppDomainSetup.ApplicationBase%2A>. Diğer **AppDomainSetup** özellikleri, belirli bir uygulama etki alanını yapılandırmak için temel olarak çalışma zamanı ana bilgisayarları tarafından kullanılır.  
  
 **ApplicationBase** uygulamanın kök dizin özelliği tanımlar. Çalışma zamanı türü isteği karşılamak gerektiğinde türü tarafından belirtilen dizindeki içeren derleme yoklamaları **ApplicationBase** özelliği.  
  
> [!NOTE]
>  Yeni bir uygulama etki alanı yalnızca devralınan **ApplicationBase** Oluşturucusu özelliği.  
  
 Aşağıdaki örnek, bir örneğini oluşturur. **AppDomainSetup** sınıfının yeni bir uygulama etki alanı oluşturmak için bu sınıfın kullandığı, bilgileri konsola yazar ve ardından uygulama etki alanını kaldırır.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [Uygulama etki alanlarıyla programlama](application-domains.md#programming-with-application-domains)  
- [Uygulama Etki Alanlarını Kullanma](../../../docs/framework/app-domains/use.md)
