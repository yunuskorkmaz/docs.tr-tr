---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 12b45c08a3d8dc69e740ce77d0d2abd097907ac2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485713"
---
# <a name="contract"></a>Daralma
Daralma  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 Sözleşme sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 Sözleşme sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="appdomainid"></a>AppDomainId  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Sözleşme barındıran appdomain kimliği.  
  
### <a name="behaviors"></a>Davranışlar  
 Veri türü: davranış dizisi  
  
 Erişim türüne: salt okunur  
  
 Bu sözleşme ile ilişkilendirilen davranışlar.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 WSDL içindeki sözleşme adı.  
  
### <a name="namespace"></a>Ad Alanı  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Ad alanı `portType` WSDL öğesinde.  
  
### <a name="operations"></a>İşlemler  
 Veri türü: işlem dizisi  
  
 Erişim türüne: salt okunur  
  
 Bu sözleşme işlemleri.  
  
### <a name="processid"></a>İşlem kimliği  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 İşlemin işlem kimliği Sözleşmeyi barındıran.  
  
### <a name="ref"></a>ref  
 Veri türü: Sözleşme  
  
 Erişim türüne: salt okunur  
  
 Sözleşme çift yönlü sözleşme olduğunda geri çağırma türü.  
  
### <a name="sessionmode"></a>SessionMode  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Sözleşme kanal oturumları kullanmak için bu sözleşmeyle ilişkili bağlama gerekli olup olmadığını gösterir.  
  
### <a name="type"></a>Tür  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Sözleşme türü.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ContractDescription>
