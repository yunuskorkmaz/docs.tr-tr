---
title: Azure Logic Apps-sunucusuz uygulamalar
description: Azure Logic Apps bulut hizmetleri ve şirket içi sistemler arasında uygulamaları ve verileri tümleştiren otomatik ölçeklenebilir iş akışları oluşturmayı etkinleştirin.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 11fdf5b5f176eb0d66eee6dde7638d3eae1e1f55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171851"
---
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Azure Logic Apps](/azure/logic-apps) , bulut hizmetleri ve şirket içi sistemler arasında uygulama ve verileri bütünleştirmek üzere otomatik iş akışları oluşturmak için sunucusuz bir altyapı sağlar. Bir görsel tasarımcı kullanarak iş akışları oluşturursunuz. İş akışlarını olaylara veya zamanlayıcılar temelinde tetikleyip, uygulamaları tümleştirmek ve işletmeler arası (B2B) iletişimini kolaylaştırmak için bağlayıcılardan yararlanabilirsiniz. Logic Apps, Azure Işlevleri ile sorunsuz bir şekilde tümleşir.

![Azure Logic Apps logosu](./media/logic-apps-logo.png)

Logic Apps, bulut hizmetlerinizi (işlevler gibi) bulut kaynaklarıyla (kuyruklar ve veritabanları gibi) yalnızca bağlama özelliğinden daha fazlasını yapabilir. Şirket içi ağ geçidi ile şirket içi iş akışlarını da düzenleyebilirsiniz. Örneğin, mantıksal uygulamayı kullanarak bir şirket içi SQL saklı yordamını, iş akışınızda bulut tabanlı bir olaya veya koşullu mantığa yanıt olarak tetikleyebilirsiniz. [Azure şirket Içi veri ağ geçidi ile şirket içi veri kaynaklarına bağlanma](/azure/analysis-services/analysis-services-gateway)hakkında daha fazla bilgi edinin.

![Logic Apps mimarisi](./media/logic-apps-architecture.png)

Azure Işlevleri gibi, mantıksal uygulama iş akışlarını bir tetikleyici ile başlatılersiniz. Aralarından seçim yapabileceğiniz birçok tetikleyici vardır. Aşağıdaki yakalama, mevcut yüzlerce yüzlerce daha popüler olanlarından yalnızca birkaçını gösterir.

![Logic Apps tetikleyicileri](./media/logic-app-triggers.png)

Uygulama tetiklendikten sonra, adımları, döngüleri, koşulları ve eylemleri oluşturmak için görsel tasarımcı 'yı kullanabilirsiniz. Önceki adımda alınan tüm veriler sonraki adımlarda kullanabileceğiniz şekilde kullanılabilir. Aşağıdaki iş akışı, CosmosDB veritabanından URL 'Leri yükler. `t.co`Daha sonra Twitter 'da bu ana bilgisayarı arar. Bunlara karşılık gelen fazla yer bulunursa, bir işlevi çağırarak ilgili alanı bulunan belgeleri güncelleştirir.

![Mantıksal uygulama iş akışı](./media/logic-app-workflow.png)

Logic Apps panosu, iş akışlarınızı çalıştırmanın geçmişini ve her çalıştırmanın başarıyla tamamlanıp tamamlanmadığını gösterir. Belirli bir çalıştırmaya gidebilir ve sorun giderme için her adım tarafından kullanılan verileri inceleyebilirsiniz. Logic Apps Ayrıca, düzenleyebileceğiniz ve karmaşık kurumsal iş akışları için uygun olan şablonları da sağlar.

Daha fazla bilgi için bkz. [Azure Logic Apps](/azure/logic-apps).

>[!div class="step-by-step"]
>[Önceki](application-insights.md) 
> [Sonraki](event-grid.md)
