---
title: "Dağıtım konuları (Entity Framework)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 03c64c9a300a92a86dfac1ed92c67be248e53219
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="deployment-considerations-entity-framework"></a>Dağıtım konuları (Entity Framework)
Bu konu, veri erişimi için ADO.NET Entity Framework kullanan uygulamaları dağıtma hakkında bilgi sağlar. Entity Framework hakkında daha fazla bilgi için bkz: [Başlarken](../../../../../docs/framework/data/adonet/ef/getting-started.md).  
  
 Entity Framework ile tümleştirilebilen ve geliştirmek Visual Studio'da kolaylaştıran araçlar sağlar. Daha fazla bilgi için bkz: [ADO.NET varlık veri modeli Araçları](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527). Bu konuda, Entity Framework tabanlı bir uygulama dağıtmak için belirli teknolojileri kullanmayı açıklamaz.  
  
 Visual Studio dağıtma ve ClickOnce dağıtımı gibi uygulamaları dağıtmak için gerekli olanakları sağlar. Daha fazla bilgi için bkz: [dağıtımı uygulamaları ve bileşenleri](https://msdn.microsoft.com/library/wtzawcsz) Visual Studio belgelerinde.  
  
 Entity Framework kullanan bir uygulamayı dağıttığınızda aşağıdaki maddeler geçerlidir:  
  
-   Entity Framework, .NET Framework 3.5 Hizmet Paketi 1 (SP1)'den başlayarak .NET Framework'ün bir bileşenidir. .NET Framework 3.5 SP1 veya sonraki bir sürümünü Entity Framework tabanlı bir uygulama dağıtırken yüklü emin olmanız gerekir.  
  
-   Kavramsal model varlık veri modeli Sihirbazı tarafından oluşturulan bir bağlantı dizesi uygulama yapılandırma dosyasında oluşturulur. Uygulama kaynakları modeli ve eşleme dosyaları katıştırılabilen veya çıktı dizinine kopyalanır. Varsayılan olarak, bunlar ekli uygulama kaynaklar olarak dağıtılır. Kullanım `Metadata Artifact Processing` bu seçeneklerden birini seçmek için Entity Designer dosyasının özelliği. Daha fazla bilgi için bkz: [nasıl yapılır: kopya modeli ve eşleme dosyalar çıkış dizinine](http://msdn.microsoft.com/en-us/e2c9820f-1705-457e-9fdb-8b289f3179b4).  
  
-   Model ve eşleme (kavramsal şema tanım dili (CSDL), depo şeması tanım dili (SSDL) ve eşleme belirtimi dili (MSL) ifade edilir) bilgileri dağıtılması uygulamayla birlikte ve konumda emin olun bağlantı dizesi tarafından belirtilen. Daha fazla bilgi için bkz: [bağlantı dizeleri](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
-   Model ve uygulama kaynakları olarak bilgilerini eşleme katıştırma derlenir ve kavramsal model her güncelleştirildiğinde uygulama yeniden dağıtın.  
  
-   Entity Framework .NET Framework'ün bir bileşeni olduğu için .NET Framework lisans sözleşmenize göre izin verilen olarak uygulamanıza ile dağıtılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)  
 [Geliştirme ve dağıtım konuları](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
