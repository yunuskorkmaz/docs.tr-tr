---
title: Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma
description: System. AppDomain sınıfını veya AppDomainSetup nesnesini kullanarak .NET 'teki bir uygulama etki alanından kurulum bilgilerini alın.
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
ms.openlocfilehash: 3b7fdd302ac11caa423815483a4add38264f0910
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325664"
---
# <a name="retrieve-setup-information-from-an-application-domain"></a>Uygulama etki alanından kurulum bilgilerini alma

Bir uygulama etki alanının her örneği, hem özelliklerden hem de <xref:System.AppDomainSetup> bilgilerden oluşur. Bir uygulama etki alanından kurulum bilgilerini sınıfını kullanarak alabilirsiniz <xref:System.AppDomain?displayProperty=nameWithType> . Bu sınıf, bir uygulama etki alanı hakkında yapılandırma bilgilerini alan çeşitli Üyeler sağlar.  
  
 Ayrıca, uygulama etki alanı için **AppDomainSetup** nesnesini sorgulayabilirsiniz. Bu, etki alanına gönderilen kurulum bilgilerini elde edebilir.  
  
 Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur ve ardından konsola birkaç üye değeri yazdırır.  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 Aşağıdaki örnek, bir uygulama etki alanı için kurulum bilgilerini ayarlar ve ardından alır. `AppDomain.SetupInformation.ApplicationBase`yapılandırma bilgilerini alır.  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama etki alanlarıyla programlama](application-domains.md#programming-with-application-domains)
- [Uygulama Etki Alanlarını Kullanma](use.md)
