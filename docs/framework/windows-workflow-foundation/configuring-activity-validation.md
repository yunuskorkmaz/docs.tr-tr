---
description: 'Daha fazla bilgi edinin: etkinlik doğrulamasını yapılandırma'
title: Etkinlik Doğrulamayı Yapılandırma
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: 9e40842a18dd2afd9a5ec0104d66e8971d691b5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792758"
---
# <a name="configuring-activity-validation"></a>Etkinlik Doğrulamayı Yapılandırma

Etkinlik doğrulaması, etkinlik yazarlarının ve kullanıcıların, çalıştırmadan önce bir etkinliğin yapılandırmasındaki hataları tanımlamasına ve rapor etmesini sağlar. Windows Workflow Foundation (WF), aşağıdaki üç tür etkinlik doğrulaması sağlar:  
  
- `RequiredArgument` ve `OverloadGroup` öznitelikleri.  
  
- Kesinlik temelli kod tabanlı doğrulama.  
  
- Bildirime dayalı kısıtlamalar.  
  
 `RequiredArgument` ve `OverloadGroup` öznitelikleri, bir etkinlikte belirli bağımsız değişkenlerin gerekli olduğunu gösterir. Zorunlu kod tabanlı doğrulama, bir etkinliğin kendisi hakkında doğrulama sağlaması için basit bir yol sağlar ve bildirim temelli kısıtlamalar, etkinlik ve kapsayan iş akışıyla ilişkisi hakkında doğrulamayı etkinleştirir. Bir etkinlik doğrulama gereksinimlerine göre doğru yapılandırılmamışsa, doğrulama hataları ve uyarıları döndürülür. İçeren iş akışı, iş akışı Tasarımcısı kullanılarak oluşturulduysa, Tasarımcıda herhangi bir doğrulama hatası ve uyarı görüntülenir. İş akışı iş akışı Tasarımcısı dışında oluşturulduysa, iş akışı çağrıldığında herhangi bir doğrulama hatası döndürülür. İş akışının oluşturulma şeklinden bağımsız olarak, doğrulama hataları olan bir iş akışının yürütülmesine hiçbir şekilde izin verilmez. Bu bölüm, bu etkinlik doğrulaması türleri ve etkinlik doğrulamasının nasıl çağrılışını sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar](required-arguments-and-overload-groups.md)  
 `RequiredArgument`Ve `OverloadGroup` özniteliklerinin doğrulama sağlamak için nasıl kullanılacağını açıklar.  
  
 [Kesin Kod Temelli Doğrulama](imperative-code-based-validation.md)  
 <xref:System.Activities.CodeActivity>Ve tabanlı etkinlikler için kod tabanlı doğrulamanın nasıl kullanılacağını açıklar <xref:System.Activities.NativeActivity> .  
  
 [Bildirim Temelli Kısıtlamalar](declarative-constraints.md)  
 Karmaşık etkinlik doğrulaması sağlamak için bildirim temelli kısıtlamaların nasıl kullanılacağını açıklar.  
  
 [Etkinlik Doğrulamayı Çağırma](invoking-activity-validation.md)  
 Etkinlik doğrulamanın otomatik olarak ne zaman çağrılacağını ve doğrulamanın açıkça nasıl çağrılacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
  
## <a name="related-sections"></a>İlgili Bölümler
