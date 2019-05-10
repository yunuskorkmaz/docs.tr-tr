---
title: Güvenlik
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: d82ad52dd24dbfcb66887693563b08c995baa63a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619492"
---
# <a name="security"></a>Güvenlik
SQL iş akışı örneği Store, örnek durum bilgilerini kalıcı veritabanındaki erişim güvenliğini sağlamak için aşağıdaki veritabanı güvenlik rollerini kullanır.  
  
- **System.Activities.DurableInstancing.InstanceStoreUsers**. Bu rol okuma ve yazma erişimi genel görünüm ve yürütme hakları katılan oluşturma, yükleme ve kaydetme örnekleri saklı yordamları.  
  
- **System.Activities.DurableInstancing.InstanceStoreObservers**. Bu rol, genel görünümlerini salt okunur erişimi vardır.  
  
- **System.Activities.DurableInstancing.WorkflowActivationUsers**. Bu rol örneği etkinleştirme işlemine dahil olan saklı yordamları yürütme hakkı vardır. Örnek etkinleştirme hakkında daha fazla bilgi için bkz: [örnek etkinleştirme](instance-activation.md). Kullanıcı hesabında genel bir ana bilgisayar (iş akışı yönetimi hizmeti, gibi [!INCLUDE[dublin](../../../includes/dublin-md.md)]) çalışır, bu veritabanı rolüne eklenmelidir.  
  
 Windows Server App Fabric ile Kalıcılık depoları için güvenlik hakkında daha fazla bilgi için bkz. [App Fabric Kalıcılık depoları için güvenlik yapılandırması](https://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  Örnek deposunda kendi örnek veri erişimi olan bir istemci aynı örnek depodaki tüm diğer örneklerden erişebilir. Örnek deposuna örnek düzeyinde belirten güvenlik izinleri desteklemez. Farklı bir örnek deposu oluşturma ve erişimi için farklı mağazalarda farklı gruplar/kullanıcılar eşleme gerekir.
