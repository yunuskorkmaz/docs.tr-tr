---
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: d61d710959f99dbc8a91441766a690eb7e9a365c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774276"
---
# <a name="4209---timeoutopeningsqlconnection"></a>4209 - TimeoutOpeningSqlConnection
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|4209|  
|anahtar sözcükler|WFInstanceStore|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir SQL bağlantı açılmaya çalışılırken zaman aşımıyla karşılaşıldı gösterir.  
  
## <a name="message"></a>İleti  
 Bir SQL bağlantı açılmaya çalışılırken zaman aşımı. İşlem, %1 ' ayrılan süre içinde tamamlanmadı. Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|zaman aşımı|xs:string|SQL Bağlantısı açmak için zaman aşımı değeri.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
