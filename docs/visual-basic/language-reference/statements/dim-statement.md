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
ms.openlocfilehash: b3384b771748a1f2c9e841407042f81ce6ebe76d
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234733"
---
# <a name="dim-statement-visual-basic"></a>Dim Deyimi (Visual Basic)
Bildirir ve depolama alanı için bir veya daha fazla değişken ayırır.  
  
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
  
    -   [Korumalı Friend](../../language-reference/modifiers/protected-friend.md)
    
    - [Özel korumalı](../../language-reference/modifiers/private-protected.md)

     Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `Shared`  
  
     İsteğe bağlı. Bkz: [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     İsteğe bağlı. Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Static`  
  
     İsteğe bağlı. Bkz: [statik](../../../visual-basic/language-reference/modifiers/static.md).  
  
-   `ReadOnly`  
  
     İsteğe bağlı. Bkz: [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
-   `WithEvents`  
  
     İsteğe bağlı. Bu olaylar oluşturabilir bir sınıfın örneklerine bakın nesne değişkenleri olduğunu belirtir. Bkz: [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).  
  
-   `variablelist`  
  
     Gerekli. Bu deyim içinde bildirilen değişkenleri listesi.  
  
     `variable [ , variable ... ]`  
  
     Her `variable` aşağıdaki söz dizimini ve bölümleri vardır:  
  
     `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`  
  
    |Bölümü|Açıklama|  
    |---|---|  
    |`variablename`|Gerekli. Değişkenin adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
    |`boundslist`|İsteğe bağlı. Bir dizi değişken her boyut sınırları listesi.|  
    |`New`|İsteğe bağlı. Sınıfının yeni bir örneğini oluşturur, `Dim` deyimini çalıştırır.|  
    |`datatype`|İsteğe bağlı. Değişken veri türü.|  
    |`With`|İsteğe bağlı. Nesne başlatıcı listesi sunar.|  
    |`propertyname`|İsteğe bağlı. Bir özelliğin adını örneği getirirsiniz.|  
    |`propinitializer`|Sonra gerekli `propertyname` =. Değerlendirilir ve özellik adına atanmış ifade.|  
    |`initializer`|İsteğe bağlı ise `New` belirtilmedi. Değerlendirilir ve oluşturulduğunda değişkenine atanan ifade.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Basic derleyici kullanan `Dim` değişkenin veri türü ve hangi kod değişkenine erişebileceği gibi diğer bilgileri belirlemek için deyimi. Aşağıdaki örnek tutmak için bir değişken bildiren bir `Integer` değeri.  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 Herhangi bir veri türü veya bir numaralandırma, yapısı, sınıf veya arabirim adını belirtebilirsiniz.  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 Bir başvuru türü için kullandığınız `New` sınıfının yeni bir örneğini oluşturun veya bu yapısı anahtar sözcüğü veri türü tarafından belirtilir. Kullanırsanız `New`, başlatıcı ifade kullanmayın. Bunun yerine, değişkeni oluşturmakta olduğunuz sınıfı oluşturucusu için gerekli iseler bağımsız değişken sağlayın.  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 Bir değişkende yordamı, blok, sınıf, yapı veya modülü bildirebilirsiniz. Bir değişkende kaynak dosya, ad alanı veya arabirimi bildiremezsiniz. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Herhangi bir yordam dışında modülü düzeyinde bildirilmiş bir değişkeni, bir *üye değişkeni* veya *alan*. Üye değişkenleri kapsamında kendi sınıf, yapı veya modülü boyunca kullanılabilir. Yordam düzeyinde bildirilen bir değişkeni, bir *yerel değişken*. Yalnızca kendi yordam veya bloğu içinde kapsamdaki yerel değişkenleri kullanılabilir.  
  
 Aşağıdaki erişim değiştiricileri yordam dışında değişkenleri bildirmek için kullanılır: `Public`, `Protected`, `Friend`, `Protected Friend`, ve `Private`. Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Dim` Anahtar sözcüğü isteğe bağlıdır ve aşağıdaki değiştiricileri belirtirseniz genellikle atlanmış: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, veya `WithEvents`.  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 Varsa `Option Explicit` olduğunu (varsayılan), derleyici, kullandığınız her değişken için bir bildirimi gerektirir. Daha fazla bilgi için bkz: [Option Explicit deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md).  
  
## <a name="specifying-an-initial-value"></a>Bir başlangıç değeri belirtme  
 Oluşturulduğunda bir değişkene bir değer atayabilirsiniz. Değer türü için kullandığınız bir *Başlatıcı* değişkenine atanan bir ifade sağlamak için. İfade derleme zamanında hesaplanan bir sabit değerlendirilmelidir.  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 Bir başlatıcı belirtilirse ve bir veri türü olarak belirtilmemiş bir `As` yan tümcesi *türü çıkarımı* Başlatıcı veri türünden anlamak için kullanılır. Aşağıdaki örnekte, her ikisi de `num1` ve `num2` tamsayı olarak kesin türü belirtilmiş. İkinci bildiriminde tür çıkarımı 3 değerinden türü oluşturur.  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 Tür çıkarımı yordamı düzeyinde uygulanır. Sınıf, yapı, modül veya arabirim yordam dışında uygulanmaz. Tür çıkarımı hakkında daha fazla bilgi için bkz: [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [yerel türü çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Veri türü veya Başlatıcı belirtilmediğinde neler olduğu hakkında daha fazla bilgi için bkz: [varsayılan veri türleri ve değerleri](../../../visual-basic/language-reference/statements/dim-statement.md#default) bu konuda daha sonra.  
  
 Kullanabileceğiniz bir *Başlatıcı nesne* adlandırılmış ve anonim türler örneklerini bildirmek için. Aşağıdaki kod örneği oluşturur bir `Student` sınıf ve nesne Başlatıcı özellikleri başlatmak için kullanır.  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 Nesne başlatıcıları hakkında daha fazla bilgi için bkz: [nasıl yapılır: nesne Başlatıcı kullanarak nesne bildirme](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [nesne başlatıcıları: adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), ve [anonim türler ](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="declaring-multiple-variables"></a>Birden çok değişkenleri bildirme  
 Parantezler ile her biri için ve her bir dizi adı aşağıdaki değişken adını belirten bir bildirim deyiminde çeşitli değişkenler bildirebilirsiniz. Birden çok değişkenleri virgülle ayrılır.  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 Bir sahip birden fazla değişken bildirirseniz `As` yan tümcesi, değişkenlerin bu grup için bir başlatıcı sağlayamıyor.  
  
 Ayrı bir kullanarak farklı veri türleri için farklı değişkenleri belirtebilirsiniz `As` yan tümcesi bildirdiğiniz her değişken için. Her bir değişken ilk belirtilen veri türü alır `As` yan tümcesi karşılaştı sonra kendi `variablename` bölümü.  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a>Diziler  
 Tutmak için bir değişken bildirebilir bir *dizi*, hangi birden fazla değer tutma. Bir değişken dizisini tutan belirtmek için izleyin, `variablename` parantez olmadan hemen. Dizileri hakkında daha fazla bilgi için bkz: [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Alt ve bir dizinin her boyut üst sınırını belirtebilirsiniz. Bunu yapmak için içeren bir `boundslist` parantez içinde. Her boyut için `boundslist` üst sınırı ve isteğe bağlı olarak alt sınırını belirtir. Olup olmadığını belirtin alt her zaman sıfır sınırdır. Her dizin aracılığıyla üst sınır değeri sıfırdan farklılık gösterebilir.  
  
 Aşağıdaki iki ifade eşdeğerdir. Her ifade 21 dizisi bildirir `Integer` öğeleri. Dizi eriştiğinizde, dizin 0 ile 20 arasında değişebilir.  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 Aşağıdaki ifade, iki boyutlu bir dizi türü bildirir `Double`. Dizi olan sütunların 6 (5 + 1) her 4 satırlar (3 + 1). Bir üst sınır boyutu uzunluğunu değil dizin için olası en yüksek değere temsil ettiğini unutmayın. Boyut uzunluğu üst sınırı artı bir taneyi olabilir.  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 Bir dizi 1 ile 32 boyutlarına sahip olabilir.  
  
 Tüm sınırların bir dizi bildiriminde boş bırakabilirsiniz. Bunu yaparsanız, dizi belirttiğiniz boyut sayısını gerekiyor, ancak bunu başlatılmamış. Değerine sahip `Nothing` en az başlatma kadar bazı öğeleri. `Dim` Deyimi tüm boyutları veya için hiç boyut sınırları belirtmeniz gerekir.  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 Dizi birden fazla boyuta varsa, virgül boyut sayısını belirtmek için parantez içermelidir.  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 Bildirebilirsiniz bir *sıfır uzunluk dizisi* -1 olarak dizinin boyutlardan birini bildirme tarafından. Sıfır uzunluklu dizi tutan bir değişken değeri yok `Nothing`. Sıfır uzunlukta diziler belirli ortak dil çalışma zamanı işlevleri tarafından gereklidir. Bu tür bir dizi erişmeye çalışırsa, bir çalışma zamanı özel durumu oluşur. Daha fazla bilgi için bkz: [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Değişmez değer bir dizi kullanarak bir dizi değerlerini başlatabilirsiniz. Bunu yapmak için başlatma değerleri köşeli parantez ile çevrelendiğinden (`{}`).  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 Çok boyutlu diziler için başlatma ayrı her boyut için dış boyutundaki köşeli parantez içine alınır. Öğeleri ana satır sırasına göre belirtilir.  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 Dizi değişmez değerleri hakkında daha fazla bilgi için bkz: [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
##  <a name="default"></a> Varsayılan veri türleri ve değerleri  
 Veri türü ve Başlatıcı belirtmenin çeşitli birleşimleri sonuçları aşağıdaki tabloda açıklanmaktadır bir `Dim` deyimi.  
  
|Belirtilen veri türü?|Belirtilen başlatıcı?|Örnek|Sonuç|  
|---|---|---|---|  
|Hayır|Hayır|`Dim qty`|Varsa [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) olan kapalı (varsayılan), değişkenini ayarlamak `Nothing`.<br /><br /> Varsa `Option Strict` olduğundan, bir derleme zamanı hatası oluşur.|  
|Hayır|Evet|`Dim qty = 5`|Varsa [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) Başlatıcı değişken alır veri türü (varsayılan), olduğunda. Bkz: [yerel türü çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Varsa `Option Infer` kapalıdır ve `Option Strict` kapalıysa, değişken veri türü alır `Object`.<br /><br /> Varsa `Option Infer` kapalıdır ve `Option Strict` olduğundan, bir derleme zamanı hatası oluşur.|  
|Evet|Hayır|`Dim qty As Integer`|Değişken veri türü için varsayılan değer için başlatılır. Bu bölümde daha sonra tabloya bakın.|  
|Evet|Evet|`Dim qty  As Integer = 5`|Başlatıcı'veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.|  
  
 Bir veri türü belirtin, ancak bir başlatıcı belirtmezseniz, Visual Basic veri türü için varsayılan değer değişkenine başlatır. Aşağıdaki tabloda, varsayılan başlatma değerleri gösterir.  
  
|Veri türü|Varsayılan değer|  
|---|---|  
|Tüm sayısal türler (de dahil olmak üzere `Byte` ve `SByte`)|0|  
|`Char`|İkili 0|  
|Tüm başvuru türleri (de dahil olmak üzere `Object`, `String`ve tüm Diziler)|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|12: 00'da, 1 yılının 1 Ocak (01/01/0001 12:00:00 AM)|  
  
 Ayrı bir değişken değilmiş gibi her bir yapı öğesinin başlatılır. Bir dizi uzunluğu, bildirme, ancak öğeleri başlatma değil, her öğe ayrı bir değişken değilmiş gibi başlatılır.  
  
## <a name="static-local-variable-lifetime"></a>Statik yerel değişken ömrü  
 A `Static` yerel değişken bu bildirilen yordamı daha uzun bir yaşam süresi yok. Değişken ömrü sınırlarının yordamı olduğu bildirildi ve olup bağlı `Shared`.  
  
|Yordam bildirimi|Değişkeni başlatılamadı|Varolan değişkeni durdurur|  
|---|---|---|  
|Bir modüle|İlk kez yordamı çağrılır|Program yürütme durduğunda|  
|Sınıf veya yapı yordamdır `Shared`|İlk kez yordamı belirli bir örneğe veya sınıf veya yapı kendisini çağrılır|Program yürütme durduğunda|  
|Sınıf veya yapı yordamı değil `Shared`|İlk kez yordamı belirli bir örneğinde çağrılır|Çöp toplama (GC) örneği serbest bırakıldığında|  
  
## <a name="attributes-and-modifiers"></a>Öznitelikler ve değiştiricileri  
 Öznitelikleri yalnızca üye değişkenleri için değil, yerel değişkenleri uygulayabilirsiniz. Bir öznitelik derlemenin meta verilerini, bilgileri yerel değişkenler gibi geçici depolama için anlamlı olmayan katkıda bulunur.  
  
 Modül düzeyinde kullanamazsınız `Static` değiştiricisi üye değişkenleri bildirin. Yordam düzeyinde kullanamazsınız `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, veya herhangi bir erişim değiştiricileri yerel değişkenleri bildirin.  
  
 Hangi kod sağlayarak bir değişkenine erişebileceği belirtebilirsiniz bir `accessmodifier`. Özel erişim için üye değişkenleri (dışında herhangi bir yordam) varsayılan sınıf ve modül ve yapısı üye değişkenleri varsayılan genel erişim için. Erişim değiştiricileri ile erişim düzeylerine göre ayarlayabilirsiniz. Erişim değiştiricileri (yordam) içindeki yerel değişkenler kullanamazsınız.  
  
 Belirleyebileceğiniz `WithEvents` yalnızca üye değişkenleri, yordam içindeki yerel değişkenler üzerinde değil. Belirtirseniz `WithEvents`, değişken veri türü belirli bir sınıf türü olmamalıdır `Object`. Bir dizi bildiremezsiniz `WithEvents`. Olaylar hakkında daha fazla bilgi için bkz: [olayları](../../../visual-basic/programming-guide/language-features/events/index.md).  
  
> [!NOTE]
>  Kod bir sınıf dışında yapısı veya modülü üye değişkenin adını bu sınıf, yapı veya modül adıyla nitelemeniz gerekir. Bu yordam veya bloğu içinde herhangi bir yerel değişkeni için bir yordam veya blok başvuramaz dışındaki kod.  
  
## <a name="releasing-managed-resources"></a>Yönetilen kaynakları serbest bırakma  
 .NET Framework Atık toplayıcısının bölümünüzün fazladan hiçbir kodlama olmadan yönetilen kaynakları siler. Ancak, atık toplayıcının beklemek yerine yönetilen bir kaynağın elden uygulayabilirsiniz.  
  
 Bir sınıf, özellikle değerli ve olması kaynağı (örneğin, bir veritabanı bağlantısı veya dosya işleci) üzerine barındırıyorsa, artık kullanımda olmayan bir sınıf örneği temizlemek için sonraki çöp toplama kadar beklenecek istemeyebilirsiniz. Bir sınıf uygulayabilir <xref:System.IDisposable> arabirimi çöp toplama önce kaynakları serbest bırakmak için bir yol sağlar. Arabirimi uygulayan bir sınıf kullanıma sunan bir `Dispose` hemen yayımlanacak değerli kaynakları zorlamak için çağrılan yöntemi.  
  
 `Using` Deyimi bir kaynak alınırken, bir dizi deyimleri yürütme ve kaynak atma işlemini otomatikleştirir. Ancak, kaynak uygulamalıdır <xref:System.IDisposable> arabirimi. Daha fazla bilgi için bkz: [kullanarak deyimi](../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanarak değişkenler bildirilmektedir `Dim` çeşitli seçenekler deyimiyle.  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 1 ile 30 arasında asal sayılar listeler. Yerel değişkenler kapsamını kodu açıklamaları açıklanmıştır.  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `speedValue` değişkeni sınıf düzeyinde açıklanmaktadır. `Private` Anahtar sözcüğü değişkeni bildirmek için kullanılır. Değişkeni herhangi bir yordam tarafından erişilebilecek `Car` sınıfı.  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
 [ReDim Deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Option Explicit Deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Option Infer Deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [Değişken Bildirimi](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Nasıl yapılır: Nesne Başlatıcısı Kullanarak Nesne Bildirme](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
 [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
