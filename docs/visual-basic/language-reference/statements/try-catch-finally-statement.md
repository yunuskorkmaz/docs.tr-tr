---
title: Deneyin... Catch... -Visual Basic finally deyimi
description: Özel durum işleme Visual Basic Try/Catch/Finally deyimleri ile kullanmayı öğrenin.
ms.date: 12/07/2018
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement [Visual Basic]
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement [Visual Basic], Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement [Visual Basic]
- When keyword [Visual Basic]
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
ms.custom: seodec18
ms.openlocfilehash: 2e4fef836b08f536565105dbab76292b2fc4388e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934270"
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally Deyimi (Visual Basic)

Kod çalışmaya devam ederken, belirli bir kod bloğu içinde oluşabilecek bazı ya da tüm olası hataları işlemek için bir yol sağlar.

## <a name="syntax"></a>Sözdizimi

```vb
Try
    [ tryStatements ]
    [ Exit Try ]
[ Catch [ exception [ As type ] ] [ When expression ]
    [ catchStatements ]
    [ Exit Try ] ]
[ Catch ... ]
[ Finally
    [ finallyStatements ] ]
End Try
```

## <a name="parts"></a>Bölümler

|Terim|Tanım|
|---|---|
|`tryStatements`|İsteğe bağlı. Deyim, burada bir hata oluşabilir. Bileşik deyim olabilir.|
|`Catch`|İsteğe bağlı. Birden çok `Catch` izin engeller. Bir özel durum işleme sırasında oluşursa `Try` engelleme, her `Catch` deyimi, özel durum ile işleme olup olmadığını belirlemek için metinsel sırayla incelenir `exception` temsil eden özel durum oluşturuldu.|
|`exception`|İsteğe bağlı. Herhangi bir değişken adı. Başlangıç değeri oluşan `exception` hatadır değeridir. İle kullanılan `Catch` hatanın belirtileceği yakalandı. Atlanırsa, `Catch` deyimi herhangi bir özel durumu yakalar.|
|`type`|İsteğe bağlı. Sınıf filtre türünü belirtir. Varsa değerini `exception` tarafından belirtilen türde `type` veya türetilmiş bir tür tanımlayıcısı özel durum nesnesine bağlı olur.|
|`When`|İsteğe bağlı. A `Catch` deyimiyle bir `When` yan tümcesi, özel durumları yakalar yalnızca `expression` değerlendiren `True`. A `When` yan tümcesi yalnızca özel durumun türünü denetledikten sonra uygulanır ve `expression` özel durumu temsil eden tanımlayıcı başvurabilir.|
|`expression`|İsteğe bağlı. Örtük olarak dönüştürülebilir olmalıdır `Boolean`. Genel filtre açıklar herhangi bir ifade. Genellikle, hata numarasına göre filtrelemek için kullanılır. İle kullanılan `When` koşullar altında hata yakalandı belirtmek için anahtar sözcüğü.|
|`catchStatements`|İsteğe bağlı. İlişkili içinde oluşan hataları işlemek için deyim `Try` blok. Bileşik deyim olabilir.|
|`Exit Try`|İsteğe bağlı. / Keser anahtar sözcüğü `Try...Catch...Finally` yapısı. Yürütmeyi hemen kod ile devam ettirir `End Try` deyimi. `Finally` Deyimi hala yürütülür. İçinde izin verilmiyor `Finally` engeller.|
|`Finally`|İsteğe bağlı. A `Finally` blok herhangi bir bölümü yürütme ayrıldığında her zaman yürütülür `Try...Catch` deyimi.|
|`finallyStatements`|İsteğe bağlı. Diğer tüm hata işleme gerçekleştikten sonra yürütülen deyim.|
|`End Try`|Sonlandırır `Try...Catch...Finally` yapısı.|

## <a name="remarks"></a>Açıklamalar

Belirli bir özel durum kodu belirli bir bölümünü sırasında oluşabilecek bekliyorsanız, kod yerleştirecek bir `Try` engelleme ve kullanmak bir `Catch` denetimini sürdürme ve bu durum oluşursa özel durum işleme bloğu.

A `Try…Catch` deyimi oluşur bir `Try` blok izlenen bir veya daha fazla tarafından `Catch` çeşitli özel durumlar için işleyiciler belirten yan tümceleri. Bir özel durum harekete geçirildiğinde bir `Try` engelleme, Visual Basic arar `Catch` özel durumu işleyen bir ifade. Eşleşen bir `Catch` deyimi bulunamadı, Visual Basic, çağrı yığını ayarlama ve benzeri geçerli bir yöntemi çağıran yönteme inceler. Hayır ise `Catch` bloğu bulundu, Visual Basic, kullanıcıya bir işlenmeyen özel durum iletisi görüntüler ve programın yürütülmesini durdurur.

Birden fazla kullanabileceğiniz `Catch` deyiminde bir `Try…Catch` deyimi. Bu sırasını `Catch` yan tümceleri, bunlar sırayla incelenir olduğundan önemlidir. Less yazımına özgü olanlardan önce daha özel istisnaları yakalayın.

Aşağıdaki `Catch` deyimi koşulları en az özel olan ve tüm türetilen özel durum <xref:System.Exception> sınıfı. Bu farklılıkların biri son normalde kullanması gereken `Catch` engelleyin `Try...Catch...Finally` beklediğiniz tüm belirli özel durumları yakalama sonra yapısı. Denetim akışı ulaşabilirsiniz hiçbir zaman bir `Catch` ya da bu farklılıkların izleyen blok.

- `type` Olduğu `Exception`, örneğin: `Catch ex As Exception`

- Deyim olmayan `exception` değişken, örneğin: `Catch`

Olduğunda bir `Try…Catch…Finally` deyimi iç içe başka `Try` blok, Visual Basic ilk inceler her `Catch` en içteki deyiminde `Try` blok. Hiç eşleşen `Catch` deyimi bulundu, aramaya devam eder `Catch` bilgilerinin dış `Try…Catch…Finally` blok.

Yerel değişkenleri bir `Try` blok içinde kullanılabilir olmayan bir `Catch` çünkü bunlar ayrı bloklarda engelleyin. Birden fazla blok içinde bir değişken kullanmak istiyorsanız, dışında değişkenini tanımlamak `Try...Catch...Finally` yapısı.

> [!TIP]
> `Try…Catch…Finally` Deyimi bir IntelliSense kod parçacığı kullanılabilir. Kod parçacıkları Yöneticisi'nde **kod desenleri - IF, adet için Try Catch, özellik vb.**, ardından **hata işleme (özel)**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).

## <a name="finally-block"></a>Finally bloğu

Çıkış önce çalıştırılması gereken bir veya daha fazla deyimleri varsa `Try` yapısı, kullanan bir `Finally` blok. Denetim geçtiği `Finally` yalnızca tanesi geçirmeden önce block `Try…Catch` yapısı. İçinde herhangi bir özel bir durum oluştuğunda olsa bile bu geçerlidir `Try` yapısı.

A `Finally` blok, bir özel durum olsa bile, herhangi bir kod çalıştıran yürütülmesi gereken için yararlıdır. Denetim geçirildiğinde `Finally` bakılmaksızın nasıl blok `Try...Catch` block çıkar.

Kodda bir `Finally` kodunuzu karşılaştığında bile bloğu çalışır bir `Return` deyiminde bir `Try` veya `Catch` blok. Denetim gelen geçirmek değil bir `Try` veya `Catch` block karşılık gelen `Finally` aşağıdaki durumlarda engelle:

- Bir [End deyimi](end-statement.md) ile karşılaşılırsa `Try` veya `Catch` blok.

- A <xref:System.StackOverflowException> oluşturulur `Try` veya `Catch` blok.

Açıkça yürütme içine aktarmak için geçerli değil bir `Finally` blok. Yürütme / aktarma bir `Finally` bloğu geçerli olmayan bir özel durum, dışında.

Varsa bir `Try` deyimi en az bir içermiyor `Catch` bloğu içermesi gereken bir `Finally` blok.

> [!TIP]
> Belirli özel durumları yakalamak yoksa `Using` deyimi davranacağını gibi bir `Try…Finally` blok ve nasıl blok çıkış bağımsız olarak bağlı olarak, kaynakların elden garanti eder. İşlenmeyen bir özel durumla bile bu geçerlidir. Daha fazla bilgi için [Using deyimi](using-statement.md).

## <a name="exception-argument"></a>Özel durum bağımsız değişken

`Catch` Blok `exception` bağımsız değişken öğesinin bir örneğiyse <xref:System.Exception> sınıfı veya türetildiği bir sınıf `Exception` sınıfı. `Exception` Karşılık gelen sınıf örneği oluştu hata `Try` blok.

Özelliklerini `Exception` nesnesi bir özel durum konumunu ve sorunun kaynağını belirlemek için Yardım. Örneğin, <xref:System.Exception.StackTrace%2A> özelliği, kod hatasının oluştuğu bulmanıza yardımcı olacak özel durumu götüren çağırılan yöntemleri listeler. <xref:System.Exception.Message%2A> özel durumu açıklayan bir ileti döndürür. <xref:System.Exception.HelpLink%2A> bir bağlantı, ilişkili bir Yardım dosyasına döndürür. <xref:System.Exception.InnerException%2A> döndürür `Exception` veya geçerli özel duruma neden olan bir nesne döndürür `Nothing` hiçbir özgün ise `Exception`.

## <a name="considerations-when-using-a-trycatch-statement"></a>Bir Try kullanmayla ilgili konular... Catch deyimi

Kullanım bir `Try…Catch` deyimi yalnızca olağan dışı ya da beklenmeyen programı olayların sinyal. Bunun nedeni aşağıdakileri içerir:

- Çalışma zamanında özel durumları yakalama ek yükü oluşturur ve özel durumlar önlemek için önceden denetlemekten daha yavaş olması olasıdır.

- Varsa bir `Catch` blok düzgün işlenmez, özel durum kullanıcılara doğru bildirilmeyebilir.

- Özel durum işleme bir program daha karmaşık hale getirir.

Her zaman gereksinim duymadığınız bir `Try…Catch` deyimi, arıza oluştuğu sırada bir koşul için denetlenecek. Aşağıdaki örnek, bir dosyayı açmak denemeden önce mevcut olup olmadığını denetler. Bu tarafından oluşturulan bir özel durum yakalama gereksinimini azaltır <xref:System.IO.File.OpenText%2A> yöntemi.

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

Bu kodu olun `Catch` blokları düzgün bir şekilde rapor edebilir, kullanıcılara özel durumları iş parçacığı günlük kaydı veya uygun iletileri üzerinden. Aksi takdirde, özel durumlar bilinmeyen kalabilir.

## <a name="async-methods"></a>Zaman uyumsuz yöntemler

Bir yöntem ile işaretlerseniz [zaman uyumsuz](../modifiers/async.md) kullanabileceğiniz değiştiricisi [Await](../operators/await-operator.md) yönteminde işleci. With deyimi `Await` işleci awaited görevi tamamlanıncaya kadar yöntemin yürütülmesini askıya alır. Görev, devam eden çalışmayı temsil eder. Zaman ile ilişkili görev `Await` işleci tamamlandıktan, aynı yöntemin yürütülmesine devam ettirir. Daha fazla bilgi için [zaman uyumsuz programlarda akış kontrolü](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).

Zaman uyumsuz bir yöntem tarafından döndürülen görev hatalı bir durumda, işlenmeyen bir özel durum nedeniyle tamamlandı belirten sonlandırabiliriz. Bir görev sonuçlanır bir iptal edilmiş duruma da bitemez bir `OperationCanceledException` await ifadesi dışında oluşturulan. Herhangi bir türde özel durum yakalamak için yerleştirin `Await` görev ile ilişkili ifade bir `Try` blok ve özel durumu `Catch` blok. Örnek bu konunun ilerleyen bölümlerinde verilmiştir.

Bir görev birden çok özel durum, hatalı için sorumlu hatalı bir durumda olabilir. Örneğin, görev yapılan bir çağrının sonucu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Böyle bir görevi beklerken, özel durum yakalandı yalnızca bir özel durumlar ve özel durum yakalandı tahmin edemezsiniz. Örnek bu konunun ilerleyen bölümlerinde verilmiştir.

Bir `Await` ifade olamaz içinde bir `Catch` blok veya `Finally` blok.

## <a name="iterators"></a>Yineleyiciler

Yineleyici işleve veya `Get` erişimci bir koleksiyon üzerinde özel yineleme gerçekleştirir. Yineleyici bir [Yield](yield-statement.md) deyimini her öğesini birer birer koleksiyonunun bir döndürür. Kullanarak bir yineleyici işlevi çağırmak bir [her biri için... Sonraki deyimi](for-each-next-statement.md).

A `Yield` deyimi içinde olabilir bir `Try` blok. A `Try` içeren blok bir `Yield` deyimi olabilir `Catch` engeller ve olabilir bir `Finally` blok. "Deneyin blokları Visual Basic" bölümüne bakın [yineleyiciler](../../programming-guide/concepts/iterators.md) örneği.

A `Yield` deyimi içinde olamaz bir `Catch` blok veya `Finally` blok.

Varsa `For Each` gövdesi (yineleyici işleve dışında) bir özel durum oluşturursa bir `Catch` yineleyici işleve bloğunda yürütülmedi, ancak bir `Finally` yineleyici işleve bloğunda yürütülür. A `Catch` blok içinde bir yineleyici işlevi yineleyici işlevde oluşan özel durumları yakalar.

## <a name="partial-trust-situations"></a>Kısmi güven durumları

Bir ağ paylaşımında barındırılan bir uygulamanın gibi kısmi güven durumlarında `Try...Catch...Finally` çağrı içeren yöntemi çağrılmadan önce gerçekleşen bir güvenlik özel durumları yakalamaz. Sunucu paylaşımı üzerindeki put ve oradan çalıştırın, aşağıdaki örnekte, bir hata oluşturur. "System.Security.SecurityException: İstek başarısız oldu." Güvenlik özel durumları hakkında daha fazla bilgi için bkz. <xref:System.Security.SecurityException> sınıfı.

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

Böyle bir kısmi güven durumda moduna sahip `Process.Start` ayrı bir deyimde `Sub`. İlk çağrı `Sub` başarısız olur. Böylece `Try...Catch` önce bunu yakalayıp yakalamayacağınıza karar `Sub` içeren `Process.Start` başlatılır ve güvenlik özel durumu üretti.

## <a name="examples"></a>Örnekler

### <a name="the-structure-of-trycatchfinally"></a>Try yapısı... Catch... Son olarak

Yapısı aşağıdaki örnekte `Try...Catch...Finally` deyimi.

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>Bir Try bloğundan adlı bir yöntemde özel durum

Aşağıdaki örnekte, `CreateException` yöntem bir `NullReferenceException`. Özel durum oluşturan kodu kullanımda olmayan bir `Try` blok. Bu nedenle, `CreateException` yöntemi özel durum işlemez. `RunSample` Olduğundan, yöntemi özel durum işleme çağrısı `CreateException` yöntemdir içinde bir `Try` blok.

Örnek içerir `Catch` deyimleri için birden fazla özel durumlar, sipariş gelen en belirli en genel.

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>Catch deyimi

Aşağıdaki örnek nasıl kullanılacağını gösteren bir `Catch When` üzerinde bir koşullu ifade filtrelemek için deyimi. Koşullu ifade değerlendirilirse `True`, kodda `Catch` bloğu çalışır.

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>İç içe geçmiş Try deyimleri

Aşağıdaki örnek sahip bir `Try…Catch` bulunan deyimi bir `Try` blok. İç `Catch` blok olan bir özel durum oluşturursa, `InnerException` özgün özel durum özelliği. Dış `Catch` blok raporları kendi özel ve iç özel durum.

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>Özel durum işleme için zaman uyumsuz yöntemi

Aşağıdaki örnekte, özel durum işleme için zaman uyumsuz yöntemler gösterilmektedir. Zaman uyumsuz bir görev için geçerli bir özel durum yakalamak için `Await` ifade konusu bir `Try` bloğunu çağıran ve özel durum yakalandı `Catch` blok.

Açıklamadan çıkarın `Throw New Exception` özel durum işleme göstermek için örnek satır. Özel durum yakalandı `Catch` engelleme, görevin `IsFaulted` özelliği `True`ve görev `Exception.InnerException` özelliği, özel duruma ayarlanır.

Açıklamadan çıkarın `Throw New OperationCancelledException` zaman uyumsuz bir işlem iptal ettiğinizde ne göstermek için satır. Özel durum yakalandı `Catch` blok ve görevin `IsCanceled` özelliği `True`. Ancak, bu örnek için geçerli değildir bazı koşullar altında `IsFaulted` ayarlanır `True` ve `IsCanceled` ayarlanır `False`.

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>Birden çok zaman uyumsuz yöntemlerde özel durumları işleme

Aşağıdaki örnek, özel durum işleme birden çok görev içinde birden çok özel durum burada sonuçlanabilir gösterir. `Try` Bloğu `Await` görev ifadesi, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> döndürdü. Üç, görevler, görev tamamlandığında <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> uygulanan getirildiğinden.

Her biri üç görev, bir özel durum neden olur. `Catch` Blok yinelenir bulunan özel durumlar üzerinden `Exception.InnerExceptions` görevin özelliği, `Task.WhenAll` döndürdü.

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Exit Deyimi](exit-statement.md)
- [On Error Deyimi](on-error-statement.md)
- [Kod Parçacıkları İçin En İyi Uygulamalar](/visualstudio/ide/best-practices-for-using-code-snippets)
- [Özel Durum İşleme](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Throw Deyimi](throw-statement.md)