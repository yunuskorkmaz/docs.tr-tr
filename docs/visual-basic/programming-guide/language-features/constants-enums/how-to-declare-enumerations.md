---
title: 'Nasıl yapılır: Numaralandırmalar bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: 042aea045313bcaf3832274acf1000f87a084b72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354052"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Nasıl yapılır: Numaralandırmaları Bildirme (Visual Basic)
Bir sınıfın veya modülün Bildirimler bölümünde `Enum` ifadesiyle bir numaralandırma oluşturursunuz. Bir yöntem içinde bir numaralandırma bildiremezsiniz. Uygun erişim düzeyini belirtmek için `Private`, `Protected`, `Friend`veya `Public`kullanın.  
  
 `Enum` türü, her biri bir sabiti temsil eden bir ada, temel alınan türe ve bir alan kümesine sahiptir. Ad geçerli bir .NET niteleyicisi olmalıdır Visual Basic. Temel alınan tür tamsayı türlerinden biri olmalıdır —`Byte`, `Short`, `Long` veya `Integer`. `Integer` varsayılandır. Numaralandırmalar her zaman kesin olarak türlidir ve tamsayı sayı türleriyle birlikte değiştirilebilir değildir.  
  
 Numaralandırmalar kayan nokta değerlerine sahip olamaz. Bir numaralandırmaya `Option Strict On`bir kayan nokta değeri atanırsa bir derleyici hatası oluşur. `Option Strict` `Off`ise, değer otomatik olarak `Enum` türüne dönüştürülür.  
  
 Adlar hakkında bilgi edinmek ve ad nitelemesini gereksiz hale getirmek için `Imports` deyimin nasıl kullanılacağını öğrenmek için bkz. [numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Bir numaralandırma bildirmek için  
  
1. Her biri farklı bir `Enum`bildiren aşağıdaki örneklerde olduğu gibi, kod erişim düzeyi, `Enum` anahtar sözcüğünü ve geçerli bir adı içeren bir bildirim yazın.  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. Sabit Listesi içindeki sabitleri tanımlayın. Varsayılan olarak, bir Numaralandırmadaki ilk sabit `0`olarak başlatılır ve sonraki sabitler önceki sabitten bir değere başlatılır. Örneğin, aşağıdaki sabit listesi `Days`, değer `0`, `1`değeri ile `Monday` adlı bir sabit, `Tuesday` değeri ile `2`adlı bir sabit olan `Sunday` adında bir sabit içerir.  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. Atama ifadesini kullanarak, bir Numaralandırmadaki sabitlere açıkça değer atayabilirsiniz. Negatif sayılar da dahil olmak üzere herhangi bir tamsayı değeri atayabilirsiniz. Örneğin, hata koşullarını temsil etmek için sıfırdan küçük değerler içeren sabitlerin olmasını isteyebilirsiniz. Aşağıdaki numaralandırmada, sabit `Invalid` `–1`değeri açıkça atanır ve sabit `Sunday` `0`değer atanır. Numaralandırmadaki ilk sabit olduğundan, `Saturday` `0`değer olarak da başlatılır. `Monday` değeri `1` (`Sunday`değerinden bir daha fazla); `Tuesday` değeri `2`ve bu şekilde devam eder.  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Bir sabit listesini açık bir tür olarak bildirmek için  
  
- Aşağıdaki örnekte gösterildiği gibi, `As` yan tümcesini kullanarak enum türünü belirtin.  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Nasıl yapılır: Visual Basic bir numaralandırmada yineleme yapma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Nasıl yapılır: Bir Sabit Listesi Değeriyle İlişkili Dizeyi Belirleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Sabit Listesi Ne Zaman Kullanılır?](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Sabitlere Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Sabit ve Değişmez Değerli Veri Türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
