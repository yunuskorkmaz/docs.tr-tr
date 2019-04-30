---
title: 206 - ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 40a92d77c57728249569a854eab8767ff371bca2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781933"
---
# <a name="206---errorhandlerinvoked"></a>206 - ErrorHandlerInvoked
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|206|  
|anahtar sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay sonra yayılan bir `ErrorHandler` bir hizmet işlemi oluştu. özel bir durumu işlemek için bir fırsat oluşturdu.  
  
## <a name="message"></a>İleti  
 Dağıtıcı '%3' türünde bir özel durum ile '%1' türünde bir ErrorHandler çağrılır. ErrorHandled == '%2'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Çağrılan türünün CLR FullName `ErrorHandler`.|  
|İşlenen|`xs:unsignedByte`|`true` hata işleyicisi hatası, aksi takdirde işleniyorsa `false`.|  
|ExceptionTypeName|`xs:string`|İşlenen özel durum CLR tam adı.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
