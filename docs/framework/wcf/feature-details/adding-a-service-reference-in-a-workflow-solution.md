---
title: Bir İş Akışı Çözümüne Hizmet Başvurusu Ekleme
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 8f1fa4604f1a1873c7063ec3c9dccf08bd0aa0ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549047"
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>Bir İş Akışı Çözümüne Hizmet Başvurusu Ekleme

Bir iş akışı uygulamasında bir hizmet başvurusu ekleme biraz normal WCF uygulaması farklı şekilde çalışır. Seçtiğinizde, **Ekle > Hizmet başvurusu** ve hizmetin URL'sini belirtin, meta veriler indirilir ve özel etkinlikler WCF hizmeti veya bir başvuru eklediğiniz WCF iş akışı hizmeti çağırmak olanak tanıyan oluşturulur. Oluşturulan etkinlikleri yerleşik şekilde hizmet başvurusunu ekledikten sonra çözümü yeniden oluşturun. Bunlar, sonra iş akışı Tasarımcısı araç kutusunda görünür. Bununla birlikte, içinde bir iş akışı çözümüne hizmet başvurusu ekliyorsanız bu yalnızca çalışacağını unutmayın. Aşağıdaki web yayınını, diğer proje türlerinin bir hizmet başvurusu ekleme işlemi gösterilmektedir: [Bir WCF hizmeti bir Web projesi bir iş akışında arama](https://go.microsoft.com/fwlink/?LinkId=207725).

Aynı işlem adı içeren hizmetler iki veya daha fazla hizmet başvuruları ekleme, bir sorun neden olur. Oluşturulan etkinlikleri yalnızca ilk hizmet işlemini çağırır. Farklı veya oluşturulan her etkinlik uç nokta yapılandırma adını değiştirmek için bu sorunu yeniden adlandırma hizmet işlemleri çalışmak için.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Web projesinde bir iş akışından bir WCF Hizmeti çağırma](https://go.microsoft.com/fwlink/?LinkId=207725)
