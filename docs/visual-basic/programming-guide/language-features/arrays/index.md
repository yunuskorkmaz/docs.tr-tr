---
title: Diziler
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
ms.openlocfilehash: 9dfe7814b00b4d060fa4ab9aa594faa948217d8d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351859"
---
# <a name="arrays-in-visual-basic"></a>Visual Basic'de Diziler

Dizi, mantıksal olarak birbirleriyle ilgili olan, adlandırılmış *öğeler*olan bir değerler kümesidir. Örneğin, bir dizi, bir dilbilgisi okulundaki her bir sınıfta bulunan öğrencilerin sayısından oluşabilir; dizideki her öğe, tek bir sınıfta bulunan öğrencilerin sayısıdır. Benzer şekilde, bir dizi bir sınıfın bir öğrenciye ait olan bir sınıftan oluşabilir; dizideki her öğe tek bir sınıf olur.

Her bir veri öğesini depolamak için bağımsız değişkenler mümkündür. Örneğin, uygulamamız öğrenci 'yi çözümlerimizde, her öğrencinin derecesi için `englishGrade1`, `englishGrade2`vb. gibi ayrı bir değişken kullanabiliriz. Bu yaklaşım üç önemli sınırlamalara sahiptir:

- Tasarım zamanında, işlemek zorunda olduğumuz çok sayıda Not olduğunu bilmeniz gerekir.
- Büyük sayıda denetimi hızla işlemek, çok daha hızlı hale gelir. Bu işlem, bir uygulamanın önemli hatalara karşı çok daha büyük bir hale gelmesini sağlar.
- Sürdürmek zordur. Eklediğimiz her yeni sınıf, uygulamanın değiştirilmesini, yeniden derlendiğini ve yeniden dağıtılmasını gerektirir.

Bir dizi kullanarak, aynı ada sahip bu ilgili değerlere başvurabilir ve dizideki konumuna göre tek bir öğeyi tanımlamak için *Dizin* veya *alt simge* olarak adlandırılan bir sayı kullanabilirsiniz. Bir dizinin dizinlerinden biri, dizideki öğelerin toplam sayısından küçük bir olan dizin aralığıdır. Bir dizinin boyutunu tanımlamak için Visual Basic sözdizimini kullandığınızda, dizideki toplam öğe sayısını değil, en yüksek dizinini belirtirsiniz. Dizi ile bir birim olarak çalışabilirsiniz ve öğelerini tekrarlayabilme özelliği, tasarım zamanında kaç öğe içerdiğini tam olarak öğrenmenize gerek kalmadan sizi serbest bırakabilirsiniz.

Açıklama öncesi bazı hızlı örnekler:

```vb
' Declare a single-dimension array of 5 numbers.
Dim numbers(4) As Integer

' Declare a single-dimension array and set its 4 values.
Dim numbers = New Integer() {1, 2, 4, 8}

' Change the size of an existing array to 16 elements and retain the current values.
ReDim Preserve numbers(15)

' Redefine the size of an existing array and reset the values.
ReDim numbers(15)

' Declare a 6 x 6 multidimensional array.
Dim matrix(5, 5) As Double

' Declare a 4 x 3 multidimensional array and set array element values.
Dim matrix = New Integer(3, 2) {{1, 2, 3}, {2, 3, 4}, {3, 4, 5}, {4, 5, 6}}

' Declare a jagged array
Dim sales()() As Double = New Double(11)() {}
```

## <a name="array-elements-in-a-simple-array"></a>Basit bir dizideki dizi öğeleri

Bir dilbilgisi okulundaki her bir sınıfta öğrenci sayısını depolamak için `students` adlı bir dizi oluşturalım. Öğelerin dizinleri 0 ile 6 arasında değişir. Bu diziyi kullanmak yedi değişken bildirenden daha basittir.

Aşağıdaki çizimde `students` dizisi gösterilmektedir. Dizideki her öğe için:

- Öğenin dizini, sınıfı temsil eder (Dizin 0, kindergaron öğesini temsil eder).

- Öğesinde yer alan değer, bu sınıfta bulunan öğrencilerin sayısını temsil eder.

![Öğrencilerin sayı dizisini gösteren diyagram](./media/index/students-array-elements.gif)

Aşağıdaki örnek, diziyi oluşturan ve kullanan Visual Basic kodu içerir:

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

Örnek üç şeyi yapar:

- Yedi öğe içeren bir `students` dizisi bildirir. Dizi bildiriminde `6` Sayı dizideki son dizini gösterir; dizideki öğe sayısından bir küçüktür.
- Dizideki her öğeye değerler atar. Dizi öğelerine, dizi adı kullanılarak erişilir ve parantez içinde tek bir öğenin dizini de eklenir.
- Dizinin her bir değerini listeler. Örnek, dizinin her öğesine Dizin numarası ile erişmek için bir [`For`](../../../language-reference/statements/for-next-statement.md) ifadesini kullanır.

Yukarıdaki örnekteki `students` dizisi tek boyutlu bir dizidir çünkü bir dizin kullanır. Birden fazla dizin veya alt simge kullanan bir dizi *çok boyutlu*olarak adlandırılır. Daha fazla bilgi için bu makalenin geri kalanına ve [dizi boyutlarına Visual Basic](../../language-features/arrays/array-dimensions.md)bakın.

## <a name="creating-an-array"></a>Dizi oluşturma

Bir dizinin boyutunu çeşitli yollarla tanımlayabilirsiniz:

- Dizinin bildirildiği zaman boyutunu belirtebilirsiniz:

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- Bir dizinin boyutunu oluşturulduğu sırada sağlamak için bir `New` yan tümcesi kullanabilirsiniz:

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

Mevcut bir diziniz varsa, [`ReDim`](../../../language-reference/statements/redim-statement.md) ifadesini kullanarak boyutunu yeniden tanımlayabilirsiniz. `ReDim` deyimin dizide bulunan değerleri tutabilmeniz veya boş bir dizi oluşturmasını belirtebilirsiniz. Aşağıdaki örnek, var olan bir dizinin boyutunu değiştirmek için `ReDim` deyimin farklı kullanımlarını gösterir.

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

Daha fazla bilgi için [ReDim bildirimine](../../../language-reference/statements/redim-statement.md)bakın.

## <a name="storing-values-in-an-array"></a>Değerleri bir dizide depolama

`Integer`türünde bir dizin kullanarak dizideki her konuma erişebilirsiniz. Parantez içine alınmış dizinini kullanarak her dizi konumuna başvurarak bir dizideki değerleri depolayıp alabilirsiniz. Çok boyutlu diziler için dizinler virgüllerle (,) ayrılır. Her dizi boyutu için bir dizine ihtiyacınız vardır.

Aşağıdaki örnek, dizilere değerler depolayan ve alan bazı deyimleri gösterir.

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a>Dizi değişmez değerleri ile bir diziyi doldurma

Bir dizi değişmez değeri kullanarak, bir diziyi, oluşturduğunuz aynı anda bir ilk değer kümesiyle doldurabilirsiniz. Dizi sabit değeri, küme ayraçları (`{}`) içine alınmış bir virgülle ayrılmış değerler listesinden oluşur.

Dizi değişmez değeri kullanarak bir dizi oluşturduğunuzda, dizi türünü ve dizi türünü belirleyebilmek için tür çıkarımı kullanabilirsiniz. Aşağıdaki örnekte her iki seçenek de gösterilmektedir.

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

Tür çıkarımı kullandığınızda, dizi türü, değişmez değerler listesindeki *baskın tür* tarafından belirlenir. Baskın tür, dizideki diğer tüm türlerin genişlebileceği türdür. Bu benzersiz tür belirlenemiyorsa, baskın tür, dizideki diğer tüm türlerin daraltabileceği benzersiz türdür. Bu benzersiz türlerden hiçbiri belirlenemiyorsa, baskın tür `Object`. Örneğin, dizi değişmez değeri için sağlanan değer listesi `Integer`, `Long`ve `Double`türünde değerler içeriyorsa, sonuçta elde edilen dizi `Double`türündedir. `Integer` ve `Long` yalnızca `Double`için genişletiğinden, baskın tür `Double`. Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../language-features/data-types/widening-and-narrowing-conversions.md).

> [!NOTE]
> Tür çıkarımı yalnızca bir tür üyesinde yerel değişkenler olarak tanımlanmış diziler için kullanabilirsiniz. Açık bir tür tanımı yoksa, sınıf düzeyinde dizi değişmez değerleri ile tanımlanan diziler `Object[]`türündedir. Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../variables/local-type-inference.md).

Önceki örnekte, dizi değişmez değerlerinin `Integer`türünde olmasına rağmen `Double` türünde bir dizi olarak `values` tanımladığına unutmayın. Bu diziyi, dizi sabit değerindeki değerler `Double` değerlere genişlebildiğinden oluşturabilirsiniz.

Ayrıca, *iç içe dizi değişmez*değerlerini kullanarak çok boyutlu bir dizi oluşturup doldurabilirsiniz. İç içe geçmiş dizi değişmez değerleri, sonuçta elde edilen dizi ile tutarlı olan sayıda boyutlara sahip olmalıdır. Aşağıdaki örnek, iç içe dizi değişmez değerlerini kullanarak iki boyutlu tamsayılar dizisi oluşturur.

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

Bir diziyi oluşturmak ve doldurmak için iç içe geçmiş dizi değişmez değerleri kullanılırken, iç içe dizi değişmez değerlerinde öğe sayısı eşleşmezse bir hata oluşur. Dizi değişkenini açıkça dizi değişmezinden farklı sayıda boyuta sahip olacak şekilde bildirirseniz bir hata oluşur.

Tek boyutlu diziler için de olduğu gibi, iç içe geçmiş dizi değişmez değerleri içeren çok boyutlu bir dizi oluştururken tür çıkarımı ' nı kullanabilirsiniz. Çıkarsanan tür, tüm iç içe geçmiş düzeyi için tüm dizi değişmez değerlerinde bulunan tüm değerlerin baskın türüdür. Aşağıdaki örnek, `Integer` ve `Double`türündeki değerlerden `Double[,]` türünde iki boyutlu bir dizi oluşturur.

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

Daha fazla örnek için bkz. [nasıl yapılır: Visual Basic dizi değişkenini başlatma](../../language-features/arrays/how-to-initialize-an-array-variable.md).

## <a name="iterating-through-an-array"></a>Bir dizi boyunca yineleme yapma

Bir dizi boyunca yineleme yaparken, dizideki her öğeye en düşük dizinden en yüksek veya en düşük değerden en düşüğe erişirsiniz. Genellikle, [için kullanın... Sonraki bildiri](../../../language-reference/statements/for-next-statement.md) veya [for each... ](../../../language-reference/statements/for-each-next-statement.md)Bir dizinin öğeleri boyunca yinelemek için sonraki ifade. Dizinin üst sınırlarını bilmiyorsanız, dizinin en yüksek değerini almak için <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> yöntemini çağırabilirsiniz. En düşük dizin değeri neredeyse her zaman 0 olsa da, dizinin en düşük değerini almak için <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> yöntemini çağırabilirsiniz.

Aşağıdaki örnek, [`For...Next`](../../../language-reference/statements/for-next-statement.md) ifadesini kullanarak tek boyutlu bir dizi aracılığıyla yinelenir.

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

Aşağıdaki örnek, bir [`For...Next`](../../../language-reference/statements/for-next-statement.md) deyimleri kullanarak çok boyutlu bir dizi boyunca yinelenir. <xref:System.Array.GetUpperBound%2A> yöntemi, boyutu belirten bir parametreye sahiptir. `GetUpperBound(0)` ilk boyutun en yüksek dizinini döndürür ve `GetUpperBound(1)` ikinci boyutun en yüksek dizinini döndürür.

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

Aşağıdaki örnek [her biri için bir kullanır... Bir sonraki Ifade](../../../language-reference/statements/for-each-next-statement.md), tek boyutlu bir dizi ve iki boyutlu bir dizi aracılığıyla yinelenir.

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a>Dizi boyutu

Bir dizinin boyutu, tüm boyutlarının uzunluklarının ürünüdür. Dizide bulunan toplam öğe sayısını temsil eder.  Örneğin, aşağıdaki örnek, her boyutta dört öğe içeren 2 boyutlu bir dizi bildirir. Örneğin çıkışının gösterdiği gibi, dizinin boyutu 16 ' dır (veya (3 + 1) * (3 + 1).

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> Dizi boyutu tartışması, pürüzlü Diziler için uygulanmaz. Sivri diziler hakkında bilgi edinmek ve pürüzlü bir dizinin boyutunu belirlemek için, [pürüzlü Diziler](#jagged-arrays) bölümüne bakın.

Bir dizinin boyutunu <xref:System.Array.Length%2A?displayProperty=nameWithType> özelliğini kullanarak bulabilirsiniz. <xref:System.Array.GetLength%2A?displayProperty=nameWithType> yöntemini kullanarak çok boyutlu bir dizinin her boyutunun uzunluğunu bulabilirsiniz.

Bir dizi değişkenini, kendisine yeni bir dizi nesnesi atayarak veya [`ReDim` ifade](../../../language-reference/statements/redim-statement.md) ifadesini kullanarak yeniden boyutlandırabilirsiniz. Aşağıdaki örnek, 100 öğeli bir diziyi 51 öğeli bir dizi olarak değiştirmek için `ReDim` ifadesini kullanır.

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

Bir dizinin boyutuyla ilgilenirken göz önünde bulundurmanız gereken birkaç nokta vardır.

|||
|---|---|
|Boyut uzunluğu|Her boyutun dizini 0 tabanlıdır, bu da 0 ' dan büyük ' a kadar değişen anlamına gelir. Bu nedenle, belirli bir boyutun uzunluğu, bu boyutun belirtilen üst sınırından bir büyük.|
|Uzunluk sınırları|Bir dizinin her boyutunun uzunluğu, <xref:System.Int32.MaxValue?displayProperty=nameWithType> veya (2 ^ 31)-1 olan `Integer` veri türünün en büyük değeriyle sınırlıdır. Ancak, bir dizinin toplam boyutu, sisteminizdeki kullanılabilir bellek ile de sınırlıdır. Kullanılabilir bellek miktarını aşan bir diziyi başlatmaya çalışırsanız, çalışma zamanı bir <xref:System.OutOfMemoryException>oluşturur.|
|Boyut ve öğe boyutu|Bir dizinin boyutu, öğelerinin veri türünden bağımsızdır. Boyut her zaman, bellekte kullandıkları bayt sayısını değil, toplam öğe sayısını temsil eder.|
|Bellek tüketimi|Bir dizinin bellekte nasıl depolandığına ilişkin varsayımlar yapmak güvenli değildir. Depolama, farklı veri genişliklerinin platformları üzerinde farklılık gösterdiği için aynı dizi, 32 bitlik 64 bir sistemde daha fazla bellek kullanabilir. Bir diziyi başlattığınızda sistem yapılandırmasına bağlı olarak, ortak dil çalışma zamanı (CLR) depolama alanını paket öğelerine mümkün olduğunca yakın bir şekilde veya tüm doğal donanım sınırları üzerinde hizalamak için atayabilir. Ayrıca, bir dizi, denetim bilgileri için bir depolama ek yükü gerektirir ve bu ek yük, eklenen her boyutla birlikte artar.|

## <a name="the-array-type"></a>Dizi türü

Her dizide, öğelerinin veri türünden farklı bir veri türü vardır. Tüm diziler için tek bir veri türü yoktur. Bunun yerine, bir dizinin veri türü, dizinin boyut sayısı veya *sıralaması*ile dizideki öğelerin veri türü tarafından belirlenir. İki dizi değişkeni yalnızca aynı dereceye sahip olduklarında ve öğeleri aynı veri türüne sahip olduğunda aynı veri türündedir. Bir dizinin boyutlarının uzunlukları dizi veri türünü etkilemez.

Her dizi <xref:System.Array?displayProperty=nameWithType> sınıfından devralır ve bir değişkeni `Array`türünde olacak şekilde bildirebilirsiniz, ancak `Array`türünde bir dizi oluşturamazsınız. Örneğin, aşağıdaki kod `arr` değişkenini `Array` türü olarak bildirir ve diziyi başlatmak için <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> yöntemini çağırır, dizinin türü Object [] olarak kanıtlar.

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

Ayrıca, [ReDim deyimleri](../../../language-reference/statements/redim-statement.md) tür `Array`olarak belirtilen bir değişkende çalışamaz. Bu nedenlerle ve tür güvenliği için her dizinin belirli bir tür olarak bildirilmesini önerilir.

Bir dizinin veya öğelerinin veri türünü çeşitli yollarla bulabilirsiniz.

- Değişkenin çalışma zamanı türünü temsil eden bir <xref:System.Type> nesnesi almak için değişkende <xref:System.Object.GetType%2A> yöntemini çağırabilirsiniz. <xref:System.Type> nesnesi, özellikleri ve yöntemlerinde kapsamlı bilgiler içerir.
- Çalışma zamanı türünün adı ile bir `String` almak için değişkeni <xref:Microsoft.VisualBasic.Information.TypeName%2A> işleve geçirebilirsiniz.

Aşağıdaki örnek, bir dizi türünü belirleyebilmek için hem `GetType` yöntemini hem de `TypeName` işlevini çağırır. Dizi türü `Byte(,)`. <xref:System.Type.BaseType%2A?displayProperty=nameWithType> özelliğinin aynı zamanda Byte dizisinin temel türünün <xref:System.Array> sınıfı olduğunu unutmayın.

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a>Dönüş değerleri ve parametreleri olarak diziler

Bir `Function` yordamından bir dizi döndürmek için, dizi veri türü ve boyut sayısını [Function ifadesinin](../../../language-reference/statements/function-statement.md)dönüş türü olarak belirtin. İşlevi içinde, aynı veri türüne ve boyut sayısına sahip bir yerel dizi değişkeni bildirin. [Return ifadesinde](../../../language-reference/statements/return-statement.md), yerel dizi değişkenini parantez olmadan dahil edin.

Bir diziyi bir `Sub` veya `Function` yordamına parametre olarak belirtmek için, parametreyi belirtilen veri türüne ve boyut sayısına sahip bir dizi olarak tanımlayın. Yordamın çağrısında, aynı veri türüne ve boyut sayısına sahip bir dizi değişkeni geçirin.

Aşağıdaki örnekte `GetNumbers` işlevi, `Integer`türünde tek boyutlu bir dizi `Integer()`döndürür. `ShowNumbers` yordam bir `Integer()` bağımsız değişkenini kabul eder.

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

Aşağıdaki örnekte `GetNumbersMultiDim` işlevi, `Integer`türünde iki boyutlu bir dizi `Integer(,)`döndürür.  `ShowNumbersMultiDim` yordam bir `Integer(,)` bağımsız değişkenini kabul eder.

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a>Sivri diziler

Bazen uygulamanızdaki veri yapısı iki boyutlu ancak dikdörtgen değildir. Örneğin, ayın her gününün yüksek sıcaklığına ilişkin verileri depolamak için bir dizi kullanabilirsiniz. Dizinin ilk boyutu ayı temsil eder, ancak ikinci boyut gün sayısını ve ay içindeki gün sayısını temsil eder. Dizi *dizileri*olarak da adlandırılan *pürüzlü bir dizi*, bu tür senaryolar için tasarlanmıştır. Pürüzlü dizi öğeleri de diziler olan bir dizidir. Sivri dizi ve pürüzlü dizideki her öğe bir veya daha fazla boyuta sahip olabilir.

Aşağıdaki örnek, her bir bir gün dizisi olan her öğesi bir ay dizisini kullanır. Farklı aylar farklı gün sayılarına sahip olduğundan, örnek pürüzlü bir diziyi kullanır.  Örnek, pürüzlü bir dizi oluşturmayı, bu değere değer atamayı ve değerlerini almayı ve görüntülemeyi gösterir.

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

Önceki örnek, `For...Next` döngüsünü kullanarak öğeleri öğe temelinde pürüzlü diziye değerler atar. Ayrıca, iç içe dizi değişmez değerlerini kullanarak pürüzlü bir dizinin öğelerine değerler atayabilirsiniz. Ancak, iç içe dizi değişmez değerlerini kullanma girişimi (örneğin, `Dim valuesjagged = {{1, 2}, {2, 3, 4}}`) derleyici hatası oluşturur [BC30568](../../../,,/../misc/bc30568.md). Hatayı düzeltmek için, iç dizi değişmez değerlerini parantez içine alın. Parantez, dizi değişmez ifadesinin değerlendirilmesini zorlar ve elde edilen değerler, aşağıdaki örnekte gösterildiği gibi dış dizi sabiti ile birlikte kullanılır.

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

Sivri dizi öğeleri diziler içeren tek boyutlu bir dizidir. Bu nedenle, <xref:System.Array.Length%2A?displayProperty=nameWithType> özelliği ve `Array.GetLength(0)` yöntemi tek boyutlu dizideki öğelerin sayısını döndürür ve pürüzlü bir dizi çok boyutlu olmadığından `Array.GetLength(1)` bir <xref:System.IndexOutOfRangeException> oluşturur. Her bir alt dizinin <xref:System.Array.Length%2A?displayProperty=nameWithType> özelliğinin değerini alarak her bir alt dizideki öğelerin sayısını belirlersiniz. Aşağıdaki örnek, pürüzlü bir dizideki öğelerin sayısının nasıl belirleneceğini göstermektedir.

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a>Sıfır uzunluklu diziler

Visual Basic, başlatılmamış bir dizi (değeri `Nothing`olan bir dizi) ve *sıfır uzunluklu bir dizi* ya da boş dizi (hiçbir öğesi olmayan bir dizi) arasında farklılaştırır. Başlatılmamış bir dizi, boyutlandırılmış olmayan veya kendisine atanmış değer içeren bir dizidir. Örneğin:

```vb
Dim arr() As String
```

Sıfır uzunlukta bir dizi,-1 boyutuyla birlikte bildirilmiştir. Örneğin:

```vb
Dim arrZ(-1) As String
```

Aşağıdaki koşullarda sıfır uzunluklu bir dizi oluşturmanız gerekebilir:

- <xref:System.NullReferenceException> bir özel durumu risksiz, kodunuzun <xref:System.Array.Length%2A> veya <xref:System.Array.Rank%2A>gibi <xref:System.Array> sınıfının üyelerine erişmesi veya Visual Basic gibi bir <xref:Microsoft.VisualBasic.Information.UBound%2A>işlevi çağırması gerekir.

- Özel bir durum olarak `Nothing` denetlemek zorunda kalmadan kodunuzu basit tutmak istersiniz.

- Kodunuz bir veya daha fazla yordamdan sıfır uzunluklu bir diziyi geçirmenize ya da bir veya daha fazla yordamdan sıfır uzunluklu bir dizi döndürmeniz gereken bir uygulama programlama arabirimi (API) ile etkileşime girer.

## <a name="splitting-an-array"></a>Diziyi bölme

Bazı durumlarda, tek bir diziyi birden çok diziye bölmeniz gerekebilir. Bu, dizinin bölüneceği nokta veya noktaları tanımlamayı ve sonra diziyi iki veya daha fazla ayrı dizilere Spitting.

> [!NOTE]
> Bu bölüm, tek bir dizeyi bir dize dizisine bölme bölümünü bir sınırlayıcı temelinde ele almaz. Bir dizeyi bölme hakkında daha fazla bilgi için <xref:System.String.Split%2A?displayProperty=nameWithType> yöntemine bakın.

Bir diziyi bölmek için en yaygın ölçütler şunlardır:

- Dizideki öğelerin sayısı Örneğin, belirtilen sayıda öğeden fazla bir diziyi, yaklaşık olarak eşit sayıda parçaya bölmek isteyebilirsiniz. Bu amaçla, <xref:System.Array.Length%2A?displayProperty=nameWithType> ya da <xref:System.Array.GetLength%2A?displayProperty=nameWithType> yöntemi tarafından döndürülen değeri kullanabilirsiniz.

- Dizinin nerede bölüneceği belirten bir sınırlayıcı görevi gören bir öğenin değeri. <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> ve <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> yöntemlerini çağırarak belirli bir değeri arayabilirsiniz.

Dizinin bölünmesi gereken dizin veya dizinleri belirledikten sonra, <xref:System.Array.Copy%2A?displayProperty=nameWithType> yöntemini çağırarak ayrı dizileri oluşturabilirsiniz.

Aşağıdaki örnek, bir diziyi yaklaşık olarak eşit boyuttaki iki diziye böler. (Dizi öğelerinin toplam sayısı tek ise, ilk dizide ikinciden daha fazla bir öğe vardır.)

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

Aşağıdaki örnek, bir dize dizisini değeri "zzz" olan ve dizi sınırlayıcısı görevi gören bir öğe varlığını temel alarak iki diziye ayırır. Yeni diziler, sınırlayıcıyı içeren öğeyi içermez.

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a>Dizileri birleştirme

Ayrıca, bir dizi diziyi tek bir daha büyük dizi içinde birleştirebilirsiniz. Bunu yapmak için <xref:System.Array.Copy%2A?displayProperty=nameWithType> yöntemini de kullanabilirsiniz.

> [!NOTE]
> Bu bölüm, dize dizisinin tek bir dizeye katılmasını tartışır. Bir dize dizisini birleştirme hakkında daha fazla bilgi için <xref:System.String.Join%2A?displayProperty=nameWithType> yöntemine bakın.

Her bir dizinin öğelerini yeni diziye kopyalamadan önce, diziyi yeni diziye uyum sağlayacak kadar büyük olacak şekilde oluşturduğunuzdan emin olmalısınız. Bunu iki yoldan biriyle yapabilirsiniz:

- Yeni öğe eklemeden önce diziyi dinamik olarak genişletmek için [`ReDim Preserve`](../../../language-reference/statements/redim-statement.md) ifadesini kullanın. Bu en kolay tekniktir, ancak büyük dizileri kopyalarken performans düşüşüne ve aşırı bellek kullanımına neden olabilir.
- Yeni büyük dizi için gereken toplam öğe sayısını hesaplayın, ardından her kaynak dizisinin öğelerini buna ekleyin.

Aşağıdaki örnek, her biri tek bir diziye on öğe içeren dört dizi eklemek için ikinci yaklaşımı kullanır.

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

Bu durumda, kaynak dizileri tümüyle küçük olduğundan, her yeni dizinin öğelerini eklediğimiz için diziyi de dinamik olarak genişletebiliriz. Aşağıdaki örnek bunu yapar.

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a>Dizilere Alternatif olarak Koleksiyonlar

Diziler, kesin olarak belirlenmiş sabit sayıda nesne oluşturmak ve bunlarla çalışmak için en yararlı seçenektir. Koleksiyonlar, nesne gruplarıyla çalışmak için daha esnek bir yol sağlar. Bir dizinin boyutunu açıkça [`ReDim` ifadesiyle](../../../language-reference/statements/redim-statement.md)değiştirmenize gerek olan dizilerin aksine koleksiyonlar, bir uygulama değişikliğinin ihtiyaçlarına göre dinamik olarak büyür ve küçülür.

Bir diziyi yeniden Dimension yapmak için `ReDim` kullandığınızda, Visual Basic yeni bir dizi oluşturur ve öncekini yayınlar. Bu, yürütme süresini alır. Bu nedenle, çalıştığınız öğe sayısı sıklıkla değişirse veya ihtiyacınız olan en fazla öğe sayısını tahmin edemezsiniz, genellikle bir koleksiyon kullanarak daha iyi performans elde edersiniz.

Bazı koleksiyonlar için, anahtarı kullanarak nesneyi hızlı bir şekilde alabilmeniz için koleksiyona yerleştirdiğiniz herhangi bir nesneye bir anahtar atayabilirsiniz.

Koleksiyonunuz yalnızca bir veri türünün öğelerini içeriyorsa, <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanındaki sınıflardan birini kullanabilirsiniz. Genel bir koleksiyon, tür güvenliğini, başka bir veri türü eklenememesi için uygular.

Koleksiyonlar hakkında daha fazla bilgi için bkz. [koleksiyonlar](../../concepts/collections.md).

## <a name="related-topics"></a>İlgili konular

|Terim|Tanım|
|----------|----------------|
|[Visual Basic dizi boyutları](../../language-features/arrays/array-dimensions.md)|Dizilerde derecelendirme ve boyutları açıklar.|
|[Nasıl yapılır: Visual Basic dizi değişkenini başlatma](../../language-features/arrays/how-to-initialize-an-array-variable.md)|İlk değerlerle dizilerin nasıl doldurulacağını açıklar.|
|[Nasıl yapılır: Visual Basic bir diziyi sıralama](../../language-features/arrays/how-to-sort-an-array.md)|Bir dizinin öğelerinin alfabetik olarak nasıl sıralanacağını gösterir.|
|[Nasıl yapılır: Bir Diziyi Başka Diziye Atama](../../language-features/arrays/how-to-assign-one-array-to-another-array.md)|Bir diziyi başka bir dizi değişkenine atamaya yönelik kuralları ve adımları açıklar.|
|[Dizilerle İlgili Sorun Giderme](../../language-features/arrays/troubleshooting-arrays.md)|Dizilerle çalışırken ortaya çıkan bazı yaygın sorunları açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array?displayProperty=nameWithType>
- [Dim Deyimi](../../../language-reference/statements/dim-statement.md)
- [ReDim Deyimi](../../../language-reference/statements/redim-statement.md)
