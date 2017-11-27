---
title: "XAML'de xml:space İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a5048cbad1d2ea914d041ac3c87a43223b208c3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xmlspace-handling-in-xaml"></a>XAML'de xml:space İşleme
`xml:space` Özniteliği olan bir nesne öğesi içinde önemli boşluk işleme davranışı bildiren XML tanımlı öznitelik. Bu davranış öğesinde bulunan tüm içerik (iç metni) için ilgili nerede `xml:space` bildirilir ve ayrıca kapsamları alt öğelerine.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \-veya -  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımı `xml:space` olası iki değeri de dahil olmak üzere XAML'de özniteliği türetilir `xml:space` "özel özniteliği" XML için W3C belirtimleri tarafından tanımlanan.  
  
 Varsayılan değer olan `xml:space` hazır değeri bir özniteliktir `"default"`. Değeri için `"default"`, veya `xml:space` önemli boşluk ayrıştırma davranışını konusundaki tanımlanan varsayılan işleme olduğundan hiç belirtilmemiş [XAML'de boşluk işleme](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
 İçinde nesne öğe içeriği korumak için belirtmek `xml:space="preserve"` bu nesne öğede.  
  
 Çoğu yorumlar altında `xml:space` özniteliği etkiler ve özniteliğinin değeri alt öğelerine kapsamlı.  
  
 XAML'de boşluk işleme kapsamlı bir açıklama için bkz: [XAML'de boşluk işleme](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML'de boşluk işleme](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [XAML genel bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
