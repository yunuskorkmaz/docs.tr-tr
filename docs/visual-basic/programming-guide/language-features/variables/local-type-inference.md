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
ms.openlocfilehash: 59559f8775a5fd66a567897b009272df1727b1e8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953325"
---
# <a name="local-type-inference-visual-basic"></a>Yerel Türü Arabirimi (Visual Basic Başvurusu)
Visual Basic derleyici, bir `As` yan tümce olmadan belirtilen yerel değişkenlerin veri türlerini belirlemede *tür çıkarımı* kullanır. Derleyici, değişkenin türünü başlatma ifadesinin türünden algılar. Bu, aşağıdaki örnekte gösterildiği gibi, bir türü açıkça belirtmeden değişkenleri bildirmenize olanak sağlar. Bildirimlerin bir sonucu olarak, `num1` ve `num2` kesin olarak tam sayı olarak türdedir.  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
> Önceki `num2` örnekte bir `Integer`olarak yazılmaları istemiyorsanız, veya `Dim num4 As Double = 3`gibi `Dim num3 As Object = 3` bir bildirim kullanarak başka bir tür belirtebilirsiniz.  

> [!NOTE]
> Tür çıkarımı, yalnızca statik olmayan yerel değişkenler için kullanılabilir; sınıf alanları, özellikler veya işlevlerin türünü belirleyebilmek için kullanılamaz.
 
 Yerel tür çıkarımı yordam düzeyinde geçerlidir. Modül düzeyinde (bir sınıf, yapı, modül veya arabirim içinde değil, yordam veya blok içinde değil) değişkenleri bildirmek için kullanılamaz. `num2` `Option Strict` `Option Strict` `Object` Önceki örnekte, bir yordamda yerel bir değişken yerine bir sınıfın alanı olsaydı, bildirim üzerinde bir hataya neden olur ve ile bir olarak sınıflandırır. `num2` Benzer şekilde, yerel tür çıkarımı olarak `Static`belirtilen yordam düzeyi değişkenlerine uygulanmaz.  
  
## <a name="type-inference-vs-late-binding"></a>Tür çıkarımı ile Geç bağlama  
 Tür çıkarımı kullanan kod, geç bağlamaya dayanan koda benzer. Ancak tür çıkarımı, değişkeni olarak bırakmak yerine değişkeni kesin bir şekilde `Object`bırakır. Derleyici, değişkenin türünü, erken bağlantılı kod oluşturmak için derleme zamanında değişkenin türünü tespit etmek için bir değişkenin başlatıcısı kullanır. Önceki örnekte `num2` `num1`, gibi, bir `Integer`olarak yazılır.  
  
 Erken bağlanan değişkenlerin davranışı, türü yalnızca çalışma zamanında bilinen, geç bağlanan değişkenlerden farklıdır. Türün erken olması, derleyicinin yürütmeden önce sorunları belirlemesini, belleği tam olarak ayırmasını ve diğer iyileştirmeleri gerçekleştirmesini sağlar. Erken bağlama Ayrıca, Visual Basic tümleşik geliştirme ortamının (IDE) bir nesnenin üyeleri hakkında IntelliSense yardımı sağlamasına olanak sağlar. Erken bağlama de performans için tercih edilir. Bunun nedeni, geç bağlantılı bir değişkende depolanan tüm verilerin tür `Object`olarak sarmalanması ve çalışma zamanında tür üyelerine erişmesi, programın daha yavaş olmasına neden olur.  
  
## <a name="examples"></a>Örnekler  
 Yerel bir değişken bir `As` yan tümce olmadan bildirildiğinde ve başlatıldığında tür çıkarımı oluşur. Derleyici, değişkenin türü olarak atanan ilk değerin türünü kullanır. Örneğin, aşağıdaki kod satırlarının her biri türünde `String`bir değişken bildirir.  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 Aşağıdaki kod, tamsayılar dizisi oluşturmanın iki denk yolunu gösterir.  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 Döngü denetim değişkeninin türünü belirleyebilmek için tür çıkarımı kullanmak uygun değildir. Aşağıdaki kodda, `number` birönceki`Integer` örnekteki bir tamsayılar dizisi olduğu için derleyici bir. `someNumbers2`  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 Yerel tür çıkarımı, aşağıdaki örnekte `Using` gösterildiği gibi, kaynak adının türünü oluşturmak için ifadelerde kullanılabilir.  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 Aşağıdaki örnekte gösterildiği gibi, bir değişkenin türü, işlevlerin dönüş değerlerinden de çıkarsanamıyor. Her `pList1` ikisi `pList2` ve işlem dizileri, çünkü `Process.GetProcesses` bir işlem dizisi döndürür.  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a>Seçenek çıkarımı  
 `Option Infer`belirli bir dosyada yerel tür çıkarımı izin verilip verilmeyeceğini belirtmenizi belirler. Seçeneği etkinleştirmek veya engellemek için, dosyanın başlangıcında aşağıdaki deyimlerden birini yazın.  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 Kodunuzda için `Option Infer` bir değer belirtmezseniz, derleyici varsayılanı olur `Option Infer On`. 
  
 Bir dosyada için `Option Infer` ayarlanan değer IDE 'de veya komut satırında ayarlanan değerle çakışıyorsa, dosyadaki değerin önceliği vardır.  
  
 Daha fazla bilgi için bkz. [Option Infer deyimleri](../../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [derleme sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Erken ve Geç Bağlama](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [For Each...Next Deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next Deyimi](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Option Infer Deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
