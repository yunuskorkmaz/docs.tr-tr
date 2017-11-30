---
title: "Nasıl yapılır: Numaralandırmaları Bildirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 938550ebbfcf099729db3de96b809549cb234d81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Nasıl yapılır: Numaralandırmaları Bildirme (Visual Basic)
Bir numaralandırma ile oluşturduğunuz `Enum` deyiminin bildirimleri bölümünde bir sınıf veya modülü. Bir yöntem içinde bir numaralandırmayı bildiremezsiniz. Uygun erişim düzeyini belirtmek için kullanın `Private`, `Protected`, `Friend`, veya `Public`.  
  
 Bir `Enum` türüne sahip bir ad, bir temel alınan türü ve bir dizi alanları, her bir sabiti temsil eden. Ad geçerli bir Visual Basic .NET niteleyici olmalıdır. Temel alınan tür tamsayı türlerden biri olmalıdır:`Byte`, `Short`, `Long` veya `Integer`. `Integer`varsayılandır. Numaralandırmalar her zaman kesin türü belirtilmiş ve tamsayı türle birbirinin yerine geçemez.  
  
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
 [Numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Nasıl yapılır: bir numaralandırma üyesine başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Nasıl yapılır: bir numaralandırma değeriyle ilişkili dizeyi belirleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Bir numaralandırmanın ne zaman kullanılacağı](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Sabitlere genel bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Sabit ve değişmez değerli veri türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Sabitler ve numaralandırmalar](../../../../visual-basic/language-reference/constants-and-enumerations.md)
