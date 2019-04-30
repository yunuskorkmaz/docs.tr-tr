---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756097"
---
# <a name="3502---inferredoperationdescription"></a>3502 - InferredOperationDescription
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|3502|  
|anahtar sözcükler|WFServices|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir OperationDescription WorkflowService ortaya çıkan gösterir.  
  
## <a name="message"></a>İleti  
 Adlı OperationDescription '%1' = '%2' WorkflowService sözleşmede ortaya çıkan. IsOneWay = %3.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:string|İşlemin adı.|  
|ContractName|xs:string|Sözleşme adı.|  
|IsOneWay|xs:string|TRUE veya false değerini tek yönlü sözleşme olup olmadığını belirten.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
