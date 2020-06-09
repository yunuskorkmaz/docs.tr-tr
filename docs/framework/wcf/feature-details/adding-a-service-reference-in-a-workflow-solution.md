---
title: Bir İş Akışı Çözümüne Hizmet Başvurusu Ekleme
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 577026249e00b528cf5c6e7ccd9527e02cb22a28
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597676"
---
# <a name="add-a-service-reference-in-a-workflow-solution"></a>Bir Iş akışı çözümüne hizmet başvurusu ekleme

Bir iş akışı uygulamasına hizmet başvurusu eklemek, normal bir WCF uygulamasından biraz farklı çalışır. **Add**  >  **Hizmet başvurusu** Ekle ' yi seçtiğinizde ve hizmetin URL 'sini belirttiğinizde, meta veriler indirilir ve bu WCF hizmetini veya WCF iş akışı hizmetini çağırabilmeniz için özel etkinlikler oluşturulur. Hizmet başvurusu ekledikten sonra, oluşturulan etkinliklerin oluşturulması için çözümü yeniden derleyin. Daha sonra iş akışı Tasarımcısı araç kutusunda görünürler. Bu, yalnızca bir iş akışı çözümüne hizmet başvurusu ekliyorsanız çalışır. Aşağıdaki Web cast, diğer proje türlerinde bir hizmet başvurusunun nasıl ekleneceğini gösterir: bir [Web projesindeki Iş akışından BIR WCF hizmeti çağırma](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).

Aynı işlem adını içeren hizmetlere iki veya daha fazla hizmet başvurusu eklemek soruna neden olur. Oluşturulan etkinlikler yalnızca ilk hizmet işlemini çağırır. Bu sorunu geçici olarak çözmek için, hizmet işlemlerini farklı olacak şekilde yeniden adlandırın veya oluşturulan her etkinlik içindeki uç nokta yapılandırma adını değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](workflow-services.md)
- [Bir Web projesindeki Iş akışından bir WCF hizmetini çağırma](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
