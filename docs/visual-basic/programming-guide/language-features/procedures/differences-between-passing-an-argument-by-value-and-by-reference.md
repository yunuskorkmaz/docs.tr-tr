---
title: Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: 1b85941c14721280a5025db442c4793930244ec8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837519"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar (Visual Basic)
Bir yordam için bir veya daha fazla değişken geçtiğinizde, her bağımsız değişken çağıran koddaki temel programlama öğesine karşılık gelir. Bu temel alınan öğenin değeri veya buna bir başvuru geçirebilirsiniz. Bu olarak bilinir *mekanizması geçirme*.  
  
## <a name="passing-by-value"></a>Değere göre geçirme  
 Bağımsız değişken geçirmeniz *değeriyle* belirterek [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) anahtar sözcüğü için yordam tanımında karşılık gelen parametre. Visual Basic programlama temel alınan öğenin değeri bu geçirme mekanizması kullandığınızda, yordamda yerel bir değişken içine kopyalar. Yordam kodu çağıran kod temel öğeye herhangi bir erişimi yok.  
  
## <a name="passing-by-reference"></a>Başvuruya göre geçirme  
 Bağımsız değişken geçirmeniz *başvuruya göre* belirterek [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) anahtar sözcüğü için yordam tanımında karşılık gelen parametre. Bu geçirme mekanizması kullandığınızda, Visual Basic yordamı bir doğrudan başvuru temel programlama öğesine çağıran kodu sağlar.  
  
## <a name="passing-mechanism-and-element-type"></a>Geçirme mekanizması ve öğe türü  
 Seçim mekanizması geçirme sınıflandırmasını temel öğe türü ile aynı değil. Değere veya başvuruya göre geçirme ne Visual Basic için yordamının kodunu sağladığı için ifade eder. Bir değer türü veya başvuru türü bir programlama öğesi bellekte depolanma için ifade eder.  
  
 Ancak, öğe türü ve geçirme mekanizması birbirleriyle ilişkilidir. Bir başvuru türü başka bir yerde bellekteki verileri için bir işaretçi değeridir. Temel alınan öğenin kendisinin erişemiyor olsa bile bir başvuru türü değerle geçirdiğinizde, yordamının kodunu temel öğesinin veri işaretçisi olduğunu gösterir. Örneğin, bir dizi değişkenini öğesiyse yordamının kodunu değişkene erişimi yok, ancak dizi üyeleri erişebilir.  
  
## <a name="ability-to-modify"></a>Değiştirme olanağı.  
 Bağımsız değişken olarak değiştirilemez öğenin başarıyla sonuçlandıktan sonra başarılı olmadığını yordamı hiçbir zaman onu çağıran kod içinde değiştirebilirsiniz `ByVal` veya `ByRef`.  
  
 Değiştirilebilir bir öğesi için öğe türü ve geçirme mekanizması arasındaki etkileşim aşağıdaki tabloda özetlenmiştir.  
  
|Öğe türü|Geçirilen `ByVal`|Geçirilen `ByRef`|  
|------------------|--------------------|--------------------|  
|Değer türü (yalnızca bir değer içeriyor)|Yordamı, değişken veya diğer üyelerinin değiştiremezsiniz.|Yordamı, değişken ve üyelerini değiştirebilirsiniz.|  
|Başvuru türü (sınıfın veya yapının örneği bir işaretçi içerir)|Yordam değişken değiştiremezsiniz ancak işaret ettiği örnek üyeleri değiştirebilir.|Yordamı, değişken ve işaret ettiği örnek üyelerini değiştirebilirsiniz.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Nasıl yapılır: Bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Nasıl yapılır: Bir yordam bağımsız değişkeninin değerini değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)
- [Nasıl yapılır: Bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Nasıl yapılır: Bağımsız değişkeni değere göre geçirilecek şekilde zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
