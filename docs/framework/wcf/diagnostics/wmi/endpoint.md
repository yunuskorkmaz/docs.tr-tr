---
title: Uç Nokta
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: ceb4e4b41502b00d7bb21f1ecbd8249fccf1ce3b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288820"
---
# <a name="endpoint"></a>Uç Nokta

Uç Nokta  
  
## <a name="syntax"></a>Syntax  
  
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
  
 Erişim türü: salt okunurdur  
  
 Uç noktanın adresini içeren bir URI.  
  
### <a name="addressheaders"></a>AddressHeaders  

 Veri türü: dize dizisi  
  
 Erişim türü: salt okunurdur  
  
 Bu uç noktaya eklenen adres üst bilgileri koleksiyonu.  
  
### <a name="addressidentity"></a>Addressıdentity  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Uç noktanın kimliği.  
  
### <a name="appdomainid"></a>AppDomainID  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Uç noktasını barındıran AppDomain 'in AppDomain kimliği.  
  
### <a name="behaviors"></a>Davranışlar  

 Veri türü: davranış dizisi  
  
 Erişim türü: salt okunurdur  
  
 Bu uç nokta tarafından uygulanan davranışların koleksiyonu.  
  
### <a name="binding"></a>Bağlama  

 Veri türü: bağlama  
  
 Erişim türü: salt okunurdur  
  
 Bu uç nokta tarafından kullanılan bağlama.  
  
### <a name="contractname"></a>ContractName  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bu uç noktanın hangi sözleşmeyi açığa çıkardığınızı belirten bir dize.  
  
### <a name="counterinstancename"></a>CounterInstanceName  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Uç noktanın performans sayaçları örneğinin adı.  
  
### <a name="listenuri"></a>Öğesini  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Uç noktanın dinlediği URI.  
  
### <a name="name"></a>Adı  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bu uç noktanın benzersiz adı.  
  
### <a name="processid"></a>Işlem  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Uç noktasını barındıran işlemin işlem kimliği.  
  
### <a name="ref"></a>ref  

 Veri türü: sözleşme  
  
 Erişim türü: salt okunurdur  
  
 Bu uç noktanın sunduğu sözleşme.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|
