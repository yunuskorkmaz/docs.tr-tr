---
title: Uç Noktası
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 03c401358839671d750985b95b1aada599931aad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795902"
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
 Endpoint sınıfı aşağıdaki yöntemi tanımlar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetOperationCounterInstanceName](getoperationcounterinstancename.md)|İşlem performans sayacı örnek adını alır|  
  
## <a name="properties"></a>Özellikler  
 Uç nokta sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="address"></a>Adres  
 Veri türü: dize  
  
 Erişim türü: Salt okunurdur  
  
 Uç noktanın adresini içeren bir URI.  
  
### <a name="addressheaders"></a>AddressHeaders  
 Veri türü: dize dizisi  
  
 Erişim türü: Salt okunurdur  
  
 Bu uç noktaya eklenen adres üst bilgileri koleksiyonu.  
  
### <a name="addressidentity"></a>Addressıdentity  
 Veri türü: dize  
  
 Erişim türü: Salt okunurdur  
  
 Uç noktanın kimliği.  
  
### <a name="appdomainid"></a>AppDomainID  
 Veri türü: Sint32  
  
 Erişim türü: Salt okunurdur  
  
 Uç noktasını barındıran AppDomain 'in AppDomain kimliği.  
  
### <a name="behaviors"></a>Davranışlar  
 Veri türü: Davranış dizisi  
  
 Erişim türü: Salt okunurdur  
  
 Bu uç nokta tarafından uygulanan davranışların koleksiyonu.  
  
### <a name="binding"></a>Bağlama  
 Veri türü: Bağlama  
  
 Erişim türü: Salt okunurdur  
  
 Bu uç nokta tarafından kullanılan bağlama.  
  
### <a name="contractname"></a>ContractName  
 Veri türü: dize  
  
 Erişim türü: Salt okunurdur  
  
 Bu uç noktanın hangi sözleşmeyi açığa çıkardığınızı belirten bir dize.  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Veri türü: dize  
  
 Erişim türü: Salt okunurdur  
  
 Uç noktanın performans sayaçları örneğinin adı.  
  
### <a name="listenuri"></a>Öğesini  
 Veri türü: dize  
  
 Erişim türü: Salt okunurdur  
  
 Uç noktanın dinlediği URI.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türü: Salt okunurdur  
  
 Bu uç noktanın benzersiz adı.  
  
### <a name="processid"></a>İşlem kimliği  
 Veri türü: Sint32  
  
 Erişim türü: Salt okunurdur  
  
 Uç noktasını barındıran işlemin işlem kimliği.  
  
### <a name="ref"></a>ref  
 Veri türü: Sözleşme  
  
 Erişim türü: Salt okunurdur  
  
 Bu uç noktanın sunduğu sözleşme.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|
