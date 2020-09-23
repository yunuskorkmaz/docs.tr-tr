---
title: 'Nasıl yapılır: Bir Sabit Listesi Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: 752b425ba32efe41a1ab1aa75de20039d36f5e50
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058904"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Nasıl yapılır: Numaralandırmaları Bildirme (Visual Basic)

`Enum`Bir sınıfın veya modülün Bildirimler bölümünde ifadesiyle bir numaralandırma oluşturursunuz. Bir yöntem içinde bir numaralandırma bildiremezsiniz. Uygun erişim düzeyini belirtmek için,, veya kullanın `Private` `Protected` `Friend` `Public` .  
  
 Bir `Enum` tür, her biri bir sabiti temsil eden bir ad, temel tür ve bir alan kümesi içerir. Ad geçerli bir .NET niteleyicisi olmalıdır Visual Basic. Temel alınan tür tamsayı türlerinden biri olmalıdır — `Byte` , `Short` , `Long` veya `Integer` . `Integer` varsayılan değerdir. Numaralandırmalar her zaman kesin olarak türlidir ve tamsayı sayı türleriyle birlikte değiştirilebilir değildir.  
  
 Numaralandırmalar kayan nokta değerlerine sahip olamaz. Bir numaralandırma ile bir kayan nokta değeri atanırsa bir `Option Strict On` derleyici hatası oluşur. `Option Strict`İse `Off` , değer otomatik olarak `Enum` türüne dönüştürülür.  
  
 Adlar hakkında bilgi edinmek ve bu `Imports` deyimin ad nitelemesini gereksiz hale getirmek için nasıl kullanılacağını öğrenmek için bkz. [numaralandırmalar ve ad niteliği](enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Bir numaralandırma bildirmek için  
  
1. Her biri farklı bildiren bir kod erişim düzeyi, `Enum` anahtar sözcük ve geçerli bir ad içeren bir bildirim yazın `Enum` .  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. Sabit Listesi içindeki sabitleri tanımlayın. Varsayılan olarak, bir Numaralandırmadaki ilk sabit olarak başlatılır `0` ve sonraki sabitler önceki sabitten bir değere başlatılır. Örneğin, aşağıdaki sabit listesi, `Days` değeri ile adlandırılmış bir sabit, değeri ile adlandırılmış bir sabit, `Sunday` `0` `Monday` `1` `Tuesday` ve değeri ile adlandırılmış `2` bir sabit içerir.  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. Atama ifadesini kullanarak, bir Numaralandırmadaki sabitlere açıkça değer atayabilirsiniz. Negatif sayılar da dahil olmak üzere herhangi bir tamsayı değeri atayabilirsiniz. Örneğin, hata koşullarını temsil etmek için sıfırdan küçük değerler içeren sabitlerin olmasını isteyebilirsiniz. Aşağıdaki numaralandırmada, sabit `Invalid` değere açıkça atanır `–1` ve sabit `Sunday` değere atanır `0` . Numaralandırmadaki ilk sabit olduğundan, `Saturday` değer olarak da başlatılır `0` . Değeri (değerinden `Monday` `1` bir daha fazla `Sunday` ); değeri `Tuesday` `2` , vb. olur.  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Bir sabit listesini açık bir tür olarak bildirmek için  
  
- `As`Aşağıdaki örnekte gösterildiği gibi yan tümcesini kullanarak enum türünü belirtin.  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](how-to-refer-to-an-enumeration-member.md)
- [Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma](how-to-iterate-through-an-enumeration.md)
- [Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Sabit Listesi Ne Zaman Kullanılır?](when-to-use-an-enumeration.md)
- [Sabitlere Genel Bakış](constants-overview.md)
- [Sabit ve Değişmez Değerli Veri Türleri](constant-and-literal-data-types.md)
- [Sabitler ve numaralandırmalar](../../../language-reference/constants-and-enumerations.md)
