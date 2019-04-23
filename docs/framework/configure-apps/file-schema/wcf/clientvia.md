---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: b8864760c1700cd785922b922346204d194f56cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176819"
---
# <a name="clientvia"></a>\<clientVia >
Taşıma kanalının oluşturulması gereken URI belirtir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.ClientViaBehavior>.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<endpointBehaviors>  
\<davranışı >  
\<clientVia >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`viaUri`|Yol gösteren bir URI belirten bir dize bir ileti almanız gerekir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir uç nokta davranışı belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
