---
title: '{}Kaçış sırası-biçimlendirme uzantısı'
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
ms.openlocfilehash: b0646c62a1342eb160d1967e86ac286429013f3c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053870"
---
# <a name="-escape-sequence--markup-extension"></a>{} Kaçış Dizisi / İşaretleme Uzantısı
Öznitelik değerleri için XAML kaçış sırası sağlar. Kaçış sırası, öznitelikteki sonraki değerlerin bir değişmez değer olarak yorumlanmasına izin verir.  
  
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
|*Edevalue*|Kaçış dizisini izleyen sabit dize. Genellikle bu dize bir açık veya kapalı küme ayracı ({veya}) içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kaçış sırası ({}), XAML 'de sabit karakter olarak bir açık küme ayracı ({) kullanılabilmesi için kullanılır.  
  
 XAML okuyucuları genellikle bir biçimlendirme uzantısının giriş noktasını belirtmek için açık küme ayracı ({) kullanır; ancak, bir kapanış ayracı (}) olup olmadığını anlamak için ilk olarak bir sonraki karakteri kontrol ederler. Yalnızca iki küme ayracı ({}) bitişik olduğunda, bir kaçış sırası olarak kabul edilir.  
  
 Kaçış dizisine karşılaşılırsa, XAML okuyucusu dizenin geri kalanını dize olarak işlemelidir. Ancak, kaçış dizisi tür dönüştürücüsü olan bir üyeye uygulanmışsa, dize bir XAML yazıcı tarafından yorumlandığı zaman tür dönüştürmeye gidebilirler.  
  
 Kaçış sırası bir işaretleme uzantısı değildir ve bir sınıf tarafından yedeklenmez. Ancak, XAML okuyucularının (özel XAML okuyucuları dahil) dikkate alınmalıdır.  
  
 Tırnak işareti (") bu şekilde kaçış sırası olarak kullanılamaz. İçerik olmayan bir özellik için özellik değeri olarak bir tırnak işareti ayarlamanız gerekirse, özellik öğesi söz dizimini kullanın ve tırnak işaretini özellik öğesinin içine bir dize olarak yerleştirin veya bir XML karakter varlığı kullanın. Bir içerik özelliği için, tırnak işareti tüm içerik olabilir.  
  
 Bir XAML biçimlendirme uzantısının{}görünebileceği bir konumda bir ad alanı niteleyicisi içermesi gereken bir xml türü belirtildiğinde, kaçış sırası () sıklıkla gereklidir. Bu, bir XAML öznitelik değerinin başlangıcını ve bir işaretleme uzantısı içinde, bir eşittir işaretinden (=) hemen sonra içerir. Aşağıdaki örnek, bir XAML öznitelik değerinin başlangıcında görüntülenen bir XML ad alanı için kaçış dizilerini gösterir.  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](type-converters-and-markup-extensions-for-xaml.md)
- [XML Karakter Varlıkları ve XAML](xml-character-entities-and-xaml.md)
