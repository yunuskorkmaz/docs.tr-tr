---
title: Dim Deyimi (Visual Basic)
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
ms.openlocfilehash: cab1cc07d23a44e57bdb0962a323b014308cb1e5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836564"
---
# <a name="dim-statement-visual-basic"></a>Dim Deyimi (Visual Basic)
Bildirir ve değişkenleri bir veya daha fazla depolama alanı ayırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a>Bölümler  
  
-   `attributelist`  
  
     İsteğe bağlı. Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
-   `accessmodifier`  
  
     İsteğe bağlı. Aşağıdakilerden biri olabilir:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [Protected Friend](../../language-reference/modifiers/protected-friend.md)
    
    - [Private Protected](../../language-reference/modifiers/private-protected.md)

     Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `Shared`  
  
     İsteğe bağlı. Bkz: [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     İsteğe bağlı. Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Static`  
  
     İsteğe bağlı. Bkz: [statik](../../../visual-basic/language-reference/modifiers/static.md).  
  
-   `ReadOnly`  
  
     İsteğe bağlı. Bkz: [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
-   `WithEvents`  
  
     İsteğe bağlı. Bunlar, olayları tetikleyebilen bir sınıf örneklerine bakın nesne değişkenleri belirtir. Bkz: [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).  
  
-   `variablelist`  
  
     Gerekli. Bu deyiminde bildirilen değişkenlerin listesi.  
  
     `variable [ , variable ... ]`  
  
     Her `variable` aşağıdaki söz dizimini ve bölümleri vardır:  
  
     `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`  
  
    |Bölümü|Açıklama|  
    |---|---|  
    |`variablename`|Gerekli. Değişkenin adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
    |`boundslist`|İsteğe bağlı. Her boyut bir dizi değişkeni sınırlarının listesi.|  
    |`New`|İsteğe bağlı. Sınıfının yeni bir örneğini oluşturur, `Dim` deyimi çalıştırır.|  
    |`datatype`|İsteğe bağlı. Değişken veri türü.|  
    |`With`|İsteğe bağlı. Nesne başlatıcı listesi tanıtır.|  
    |`propertyname`|İsteğe bağlı. Bir sınıf özelliği adı örneği hale getiriyoruz.|  
    |`propinitializer`|Sonra gerekli `propertyname` =. Değerlendirilir ve özellik adına atanan ifade.|  
    |`initializer`|İsteğe bağlı ise `New` belirtilmedi. Değerlendirilir ve oluşturulduğu sırada değişkene atanan ifade.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Basic Derleyicisi kullanan `Dim` değişkenin veri türü ve hangi kod değişkenine erişebileceği gibi diğer bilgileri belirlemek için deyimi. Aşağıdaki örnek, tutacak bir değişken bildirir. bir `Integer` değeri.  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 Herhangi bir veri türü veya bir sabit listesi, yapısı, sınıf veya arabirim adını belirtebilirsiniz.  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 Bir başvuru türü için kullandığınız `New` sınıfının yeni bir örneğini oluşturmak veya bu yapı için anahtar sözcüğü veri türü tarafından belirtilir. Kullanırsanız `New`, bir başlatıcı ifadesinin kullanmayın. Bunun yerine, değişken oluşturmakta olduğunuz sınıf oluşturucusuna gerekli iseler bağımsız değişken sağlayın.  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 Yordamı, blok, sınıf, yapı veya modül bir değişkende bildirebilirsiniz. İçinde bir değişken bir kaynak dosyası, ad alanı veya arabirimi bildiremezsiniz. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Dışında herhangi bir yordam Modül düzeyinde bildirilmiş bir değişken bir *üye değişkeni* veya *alan*. Üye değişkenleri kendi sınıf, yapı veya modül boyunca kapsamına dahildir. Yordam düzeyinde bildirilen bir değişken bir *yerel değişken*. Yerel değişkenler yalnızca kendi yordam veya blok içinde kapsamına dahildir.  
  
 Aşağıdaki erişim değiştiriciler yordam dışında değişkenler bildirmek için kullanılır: `Public`, `Protected`, `Friend`, `Protected Friend`, ve `Private`. Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Dim` Anahtar sözcüğü, isteğe bağlıdır ve aşağıdaki değiştiriciler belirtirseniz, genellikle atlanmış: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, veya `WithEvents`.  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 Varsa `Option Explicit` olduğunu (varsayılan), derleyici bir bildirimi kullandığınız her değişken için gerektirir. Daha fazla bilgi için [Option Explicit deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md).  
  
## <a name="specifying-an-initial-value"></a>Bir başlangıç değeri belirtme  
 Oluşturulduğunda bir değişkene bir değer atayabilirsiniz. Bir değer türü için kullandığınız bir *Başlatıcı* değişkene atanmış bir ifade sağlamanız için. Derleme zamanında hesaplanabilen bir sabit ifade değerlendirilmelidir.  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 Bir başlatıcı belirtilirse ve bir veri türü belirtilmedi bir `As` yan tümcesi *anlam çıkarma* veri türü başlatıcıdan çıkarmak için kullanılır. Aşağıdaki örnekte, her ikisi de `num1` ve `num2` tamsayı olarak kesin olarak belirlenmiştir. İkinci bildiriminde tür çıkarımını 3 değeri türünden çıkarır.  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 Tür çıkarımı yordam düzeyinde uygulanır. Bir yordamda bir sınıf, yapı, modül veya arabirimi dışından uygulanmaz. Tür çıkarımı hakkında daha fazla bilgi için bkz: [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Bir veri türü veya Başlatıcı belirtilmediğinde neler olduğu hakkında daha fazla bilgi için bkz: [varsayılan veri türleri ve değerleri](../../../visual-basic/language-reference/statements/dim-statement.md#default) bu konuda.  
  
 Kullanabileceğiniz bir *nesne Başlatıcı* adlandırılmış ve anonim türlerin örneklerini bildirmek için. Aşağıdaki kod örneği oluşturur. bir `Student` sınıfı ve özellikleri başlatmak için bir nesne Başlatıcı kullanır.  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 Nesne başlatıcıları hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir nesne Başlatıcı kullanarak nesne bildirme](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), ve [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="declaring-multiple-variables"></a>Birden fazla değişken bildirme  
 Parantezler ile her biri için ve her dizi adı aşağıdaki değişken adını belirten bir bildirim deyiminde, çeşitli değişkenleri bildirebilirsiniz. Birden fazla değişken virgülle ayrılır.  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 Bir sahip birden fazla değişken bildirirseniz `As` yan tümcesi, o grubu değişkenlerin bir başlatıcı sağlayamıyor.  
  
 Ayrı bir kullanarak farklı veri türleri için farklı değişkenleri belirtebilirsiniz `As` bildirdiğiniz her bir değişken yan tümcesi. Her bir değişken ilk belirtilen veri türü alan `As` yan tümcesi karşılaştı sonra kendi `variablename` bölümü.  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a>Diziler  
 Tutacak bir değişken bildirmek bir *dizi*, birden çok değer tutabilir. Bir değişken bir dizi tutan belirtmek için izleyin, `variablename` parantez olmadan hemen. Diziler hakkında daha fazla bilgi için bkz. [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Alt ve bir dizinin her boyutunun üst sınırını belirtebilirsiniz. Bunu yapmak için dahil bir `boundslist` parantez içinde. Her boyut için `boundslist` üst sınırı ve isteğe bağlı alt sınırını belirtir. Olup olmadığını belirtin alt sınırı her zaman sıfırdır. Her dizin aracılığıyla üst sınır değeri sıfırdan farklılık gösterebilir.  
  
 Aşağıdaki iki deyimi eşdeğerdir. Her deyim 21 dizisi bildirir `Integer` öğeleri. Dizi eriştiğinizde, dizin 0 ile 20 arasında değişebilir.  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 Aşağıdaki deyim türünde iki boyutlu bir dizi bildirir `Double`. Dizi 6 sütunlar (5 + 1) her biri 4 satır (3 + 1) sahiptir. Bir üst sınır boyutun uzunluğu dizini için olası en yüksek değere temsil ettiğini unutmayın. Boyutun uzunluğu üst sınırı artı bir taneyi ' dir.  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 Bir dizi 1 ila 32 boyutlara sahip olabilir.  
  
 Tüm sınırların bir dizi bildirimi boş bırakabilirsiniz. Bunu yaparsanız, belirttiğiniz boyutların sayısı dizi sahiptir, ancak başlatılmamış. Değerine sahip `Nothing` en az başlatmak kadar bazı alt öğeleri. `Dim` Deyimi tüm boyutlar veya hiç boyut sınırları belirtin.  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 Dizi boyut birden fazla varsa, virgül boyut sayısını göstermek için parantez içermelidir.  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 Bildirebilirsiniz bir *sıfır uzunluklu dizi* göre -1 olarak dizi boyutlarından birini bildirme. Sıfır uzunluğunda diziyi tutan değişken değeri yok `Nothing`. Sıfır uzunlukta diziler bazı ortak dil çalışma zamanı işlevleri tarafından gereklidir. Böyle bir dizi erişmeye çalışırsanız bir çalışma zamanı özel durumu oluşur. Daha fazla bilgi için [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Dizi değişmez değeri kullanarak dizi değerlerini başlatabilirsiniz. Bunu yapmak için Küme ayraçları başlatma değerlerle çevreleyen (`{}`).  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 Çok boyutlu diziler için başlatma ayrı her boyut için dış boyutundaki köşeli ayraçlar içine alınır. Öğeler satır ağırlıklı sırada belirtilir.  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 Dizi değişmez değerleri hakkında daha fazla bilgi için bkz: [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="default"></a> Varsayılan veri türleri ve değerleri  
 Aşağıdaki tabloda çeşitli birleşimlerini başlatıcısında ve veri türünü belirtmenin sonuçlarını açıklar bir `Dim` deyimi.  
  
|Belirtilen veri türü?|Belirtilen başlatıcı?|Örnek|Sonuç|  
|---|---|---|---|  
|Hayır|Hayır|`Dim qty`|Varsa [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) olan kapalı (varsayılan), değişkeni ayarlanır `Nothing`.<br /><br /> Varsa `Option Strict` açıktır, bir derleme zamanı hatası oluşur.|  
|Hayır|Evet|`Dim qty = 5`|Varsa [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) değişken alır veri öğesinin başlatıcısını yazın (varsayılan), olan. Bkz: [yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Varsa `Option Infer` kapalıdır ve `Option Strict` kapalıysa, değişken veri türünü alan `Object`.<br /><br /> Varsa `Option Infer` kapalıdır ve `Option Strict` açıktır, bir derleme zamanı hatası oluşur.|  
|Evet|Hayır|`Dim qty As Integer`|Değişken veri türü için varsayılan değer için başlatılır. Bu bölümdeki tabloya bakın.|  
|Evet|Evet|`Dim qty  As Integer = 5`|Başlatıcı veri türü belirtilen veri türüne dönüştürülebilir değil, bir derleme zamanı hatası oluşur.|  
  
 Bir veri türü belirtin, ancak bir başlatıcı belirtmezseniz, Visual Basic veri türü için varsayılan değer değişkenine başlatır. Aşağıdaki tabloda, varsayılan başlatma değerleri gösterir.  
  
|Veri türü|Varsayılan değer|  
|---|---|  
|Tüm sayısal türlerin (dahil olmak üzere `Byte` ve `SByte`)|0|  
|`Char`|İkili 0|  
|Tüm başvuru türleri (dahil olmak üzere `Object`, `String`ve tüm Diziler)|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|12: 00'da, 1 yılının 1 Ocak (01/01/0001 12:00:00 AM)|  
  
 Bir yapının her öğe ayrı bir değişken gibi başlatılır. Bir dizinin uzunluğu bildirmek, ancak öğeleri başlatmayın, her öğe ayrı bir değişken gibi başlatılır.  
  
## <a name="static-local-variable-lifetime"></a>Statik yerel değişken ömrü  
 A `Static` yerel değişken bu bildirilen yordamın daha uzun bir ömrü vardır. Değişkenin ömrü sınırları yordamı burada bildirilir ve olmasına bağlıdır `Shared`.  
  
|Yordam bildirimi|Değişken başlatılmamış|Değişkeni mevcut durdurur.|  
|---|---|---|  
|Bir modülde|İlk kez yordamı çağrılır|Programınızı yürütme durduğunda|  
|Bir sınıf veya yapı yordamdır `Shared`|İlk kez yordamı belirli bir örneğine veya sınıf veya yapının kendisi üzerinde çağrılır|Programınızı yürütme durduğunda|  
|Bir sınıf veya yapı yordamı değil `Shared`|İlk kez yordamı belirli bir örneği üzerinde çağrılır|Çöp toplama (GC) örneği yayınlandığında|  
  
## <a name="attributes-and-modifiers"></a>Öznitelikler ve değiştiriciler  
 Öznitelikleri yalnızca değişkenlere, yerel değişkenler için uygulayabilirsiniz. Bir öznitelik bilgileri derlemenin meta verilerini, geçici depolama gibi yerel değişkenleri için anlamlı değil katkıda bulunur.  
  
 Modül düzeyinde kullanamazsınız `Static` değiştiricisi üye değişkenleri bildirmek için. Yordam düzeyinde kullanamazsınız `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, ya da herhangi bir erişim değiştiricilerine yerel değişkenler bildirmek için.  
  
 Hangi kod sağlayarak bir değişkenine erişebileceği belirtebileceğiniz bir `accessmodifier`. Özel erişim için üye değişkenleri (dışında herhangi bir yordam) varsayılan sınıf ve modül ve yapı üyesi değişkenleri varsayılan genel erişim için. Erişim değiştiricileri ile kullanıcıların erişim düzeylerini ayarlayabilirsiniz. Erişim değiştiricileri (içinde bir yordam) yerel değişkenler kullanamazsınız.  
  
 Belirtebileceğiniz `WithEvents` yalnızca değişkenlere, yordam içindeki yerel değişkenlere göre değil. Belirtirseniz `WithEvents`, değişkenin veri türü, belirli bir sınıf türü olmamalıdır `Object`. Bir dizi bildiremezsiniz `WithEvents`. Olaylar hakkında daha fazla bilgi için bkz. [olayları](../../../visual-basic/programming-guide/language-features/events/index.md).  
  
> [!NOTE]
>  Kod bir sınıf dışında yapısını veya modülünü bir üye değişkeninin adı bu sınıf, yapı veya modül adıyla nitelemeniz gerekir. Bir yordam veya blok Bu yordam veya blok içinde herhangi bir yerel değişkenlere başvuruda bulunamaz dışındaki kod.  
  
## <a name="releasing-managed-resources"></a>Yönetilen kaynakları serbest bırakma  
 Ek kodlamaya bulunmanıza gerek kalmadan, .NET Framework atık toplayıcı yönetilen kaynakları siler. Bununla birlikte, çöp toplayıcının beklemek yerine bir yönetilen kaynak elden zorlayabilirsiniz.  
  
 Bir sınıf, özellikle değerli ve nadir bir kaynak (örneğin, bir veritabanı bağlantısı veya dosya tanıtıcısı) üzerine tutuyorsa artık kullanımda olmayan bir sınıf örneğini temizlemek için bir sonraki atık koleksiyonuna kadar beklemek istemeyebilirsiniz. Bir sınıf uygulayabilir <xref:System.IDisposable> çöp toplama önce kaynakları serbest bırakmak için bir yol sağlamak üzere arabirimi. Arabirimi uygulayan bir sınıfı gösterir bir `Dispose` değerli kaynakları hemen serbest bırakılması zorlamak için çağrılabilen bir yöntem.  
  
 `Using` Deyimi bir kaynağı alma, bir dizi deyimleri yürütme ve ardından kaynak disposing işlemini otomatikleştirir. Ancak, kaynak uygulamalıdır <xref:System.IDisposable> arabirimi. Daha fazla bilgi için [Using deyimi](../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneği kullanarak değişkenler bildirilmektedir `Dim` çeşitli seçeneklerle deyimi.  
  
 [!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 1 ile 30 arasında asal sayıları listeler. Yerel değişkenler kapsamını, kod açıklamaları açıklanmıştır.  
  
 [!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `speedValue` sınıf düzeyinde bildirilen değişkenin. `Private` Anahtar sözcüğü bir değişken bildirmek için kullanılır. Değişken, herhangi bir yordam tarafından erişilebilen `Car` sınıfı.  
  
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
- [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Nasıl yapılır: Bir nesne Başlatıcı kullanarak nesne bildirme](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
