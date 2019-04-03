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
ms.openlocfilehash: e6214938262b987a1bae4a9ca1d5c945f8b7fe6e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826827"
---
# <a name="local-type-inference-visual-basic"></a>Yerel Türü Arabirimi (Visual Basic Başvurusu)
Visual Basic Derleyicisi kullanan *anlam çıkarma* olmadan bildirilen yerel değişkenlerin veri türlerini belirlemek için bir `As` yan tümcesi. Derleyici, başlatma ifadesinin türünden değişkeninin türü çıkarır. Bu, açıkça bir türü bildirmeden aşağıdaki örnekte gösterildiği gibi değişkenleri tanımlayın sağlar. Bildirimleri sonucu olarak hem de `num1` ve `num2` tamsayı olarak kesin olarak belirlenmiştir.  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
>  İstemiyorsanız, `num2` olarak yazılması için önceki örnekte bir `Integer`, gibi bir bildirim kullanarak başka bir tür belirtebilirsiniz `Dim num3 As Object = 3` veya `Dim num4 As Double = 3`.  

> [!NOTE]
>  Tür çıkarımı, yalnızca statik olmayan yerel değişkenler için kullanılabilir. sınıf alanlar, özellikler veya İşlevler türünü belirlemek için kullanılamaz.
 
 Yerel tür çıkarımı yordamı düzeyinde uygulanır. Modül düzeyinde (bir sınıf, yapı, modül veya arabirimi içinde ancak bir yordam veya blok içinde değil) değişkenler bildirmek için kullanılamaz. Varsa `num2` önceki örnekte yerine yerel bir değişken bir yordamda bir sınıfının bir alanı, bildirimi ile ilgili bir hata oluşturabilecek `Option Strict` ve sınıflandırabilir `num2` olarak bir `Object` ile `Option Strict` devre dışı. Benzer şekilde, yerel tür çıkarımı olarak bildirilen yordam düzeyi değişkenler uygulanmaz `Static`.  
  
## <a name="type-inference-vs-late-binding"></a>Çıkarım vs yazın. Geç bağlama  
 Tür çıkarımı kullanan kod geç bağlama kullanan koda benzer. Tür çıkarımı kesin olarak bırakmak yerine değişken türleri ancak `Object`. Derleyici, değişkenin türüne erken bağlanan kod üretmek için derleme zamanında belirlemek için bir değişken başlatıcı kullanır. Önceki örnekte, `num2`gibi `num1`, olarak belirlenmiş bir `Integer`.  
  
 Erken bağlanmış değişkenleri davranışı, geç bağlanan değişken, yalnızca çalışma zamanında bilinen türü için farklıdır. Türü erken bilmek yürütmeden önce sorunları belirlemenize, tam olarak bellek ve diğer iyileştirmeler gerçekleştirmek derleyiciyi etkinleştirir. Erken bağlama, ayrıca Visual Basic tümleşik geliştirme ortamı (IDE) IntelliSense Yardım bir nesnenin üyelerine hakkında sağlamaya olanak tanır. Erken bağlama de performans için tercih edilir. Geç bağlama değişkeninde depolanan tüm veriler türü olarak alınmalıdır olmasıdır `Object`, ve tür üyelerinin çalışma zamanında erişme programın daha yavaş hale getirir.  
  
## <a name="examples"></a>Örnekler  
 Tür çıkarımı oluşuyor olmadan bildirilen yerel değişken bir `As` yan tümcesi ve başlatılır. Derleyici, değişken türü olarak atanan başlangıç değeri türünü kullanır. Örneğin, her biri aşağıdaki kod satırlarını türünde bir değişken bildirir `String`.  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 Aşağıdaki kod, tamsayı dizisi oluşturmak için iki eşdeğer yol gösterir.  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 Bir for döngüsü denetim değişkeni türünü tür çıkarımı kullanmak uygundur. Derleyici aşağıdaki kodda algılar `number` olduğu bir `Integer` çünkü `someNumbers2` önceki örnekten tamsayılar dizisidir.  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 Yerel tür çıkarımı kullanılabilir `Using` ifadeleri, aşağıdaki örnekte de gösterildiği gibi kaynak adı, türü oluşturmak için.  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 Aşağıdaki örnekte de gösterildiği gibi bir değişken türü işlevlerinin dönüş değerleri de çıkarılan. Her ikisi de `pList1` ve `pList2` çünkü dizilerdir işlemlerin `Process.GetProcesses` süreçlerini bir dizi döndürür.  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a>Option Infer  
 `Option Infer` etkinleştirir, belirli bir dosya yerel tür çıkarımı izin verilip verilmeyeceğini belirtin. Dosyasının başında, etkinleştirmek veya seçeneği engellemek için aşağıdaki deyimleri birini yazın.  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 İçin bir değer belirtmezseniz `Option Infer` kodunuzda derleyici varsayılandır `Option Infer On`. Projeleri uygulamasından yükseltilen için [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] veya önceki sürümlerinde, derleyici varsayılan `Option Infer Off`.  
  
 Değeri ayarlarsanız `Option Infer` IDE veya komut satırında ayarlanan değer ile dosya çakışmalarını içinde dosyasındaki değeri önceliğe sahiptir.  
  
 Daha fazla bilgi için [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Erken ve Geç Bağlama](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [For Each...Next Deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next Deyimi](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Option Infer Deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
