---
description: 'Hakkında daha fazla bilgi edinin: 3502-ınınredoperationdescription'
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 5068a3553484b38242951ef985886190f8027035
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631495"
---
# <a name="3502---inferredoperationdescription"></a>3502 - InferredOperationDescription

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|3502|  
|Anahtar sözcükler|WFServices|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 WorkflowService 'dan bir OperationDescription 'in çıkartılan olduğunu gösterir.  
  
## <a name="message"></a>İleti  

 ' %2 ' sözleşmesindeki Name = ' %1 ' olan OperationDescription WorkflowService 'dan çıkarsandı. IsOneWay = %3.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|OperationName|xs: String|İşlemin adı.|  
|ContractName|xs: String|Sözleşmenin adı.|  
|IsOneWay|xs: String|Sözleşmenin tek yönlü olup olmadığını belirten doğru veya yanlış.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
