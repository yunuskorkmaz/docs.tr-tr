---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 2755ac4f365536366b41e743110ce494063a5ecc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486966"
---
# <a name="callbackbehavior"></a>CallbackBehavior
CallbackBehavior  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 CallbackBehavior sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 CallbackBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Bir hizmet çift yönlü oturumu kapattığında doğru olduğunda, oturumu otomatik olarak kapatılır.  
  
### <a name="concurrencymode"></a>ConcurrencyMode  
 Veri türü: dize  
Erişim türüne: salt okunur  
  
 Hizmet bir iş parçacığı, birden çok iş parçacığı veya desteklemeyeceğini aramalar destekleyip desteklemediğini belirtir.  
  
### <a name="ignoreextensiondataobject"></a>ignoreExtensionDataObject  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Bilinmeyen seri hale getirme verilerinin gönderilip gönderilmeyeceğini belirten bir değer.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Etkinleştirildiğinde, hakkındaki geri arama özel durumların ayrıntıları hizmete döndürülen hatalara eklenir.  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Serileştirilmiş nesne içinde izin verilen öğe maksimum sayısı.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Geçerli eşitleme bağlamı yürütme iş parçacığı seçmek için kullanılıp kullanılmayacağını belirtir.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Sistem veya uygulama SOAP MustUnderstand üstbilgi işlemeyi zorunlu olup olmadığını belirtir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
