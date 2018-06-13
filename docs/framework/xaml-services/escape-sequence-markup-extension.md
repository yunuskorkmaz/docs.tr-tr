---
title: '{} Çıkış sırası - biçimlendirme uzantısı'
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
ms.openlocfilehash: a90f6928d68eddd29762e6206769dd7f07704e4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564527"
---
# <a name="-escape-sequence--markup-extension"></a>{} Çıkış dizisi / işaretleme uzantısı
XAML kaçış sırası öznitelik değerlerini sağlar. Kaçış sırası bundan sonraki değerlere sabit değer olarak yorumlanması için özniteliğini verir.  
  
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
|*literalValue*|Kaçış sırası izleyen değişmez değer dize. Genellikle bu dize bir açma veya kapatma parantezi içeriyor ({veya}).|  
  
## <a name="remarks"></a>Açıklamalar  
 Kaçış sırası ({}) XAML'de harf karakter olarak bir açma ayracı ({}) kullanılabilir böylece kullanılır.  
  
 XAML okuyucuları açma ayracı ({}) genellikle bir işaretleme uzantısı giriş noktasını belirtmek için kullanın; Bununla birlikte, bunlar önce bir kapanış ayracı (}) olup olmadığını belirlemek için sonraki karakteri kontrol edin. Yalnızca zaman iki küme ayraçları ({}) olan bitişik, bunlar bir kaçış sırası kabul şunlardır.  
  
 Kaçış sırası karşılaşılırsa, XAML okuyucu dizenin geri kalanı bir dize olarak işleme. Ancak, kaçış sırası tür dönüştürücüsünü sahip bir üye uyguladıysanız, XAML yazıcı tarafından değerlendirdiğinde dize türü dönüştürme uygulanabilir.  
  
 Kaçış sırası biçimlendirme uzantısı değil ve bir sınıf tarafından yedeklenen değil. Ancak, XAML okuyucuları (özel XAML okuyucuları dahil) saygı bir kural gerekir.  
  
 Tırnak işareti ("), bu şekilde bir kaçış sırası olarak kullanılamaz. Tırnak işareti noncontent bir özellik için özellik değeri olarak ayarlamak gerekiyorsa, özellik öğesi sözdizimini kullanın ve özellik öğe içindeki bir dize olarak tırnak işareti koyun veya bir XML karakteri varlık kullanın. İçerik özelliği için tüm içeriği tırnak işareti olabilir.  
  
 Kaçış sırası ({}), bir ad alanı niteleyicisi XAML biçimlendirme uzantısı göründüğü bir konumda içermesi gereken bir XML türü belirtirken sık gereklidir. Bu başlangıç XAML öznitelik değeri ve bir işaretleme uzantısı hemen bir eşittir işaretinden sonra (=) içerir. Aşağıdaki örnek çıkış sıraları XAML öznitelik değeri başlangıcında görünür bir XML ad alanı için gösterir.  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [XML Karakter Varlıkları ve XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
