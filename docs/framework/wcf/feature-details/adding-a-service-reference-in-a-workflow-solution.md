---
title: Bir İş Akışı Çözümüne Hizmet Başvurusu Ekleme
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 9dcbf779d948f6d295c2a23f5a09efc5ac989cdd
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082870"
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>Bir İş Akışı Çözümüne Hizmet Başvurusu Ekleme

Bir iş akışı uygulamasında bir hizmet başvurusu ekleme biraz normal WCF uygulaması farklı şekilde çalışır. Seçtiğinizde, **Ekle > Hizmet başvurusu** ve hizmetin URL'sini belirtin, meta veriler indirilir ve özel etkinlikler WCF hizmeti veya bir başvuru eklediğiniz WCF iş akışı hizmeti çağırmak olanak tanıyan oluşturulur. Oluşturulan etkinlikleri yerleşik şekilde hizmet başvurusunu ekledikten sonra çözümü yeniden oluşturun. Bunlar, sonra iş akışı Tasarımcısı araç kutusunda görünür. Bununla birlikte, içinde bir iş akışı çözümüne hizmet başvurusu ekliyorsanız bu yalnızca çalışacağını unutmayın. Aşağıdaki web yayınını, diğer proje türlerinin bir hizmet başvurusu ekleme işlemi gösterilmektedir: [Web projesinde bir iş akışından bir WCF Hizmeti çağırma](https://go.microsoft.com/fwlink/?LinkId=207725).

Aynı işlem adı içeren hizmetler iki veya daha fazla hizmet başvuruları ekleme, bir sorun neden olur. Oluşturulan etkinlikleri yalnızca ilk hizmet işlemini çağırır. Farklı veya oluşturulan her etkinlik uç nokta yapılandırma adını değiştirmek için bu sorunu yeniden adlandırma hizmet işlemleri çalışmak için.

## <a name="see-also"></a>Ayrıca Bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Nasıl yapılır: Başka Bir İş Akışı Hizmetine Çağrı Yapan Bir İş Akışı Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)
- [Web projesinde bir iş akışından bir WCF Hizmeti çağırma](https://go.microsoft.com/fwlink/?LinkId=207725)
