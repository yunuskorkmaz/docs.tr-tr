---
title: Güvenlik
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: cbfb82c2db329725d3445e1a88b54e01d5813f36
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348401"
---
# <a name="security"></a>Güvenlik
SQL iş akışı örneği Store, örnek durum bilgilerini kalıcı veritabanındaki erişim güvenliğini sağlamak için aşağıdaki veritabanı güvenlik rollerini kullanır.  
  
- **System.Activities.DurableInstancing.InstanceStoreUsers**. Bu rol okuma ve yazma erişimi genel görünüm ve yürütme hakları katılan oluşturma, yükleme ve kaydetme örnekleri saklı yordamları.  
  
- **System.Activities.DurableInstancing.InstanceStoreObservers**. Bu rol, genel görünümlerini salt okunur erişimi vardır.  
  
- **System.Activities.DurableInstancing.WorkflowActivationUsers**. Bu rol örneği etkinleştirme işlemine dahil olan saklı yordamları yürütme hakkı vardır. Örnek etkinleştirme hakkında daha fazla bilgi için bkz: [örnek etkinleştirme](instance-activation.md). Genel bir ana bilgisayar (örneğin, Windows Server AppFabric barındırma özellikleri iş akışı yönetimi hizmeti) altında çalıştığı hesabın bu veritabanı rolüne eklenmelidir.  
  
 Windows Server App Fabric ile Kalıcılık depoları için güvenlik hakkında daha fazla bilgi için bkz. [App Fabric Kalıcılık depoları için güvenlik yapılandırması](https://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  Örnek deposunda kendi örnek veri erişimi olan bir istemci aynı örnek depodaki tüm diğer örneklerden erişebilir. Örnek deposuna örnek düzeyinde belirten güvenlik izinleri desteklemez. Farklı bir örnek deposu oluşturma ve erişimi için farklı mağazalarda farklı gruplar/kullanıcılar eşleme gerekir.
