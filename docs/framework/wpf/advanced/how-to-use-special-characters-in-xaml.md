---
title: "Nasıl yapılır: XAML'de Özel Karakterler Kullanma"
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 18934e06f45ca4b88f48bce8a310a07b460a5f53
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377969"
---
# <a name="how-to-use-special-characters-in-xaml"></a>Nasıl yapılır: XAML'de Özel Karakterler Kullanma
Oluşturulan biçimlendirme dosyalarında biçimlendirmeyi [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] otomatik olarak kaydedilir [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] vurgu işaretleri gibi çoğu özel karakteri doğru kodlanmış anlamına gelen UTF-8 dosya biçimi. Ancak, bir dizi farklı şekilde ele alınan sık kullanılan özel karakterler var. Bu özel karakterlerin izleyin [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] kodlama standardı.  
  
 Aşağıdaki tabloda, bu özel karakter kümesi kodlaması için sözdizimi gösterilmektedir:  
  
|Karakter|Sözdizimi|Açıklama|  
|---------------|------------|-----------------|  
|<|`&lt;`|Küçük simge.|  
|>|`&gt;`|Büyüktür işareti.|  
|&|`&amp;`|Ampersan simgesi.|  
|"|`&quot;`|Çift tırnak işareti sembolü.|  
  
> [!NOTE]
>  Biçimlendirme dosyası kullanarak bir metin düzenleyicisi gibi oluşturursanız [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] not defteri dosyasında kaydetmelisiniz [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] herhangi korumak için dosya biçimi UTF-8 kodlamalı özel karakterler.  
  
 Aşağıdaki örnekte, nasıl özel karakterler metin biçimlendirme oluştururken kullanabileceğiniz gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
