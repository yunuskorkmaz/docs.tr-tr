---
title: GetType İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 2e3e05973f2ef72fef5e429bc98cc58b4b21f2c2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592146"
---
# <a name="gettype-operator-visual-basic"></a>GetType İşleci (Visual Basic)
Belirtilen tür için bir <xref:System.Type> nesnesi döndürür. @No__t-0 nesnesi, bu tür hakkında özellikler, Yöntemler ve olaylar gibi bilgiler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---|---|  
|`typename`|Bilgilerini istediğiniz türün adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 işleci, belirtilen `typename` için <xref:System.Type> nesnesini döndürür. @No__t-0 ' da tanımlı herhangi bir türün adını geçirebilirsiniz. Bu, aşağıdakileri içerir:  
  
- @No__t-0 veya `Date` gibi Visual Basic veri türleri.  
  
- @No__t-0 veya <xref:System.Double?displayProperty=nameWithType> gibi .NET Framework sınıf, yapı, modül veya arabirim.  
  
- Uygulamanız tarafından tanımlanan herhangi bir sınıf, yapı, modül veya arabirim.  
  
- Uygulamanız tarafından tanımlanan herhangi bir dizi.  
  
- Uygulamanız tarafından tanımlanan tüm temsilciler.  
  
- Visual Basic, .NET Framework veya uygulamanız tarafından tanımlanan tüm sabit listesi.  
  
 Bir nesne değişkeninin tür nesnesini almak istiyorsanız <xref:System.Type.GetType%2A?displayProperty=nameWithType> yöntemini kullanın.  
  
 @No__t-0 işleci aşağıdaki koşullarda yararlı olabilir:  
  
- Çalışma zamanında bir türün meta verilerine erişmeniz gerekir. @No__t-0 nesnesi, tür üyeleri ve dağıtım bilgileri gibi meta verileri sağlar. Örneğin, bir derlemeyi yansıtmak için bu gereklidir. Daha fazla bilgi için bkz. <xref:System.Reflection?displayProperty=nameWithType>.  
  
- Aynı türdeki örneklere başvurduklarında, iki nesne başvurularını karşılaştırmak istiyorsunuz. @No__t-0, aynı <xref:System.Type> nesnesine başvuruları döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde `GetType` işleci kullanımda gösterilmektedir.  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
