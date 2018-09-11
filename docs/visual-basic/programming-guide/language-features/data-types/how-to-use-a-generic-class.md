---
title: 'Nasıl yapılır: Genel Bir Sınıf Kullanma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: 108532e5b765fa918fa894199ef710a9f52db4e4
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264408"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Nasıl yapılır: Genel Bir Sınıf Kullanma (Visual Basic)
Alan bir sınıf *tür parametrelerindeki* çağrılır bir *genel sınıf*. Genel sınıf kullanıyorsanız, oluşturabileceğiniz bir *oluşturulan sınıfı* sağlama tarafından gelen bir *tür bağımsız değişkeni* bu parametrelerin her biri için. Ardından oluşturulan sınıf türünde bir değişken bildirebilir ve oluşturulan sınıfın bir örneğini oluşturun ve bu değişkene atayın.  
  
 Sınıflara ek olarak tanımlayabilir ve genel yapılar, arabirimler, yordamları ve temsilciler kullanın.  
  
 Tanımlanan genel bir sınıf aşağıdaki yordamın kullandığı [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ve bir örnek oluşturur.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Bir tür parametresi bir alan bir sınıf kullanma  
  
1.  Kaynak dosyasının başında, dahil bir [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) içeri aktarmak için <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı. Bu sayede başvurmak <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> gibi diğer kuyruk sınıflarından ayırt etmek için tam olarak nitelemek gerek kalmadan sınıfı <xref:System.Collections.Queue?displayProperty=nameWithType>.  
  
2.  Normal bir şekilde oluşturur, ancak ekleme `(Of` `type``)` hemen sonra sınıf adı.  
  
     Aşağıdaki örnek, aynı sınıf kullanır (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) farklı veri türlerinin öğeleri tutmak iki sıranın nesneleri oluşturmak için. Her kuyruk sonuna öğe ekler ve ardından kaldırır ve her kuyruk önüne öğeleri görüntülemektedir.  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
- [Visual Basic'de genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../../../standard/language-independence-and-language-independent-components.md)  
- [,](../../../../visual-basic/language-reference/statements/of-clause.md)  
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
- [Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
- [Yineleyiciler](../../../../visual-basic/programming-guide/concepts/iterators.md)
