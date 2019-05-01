---
title: Uç Noktası
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 4562481e8b0b18c0ea0d9df0af3427ffe6419821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963611"
---
# <a name="endpoint"></a>Uç Noktası
Uç Noktası  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
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
 Uç nokta sınıfı, aşağıdaki yöntemi tanımlar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetOperationCounterInstanceName](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|İşlemi performans sayacı örneği adını alır.|  
  
## <a name="properties"></a>Özellikler  
 Uç nokta sınıfı, aşağıdaki özelliklere sahiptir:  
  
### <a name="address"></a>Adres  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Bitiş noktasının adresini içeren bir URI.  
  
### <a name="addressheaders"></a>AddressHeaders  
 Veri türü: dize dizisi  
  
 Erişim türü: salt okunur  
  
 Adres üstbilgileri Bu uç noktaya bağlı koleksiyonu.  
  
### <a name="addressidentity"></a>AddressIdentity  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Uç noktanın kimliği.  
  
### <a name="appdomainid"></a>AppDomainId  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Uç noktayı barındıran appdomain kimliği.  
  
### <a name="behaviors"></a>Davranışlar  
 Veri türü: Davranış dizi  
  
 Erişim türü: salt okunur  
  
 Bu bitiş noktası tarafından uygulanan davranış koleksiyonu.  
  
### <a name="binding"></a>Bağlama  
 Veri türü: Bağlama  
  
 Erişim türü: salt okunur  
  
 Bu uç nokta tarafından kullanılan bağlama.  
  
### <a name="contractname"></a>ContractName  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Hangi anlaşmanın belirten bir dize bu koncový bod vystavuje.  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Uç nokta performans sayaçları örneğinin adı.  
  
### <a name="listenuri"></a>ListenUri  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Uç nokta URI'si dinler.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Bu uç nokta benzersiz adı.  
  
### <a name="processid"></a>İşlem kimliği  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 İşlem uç noktasını barındıran işlem kimliği.  
  
### <a name="ref"></a>ref  
 Veri türü: Sözleşme  
  
 Erişim türü: salt okunur  
  
 Bu uç noktanın sözleşme.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|
