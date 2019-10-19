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
ms.openlocfilehash: 26df91229f7c640f53fcc018d881f7d24baf7e42
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582460"
---
# <a name="local-type-inference-visual-basic"></a>Yerel Türü Arabirimi (Visual Basic Başvurusu)

Visual Basic derleyici, bir `As` yan tümcesi olmadan bildirildiği yerel değişkenlerin veri türlerini belirlemekte *tür çıkarımı* kullanır. Derleyici, değişkenin türünü başlatma ifadesinin türünden algılar. Bu, aşağıdaki örnekte gösterildiği gibi, bir türü açıkça belirtmeden değişkenleri bildirmenize olanak sağlar. Bildirimlerin bir sonucu olarak, hem `num1` hem de `num2` tam olarak tamsayılar olarak türdedir.

[!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]

> [!NOTE]
> Önceki örnekte `num2` `Integer` olarak yazılmaları istemiyorsanız, `Dim num3 As Object = 3` veya `Dim num4 As Double = 3` gibi bir bildirim kullanarak başka bir tür belirtebilirsiniz.

> [!NOTE]
> Tür çıkarımı, yalnızca statik olmayan yerel değişkenler için kullanılabilir; sınıf alanları, özellikler veya işlevlerin türünü belirleyebilmek için kullanılamaz.

Yerel tür çıkarımı yordam düzeyinde geçerlidir. Modül düzeyinde (bir sınıf, yapı, modül veya arabirim içinde değil, yordam veya blok içinde değil) değişkenleri bildirmek için kullanılamaz. Önceki örnekteki `num2`, bir yordamda yerel bir değişken yerine bir sınıfın alanı olsaydı, bildirim, üzerinde `Option Strict` bir hataya neden olur ve `Option Strict` kapalı bir `Object` olarak `num2` sınıflandırır. Benzer şekilde, yerel tür çıkarımı `Static` olarak belirtilen yordam düzeyi değişkenlerine uygulanmaz.

## <a name="type-inference-vs-late-binding"></a>Tür çıkarımı ile geç bağlama

Tür çıkarımı kullanan kod, geç bağlamaya dayanan koda benzer. Ancak, tür çıkarımı türü `Object` olarak bırakmak yerine değişkeni kesin olarak türler. Derleyici, değişkenin türünü, erken bağlantılı kod oluşturmak için derleme zamanında değişkenin türünü tespit etmek için bir değişkenin başlatıcısı kullanır. Önceki örnekte, `num1` gibi `num2`, `Integer` olarak yazılır.

Erken bağlanan değişkenlerin davranışı, türü yalnızca çalışma zamanında bilinen, geç bağlanan değişkenlerden farklıdır. Türün erken olması, derleyicinin yürütmeden önce sorunları belirlemesini, belleği tam olarak ayırmasını ve diğer iyileştirmeleri gerçekleştirmesini sağlar. Erken bağlama Ayrıca, Visual Basic tümleşik geliştirme ortamının (IDE) bir nesnenin üyeleri hakkında IntelliSense yardımı sağlamasına olanak sağlar. Erken bağlama de performans için tercih edilir. Bunun nedeni, bir geç bağlantılı değişkende depolanan tüm verilerin `Object` tür olarak sarmalanması ve çalışma zamanında türün üyelerine erişilmesi, programın daha yavaş olmasını sağlar.

## <a name="examples"></a>Örnekler

Yerel bir değişken bir `As` yan tümcesi olmadan bildirildiğinde ve başlatıldıktan sonra tür çıkarımı oluşur. Derleyici, değişkenin türü olarak atanan ilk değerin türünü kullanır. Örneğin, aşağıdaki kod satırlarının her biri `String` türünde bir değişken bildirir.

[!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]

Aşağıdaki kod, tamsayılar dizisi oluşturmanın iki denk yolunu gösterir.

[!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]

Döngü denetim değişkeninin türünü belirleyebilmek için tür çıkarımı kullanmak uygun değildir. Aşağıdaki kodda, önceki örnekteki `someNumbers2` bir tamsayılar dizisi olduğundan derleyici `number` `Integer`.

[!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]

Yerel tür çıkarımı, aşağıdaki örnekte gösterildiği gibi, kaynak adının türünü oluşturmak için `Using` ifadelerde kullanılabilir.

[!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]

Aşağıdaki örnekte gösterildiği gibi, bir değişkenin türü, işlevlerin dönüş değerlerinden de çıkarsanamıyor. @No__t_0 ve `pList2`, `Process.GetProcesses` bir işlem dizisi döndürdüğünden işlem dizilerdir.

[!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]

## <a name="option-infer"></a>Seçenek çıkarımı

`Option Infer`, yerel tür çıkarımını belirli bir dosyada izin verilip verilmeyeceğini belirtmenizi belirler. Seçeneği etkinleştirmek veya engellemek için, dosyanın başlangıcında aşağıdaki deyimlerden birini yazın.

`Option Infer On`

`Option Infer Off`

Kodunuzda `Option Infer` için bir değer belirtmezseniz, varsayılan derleyici `Option Infer On`.

Bir dosyadaki `Option Infer` için ayarlanan değer IDE 'de veya komut satırında ayarlanan değer ile çakışıyorsa, dosyadaki değerin önceliği vardır.

Daha fazla bilgi için bkz. [Option Infer deyimleri](../../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [derleme sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).

## <a name="see-also"></a>Ayrıca bkz.

- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Erken ve Geç Bağlama](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [For Each...Next Deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next Deyimi](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Option Infer Deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
