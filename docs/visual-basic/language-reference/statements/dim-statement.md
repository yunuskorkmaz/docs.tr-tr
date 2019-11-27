---
title: Dim Deyimi
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: ac66ffdba622673ef42017d147c05b2a2733dede
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343764"
---
# <a name="dim-statement-visual-basic"></a>Dim Deyimi (Visual Basic)

Bir veya daha fazla değişken için depolama alanı bildirir ve ayırır.

## <a name="syntax"></a>Sözdizimi

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a>Bölümler

- `attributelist`

  İsteğe bağlı. Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).

- `accessmodifier`

  İsteğe bağlı. Aşağıdakilerden biri olabilir:

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  [Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.

- `Shared`

  İsteğe bağlı. Bkz. [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).

- `Shadows`

  İsteğe bağlı. Bkz. [gölgeler](../../../visual-basic/language-reference/modifiers/shadows.md).

- `Static`

  İsteğe bağlı. Bkz. [statik](../../../visual-basic/language-reference/modifiers/static.md).

- `ReadOnly`

  İsteğe bağlı. Bkz. [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).

- `WithEvents`

İsteğe bağlı. Bunların, olayları yükseltebileceği bir sınıfın örneklerine başvuran nesne değişkenleri olduğunu belirtir. Bkz. [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).

- `variablelist`

  Gerekli. Bu bildirimde bildirildiği değişkenlerin listesi.

  `variable [ , variable ... ]`

  Her `variable` aşağıdaki söz dizimi ve bölümlere sahiptir:

  `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`

  |Bölümüyle|Açıklama|
  |---|---|
  |`variablename`|Gerekli. Değişkenin adı. Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
  |`boundslist`|İsteğe bağlı. Bir dizi değişkeninin her boyutunun sınırları listesi.|
  |`New`|İsteğe bağlı. `Dim` deyimleri çalıştırıldığında, sınıfının yeni bir örneğini oluşturur.|
  |`datatype`|İsteğe bağlı. Değişkenin veri türü.|
  |`With`|İsteğe bağlı. Nesne Başlatıcısı listesini tanıtır.|
  |`propertyname`|İsteğe bağlı. Örneği yaptığınız sınıftaki bir özelliğin adı.|
  |`propinitializer`|`propertyname` = sonra gerekli. Değerlendirilen ve özellik adına atanan ifade.|
  |`initializer`|`New` belirtilmemişse isteğe bağlıdır. Değerlendirilen ve değişken oluşturulduğunda değişkene atanan ifade.|

## <a name="remarks"></a>Açıklamalar

Visual Basic derleyici, değişkenin veri türünü ve hangi kodun değişkene erişebileceği gibi diğer bilgileri belirlemek için `Dim` ifadesini kullanır. Aşağıdaki örnek bir `Integer` değerini tutacak bir değişken bildirir.

```vb
Dim numberOfStudents As Integer
```

Herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirim adı belirtebilirsiniz.

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

Bir başvuru türü için, veri türü tarafından belirtilen sınıf veya yapının yeni bir örneğini oluşturmak üzere `New` anahtar sözcüğünü kullanırsınız. `New`kullanıyorsanız, başlatıcı ifadesi kullanmayın. Bunun yerine, varsa bağımsız değişkenleri değişkeni oluşturduğunuz sınıfın oluşturucusuna sağlarsınız.

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

Bir yordam, blok, sınıf, yapı veya modülde bir değişken bildirebilirsiniz. Bir kaynak dosyasında, ad alanında veya arabirimde bir değişken bildiremezsiniz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Modül düzeyinde belirtilen bir değişken, herhangi bir yordam dışında, bir *üye değişkeni* veya *alanıdır*. Üye değişkenleri, sınıfları, yapısı veya modülleri genelinde kapsamdadır. Yordam düzeyinde belirtilen bir değişken *yerel bir değişkendir*. Yerel değişkenler yalnızca kendi yordamı veya blokları içinde kapsamdadır.

Aşağıdaki erişim değiştiricileri, değişkenleri bir yordam dışında bildirmek için kullanılır: `Public`, `Protected`, `Friend`, `Protected Friend`ve `Private`. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

`Dim` anahtar sözcüğü isteğe bağlıdır ve aşağıdaki değiştiricilerin herhangi birini belirtirseniz genellikle atlanır: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`veya `WithEvents`.

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

`Option Explicit` açık ise (varsayılan), derleyici kullandığınız her değişken için bir bildirim gerektirir. Daha fazla bilgi için bkz. [Option Explicit deyimdir](../../../visual-basic/language-reference/statements/option-explicit-statement.md).

## <a name="specifying-an-initial-value"></a>Bir başlangıç değeri belirtme

Bir değişkene, oluşturulduğunda bir değer atayabilirsiniz. Değer türü için, değişkene atanacak bir ifade sağlamak üzere bir *Başlatıcı* kullanırsınız. İfade, derleme zamanında hesaplanabilecek bir sabit olarak değerlendirilmelidir.

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

Bir başlatıcı belirtilmişse ve bir `As` yan tümcesinde veri türü belirtilmemişse, veri türünü başlatıcıdan çıkarsmak için *tür çıkarımı* kullanılır. Aşağıdaki örnekte, hem `num1` hem de `num2` kesin olarak tam sayı olarak türdedir. İkinci bildirimde, tür çıkarımı tür 3 ' ten yazın.

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

Tür çıkarımı yordam düzeyinde uygulanır. Bir sınıf, yapı, modül veya arabirimdeki bir yordamın dışında uygulanmaz. Tür çıkarımı hakkında daha fazla bilgi için bkz. [Option Infer deyimleri](../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).

Veri türü veya Başlatıcı belirtilmediğinde ne olacağı hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alarak [varsayılan veri türleri ve değerleri](../../../visual-basic/language-reference/statements/dim-statement.md#default) bölümüne bakın.

Adlandırılmış ve anonim türlerin örneklerini bildirmek için bir *nesne Başlatıcısı* kullanabilirsiniz. Aşağıdaki kod `Student` sınıfının bir örneğini oluşturur ve özellikleri başlatmak için bir nesne Başlatıcısı kullanır.

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

Nesne başlatıcıları hakkında daha fazla bilgi için bkz. [nasıl yapılır: nesne Başlatıcısı](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [nesne başlatıcıları: adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)ve [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)kullanarak nesne bildirme.

## <a name="declaring-multiple-variables"></a>Birden çok değişken bildirme

Tek bir bildirim ifadesinde, her biri için değişken adını belirterek ve her dizi adını parantez ile izleyerek birkaç değişken bildirebilirsiniz. Birden çok değişken virgülle ayrılır.

```vb
Dim lastTime, nextTime, allTimes() As Date
```

Bir `As` yan tümcesiyle birden fazla değişken bildirirseniz, bu değişken grubu için bir başlatıcı sağlayamazsınız.

Farklı değişkenler için, bildirdiğiniz her değişken için ayrı bir `As` yan tümcesi kullanarak farklı veri türleri belirtebilirsiniz. Her değişken, `variablename` bölümünün ardından karşılaşılan ilk `As` yan tümcesinde belirtilen veri türünü alır.

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a>Diziler

Birden çok değer içerebilen bir *diziyi*tutacak bir değişken bildirebilirsiniz. Bir değişkenin bir diziyi bulundurduğunu belirtmek için, parantez ile hemen `variablename` izleyin. Diziler hakkında daha fazla bilgi için bkz. [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).

Bir dizinin her boyutunun alt ve üst sınırını belirtebilirsiniz. Bunu yapmak için, parantez içine bir `boundslist` ekleyin. Her boyut için `boundslist` üst sınırı ve isteğe bağlı olarak alt sınırı belirtir. Alt sınır, sizin belirtmeksizin her zaman sıfırdır. Her dizin, üst sınır değeri ile sıfırdan farklılık gösterebilir.

Aşağıdaki iki deyim eşdeğerdir. Her bir ifade 21 `Integer` öğelerinden oluşan bir dizi bildirir. Diziye eriştiğinizde, dizin 0 ile 20 arasında farklılık gösterebilir.

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

Aşağıdaki ifade `Double`türünde iki boyutlu bir dizi bildirir. Dizide 4 satır (3 + 1) 6 sütun (5 + 1) bulunur. Üst sınır, boyutun uzunluğunu değil, dizin için mümkün olan en yüksek değeri temsil ettiğini unutmayın. Boyutun uzunluğu üst sınır artı bir değer.

```vb
Dim matrix2(3, 5) As Double
```

Bir dizi 1 ile 32 arasında boyutlara sahip olabilir.

Bir dizi bildiriminde tüm sınırların boş kalmasını sağlayabilirsiniz. Bunu yaparsanız dizi, belirttiğiniz boyut sayısına sahiptir ancak başlatılmamış olur. Öğelerinin en az bir kısmını başlatana kadar bir `Nothing` değeri vardır. `Dim` deyimin tüm boyutlar veya hiçbir boyut için sınır belirtmesi gerekir.

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

Dizide birden fazla boyut varsa, boyut sayısını göstermek için parantez arasına virgül eklemeniz gerekir.

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

Dizinin boyutlarından birini-1 olarak bildirerek *sıfır uzunluklu bir dizi* bildirebilirsiniz. Sıfır uzunluklu bir diziyi tutan bir değişken `Nothing`değerine sahip değil. Belirli ortak dil çalışma zamanı işlevleri için sıfır uzunluklu diziler gereklidir. Böyle bir diziye erişmeyi denerseniz, bir çalışma zamanı özel durumu oluşur. Daha fazla bilgi için bkz. [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).

Bir dizinin değerlerini bir dizi değişmez değeri kullanarak başlatabilirsiniz. Bunu yapmak için, başlatma değerlerini küme ayraçları (`{}`) ile çevreleyin.

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

Çok boyutlu diziler için, her ayrı boyut için başlatma, dış boyuttaki küme ayraçları içine alınır. Öğeler satır birincil sırada belirtilmiştir.

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

Dizi değişmez değerleri hakkında daha fazla bilgi için bkz. [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="default"></a>Varsayılan veri türleri ve değerleri

Aşağıdaki tabloda, bir `Dim` bildiriminde veri türünü ve başlatıcıyı belirtmenin çeşitli birleşimlerinin sonuçları açıklanmaktadır.

|Veri türü belirtildi mi?|Başlatıcı belirtildi mi?|Örnek|Sonuç|
|---|---|---|---|
|Hayır|Hayır|`Dim qty`|[Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) kapalıysa (varsayılan), değişken `Nothing`olarak ayarlanır.<br /><br /> `Option Strict` açık ise, bir derleme zamanı hatası oluşur.|
|Hayır|Evet|`Dim qty = 5`|[Seçenek çıkarımı](../../../visual-basic/language-reference/statements/option-infer-statement.md) açık ise (varsayılan), değişkeni başlatıcının veri türünü alır. Bkz. [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> `Option Infer` kapalıysa ve `Option Strict` kapalıysa, değişken `Object`veri türünü alır.<br /><br /> `Option Infer` kapalıysa ve `Option Strict` açık ise, bir derleme zamanı hatası oluşur.|
|Evet|Hayır|`Dim qty As Integer`|Değişken, veri türü için varsayılan değer olarak başlatılır. Bu bölümün ilerleyen kısımlarında tabloya bakın.|
|Evet|Evet|`Dim qty  As Integer = 5`|Başlatıcının veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.|

Bir veri türü belirtirseniz ancak Başlatıcı belirtmezseniz, Visual Basic değişkeni, veri türü için varsayılan değer olarak başlatır. Aşağıdaki tabloda varsayılan başlatma değerleri gösterilmektedir.

|Veri türü|Varsayılan değer|
|---|---|
|Tüm sayısal türler (`Byte` ve `SByte`dahil)|0|
|`Char`|İkili 0|
|Tüm başvuru türleri (`Object`, `String`ve tüm diziler dahil)|`Nothing`|
|`Boolean`|`False`|
|`Date`|1 yılın 1 Ocak 12:00 (01/01/0001 12:00:00)|

Bir yapının her öğesi ayrı bir değişken gibi başlatılır. Bir dizinin uzunluğunu bildirir ancak öğelerini başlatmayın, her öğe ayrı bir değişken gibi başlatılır.

## <a name="static-local-variable-lifetime"></a>Statik yerel değişken ömrü

`Static` yerel bir değişken, bildirildiği yordamın süresinden daha uzun bir süre içinde. Değişkenin yaşam süresinin sınırları yordamın bildirildiği yere ve `Shared`olup olmadığına bağlıdır.

|Yordam bildirimi|Değişken başlatıldı|Değişken var olanı durduruyor|
|---|---|---|
|Bir modülde|Yordamın ilk çağrılışında|Programınız yürütmeyi durduruyor|
|Bir sınıf veya yapıda, yordam `Shared`|Yordamın, belirli bir örnek veya sınıf ya da yapının kendisindeki ilk kez çağrılması|Programınız yürütmeyi durduruyor|
|Bir sınıf veya yapıda, yordam `Shared` değildir|Yordamın belirli bir örnek üzerinde ilk çağrılışında|Örnek, atık toplama (GC) için bırakıldığında|

## <a name="attributes-and-modifiers"></a>Öznitelikler ve değiştiriciler

Öznitelikleri, yerel değişkenlere değil yalnızca üye değişkenlerine uygulayabilirsiniz. Bir öznitelik, bilgileri derlemenin meta verilerine katkıda bulunur ve bu, yerel değişkenler gibi geçici depolama için anlamlı değildir.

Modül düzeyinde, üye değişkenlerini bildirmek için `Static` değiştiricisini kullanamazsınız. Yordam düzeyinde, yerel değişkenleri bildirmek için `Shared`, `Shadows`, `ReadOnly`, `WithEvents`veya herhangi bir erişim değiştiricilerini kullanamazsınız.

Bir `accessmodifier`sağlayarak hangi kodun bir değişkene erişebileceğini belirtebilirsiniz. Sınıf ve modül üye değişkenleri (herhangi bir yordam dışında), varsayılan olarak özel erişim ve yapı üye değişkenlerini genel erişime varsayılan olarak sağlar. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz. Yerel değişkenlerde erişim değiştiricilerini kullanamazsınız (bir yordam içinde).

Yalnızca üye değişkenlerinde `WithEvents`, bir yordamın içindeki yerel değişkenlerde değil, ' ı belirtebilirsiniz. `WithEvents`belirtirseniz, değişkenin veri türü, `Object`değil, belirli bir sınıf türü olmalıdır. `WithEvents`bir dizi bildiremezsiniz. Olaylar hakkında daha fazla bilgi için bkz. [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md).

> [!NOTE]
> Bir sınıf, yapı veya modülün dışındaki kodun, bir üye değişkeninin adını bu sınıf, yapı veya modülün adı ile nitelemeniz gerekir. Bir yordamın veya bloğun dışındaki kod, bu yordam veya blok içindeki herhangi bir yerel değişkene başvuramaz.

## <a name="releasing-managed-resources"></a>Yönetilen kaynakları serbest bırakma

.NET Framework atık toplayıcı, sizin bölüminizdeki ek kodlama yapmadan yönetilen kaynakları ortadan kaldırır. Ancak, atık toplayıcıyı beklemek yerine, yönetilen bir kaynağın elden çıkarılmasını zorlayabilirsiniz.

Bir sınıf özellikle değerli ve nadir kaynağına (veritabanı bağlantısı veya dosya tanıtıcısı gibi) sahip olursa, artık kullanımda olmayan bir sınıf örneğini temizleyebilmek için sonraki atık toplamaya kadar beklemek istemeyebilirsiniz. Bir sınıf, bir atık toplama işleminden önce kaynakları serbest bırakmak için <xref:System.IDisposable> arabirimini uygulayabilir. Bu arabirimi uygulayan bir sınıf, değerli kaynakların hemen yayınlanmasını zorlamak için çağrılabilecek bir `Dispose` yöntemi sunar.

`Using` deyimi, kaynak alma, bir deyim kümesi yürütme ve sonra kaynağı atma sürecini otomatikleştirir. Ancak, kaynağın <xref:System.IDisposable> arabirimini uygulaması gerekir. Daha fazla bilgi için bkz. [using deyimleri](../../../visual-basic/language-reference/statements/using-statement.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, çeşitli seçeneklerle `Dim` ifadesini kullanarak değişkenleri bildirir.

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte 1 ile 30 arasında asal sayılar listelenmektedir. Yerel değişkenlerin kapsamı kod açıklamalarında açıklanmıştır.

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte `speedValue` değişkeni sınıf düzeyinde bildirilmiştir. `Private` anahtar sözcüğü değişkeni bildirmek için kullanılır. Değişkenine `Car` sınıfındaki herhangi bir yordam tarafından erişilebilir.

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a>Ayrıca bkz.

- [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)
- [ReDim Deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Option Explicit Deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Infer Deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Değişken Bildirimi](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Nasıl yapılır: Nesne Başlatıcısı Kullanarak Nesne Bildirme](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
