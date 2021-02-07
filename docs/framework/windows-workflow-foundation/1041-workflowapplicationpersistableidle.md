---
description: 'Hakkında daha fazla bilgi edinin: 1041-Workflowapplicationpersistableıdle'
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: eb004077a36ed3e78229df92a73972ed5feda665
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667765"
---
# <a name="1041---workflowapplicationpersistableidle"></a>1041 - WorkflowApplicationPersistableIdle

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1041|  
|Anahtar sözcükler|WFRuntime|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir iş akışı uygulamasının boşta ve kalıcı olduğunu gösterir. İş akışı uygulaması bırakılacak veya kalıcı olacak.  
  
## <a name="message"></a>İleti  

 WorkflowApplication kimliği: ' %1 ' boşta ve sürekli tablo.  Şu işlem gerçekleştirilecek: %2.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Workflowapplicationıd|xs: String|İş akışı uygulama kimliği|  
|Gerçekleştirilen eylem|xs: String|İş akışı uygulamasında gerçekleştirilecek eylem.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
