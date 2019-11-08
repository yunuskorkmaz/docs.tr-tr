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
ms.openlocfilehash: 59449637bb45f6b75462b6809c354af7972fc2e7
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740837"
---
# <a name="how-to-use-special-characters-in-xaml"></a>Nasıl yapılır: XAML'de Özel Karakterler Kullanma
Visual Studio 'da oluşturulan biçimlendirme dosyaları Unicode UTF-8 dosya biçiminde otomatik olarak kaydedilir, bu da vurgu işaretleri gibi çok sayıda özel karakterin doğru kodlandığı anlamına gelir. Ancak, farklı şekilde işlenen yaygın olarak kullanılan özel karakterlerin bir kümesi vardır. Bu özel karakterler, kodlama için World Wide Web Konsorsiyumu (W3C) XML standardını izler.  
  
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
