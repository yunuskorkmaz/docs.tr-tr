---
title: Visual Basic'de Diziler
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
ms.openlocfilehash: 6b131d073e10f99feaf770fe5fd3c393551fa5a3
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675971"
---
# <a name="arrays-in-visual-basic"></a>Visual Basic'de Diziler

Bir dizi terimiyle gösterilen değerler kümesidir *öğeleri*, mantıksal olarak ilgili arasındaki ilişki. Örneğin, bir dizi, dilbilgisi okulundaki her sınıfta Öğrenciler sayısının oluşabilir; dizinin her öğesi tek bir sınıf Öğrenci sayısıdır. Benzer şekilde, bir sınıf için bir öğrenci derece, bir dizi oluşabilir; dizinin her öğesi, bir tek sınıf hizmetidir.

Bu, bizim veri öğelerinin her biri depolamak için olası bağımsız değişkenler olur. Öğrenci derece uygulamamız analiz edilirse, örneğin, ayrı bir değişken için her öğrencinin sınıf, gibi kullanabiliriz `englishGrade1`, `englishGrade2`vb. Bu yaklaşım, üç önemli sınırlamaları vardır:

- Tasarım zamanında işlemek sahibiz tam olarak kaç derece bilmek sahibiz.
- Derece çok sayıda hızlı işleme zahmetli hale gelir. Bu sırayla bir uygulama ciddi hatalar olması olasılığı çok daha kolaylaştırır.
- Elde etmek zordur. Eklediğimiz her bir yeni sınıf uygulama değiştirilmiş, yeniden derlenen, imzalanmasını ve gerektirir.

Dizi kullanarak, aynı adla ilgili değerlere için bakın ve çağrılan kullanma bir *dizin* veya *alt simge* dizideki konumuna göre tek tek bir öğeyi tanımlamak için. Bir dizideki öğelerin toplam sayısından daha az bir dizi aralığı 0'dan dizinler. Bir dizinin boyutu tanımlamak için Visual Basic sözdizimini kullandığınızda, dizideki öğelerin toplam sayısını değil en yüksek dizinini belirtin. Bir birim olarak dizi çalışabilirsiniz ve öğeleri yineleme özelliğini, tasarım zamanında içeren tam olarak kaç öğenin bilmek gerek serbest bırakır.

Açıklama önce hızlı bazı örnekler:

```vb
' Declare a single-dimension array of 5 numbers.
Dim numbers(4) As Integer

'Declare a single-dimension array and set its 4 values.
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

## <a name="array-elements-in-a-simple-array"></a>Basit bir dizide dizi öğeleri

Adlı bir dizi oluşturalım `students` Öğrenci sayısı, dilbilgisi okulundaki her sınıfta depolamak için. Dizinleri öğelerin aralığının 0-6 arasıdır. Bu dizi kullanarak, yedi değişken bildirilmesinden daha kolay olacaktır.

Aşağıdaki çizimde gösterildiği `students` dizisi. Dizinin her öğesi için:

- Öğenin dizini dereceyi temsil eder (0 dizini dereceyi temsil eder).

- Öğesi içinde yer alan değer o derecedeki Öğrenci sayısını temsil eder.

![Öğrenciler sayıdan oluşan bir diziyi gösteren diyagram](./media/index/students-array-elements.gif)

Aşağıdaki örnek, bir dizi oluşturur ve Visual Basic kodu içerir:

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

Örneğin, üç şeyi yapar:

- Bunu bildiren bir `students` dizisi yedi öğe ile. Sayı `6` dizide bildirimi dizideki son dizini belirtir; bir değer dizideki öğelerin sayısından küçük.
- Değer, dizideki her öğeye atar. Dizi adını kullanarak ve parantez içinde tek tek öğenin dizini de dahil olmak üzere dizi öğelerine erişebilirsiniz.
- Her dizi değerini listeler. Örnekte bir [ `For` ](../../../language-reference/statements/for-next-statement.md) dizin numarası ile dizideki her öğeye erişmek için deyimi.

`students` Önceki örnekte dizisi olduğundan tek boyutlu dizi bir dizin kullanır. Birden fazla dizin veya alt simge kullanan dizi olarak adlandırılan *çok boyutlu*. Daha fazla bilgi için bu makalenin devamını görmek ve [Visual Basic'de dizi boyutları](../../language-features/arrays/array-dimensions.md).

## <a name="creating-an-array"></a>Bir dizi oluşturma

Bir dizinin boyutu, çeşitli yollarla tanımlayabilirsiniz:

- Dizi bildirildiğinde boyutu belirtebilirsiniz:

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- Kullanabileceğiniz bir `New` yan tümcesi oluşturulduğunda bir dizinin boyutunu sağlamak için:

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

Var olan bir dizi varsa, boyutunu kullanarak tanımlayabilirsiniz [ `ReDim` ](../../../language-reference/statements/redim-statement.md) deyimi. Belirtebilirsiniz `ReDim` deyimi bir dizideki değerleri koruyabilir veya boş dizi oluşturmasını belirtebilirsiniz. Aşağıdaki örnek, farklı kullanımlarını gösterir `ReDim` mevcut dizinin boyutunu değiştirmek için deyimi.

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

Daha fazla bilgi için [ReDim deyimi](../../../language-reference/statements/redim-statement.md).

## <a name="storing-values-in-an-array"></a>Bir dizideki değerleri saklama

Bir dizideki her konum türünden dizin kullanarak erişebileceğiniz `Integer`. Depolayın ve parantez içindeki dizinini kullanarak her dizi konumuna başvurarak dizideki değerleri alın. Dizinler çok boyutlu diziler için virgülle (,) tarafından ayrılır. Her dizi boyutu için bir dizine ihtiyacınız var.

Aşağıdaki örnek, dizilerde değerler depolanıp bazı deyimleri gösterir.

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a>Dizi değişmez değerleri olan bir dizi doldurma

Dizi değişmez değeri kullanarak başlangıç değer kümesi ile bir dizi oluşturduğunuzda, aynı anda doldurabilirsiniz. Küme ayraçları içine alınmış bir virgülle ayrılmış değerler listesi, dizi değişmez değeri oluşur (`{}`).

Dizi değişmez değeri kullanarak dizi oluşturduğunuzda, dizi türü sağlarsınız veya dizi türünü saptamak için tür çıkarımını kullanın. Aşağıdaki örnek, her iki seçeneği gösterir.

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

Tür çıkarımı kullandığınızda, dizinin türü tarafından belirlenir *baskın tür* değişmez değerler listesinde. Baskın tür, dizideki diğer tüm türlerin genişleyebileceği türüdür. Bu benzersiz tür belirlenemiyorsa, baskın tür dizideki diğer tüm türleri daraltmak benzersiz türüdür. Bu benzersiz türlerden hiçbiri belirlenemezse, baskın türdür `Object`. Örneğin, dizi değişmez değerine sağlanan değerler listesi türü değerler içeriyorsa `Integer`, `Long`, ve `Double`, ortaya çıkan dizi türünde `Double`. Çünkü `Integer` ve `Long` yalnızca genişletmek `Double`, `Double` baskın türdür. Daha fazla bilgi için [Widening ve daraltma dönüşümleri](../../language-features/data-types/widening-and-narrowing-conversions.md).

> [!NOTE]
> Tür çıkarımı, yerel bir tür üye değişkenlerinde olarak tanımlanan diziler için kullanabilirsiniz. Açık tür tanımı yoksa, dizi değişmez değerleri sınıf düzeyinde tanımlanan tür dizilerdir `Object[]`. Daha fazla bilgi için [yerel tür çıkarımı](../variables/local-type-inference.md).

Önceki örnekte tanımlayan Not `values` türünde bir dizi olarak `Double` tüm dizi değişmez değerleri türü olmasına rağmen `Integer`. Dizi değişmez değerleri için genişletebilirsiniz çünkü bu bir dizi oluşturabilirsiniz `Double` değerleri.

Ayrıca oluşturabilir ve çok boyutlu bir dizi kullanarak doldurmak *iç içe geçmiş dizi değişmez değerleri*. İç içe geçmiş dizi değişmez değerleri, sonuçta elde edilen diziyle tutarlı olan bir dizi boyutları olması gerekir. Aşağıdaki örnekte, iç içe geçmiş dizi değişmez değerlerini kullanarak iki boyutlu bir tamsayı dizisi oluşturur.

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

İç içe geçmiş dizi değişmez değerleri oluşturma ve bir dizi doldurmak için kullanılırken, iç içe geçmiş dizi değişmez değerlerinde öğe sayısı eşleşmezse bir hata oluşur. Dizi değişmez değerleri boyutlardan farklı sayıda sahip şekilde dizi değişkenini açıkça bildirirseniz hata da oluşur.

Tek boyutlu diziler için yapabildiğiniz gibi çok boyutlu bir dizi iç içe geçmiş dizi değişmez değerleri ile oluştururken üzerinde tür çıkarımı güvenebilirsiniz. Tüm iç içe yerleştirme düzeyinin tüm dizi değişmez değerleri tüm değerler için baskın tür gösterilen türüdür. Aşağıdaki örnek, türünde iki boyutlu bir dizi oluşturur. `Double[,]` türü değerlerinin `Integer` ve `Double`.

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

Diğer örnekler için [nasıl yapılır: Visual Basic'te dizi değişkeni başlatma](../../language-features/arrays/how-to-initialize-an-array-variable.md).

## <a name="iterating-through-an-array"></a>Bir dizi boyunca gezinme

Bir dizi aracılığıyla yineleme yaptığınızda, dizideki her öğe düşük dizine en yüksek veya en yüksek erişim için en düşük. Genellikle, kullanın [için... Sonraki deyimi](../../../language-reference/statements/for-next-statement.md) veya [her biri için... Sonraki deyimi](../../../language-reference/statements/for-each-next-statement.md) dizi öğelerinde yineleme yapmak için. Dizi üst sınırları bilmediğinizde çağırabilirsiniz <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> en yüksek dizin değerini almak için yöntemi. En düşük dizin değeri hemen hemen aynıdır ancak her zaman 0 çağırabilirsiniz <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> dizini en düşük değerini almak için yöntemi.

Aşağıdaki örnek, kullanarak tek boyutlu bir dizi aracılığıyla yinelenir [ `For...Next` ](../../../language-reference/statements/for-next-statement.md) deyimi.

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

Aşağıdaki örneği kullanarak çok boyutlu bir dizi yinelenir. bir [ `For...Next` ](../../../language-reference/statements/for-next-statement.md) deyimi. <xref:System.Array.GetUpperBound%2A> Yönteminin boyutu belirten bir parametre vardır. `GetUpperBound(0)` İlk boyutun yüksek dizin döndürür ve `GetUpperBound(1)` İkinci boyutun yüksek dizin döndürür.

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

Aşağıdaki örnekte bir [her biri için... Sonraki deyimi](../../../language-reference/statements/for-each-next-statement.md)tek boyutlu bir dizi ve iki boyutlu bir dizi aracılığıyla yineleme yapmak için.

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a>Dizi boyutu

Bir dizinin boyutu, tüm boyutlarının uzunluklarının ürünüdür. Bu, şu anda dizide yer alan öğelerin toplam sayısını temsil eder.  Örneğin, aşağıdaki örnekte, her boyutta, dört öğelerle 2 boyutlu bir dizi bildirir. Örneğin çıktısında gösterildiği gibi dizinin boyutu 16'dır (veya (3 + 1) * (3 + 1).

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> Bu tartışma dizisi boyutunun basit diziler için geçerli değildir. Basit diziler ve düzensiz bir dizi boyutunu belirleme hakkında daha fazla bilgi için bkz. [basit dizileri](#jagged-arrays) bölümü.

Bir dizinin boyutu kullanarak bulabilirsiniz <xref:System.Array.Length%2A?displayProperty=nameWithType> özelliği. Kullanarak çok boyutlu bir dizinin her boyutunun uzunluğunu bulabilirsiniz <xref:System.Array.GetLength%2A?displayProperty=nameWithType> yöntemi.

Ona yeni bir dizi nesnesi atayarak veya kullanarak, bir dizi değişkenini boyutlandırabilirsiniz [ `ReDim` deyimi](../../../language-reference/statements/redim-statement.md) deyimi. Aşağıdaki örnekte `ReDim` 100 öğeli bir dizi için 51 öğeli bir dizi değiştirmek için deyimi.

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

Bir dizinin boyutu ile uğraşırken akılda tutulması gereken birkaç şey vardır.

|||
|---|---|
|Boyut uzunluğu|Her boyutun dizini 0 tabanlıdır; için üst sınır 0'dan aralıkları anlamına gelir. Bu nedenle, belirli bir boyutun uzunluğu o boyut bildirilen üst sınırdan büyük biridir.|
|Uzunluk sınırları|Bir dizinin her boyutunun uzunluğu en büyük değerini sınırlıdır `Integer` olan veri türü <xref:System.Int32.MaxValue?displayProperty=nameWithType> veya (2 ^ 31) - 1. Ancak, bir dizinin toplam boyutu ayrıca sistemdeki kullanılabilir bellek ile sınırlıdır. Bir diziyi başlatmaya çalışırsanız, kullanılabilir bellek miktarını aşıyor, çalışma zamanı bir <xref:System.OutOfMemoryException>.|
|Boyut ve öğe boyutu|Bir dizinin boyutu, öğelerin veri türü bağımsızdır. Boyutu her zaman öğelerin, bellekte kullandıkları bayt sayısını değil toplam sayısını temsil eder.|
|Bellek tüketimi|Bir dizinin bellekte depolanma ilgili varsayımlar yapılması güvenli değildir. Aynı dizi 64-bit sistemde 32-bit sistemde daha fazla bellek tüketebilir şekilde depolama farklı veri genişliği platformlarda değişir. Bir diziyi başlattığınızda sistem yapılandırmasına bağlı olarak ortak dil çalışma zamanı (CLR) depolama öğeleri mümkün olduğunca birbirine yakın paketlemek için veya onları doğal donanım sınırlarına göre hizalamak için atayabilirsiniz. Ayrıca, bir dizi bir depolama alanı yükü, denetim bilgileri için gerektirir ve bu yükü eklenen her boyutla artar.|

## <a name="the-array-type"></a>Dizi türü

Her dizi öğelerine veri türünden farklı bir veri türü var. Tüm diziler için tek bir veri türü yoktur. Bunun yerine, bir dizi veri türü boyut sayısına göre belirlenir veya *derece*, dizi ve dizideki öğelerin veri türü. İki dizi aynı veri türünden yalnızca zaman aynı dereceye sahip oldukları yazın ve öğeleri aynı veri türüne sahip değişkenlerdir. Bir dizideki boyutların uzunlukları dizinin veri türünü etkilemek değil.

Her dizi öğesinden devralınan <xref:System.Array?displayProperty=nameWithType> sınıfı ve bir değişken türü olmasını bildirebilirsiniz `Array`, ancak türünde bir dizi oluşturamazsınız `Array`. Örneğin, aşağıdaki kod bildirir ancak `arr` değişken türünde olmasını `Array` ve çağıran <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> dizinin türü dizi oluşturmak için gereken yöntemini kanıtlar olmasını Object [].

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

Ayrıca, [ReDim deyimi](../../../language-reference/statements/redim-statement.md) türü olarak bildirilmiş bir değişken üzerinde çalışamaz `Array`. Bu nedenlerle ve tür güvenliği için her dizinin belirli bir tür olarak bildirilmesi önerilir.

Veri türü diziye veya öğelerine çeşitli şekillerde bulabilirsiniz.

- Çağırabilirsiniz <xref:System.Object.GetType%2A> yöntemi almak için bir değişken üzerinde bir <xref:System.Type> değişkeninin çalışma zamanı türünü temsil eden nesne. <xref:System.Type> Nesnesi, özelliklerinde ve yöntemlerinde kapsamlı bilgiler içerir.
- Değişken geçirebilirsiniz <xref:Microsoft.VisualBasic.Information.TypeName%2A> almak için işlevi bir `String` ile çalışma zamanı türünün adı.

Aşağıdaki örnek, hem çağırır `GetType` yöntemi ve `TypeName` işlevi bir dizi türünü belirlemek için. Dizi türü `Byte(,)`. Unutmayın <xref:System.Type.BaseType%2A?displayProperty=nameWithType> özelliği de gösterir bayt dizisinin temel tür olduğunu <xref:System.Array> sınıfı.

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a>Dönüş değerleri ve parametreler olarak diziler

Bir diziden döndürülecek bir `Function` yordamı, dönüş türü olarak dizi veri türü ve boyut sayısına belirtin [Function deyimi](../../../language-reference/statements/function-statement.md). İşlevin içinde aynı veri türü ve boyut sayısına sahip bir yerel dizi değişkenini bildirin. İçinde [dönüş deyimi](../../../language-reference/statements/return-statement.md), parantez olmadan yerel dizi değişkenini içerir.

Bir parametre olarak bir dizi belirtmek için bir `Sub` veya `Function` yordamı, parametreyi belirtilen veri türü ve boyut sayısına bir dizi olarak tanımlayın. Yordam çağrısı içinde aynı veri türü ve boyut sayısına sahip bir dizi değişken geçirin.

Aşağıdaki örnekte, `GetNumbers` işlevinin döndürdükleriyle bir `Integer()`, tek boyutlu bir dizi türü `Integer`. `ShowNumbers` Yordamı kabul eden bir `Integer()` bağımsız değişken.

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

Aşağıdaki örnekte, `GetNumbersMultiDim` işlevinin döndürdükleriyle bir `Integer(,)`, türünde iki boyutlu bir dizi `Integer`.  `ShowNumbersMultiDim` Yordamı kabul eden bir `Integer(,)` bağımsız değişken.

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a>Basit diziler

Bazen uygulamanızdaki veri yapısı iki boyutludur ancak dikdörtgen değildir. Örneğin, ayın her günü yüksek Sıcaklığın hakkında veri depolamak için bir dizi kullanabilirsiniz. Dizinin ilk boyutu ayı temsil eder, ancak ikinci boyuttaki gün sayısını temsil eder ve bir ay içindeki gün sayısını Tekdüzen değildir. A *düzensiz dizi*, da adlandırılan bir *dizi*, bu tür senaryolar için tasarlanmıştır. Basit bir dizi, öğeleri dizi da olan bir dizidir. Düzensiz bir dizi ve düzensiz bir dizideki her öğe bir veya daha fazla boyuta sahip olabilir.

Aşağıdaki örnek, her öğesi Günlerden oluşan olan bir dizi ay kullanır. Farklı aylar farklı gün sayılarına sahip olduğundan bu örnek bir düzensiz dizi kullanır.  Örneğin, düzensiz bir dizi oluşturun, bunun için değerler atayın ve almak ve değerlerini görüntülemek gösterilmektedir.

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

Önceki örnekte değerlerini bir öğeye göre temelinde düzensiz dizi kullanarak atar bir `For...Next` döngü. İç içe geçmiş dizi değişmez değerleri kullanarak basit bir dizi öğelerine değerleri de atayabilirsiniz. Ancak, kullanma girişimi iç içe geçmiş dizi değişmez değerleri (örneğin, `Dim valuesjagged = {{1, 2}, {2, 3, 4}}`) derleyici hatası oluşturur [BC30568](../../../,,/../misc/bc30568.md). Hatayı düzeltmek için iç diziyi parantez içine alın. Parantezler değerlendirilecek dizi değişmez değer ifadesinin değerlendirilmesini ve aşağıdaki örnekte gösterildiği gibi dış dizi değişmez değeri, sonuçta elde edilen değerleri kullanılır.

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

Düzensiz bir dizi, diziler öğeleri içeren tek boyutlu bir dizidir. Bu nedenle, <xref:System.Array.Length%2A?displayProperty=nameWithType> özelliği ve `Array.GetLength(0)` yöntemi tek boyutlu bir dizideki öğelerin sayısını döndürür ve `Array.GetLength(1)` oluşturur bir <xref:System.IndexOutOfRangeException> düzensiz bir dizi çok boyutlu olmadığı için. Her alt dizinin 's değerini alarak her alt dizinin içindeki öğelerin sayısını belirlemek <xref:System.Array.Length%2A?displayProperty=nameWithType> özelliği. Aşağıdaki örnek, düzensiz bir dizideki öğelerin sayısını belirlemek nasıl gösterir.

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a>Sıfır uzunluklu dizilerin kullanımı

Visual Basic arasında başlatılmamış bir dizi ayırır (değeri olan bir dizi `Nothing`) ve bir *sıfır uzunluklu dizi* veya boş dizi (hiçbir öğe içermeyen bir dizi.) Başlatılmamış bir dizi değil dimensioned bir veya herhangi bir değer atanmış vardı. Örneğin:

```vb
Dim arr() As String
```

Sıfır uzunluklu dizi -1 olan bir boyut ile bildirilir. Örneğin:

```vb
Dim arrZ(-1) As String
```

Aşağıdaki koşullarda sıfır uzunlukta bir dizi oluşturmanız gerekebilir:

- Riski olmadan bir <xref:System.NullReferenceException> özel durum, kodunuzu gerekir üyelerine erişme <xref:System.Array> gibi sınıf <xref:System.Array.Length%2A> veya <xref:System.Array.Rank%2A>, veya Visual Basic işlevi çağırmak <xref:Microsoft.VisualBasic.Information.UBound%2A>.

- Denetlenecek zorunluluğunu ortadan kaldırarak kodunuzu basit tutmak istediğiniz `Nothing` bir özel durum olarak.

- Kodunuz, bir veya daha fazla yordamlar için sıfır uzunlukta bir dizi geçirmenizi gerektiren ya da bir veya birden çok sıfır uzunlukta bir dizi döndürür bir uygulama programlama arabirimi (API) ile etkileşim kurar.

## <a name="splitting-an-array"></a>Bir dizi bölme

Bazı durumlarda tek bir dizi birden çok dizisi bölün gerekebilir. Bu noktayı veya dizi Bölünecek olduğu noktaları belirleyerek ve ardından dizi iki veya daha fazla ayrı diziye kopyalamıştır içerir.

> [!NOTE]
> Bu bölümde bazı sınırlayıcıyı dize dizisi olarak tek bir dize bölme ele almaz. Bir dizeyi bölerken hakkında daha fazla bilgi için bkz: <xref:System.String.Split%2A?displayProperty=nameWithType> yöntemi.

Bir dizi bölme en yaygın ölçütlerini şunlardır:

- Dizideki öğelerin sayısı Örneğin, birden çok belirtilen sayıda öğeyi bir dizi yaklaşık olarak eşit bölümlerinin sayıya bölmek isteyebilirsiniz. Bu amaçla tarafından döndürülen değer kullanabileceğiniz <xref:System.Array.Length%2A?displayProperty=nameWithType> veya <xref:System.Array.GetLength%2A?displayProperty=nameWithType> yöntemi.

- Dizi yeri belirten bir sınırlayıcı hizmet veren bir öğenin değerini bölmeniz gerekir. Belirli bir değeri çağırarak arayabilirsiniz <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> ve <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> yöntemleri.

Dizin veya dizinleri, dizi bölme saptadıktan sonra daha sonra tek tek dizileri çağırarak oluşturabilirsiniz <xref:System.Array.Copy%2A?displayProperty=nameWithType> yöntemi.

Aşağıdaki örnek, bir dizi yaklaşık aynı boyutta iki diziye ayırır. (İlk diziyi dizi öğelerinin toplam sayı tek ise ikinciden bir daha fazla öğe yok.)

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

Aşağıdaki örnek iki dizi değeri dizi sınırlayıcı hizmet veren "zzz" olan bir öğe olup olmamasına göre bir dize dizisi ayıran. Yeni dizileri sınırlayıcısı içeren öğe içermez.

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a>Diziler katılma

Ayrıca, bir sayı dizisi tek büyük bir diziye birleştirebilirsiniz. Bunu yapmak için ayrıca kullandığınız <xref:System.Array.Copy%2A?displayProperty=nameWithType> yöntemi.

> [!NOTE]
> Bu bölümde, bir dize dizisi, tek bir dize olarak katılma açıklanmamıştır. Dize dizisi birleştirme hakkında daha fazla bilgi için bkz: <xref:System.String.Join%2A?displayProperty=nameWithType> yöntemi.

Yeni bir diziye her dizinin öğeleri kopyalamadan önce böylece yeni bir dizi tutabilecek kadar büyük dizi başlattıysanız ilk sağlamalıdır. Bunu iki yoldan biriyle yapabilirsiniz:

- Kullanım [ `ReDim Preserve` ](../../../language-reference/statements/redim-statement.md) deyimini yeni öğeleri eklemeden önce bir dizi dinamik olarak genişletin. En kolay yöntemi budur ancak büyük diziler kopyalarken aşırı bellek kullanımı ve performans düşüşü ile sonuçlanabilir.
- Yeni büyük dizisi için gerekli öğelerin toplam sayısını hesaplama ve her kaynak dizinin öğeleri ekleyin.

Aşağıdaki örnek, tek bir dizi dört dizilerle on öğe eklemek için ikinci yaklaşım kullanır.

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

Bu durumda kaynak diziler tüm küçük olduğundan, size her yeni dizinin öğeleri eklemek gibi biz de dinamik olarak dizi genişletebilirsiniz. Aşağıdaki örnek yapar.

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a>Dizilere alternatif olarak koleksiyonlar

Dizileri oluşturmak ve güçlü şekilde yazılan nesnelerin sabit sayıda ile çalışmak için ekseriyetle faydalıdır. Koleksiyonlar nesne grupları ile çalışmak için daha esnek bir yol sağlar. Dizilerden farklı olarak gerektiren açıkça ile bir dizinin boyutunu değiştirmeniz [ `ReDim` deyimi](../../../language-reference/statements/redim-statement.md), koleksiyonlar büyütün ve dinamik bir uygulama değişikliği ihtiyaçlarını Daralt.

Kullanırken `ReDim` dizi redimension için Visual Basic yeni bir dizi oluşturur ve önceki sürümleri. Bu, yürütme zamanı alır. Öğelerin sayısı sık sık değişiyorsa veya ihtiyacınız olan çalıştığınız öğe sayısını tahmin edemiyorsanız, bu nedenle, genellikle daha iyi performans bir koleksiyon kullanarak elde.

Bazı koleksiyonlar için koleksiyona eklediğiniz ve böylece anahtarını kullanarak hızlı bir şekilde nesnesi alabilirsiniz herhangi bir nesneye bir anahtar atayabilirsiniz.

Koleksiyonunuz tek bir veri türünde öğeler içeriyorsa, sınıflarda birini kullanabilirsiniz <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı. Genel koleksiyon tür güvenliği sağlar, böylece başka bir veri türü eklenebilir.

Koleksiyonlar hakkında daha fazla bilgi için bkz. [koleksiyonları](../../concepts/collections.md).

## <a name="related-topics"></a>İlgili konular

|Terim|Tanım|
|----------|----------------|
|[Visual Basic'de dizi boyutları](../../language-features/arrays/array-dimensions.md)|Boyut sayısı ve boyutları açıklar.|
|[Nasıl yapılır: Visual Basic'te dizi değişkeni başlatma](../../language-features/arrays/how-to-initialize-an-array-variable.md)|İlk değerlerle dizilerin doldurmak açıklar.|
|[Nasıl yapılır: Visual Basic'te dizi Sırala](../../language-features/arrays/how-to-sort-an-array.md)|Bir dizinin öğeleri alfabetik olarak sıralamak gösterilmektedir.|
|[Nasıl yapılır: Bir diziyi başka diziye atama](../../language-features/arrays/how-to-assign-one-array-to-another-array.md)|Bir dizi başka bir dizi değişkenine atamak için adımları ve kuralları açıklar.|
|[Dizilerle İlgili Sorun Giderme](../../language-features/arrays/troubleshooting-arrays.md)|Dizilerle çalışırken ortaya çıkan bazı ortak sorunları açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array?displayProperty=nameWithType>
- [Dim Deyimi](../../../language-reference/statements/dim-statement.md)
- [ReDim Deyimi](../../../language-reference/statements/redim-statement.md)
