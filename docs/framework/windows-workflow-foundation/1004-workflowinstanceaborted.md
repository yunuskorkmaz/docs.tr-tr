---
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d34f6f1ab6af8e06a0f28fb043faf9fe16a8b211
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485193"
---
# <a name="1004---workflowinstanceaborted"></a>1004 - WorkflowInstanceAborted

## <a name="properties"></a>Özellikler

|||
|-|-|
|Kimlik|1004|
|Anahtar Sözcükler|WFRuntime|
|Düzey|Bilgiler|
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|

## <a name="description"></a>Açıklama

Bir özel durum ile bir iş akışı örneği iptal edildi gösterir.

## <a name="message"></a>İleti

WorkflowInstance ID: '%1', bir özel durum ile iptal edildi.

## <a name="details"></a>Ayrıntılar

|Veri öğesi adı|Veri öğesi türü|Açıklama|
|--------------------|--------------------|-----------------|
|WorkflowInstanceID|`xs:string`|İş akışı örnek kimliği|
|Özel Durum|`xs:string`|Özel durum için özel durum ayrıntıları|
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
