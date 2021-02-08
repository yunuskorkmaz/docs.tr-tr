---
description: 'Daha fazla bilgi edinin: Dim deyimleri (Visual Basic)'
title: Dim ekstresi
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
ms.openlocfilehash: b950ae95af01be4e064ac9177300f144e0cc08b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795202"
---
# <a name="dim-statement-visual-basic"></a>Dim ekstresi (Visual Basic)

Bir veya daha fazla değişken için depolama alanı bildirir ve ayırır.

## <a name="syntax"></a>Syntax

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a>Bölümler

- `attributelist`

  İsteğe bağlı. Bkz. [öznitelik listesi](attribute-list.md).

- `accessmodifier`

  İsteğe bağlı. Aşağıdakilerden biri olabilir:

  - [Genel](../modifiers/public.md)

  - [Korunamadı](../modifiers/protected.md)

  - [Arkadaş](../modifiers/friend.md)

  - [Özel](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Özel korumalı](../modifiers/private-protected.md)

  [Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.

- `Shared`

  İsteğe bağlı. Bkz. [paylaşılan](../modifiers/shared.md).

- `Shadows`

  İsteğe bağlı. Bkz. [gölgeler](../modifiers/shadows.md).

- `Static`

  İsteğe bağlı. Bkz. [statik](../modifiers/static.md).

- `ReadOnly`

  İsteğe bağlı. Bkz. [ReadOnly](../modifiers/readonly.md).

- `WithEvents`

  İsteğe bağlı. Bunların, olayları yükseltebileceği bir sınıfın örneklerine başvuran nesne değişkenleri olduğunu belirtir. Bkz. [WithEvents](../modifiers/withevents.md).

- `variablelist`

  Gereklidir. Bu bildirimde bildirildiği değişkenlerin listesi.

  `variable [ , variable ... ]`

  Her birinin `variable` aşağıdaki söz dizimi ve parçaları vardır:

  `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`

  |Bölüm|Description|
  |---|---|
  |`variablename`|Gereklidir. Değişkenin adı. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
  |`boundslist`|İsteğe bağlı. Bir dizi değişkeninin her boyutunun sınırları listesi.|
  |`New`|İsteğe bağlı. Deyimin çalıştırıldığı zaman sınıfının yeni bir örneğini oluşturur `Dim` .|
  |`datatype`|İsteğe bağlı. Değişkenin veri türü.|
  |`With`|İsteğe bağlı. Nesne Başlatıcısı listesini tanıtır.|
  |`propertyname`|İsteğe bağlı. Örneği yaptığınız sınıftaki bir özelliğin adı.|
  |`propinitializer`|Şu tarihten sonra gereklidir `propertyname` =. Değerlendirilen ve özellik adına atanan ifade.|
  |`initializer`|`New`Belirtilmemişse, isteğe bağlıdır. Değerlendirilen ve değişken oluşturulduğunda değişkene atanan ifade.|

## <a name="remarks"></a>Açıklamalar

Visual Basic derleyici, değişkenin `Dim` veri türünü ve değişkene hangi kodun erişebileceği gibi diğer bilgileri belirlemek için ifadesini kullanır. Aşağıdaki örnek, bir değeri tutacak bir değişken bildirir `Integer` .

```vb
Dim numberOfStudents As Integer
```

Herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirim adı belirtebilirsiniz.

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

Bir başvuru türü için, `New` veri türü tarafından belirtilen sınıf veya yapının yeni bir örneğini oluşturmak için anahtar sözcüğünü kullanırsınız. Kullanırsanız `New` , bir başlatıcı ifadesi kullanmayın. Bunun yerine, varsa bağımsız değişkenleri değişkeni oluşturduğunuz sınıfın oluşturucusuna sağlarsınız.

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

Bir yordam, blok, sınıf, yapı veya modülde bir değişken bildirebilirsiniz. Bir kaynak dosyasında, ad alanında veya arabirimde bir değişken bildiremezsiniz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).

Modül düzeyinde belirtilen bir değişken, herhangi bir yordam dışında, bir *üye değişkeni* veya *alanıdır*. Üye değişkenleri, sınıfları, yapısı veya modülleri genelinde kapsamdadır. Yordam düzeyinde belirtilen bir değişken *yerel bir değişkendir*. Yerel değişkenler yalnızca kendi yordamı veya blokları içinde kapsamdadır.

Aşağıdaki erişim değiştiricileri, değişkenleri bir yordam dışında bildirmek için kullanılır: `Public` , `Protected` ,, `Friend` `Protected Friend` ve `Private` . Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).

`Dim`Anahtar sözcüğü isteğe bağlıdır ve aşağıdaki değiştiricilerin herhangi birini belirtirseniz genellikle atlanır: `Public` ,,, `Protected` `Friend` `Protected Friend` , `Private` , `Shared` , `Shadows` , `Static` , `ReadOnly` veya `WithEvents` .

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

`Option Explicit`Açık ise (varsayılan), derleyici kullandığınız her değişken için bir bildirim gerektirir. Daha fazla bilgi için bkz. [Option Explicit deyimdir](option-explicit-statement.md).

## <a name="specifying-an-initial-value"></a>Bir başlangıç değeri belirtme

Bir değişkene, oluşturulduğunda bir değer atayabilirsiniz. Değer türü için, değişkene atanacak bir ifade sağlamak üzere bir *Başlatıcı* kullanırsınız. İfade, derleme zamanında hesaplanabilecek bir sabit olarak değerlendirilmelidir.

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

Bir başlatıcı belirtilmişse ve bir yan tümcesinde veri türü belirtilmemişse `As` , veri türünü başlatıcıdan çıkarsmak için *tür çıkarımı* kullanılır. Aşağıdaki örnekte, her ikisi de `num1` `num2` kesin olarak tam sayı olarak türdedir. İkinci bildirimde, tür çıkarımı tür 3 ' ten yazın.

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

Tür çıkarımı yordam düzeyinde uygulanır. Bir sınıf, yapı, modül veya arabirimdeki bir yordamın dışında uygulanmaz. Tür çıkarımı hakkında daha fazla bilgi için bkz. [Option Infer deyimleri](option-infer-statement.md) ve [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md).

Veri türü veya Başlatıcı belirtilmediğinde ne olacağı hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alarak [varsayılan veri türleri ve değerleri](dim-statement.md#default) bölümüne bakın.

Adlandırılmış ve anonim türlerin örneklerini bildirmek için bir *nesne Başlatıcısı* kullanabilirsiniz. Aşağıdaki kod, sınıfının bir örneğini oluşturur `Student` ve özellikleri başlatmak için bir nesne Başlatıcısı kullanır.

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

Nesne başlatıcıları hakkında daha fazla bilgi için bkz. [nasıl yapılır: nesne Başlatıcısı](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [nesne başlatıcıları: adlandırılmış ve anonim türler](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)ve [anonim türler](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)kullanarak nesne bildirme.

## <a name="declaring-multiple-variables"></a>Birden çok değişken bildirme

Tek bir bildirim ifadesinde, her biri için değişken adını belirterek ve her dizi adını parantez ile izleyerek birkaç değişken bildirebilirsiniz. Birden çok değişken virgülle ayrılır.

```vb
Dim lastTime, nextTime, allTimes() As Date
```

Tek bir yan tümcesiyle birden fazla değişken bildirirseniz `As` , bu değişken grubu için bir başlatıcı sağlayamazsınız.

Farklı değişkenler için, `As` bildirdiğiniz her değişken için ayrı bir yan tümce kullanarak farklı veri türleri belirtebilirsiniz. Her değişken, `As` bölümünün sonunda karşılaşılan ilk yan tümcesinde belirtilen veri türünü alır `variablename` .

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a>Diziler

Birden çok değer içerebilen bir *diziyi* tutacak bir değişken bildirebilirsiniz. Bir değişkenin bir diziyi bulundurduğunu belirtmek için, `variablename` parantez ile hemen izleyin. Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/language-features/arrays/index.md).

Bir dizinin her boyutunun alt ve üst sınırını belirtebilirsiniz. Bunu yapmak için `boundslist` ayraçları içine ekleyin. Her boyut için, `boundslist` üst sınırı ve isteğe bağlı olarak alt sınırı belirtir. Alt sınır, sizin belirtmeksizin her zaman sıfırdır. Her dizin, üst sınır değeri ile sıfırdan farklılık gösterebilir.

Aşağıdaki iki deyim eşdeğerdir. Her ifade bir 21 öğe dizisi bildirir `Integer` . Diziye eriştiğinizde, dizin 0 ile 20 arasında farklılık gösterebilir.

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

Aşağıdaki ifade, türünde iki boyutlu bir dizi bildirir `Double` . Dizide 4 satır (3 + 1) 6 sütun (5 + 1) bulunur. Üst sınır, boyutun uzunluğunu değil, dizin için mümkün olan en yüksek değeri temsil ettiğini unutmayın. Boyutun uzunluğu üst sınır artı bir değer.

```vb
Dim matrix2(3, 5) As Double
```

Bir dizi 1 ile 32 arasında boyutlara sahip olabilir.

Bir dizi bildiriminde tüm sınırların boş kalmasını sağlayabilirsiniz. Bunu yaparsanız dizi, belirttiğiniz boyut sayısına sahiptir ancak başlatılmamış olur. `Nothing`Öğelerinin en az bir kısmını başlatana kadar bir değeri vardır. `Dim`Deyimin tüm boyutlar veya boyut yok için sınır belirtmesi gerekir.

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

Dizinin boyutlarından birini-1 olarak bildirerek *sıfır uzunluklu bir dizi* bildirebilirsiniz. Sıfır uzunluklu bir diziyi tutan bir değişken değeri yok `Nothing` . Belirli ortak dil çalışma zamanı işlevleri için sıfır uzunluklu diziler gereklidir. Böyle bir diziye erişmeyi denerseniz, bir çalışma zamanı özel durumu oluşur. Daha fazla bilgi için bkz. [diziler](../../programming-guide/language-features/arrays/index.md).

Bir dizinin değerlerini bir dizi değişmez değeri kullanarak başlatabilirsiniz. Bunu yapmak için başlatma değerlerini küme ayraçları () ile çevreleyin `{}` .

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

Çok boyutlu diziler için, her ayrı boyut için başlatma, dış boyuttaki küme ayraçları içine alınır. Öğeler satır birincil sırada belirtilmiştir.

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

Dizi değişmez değerleri hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/language-features/arrays/index.md).

## <a name="default-data-types-and-values"></a><a name="default"></a> Varsayılan veri türleri ve değerleri

Aşağıdaki tabloda, bir deyimindeki veri türünü ve başlatıcıyı belirtmenin çeşitli birleşimlerinin sonuçları açıklanmaktadır `Dim` .

|Veri türü belirtildi mi?|Başlatıcı belirtildi mi?|Örnek|Sonuç|
|---|---|---|---|
|Hayır|Hayır|`Dim qty`|[Option Strict](option-strict-statement.md) kapalıysa (varsayılan), değişkeni olarak ayarlanır `Nothing` .<br /><br /> `Option Strict`Açık ise, bir derleme zamanı hatası oluşur.|
|Hayır|Yes|`Dim qty = 5`|[Seçenek çıkarımı](option-infer-statement.md) açık ise (varsayılan), değişkeni başlatıcının veri türünü alır. Bkz. [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md).<br /><br /> `Option Infer`Kapalıysa ve `Option Strict` kapalıysa, değişken veri türünü alır `Object` .<br /><br /> `Option Infer`Kapalıysa ve açık ise `Option Strict` , bir derleme zamanı hatası oluşur.|
|Yes|Hayır|`Dim qty As Integer`|Değişken, veri türü için varsayılan değer olarak başlatılır. Bu bölümün ilerleyen kısımlarında tabloya bakın.|
|Yes|Yes|`Dim qty  As Integer = 5`|Başlatıcının veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.|

Bir veri türü belirtirseniz ancak Başlatıcı belirtmezseniz, Visual Basic değişkeni, veri türü için varsayılan değer olarak başlatır. Aşağıdaki tabloda varsayılan başlatma değerleri gösterilmektedir.

|Veri türü|Varsayılan değer|
|---|---|
|Tüm sayısal türler ( `Byte` ve dahil `SByte` )|0|
|`Char`|İkili 0|
|Tüm başvuru türleri ( `Object` , `String` ve tüm diziler dahil)|`Nothing`|
|`Boolean`|`False`|
|`Date`|1 yılın 1 Ocak 12:00 (01/01/0001 12:00:00)|

Bir yapının her öğesi ayrı bir değişken gibi başlatılır. Bir dizinin uzunluğunu bildirir ancak öğelerini başlatmayın, her öğe ayrı bir değişken gibi başlatılır.

## <a name="static-local-variable-lifetime"></a>Statik yerel değişken ömrü

`Static`Yerel bir değişken, bildirildiği yordamın süresinden daha uzun bir yaşam süresine sahiptir. Değişkenin yaşam süresinin sınırları yordamın bildirildiği yere ve olup olmadığına bağlıdır `Shared` .

|Yordam bildirimi|Değişken başlatıldı|Değişken var olanı durduruyor|
|---|---|---|
|Bir modülde|Yordamın ilk çağrılışında|Programınız yürütmeyi durduruyor|
|Bir sınıf veya yapıda, yordam `Shared`|Yordamın, belirli bir örnek veya sınıf ya da yapının kendisindeki ilk kez çağrılması|Programınız yürütmeyi durduruyor|
|Bir sınıf veya yapıda, yordam `Shared`|Yordamın belirli bir örnek üzerinde ilk çağrılışında|Örnek, atık toplama (GC) için bırakıldığında|

## <a name="attributes-and-modifiers"></a>Öznitelikler ve değiştiriciler

Öznitelikleri, yerel değişkenlere değil yalnızca üye değişkenlerine uygulayabilirsiniz. Bir öznitelik, bilgileri derlemenin meta verilerine katkıda bulunur ve bu, yerel değişkenler gibi geçici depolama için anlamlı değildir.

Modül düzeyinde, `Static` üye değişkenlerini bildirmek için değiştiricisini kullanamazsınız. Yordam düzeyinde,,,, `Shared` `Shadows` `ReadOnly` `WithEvents` veya herhangi bir erişim değiştiricilerini yerel değişkenleri bildirmek için kullanamazsınız.

Bir değişkene hangi kodun erişebileceğini belirtebilirsiniz `accessmodifier` . Sınıf ve modül üye değişkenleri (herhangi bir yordam dışında), varsayılan olarak özel erişim ve yapı üye değişkenlerini genel erişime varsayılan olarak sağlar. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz. Yerel değişkenlerde erişim değiştiricilerini kullanamazsınız (bir yordam içinde).

`WithEvents`Bir yordamın içindeki yerel değişkenlerde değil, yalnızca üye değişkenlerinde belirtebilirsiniz. Belirtirseniz `WithEvents` , değişkenin veri türü, değil, belirli bir sınıf türü olmalıdır `Object` . İle bir dizi bildiremezsiniz `WithEvents` . Olaylar hakkında daha fazla bilgi için bkz. [Olaylar](../../programming-guide/language-features/events/index.md).

> [!NOTE]
> Bir sınıf, yapı veya modülün dışındaki kodun, bir üye değişkeninin adını bu sınıf, yapı veya modülün adı ile nitelemeniz gerekir. Bir yordamın veya bloğun dışındaki kod, bu yordam veya blok içindeki herhangi bir yerel değişkene başvuramaz.

## <a name="releasing-managed-resources"></a>Yönetilen kaynakları serbest bırakma

.NET Framework atık toplayıcı, sizin bölüminizdeki ek kodlama yapmadan yönetilen kaynakları ortadan kaldırır. Ancak, atık toplayıcıyı beklemek yerine, yönetilen bir kaynağın elden çıkarılmasını zorlayabilirsiniz.

Bir sınıf özellikle değerli ve nadir kaynağına (veritabanı bağlantısı veya dosya tanıtıcısı gibi) sahip olursa, artık kullanımda olmayan bir sınıf örneğini temizleyebilmek için sonraki atık toplamaya kadar beklemek istemeyebilirsiniz. Bir sınıf, bir <xref:System.IDisposable> atık toplama işleminden önce kaynakları serbest bırakmak için arabirimi uygulayabilir. Bu arabirimi uygulayan bir sınıf, `Dispose` değerli kaynakların hemen yayınlanmasını zorlamak için çağrılabilecek bir yöntemi ortaya koyar.

`Using`Deyimi bir kaynağı alma, bir deyim kümesi yürütme ve sonra kaynağı atma sürecini otomatikleştirir. Ancak, kaynağın arabirimini uygulaması gerekir <xref:System.IDisposable> . Daha fazla bilgi için bkz. [using deyimleri](using-statement.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Dim` çeşitli seçeneklerle deyimleri kullanarak değişkenleri bildirir.

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte 1 ile 30 arasında asal sayılar listelenmektedir. Yerel değişkenlerin kapsamı kod açıklamalarında açıklanmıştır.

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `speedValue` değişkeni sınıf düzeyinde bildirilmiştir. `Private`Anahtar sözcüğü değişkeni bildirmek için kullanılır. Değişkenine, sınıftaki herhangi bir yordam tarafından erişilebilir `Car` .

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a>Ayrıca bkz.

- [Const Deyimi](const-statement.md)
- [ReDim Deyimi](redim-statement.md)
- [Option Explicit Deyimi](option-explicit-statement.md)
- [Option Infer Deyimi](option-infer-statement.md)
- [Option Strict Deyimi](option-strict-statement.md)
- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Değişken Bildirimi](../../programming-guide/language-features/variables/variable-declaration.md)
- [Diziler](../../programming-guide/language-features/arrays/index.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonim Türler](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Nasıl yapılır: Nesne Başlatıcı Kullanarak Nesne Bildirme](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [Yerel Tür Arabirimi](../../programming-guide/language-features/variables/local-type-inference.md)
