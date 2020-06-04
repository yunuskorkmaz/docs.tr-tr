---
title: 'Nasıl yapılır: Dizi Değişkeni Başlatma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 7feaf71fa1c59c24aa751f2b9e28328d47ba357c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413072"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te Dizi Değişkeni Başlatma
Bir yan tümcesine dizi değişmez değeri ekleyerek `New` ve dizinin başlangıç değerlerini belirterek bir dizi değişkenini başlatırsınız. Türü belirtebilir veya dizi sabit değerindeki değerlerden çıkarsanamıyor izin verebilirsiniz. Türün nasıl çıkarsandığına ilişkin daha fazla bilgi için, [diziler](index.md)Içindeki "başlangıç değerleriyle bir diziyi doldurma" konusuna bakın.  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>Dizi değişmezi kullanarak bir dizi değişkeni başlatmak için  
  
- `New`Yan tümcesinde veya dizi değerini atadığınızda, öğe değerlerini küme ayracı () içinde sağlayın `{}` . Aşağıdaki örnek, türünde öğeleri olan bir dizi içeren bir değişkeni bildirmek, oluşturmak ve başlatmak için çeşitli yollar gösterir `Char` .  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     Her bir deyimden sonra oluşturulan dizi 3 uzunluğuna sahiptir ve dizin 0 ' dan başlayarak başlangıç değerlerini içeren dizin 2 ' dir. Hem üst sınırı hem de değerleri sağlarsanız, üst sınır aracılığıyla 0 dizininden her öğe için bir değer eklemelisiniz.  
  
     Dizi sabit değerinde öğe değerleri sağlarsanız, dizin üst sınırını belirtmeniz gerekmez. Üst sınır belirtilmemişse, dizi boyutu dizi sabit değerindeki değer sayısına göre algılanır.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>Dizi değişmez değerlerini kullanarak çok boyutlu bir dizi değişkeni başlatmak için  
  
- Küme ayraçları içinde parantez () içinde iç içe değerler `{}` . İç içe geçmiş dizi değişmez değerlerinin tümünün aynı türdeki ve uzunluktaki diziler olarak çıkardığına emin olun. Aşağıdaki kod örneğinde çok boyutlu dizi başlatmanın birkaç örneği gösterilmektedir.  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- Dizi sınırlarını açıkça belirtebilir veya dışarı bırakabilir ve derleyicinin dizi sınırlarını, dizi değişmez değerindeki değerlere göre çıkarmasını sağlayabilirsiniz. Hem üst sınırı hem de değerleri sağlarsanız, her boyuttaki üst sınır aracılığıyla 0 dizininden her öğe için bir değer eklemelisiniz. Aşağıdaki örnek, türünde öğeleri olan iki boyutlu bir dizi içeren bir değişkeni bildirmek, oluşturmak ve başlatmak için çeşitli yollar gösterir`Short`  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     Her bir deyimden sonra oluşturulan dizi,,,,, ve dizinleri olan altı adet başlatılmış öğe içerir `(0,0)` `(0,1)` `(0,2)` `(1,0)` `(1,1)` `(1,2)` . Her dizi konumu değeri içerir `10` .  
  
- Aşağıdaki örnek, çok boyutlu bir dizi aracılığıyla yinelenir. Visual Basic yazılan bir Windows konsol uygulamasında kodu yönteminin içine yapıştırın `Sub Main()` . Son açıklamalar çıktıyı gösterir.  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>Dizi değişmez değerlerini kullanarak pürüzlü bir dizi değişkeni başlatmak için  
  
- Nesne değerlerini küme ayracı () içinde iç içe `{}` . Ayrıca, farklı uzunluklardan oluşan dizileri belirten dizi sabit değerlerini iç içe geçirebilirsiniz, ancak pürüzlü bir dizi söz konusu olduğunda, iç içe geçmiş dizi değişmez değerlerinin parantez () içine alındığına emin olun `()` . Parantezler, iç içe geçmiş dizi değişmez değerlerinin değerlendirilmesini zorlar ve ortaya çıkan diziler, pürüzlü dizinin başlangıç değerleri olarak kullanılır. Aşağıdaki kod örneğinde, pürüzlü dizi başlatmanın iki örneği gösterilmektedir.  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- Aşağıdaki örnek, pürüzlü bir dizi aracılığıyla yinelenir. Visual Basic yazılan bir Windows konsol uygulamasında kodu yönteminin içine yapıştırın `Sub Main()` .  Koddaki son açıklamalar çıktıyı gösterir.  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Diziler](index.md)
- [Dizilerle İlgili Sorun Giderme](troubleshooting-arrays.md)
