---
title: İş akışı tasarım deneyimini özelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 87b49b025cfb27812933511b76c5a024cde4995a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680318"
---
# <a name="customizing-the-workflow-design-experience"></a>İş akışı tasarım deneyimini özelleştirme

Özel etkinlikler tasarlama ve yeniden barındırma senaryolarında [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] içinde önemli ölçüde basitleştirilmiştir [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. Geliştirme ve dağıtım artık daha kolay ve daha esnektir. Anahtar altyapısal değişikliği, Windows Presentation Foundation (WPF) üzerine yeni etkinlik Tasarımcısı programlama modeli yerleşik olarak eklenmesidir. Bu etkinlik tasarımcıları bildirimli olarak tanımlamanızı ve barındırma olanağı verir [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] diğer uygulamalarda ile karşılaştırmalı kolay. Yeniden barındırma, IntelliSense ya da bir Basitleştirilmiş ifade etki alanı desteklemek için özel ifade düzenleyicisini geliştirilebilir. Windows Communication Foundation (WCF) ile tümleştirme, iş akışı hizmet kullanımı ile daha sorunsuz hale geldi. Özel Etkinlik tasarımcıları ve modeli öğe ağacı, tasarım zamanı yeniden barındırılan iş akışı tasarımcıları deneyimler geliştirmek için kullanılabilir.

## <a name="in-this-section"></a>Bu Bölümde

 [Özel Etkinlik Tasarımcıları ve Şablonları Kullanma](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)

 Yeni özel etkinlik tasarımcıları ve şablonları nasıl oluşturulacağını açıklar.

 [İş Akışı Tasarımcısını Yeniden Barındırma](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)

 Yeniden barındırma açıklar [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] Visual Studio ve doğrulama hataları görüntülemek nasıl dışında.

 [Özel İfade Düzenleyicisi Kullanma](../../../docs/framework/windows-workflow-foundation/using-a-custom-expression-editor.md)

 Visual Studio 2010 dışında yeniden barındırılan iş akışı tasarımcıları ile kullanılacak özel ifade düzenleyicisini uygulanacağını açıklar.

## <a name="reference"></a>Başvuru

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Workflow Foundation’ı Genişletme](../../../docs/framework/windows-workflow-foundation/extend.md)
- [Tasarımcı](../../../docs/framework/windows-workflow-foundation/samples/designer.md)
- [Özel Etkinlik Tasarımcıları](../../../docs/framework/windows-workflow-foundation/samples/custom-activity-designers.md)
- [Tasarımcıyı Yeniden Barındırma](../../../docs/framework/windows-workflow-foundation/samples/designer-rehosting.md)