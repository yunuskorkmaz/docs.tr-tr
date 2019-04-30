---
title: 225 - TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: 0bb54387dbd738a01225008edfc45ecb7297cd00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755668"
---
# <a name="225---tracecorrelationkeys"></a>225 - TraceCorrelationKeys
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|225|  
|anahtar sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay, bir iş akışı hizmeti için içerik temelli bağıntı kullanıldığında yayınlanır. Bu örneği mesajıyla uygulanan bağıntı anahtarlarını içerir.  
  
## <a name="message"></a>İleti  
 Bağıntı anahtar '%1' değerleri '%2' üst kapsamda '%3' kullanılarak hesaplanır.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Örnek anahtarı|`xs:GUID`|Bağıntı değerlerden oluşturulan anahtar.|  
|Değerler|`xs:string`|Bağıntı örneği anahtarı hesaplamak için kullanılan değerler.|  
|Üst kapsam|`xs:string`||  
|HostReference|`xs:string`|Bu alan, barındırılan Web Hizmetleri için Hizmet Web hiyerarşideki benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
