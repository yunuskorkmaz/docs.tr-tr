---
description: 'Daha fazla bilgi edinin: Işlem sınıfı'
title: İşlem sınıfı
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 035c02bc05b7a64c5d15538001dbdcf2ec0b135b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803080"
---
# <a name="operation-class"></a>İşlem sınıfı

İşlem  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 Işlem sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 Işlem sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="action"></a>Eylem  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 İstek iletisinin WS-Addressing eylemi.  
  
### <a name="asyncpattern"></a>Metodundaki AsyncPattern  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Bir işlemin zaman uyumsuz `Begin` olarak bir hizmet sözleşmesindeki [açık/kapalı açılı ayraçlar] ve `End` [açık/kapalı açılı ayraçlar] Yöntem çifti kullanılarak uygulandığını belirtir.  
  
### <a name="behaviors"></a>Davranışlar  

 Veri türü: davranış dizisi  
  
 Erişim türü: salt okunurdur  
  
 Bu işlemle ilişkilendirilen davranışlar.  
  
### <a name="iscallback"></a>IsCallback  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 İşlem bir geri çağırma işlemi olduğunda true.  
  
### <a name="isinitiating"></a>IsInitiating  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Yöntemin sunucuda oturum başlatabilen bir işlem uygulayıp uygulamadığını gösterir.  
  
### <a name="isoneway"></a>IsOneWay  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Bir işlemin yanıt iletisi döndürüp döndürmediğini belirtir.  
  
### <a name="isterminating"></a>IsTerminating  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Bir işlemin yanıt iletisi döndürüp döndürmediğini belirtir.  
  
### <a name="methodsignature"></a>MethodSignature  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 İşlemin Yöntem imzası.  
  
### <a name="name"></a>Name  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 İşlemin adı.  
  
### <a name="parametertypes"></a>ParameterTypes  

 Veri türü: dize dizisi  
  
 Erişim türü: salt okunurdur  
  
 İşlemin parametrelerinin türleri.  
  
### <a name="replyaction"></a>ReplyAction  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 İşlemin yanıt iletisi için SOAP eyleminin değeri.  
  
### <a name="returntype"></a>'Indaki  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 İşlemin dönüş türü.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.OperationDescription>
