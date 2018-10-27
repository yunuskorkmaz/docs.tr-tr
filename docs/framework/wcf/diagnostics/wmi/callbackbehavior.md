---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 38a38a71db2927d187ccdd93e5e364b0d4955373
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452618"
---
# <a name="callbackbehavior"></a>CallbackBehavior
CallbackBehavior  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 CallbackBehavior sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 CallbackBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Bir hizmeti bir çift yönlü oturumu kapattığında true olduğunda, oturumu otomatik olarak kapatılır.  
  
### <a name="concurrencymode"></a>ConcurrencyMode  
 Veri türü: dize  
Erişim türü: salt okunur  
  
 Hizmet bir iş parçacığı, birden çok iş parçacığı veya yeniden girilen çağrıları destekleyip desteklemediğini belirtir.  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Bilinmeyen serileştirme verilerinin gönderilip gönderilmeyeceğini belirten bir değeri.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Etkin olduğunda, geri çağırma özel durumları hakkında ayrıntıları hizmete döndürülen hatalara eklenir.  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Serileştirilmiş nesne içinde izin verilen öğe sayısı.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Geçerli eşitleme bağlamı yürütme iş parçacığı seçmek için kullanılıp kullanılmayacağını belirtir.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Sistem veya uygulama SOAP MustUnderstand üst bilgi işleme uygulayıp uygulamayacağını belirtir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
