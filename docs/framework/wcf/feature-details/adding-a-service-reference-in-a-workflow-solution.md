---
title: Bir İş Akışı Çözümüne Hizmet Başvurusu Ekleme
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 7197ae991207efd60ea398794c7c23f427f6b0cc
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964210"
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>Bir İş Akışı Çözümüne Hizmet Başvurusu Ekleme

Bir iş akışı uygulamasına hizmet başvurusu eklemek, normal bir WCF uygulamasından biraz farklı çalışır. **> hizmet başvurusu Ekle** ' yi seçtiğinizde ve hizmetin URL 'sini belirttiğinizde, meta veriler indirilir ve bir başvuru eklediğiniz WCF HIZMETINI veya WCF iş akışı hizmetini çağırabilmeniz için özel etkinlikler oluşturulur. Hizmet başvurusu ekledikten sonra, oluşturulan etkinliklerin oluşturulması için çözümü yeniden derleyin. Daha sonra iş akışı Tasarımcısı araç kutusunda görünürler. Bununla birlikte, bunun yalnızca bir iş akışı çözümüne hizmet başvurusu ekliyorsanız iş olacağını unutmayın. Aşağıdaki Web cast, diğer proje türlerinde bir hizmet başvurusunun nasıl ekleneceğini gösterir: bir [Web projesindeki Iş akışından BIR WCF hizmeti çağırma](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).

Aynı işlem adını içeren hizmetlere iki veya daha fazla hizmet başvurusu eklemek soruna neden olur. Oluşturulan etkinlikler yalnızca ilk hizmet işlemini çağırır. Bu sorunu geçici olarak çözmek için hizmet işlemlerini farklı olacak şekilde yeniden adlandırın veya oluşturulan her etkinlik içindeki uç nokta yapılandırması adını değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Bir Web projesindeki Iş akışından bir WCF hizmetini çağırma](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
