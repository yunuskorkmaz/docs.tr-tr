---
title: Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 06f3009d984f7a303a0ee6e8d529a3ff60900fbc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498693"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)
Bir yordamı çağırdığınızda, genellikle bir veya daha fazla bağımsız değişken geçirin. Her bir bağımsız değişkenin temel alınan bir programlama öğesine karşılık gelir. Temel alınan öğeleri hem bağımsız değiştirilebilir veya değiştirilemez olabilir.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Öğeler değiştirilebilir ve değiştirilemez  
 Bir programlama öğesi olabilir bir *değiştirilebilir öğesi*, değişen değeri olabilir veya *değiştirilemez öğenin*, oluşturulduktan sonra sabit bir değere sahip.  
  
 Aşağıdaki tabloda, değiştirilebilir ve değiştirilemez programlama öğelerini listeler.  
  
|Değiştirilebilir öğeleri|Değiştirilemez öğeleri|  
|-------------------------|----------------------------|  
|Salt okunur hariç nesne değişkenleri (yordamların içinde bildirilen), yerel değişkenleri de dahil olmak üzere|Salt okunur değişkenler, alanlar ve Özellikler|  
|Salt okunur dışında alanlar (üye değişkenleri) modülleri, sınıflar ve yapılar|Sabit ve değişmez değerleri|  
|Salt okunur dışındaki özellikleri|Numaralandırma üyeleri|  
|Dizi öğeleri|İfadeler (öğeleri değiştirilebilir olsa bile)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Değiştirilebilir ve değiştirilemez bağımsız değişkenler  
 A *değiştirilebilir bağımsız değişken* değiştirilebilir bir temel alınan öğe biridir. Çağıran kod, herhangi bir zamanda yeni bir değer depolayabilir ve bağımsız değişken geçirirseniz [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), yordamda kod çağıran koddaki temel alınan öğe de değiştirebilirsiniz.  
  
 A *değiştirilemez bağımsız değişken* değiştirilemez bir alt öğeye sahip ya da geçirilir [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Değiştirilebilir bir öğe olsa bile, yordamı çağıran kod, temel alınan öğe değiştiremezsiniz. Çağıran kod, değiştirilemez bir öğeyse, değiştiremezsiniz.  
  
 Değişiklik, temel alınan öğe çağıran koddaki etkilemez ancak bu, çağrılan yordam değiştirilemez bir bağımsız değişken yerel kopyasına değiştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Nasıl yapılır: Bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Nasıl yapılır: Bir yordam bağımsız değişkeninin değerini değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)
- [Nasıl yapılır: Bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Nasıl yapılır: Bağımsız değişkeni değere göre geçirilecek şekilde zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
