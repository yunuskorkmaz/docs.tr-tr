---
title: XAML'de xml:space İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: a7c3775f2e49a80eabc61f24d086a94fcadfd574
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617583"
---
# <a name="xmlspace-handling-in-xaml"></a>XAML'de xml:space İşleme
`xml:space` Özniteliği olan bir nesne öğesi içinde önemli boşluk işleme davranışını bildiren XML tanımlı öznitelik. Bu öğe içinde bulunan tüm içeriği (iç metni) ilgili, davranıştır burada `xml:space` bildirilmiş ve aynı zamanda kapsamları alt öğeleri için.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- veya -  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımı `xml:space` iki olası değerleri dahil olmak üzere XAML özniteliği türetilen `xml:space` "özel özniteliği" belirtimleri XML W3C tarafından tanımlandığı şekilde.  
  
 Varsayılan değer olan `xml:space` özniteliktir değişmez değer `"default"`. Değeri için `"default"`, veya `xml:space` önemli boşluk ayrıştırma davranıştır varsayılan işleme konusundaki tanımlandığı şekilde, belirtilmemiş [boşluk XAML içinde işleme](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
 Boşluk nesne öğe içeriği içinde korumak için bu seçeneği belirtin `xml:space="preserve"` o nesne öğesi üzerinde.  
  
 Çoğu yorumlaması altında `xml:space` özniteliği etkiler ve öznitelik değeri için alt öğeleri kapsanır.  
  
 Boşluk işleme XAML içinde tam bir açıklaması için bkz: [boşluk XAML içinde işleme](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Boşluk XAML içinde işleme](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)
- [XAML'ye Genel Bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
