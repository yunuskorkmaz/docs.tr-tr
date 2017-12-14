---
title: Visual Basic'de Diziler
ms.custom: 
ms.date: 12/06/2017
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
author: rpetrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: d223ca8b0ff59a13c31fa777e5cb6a97918421c6
ms.sourcegitcommit: 01ea3686e74ff05e4f6de3d8d46dc603d051ec00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2017
---
# <a name="arrays-in-visual-basic"></a>Visual Basic'de Diziler
Bir dizi olarak ifade edilmektedir değerler kümesidir *öğeleri*, mantıksal olarak ilgili diğer için. Örneğin, bir dizi dilbilgisi Okul içinde her düzeyde öğrencinin sayısının oluşabilir; Dizideki her öğe tek bir düzeyde öğrencinin sayısıdır. Benzer şekilde, bir dizi bir sınıf için öğrencinin dereceleri oluşur; her dizinin tek bir düzeyde öğedir.    

Bizim veri öğelerin her birini depolamak için olası bağımsız değişkenler var. Uygulamamız Öğrenci dereceleri analiz eder, örneğin, biz ayrı bir değişken her Öğrencinin notu için gibi kullanabilir `englishGrade1`, `englishGrade2`vb. Bu yaklaşım, üç ana sınırlamalara sahiptir:
- Biz işlemek sahibiz tam olarak kaç dereceleri tasarım zamanında bilmeniz gerekir.
- Çok sayıda derece hızlı bir şekilde işleme yönetilmeleri haline gelir. Bu sırayla ciddi hatalar sahip çok daha büyük olasılıkla bir uygulama sağlar.
- Etmek zordur. Eklediğimiz her yeni bir sınıf uygulama değiştiren, yeniden derlenmesi, imzalanması ve dağıtılması gerektiğini gerektirir.  
 
 Bir dizi kullanarak tarafından aynı ad ile ilgili bu değerleri başvurmak ve çağrılan bir sayı kullanın bir *dizin* veya *alt simge* dizideki konumuna bağlı tek bir öğe tanımlamak için. Bir dizi aralığı 0'dan bir dizide öğe toplam sayısından daha az dizinleri. Bir dizinin boyutu tanımlamak için Visual Basic sözdizimini kullandığınızda, en yüksek dizinini, dizideki öğeler değil toplam sayısını belirtin. Bir birim olarak dizi birlikte çalışabilir ve öğeleri yineleme özelliğini tam olarak tasarım zamanında içerdiği kaç öğeleri bilmenize gerek gelen boşaltır.
  
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
  
 ## <a name="in-this-article"></a>Bu makalede
  
- [Basit dizi dizi öğeleri](#array-elements-in-a-simple-array)  
  
- [Bir dizi oluşturma](#creating-an-array)  
  
- [Bir dizi değerlerini depolama](#storing-values-in-an-array)  
  
- [Dizi değişmez değerleri olan bir dizi doldurma](#populating-an-array-with-array-literals)  
  
- [Bir dizi yineleme yapma](#iterating-through-an-array)  
  
- [Dizi boyutu](#BKMK_ArraySize)  

- [Dizi türü](#the-array-type)  
  
- [Dönüş değerleri ve parametre olarak diziler](#arrays-as-return-values-and-parameters)  
- [Basit diziler](#jagged-arrays)  
  
- [Sıfır uzunlukta diziler](#zero-length-arrays)  

- [Bir dizi bölme](#splitting-an-array)
  
- [Diziler için bir alternatif olarak koleksiyonları](#collections-as-an-alternative-to-arrays)  
  
##  <a name="array-elements-in-a-simple-array"></a>Basit dizi dizi öğeleri  

Adlı bir dizi oluşturalım `students` Öğrenciler sayısı her düzeyde dilbilgisi Okul içinde depolamak. 0 ile 6 öğeleri aralığından dizinleri. Bu dizi kullanarak yedi değişkenleri bildirme daha basittir.

Aşağıdaki çizimde gösterildiği `students` dizi. Dizideki her öğe için:  
  
-   Düzey öğenin dizinini temsil eder (dizin 0 kindergarten temsil eder).
  
-   Öğesinde bulunan değer o düzeyde öğrencinin sayısını temsil eder.
  
 ![Öğrenciler sayıda gösteren dizinin resmi](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")  
"Öğrenciler" dizideki öğeler  
 
Aşağıdaki örnek, oluşturur ve dizi kullanan Visual Basic kodu içerir:

 [!code-vb[simple-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]  

Örneğin, üç şey yapar:

- Bunu bildiren bir `students` yedi öğeleri dizisi. Sayı `6` dizideki bildirimi dizideki son dizin gösterir; bir değer dizideki öğe sayısından daha az.
- Dizideki her öğe için değerleri atar. Dizi öğeleri dizi adı kullanarak ve tek tek öğenin dizini parantez içine dahil olmak üzere erişilir.
- Dizinin her bir değeri listeler. Örnek kullanan bir [ `For` ](../../../language-reference/statements/for-next-statement.md) dizin numarası ile dizinin her öğesine erişmek için bildirimi.
  
 `students` Önceki örnekte dizidir tek boyutlu dizi çünkü bir dizin kullanır. Birden çok dizini veya alt simge kullanan bir dizi adlı *çok boyutlu*. Daha fazla bilgi için bu makalenin geri kalanını görmek ve [Visual Basic'de dizi boyutları](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
##  <a name="creating-an-array"></a>Bir dizi oluşturma  
 
Bir dizinin boyutu çeşitli yollarla tanımlayabilirsiniz: 

- Dizi bildirilmişse boyutu belirtebilirsiniz:
  
    [!code-vb[creating1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]  
  
 - Kullanabileceğiniz bir `New` oluşturulduğunda bir dizi boyutu sağlamak için yan tümcesi:  
  
    [!code-vb[creating2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]  
  
 Var olan bir dizi varsa, kullanarak boyutunu tanımlayabilirsiniz [ `Redim` ](../../../../visual-basic/language-reference/statements/redim-statement.md) deyimi. Belirtebilirsiniz `Redim` deyimi tutmak dizideki değerleri ya da boş bir dizi oluşturmak belirtebilirsiniz. Aşağıdaki örnek, farklı kullanımlarını gösterir `Redim` var olan bir dizi boyutunu değiştirmek için deyimi.  
  
 [!code-vb[redimensioning](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]  
  
 Daha fazla bilgi için bkz: [ReDim deyimi](../../../../visual-basic/language-reference/statements/redim-statement.md).  
  
##  <a name="storing-values-in-an-array"></a>Bir dizi değerlerini depolama
 
 Her iki yerde de bir dizi türü bir dizin kullanarak erişebilirsiniz `Integer`. Depolamak ve bir dizi değerlerini parantez içine alınmış kendi dizini kullanılarak her bir dizi konum başvurarak alın. Çok boyutlu diziler için dizin (,) virgülle ayrılır. Her bir dizi boyut için bir dizin gerekir. 

Aşağıdaki örnek, depolama ve diziler değerleri alma bazı deyimleri gösterir.
  
 [!code-vb[store-and-retrieve](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]  
  
## <a name="populating-an-array-with-array-literals"></a>Dizi değişmez değerleri olan bir dizi doldurma
 Değişmez değer bir dizi kullanarak oluşturduğunuz aynı anda bir dizi bir başlangıç değerleri kümesi ile doldurabilirsiniz. Değişmez değer bir dizi ayraç içine virgülle ayrılmış değerler listesini oluşur (`{}`).  
  
 Değişmez değer bir dizi kullanarak bir dizi oluşturduğunuzda, dizi türü girmeyin veya dizi türü belirlemek için tür çıkarımı kullanın. Aşağıdaki örnek, her iki seçenek gösterir.  
  
 [!code-vb[create-with-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]  
  
 Tür çıkarımı kullandığınızda, dizi türü tarafından belirlenir *baskın türü* değişmez değerler listesinde. Baskın türü dizisindeki tüm diğer türleri genişletmek türüdür. Bu benzersiz türü belirlenemiyorsa baskın türü dizisindeki tüm diğer türleri daraltmak benzersiz türüdür. Bu benzersiz türlerinden hiçbiri belirlenebilir baskın türü varsa, `Object`. Değişmez değer dizisine sağlanan değerler listesi türündeki değerler içeriyorsa, örneğin, `Integer`, `Long`, ve `Double`, sonuç dizisi türünde `Double`. Çünkü `Integer` ve `Long` yalnızca genişletmek `Double`, `Double` baskın türüdür. Daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). 
 
> [!NOTE] 
> Yalnızca bir tür üyesi yerel değişkenleri olarak tanımlanan diziler için tür çıkarımı kullanabilirsiniz. Bir açık tür tanımı olmazsa, dizi değişmez değerleri sınıf düzeyinde tanımlanan dizilere türlerinin `Object[]`. Daha fazla bilgi için bkz: [yerel türü çıkarımı](../variables/local-type-inference.md). 

Önceki örnekte tanımlar Not `values` türünde bir dizi olarak `Double` tüm dizi değişmez değerleri türü olsa bile `Integer`. Dizi değişmez değerleri için genişletebilirsiniz olduğundan bu diziye oluşturabilirsiniz `Double` değerleri. 
  
 Ayrıca oluşturabilir ve çok boyutlu bir diziye kullanarak doldurmak *dizi değişmez değerleri iç içe geçmiş*. İç içe geçmiş dizi değişmez değerleri elde edilen dizi ile tutarlı olan bir dizi boyutları olması gerekir. Aşağıdaki örnek, iç içe geçmiş dizi değişmez değerleri kullanarak iki boyutlu dizisi oluşturur.  
  
 [!code-vb[nested-array-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]  
  
İç içe geçmiş dizi değişmez değerleri öğe sayısı eşleşmiyorsa iç içe geçmiş dizi değişmez değerleri oluşturma ve bir dizi doldurmak için kullanılırken bir hata oluşur. Dizi değişmez değerleri boyutlardan farklı sayıda dizi değişkeni açıkça bildirirseniz da bir hata oluşur. 
  
Tek boyutlu diziler için yapabildiğiniz gibi çok boyutlu bir diziye iç içe geçmiş dizi değişmez değerleri oluştururken tür çıkarımı güvenebilirsiniz. Çıkarılan türü, tüm dizi değişmez değerleri tüm iç içe geçirme düzeyi tüm değerleri için baskın türüdür. Aşağıdaki örnek türünde iki boyutlu bir dizi oluşturur `Double[,]` türü değerlerinden `Integer` ve `Double`.  
  
 [!code-vb[nested-type-inference](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]  
  
 Ek örnekler için bkz: [nasıl yapılır: bir dizi değişken Visual Basic'te başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md).  
  
##  <a name="iterating-through-an-array"></a>Bir dizi yineleme yapma  
 Bir dizi yineleme yaparken, dizideki her öğe için en düşük dizin en yüksek veya en yüksek erişim için en düşük. Genellikle, ya da kullanma [için... Sonraki deyim](../../../../visual-basic/language-reference/statements/for-next-statement.md) veya [For Each... Sonraki deyim](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) bir dizi öğelerinde yineleme yapmak için. Dizinin üst sınırları bilmiyorsanız, çağırabilirsiniz <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> dizin için en yüksek değeri almak için yöntemi. En düşük dizin değeri neredeyse olsa da her zaman 0 çağırabilirsiniz <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> dizini en düşük değerini almak için yöntemi.   
  
 Aşağıdaki örnek bir tek boyutlu dizi kullanarak tekrarlanan [ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md) deyimi. 
  
 [!code-vb[iterate-one-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]  
  
 Aşağıdaki örnek kullanarak çok boyutlu bir diziye tekrarlanan bir [ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md) deyimi. <xref:System.Array.GetUpperBound%2A> Yöntemi boyut belirten bir parametre vardır. `GetUpperBound(0)`ilk boyut, en yüksek dizinini döndürür ve `GetUpperBound(1)` ikinci boyutu en yüksek dizinini döndürür.
  
 [!code-vb[iterate-two-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]  
  
 Aşağıdaki örnek kullanan bir [For Each... Sonraki deyim](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)tek boyutlu dizi ve iki boyutlu bir dizi aracılığıyla yinelemek için.  
  
 [!code-vb[iterate-for-each-next](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]  
  
## <a name="array-size"></a>Dizi boyutu  

 Bir dizi tüm boyutlar uzunluklarının ürün boyutudur. Şu anda dizisinde bulunan öğeleri toplam sayısını temsil eder.  Örneğin, aşağıdaki örnekte, her boyut dört öğelerle 2 boyutlu bir dizi bildirir. Örneğin çıktısını gösterildiği gibi dizinin boyutu 16'dır (veya (3 + 1) * (3 + 1).

 [!code-vb[array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]  

> [!NOTE] 
> Bu tartışma dizi boyutunun basit diziler için geçerli değildir. Basit diziler ve basit bir dizi boyutunu belirleme hakkında daha fazla bilgi için bkz: [basit dizileri](#jagged-arrays) bölümü.
  
  Kullanarak bir dizinin boyutu bulabilirsiniz <xref:System.Array.Length%2A?displayProperty=nameWithType> özelliği. Kullanarak her boyut bir çok boyutlu dizi uzunluğu bulabilirsiniz <xref:System.Array.GetLength%2A?displayProperty=nameWithType> yöntemi.  
  
 Bir dizi değişkeni kullanarak veya ona yeni bir dizi nesnesi atayarak boyutlandırabilirsiniz [ `ReDim` deyimi](../../../../visual-basic/language-reference/statements/redim-statement.md) deyimi. Aşağıdaki örnek kullanır `ReDim` 100 öğeli bir dizi 51 öğeli bir dizi değiştirmek için deyimi.

 [!code-vb[resize-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]  
  
 Bir dizi boyutu ile ilgilenirken göz önünde bulundurmanız gereken birkaç nokta vardır.  
  
|||  
|---|---|  
|Boyut uzunluğu|Her boyut dizin 0 tabanlı kendi üst sınırı 0'dan aralıkları anlamına gelir. Bu nedenle, belirli bir boyutun uzunluğu bu boyut bildirilen üst sınırdan büyük biridir.|  
|Uzunluğu sınırları|Bir dizinin her boyutun uzunluğu için en büyük değerini sınırlıdır `Integer` olan veri türü <xref:System.Int32.MaxValue?displayProperty=nameWithType> veya (2 ^ 31) - 1. Ancak, bir dizi toplam boyutu da sisteminizdeki kullanılabilir bellek sınırlıdır. Bir dizi başlatmaya çalışırsanız, kullanılabilir bellek miktarını aşıyor, çalışma zamanı oluşturur bir <xref:System.OutOfMemoryException>.|  
|Boyutu ve öğesi boyutu|Bir dizinin boyut öğelerinden veri türünü bağımsızdır. Boyut her zaman öğeleri, değil bellekte tüketen bayt sayısı toplam sayısını temsil eder.|  
|Bellek tüketimi|Bir dizi bellekte nasıl depolandığını ilgili tüm varsayımlarda güvenli değildir. Aynı dizi bir 32 bit sistemde 64-bit sistemde daha fazla bellek tüketebileceği şekilde depolama farklı veri genişliği platformlarda değişir. Bir dizi başlattığınızda sistem yapılandırmasına bağlı olarak ortak dil çalışma zamanı (CLR) depolama öğeleri olarak birbirine yakın mümkün olduğunca paketi veya tüm doğal donanım sınırları hizalamak için atayabilirsiniz. Ayrıca, bir dizi bir depolama ek yükü için denetim bilgilerini gerektirir ve bu ek yükü ile eklenen her boyut artırır.|  

## <a name="the-array-type"></a>Dizi türü 
 Her dizi öğeleri veri türünden farklı bir veri türü var. Tüm dizileri için tek bir veri türü yok. Bunun yerine, bir dizi veri türü boyutları sayısı tarafından belirlenir veya *derece*, dizi ve dizideki öğeler veri türü. İki dizi değişkenleri yalnızca zaman aynı derece sahip oldukları yazın ve öğeleri aynı veri türüne sahip aynı verilerin kullanılabilir. Bir dizi boyutları uzunlukları dizi veri türü etkilemek değil.  
  
 Her dizi devraldığı <xref:System.Array?displayProperty=nameWithType> sınıfı ve türünde olması için bir değişken bildirebilirsiniz `Array`, ancak türünde bir dizi oluşturamazsınız `Array`. Örneğin, aşağıdaki kod bildirir rağmen `arr` türünde olması için değişken `Array` ve çağırır <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> dizi, dizinin türü örneği için yöntemi kanıtlar olmasını Object [].

 [!code-vb[array-class](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)] 

Ayrıca, [ReDim deyimi](../../../../visual-basic/language-reference/statements/redim-statement.md) türü olarak bildirilen bir değişken çalışamaz `Array`. Bu nedenlerle ve tür güvenliği için belirli bir tür olarak her diziyi bildirmek için önerilir.  
  
 Bir dizi veya öğeleri çeşitli şekillerde veri türünü bulabilirsiniz. 
  
-   Çağırabilirsiniz <xref:System.Object.GetType%2A> yöntemi almak için değişken bir <xref:System.Type> değişkeni çalışma zamanı türünü temsil eden nesne. <xref:System.Type> Nesnesi özelliklerini ve yöntemlerini kapsamlı bilgileri tutar.  
  
-   Değişkene geçirebilirsiniz <xref:Microsoft.VisualBasic.Information.TypeName%2A> almak için işlevi bir `String` çalışma zamanı tür adı.  
  
 Aşağıdaki örnek hem çağırır `GetType` yöntemi ve `TypeName` işlevi bir dizi türü belirlenemedi. Dizi türü `Byte(,)`. Unutmayın <xref:System.Type.BaseType%2A?displayProperty=nameWithType> özelliği de bayt dizisi temel türü olduğunu gösterir <xref:System.Array> sınıfı.  
  
 [!code-vb[array-type](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]  
  
##  <a name="arrays-as-return-values-and-parameters"></a>Dönüş değerleri ve parametre olarak diziler  
 Dizisinden döndürmek için bir `Function` yordamı, dizi veri türü ve dimensions sayısı dönüş türünü belirtmeniz [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md). İşlev içinde aynı veri türüne ve dimensions sayısı ile bir yerel dizi değişken bildirin. İçinde [dönüş deyimi](../../../../visual-basic/language-reference/statements/return-statement.md), parantezler olmadan yerel dizi değişken içerir.  
  
 Bir parametre olarak bir dizi belirtmek için bir `Sub` veya `Function` yordamı, belirtilen veri türü ve boyut sayısını içeren bir dizi olarak parametre tanımlayın. Yordam çağrısında dimensions sayısı ve aynı veri türüne sahip bir dizi değişken geçirin.  
  
 Aşağıdaki örnekte, `GetNumbers` işlev döndürür bir `Integer()`, tek boyutlu dizi türü `Integer`. `ShowNumbers` Yordamı kabul eden bir `Integer()` bağımsız değişkeni. 
  
 [!code-vb[return-value-and-params](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]  
  
 Aşağıdaki örnekte, `GetNumbersMultiDim` işlev döndürür bir `Integer(,)`, iki boyutlu bir dizi türü `Integer`.  `ShowNumbersMultiDim` Yordamı kabul eden bir `Integer(,)` bağımsız değişkeni.  
  
 [!code-vb[multidimensional-return-value](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]  
  
## <a name="jagged-arrays"></a>Basit Diziler  
 
Bazen veri uygulamanızda iki boyutlu ancak dikdörtgen yapısıdır. Örneğin, her ayın yüksek sıcaklık hakkındaki verileri depolamak için bir dizi kullanabilirsiniz. Dizinin ilk boyutu ay temsil eder, ancak ikinci boyut gün sayısını temsil eder ve bir ay içindeki gün sayısını Tekdüzen değil. A *Basit dizi*, ayrıca adlandırılan bir *dizi dizisi*, bu tür senaryoları için tasarlanmıştır. Basit bir dizi öğeleri de diziler olan bir dizidir. Basit dizi ve basit bir dizideki her öğe bir veya daha fazla boyutları sahip olabilir.  
  
 Aşağıdaki örnek, ay, her öğeye gün dizisidir dizisi kullanır. Farklı ay gün sayıları farklı olduğundan bu örnek basit bir dizi kullanır.  Örneğin, basit bir dizi oluşturmak, değerler, atayın ve alabilir ve değerlerini görüntülemek gösterilmektedir.
  
 [!code-vb[jagged-arrays](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]  

Önceki örnek değerler Basit dizi öğesi öğeli düzenli olarak kullanarak atayan bir `For...Next` döngü. İç içe geçmiş dizi değişmez değerleri kullanarak basit bir dizi öğelerine değerler de atayabilirsiniz. Ancak, kullanma girişimi iç içe geçmiş dizi değişmez değerleri (örneğin, ```Dim valuesjagged = {{1, 2}, {2, 3, 4}}```) derleyici hatası oluşturur [BC30568](../../../,,/../misc/bc30568.md). Hatayı düzeltmek için iç dizi değişmez değerleri parantez içine alın. Değerlendirilecek dizi değişmez değer ifadesi parantez zorlamak ve aşağıdaki örnekte gösterildiği gibi sonuçta elde edilen değerleri dış dizi ile kullanılır.  
  
 [!code-vb[jagged-array-initialization](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)] 

Basit bir dizi diziler öğeleri içeren tek boyutlu bir dizidir. Bu nedenle, <xref:System.Array.Length%2A?displayProperty=nameWithType> özelliği ve `Array.GetLength(0)` yöntemi tek boyutlu diziye öğe sayısını döndürür ve `Array.GetLength(1)` oluşturur bir <xref:System.IndexOutOfRangeException> basit bir dizi çok boyutlu olmadığından. Her subarray's değerini alarak her subarray öğelerin sayısını belirlemek <xref:System.Array.Length%2A?displayProperty=nameWithType> özelliği. Aşağıdaki örnekte basit bir dizide öğe sayısını belirlemek nasıl gösterilmektedir.

[!code-vb[jagged-array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)] 

## <a name="zero-length-arrays"></a>Sıfır uzunlukta diziler  
Visual Basic ayıran arasında başlatılmamış bir dizi (değeri olan bir dizi `Nothing`) ve bir *sıfır uzunluk dizisi* veya boş dizi (herhangi bir öğesi olan bir dizi.) Başlatılmamış bir dizi değil dimensioned bir ya da herhangi bir değeri atanmış vardı. Örneğin:

```vb
Dim arr() As String
```
Sıfır uzunluklu dizi -1 olan bir boyut ile bildirilir. Örneğin:

```vb
Dim arrZ(-1) As String
```
Sıfır uzunluklu dizi aşağıdaki koşullarda oluşturmanız gerekebilir:  
  
-   Riski olmadan bir <xref:System.NullReferenceException> özel durum, kodunuzu gerekir üyelerine erişme <xref:System.Array> gibi sınıfı <xref:System.Array.Length%2A> veya <xref:System.Array.Rank%2A>, veya Visual Basic işlevi gibi arama <xref:Microsoft.VisualBasic.Information.UBound%2A>.  
  
-   Korumak istediğiniz kodunuzu denetlemek zorunluluğunu ortadan kaldırarak basit `Nothing` bir özel durum olarak.  
  
-   Kodunuzu sıfır uzunluk dizisi için bir veya daha fazla yordamları geçirmeniz gerekir ya da bir veya daha fazla yordamlardan sıfır uzunlukta bir dizi döndürür bir uygulama programlama arabirimi (API) ile etkileşim kurar.

## <a name="splitting-an-array"></a>Bir dizi bölme

Bazı durumlarda, tek bir dizi birden çok diziye bölme gerekebilir. Bu, noktası veya noktaları Bölünecek dizi olan tanımlama ve sonra iki veya daha fazla ayrı diziye dizi yollanmasından içerir. 

> [!NOTE] 
> Bu bölümde bazı sınırlayıcıyı kullanarak bir dize dizisi içine tek bir dize bölme açıklanmamıştır. Bir dize bölme hakkında daha fazla bilgi için bkz: <xref:System.String.Split%2A?displayProperty=nameWithType> yöntemi.

Bir dizi bölme en yaygın ölçütlerini şunlardır:

- Dizideki öğelerin sayısı Örneğin, birden çok belirtilen sayıda öğeyi bir dizi yaklaşık eşit parçalar sayıya bölme isteyebilirsiniz. Bu amaçla tarafından döndürülen değer kullanabilirsiniz <xref:System.Array.Length%2A?displayProperty=nameWithType> veya <xref:System.Array.GetLength%2A?displayProperty=nameWithType> yöntemi.

- Dizi bölme yeri gösteren ayırıcı olarak hizmet veren bir öğenin değeri. Belirli bir değeri çağırarak arayabilirsiniz <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> ve <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> yöntemleri.
 
Dizin veya dizinleri, dizi bölme saptadıktan sonra daha sonra ayrı diziler çağırarak oluşturabilirsiniz <xref:System.Array.Copy%2A?displayProperty=nameWithType> yöntemi. 

Aşağıdaki örnek, bir dizi yaklaşık eşit boyutu iki diziye ayırır. (Dizi öğelerinin toplam sayı tek ise ilk dizi ikinciden daha fazla öğe var.) 

[!code-vb[splitting-an-array-by-length](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)] 

Aşağıdaki örnek dizilerinin dizi ayırıcı olarak hizmet veren "zzz" değeri olan bir öğeyi varlığına dayalı bir dize dizisi ayıran. Yeni diziler sınırlayıcısı içeriyor öğesi dahil etmeyin.

[!code-vb[splitting-an-array-by-delimiter](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)] 

## <a name="joining-arrays"></a>Diziler birleştirme

Ayrıca, tek bir büyük dizi dizileri sayısı birleştirebilirsiniz. Bunu yapmak için ayrıca kullandığınız <xref:System.Array.Copy%2A?displayProperty=nameWithType> yöntemi. 

> [!NOTE] 
> Bu bölümde, tek bir dize halinde bir dize dizisi birleştirme açıklanmamıştır. Bir dize dizisi birleştirme hakkında daha fazla bilgi için bkz: <xref:System.String.Join%2A?displayProperty=nameWithType> yöntemi.

Her dizinin öğeleri yeni diziye kopyalamadan önce böylece yeni bir dizi accompodate için yeterince büyük dizi ayarladıktan ilk sağlamalısınız. Bunu iki yoldan biriyle yapabilirsiniz:

- Kullanım [ `ReDim Preserve` ](../../../../visual-basic/language-reference/statements/redim-statement.md) deyimi dinamik olarak yeni öğeler eklemeden önce dizi genişletin. Bu kolay tekniği olan, ancak büyük diziler kopyalarken, performans düşüşünü ve aşırı bellek kullanımına neden olabilir.
- Yeni bir büyük dizi için gereken öğeleri toplam sayısını hesaplayın sonra her kaynak dizinin öğeleri ekleyin.

Aşağıdaki örnek, tek bir dizi on öğeleri dört dizilerle eklemek için ikinci yaklaşımı kullanır.  

[!code-vb[joining-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)] 

Bu durumda kaynak diziler tüm küçük olduğundan, biz her yeni bir dizi öğelerini eklemek gibi biz de dinamik olarak dizi genişletebilirsiniz. Aşağıdaki örnek, yapar.

[!code-vb[joining-an-array-dynamically](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)] 

##  <a name="collections-as-an-alternative-to-arrays"></a>Diziler için bir alternatif olarak koleksiyonları  
 Diziler oluşturmak ve güçlü şekilde yazılan nesnelerin sabit sayıda ile çalışmak için çok kullanışlıdır. Koleksiyonları nesneleri grupları ile çalışmak için daha esnek bir şekilde sağlar. Diziler gerektiren açıkça bir dizi boyutunu değiştirme [ `ReDim` deyimi](../../../../visual-basic/language-reference/statements/redim-statement.md), koleksiyonları büyür ve dinamik olarak bir uygulama değişikliği ihtiyaçları geliştikçe daraltma.  
  
 Kullandığınızda `ReDim` bir dizi redimension için Visual Basic yeni bir dizi oluşturur ve önceki serbest bırakır. Bu, yürütme sürüyor. Sık değişiklikler veya çalıştığınız öğe sayısı ihtiyacınız öğe maksimum sayısı tahmin edilemez, bu nedenle, genellikle daha iyi performans koleksiyonu kullanarak elde.  
  
 Bazı koleksiyonlar için nesne anahtarı kullanarak hızlı bir şekilde alabilmeleri koleksiyona koymak nesnesine bir anahtar atayabilirsiniz.  
  
 Koleksiyonunuz yalnızca bir veri türündeki öğeler içeriyorsa, sınıflarda birini kullanabilirsiniz <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı. Böylece başka bir veri türü eklenebilir bir genel koleksiyon tür güvenliği zorlar.  
  
 Koleksiyonlar hakkında daha fazla bilgi için bkz: [koleksiyonları](../../concepts/collections.md).
  
## <a name="related-topics"></a>İlgili Konular  
  
|Terim|Tanım|  
|----------|----------------|  
|[Visual Basic'de dizi boyutları](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|Rank ve boyutları dizilerde açıklanmaktadır.|  
|[Nasıl yapılır: Visual Basic'te dizi değişkeni başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|Dizilerle ilk değerleri doldurmak açıklar.|  
|[Nasıl yapılır: Visual Basic'te bir dizi sıralama](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|Dizi öğelerini alfabetik olarak sıralamak gösterilmiştir.|  
|[Nasıl yapılır: bir diziyi başka diziye atama](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|Kuralları ve bir dizi başka bir dizi değişkenine atamak için adımlar açıklanmaktadır.|  
|[Dizilerle ilgili sorun giderme](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|Dizilerle çalışırken ortaya bazı yaygın sorunlar ele alınmaktadır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Array?displayProperty=nameWithType>  
 [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim deyimi](../../../../visual-basic/language-reference/statements/redim-statement.md)
