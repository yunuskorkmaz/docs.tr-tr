---
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: eb4289c0346c9e1d9481347d69db8c5f007e4325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781738"
---
# <a name="219---serviceexception"></a>219 - ServiceException
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|219|  
|anahtar sözcükler|Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir WCF Hizmeti işlenmeyen bir özel durumla karşılaştığında bu olay yayılır. Bu ileti işleme sırasında ve kullanıcı kodunda etkinleştirme sırasında işlenmeyen özel durumları içerir.  
  
## <a name="message"></a>İleti  
 İleti işleme sırasında '%2' türünde yakalanamayan bir özel durum oluştu. ToString tam özel durum: %1.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|Arama sonucu `ToString`(CLR özel durumda).|  
|ExceptionTypeName|`xs:string`|CLR FullName özel durumun türü.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
