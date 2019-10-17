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
ms.openlocfilehash: 27f2b18593d075b54eb8c3351bbb84415700cfd4
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395800"
---
# <a name="how-to-use-special-characters-in-xaml"></a>Nasıl yapılır: XAML'de Özel Karakterler Kullanma
@No__t-0 ' da oluşturulan biçimlendirme dosyaları Unicode UTF-8 dosya biçiminde otomatik olarak kaydedilir, bu da vurgu işaretleri gibi çok sayıda özel karakterin doğru kodlandığı anlamına gelir. Ancak, farklı şekilde işlenen yaygın olarak kullanılan özel karakterlerin bir kümesi vardır. Bu özel karakterler, kodlama için [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standardını izler.  
  
 Aşağıdaki tabloda, bu özel karakter kümesini kodlamaya yönelik sözdizimi gösterilmektedir:  
  
|Karakter|Sözdizimi|Açıklama|  
|---------------|------------|-----------------|  
|<|`&lt;`|Küçüktür simgesi.|  
|>|`&gt;`|Büyüktür işareti.|  
|&|`&amp;`|Ve simgesi.|  
|"|`&quot;`|Çift tırnak simgesi.|  
  
> [!NOTE]
> Windows Not Defteri gibi bir metin düzenleyicisi kullanarak bir biçimlendirme dosyası oluşturursanız, kodlanmış özel karakterleri korumak için dosyayı Unicode UTF-8 dosya biçiminde kaydetmelisiniz.  
  
 Aşağıdaki örnek, biçimlendirme oluştururken metindeki özel karakterleri nasıl kullanabileceğinizi gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
