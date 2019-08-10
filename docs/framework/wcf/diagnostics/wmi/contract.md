---
title: Sözleşme
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: e4a21e95a6f1f1860ed36c968d17bb8ac8465dce
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868439"
---
# <a name="contract"></a>Sözleşme
Sözleşme  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 Anlaşma sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 Sözleşme sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="appdomainid"></a>AppDomainID  
 Veri türü: Sint32  
  
 Erişim türü: Salt okunurdur  
  
 Sözleşmeyi barındıran AppDomain 'in AppDomain kimliği.  
  
### <a name="behaviors"></a>Davranışlar  
 Veri türü: Davranış dizisi  
  
 Erişim türü: Salt okunurdur  
  
 Bu sözleşmeyle ilişkilendirilen davranışlar.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türü: Salt okunurdur  
  
 WSDL 'deki sözleşmenin adı.  
  
### <a name="namespace"></a>Ad Alanı  
 Veri türü: dize  
  
 Erişim türü: Salt okunurdur  
  
 WSDL içindeki `portType` öğenin ad alanı.  
  
### <a name="operations"></a>İşlemler  
 Veri türü: İşlem dizisi  
  
 Erişim türü: Salt okunurdur  
  
 Bu sözleşmenin işlemleri.  
  
### <a name="processid"></a>İşlem kimliği  
 Veri türü: Sint32  
  
 Erişim türü: Salt okunurdur  
  
 Sözleşmeyi barındıran işlemin işlem kimliği.  
  
### <a name="ref"></a>ref  
 Veri türü: Sözleşme  
  
 Erişim türü: Salt okunurdur  
  
 Anlaşma bir çift yönlü sözleşme olduğunda geri çağırma türü.  
  
### <a name="sessionmode"></a>SessionMode  
 Veri türü: dize  
  
 Erişim türü: Salt okunurdur  
  
 Sözleşmenin Bu sözleşmeyle ilişkili bağlamanın kanal oturumlarını kullanmasını gerektirip gerektirmediğini belirtir.  
  
### <a name="type"></a>Tür  
 Veri türü: dize  
  
 Erişim türü: Salt okunurdur  
  
 Sözleşmenin türü.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ContractDescription>
