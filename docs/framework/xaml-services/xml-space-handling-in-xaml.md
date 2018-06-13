---
title: XAML'de xml:space İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: af971ad9ea74e123b939ff8d8488e4e45c5d4aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563473"
---
# <a name="xmlspace-handling-in-xaml"></a>XAML'de xml:space İşleme
`xml:space` Özniteliği olan bir nesne öğesi içinde önemli boşluk işleme davranışı bildiren XML tanımlı öznitelik. Bu davranış öğesinde bulunan tüm içerik (iç metni) için ilgili nerede `xml:space` bildirilir ve ayrıca kapsamları alt öğelerine.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- veya -  
  
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
 [XAML'de Boşluk İşleme](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [XAML'ye Genel Bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
