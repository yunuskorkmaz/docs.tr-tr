---
title: "Nasıl yapılır: Visual Basic'te Dizi Değişkeni Başlatma"
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: ee8cb91fd2fae9637a0d0e33fca63a4cdb9d2fce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te Dizi Değişkeni Başlatma
Dizi değişmez değer de dahil olmak üzere bir dizi değişkeni başlatma bir `New` yan tümcesi ve dizinin ilk değerleri belirtme. Türünü belirtin veya değişmez değer dizideki olayla izin verin. Ne tür çıkarımı yapılan hakkında daha fazla bilgi için "Doldurma bir dizi ile ilk değerleri" bölümüne bakın. [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>Değişmez değer bir dizi kullanarak bir dizi değişkeni başlatılamadı  
  
-   Ya da `New` yan tümcesi veya dizi değeri atadığınızda, köşeli parantez içindeki öğe değerlerini sağlayın (`{}`). Aşağıdaki örnek, bildirme, oluşturma ve bir değişken türü öğesi içeren bir dizi içerecek şekilde başlatmak için çeşitli yollar gösterir `Char`.  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     Her deyim yürütüldükten sonra oluşturulan dizi dizini ilk değerleri içeren 2 aracılığıyla dizin 0 konumunda öğelerle 3 uzunluğuna sahip. Üst sınır ve değerlerini sağlarsanız, üst sınır aracılığıyla 0 dizinden her öğe için bir değer içermelidir.  
  
     Değişmez değer bir dizi öğesi değerlerini sağlarsanız dizini üst sınırı belirtin gerekmez dikkat edin. Üst sınır belirtilirse, dizinin boyutunu değişmez değer dizideki sayısına dayalı olarak algılanır.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>Dizi değişmez değerleri kullanarak çok boyutlu bir diziye başlatmak için  
  
-   İç içe köşeli parantez içindeki değerleri (`{}`) küme ayraçları içinde. Tümü aynı türde ve uzunluk dizileri olarak Infer iç içe geçmiş dizi değişmez değerleri emin olun. Aşağıdaki kod örneğinde boyutlu bir diziye başlatma bazı örnekleri gösterilmektedir.  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   Açıkça dizi sınırları belirtin ya da bunları dışlamayı ve değişmez değer dizideki değerlere göre dizi sınırları Infer derleyici sahip. Üst sınırları ve değerlerini sağlarsanız, her boyut üst sınırı aracılığıyla 0 dizinden her öğe için bir değer içermelidir. Aşağıdaki örnek, bildirme, oluşturma ve türündeki öğeler sahip iki boyutlu bir dizi içeren bir değişkeni başlatmak için çeşitli yollar gösterir. `Short`  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     Her deyim yürütüldükten sonra oluşturulan dizi dizine sahip altı başlatılmış öğeleri içerir `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, ve `(1,2)`. Her bir dizi konum değeri içeren `10`.  
  
-   Aşağıdaki örnek, çok boyutlu bir diziye yineler. Visual Basic ile yazılmış bir Windows konsol uygulaması içinde içinde kod yapıştırın `Sub Main()` yöntemi. Son açıklamaları çıktısını göster.  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>Dizi değişmez değerleri kullanarak basit bir diziye başlatmak için  
  
-   İç içe nesne değerleri kaşlı ayraçlar içinde (`{}`). Ayrıca, basit bir dizi söz konusu olduğunda farklı uzunlukta diziler belirtin dizi değişmez değerleri geçirebilmenize rağmen emin olun, iç içe geçmiş dizi değişmez değerleri parantez içine alınmış (`()`). İç içe geçmiş dizi değişmez değerleri değerlendirmesi parantez zorlamak ve sonuçta elde edilen diziler Basit dizi ilk değerleri olarak kullanılır. Aşağıdaki kod örneği iki örnek basit dizi başlatma gösterir.  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   Aşağıdaki örnekte basit bir dizisini yineler. Visual Basic ile yazılmış bir Windows konsol uygulaması içinde içinde kod yapıştırın `Sub Main()` yöntemi.  Kodu son açıklamalarda çıktısını göster.  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Dizilerle İlgili Sorun Giderme](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
