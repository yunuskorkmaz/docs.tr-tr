---
title: GetType İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 9ff207ea4f2b89ea30eb8f46a3e640ccf3789974
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867008"
---
# <a name="gettype-operator-visual-basic"></a>GetType İşleci (Visual Basic)

<xref:System.Type>Belirtilen tür için bir nesne döndürür. <xref:System.Type>Nesnesi, bu tür hakkında özellikler, Yöntemler ve olaylar gibi bilgiler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---|---|  
|`typename`|Bilgilerini istediğiniz türün adı.|  
  
## <a name="remarks"></a>Açıklamalar  

 `GetType`İşleci, <xref:System.Type> belirtilen için nesnesini döndürür `typename` . ' De tanımlı herhangi bir türün adını geçirebilirsiniz `typename` . Bu, aşağıdakileri içerir:  
  
- Ya da gibi Visual Basic veri türü `Boolean` `Date` .  
  
- Ya da gibi .NET Framework sınıf, yapı, modül veya arabirim <xref:System.ArgumentException?displayProperty=nameWithType> <xref:System.Double?displayProperty=nameWithType> .  
  
- Uygulamanız tarafından tanımlanan herhangi bir sınıf, yapı, modül veya arabirim.  
  
- Uygulamanız tarafından tanımlanan herhangi bir dizi.  
  
- Uygulamanız tarafından tanımlanan tüm temsilciler.  
  
- Visual Basic, .NET Framework veya uygulamanız tarafından tanımlanan tüm sabit listesi.  
  
 Bir nesne değişkeninin Type nesnesini almak istiyorsanız <xref:System.Type.GetType%2A?displayProperty=nameWithType> yöntemini kullanın.  
  
 `GetType`İşleci aşağıdaki koşullarda yararlı olabilir:  
  
- Çalışma zamanında bir türün meta verilerine erişmeniz gerekir. <xref:System.Type>Nesnesi, tür üyeleri ve dağıtım bilgileri gibi meta verileri sağlar. Örneğin, bir derlemeyi yansıtmak için bu gereklidir. Daha fazla bilgi için bkz. <xref:System.Reflection?displayProperty=nameWithType>.  
  
- Aynı türdeki örneklere başvurduklarında, iki nesne başvurularını karşılaştırmak istiyorsunuz. Varsa, `GetType` aynı nesneye başvuruları döndürür <xref:System.Type> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örneklerde `GetType` kullanılan operatör gösterilmektedir.  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [İşleçler ve Ifadeler](../../programming-guide/language-features/operators-and-expressions/index.md)
