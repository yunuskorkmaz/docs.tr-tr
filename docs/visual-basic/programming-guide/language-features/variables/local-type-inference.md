---
title: Yerel Tür Arabirimi
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
ms.openlocfilehash: 3979396d32aa5d3b853aa087d43f70d5987e510b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410405"
---
# <a name="local-type-inference-visual-basic"></a>Yerel Türü Arabirimi (Visual Basic Başvurusu)

Visual Basic derleyici, bir yan tümce olmadan belirtilen yerel değişkenlerin veri türlerini belirlemede *tür çıkarımı* kullanır `As` . Derleyici, değişkenin türünü başlatma ifadesinin türünden algılar. Bu, aşağıdaki örnekte gösterildiği gibi, bir türü açıkça belirtmeden değişkenleri bildirmenize olanak sağlar. Bildirimlerin bir sonucu olarak, `num1` ve `num2` kesin olarak tam sayı olarak türdedir.

[!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]

> [!NOTE]
> `num2`Önceki örnekte bir olarak yazılmaları istemiyorsanız `Integer` , veya gibi bir bildirim kullanarak başka bir tür belirtebilirsiniz `Dim num3 As Object = 3` `Dim num4 As Double = 3` .

> [!NOTE]
> Tür çıkarımı, yalnızca statik olmayan yerel değişkenler için kullanılabilir; sınıf alanları, özellikler veya işlevlerin türünü belirleyebilmek için kullanılamaz.

Yerel tür çıkarımı yordam düzeyinde geçerlidir. Modül düzeyinde (bir sınıf, yapı, modül veya arabirim içinde değil, yordam veya blok içinde değil) değişkenleri bildirmek için kullanılamaz. `num2`Önceki örnekte, bir yordamda yerel bir değişken yerine bir sınıfın alanı olsaydı, bildirim üzerinde bir hataya neden olur `Option Strict` ve `num2` ile bir olarak sınıflandırır `Object` `Option Strict` . Benzer şekilde, yerel tür çıkarımı olarak belirtilen yordam düzeyi değişkenlerine uygulanmaz `Static` .

## <a name="type-inference-vs-late-binding"></a>Tür çıkarımı ile geç bağlama

Tür çıkarımı kullanan kod, geç bağlamaya dayanan koda benzer. Ancak tür çıkarımı, değişkeni olarak bırakmak yerine değişkeni kesin bir şekilde bırakır `Object` . Derleyici, değişkenin türünü, erken bağlantılı kod oluşturmak için derleme zamanında değişkenin türünü tespit etmek için bir değişkenin başlatıcısı kullanır. Önceki örnekte, gibi, `num2` `num1` bir olarak yazılır `Integer` .

Erken bağlanan değişkenlerin davranışı, türü yalnızca çalışma zamanında bilinen, geç bağlanan değişkenlerden farklıdır. Türün erken olması, derleyicinin yürütmeden önce sorunları belirlemesini, belleği tam olarak ayırmasını ve diğer iyileştirmeleri gerçekleştirmesini sağlar. Erken bağlama Ayrıca, Visual Basic tümleşik geliştirme ortamının (IDE) bir nesnenin üyeleri hakkında IntelliSense yardımı sağlamasına olanak sağlar. Erken bağlama de performans için tercih edilir. Bunun nedeni, geç bağlantılı bir değişkende depolanan tüm verilerin tür olarak sarmalanması `Object` ve çalışma zamanında tür üyelerine erişmesi, programın daha yavaş olmasına neden olur.

## <a name="examples"></a>Örnekler

Yerel bir değişken bir yan tümce olmadan bildirildiğinde ve başlatıldığında tür çıkarımı oluşur `As` . Derleyici, değişkenin türü olarak atanan ilk değerin türünü kullanır. Örneğin, aşağıdaki kod satırlarının her biri türünde bir değişken bildirir `String` .

[!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]

Aşağıdaki kod, tamsayılar dizisi oluşturmanın iki denk yolunu gösterir.

[!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]

Döngü denetim değişkeninin türünü belirleyebilmek için tür çıkarımı kullanmak uygun değildir. Aşağıdaki kodda, `number` bir `Integer` önceki örnekteki bir tamsayılar dizisi olduğu için derleyici bir `someNumbers2` .

[!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]

Yerel tür çıkarımı, `Using` Aşağıdaki örnekte gösterildiği gibi, kaynak adının türünü oluşturmak için ifadelerde kullanılabilir.

[!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]

Aşağıdaki örnekte gösterildiği gibi, bir değişkenin türü, işlevlerin dönüş değerlerinden de çıkarsanamıyor. Her ikisi `pList1` ve `pList2` işlem dizileri, çünkü `Process.GetProcesses` bir işlem dizisi döndürür.

[!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]

## <a name="option-infer"></a>Seçenek çıkarımı

`Option Infer`belirli bir dosyada yerel tür çıkarımı izin verilip verilmeyeceğini belirtmenizi belirler. Seçeneği etkinleştirmek veya engellemek için, dosyanın başlangıcında aşağıdaki deyimlerden birini yazın.

`Option Infer On`

`Option Infer Off`

Kodunuzda için bir değer belirtmezseniz `Option Infer` , derleyici varsayılanı olur `Option Infer On` .

Bir dosyada için ayarlanan değer `Option Infer` IDE 'de veya komut satırında ayarlanan değerle çakışıyorsa, dosyadaki değerin önceliği vardır.

Daha fazla bilgi için bkz. [Option Infer deyimleri](../../../language-reference/statements/option-infer-statement.md) ve [derleme sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).

## <a name="see-also"></a>Ayrıca bkz.

- [Anonim Türler](../objects-and-classes/anonymous-types.md)
- [Erken ve geç bağlama](../early-late-binding/index.md)
- [For Each...Next Deyimi](../../../language-reference/statements/for-each-next-statement.md)
- [For...Next Deyimi](../../../language-reference/statements/for-next-statement.md)
- [Option Infer Deyimi](../../../language-reference/statements/option-infer-statement.md)
- [-optioninfer](../../../reference/command-line-compiler/optioninfer.md)
- [Visual Basic'de LINQ'e Giriş](../linq/introduction-to-linq.md)
