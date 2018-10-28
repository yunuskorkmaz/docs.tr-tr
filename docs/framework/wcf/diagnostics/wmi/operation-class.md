---
title: İşlem sınıfı
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 16de8b25594896349ea546d3def52dd256fe5c70
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180945"
---
# <a name="operation-class"></a>İşlem sınıfı
Çalışma  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 İşlem sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 İşlem sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="action"></a>Eylem  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İstek iletisinin WS-Addressing eylem.  
  
### <a name="asyncpattern"></a>AsyncPattern  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Bir işlem kullanarak zaman uyumsuz olarak uygulandığını belirtir bir `Begin`[Aç/Kapat açılı ayraçlar] ve `End`hizmet sözleşmesi [Aç/Kapat açılı ayraçlar] yöntemi çifti.  
  
### <a name="behaviors"></a>Davranışlar  
 Veri türü: davranışı dizi  
  
 Erişim türü: salt okunur  
  
 Bu işlemle ilişkili davranışlar.  
  
### <a name="iscallback"></a>IsCallback  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 İşlemi bir geri çağırma işlemi olduğunda true olur.  
  
### <a name="isinitiating"></a>IsInitiating  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Yöntemi sunucudaki bir oturum başlatabilirsiniz bir işlem uygulayıp uygulamadığını gösterir.  
  
### <a name="isoneway"></a>IsOneWay  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Bir işlem bir yanıt iletisi döndürüp döndürmediğini gösterir.  
  
### <a name="isterminating"></a>IsTerminating  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Bir işlem bir yanıt iletisi döndürüp döndürmediğini gösterir.  
  
### <a name="methodsignature"></a>MethodSignature  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İşlem metodu imzası.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İşlemin adı.  
  
### <a name="parametertypes"></a>ParameterTypes  
 Veri türü: dize dizisi  
  
 Erişim türü: salt okunur  
  
 İşlem parametrelerinin türleri.  
  
### <a name="replyaction"></a>ReplyAction  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İşlem yanıt iletisi için SOAP eylemi değeri.  
  
### <a name="returntype"></a>ReturnType  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İşlemin dönüş türü.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.OperationDescription>
