---
title: Çalıştırılabilir Örnekleri Algılama Dönemi
ms.date: 03/30/2017
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
ms.openlocfilehash: aefde2726bb2ccc15f9e68009e5e141602b13b10
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245776"
---
# <a name="runnable-instances-detection-period"></a>Çalıştırılabilir Örnekleri Algılama Dönemi

SQL Iş akışı örneği deposu, düzenli aralıklarla uyandığı ve kalıcılık veritabanındaki çalıştırılabilir veya etkinleştirilebilir örneklerini algılayan bir iç görev çalıştırır. SQL Iş akışı örneği deposunun **çalıştırılabilir örnek algılama dönemi** ÖZELLIĞI, SQL Iş akışı örneği deposunun, önceki algılama döngüsünden sonra kalıcılık veritabanında herhangi bir çalıştırılabilir veya etkinleştirilebilir iş akışı örneğini algılamak için bir algılama görevi çalıştırması için geçen süreyi belirtir.  
  
 Bu özellik için daha kısa bir zaman aralığı ayarlandığında, bir iş akışı örneğiyle ilişkili bir zamanlayıcı süresi ve olay sinyali ve örneğin sonraki yüklemesi arasındaki süre azaltılır. Ancak, aynı zamanda bir konaktaki işleme yükünü artırır ve dayanıklı zamanlayıcılar ile/veya ana bilgisayar hatalarının nadir olduğu senaryolarda istenmeyebilir. Özelliğin türü TimeSpan ve özelliğin değeri şu biçimdedir: ss: DD: ss. Bu özellik için en düşük değer 00:00:01 ' dir. Özelliği için varsayılan değer 00:00:05 ' dir.  
  
 Runactivation ve etkinleştirilebilir iş akışı örneklerinin algılanması ve etkinleştirilmesi hakkında daha fazla bilgi için bkz. [örnek etkinleştirme](instance-activation.md).
