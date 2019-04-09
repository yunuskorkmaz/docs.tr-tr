---
title: Dağıtım konuları (varlık çerçevesi)
ms.date: 03/30/2017
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
ms.openlocfilehash: 7ab3827a9f2072f6f4b0c34f3801ee5dff2821d3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199602"
---
# <a name="deployment-considerations-entity-framework"></a>Dağıtım konuları (varlık çerçevesi)
Bu konuda, veri erişimi için ADO.NET Entity Framework kullanan uygulamaları dağıtma hakkında bilgi sağlar. Varlık çerçevesi hakkında daha fazla bilgi için bkz: [Başlarken](../../../../../docs/framework/data/adonet/ef/getting-started.md).  
  
 Entity Framework ile tümleştirin ve Visual Studio'da geliştirme daha kolay hale getirmek araçları kümesi sağlar. Daha fazla bilgi için [ADO.NET varlık veri modeli Araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)). Bu konuda, Entity Framework tabanlı bir uygulama dağıtmak için belirli teknolojileri kullanmayı açıklamaz.  
  
 Visual Studio için dağıtma ve ClickOnce dağıtımı gibi dağıtmaya olanakları sağlar. Daha fazla bilgi için [dağıtımı uygulamaları ve bileşenleri](/visualstudio/deployment/deploying-applications-services-and-components) Visual Studio belgelerinde.  
  
 Entity Framework kullanan bir uygulamayı dağıttığınızda, aşağıdaki maddeler geçerlidir:  
  
-   Entity Framework, .NET Framework 3.5 Service Pack 1 ile (SP1) ile başlayan .NET Framework'ün bir bileşenidir. .NET Framework 3.5 SP1 veya sonraki bir sürümünü Entity Framework tabanlı bir uygulama dağıtırken yüklendiğinden emin olmalısınız.  
  
-   Varlık veri modeli Sihirbazı tarafından oluşturulan bir kavramsal model, bağlantı dizesini uygulama yapılandırma dosyasında oluşturulur. Model ve eşleme dosyalarını uygulama kaynakları eklenebilir veya çıkış dizinine kopyalanır. Varsayılan olarak, bunlar katıştırılmış uygulama kaynaklar olarak dağıtılır. Kullanım `Metadata Artifact Processing` özelliği varlık Tasarımcısı dosyasının bu seçeneklerden birini belirleyin. Daha fazla bilgi için [nasıl yapılır: Model kopyalayın ve çıkış dizinine dosyaları eşleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716709(v=vs.100)).  
  
-   Model ve eşleme (kavramsal şema tanım dili (CSDL), depo şeması tanım dili (SSDL) ve eşleme belirtimi dili (MSL) ifade edilir) bilgileri dağıtılan uygulamayla birlikte ve konumda emin olun bağlantı dizesi tarafından belirtilmiş. Daha fazla bilgi için [bağlantı dizeleri](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
-   Model ve eşleme bilgileri uygulama kaynakları olarak katıştırma yeniden derleyin ve kavramsal model her güncelleştirildiğinde uygulama dağıtmanız gerekir.  
  
-   Entity Framework, .NET Framework'ün bir bileşen olduğundan, .NET Framework lisans sözleşmenize göre izin verilen olarak uygulamanızla birlikte yeniden dağıtılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
- [Geliştirme ve Dağıtım Konuları](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
