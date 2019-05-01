---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 10789f9a2940c239ae20c8fd1e9d48bca0e820ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963702"
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
 Sözleşme sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 Sözleşme sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="appdomainid"></a>AppDomainId  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Sözleşme barındıran appdomain kimliği.  
  
### <a name="behaviors"></a>Davranışlar  
 Veri türü: Davranış dizi  
  
 Erişim türü: salt okunur  
  
 Bu sözleşme ile ilişkili davranışlar.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 WSDL sözleşmede adı.  
  
### <a name="namespace"></a>Ad Alanı  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Ad alanı `portType` WSDL öğesinde.  
  
### <a name="operations"></a>İşlemler  
 Veri türü: İşlem dizisi  
  
 Erişim türü: salt okunur  
  
 Operace tohoto kontraktu.  
  
### <a name="processid"></a>İşlem kimliği  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 İşlem anlaşması barındıran işlem kimliği.  
  
### <a name="ref"></a>ref  
 Veri türü: Sözleşme  
  
 Erişim türü: salt okunur  
  
 Sözleşme çift yönlü sözleşme olduğunda geri çağırma türü.  
  
### <a name="sessionmode"></a>Sessionmode'u  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Sözleşme kanal oturumları kullanmak için bu Sözleşmesi ile ilişkili bağlama gerekli olup olmadığını gösterir.  
  
### <a name="type"></a>Tür  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Sözleşme türü.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ContractDescription>
