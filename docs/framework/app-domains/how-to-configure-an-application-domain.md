---
title: "Nasıl yapılır: Uygulama Etki Alanını Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 890a8b31339715a4dac8fd2c6e76cc11cda0ee4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-an-application-domain"></a>Nasıl yapılır: Uygulama Etki Alanını Yapılandırma
Ortak dil çalışma zamanı kullanarak yeni bir uygulama etki alanı için yapılandırma bilgilerini sağlayabilir <xref:System.AppDomainSetup> sınıfı. Kendi uygulama etki alanları oluştururken en önemli özelliktir <xref:System.AppDomainSetup.ApplicationBase%2A>. Diğer **AppDomainSetup** özellikleri, belirli bir uygulama etki yapılandırmak için çoğunlukla çalışma zamanı ana bilgisayarı tarafından kullanılır.  
  
 **ApplicationBase** özelliği tanımlar uygulaması kök dizini. Çalışma zamanı türü isteği karşılamak gerektiğinde tarafından belirtilen dizinde türünü içeren bütünleştirilmiş için yoklamaları **ApplicationBase** özelliği.  
  
> [!NOTE]
>  Yeni bir uygulama etki alanı yalnızca devralınan **ApplicationBase** Oluşturucusu özelliği.  
  
 Aşağıdaki örnekte bir örneğini oluşturur **AppDomainSetup** sınıfı, yeni bir uygulama etki alanı oluşturmak için bu sınıfı kullanır, bilgileri konsola yazar ve uygulama etki alanı kaldırır.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama etki alanları ile programlama](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [Uygulama Etki Alanlarını Kullanma](../../../docs/framework/app-domains/use.md)
