---
title: Visual Basic'de Diziler
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
caps.latest.revision: "47"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04deeccd19fd4edb3f2c88310d660eedf5c707d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-in-visual-basic"></a>Visual Basic'de Diziler
Bir dizi birbirlerine, her düzeyde dilbilgisi Okul içinde öğrencinin sayısı gibi mantıksal olarak ilişkili değerler kümesidir.  Visual Basic'de diziler hakkında Yardım için Applications (VBA) arıyorsanız bkz [dil başvurusu](https://msdn.microsoft.com/library/office/gg264383\(v=office.14\).aspx).  
  
 Bir dizi kullanarak, aynı ad ile ilgili bu değerleri başvurmak ve bir dizin veya söyleyin indisi birbirinden çağırdı bir sayı kullanın. Değerlerini ayrı ayrı dizinin öğeleri denir. Bunlar, en yüksek dizin değeri ile 0 dizinden bitişik.  
  
 Bir dizi aksine, tek bir değer içeren bir değişken adı verilen bir *skaler* değişkeni.  
  
 Açıklama önce hızlı bazı örnekler:  
  
```vb  
'Declare a single-dimension array of 5 values  
Dim numbers(4) As Integer   
  
'Declare a single-dimension array and set array element values  
Dim numbers = New Integer() {1, 2, 4, 8}  
  
'Redefine the size of an existing array retaining the current values  
ReDim Preserve numbers(15)  
  
'Redefine the size of an existing array, resetting the values  
ReDim numbers(15)  
  
'Declare a multi-dimensional array  
Dim matrix(5, 5) As Double  
  
'Declare a multi-dimensional array and set array element values  
Dim matrix = New Integer(4, 4) {{1, 2}, {3, 4}, {5, 6}, {7, 8}}  
  
'Declare a jagged array  
Dim sales()() As Double = New Double(11)() {}  
```  
  
 **Bu konudaki**  
  
-   [Basit dizi dizi öğeleri](#BKMK_ArrayElements)  
  
-   [Bir dizi oluşturma](#BKMK_CreatingAnArray)  
  
-   [Bir dizi değerlerini depolama](#BKMK_StoringValues)  
  
-   [İlk değerleri içeren bir dizi doldurma](#BKMK_Populating)  
  
    -   [İç içe geçmiş dizi değişmez değerleri](#BKMK_NestedArrayLiterals)  
  
-   [Bir dizi yineleme yapma](#BKMK_Iterating)  
  
-   [Dönüş değerleri ve parametre olarak diziler](#BKMK_ReturnValues)  
  
-   [Basit diziler](#BKMK_JaggedArrays)  
  
-   [Sıfır uzunlukta diziler](#BKMK_ZeroLength)  
  
-   [Dizi boyutu](#BKMK_ArraySize)  
  
-   [Dizi türleri ve diğer türleri](#BKMK_ArrayTypes)  
  
-   [Diziler için bir alternatif olarak koleksiyonları](#BKMK_Collections)  
  
##  <a name="BKMK_ArrayElements"></a>Basit dizi dizi öğeleri  
 Aşağıdaki örnek Öğrenciler sayısı her düzeyde dilbilgisi Okul içinde tutacak bir dizi değişkeni bildirir.  
  
 [!code-vb[VbVbalrArrays#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#2)]  
  
 Dizi `students` önceki örnekte yedi öğeleri içerir. 0 ile 6 öğeleri aralığından dizinleri. Bu dizi yedi değişkenleri bildirme daha basittir.  
  
 Dizi aşağıda gösterilmiştir `students`. Dizideki her öğe için:  
  
-   Düzey öğenin dizinini temsil eder (dizin 0 kindergarten temsil eder).  
  
-   Öğesinde bulunan değer o düzeyde öğrencinin sayısını temsil eder.  
  
 ![Öğrenciler sayıda gösteren dizinin resmi](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")  
"Öğrenciler" dizideki öğeler  
  
 Aşağıdaki örnekte birinci, ikinci ve dizinin son öğenin nasıl çağrılacağını `students`.  
  
 [!code-vb[VbVbalrArrays#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#3)]  
  
 Yalnızca dizi değişkeni adı dizinleri olmadan kullanarak bir bütün olarak diziye başvurabilirsiniz.  
  
 Dizi `students` önceki örnekte bir dizin kullanır ve tek boyutlu olarak kabul edilir. Birden çok dizini veya alt simge kullanan bir dizi çok boyutlu adı verilir. Daha fazla bilgi için bu konunun geri kalanında bakın ve [Visual Basic'de dizi boyutları](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
##  <a name="BKMK_CreatingAnArray"></a>Bir dizi oluşturma  
 Bir dizi çeşitli yollardan boyutunu tanımlayabilirsiniz. Dizi bildirilmişse aşağıdaki örnekte gösterildiği gibi boyutu sağlayabilir.  
  
 [!code-vb[VbVbalrArrays#12](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#12)]  
  
 Aynı zamanda bir `New` yan tümcesini, aşağıdaki örnekte gösterildiği gibi oluşturulduğunda bir dizi boyutunu sağlayın.  
  
 [!code-vb[VbVbalrArrays#11](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#11)]  
  
 Var olan bir dizi varsa, kullanarak boyutunu tanımlayabilirsiniz `Redim` deyimi. Belirtebilirsiniz `Redim` deyimi dizideki değerleri tutmak ya da boş bir dizi oluşturmak belirtebilirsiniz. Aşağıdaki örnek, farklı kullanımlarını gösterir `Redim` var olan bir dizi boyutunu değiştirmek için deyimi.  
  
 [!code-vb[VbVbalrArrays#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#13)]  
  
 Daha fazla bilgi için bkz: [ReDim deyimi](../../../../visual-basic/language-reference/statements/redim-statement.md).  
  
##  <a name="BKMK_StoringValues"></a>Bir dizi değerlerini depolama  
 Her iki yerde de bir dizi türü bir dizin kullanarak erişebilirsiniz `Integer`. Depolamak ve bir dizi değerlerini parantez içine alınmış kendi dizini kullanılarak her bir dizi konum başvurarak alın. Çok boyutlu diziler için dizin (,) virgülle ayrılır. Her bir dizi boyut için bir dizin gerekir. Aşağıdaki örnek değerleri dizilerde saklayan bazı deyimleri gösterir.  
  
 [!code-vb[VbVbalrArrays#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#5)]  
  
 Aşağıdaki örnek diziler de değerlerini alma bazı deyimleri gösterir.  
  
 [!code-vb[VbVbalrArrays#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#6)]  
  
##  <a name="BKMK_Populating"></a>İlk değerleri içeren bir dizi doldurma  
 Değişmez değer bir dizi kullanarak, bir başlangıç değerleri kümesi içeren bir dizi oluşturabilirsiniz. Değişmez değer bir dizi ayraç içine virgülle ayrılmış değerler listesini oluşur (`{}`).  
  
 Değişmez değer bir dizi kullanarak bir dizi oluşturduğunuzda, dizi türü girmeyin veya dizi türü belirlemek için tür çıkarımı kullanın. Aşağıdaki kod, her iki seçenek gösterir.  
  
 [!code-vb[VbVbalrCollectionInitializers#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#3)]  
  
 Tür çıkarımı kullandığınızda, dizi türü dizi değişmez değer için sağlanan baskın listesindeki değerlerin türü tarafından belirlenir. Baskın türü hangi tüm diğer türleri için dizideki değişmez değeri genişletebilirsiniz benzersiz bir türüdür. Bu benzersiz türü belirlenemiyorsa baskın türü dizisindeki tüm diğer türleri daraltmak benzersiz türüdür. Bu benzersiz türlerinden hiçbiri belirlenebilir baskın türü varsa, `Object`. Değişmez değer dizisine sağlanan değerler listesi türündeki değerler içeriyorsa, örneğin, `Integer`, `Long`, ve `Double`, sonuç dizisi türünde `Double`. Her ikisi de `Integer` ve `Long` yalnızca genişletmek `Double`. Bu nedenle, `Double` baskın türüdür. Daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Sınıf üyesi tanımlanan yerel değişkenleri diziler için olayla türleri için bu çıkarım kuralları uygulanır. Sınıf düzeyi değişkenleri oluşturduğunuzda, dizi değişmez değerleri kullanabilirsiniz, ancak sınıf düzeyinde tür çıkarımı kullanamazsınız. Sınıf düzeyinde belirtilen dizi değişmez değerleri türü olarak değişmez değer dizisi için sağlanan değerler sonucu olarak Infer `Object`.  
  
 Açıkça bir dizi değişmez değer kullanılarak oluşturulmuş bir dizi öğelerin türünü belirtebilirsiniz. Bu durumda, değişmez değer dizideki dizinin öğeleri türüne genişletmek gerekir. Aşağıdaki kod örneğinde türünde bir dizi oluşturur `Double` tamsayılar listesinden.  
  
 [!code-vb[VbVbalrCollectionInitializers#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#4)]  
  
###  <a name="BKMK_NestedArrayLiterals"></a>İç içe geçmiş dizi değişmez değerleri  
 Çok boyutlu bir diziye iç içe geçmiş dizi değişmez değerleri kullanarak oluşturabilirsiniz. Sıralama, sonuçta elde edilen dizi ile tutarlı olan veya iç içe geçmiş dizi değişmez değerleri bir boyut ve dimensions sayısı olmalıdır. Aşağıdaki kod örneği, bir dizi değişmez değer kullanarak iki boyutlu dizisi oluşturur.  
  
 [!code-vb[VbVbalrCollectionInitializers#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#7)]  
  
 Önceki örnekte, bir hata ortaya ve iç içe geçmiş dizi değişmez değerleri öğe sayısı eşleşmiyordu. İki boyutlu dışında olacak şekilde dizi değişkeni açıkça bildirilen hata de ortaya.  
  
> [!NOTE]
>  İç dizi değişmez değerleri parantez içinde kapsayan tarafından iç içe geçmiş dizi değişmez değerleri farklı boyutlarının sağladığında, bir hata önleyebilirsiniz. Değerlendirilecek dizi değişmez değer ifadesi parantez zorlamak ve aşağıdaki kodda gösterildiği gibi sonuçta elde edilen değerleri dış dizi ile kullanılır.  
  
 [!code-vb[VbVbalrCollectionInitializers#11](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#11)]  
  
 İç içe geçmiş dizi değişmez değerleri kullanarak çok boyutlu bir diziye oluşturduğunuzda tür çıkarımı kullanabilirsiniz. Tür çıkarımı kullandığınızda, çıkarılan türü için tüm dizi değişmez değerleri iç içe geçirme düzeyi tüm değerleri baskın türüdür. Aşağıdaki kod örneğinde türünde iki boyutlu bir dizi oluşturur `Double` türü değerlerinden `Integer` ve `Double`.  
  
 [!code-vb[VbVbalrCollectionInitializers#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#8)]  
  
 Ek örnekler için bkz: [nasıl yapılır: bir dizi değişken Visual Basic'te başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md).  
  
##  <a name="BKMK_Iterating"></a>Bir dizi yineleme yapma  
 Bir dizi yineleme yaparken dizideki her öğe yüksek dizine düşük dizinden erişin.  
  
 Aşağıdaki örnek bir tek boyutlu dizi kullanarak tekrarlanan [için... Sonraki deyim](../../../../visual-basic/language-reference/statements/for-next-statement.md). <xref:System.Array.GetUpperBound%2A> Yöntemi dizine sahip olabileceği en yüksek değeri döndürür. En düşük dizin değeri her zaman olan 0.  
  
 [!code-vb[VbVbalrArrays#41](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#41)]  
  
 Aşağıdaki örnek kullanarak çok boyutlu bir diziye tekrarlanan bir `For...Next` deyimi. <xref:System.Array.GetUpperBound%2A> Yöntemi boyut belirten bir parametre vardır. `GetUpperBound(0)`ilk boyutu için yüksek dizin değerini döndürür ve `GetUpperBound(1)` ikinci boyutu için yüksek dizin değeri döndürür.  
  
 [!code-vb[VbVbalrArrays#42](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#42)]  
  
 Aşağıdaki örnek bir tek boyutlu dizi kullanarak tekrarlanan bir [For Each... Sonraki deyim](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 [!code-vb[VbVbalrArrays#43](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#43)]  
  
 Aşağıdaki örnek kullanarak çok boyutlu bir diziye tekrarlanan bir `For Each...Next` deyimi. Ancak, iç içe bir kullanırsanız boyutlu bir diziye öğeler hakkında daha fazla denetime sahip `For…Next` deyimi, bir önceki örnekte olduğu gibi yerine bir `For Each…Next` deyimi.  
  
 [!code-vb[VbVbalrArrays#44](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#44)]  
  
##  <a name="BKMK_ReturnValues"></a>Dönüş değerleri ve parametre olarak diziler  
 Dizisinden döndürmek için bir `Function` yordamı, dizi veri türü ve dimensions sayısı dönüş türünü belirtmeniz [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md). İşlev içinde aynı veri türüne ve dimensions sayısı ile bir yerel dizi değişken bildirin. İçinde [dönüş deyimi](../../../../visual-basic/language-reference/statements/return-statement.md), parantezler olmadan yerel dizi değişken içerir.  
  
 Bir parametre olarak bir dizi belirtmek için bir `Sub` veya `Function` yordamı, belirtilen veri türü ve boyut sayısını içeren bir dizi olarak parametre tanımlayın. Yordam çağrısında dimensions sayısı ve aynı veri türüne sahip bir dizi değişken gönderin.  
  
 Aşağıdaki örnekte, `GetNumbers` işlev döndürür bir `Integer()`. Bu dizi türü bir tek boyutlu dizi türü olan `Integer`. `ShowNumbers` Yordamı kabul eden bir `Integer()` bağımsız değişkeni.  
  
 [!code-vb[VbVbalrArrays#51](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#51)]  
  
 Aşağıdaki örnekte, `GetNumbersMultiDim` işlev döndürür bir `Integer(,)`. Bu dizi türüdür iki boyutlu bir dizi türü `Integer`.  `ShowNumbersMultiDim` Yordamı kabul eden bir `Integer(,)` bağımsız değişkeni.  
  
 [!code-vb[VbVbalrArrays#52](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#52)]  
  
##  <a name="BKMK_JaggedArrays"></a>Basit diziler  
 Diğer dizileri öğeleri olarak tutan bir dizi diziler veya basit bir dizi bir dizi bilinir. Basit dizi ve basit bir dizideki her öğe bir veya daha fazla boyutları sahip olabilir. Bazen veri uygulamanızda iki boyutlu ancak dikdörtgen yapısıdır.  
  
 Aşağıdaki örnekte, her öğeye gün dizisidir ay, bir dizi sahiptir. Farklı ay gün sayıları farklı olduğundan, öğeleri dikdörtgen iki boyutlu bir dizi form yok. Bu nedenle, basit bir dizi çok boyutlu bir diziye yerine kullanılır.  
  
 [!code-vb[VbVbalrArrays#21](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#21)]  
  
##  <a name="BKMK_ZeroLength"></a>Sıfır uzunlukta diziler  
 Öğe içeren bir dizi, sıfır uzunluk dizisi olarak da adlandırılır. Sıfır uzunluklu dizi tutan bir değişken değeri yok `Nothing`. Hiçbir öğesi içeren bir dizi oluşturmak için -1, aşağıdaki örnekte gösterildiği gibi olmasını dizinin boyutlardan birini bildirin.  
  
 [!code-vb[VbVbalrArrays#14](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#14)]  
  
 Sıfır uzunluklu dizi aşağıdaki koşullarda oluşturmanız gerekebilir:  
  
-   Riski olmadan bir <xref:System.NullReferenceException> özel durum, kodunuzu gerekir üyelerine erişme <xref:System.Array> gibi sınıfı <xref:System.Array.Length%2A> veya <xref:System.Array.Rank%2A>, veya çağrısı bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gibi işlev <xref:Microsoft.VisualBasic.Information.UBound%2A>.  
  
-   Denetlenecek zorunluluğunu ortadan kaldırarak kullanıcı kodu daha basit tutmak istediğiniz `Nothing` bir özel durum olarak.  
  
-   Kodunuzu sıfır uzunluk dizisi için bir veya daha fazla yordamları geçirmeniz gerekir ya da bir veya daha fazla yordamlardan sıfır uzunlukta bir dizi döndürür bir uygulama programlama arabirimi (API) ile etkileşim kurar.  
  
##  <a name="BKMK_ArraySize"></a>Dizi boyutu  
 Bir dizi tüm boyutlar uzunluklarının ürün boyutudur. Şu anda dizisinde bulunan öğeleri toplam sayısını temsil eder.  
  
 Aşağıdaki örnekte, üç boyutlu bir dizi bildirir.  
  
```vb
Dim prices(3, 4, 5) As Long  
```  
  
 Değişkenin dizisinde toplam boyutunu `prices` (3 + 1) (4 + 1) x (5 + 1) x = 120.  
  
 Kullanarak bir dizinin boyutu bulabilirsiniz <xref:System.Array.Length%2A> özelliği. Kullanarak her boyutunun çok boyutlu bir dizi uzunluğu bulabilirsiniz <xref:System.Array.GetLength%2A> yöntemi.  
  
 Bir dizi değişkeni kullanarak veya ona yeni bir dizi nesnesi atayarak boyutlandırabilirsiniz `ReDim` deyimi.  
  
 Bir dizi boyutu ile ilgilenirken göz önünde bulundurmanız gereken birkaç nokta vardır.  
  
|||  
|---|---|  
|Boyut uzunluğu|Her boyut dizin 0 tabanlı kendi üst sınırı 0'dan aralıkları anlamına gelir. Bu nedenle, belirli bir boyutun uzunluğu 1 ile bu boyut için bildirilen üst sınırdan büyük.|  
|Uzunluğu sınırları|Bir dizinin her boyutun uzunluğu için en büyük değerini sınırlıdır `Integer` olan veri türü (2 ^ 31) - 1. Ancak, bir dizi toplam boyutu da sisteminizdeki kullanılabilir bellek sınırlıdır. Bir dizi başlatmaya çalışırsanız, kullanılabilir RAM miktarını aşıyor, ortak dil çalışma zamanı oluşturur bir <xref:System.OutOfMemoryException> özel durum.|  
|Boyutu ve öğesi boyutu|Bir dizinin boyut öğelerinden veri türünü bağımsızdır. Boyut her zaman öğeleri, değil depolama tüketen bayt sayısı toplam sayısını temsil eder.|  
|Bellek tüketimi|Bir dizi bellekte nasıl depolandığını ilgili tüm varsayımlarda güvenli değildir. Aynı dizi bir 32 bit sistemde 64-bit sistemde daha fazla bellek tüketebileceği şekilde depolama farklı veri genişliği platformlarda değişir. Bir dizi başlattığınızda sistem yapılandırmasına bağlı olarak ortak dil çalışma zamanı (CLR) depolama öğeleri olarak birbirine yakın mümkün olduğunca paketi veya tüm doğal donanım sınırları hizalamak için atayabilirsiniz. Ayrıca, bir dizi bir depolama ek yükü için denetim bilgilerini gerektirir ve bu ek yükü ile eklenen her boyut artırır.|  
  
##  <a name="BKMK_ArrayTypes"></a>Dizi türleri ve diğer türleri  
 Her dizi bir veri türüne sahip, ancak öğeleri veri türünden farklı. Tüm dizileri için tek bir veri türü yok. Bunun yerine, bir dizi veri türü boyutları sayısı tarafından belirlenir veya *derece*, dizi ve dizideki öğeler veri türü. İki dizi değişkenleri aynı verilerin yalnızca zaman aynı derece sahip oldukları yazın ve öğeleri aynı veri türüne sahip olduğu kabul edilir. Bir dizi boyutları uzunlukları dizi veri türü etkilemek değil.  
  
 Her dizi devraldığı <xref:System.Array?displayProperty=nameWithType> sınıfı ve türünde olması için bir değişken bildirebilirsiniz `Array`, ancak türünde bir dizi oluşturamazsınız `Array`. Ayrıca, [ReDim deyimi](../../../../visual-basic/language-reference/statements/redim-statement.md) türü olarak bildirilen bir değişken çalışamaz `Array`. Bu nedenlerle ve tür güvenliği için gibi belirli bir tür olarak her dizi bildirmeniz önerilir; `Integer` önceki örnekte.  
  
 Bir dizi veya öğeleri çeşitli şekillerde veri türünü bulabilirsiniz.  
  
-   Çağırabilirsiniz <xref:System.Object.GetType%2A?displayProperty=nameWithType> değişkenin almasını yöntemi bir <xref:System.Type> nesne değişkeni çalışma zamanı tür. <xref:System.Type> Nesnesi özelliklerini ve yöntemlerini kapsamlı bilgileri tutar.  
  
-   Değişkene geçirebilirsiniz <xref:Microsoft.VisualBasic.Information.TypeName%2A> almaya işlevi bir `String` çalışma zamanı tür adını içeren.  
  
-   Değişkene geçirebilirsiniz <xref:Microsoft.VisualBasic.Information.VarType%2A> almaya işlevi bir `VariantType` değişkenin türü sınıflandırma gösteren değer.  
  
 Aşağıdaki örnek çağrıları `TypeName` işlevi dizi türü ve dizideki öğeler türünü belirler. Dizi türü `Integer(,)` ve dizideki öğeler türü `Integer`.  
  
 [!code-vb[VbVbalrArrays#15](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#15)]  
  
##  <a name="BKMK_Collections"></a>Diziler için bir alternatif olarak koleksiyonları  
 Diziler oluşturmak ve güçlü şekilde yazılan nesnelerin sabit sayıda ile çalışmak için çok kullanışlıdır. Koleksiyonları nesneleri grupları ile çalışmak için daha esnek bir şekilde sağlar. Diziler farklı olarak, birlikte çalıştığınız nesne grubunu büyür ve dinamik olarak uygulama değişikliği ihtiyaçları geliştikçe daraltma.  
  
 Bir dizinin boyutu değiştirmeniz gerekiyorsa, kullanmalısınız [ReDim deyimi](../../../../visual-basic/language-reference/statements/redim-statement.md). Bunu yaptığınızda [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] yeni bir dizi oluşturur ve önceki dizi elden için serbest bırakır. Bu, yürütme sürüyor. Bu nedenle, sık değişiklikler veya çalıştığınız öğe sayısı ihtiyacınız öğe maksimum sayısı tahmin edilemez, bir koleksiyonu kullanarak daha iyi performans elde edebilirsiniz.  
  
 Bazı koleksiyonlar için nesne anahtarı kullanarak hızlı bir şekilde alabilmeleri koleksiyona koymak nesnesine bir anahtar atayabilirsiniz.  
  
 Koleksiyonunuz yalnızca bir veri türündeki öğeler içeriyorsa, sınıflarda birini kullanabilirsiniz <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı. Böylece başka bir veri türü eklenebilir bir genel koleksiyon tür güvenliği zorlar. Genel bir koleksiyondaki bir öğe aldığınızda, kendi veri türü belirlenemiyor veya dönüştürmeden gerekmez.  
  
 Koleksiyonlar hakkında daha fazla bilgi için bkz: [koleksiyonları](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b).  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] genel bir sınıf <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> liste koleksiyonu oluşturmak için `Customer` nesneleri.  
  
 [!code-vb[VbVbalrArrays#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#1)]  
  
 Bildirimi `CustomerFile` koleksiyonu belirler, yalnızca türündeki öğeler içerebilir `Customer`. Ayrıca, 200 öğeleri için bir başlangıç kapasitesi sağlar. Yordam `AddNewCustomer` yeni öğe geçerliliğini denetler ve koleksiyona ekler. Yordam `PrintCustomers` kullanan bir `For Each` koleksiyonu çapraz geçiş ve alt öğelerini görüntülemek için döngü.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Terim|Tanım|  
|----------|----------------|  
|[Visual Basic'de dizi boyutları](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|Rank ve boyutları dizilerde açıklanmaktadır.|  
|[Nasıl yapılır: Visual Basic'te dizi değişkeni başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|Dizilerle ilk değerleri doldurmak açıklar.|  
|[Nasıl yapılır: Visual Basic'te bir dizi sıralama](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|Dizi öğelerini alfabetik olarak sıralamak gösterilmiştir.|  
|[Nasıl yapılır: bir diziyi başka diziye atama](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|Kuralları ve bir dizi başka bir dizi değişkenine atamak için adımlar açıklanmaktadır.|  
|[Dizilerle ilgili sorun giderme](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|Dizilerle çalışırken ortaya bazı yaygın sorunlar ele alınmaktadır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Array>  
 [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim deyimi](../../../../visual-basic/language-reference/statements/redim-statement.md)
