---
title: 'Nasıl yapılır: Numaralandırmaları Bildirme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: e2dbdbbf6bf7fe3e4b71cbe7edc7a19b18f96ef2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650809"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Nasıl yapılır: Numaralandırmaları Bildirme (Visual Basic)
Bir numaralandırma ile oluşturduğunuz `Enum` deyiminin bildirimleri bölümünde bir sınıf veya modülü. Bir yöntem içinde bir numaralandırmayı bildiremezsiniz. Uygun erişim düzeyini belirtmek için kullanın `Private`, `Protected`, `Friend`, veya `Public`.  
  
 Bir `Enum` türüne sahip bir ad, bir temel alınan türü ve bir dizi alanları, her bir sabiti temsil eden. Ad geçerli bir Visual Basic .NET niteleyici olmalıdır. Temel alınan tür tamsayı türlerden biri olmalıdır:`Byte`, `Short`, `Long` veya `Integer`. `Integer` varsayılandır. Numaralandırmalar her zaman kesin türü belirtilmiş ve tamsayı türle birbirinin yerine geçemez.  
  
 Numaralandırmalar kayan nokta değerlerine sahip olamaz. Kayan nokta değeri olan bir numaralandırma atanmışsa `Option Strict On`, derleyici hatası sonuçları. Varsa `Option Strict` olan `Off`, değer otomatik olarak dönüştürülür `Enum` türü.  
  
 Adları hakkında bilgi ve nasıl kullanılacağını `Imports` ad niteliği gereksiz, yapmak için Bildirimi'ne [numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Bir numaralandırma bildirme  
  
1.  Kod erişim düzeyi içeren bir bildirim yazma `Enum` anahtar sözcüğü ve her biri farklı bir bildirir geçerli bir ad, aşağıdaki örneklerde olduğu gibi `Enum`.  
  
     [!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  Sabitler numaralandırmada tanımlayın. Varsayılan olarak, bir listedeki ilk sabiti için başlatılmış `0`, ve sonraki sabitleri önceki sabiti'den fazla bir değere başlatılır. Örneğin, aşağıdaki numaralandırması `Days`, adlandırılmış bir sabit içeriyor `Sunday` değerle `0`, adlı bir sabit `Monday` değerle `1`, adlı bir sabit `Tuesday` değeriyle`2`ve benzeri.  
  
     [!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  Değerler numaralandırma sabitler için bir atama deyimi kullanılarak açıkça atayabilirsiniz. Negatif sayılar dahil olmak üzere, herhangi bir tamsayı değeri atayabilirsiniz. Örneğin, hata koşullarını temsil etmek için sıfır'den az olan değerlerin ile sabitleri isteyebilirsiniz. Aşağıdaki listedeki sabiti `Invalid` değeri açıkça atanan `–1`ve sabit `Sunday` değeri atanmış `0`. Listedeki ilk sabit olduğundan `Saturday` değerine de başlatılır `0`. Değeri `Monday` olan `1` (tane değerinden daha `Sunday`); değerini `Tuesday` olan `2`ve benzeri.  
  
     [!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Sabit açık bir tür olarak bildirmek için  
  
-   Enum türü kullanarak belirtin `As` aşağıdaki örnekte gösterildiği gibi yan tümcesi.  
  
     [!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Nasıl yapılır: Bir Sabit Listesi Değeriyle İlişkili Dizeyi Belirleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Sabit Listesi Ne Zaman Kullanılır?](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Sabitlere Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Sabit ve Değişmez Değerli Veri Türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
