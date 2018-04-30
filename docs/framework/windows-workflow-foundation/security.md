---
title: Güvenlik
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f4a2204e091be1d1246041a2e961e9fd2b156780
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="security"></a>Güvenlik
SQL iş akışı örneği deposu Kalıcılık veritabanındaki örneği durumu bilgilere erişimi güvenli hale getirmek için aşağıdaki veritabanı güvenlik rollerini kullanır.  
  
-   **System.Activities.DurableInstancing.InstanceStoreUsers**. Bu rol okuma ve yazma erişimi ortak görünümler ve yürütme hakları oynayan oluşturma, yükleme ve kaydetme örnekleri saklı yordamlar.  
  
-   **System.Activities.DurableInstancing.InstanceStoreObservers**. Bu rol ortak görünümler salt okunur erişimi vardır.  
  
-   **System.Activities.DurableInstancing.WorkflowActivationUsers**. Bu rol örneği etkinleştirme işlemine dahil olan saklı yordamları yürütme haklarına sahip. Örnek etkinleştirme hakkında daha fazla bilgi için bkz: [örneği etkinleştirme](../../../docs/framework/windows-workflow-foundation/instance-activation.md). Kullanıcı hesabında genel ana bilgisayar (iş akışı yönetimi hizmetini gibi [!INCLUDE[dublin](../../../includes/dublin-md.md)]) çalıştığında bu veritabanı rolüne eklenmesi.  
  
 Windows Server App Fabric ile kalıcılığı depoları için güvenlik hakkında daha fazla bilgi için bkz: [App Fabric Kalıcılık depolarında için güvenlik yapılandırması](http://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  Örnek deposunda kendi örnek veri erişimi olan bir istemci aynı örnek deposunda tüm diğer örnekleri erişebilir. Örnek deposuna örnek düzeyinde belirten güvenlik izinleri desteklemez. Ayrı örneği deposu oluşturma ve farklı gruplar/farklı mağazalarının kullanıcılarının erişimini eşleme gerekir.
