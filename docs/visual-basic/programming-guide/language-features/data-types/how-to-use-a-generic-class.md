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
ms.openlocfilehash: 01f1f7ef5963feeb3fe2b5390244e4e516773bad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393850"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Nasıl yapılır: Genel Bir Sınıf Kullanma (Visual Basic)
*Tür parametreleri* alan bir sınıfa *Genel sınıf*denir. Genel bir sınıf kullanıyorsanız, bu parametrelerin her biri için bir *tür bağımsız değişkeni* sağlayarak bundan *oluşturulmuş bir sınıf* oluşturabilirsiniz. Daha sonra, oluşturulan sınıf türünün bir değişkenini bildirebilir ve oluşturulan sınıfın bir örneğini oluşturabilir ve bu değişkene atayabilirsiniz.  
  
 Sınıfların yanı sıra genel yapıları, arabirimleri, yordamları ve temsilcileri de tanımlayabilir ve kullanabilirsiniz.  
  
 Aşağıdaki yordam .NET Framework tanımlı bir genel sınıf alır ve bundan bir örnek oluşturur.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Bir tür parametresi alan bir sınıfı kullanmak için  
  
1. Kaynak dosyanızın başlangıcında, ad alanını içeri aktarmak için bir [Imports (.net ad alanı ve türü) ifadesini](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) ekleyin <xref:System.Collections.Generic?displayProperty=nameWithType> . Bu, sınıfını, gibi <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> diğer sıra sınıflarından ayırt etmek için tam olarak nitelendirmek zorunda kalmadan sınıfa başvurmanıza olanak sağlar <xref:System.Collections.Queue?displayProperty=nameWithType> .  
  
2. Nesneyi normal şekilde oluşturun, ancak `(Of type)` sınıf adından hemen sonra ekleyin.  
  
     Aşağıdaki örnek, <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> farklı veri türlerindeki öğeleri tutan iki kuyruk nesnesi oluşturmak için aynı sınıfı () kullanır. Her kuyruğun sonuna öğeler ekler ve sonra her kuyruğun önüne öğeleri kaldırır ve görüntüler.  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri türleri](index.md)
- [Visual Basic genel türler](generic-types.md)
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../../../standard/language-independence-and-language-independent-components.md)
- [Durumunu](../../../language-reference/statements/of-clause.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Yineleyiciler](../../concepts/iterators.md)
