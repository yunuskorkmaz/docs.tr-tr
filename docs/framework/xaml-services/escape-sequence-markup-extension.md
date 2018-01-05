---
title: "{} Kaçış sırası - biçimlendirme uzantısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
caps.latest.revision: "21"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8419a1e89d5e94b9868b0fd1fb81540253efca5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="-escape-sequence--markup-extension"></a>{} Çıkış Dizisi / İşaretleme Uzantısı
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
 Böylece bir açma ayracı ({}) XAML'de değişmez değer karakter olarak kullanılan kaçış sırası ({}) kullanılır.  
  
 XAML okuyucuları açma ayracı ({}) genellikle bir işaretleme uzantısı giriş noktasını belirtmek için kullanın; Bununla birlikte, bunlar önce bir kapanış ayracı (}) olup olmadığını belirlemek için sonraki karakteri kontrol edin. Yalnızca iki kaşlı ayraçlar bitişik olduğunda, bir kaçış sırası olarak kabul edilir.  
  
 Kaçış sırası karşılaşılırsa, XAML okuyucu dizenin geri kalanı bir dize olarak işleme. Ancak, kaçış sırası tür dönüştürücüsünü sahip bir üye uyguladıysanız, XAML yazıcı tarafından değerlendirdiğinde dize türü dönüştürme uygulanabilir.  
  
 Kaçış sırası biçimlendirme uzantısı değil ve bir sınıf tarafından yedeklenen değil. Ancak, XAML okuyucuları (özel XAML okuyucuları dahil) saygı bir kural gerekir.  
  
 Tırnak işareti ("), bu şekilde bir kaçış sırası olarak kullanılamaz. Tırnak işareti noncontent bir özellik için özellik değeri olarak ayarlamak gerekiyorsa, özellik öğesi sözdizimini kullanın ve özellik öğe içindeki bir dize olarak tırnak işareti koyun veya bir XML karakteri varlık kullanın. İçerik özelliği için tüm içeriği tırnak işareti olabilir.  
  
 Kaçış sırası ({}), bir ad alanı niteleyicisi XAML biçimlendirme uzantısı burada görünebilir bir konumda içermesi gereken bir XML türü belirtirken sık gereklidir. Bu başlangıç XAML öznitelik değeri ve bir işaretleme uzantısı hemen bir eşittir işaretinden sonra (=) içerir. Aşağıdaki örnek çıkış sıraları XAML öznitelik değeri başlangıcında görünür bir XML ad alanı için gösterir.  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [XML Karakter Varlıkları ve XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
