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
ms.openlocfilehash: 80c9fe6de0fca86497ffe84cd8dadf0eb8cef6c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705577"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a>Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma
Her örnek bir uygulama etki alanının her iki özellikten oluşur ve <xref:System.AppDomainSetup> bilgileri. Kullanarak bir uygulama etki alanı kurulum bilgilerini alabilir <xref:System.AppDomain?displayProperty=nameWithType> sınıfı. Bu sınıf, bir uygulama etki alanı yapılandırma bilgilerini almak birkaç üyeleri sağlar.  
  
 Ayrıca Sorgulayabileceğiniz **AppDomainSetup** oluşturulduğunda, etki alanına geçirildi kurulum bilgilerini almak uygulama etki alanı için nesne.  
  
 Aşağıdaki örnek, yeni bir uygulama etki alanı oluşturur ve ardından çeşitli üye değerleri konsola yazdırır.  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 Örnek ayarlar ve alır, kurulum için aşağıdaki bilgileri uygulama etki alanı. Unutmayın `AppDomain.SetupInformation.ApplicationBase` yapılandırma bilgilerini alır.  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama etki alanlarıyla programlama](application-domains.md#programming-with-application-domains)
- [Uygulama Etki Alanlarını Kullanma](../../../docs/framework/app-domains/use.md)
