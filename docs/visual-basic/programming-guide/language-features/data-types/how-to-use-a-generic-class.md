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
ms.openlocfilehash: adea9f7e7dbbc2317e5b857a5153e3ec67d63344
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Nasıl yapılır: Genel Bir Sınıf Kullanma (Visual Basic)
Alan bir sınıf *tür parametrelerindeki* çağrılır bir *genel bir sınıf*. Genel bir sınıf kullanıyorsanız, oluşturabileceğiniz bir *oluşturulan sınıf* dışarı sağlayarak bir *tür bağımsız değişkeni* bu parametrelerin her biri için. Oluşturulan sınıf türü bir değişken sonra bildirebilir ve oluşturulan sınıfının bir örneği oluşturun ve bu değişkenine atayın.  
  
 Sınıfları yanı sıra tanımlayabilir ve genel yapılar, arabirimler, yordamlar ve temsilciler kullanın.  
  
 Aşağıdaki yordamda tanımlanan genel bir sınıf gereken [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ve bir örnek oluşturur.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Bir tür parametresi bir alan bir sınıf kullanma  
  
1.  Kaynak dosyanızı başında dahil bir [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) almak için <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı. Bu sayede başvurmak <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> gibi diğer sıra sınıflardan ayırt etmek için tam olarak nitelemek gerek kalmadan sınıfı <xref:System.Collections.Queue?displayProperty=nameWithType>.  
  
2.  Normal bir şekilde oluşturur, ancak eklemek `(Of` `type``)` hemen sonra sınıf adı.  
  
     Aşağıdaki örnek aynı sınıfını kullanır (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) farklı veri türlerini öğelerinizi tutmak iki sıra nesneleri oluşturmak için. Öğeleri her sırasının sonuna ekler ve ardından kaldırır ve her sıranın önünü öğelerinden görüntüler.  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Visual Basic'de genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../../../standard/language-independence-and-language-independent-components.md)  
 [,](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [Yineleyiciler](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
