---
title: 1040 - InArgumentBound
ms.date: 03/30/2017
ms.assetid: 7dfaad1b-36c0-4575-84c1-31d63b0eaf5d
ms.openlocfilehash: 984372c07ccfb11f2f05d5488fa5ffc95075db41
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009753"
---
# <a name="1040---inargumentbound"></a>1040 - InArgumentBound
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1040|  
|anahtar sözcükler|WFActivities|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir giriş bağımsız değişkeni bağlı gösterir.  
  
## <a name="message"></a>İleti  
 Bağımsız değişkeninde '%1' etkinliği '%2', DisplayName: '%3', InstanceId: '%4', değer ile ilişkili: %5.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InArgument|xs:string|InArgument adı.|  
|Etkinlik|xs:string|Etkinlik türü adı.|  
|displayName|xs:string|Etkinliğin görünen adı.|  
|InstanceId|xs:string|Etkinlik örneği kimliği.|  
|Değer|xs:string|InArgument için sınır değeri.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
