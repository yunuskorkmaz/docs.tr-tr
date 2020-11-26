---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 05278067e3f86612ee4aafbe7d5eb66dc934cb85
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242116"
---
# <a name="3502---inferredoperationdescription"></a>3502 - InferredOperationDescription

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|3502|  
|Anahtar sözcükler|WFServices|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 WorkflowService 'dan bir OperationDescription 'in çıkartılan olduğunu gösterir.  
  
## <a name="message"></a>İleti  

 ' %2 ' sözleşmesindeki Name = ' %1 ' olan OperationDescription WorkflowService 'dan çıkarsandı. IsOneWay = %3.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|OperationName|xs: String|İşlemin adı.|  
|ContractName|xs: String|Sözleşmenin adı.|  
|IsOneWay|xs: String|Sözleşmenin tek yönlü olup olmadığını belirten doğru veya yanlış.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
