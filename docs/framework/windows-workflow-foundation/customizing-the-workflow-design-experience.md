---
title: İş Akışı Tasarım Deneyimini Özelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 41be55391ae9481f6c2e4feb76443f7fb676b69d
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141930"
---
# <a name="customizing-the-workflow-design-experience"></a>İş Akışı Tasarım Deneyimini Özelleştirme

Özel etkinlikler tasarlama ve [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] yeniden barındırma için senaryolar, .NET Framework 4 ' te büyük ölçüde basitleştirilmiştir. Geliştirme ve dağıtım artık daha kolay ve daha esnektir. Key altyapısal değişikliği, yeni etkinlik Tasarımcısı programlama modelinin Windows Presentation Foundation (WPF) üzerine kurulmuştur. Bu sayede etkinlik tasarımcılarını bildirimli olarak tanımlayabilir ve diğer uygulamalardaki [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] karşılaştırıcı kolay bir şekilde yeniden barındırabilirsiniz. Yeniden barındırma sırasında, IntelliSense veya Basitleştirilmiş bir ifade etki alanını desteklemek için özel bir ifade Düzenleyicisi geliştirilebilir. Windows Communication Foundation (WCF) tümleştirmesi, iş akışı hizmetleri kullanımıyla daha sorunsuz hale geldi. Özel etkinlik tasarımcıları ve model öğesi ağacı, yeniden barındırılan iş akışı tasarımcılarındaki tasarım zamanı deneyimlerini geliştirmek için kullanılabilir.

## <a name="in-this-section"></a>Bu Bölümde

 [Özel Etkinlik Tasarımcıları ve Şablonları Kullanma](using-custom-activity-designers-and-templates.md)

 Yeni özel etkinlik tasarımcıları ve şablonlarının nasıl oluşturulduğunu açıklar.

 [İş Akışı Tasarımcısını Yeniden Barındırma](rehosting-the-workflow-designer.md)

 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] Visual Studio dışında nasıl yeniden barındırılacağını ve doğrulama hatalarının nasıl görüntüleneceğini açıklar.

 [Özel İfade Düzenleyicisi Kullanma](using-a-custom-expression-editor.md)

 Visual Studio 2010 dışında barındırılan iş akışı tasarımcıları ile kullanmak için özel bir ifade düzenleyicisinin nasıl uygulanacağını açıklar.

## <a name="reference"></a>Başvuru

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Workflow Foundation’ı Genişletme](extend.md)
- [Tasarımcı](./samples/designer.md)
- [Özel Etkinlik Tasarımcıları](./samples/custom-activity-designers.md)
- [Tasarımcıyı Yeniden Barındırma](./samples/designer-rehosting.md)
