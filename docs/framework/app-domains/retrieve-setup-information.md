---
title: Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 719ea15de135d8bbeb7bb88ea3d5b5874e30b5d6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053099"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a>Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma
Bir uygulama etki alanının her örneği, hem özelliklerden <xref:System.AppDomainSetup> hem de bilgilerden oluşur. Bir uygulama etki alanından kurulum bilgilerini <xref:System.AppDomain?displayProperty=nameWithType> sınıfını kullanarak alabilirsiniz. Bu sınıf, bir uygulama etki alanı hakkında yapılandırma bilgilerini alan çeşitli Üyeler sağlar.  
  
 Ayrıca, uygulama etki alanı için **AppDomainSetup** nesnesini sorgulayabilirsiniz. Bu, etki alanına gönderilen kurulum bilgilerini elde edebilir.  
  
 Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur ve ardından konsola birkaç üye değeri yazdırır.  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 Aşağıdaki örnek, bir uygulama etki alanı için kurulum bilgilerini ayarlar ve ardından alır. Yapılandırma bilgilerini `AppDomain.SetupInformation.ApplicationBase` alır.  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama etki alanlarıyla programlama](application-domains.md#programming-with-application-domains)
- [Uygulama Etki Alanlarını Kullanma](use.md)
