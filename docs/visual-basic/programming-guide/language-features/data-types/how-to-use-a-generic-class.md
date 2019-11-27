---
title: 'Nasıl yapılır: Genel Bir Sınıf Kullanma'
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
ms.openlocfilehash: 87ca0da5095484615666cda505b4f7678d8160de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350055"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Nasıl yapılır: Genel Bir Sınıf Kullanma (Visual Basic)
*Tür parametreleri* alan bir sınıfa *Genel sınıf*denir. Genel bir sınıf kullanıyorsanız, bu parametrelerin her biri için bir *tür bağımsız değişkeni* sağlayarak bundan *oluşturulmuş bir sınıf* oluşturabilirsiniz. Daha sonra, oluşturulan sınıf türünün bir değişkenini bildirebilir ve oluşturulan sınıfın bir örneğini oluşturabilir ve bu değişkene atayabilirsiniz.  
  
 Sınıfların yanı sıra genel yapıları, arabirimleri, yordamları ve temsilcileri de tanımlayabilir ve kullanabilirsiniz.  
  
 Aşağıdaki yordam .NET Framework tanımlı bir genel sınıf alır ve bundan bir örnek oluşturur.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Bir tür parametresi alan bir sınıfı kullanmak için  
  
1. Kaynak dosyanızın başlangıcında, <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanını içeri aktarmak için bir [Imports (.net ad alanı ve türü) ifadesini](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) ekleyin. Bu, <xref:System.Collections.Queue?displayProperty=nameWithType>gibi diğer sıra sınıflarından ayırt etmek için tam olarak nitelendirmek zorunda kalmadan <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> sınıfına başvurmanıza olanak sağlar.  
  
2. Nesneyi normal şekilde oluşturun, ancak sınıf adından hemen sonra `(Of type)` ekleyin.  
  
     Aşağıdaki örnek, farklı veri türlerindeki öğeleri tutan iki kuyruk nesnesi oluşturmak için aynı sınıfı (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) kullanır. Her kuyruğun sonuna öğeler ekler ve sonra her kuyruğun önüne öğeleri kaldırır ve görüntüler.  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Visual Basic genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../../../standard/language-independence-and-language-independent-components.md)
- [Durumunu](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Yineleyiciler](../../../../visual-basic/programming-guide/concepts/iterators.md)
