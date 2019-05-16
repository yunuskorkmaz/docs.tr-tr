---
title: Azure Logic Apps - sunucusuz uygulamalar
description: Azure Logic Apps uygulamaları tümleştirin otomatik ölçeklenebilir iş akışlarını oluşturmayı etkinleştirin ve verileri bulut Hizmetleri ve şirket içi sistemler.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638793"
---
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) uygulamaları ve bulut hizmetleri arasında verileri tümleştirmek için otomatik iş akışları oluşturmak için sunucusuz bir altyapı sağlar ve şirket içi sistemler. Bir görsel tasarımcı kullanarak iş akışları oluşturun. Olayları veya süreölçerler ve Dengeleme bağlayıcılar tümleştirme uygulamalara dayalı iş akışlarını tetikleyin ve işletmeden işletmeye (B2B) iletişimi kolaylaştırır. Logic Apps, Azure işlevleri ile sorunsuz şekilde entegre olur.

![Azure Logic Apps logosu](./media/logic-apps-logo.png)

Logic Apps, bulut hizmetlerinizde (gibi işlevler) bağlamanız yeterlidir birden fazla (kuyruklar ve veritabanları gibi) bulut kaynakları ile yapabilirsiniz. Şirket içi ağ geçidi ile şirket içi iş akışları da düzenleyebilirsiniz. Örneğin, mantıksal uygulama, bulut tabanlı bir olaya yanıt olarak bir şirket içi SQL saklı yordamı veya koşullu mantığı, iş akışı tetiklemek için kullanabilirsiniz. Daha fazla bilgi edinin [Azure şirket içi veri ağ geçidi ile şirket içi veri kaynaklarına bağlanma](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).

![Logic Apps mimarisi](./media/logic-apps-architecture.png)

Azure işlevleri gibi bir tetikleyici ile mantıksal uygulama iş akışlarını başlatabilir. Aralarından seçim yapabileceğiniz birçok tetikleyici vardır. Aşağıdaki yakalama daha popüler olanları tanesi kullanılabilir olan yüzlerce birkaçı gösterilir.

![Mantıksal uygulama Tetikleyicileri](./media/logic-app-triggers.png)

Uygulama tetiklendikten sonra görsel tasarımcı adımları, döngüler, koşullar ve Eylemler oluşturmak için kullanabilirsiniz. Bir önceki adımda alınan tüm veriler, sonraki adımlarda kullanılacağı için kullanılabilir. Aşağıdaki iş akışı URL'leri CosmosDB veritabanından yükler. Çok sayıda oluşturduklarıyla bulduğu `t.co` kendileri için Twitter'da arama yapar. İlgili tweetleri bulur, belgeleri ile ilgili tweetleri bir işlev çağırarak güncelleştirir.

![Mantıksal uygulama iş akışı](./media/logic-app-workflow.png)

Logic Apps Panosu, akışlarınızı ve her çalışıp tamamlanmış başarılı ya da başarısız çalıştırma geçmişini gösterir. Verilen tüm run gidin ve sorun giderme için her adımı tarafından kullanılan verileri inceleyin. Logic Apps ayrıca düzenleyebilir ve karışık kurumsal iş akışları için uygun olan mevcut şablonları sağlar.

Daha fazla bilgi için bkz. [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).

>[!div class="step-by-step"]
>[Önceki](application-insights.md)
>[İleri](event-grid.md)
