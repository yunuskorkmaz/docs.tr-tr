---
description: 'Daha fazla bilgi edinin: CallbackBehavior'
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: fa9e403324afe818e247d1f751cce0ce7d5a6fb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757767"
---
# <a name="callbackbehavior"></a>CallbackBehavior

CallbackBehavior  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 CallbackBehavior sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 CallbackBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="automaticsessionshutdown"></a>Automaticsessionkapanıyor  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Doğru olduğunda, bir hizmet bir çift yönlü oturumu kapattığında oturum otomatik olarak kapatılır.  
  
### <a name="concurrencymode"></a>ConcurrencyMode  

 Veri türü: dize  
Erişim türü: salt okunurdur  
  
 Hizmetin bir iş parçacığını, birden çok iş parçacığını veya yer aldığı çağrıları destekleyip desteklemediğini belirtir.  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Bilinmeyen serileştirme verilerinin hatta gönderileceğini belirten bir değer.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Etkinleştirildiğinde, geri çağırmada özel durumlar hakkındaki ayrıntılar, hizmete döndürülen hatalara eklenir.  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Seri hale getirilen bir nesnede izin verilen en fazla öğe sayısı.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Yürütmenin iş parçacığını seçmek için geçerli eşitleme kapsamının kullanılıp kullanılmayacağını belirtir.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Sistemin ya da uygulamanın SOAP MustUnderstand üst bilgi işlemeyi zorunlu yapıp uygulamamadığını belirtir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.CallbackBehaviorAttribute>
