---
description: 'Hakkında daha fazla bilgi edinin: 1004-Workflowınstancedurdurulan'
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: 4aaa0899da9b0b8510684a13537a8cb8f9117ee1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755634"
---
# <a name="1004---workflowinstanceaborted"></a>1004 - WorkflowInstanceAborted

## <a name="properties"></a>Özellikler

|||
|-|-|
|ID|1004|
|Anahtar sözcükler|WFRuntime|
|Level|Bilgi|
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|

## <a name="description"></a>Description

Bir iş akışı örneğinin bir özel durumla durdurulduğunu gösterir.

## <a name="message"></a>İleti

WorkflowInstance kimliği: ' %1 ' bir özel durumla durduruldu.

## <a name="details"></a>Ayrıntılar

|Veri öğesi adı|Veri öğesi türü|Description|
|--------------------|--------------------|-----------------|
|WorkflowInstanceId|`xs:string`|İş akışının örnek kimliği|
|Özel durum|`xs:string`|Özel durum için özel durum ayrıntıları|
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
