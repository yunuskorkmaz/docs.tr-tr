---
title: GetType İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: de80feecda1268f3899f73c52727372452a2d366
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502637"
---
# <a name="gettype-operator-visual-basic"></a>GetType İşleci (Visual Basic)
Döndürür bir <xref:System.Type> belirtilen türde bir nesne. <xref:System.Type> Nesne türü özellikleri, yöntemleri ve olayları gibi hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
GetType(typename)  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---|---|  
|`typename`|Bilgi bağlamasına türünün adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `GetType` İşleci döndürür <xref:System.Type> nesne için belirtilen `typename`. İçinde tanımlanan bir tür adını geçirebilirsiniz `typename`. Bu, aşağıdakileri içerir:  
  
-   Herhangi bir Visual Basic veri türü, gibi `Boolean` veya `Date`.  
  
-   Herhangi .NET Framework sınıf, yapı, modül veya arabirimi gibi <xref:System.ArgumentException?displayProperty=nameWithType> veya <xref:System.Double?displayProperty=nameWithType>.  
  
-   Herhangi sınıf, yapı, modül veya uygulamanız tarafından tanımlanan arabirimi.  
  
-   Uygulamanız tarafından tanımlanan bir dizi.  
  
-   Uygulamanız tarafından tanımlanan herhangi bir temsilci.  
  
-   Visual Basic, .NET Framework veya uygulamanız tarafından tanımlanan tüm sabit listesi.  
  
 Bir nesne değişkeninin türdeki nesneyi almak istiyorsanız, kullanmanız <xref:System.Type.GetType%2A?displayProperty=nameWithType> yöntemi.  
  
 `GetType` İşleci aşağıdaki durumlarda kullanışlı olabilir:  
  
-   Çalışma zamanında bir türü için meta veriler erişmeniz gerekir. <xref:System.Type> Nesnesi, tür üyeleri ve dağıtım bilgileri gibi meta veriler sağlar. Bu, örneğin, bir derleme üzerinden yansıtacak şekilde ihtiyacınız var. Daha fazla bilgi için bkz. <xref:System.Reflection?displayProperty=nameWithType>.  
  
-   Bunlar aynı tür örneklerine başvuruyorsa görmek için iki nesne başvuru karşılaştırmak istediğiniz. Eğer öyleyse `GetType` aynı başvuruları döndürür <xref:System.Type> nesne.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde gösterildiği `GetType` işleci kullanılıyor.  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
