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
ms.openlocfilehash: c593ca094487e8f7016b02870026321fbcb9a7c3
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-use-special-characters-in-xaml"></a>Nasıl yapılır: XAML'de Özel Karakterler Kullanma
Oluşturulan biçimlendirme dosyaları [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] otomatik olarak kaydedilir [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] vurgu işaretleri gibi en özel karakterleri düzgün şekilde kodlanmış anlamına gelen UTF-8 dosya biçimi. Ancak, farklı şekilde ele alınan yaygın olarak kullanılan özel karakter kümesi yok. Şu özel karakterleri izleyin [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] kodlama için standart.  
  
 Aşağıdaki tabloda, bu özel karakter kümesi kodlaması sözdizimi gösterilmektedir:  
  
|Karakter|Sözdizimi|Açıklama|  
|---------------|------------|-----------------|  
|<|`&lt;`|Küçüktür simgesi|  
|>|`&gt;`|Büyüktür işareti.|  
|&|`&amp;`|Ampersan simgesi.|  
|"|`&quot;`|Çift tırnak işareti simge.|  
  
> [!NOTE]
>  Bir metin kullanarak biçimlendirme dosyası Düzenleyicisi gibi oluşturursanız, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] not defteri dosyasında kaydetmelisiniz [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] herhangi korumak için UTF-8 dosya biçiminde kodlanmış özel karakter.  
  
 Aşağıdaki örnek, nasıl özel karakterler metin biçimlendirme oluştururken kullanabileceğiniz gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
