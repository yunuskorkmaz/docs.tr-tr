---
title: '{} Çıkış sırası - işaretleme uzantısı'
ms.date: 03/30/2017
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
ms.openlocfilehash: eaee0a1f92d8b7cb3810651eda21f1cc800ebf57
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58018555"
---
# <a name="-escape-sequence--markup-extension"></a>{} Kaçış dizisi / işaretleme uzantısı
XAML kaçış dizisi, öznitelik değerleri sağlar. Kaçış sırası bundan sonraki değerlere öznitelik değişmez değer olarak yorumlanmasını sağlar.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>XAML Özellik Öğesi Kullanımı  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|*literalValue*|Kaçış sırası aşağıdaki değişmez değer dize. Genellikle bu dize bir açma veya kapatma ayracı içeriyor ({veya}).|  
  
## <a name="remarks"></a>Açıklamalar  
 Kaçış dizisi ({}) açık küme ayracı ({}) XAML değişmez bir karakter olarak kullanılabilir olacak şekilde kullanılır.  
  
 XAML okuyucular açık küme ayracı ({}) genellikle bir işaretleme uzantısı giriş noktasını belirtmek için kullanılır; ancak, bunlar ilk kapanış ayracından (}) olup olmadığını belirlemek için sonraki karakteri kontrol edin. Yalnızca ne zaman iki küme ayraçları ({}) bitişik olan, bunlar bir kaçış dizisi kabul şunlardır.  
  
 XAML okuyucu dizenin geri kalanı, kaçış dizisi ile karşılaşırsa, bir dize olarak işlemelisiniz. Ancak kaçış sırası üyesi olan bir tür dönüştürücüsü uygulanırsa, XAML yazıcı tarafından yorumlandığında dize türü dönüşümünü uygulanabilir.  
  
 Kaçış dizisi, bir işaretleme uzantısı değil ve bir sınıf tarafından yedeklenmez. Ancak, XAML okuyucular (özel XAML okuyucular dahil) dikkate bir kuralı olur.  
  
 Tırnak işareti ("), bu şekilde bir kaçış dizisi olarak kullanılamaz. Tırnak işareti noncontent bir özellik için özellik değeri olarak ayarlanacak ihtiyacınız varsa, özellik öğesi sözdizimini kullanın ve özellik öğesi içinde bir dize olarak tırnak işareti girin veya bir XML karakter varlık kullanın. İçerik özelliği için tüm içeriği tırnak işareti olabilir.  
  
 Kaçış dizisi ({}) bir XAML işaretleme uzantısı göründüğü bir konumda bir ad alanı niteleyicisi içermelidir bir XML türü belirtirken sık gereklidir. Bu, hemen bir eşittir işaretinden sonra (=) başlangıç XAML öznitelik değeri ve bir işaretleme uzantısı içerir. Aşağıdaki örnek bir XAML öznitelik değeri başlangıcında görünür bir XML ad alanı için kaçış sıralarını gösterir.  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](type-converters-and-markup-extensions-for-xaml.md)
- [XML Karakter Varlıkları ve XAML](xml-character-entities-and-xaml.md)
