---
description: 'Hakkında daha fazla bilgi edinin: 1035-RuntimeTransactionSet'
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 513ba49962a8f02ab47b8e5b762949cd09154a3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667908"
---
# <a name="1035---runtimetransactionset"></a>1035 - RuntimeTransactionSet

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1035|  
|Anahtar sözcükler|WFRuntime|  
|Level|Ayrıntılı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir etkinliğin çalışma zamanı işlemini ayarlamış olduğunu gösterir.  
  
## <a name="message"></a>İleti  

 Çalışma zamanı işlemi, DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' etkinliğine göre ayarlandı.  Yürütme, DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' etkinliğine yalıtılmış.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Etkinlik|xs: String|Etkinliğin tür adı.|  
|DisplayName|xs: String|Etkinliğin görünen adı.|  
|InstanceId|xs: String|Etkinliğin örnek kimliği.|  
|Isotedactivity|xs: String|İşlemin yalıtılmış olduğu etkinliğin tür adı.|  
|Isotedactivitydisplayname|xs: String|İşlemin yalıtılmış olduğu etkinliğin görünen adı.|  
|Isotedactivityınstanceıd|xs: String|İşlemin yalıtılmış olduğu etkinliğin örnek kimliği.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
