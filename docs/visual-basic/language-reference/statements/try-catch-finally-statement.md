---
title: Deneyin... Yakala... Finally ekstresi
description: Visual Basic try/catch/finally deyimleriyle özel durum işlemeyi kullanmayı öğrenin.
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
ms.openlocfilehash: 22f1611786a3da512632b5b547b7ef141c8f65c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391774"
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally Deyimi (Visual Basic)

Kodu çalıştırmaya devam ederken, belirli bir kod bloğunda oluşabilecek bazı veya tüm olası hataları işlemek için bir yol sağlar.

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
|`tryStatements`|İsteğe bağlı. Bir hatanın gerçekleşebileceği deyimler. Bileşik bir ifade olabilir.|
|`Catch`|İsteğe bağlı. Birden çok `Catch` blok izin veriliyor. Bloğu işlerken bir özel durum oluşursa `Try` , her bir `Catch` ifade özel durumu, `exception` oluşturulan özel durumu temsil eden bir şekilde işlemediğini tespit etmek üzere metin sırasına göre incelenir.|
|`exception`|İsteğe bağlı. Herhangi bir değişken adı. Başlangıç değeri `exception` oluşturulan hatanın değeridir. `Catch`Yakalanan hatayı belirtmek için ile birlikte kullanılır. Atlanırsa, `Catch` ifade herhangi bir özel durumu yakalar.|
|`type`|İsteğe bağlı. Sınıf filtresinin türünü belirtir. Değeri `exception` `type` türetilmiş bir tür veya tarafından belirtilen türde ise, tanımlayıcı özel durum nesnesine bağlanır.|
|`When`|İsteğe bağlı. `Catch`Yan tümcesinin bulunduğu bir ifade, `When` yalnızca olarak değerlendirildiğinde özel durumları yakalar `expression` `True` . `When`Yan tümce yalnızca özel durumun türü denetlendikten sonra uygulanır ve `expression` özel durumu temsil eden tanımlayıcıya başvurabilir.|
|`expression`|İsteğe bağlı. Örtülü olarak dönüştürülebilir olmalıdır `Boolean` . Genel bir filtreyi tanımlayan herhangi bir ifade. Genellikle hata numarasına göre filtrelemek için kullanılır. `When`Hatanın yakalandığı koşulları belirtmek için anahtar sözcüğü ile birlikte kullanılır.|
|`catchStatements`|İsteğe bağlı. İlişkili blokta oluşan hataları işleyecek olan deyimler `Try` . Bileşik bir ifade olabilir.|
|`Exit Try`|İsteğe bağlı. Yapıyı kesen anahtar sözcük `Try...Catch...Finally` . Yürütme, deyimden hemen sonraki kodla devam eder `End Try` . `Finally`Bu ifade yine de yürütülür. `Finally`Bloklara izin verilmiyor.|
|`Finally`|İsteğe bağlı. `Finally`Yürütme deyimin herhangi bir parçasını terk ettiğinde bir blok her zaman yürütülür `Try...Catch` .|
|`finallyStatements`|İsteğe bağlı. Diğer tüm hata işlemeden sonra yürütülen deyimler.|
|`End Try`|Yapıyı sonlandırır `Try...Catch...Finally` .|

## <a name="remarks"></a>Açıklamalar

Belirli bir özel durumun kodun belirli bir bölümü sırasında oluşması beklendiğinde, kodu bir `Try` bloğa koyun ve `Catch` denetimi sürdürmek ve gerçekleştiklerinde özel durumu işlemek için bir bloğu kullanın.

Bir `Try…Catch` ifade `Try` `Catch` , çeşitli özel durumlar için işleyiciler belirten bir veya daha fazla yan tümce tarafından izlenen bir bloğundan oluşur. Bir blok içinde bir özel durum oluştuğunda `Try` , Visual Basic `Catch` özel durumu işleyen ifadeye bakar. Eşleşen bir `Catch` ifade bulunamazsa, Visual Basic geçerli yöntemi çağıran yöntemi inceler ve bu şekilde çağrı yığınını devam eder. Herhangi `Catch` bir blok bulunmazsa Visual Basic kullanıcıya işlenmeyen bir özel durum iletisi görüntüler ve programın yürütülmesini engeller.

Bir ifadede birden fazla ifade kullanabilirsiniz `Catch` `Try…Catch` . Bunu yaparsanız, `Catch` yan tümcelerinin sıralaması, sırayla incelendikleri için önemlidir. Daha az özel durumları daha az spesifik olanlardan önce yakalayın.

Aşağıdaki `Catch` ifade koşulları en az özeldir ve sınıfından türetilen tüm özel durumları yakalar <xref:System.Exception> . `Catch` `Try...Catch...Finally` Tüm özel özel durumları yakalandıktan sonra, bu çeşitlemelerden genellikle yapıdaki son blok olarak kullanılması gerekir. Denetim akışı, `Catch` Bu çeşitlemelerden birini izleyen bir bloğa hiçbir şekilde ulaşabilirler.

- , `type` `Exception` Örneğin:`Catch ex As Exception`

- İfadesinde `exception` değişken yoktur, örneğin:`Catch`

Bir `Try…Catch…Finally` ifade başka bir blokta iç içe olduğunda `Try` , ilk olarak en içteki bloktaki her bir ifadeyi inceler Visual Basic `Catch` `Try` . Eşleşen hiçbir `Catch` deyim bulunmazsa, arama, `Catch` dış bloğun deyimlerine ilerler `Try…Catch…Finally` .

Bir bloktaki yerel değişkenler `Try` `Catch` ayrı bloklar olduklarından bir blokta kullanılamaz. Birden fazla blok içinde bir değişken kullanmak istiyorsanız, değişkeni yapının dışında bildirin `Try...Catch...Finally` .

> [!TIP]
> `Try…Catch…Finally`İfade, bir IntelliSense kod parçacığı olarak kullanılabilir. Kod parçacıkları yöneticisinde, **her biri için, catch, Property, vb**. ve ardından **hata Işleme (özel durumlar)** için kod desenleri ' ni genişletin. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).

## <a name="finally-block"></a>Finally bloğu

Yapıdan çıkmadan önce çalışması gereken bir veya daha fazla deyim varsa `Try` , bir `Finally` blok kullanın. Denetim, `Finally` yapıyı dışına geçirmeden hemen önce bloğa geçer `Try…Catch` . Bu, yapının içinde herhangi bir yerde bir özel durum gerçekleşse bile geçerlidir `Try` .

Bir `Finally` blok, bir özel durum olsa bile yürütülmesi gereken herhangi bir kodu çalıştırmak için yararlıdır. Denetim, `Finally` bloğun nasıl çıkdığına bakılmaksızın bloğa geçirilir `Try...Catch` .

Bir bloktaki kod, `Finally` kodunuz `Return` bir veya bloğunda deyimle karşılaşırsa bile çalışır `Try` `Catch` . Denetim bir `Try` veya `Catch` bloğundan, aşağıdaki durumlarda karşılık gelen bloğa geçmiyor `Finally` :

- Veya bloğunda bir [End ifadesine](end-statement.md) rastlandı `Try` `Catch` .

- <xref:System.StackOverflowException>, `Try` Veya `Catch` bloğunda oluşturulur.

Yürütmeyi açıkça bir bloğa aktarmak geçerli değildir `Finally` . Bir `Finally` özel durum dışında bir bloğun yürütülmesini aktarma işlemi geçersizdir.

Bir `Try` ifade en az bir `Catch` blok içermiyorsa, bir blok içermesi gerekir `Finally` .

> [!TIP]
> Belirli özel durumları yakalamak zorunda değilseniz, `Using` ifade bir blok gibi davranır `Try…Finally` ve bloğundan nasıl çıkdığlarından bağımsız olarak kaynakların elden çıkarılması garantisi verir. Bu, işlenmeyen bir özel durumla bile geçerlidir. Daha fazla bilgi için bkz. [using deyimleri](using-statement.md).

## <a name="exception-argument"></a>Özel durum bağımsız değişkeni

`Catch`Block `exception` bağımsız değişkeni, sınıfının bir örneğidir <xref:System.Exception> veya sınıfından türetilen bir sınıf `Exception` . `Exception`Sınıf örneği, bloğunda oluşan hataya karşılık gelir `Try` .

Nesnesinin özellikleri, `Exception` bir özel durumun nedenini ve konumunu belirlemesine yardımcı olur. Örneğin, <xref:System.Exception.StackTrace%2A> özelliği özel duruma yol eden çağrılan yöntemleri listeler ve hatanın kodda nerede oluştuğunu bulmanıza yardımcı olur. <xref:System.Exception.Message%2A>özel durumu açıklayan bir ileti döndürür. <xref:System.Exception.HelpLink%2A>ilişkili bir yardım dosyasının bağlantısını döndürür. <xref:System.Exception.InnerException%2A>`Exception`geçerli özel duruma neden olan nesneyi döndürür veya orijinal olmadığında döndürür `Nothing` `Exception` .

## <a name="considerations-when-using-a-trycatch-statement"></a>TRY kullanırken dikkat edilecek noktalar... Catch ekstresi

`Try…Catch`Yalnızca olağan dışı veya beklenmeyen program olaylarının oluşumunu bildirmek için bir ifade kullanın. Bunun nedenleri şunları içerir:

- Çalışma zamanında özel durumları yakalama, ek yük oluşturur ve özel durumların önüne geçmek için önceden denetlenmekten daha yavaş olabilir.

- Bir `Catch` blok doğru işlenmezse, özel durum kullanıcılara doğru şekilde raporlanmayabilir.

- Özel durum işleme bir programı daha karmaşık hale getirir.

`Try…Catch`Gerçekleşmesi olası bir koşulu denetlemek için her zaman bir deyime gerek kalmaz. Aşağıdaki örnek, açmayı denemeden önce bir dosyanın var olup olmadığını denetler. Bu, yöntemi tarafından oluşturulan bir özel durum yakalama gereksinimini azaltır <xref:System.IO.File.OpenText%2A> .

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

`Catch`Bloklarında kodun, iş parçacığı güvenli günlüğe kaydetme veya uygun iletiler aracılığıyla kullanıcılara özel durumları düzgün bir şekilde bildirediğinden emin olun. Aksi takdirde, özel durumlar bilinmiyor olarak kalabilir.

## <a name="async-methods"></a>Zaman uyumsuz yöntemler

[Zaman uyumsuz](../modifiers/async.md) değiştiriciyle bir yöntemi işaretlerseniz, yönteminde [await](../operators/await-operator.md) işlecini kullanabilirsiniz. İşleci olan bir ifade, `Await` beklenen görev tamamlanana kadar yöntemi yürütmeyi askıya alır. Görev, devam eden işi temsil eder. Operatör ile ilişkili görev `Await` tamamlandığında, yürütme aynı yöntemde devam eder. Daha fazla bilgi için bkz. [zaman uyumsuz programlarda denetim akışı](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

Zaman uyumsuz bir yöntem tarafından döndürülen bir görev, işlenmemiş bir özel durum nedeniyle tamamlanmadığını belirten hatalı bir durumda bitemeyebilir. Bir görev iptal edilmiş durumunda da bitebileceği `OperationCanceledException` için, await ifadesinin dışında bir durum ortaya çıkar. Her iki tür özel durum yakalamak için, `Await` görevle ilişkili ifadeyi bir `Try` blokta yerleştirin ve özel durumu `Catch` blosonra yakalayın. Bu konunun ilerleyen kısımlarında bir örnek verilmiştir.

Bir görev hatalı bir durumda olabilir, çünkü hatalı bir şekilde birden çok özel durum sorumludur. Örneğin, görev bir çağrısının sonucu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> . Böyle bir görevi bekleyolduğunuzda, yakalanan özel durum yalnızca özel durumlardan biridir ve hangi özel durumun yakalanıp yakalanmayacak olduğunu tahmin edemeyecektir. Bu konunun ilerleyen kısımlarında bir örnek verilmiştir.

Bir `Await` ifade bir `Catch` blok veya blok içinde olamaz `Finally` .

## <a name="iterators"></a>Yineleyiciler

Yineleyici işlevi veya `Get` erişimcisi bir koleksiyon üzerinde özel bir yineleme gerçekleştirir. Bir yineleyici, tek seferde koleksiyonun her bir öğesini döndürmek için bir [yield](yield-statement.md) ifadesini kullanır. Her biri Için bir kullanarak bir yineleyici işlevi çağırın [... Sonraki Ifade](for-each-next-statement.md).

Bir `Yield` ifade bir blok içinde olabilir `Try` . `Try`Bir ifade içeren bir blok `Yield` `Catch` blokları içerebilir ve bir bloğuna sahip olabilir `Finally` . Bir örnek için [yineleyicilerin](../../programming-guide/concepts/iterators.md) "Visual Basic blokları dene" bölümüne bakın.

Bir `Yield` ifade bir `Catch` blok veya blok içinde olamaz `Finally` .

`For Each`Gövde (Yineleyici işlevi dışında) bir özel durum oluşturursa, `Catch` Yineleyici işlevindeki bir blok yürütülmez, ancak `Finally` Yineleyici işlevindeki bir blok yürütülür. `Catch`Yineleyici işlevi içindeki bir blok yalnızca Yineleyici işlevinin içinde oluşan özel durumları yakalar.

## <a name="partial-trust-situations"></a>Kısmi güven durumları

Bir ağ paylaşımında barındırılan bir uygulama gibi kısmi güven durumlarında, `Try...Catch...Finally` çağrıyı içeren yöntemden önce oluşan güvenlik özel durumlarını yakalamaz. Aşağıdaki örnek, bir sunucu paylaşımında yerleştirip buradan çalıştırdığınızda "System. Security. SecurityException: Istek başarısız oldu" hatasını üretir. Güvenlik özel durumları hakkında daha fazla bilgi için, <xref:System.Security.SecurityException> sınıfına bakın.

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

Böyle bir kısmi güven durumunda, `Process.Start` bir ifadeyi ayrı bir içine koymanız gerekir `Sub` . Öğesine yapılan ilk çağrı `Sub` başarısız olur. Bu `Try...Catch` , öğesini `Sub` içeren `Process.Start` ve güvenlik özel durumunun üretilmesine neden olacak şekilde yakalamak için bu işlemi yakalar.

## <a name="examples"></a>Örnekler

### <a name="the-structure-of-trycatchfinally"></a>TRY yapısı... Yakala... Son olarak

Aşağıdaki örnek deyimin yapısını gösterir `Try...Catch...Finally` .

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>Try bloğundan çağrılan bir yöntemde özel durum

Aşağıdaki örnekte, `CreateException` yöntemi bir oluşturur `NullReferenceException` . Özel durumu üreten kod bir blok içinde değil `Try` . Bu nedenle, `CreateException` yöntemi özel durumu işlemez. Yöntemine yapılan `RunSample` çağrı bir blokta olduğundan, yöntemi özel durumu işler `CreateException` `Try` .

Örnek, en `Catch` belirli özel durum türleri için en çok genel olarak sıralanmış deyimler içerir.

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>Catch while ekstresi

Aşağıdaki örnek, bir `Catch When` ifadenin koşullu bir ifadeye filtre uygulamak için nasıl kullanılacağını gösterir. Koşullu ifade olarak değerlendirilirse `True` , `Catch` bloktaki kod çalışır.

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>İç içe deneme deyimleri

Aşağıdaki örnekte, `Try…Catch` bloğunda bulunan bir ifade vardır `Try` . İç `Catch` blok, `InnerException` özelliği özgün özel duruma ayarlanmış bir özel durum oluşturur. Dış `Catch` blok kendi özel durumunu ve iç özel durumu raporlar.

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>Zaman uyumsuz metotlar için özel durum işleme

Aşağıdaki örnek, zaman uyumsuz metotlar için özel durum işlemeyi gösterir. Zaman uyumsuz bir görev için geçerli olan bir özel durumu yakalamak için, `Await` ifade çağıranın bir `Try` bloğunda ve özel durum `Catch` bloğunda yakalanır.

`Throw New Exception`Özel durum işlemeyi göstermek için örnekteki satırın açıklamasını kaldırın. Özel durum `Catch` bloğunda yakalanır, görevin `IsFaulted` özelliği olarak ayarlanır `True` ve görevin `Exception.InnerException` özelliği özel duruma ayarlanır.

`Throw New OperationCancelledException`Zaman uyumsuz bir işlemi iptal ettiğinizde ne olacağını göstermek için çizginin açıklamasını kaldırın. Özel durum `Catch` bloğunda yakalanır ve görevin `IsCanceled` özelliği olarak ayarlanır `True` . Ancak, bu örnek için geçerli olmayan bazı koşullar altında, olarak `IsFaulted` ayarlanır `True` ve `IsCanceled` olarak ayarlanır `False` .

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>Zaman uyumsuz metotlarda birden çok özel durumu işleme

Aşağıdaki örnekte, birden çok görevin birden çok özel durum ile sonuçlanbildiği özel durum işleme gösterilmektedir. `Try`Blok `Await` döndürülen görevin ifadesine sahiptir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> . Uygulanan üç görev tamamlandığında görev tamamlanır <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> .

Üç görevin her biri özel duruma neden olur. `Catch`Blok, `Exception.InnerExceptions` döndürülen görevin özelliğinde bulunan özel durumlar boyunca yinelenir `Task.WhenAll` .

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Exit Deyimi](exit-statement.md)
- [On Error Deyimi](on-error-statement.md)
- [Kod Parçacıkları İçin En İyi Uygulamalar](/visualstudio/ide/best-practices-for-using-code-snippets)
- [Özel Durum İşleme](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Throw Deyimi](throw-statement.md)
