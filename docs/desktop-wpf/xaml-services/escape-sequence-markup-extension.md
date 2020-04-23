---
title: '{}Kaçış Sırası - Biçimlendirme Uzantısı'
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
ms.openlocfilehash: f84243994557d76fa52d72b060a1ba35460e98b0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071747"
---
# <a name="-escape-sequence--markup-extension"></a>{}Kaçış sırası / biçimlendirme uzantısı

Öznitelik değerleri için XAML kaçış sırasını sağlar. Kaçış sırası özniteliksonraki değerleri bir edebi olarak yorumlanmasına olanak sağlar.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object property="{} literalValue" .../>
```

## <a name="xaml-property-element-usage"></a>XAML Özellik Öğesi Kullanımı

```xaml
<object>
  <object.property>
    {} literalValue
  </object.property>
</object>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|*literalValue*|Kaçış sırasını izleyen gerçek dize. Genellikle bu dize açık veya yakın bir ayraç ({ veya }) içerir.|

## <a name="remarks"></a>Açıklamalar

Kaçış sırası{}( ) böylece açık bir ayraç ({) XAML'de gerçek bir karakter olarak kullanılabilir.

XAML okuyucuları genellikle bir biçimlendirme uzantısı giriş noktasını belirtmek için açık ayraç ({) kullanır; Yalnızca iki parantez bitişik{}olduğunda, bir kaçış sırası olarak kabul edilirler.

Kaçış sırası ile karşılaşılırsa, XAML okuyucusunun dize geri kalanını bir dize olarak işlemesi gerekir. Ancak, kaçış sırası bir tür dönüştürücüse bir üyeye uygulanırsa, bir XAML yazarı tarafından yorumlandığında dize tür dönüştürmeden geçebilirsiniz.

Kaçış sırası bir biçimlendirme uzantısı değildir ve bir sınıf tarafından desteklenen değildir. Ancak, XAML okuyucuların (özel XAML okuyucuları dahil) saygı göstermesi gereken bir kuraldır.

Tırnak işareti (") bu şekilde kaçış sırası olarak kullanılamaz. İçerik içermeyen bir özellik için özellik değeri olarak bir teklif işareti ayarlamanız gerekiyorsa, özellik öğesi sözdizimini kullanın ve teklif işaretini özellik öğesinin içine dize olarak yerleştirin veya bir XML karakter varlığı kullanın. Bir içerik özelliği için teklif işareti içeriğin tamamı olabilir.

XAML{}biçimlendirme uzantısının görünebileceği bir konumda ad alanı niteleyicisi içermesi gereken bir XML türü belirtirken kaçış sırası ( ) sık sık gereklidir. Bu konum, bir XAML öznitelik değerinin başlangıcını ve eşit bir işaretten hemen sonra bir biçimlendirme uzantısını içerir (=). Aşağıdaki örnekte, XAML öznitelik değerinin başında görünen bir XML ad alanının kaçış sıraları gösterilmektedir.

[!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]

## <a name="see-also"></a>Ayrıca bkz.

- [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](type-converters-and-markup-extensions.md)
- [XML Karakter Varlıkları ve XAML](xml-character-entities.md)
