---
title: Uç Noktası
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 5d597e9e029cec3552c94b47a64dfbf36d933e67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487652"
---
# <a name="endpoint"></a>Uç Noktası
Uç Noktası  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 Uç nokta sınıfı aşağıdaki yöntemi tanımlar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetOperationCounterInstanceName](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|İşlemi performans sayacı örneği adını alır.|  
  
## <a name="properties"></a>Özellikler  
 Uç nokta sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="address"></a>Adres  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Uç nokta adresi içeren bir URI.  
  
### <a name="addressheaders"></a>AddressHeaders  
 Veri türü: dize dizisi  
  
 Erişim türüne: salt okunur  
  
 Bu uç noktaya eklenen adres üstbilgileri koleksiyonu.  
  
### <a name="addressidentity"></a>AddressIdentity  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bitiş noktasının kimliğini.  
  
### <a name="appdomainid"></a>AppDomainId  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Uç noktayı barındıran appdomain kimliği.  
  
### <a name="behaviors"></a>Davranışlar  
 Veri türü: davranış dizisi  
  
 Erişim türüne: salt okunur  
  
 Bu bitiş noktası tarafından uygulanan davranış koleksiyonu.  
  
### <a name="binding"></a>Bağlama  
 Veri türü: bağlama  
  
 Erişim türüne: salt okunur  
  
 Bu bitiş noktası tarafından kullanılan bağlama.  
  
### <a name="contractname"></a>ContractName  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bu uç noktaya sunduğu sözleşmeyi belirten bir dize.  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Uç noktanın performans sayaçları örneğinin adı.  
  
### <a name="listenuri"></a>listenUri  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Uç noktası URI dinler.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bu uç noktayı benzersiz adı.  
  
### <a name="processid"></a>İşlem kimliği  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 İşlemin işlem kimliği uç noktasını barındıran.  
  
### <a name="ref"></a>ref  
 Veri türü: Sözleşme  
  
 Erişim türüne: salt okunur  
  
 Bu bitiş noktasının sunduğu sözleşme.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|
