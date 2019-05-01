---
title: Güvenlik
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: c27ac9cf41436332d560e11987e3ce4b68576895
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004698"
---
# <a name="security"></a>Güvenlik
SQL iş akışı örneği Store, örnek durum bilgilerini kalıcı veritabanındaki erişim güvenliğini sağlamak için aşağıdaki veritabanı güvenlik rollerini kullanır.  
  
- **System.Activities.DurableInstancing.InstanceStoreUsers**. Bu rol okuma ve yazma erişimi genel görünüm ve yürütme hakları katılan oluşturma, yükleme ve kaydetme örnekleri saklı yordamları.  
  
- **System.Activities.DurableInstancing.InstanceStoreObservers**. Bu rol, genel görünümlerini salt okunur erişimi vardır.  
  
- **System.Activities.DurableInstancing.WorkflowActivationUsers**. Bu rol örneği etkinleştirme işlemine dahil olan saklı yordamları yürütme hakkı vardır. Örnek etkinleştirme hakkında daha fazla bilgi için bkz: [örnek etkinleştirme](instance-activation.md). Kullanıcı hesabında genel bir ana bilgisayar (iş akışı yönetimi hizmeti, gibi [!INCLUDE[dublin](../../../includes/dublin-md.md)]) çalışır, bu veritabanı rolüne eklenmelidir.  
  
 Windows Server App Fabric ile Kalıcılık depoları için güvenlik hakkında daha fazla bilgi için bkz. [App Fabric Kalıcılık depoları için güvenlik yapılandırması](https://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  Örnek deposunda kendi örnek veri erişimi olan bir istemci aynı örnek depodaki tüm diğer örneklerden erişebilir. Örnek deposuna örnek düzeyinde belirten güvenlik izinleri desteklemez. Farklı bir örnek deposu oluşturma ve erişimi için farklı mağazalarda farklı gruplar/kullanıcılar eşleme gerekir.
