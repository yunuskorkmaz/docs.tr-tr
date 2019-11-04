---
title: XAML'de xml:space İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 8f860f5ee42b5c1df43c4ec2b1003408bc1c0d8e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458798"
---
# <a name="xmlspace-handling-in-xaml"></a>XAML'de xml:space İşleme
`xml:space` özniteliği bir nesne öğesi içinde önemli beyaz boşluk işleme davranışını bildiren XML tanımlı bir özniteliktir. Bu davranış, `xml:space` bildirildiği öğede bulunan tüm içerik (iç metin) ve ayrıca alt öğe kapsamları için geçerlidir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- veya-  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Açıklamalar  
 XAML 'de iki olası değeri de dahil olmak üzere `xml:space` özniteliğinin tanımı, XML için W3C belirtimleri tarafından bir "özel öznitelik" olarak tanımlanan `xml:space` türetilir.  
  
 `xml:space` özniteliğin varsayılan değeri, `"default"`değişmez değer değeridir. `"default"`değer için ya da `xml:space` hiç belirtilmemişse, önemli boşluk ayrıştırması davranışı [xaml 'Deki beyaz boşluk işleme](whitespace-processing-in-xaml.md)konusunda tanımlandığı şekilde varsayılan işleme olur.  
  
 Nesne öğesi içeriği içinde boşluk korumak için, bu nesne öğesinde `xml:space="preserve"` belirtin.  
  
 En çok yorumlamalar altında, `xml:space` öznitelik etkileri ve özniteliğin değeri alt öğelerin kapsamına alınır.  
  
 XAML 'de beyaz alan işleme hakkında tam bir açıklama için bkz. [xaml 'de beyaz boşluk işleme](whitespace-processing-in-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML 'de boşluk işleme](whitespace-processing-in-xaml.md)
- [XAML'ye Genel Bakış (WPF)](../../desktop-wpf/fundamentals/xaml.md)
