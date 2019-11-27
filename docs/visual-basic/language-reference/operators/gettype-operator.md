---
title: GetType İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 4e59bcfaa24c9545ed75c6b5c1d29cad398ac2de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349545"
---
# <a name="gettype-operator-visual-basic"></a>GetType İşleci (Visual Basic)
Belirtilen tür için bir <xref:System.Type> nesnesi döndürür. <xref:System.Type> nesnesi, bu tür hakkında özellikler, Yöntemler ve olaylar gibi bilgiler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---|---|  
|`typename`|Bilgilerini istediğiniz türün adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `GetType` işleci, belirtilen `typename`için <xref:System.Type> nesnesini döndürür. Tanımlı herhangi bir türün adını `typename`geçirebilirsiniz. Buna aşağıdakiler dahildir:  
  
- `Boolean` veya `Date`gibi herhangi bir Visual Basic veri türü.  
  
- <xref:System.ArgumentException?displayProperty=nameWithType> veya <xref:System.Double?displayProperty=nameWithType>gibi .NET Framework sınıf, yapı, modül veya arabirim.  
  
- Uygulamanız tarafından tanımlanan herhangi bir sınıf, yapı, modül veya arabirim.  
  
- Uygulamanız tarafından tanımlanan herhangi bir dizi.  
  
- Uygulamanız tarafından tanımlanan tüm temsilciler.  
  
- Visual Basic, .NET Framework veya uygulamanız tarafından tanımlanan tüm sabit listesi.  
  
 Bir nesne değişkeninin Type nesnesini almak istiyorsanız <xref:System.Type.GetType%2A?displayProperty=nameWithType> yöntemini kullanın.  
  
 `GetType` işleci aşağıdaki koşullarda yararlı olabilir:  
  
- Çalışma zamanında bir türün meta verilerine erişmeniz gerekir. <xref:System.Type> nesnesi, tür üyeleri ve dağıtım bilgileri gibi meta verileri sağlar. Örneğin, bir derlemeyi yansıtmak için bu gereklidir. Daha fazla bilgi için bkz. <xref:System.Reflection?displayProperty=nameWithType>.  
  
- Aynı türdeki örneklere başvurduklarında, iki nesne başvurularını karşılaştırmak istiyorsunuz. `GetType`, aynı <xref:System.Type> nesnesine başvuruları döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde kullanılan `GetType` işleci gösterilmektedir.  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
