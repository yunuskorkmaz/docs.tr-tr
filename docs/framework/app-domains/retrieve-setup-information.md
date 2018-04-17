---
title: Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b5a7585b68c36fe5e435e563729d9a0f3540a42a
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="retrieving-setup-information-from-an-application-domain"></a>Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma
Uygulama etki alanı her örneği her iki özellikten oluşur ve <xref:System.AppDomainSetup> bilgi. Kullanarak bir uygulama etki alanı, Kur bilgi alabileceğiniz <xref:System.AppDomain?displayProperty=nameWithType> sınıfı. Bu sınıf, uygulama etki alanı hakkında yapılandırma bilgilerini almak birkaç üye sağlar.  
  
 Sorgu da **AppDomainSetup** oluşturulduğunda, etki alanına geçirilen kurulum bilgilerini almak uygulama etki alanı için nesne.  
  
 Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur ve birkaç üyesine değerlerini konsola yazdırır.  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 Aşağıdaki örnek kümeleri ve alır, Kur bilgi için uygulama etki alanı. Unutmayın `AppDomain.SetupInformation.ApplicationBase` yapılandırma bilgilerini alır.  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Uygulama etki alanları ile programlama](application-domains.md#programming-with-application-domains)  
 [Uygulama Etki Alanlarını Kullanma](../../../docs/framework/app-domains/use.md)
