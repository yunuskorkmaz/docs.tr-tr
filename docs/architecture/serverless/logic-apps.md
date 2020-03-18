---
title: Azure Mantık Uygulamaları - Sunucusuz uygulamalar
description: Azure Logic Apps, bulut hizmetleri ve şirket içi sistemler arasında uygulamaları ve verileri tümleştiren otomatik ölçeklenebilir iş akışları oluşturmayı sağlar.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676753"
---
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Azure Logic Apps,](https://docs.microsoft.com/azure/logic-apps) bulut hizmetleri ve şirket içi sistemler arasında uygulamaları ve verileri tümleştirmek için otomatik iş akışları oluşturmak için sunucusuz bir altyapı sağlar. Görsel bir tasarımcı kullanarak iş akışları oluşturursunuz. Olaylara veya zamanlayıcılara dayalı iş akışlarını tetikleyebilir ve tümleştirme uygulamalarına konektörleri kullanabilir ve işletmeler arası (B2B) iletişimi kolaylaştırabilirsiniz. Logic Apps, Azure Fonksiyonları ile sorunsuz bir şekilde tümleşir.

![Azure Logic Apps logosu](./media/logic-apps-logo.png)

Logic Apps, bulut hizmetlerinizi (işlevler gibi) bulut kaynaklarıyla (kuyruklar ve veritabanları gibi) bağlamaktan daha fazlasını yapabilir. Ayrıca şirket içi ağ geçidi ile şirket içi iş akışları düzenleyebilirsiniz. Örneğin, iş akışınızdaki bulut tabanlı bir olaya veya koşullu mantığa yanıt olarak şirket içi SQL depolanan yordamı tetiklemek için Mantık Uygulamasını kullanabilirsiniz. [Azure Şirket Içi Veri Ağ Geçidi ile şirket içi veri kaynaklarına bağlanma](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)hakkında daha fazla bilgi edinin.

![Logic Apps mimarisi](./media/logic-apps-architecture.png)

Azure İşlevleri gibi, Logic App iş akışlarını bir tetikleyiciyle başlatırsınız. Seçim yapabileceğiniz birçok tetikleyici vardır. Aşağıdaki yakalama, mevcut yüzlerce daha popüler olanlardan sadece birkaçını gösterir.

![Logic Apps tetikleyicileri](./media/logic-app-triggers.png)

Uygulama tetiklendikten sonra, adımları, döngüleri, koşulları ve eylemleri oluşturmak için görsel tasarımcıyı kullanabilirsiniz. Önceki adımda alınan tüm veriler sonraki adımlarda kullanmanız için kullanılabilir. Aşağıdaki iş akışı URL'leri bir CosmosDB veritabanından yükler. Bu twitter'da onlar `t.co` için daha sonra arama bir dizi olanlar bulur. Karşılık gelen tweetleri bulursa, bir işlevi arayarak belgeleri ilgili tweetlerle güncelleştirir.

![Mantık Uygulaması iş akışı](./media/logic-app-workflow.png)

Logic Apps panosu, iş akışlarınızı çalıştırma geçmişini ve her çalıştırmanın başarıyla tamamlanıp tamamlanmadığını gösterir. Belirli bir çalıştırmaya gidebilir ve her adımda kullanılan verileri sorun giderme için inceleyebilirsiniz. Logic Apps ayrıca, edinebileceğiniz varolan şablonları da sağlar ve karmaşık kurumsal iş akışları için uygundur.

Daha fazla bilgi için [Azure Mantık Uygulamaları'na](https://docs.microsoft.com/azure/logic-apps)bakın.

>[!div class="step-by-step"]
>[Önceki](application-insights.md)
>[Sonraki](event-grid.md)
