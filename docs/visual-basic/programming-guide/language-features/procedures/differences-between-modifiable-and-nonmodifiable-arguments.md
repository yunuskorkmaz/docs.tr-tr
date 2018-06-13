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
ms.openlocfilehash: 2b60d732b260ad0477946e41ece4cd182de541ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649769"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)
Bir yordam çağrısı, genellikle bir veya daha fazla bağımsız değişken için geçirdiğiniz. Her bağımsız bir temel programlama öğeye karşılık gelir. Temel alınan öğeleri ve bağımsız değişkenler kendilerini değiştirilebilir veya değiştirilemez olabilir.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Değiştirilebilir ve değiştirilemez öğeleri  
 Bir programlama öğesi ya da olabilir bir *değiştirilebilir öğesi*, değişti, değeri olabilir veya bir *değiştirilemez öğesi*, oluşturulduktan sonra bir sabit değere sahip.  
  
 Aşağıdaki tabloda, değiştirilebilir ve değiştirilemez programlama öğeleri listeler.  
  
|Değiştirilebilir öğeleri|Değiştirilemez öğeleri|  
|-------------------------|----------------------------|  
|Salt okunur dışında nesne değişkenleri (yordamların içinde bildirilen), yerel değişkenleri dahil|Salt okunur değişkenler, alanlar ve Özellikler|  
|Salt okunur dışında alanları (üye değişkenleri) modülleri, sınıflar ve yapılar|Sabit ve değişmez değerleri|  
|Salt okunur dışında özellikleri|Numaralandırma üyeleri|  
|Dizi öğeleri|Deyimler (öğelerini değiştirilebilir olsa bile)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Değiştirilebilir ve değiştirilemez bağımsız değişkenler  
 A *değiştirilebilir bağımsız değişkeni* değiştirilebilir ve temel bir öğesiyle biridir. Çağrıyı yapan kod herhangi bir zamanda yeni bir değer depolayabilir ve bağımsız değişken geçirirseniz [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), yordamdaki kod çağıran kodu temel alınan öğe de değiştirebilirsiniz.  
  
 A *değiştirilemez bağımsız değişkeni* değiştirilemez bir temel öğeye sahip ya da geçirilen [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Değiştirilebilir öğesi olsa bile, yordamı çağıran kodu, temel alınan öğe değiştirilemiyor. Bunu değiştirilemez bir öğeyse, çağrıyı yapan kod onu değiştiremezsiniz.  
  
 Değişiklik çağıran kodu temel alınan öğe etkilemez ancak bu adlı yordamı değiştirilemez bağımsız değişkeni yerel kopyasını değiştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)  
 [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
