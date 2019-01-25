---
title: Dağıtım konuları (varlık çerçevesi)
ms.date: 03/30/2017
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
ms.openlocfilehash: b240b7da1d05e1bf02e31acc3c99b16a908a6add
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689883"
---
# <a name="deployment-considerations-entity-framework"></a>Dağıtım konuları (varlık çerçevesi)
Bu konuda, veri erişimi için ADO.NET Entity Framework kullanan uygulamaları dağıtma hakkında bilgi sağlar. Varlık çerçevesi hakkında daha fazla bilgi için bkz: [Başlarken](../../../../../docs/framework/data/adonet/ef/getting-started.md).  
  
 Entity Framework ile tümleştirin ve Visual Studio'da geliştirme daha kolay hale getirmek araçları kümesi sağlar. Daha fazla bilgi için [ADO.NET varlık veri modeli Araçları](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527). Bu konuda, Entity Framework tabanlı bir uygulama dağıtmak için belirli teknolojileri kullanmayı açıklamaz.  
  
 Visual Studio için dağıtma ve ClickOnce dağıtımı gibi dağıtmaya olanakları sağlar. Daha fazla bilgi için [dağıtımı uygulamaları ve bileşenleri](/visualstudio/deployment/deploying-applications-services-and-components) Visual Studio belgelerinde.  
  
 Entity Framework kullanan bir uygulamayı dağıttığınızda, aşağıdaki maddeler geçerlidir:  
  
-   Entity Framework, .NET Framework 3.5 Service Pack 1 ile (SP1) ile başlayan .NET Framework'ün bir bileşenidir. .NET Framework 3.5 SP1 veya sonraki bir sürümünü Entity Framework tabanlı bir uygulama dağıtırken yüklendiğinden emin olmalısınız.  
  
-   Varlık veri modeli Sihirbazı tarafından oluşturulan bir kavramsal model, bağlantı dizesini uygulama yapılandırma dosyasında oluşturulur. Model ve eşleme dosyalarını uygulama kaynakları eklenebilir veya çıkış dizinine kopyalanır. Varsayılan olarak, bunlar katıştırılmış uygulama kaynaklar olarak dağıtılır. Kullanım `Metadata Artifact Processing` özelliği varlık Tasarımcısı dosyasının bu seçeneklerden birini belirleyin. Daha fazla bilgi için [nasıl yapılır: Model kopyalayın ve çıkış dizinine dosyaları eşleme](https://msdn.microsoft.com/library/e2c9820f-1705-457e-9fdb-8b289f3179b4).  
  
-   Model ve eşleme (kavramsal şema tanım dili (CSDL), depo şeması tanım dili (SSDL) ve eşleme belirtimi dili (MSL) ifade edilir) bilgileri dağıtılan uygulamayla birlikte ve konumda emin olun bağlantı dizesi tarafından belirtilmiş. Daha fazla bilgi için [bağlantı dizeleri](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
-   Model ve eşleme bilgileri uygulama kaynakları olarak katıştırma yeniden derleyin ve kavramsal model her güncelleştirildiğinde uygulama dağıtmanız gerekir.  
  
-   Entity Framework, .NET Framework'ün bir bileşen olduğundan, .NET Framework lisans sözleşmenize göre izin verilen olarak uygulamanızla birlikte yeniden dağıtılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
- [Geliştirme ve Dağıtım Konuları](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
