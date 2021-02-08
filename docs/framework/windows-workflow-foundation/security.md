---
description: 'Daha fazla bilgi edinin: güvenlik'
title: Güvenlik
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: 8f095292deac77c1c72cf87a93064569f7dab982
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798101"
---
# <a name="security"></a>Güvenlik

SQL Iş akışı örneği deposu, kalıcılık veritabanındaki örnek durum bilgilerine erişimi güvenli hale getirmek için aşağıdaki veritabanı güvenlik rollerini kullanır.  
  
- **System. Activities. Durableörneksistemi. InstanceStoreUsers**. Bu rol, örnekleri oluşturma, yükleme ve kaydetme konusunda yer alan saklı yordamlarda ortak görünümlere ve yürütme haklarına okuma ve yazma erişimi içerir.  
  
- **System. Activities. Durableörneksistemi. InstanceStoreObservers**. Bu rolün ortak görünümlere salt okuma erişimi vardır.  
  
- **System. Activities. Durableörnek oluşturma. WorkflowActivationUsers**. Bu rol, örnek etkinleştirme işleminde yer alan saklı yordamlara yönelik yürütme haklarına sahiptir. Örnek etkinleştirme hakkında daha fazla bilgi için bkz. [örnek etkinleştirme](instance-activation.md). Altında genel bir ana bilgisayarın (Windows Server AppFabric 'in barındırma özelliklerinin Iş akışı yönetim hizmeti gibi) çalıştırıldığı Kullanıcı hesabı, bu veritabanı rolüne eklenmelidir.  
  
 Windows Server App Fabric ile Kalıcılık mağazalarına yönelik güvenlik hakkında daha fazla bilgi için bkz. [App Fabric 'Te Kalıcılık depoları Için güvenlik yapılandırması](/previous-versions/appfabric/ff431727(v=azure.10))  
  
> [!CAUTION]
> Örnek deposundaki kendi örnek verilerine erişimi olan bir istemcinin aynı örnek deposundaki diğer tüm örneklere erişimi vardır. Örnek deposu, örnek düzeyinde güvenlik izinleri belirtmeyi desteklemiyor. Farklı depolara erişim sağlamak için ayrı örnek depoları oluşturmanız ve farklı grupları/kullanıcıları eşlemeniz gerekir.
