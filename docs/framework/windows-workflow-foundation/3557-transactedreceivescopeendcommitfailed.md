---
description: 'Hakkında daha fazla bilgi edinin: 3557-TransactedReceiveScopeEndCommitFailed'
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 7865ae27e7ce5b3f13b3567f3f8aeebd6edf3fd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777989"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a>3557 - TransactedReceiveScopeEndCommitFailed

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|3557|  
|Anahtar sözcükler|WFServices|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bir CommittableTransaction üzerinde Endcommıt çağrısının bir TransactionException olduğunu gösterir.  
  
## <a name="message"></a>İleti  

 ID = ' %1 ' olan CommittableTransaction üzerinde Endcommıt çağrısı şu iletiyle bir TransactionException oluşturdu: ' %2 '.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|TransactionId|xs: String|CommittableTransaction kimliği.|  
|Özel durum|xs: String|Özel durum için özel durum ayrıntıları|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
