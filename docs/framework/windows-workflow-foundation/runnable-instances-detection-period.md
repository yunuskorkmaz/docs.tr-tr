---
title: "Runnable örnekleri algılama süresi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a78f8404d5e6b9d63c9455d059dcbb9a76f8c18
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="runnable-instances-detection-period"></a>Runnable örnekleri algılama süresi
SQL iş akışı örneği deposuna düzenli aralıklarla uyanır ve kalıcılığı veritabanında runnable veya activatable örneklerini algılayan bir iç görev çalıştırır. **Runnable örnekleri algılama süresi** özelliği SQL iş akışı örneği deposunun SQL iş akışı örneği deposuna sonra hiçbir runnable veya activatable iş akışı algılamak için algılama görev çalıştırır süre belirtir Önceki algılama döngüsü sonra Kalıcılık veritabanındaki örnekleri.  
  
 Bu özellik için daha kısa bir aralığı ayarını bir iş akışı örneği ve olay ve sonraki yükleme örneğinin sinyal ilişkili bir süreölçer sona erme tarihi arasındaki süreyi azaltır. Ancak, aynı zamanda bir ana bilgisayar üzerindeki işlem yükü artırır ve dayanıklı zamanlayıcılar ve/veya ana bilgisayar hataları nadir olduğu senaryolarda tercih edilebilir değil. Özelliğin türü TimeSpan ve özelliğinin değeri biçimdedir: ss: dd:. Bu özellik için en düşük değer 00:00:01 ' dir. Özelliği için varsayılan değer 00:00:05 ' dir.  
  
 Daha fazla bilgi için bkz: algılama ve runnable ve activatable iş akışı örnekleri, etkinleştirme [örneği etkinleştirme](../../../docs/framework/windows-workflow-foundation/instance-activation.md).
