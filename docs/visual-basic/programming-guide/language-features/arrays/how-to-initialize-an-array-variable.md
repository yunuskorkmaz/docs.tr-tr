---
title: "Nasıl yapılır: Visual Basic'te dizi değişkeni başlatma"
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 0e450a370c27de4690105231847de25ce5a90553
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627446"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te dizi değişkeni başlatma
Bir dizi değişmez değeri ekleyerek bir dizi değişkeni başlatmak bir `New` yan tümcesi ve dizinin başlangıç değerlerini belirterek. Türü belirtin veya dizi değişmez değerlerinin çıkarılan izin verebilirsiniz. Türün gösterilmesi hakkında daha fazla bilgi için bkz: "Doldurma bir dizeyi başlangıç değerleriyle" [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>Dizi değişmez değeri kullanarak dizi değişkeni başlatmak için  
  
- Ya da `New` yan tümcesi veya dizi değeri atadığınızda, öğe değerlerini ayraçlar içinde sağlayabilirsiniz (`{}`). Aşağıdaki örnek, bildirmek, oluşturmak ve türünde öğelere sahip bir dizi içeren bir değişkeni başlatmak için birçok yol gösterir. `Char`.  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     Her deyim yürütüldükten sonra oluşturulan dizi bir dizini ilk değerleri içeren 2 dizini aracılığıyla 0 dizininde öğelerle birlikte 3 oluşabilir. Hem üst sınırı hem de değerleri sağlarsanız, 0 dizininden üst sınıra kadar her öğe için bir değer içermesi gerekir.  
  
     Öğe değerlerini bir dizi değişmezinde sağlarsanız, dizin üst sınırını belirtmeniz gerekmez dikkat edin. Hiçbir üst sınır belirtilmediyse dizi boyutu dizi değişmez değerlerinin göre algılanır.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>Dizi değişmez değerleri kullanarak bir çok boyutlu dizi değişkeni başlatmak için  
  
- İç içe değerleri küme ayracı (`{}`) içinde yerleştirin. Tümü aynı türde ve uzunluktaki diziler tanım Çıkarsama iç içe geçmiş dizi değişmez değerleri emin olun. Aşağıdaki kod örneği, çeşitli çok boyutlu dizi başlatma örneklerini gösterir.  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- Açıkça dizi sınırları belirtin ya da bunları bırakın ve derleyicinin dizi sınırlarını dizi değişmez değerlere göre sağlayabilirsiniz. Hem üst sınırları hem de değerleri sağlarsanız, her boyutta, 0 dizininden üst sınıra kadar her öğe için bir değer içermesi gerekir. Aşağıdaki örnek, bildirmek, oluşturmak ve türünde öğelere sahip iki boyutlu bir dizi içeren bir değişkeni başlatmak için birçok yol gösterir. `Short`  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     Her deyim yürütüldükten sonra oluşturulan dize dizinlerine sahip altı tane başlatılmış öğeyi içerir `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, ve `(1,2)`. Her dizi konumuna değeri içeren `10`.  
  
- Aşağıdaki örnek, çok boyutlu bir dizi yinelenir. Visual Basic'te yazılmış bir Windows konsol uygulaması içinde içindeki kodu yapıştırın `Sub Main()` yöntemi. Son açıklamalar çıktıyı gösterir.  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>Dizi değişmez değerleri kullanarak basit bir dizi değişkeni başlatmak için  
  
- Nesne değerlerini küme ayraçları içinde (`{}`). Ayrıca düzensiz bir dizi farklı uzunluktaki dizileri belirten dizi değişmezlerini iç içe ancak iç içe geçmiş dizi değişmez değerlerini parantez içine alınmış emin olun (`()`). Parantezler iç içe geçmiş dizi değişmez değerlerinin değerlendirilmesini zorlar ve ortaya çıkan diziler düzensiz dizinin başlangıç değerleri kullanılır. Aşağıdaki kod örneği, iki düzensiz dizi başlatma örneklerini gösterir.  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- Aşağıdaki örnek bir düzensiz dizi aracılığıyla yinelenir. Visual Basic'te yazılmış bir Windows konsol uygulaması içinde içindeki kodu yapıştırın `Sub Main()` yöntemi.  Koddaki son açıklamalar çıktıyı gösterir.  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Dizilerle İlgili Sorun Giderme](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
