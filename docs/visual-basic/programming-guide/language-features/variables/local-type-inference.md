---
title: Yerel Türü Arabirimi (Visual Basic Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: b33b8b2d17c240e380377528d4f5d2f511381a7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="local-type-inference-visual-basic"></a>Yerel Türü Arabirimi (Visual Basic Başvurusu)
Visual Basic derleyici kullanan *türü çıkarımı* olmadan bildirilen yerel değişkenleri veri türlerini belirlemek için bir `As` yan tümcesi. Derleyici başlatma ifade türü değişkeninden türü oluşturur. Bu, açıkça bir türü bildirmeden aşağıdaki örnekte gösterildiği gibi değişkenleri olanak sağlar. Bildirimleri sonucunda her ikisi de `num1` ve `num2` tamsayı olarak kesin türü belirtilmiş.  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
 
> [!NOTE]
>  İstemiyorsanız, `num2` olarak yazılması için önceki örnekte bir `Integer`, bir bildirimi gibi kullanarak başka bir tür belirtebilirsiniz `Dim num3 As Object = 3` veya `Dim num4 As Double = 3`.  

> [!NOTE]
>  Tür çıkarımı yalnızca statik olmayan yerel değişkenler için kullanılabilir; class alanları, özellikler veya İşlevler türünü belirlemek için kullanılamaz.
 
 Yerel türü çıkarımı yordamı düzeyinde uygulanır. Modül düzeyinde (sınıf, yapı, modül veya arabirimi içinde ancak bir yordam veya bloğu içinde değil) değişkenleri bildirmek için kullanılamaz. Varsa `num2` önceki örnekte bir yordam yerel bir değişkende yerine sınıfının bir alanı, hata bildirimi neden olur `Option Strict` ve sınıflandırabilir `num2` olarak bir `Object` ile `Option Strict` devre dışı. Benzer şekilde, yerel türü çıkarımı olarak bildirilen yordam düzeyi değişkenler uygulanmaz `Static`.  
  
## <a name="type-inference-vs-late-binding"></a>Çıkarım vs yazın. Geç bağlama  
 Tür çıkarımı kullanan kodu geç bağlama dayanır kod benzer. Ancak, tür çıkarımı olarak bırakarak yerine değişkeni kesinlikle türleri `Object`. Derleyici değişkenin Başlatıcı erken bağlama kod üretmek için derleme zamanında değişkenin türü belirlemek için kullanır. Önceki örnekte, `num2`gibi `num1`, olarak yazılan bir `Integer`.  
  
 Erken bağlama değişkenleri davranışını, yalnızca çalışma zamanında türü bilinen geç bağlama değişkenlerin farklılık gösterir. Türü erken bilerek yürütmeden önce sorunları belirlemek, tam olarak bellek ve diğer en iyi duruma getirme gerçekleştirmek derleyici sağlar. Erken bağlama, Visual Basic tümleşik geliştirme ortamını (IDE) bir nesnenin üyelerine hakkında IntelliSense Yardım sağlamak için de sağlar. Erken bağlama da performans için tercih edilir. Geç bağlama değişkeninde depolanan tüm verileri türü olarak alınmalıdır olmasıdır `Object`, ve çalışma zamanında tür üyelerine erişme programın yavaş yapar.  
  
## <a name="examples"></a>Örnekler  
 Tür çıkarımı oluşuyor yerel bir değişken olmadan bildirilmiş bir `As` yan tümcesi ve başlatıldı. Derleyici atanan ilk değer türü değişkeni türü olarak kullanır. Örneğin, aşağıdaki kod satırlarını her türünde bir değişken bildirir `String`.  
  
 [!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 Aşağıdaki kod dizisi oluşturmak için iki eşdeğer yol gösterir.  
  
 [!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 Tür çıkarımı for döngüsü denetim değişkeni türü belirlemek amacıyla kullanmak uygundur. Aşağıdaki kodda, derleyici, oluşturur `number` olan bir `Integer` çünkü `someNumbers2` önceki örnekten tamsayılar dizisidir.  
  
 [!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 Yerel türü çıkarımı kullanılabilir `Using` aşağıdaki örnekte gösterilmiştir gibi tür bir kaynak adın kurmaya deyimleri.  
  
 [!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 Aşağıdaki örnekte gösterilmiştir gibi bir değişken türü, işlevlerin dönüş değerleri de çıkarsanabileceği. Her ikisi de `pList1` ve `pList2` işlemleri dizileri olduklarından `Process.GetProcesses` işlemleri bir dizi döndürür.  
  
 [!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## <a name="option-infer"></a>Option Infer  
 `Option Infer` Yerel türü çıkarımı belli bir dosyada izin verilip verilmeyeceğini belirtin etkinleştirir. Etkinleştirmek veya seçeneği engellemek için aşağıdaki ifadeleri birini dosya başlangıcında yazın.  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 İçin bir değer belirtmezseniz, `Option Infer` kodunuzda derleyici varsayılandır `Option Infer On`. Projeleri sürümüne için [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] veya önceki sürümlerini, derleyici varsayılan `Option Infer Off`.  
  
 Değeri ayarlarsanız `Option Infer` IDE veya komut satırında ayarlanan değer ile dosya çakışmalarını içinde dosyasındaki değer önceliğe sahiptir.  
  
 Daha fazla bilgi için bkz: [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Erken ve Geç Bağlama](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [For Each...Next Deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next Deyimi](../../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Option Infer Deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
