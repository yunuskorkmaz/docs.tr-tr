---
title: Özel Etkinlikler Tasarlama ve Uygulama
description: Bu makale, bileşik etkinlikler oluşturarak veya yeni etkinlik türleri oluşturarak Workflow Foundation 'da özel etkinlikler oluşturmaya yönelik kaynaklar sağlar.
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 9c184bff9518bb5581f3bf4cd408db224736192b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419999"
---
# <a name="designing-and-implementing-custom-activities"></a>Özel Etkinlikler Tasarlama ve Uygulama
İçindeki özel etkinlikler [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] , sistem tarafından belirtilen etkinlikleri bileşik etkinliklere dağıtarak ya da, veya ' den türetilen yeni türler oluşturularak oluşturulur <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.NativeActivity> . Bu bölümde, her iki yöntemle de özel etkinliklerin nasıl oluşturulduğu açıklanmaktadır.  
  
> [!IMPORTANT]
> Varsayılan olarak özel etkinlikler, etkinlik adı ile basit bir dikdörtgen olarak iş akışı Tasarımcısı içinde görüntülenir. İş akışı tasarımcısında etkinliğinizin özel görsel temsilini sağlamak için özel bir tasarımcı da oluşturmanız gerekir. Daha fazla bilgi için bkz. [özel etkinlik tasarımcıları ve şablonları kullanma](using-custom-activity-designers-and-templates.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Etkinlik Yazma Seçenekleri](activity-authoring-options-in-wf.md)  
 ' De bulunan yazma stillerini açıklar [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] .  
  
 [Özel etkinlik kullanma](using-a-custom-activity.md)  
 Bir iş akışı projesine özel bir etkinliğin nasıl ekleneceğini açıklar.  
  
  [Zaman Uyumsuz Etkinlikler Oluşturma](creating-asynchronous-activities-in-wf.md)  
 Zaman uyumsuz etkinliklerin nasıl oluşturulduğunu açıklar.  
  
 [Etkinlik Doğrulamayı Yapılandırma](configuring-activity-validation.md)  
 Etkinlik doğrulamanın yürütmeden önce bir etkinliğin yapılandırmasındaki hataları tanımlamak ve raporlamak için nasıl kullanılabileceğini açıklar.  
  
 [Çalışma Zamanında Etkinlik Oluşturma](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 Kullanarak çalışma zamanında etkinliklerin nasıl oluşturulduğunu açıklar <xref:System.Activities.DynamicActivity> .  
  
 [İş Akışı Yürütme Özellikleri](workflow-execution-properties.md)  
 Bir etkinliğin ortamına bağlama özgü özellikler eklemek için iş akışı yürütme özelliklerinin nasıl kullanılacağını açıklar  
  
 [Etkinlik Temsilcileri Kullanma](using-activity-delegates.md)  
 Etkinlik temsilcileri içeren etkinliklerin nasıl yazılacağını ve kullanılacağını açıklar.
  
 [Etkinlik Uzantıları Kullanma](using-activity-extensions.md)  
 Etkinlik uzantılarının nasıl yazılacağını ve kullanılacağını açıklar.  
  
 [İş Akışından OData Akışları Kullanma](consuming-odata-feeds-from-a-workflow.md)  
 Bir iş akışından bir WCF veri hizmetini çağırmak için çeşitli yöntemler açıklanmıştır.  
  
 [Etkinlik Tanımı Kapsamı ve Görünürlüğü](activity-definition-scoping-and-visibility.md)  
 Etkinlik için veri kapsamını ve üye görünürlüğünü tanımlamaya yönelik seçenekleri ve kuralları açıklar.
