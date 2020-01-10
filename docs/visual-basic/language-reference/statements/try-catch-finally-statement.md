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
ms.openlocfilehash: bb6f17f7ce88caea0b9d30ec880194f2bb71c6a6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705775"
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
|`Catch`|İsteğe bağlı. Çoklu `Catch` blokları izin veriliyor. `Try` bloğunu işlerken bir özel durum oluşursa, her `Catch` bir durum, özel durumu (atılan özel durumu temsil eden `exception`) nasıl işleyeceğini öğrenmek için metin sırasına göre incelenir.|
|`exception`|İsteğe bağlı. Herhangi bir değişken adı. `exception` ilk değeri oluşturulan hatanın değeridir. Yakalanan hatayı belirtmek için `Catch` ile birlikte kullanılır. Atlanırsa, `Catch` ifade herhangi bir özel durumu yakalar.|
|`type`|İsteğe bağlı. Sınıf filtresinin türünü belirtir. `exception` değeri `type` veya türetilmiş bir tür tarafından belirtilen türde ise, tanımlayıcı özel durum nesnesine bağlanır.|
|`When`|İsteğe bağlı. `When` yan tümcesinin bulunduğu `Catch` deyimi, yalnızca `expression` `True`değerlendirirken özel durumları yakalar. `When` yan tümcesi yalnızca özel durumun türü denetlendikten sonra uygulanır ve `expression` özel durumu temsil eden tanımlayıcıya başvurabilir.|
|`expression`|İsteğe bağlı. `Boolean`için örtük olarak dönüştürülebilir olmalıdır. Genel bir filtreyi tanımlayan herhangi bir ifade. Genellikle hata numarasına göre filtrelemek için kullanılır. Hatanın yakalandığı koşulları belirtmek için `When` anahtar sözcüğüyle birlikte kullanılır.|
|`catchStatements`|İsteğe bağlı. İlişkili `Try` bloğunda oluşan hataları işlemek için deyimler. Bileşik bir ifade olabilir.|
|`Exit Try`|İsteğe bağlı. `Try...Catch...Finally` yapısını kesen anahtar sözcük. Yürütme `End Try` deyimden hemen sonra kodla devam eder. `Finally` deyimin yürütülmesi devam eder. `Finally` bloklarında izin verilmez.|
|`Finally`|İsteğe bağlı. `Finally` bloğu her zaman yürütme, `Try...Catch` bildiriminin herhangi bir parçasını terk ettiğinde yürütülür.|
|`finallyStatements`|İsteğe bağlı. Diğer tüm hata işlemeden sonra yürütülen deyimler.|
|`End Try`|`Try...Catch...Finally` yapısını sonlandırır.|

## <a name="remarks"></a>Açıklamalar

Belirli bir özel durumun kodun belirli bir bölümü sırasında oluşması beklendiğinde, kodu bir `Try` bloğuna koyun ve bir `Catch` bloğunu kullanarak denetimi koruyabilir ve hata oluşursa özel durumu işleyebilir.

`Try…Catch` bir ifade, çeşitli özel durumlar için işleyiciler belirten bir veya daha fazla `Catch` yan tümcesi tarafından izlenen bir `Try` bloğundan oluşur. Bir `Try` bloğunda bir özel durum oluştuğunda, Visual Basic özel durumu işleyen `Catch` ifadeye bakar. Eşleşen bir `Catch` deyimleri bulunamazsa, Visual Basic geçerli yöntemi çağıran yöntemi inceler ve bu şekilde çağrı yığınını devam eder. `Catch` bloğu bulunmazsa Visual Basic kullanıcıya işlenmeyen bir özel durum iletisi görüntüler ve programın yürütülmesini engeller.

Bir `Try…Catch` bildiriminde birden fazla `Catch` ifadesini kullanabilirsiniz. Bunu yaparsanız, `Catch` yan tümcelerinin sıralaması, sırayla incelendikleri için önemlidir. Daha az özel durumları daha az spesifik olanlardan önce yakalayın.

Aşağıdaki `Catch` deyimin koşulları en az özeldir ve <xref:System.Exception> sınıfından türetilen tüm özel durumları yakalar. Tahmin ettiğiniz tüm özel durumları yakalandıktan sonra, bu varyasyonların her birini `Try...Catch...Finally` yapısında son `Catch` bloğu olarak kullanmanız gerekir. Denetim akışı, bu çeşitlemelerden birini izleyen `Catch` bloğuna hiçbir şekilde ulaşabilirler.

- `type` `Exception`, örneğin: `Catch ex As Exception`

- Deyimin `exception` değişkeni yok, örneğin: `Catch`

`Try…Catch…Finally` bir ifade başka bir `Try` bloğunda iç içe olduğunda, Visual Basic ilk olarak en içteki `Try` bloğundaki her bir `Catch` ekstresini inceler. Eşleşen `Catch` deyimi bulunamazsa, arama, dış `Try…Catch…Finally` bloğunun `Catch` ifadelerine devam eder.

`Try` bloğundan yerel değişkenler, ayrı bloklar olduklarından bir `Catch` bloğunda kullanılamaz. Birden fazla blok içinde bir değişken kullanmak istiyorsanız, değişkeni `Try...Catch...Finally` yapısı dışında bildirin.

> [!TIP]
> `Try…Catch…Finally` deyimin bir IntelliSense kod parçacığı olarak kullanılabilir. Kod parçacıkları yöneticisinde, **her biri için, catch, Property, vb**. ve ardından **hata Işleme (özel durumlar)** için kod desenleri ' ni genişletin. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).

## <a name="finally-block"></a>Finally bloğu

`Try` yapısından çıkmadan önce çalışması gereken bir veya daha fazla deyim varsa, bir `Finally` bloğu kullanın. Denetim, `Try…Catch` yapısını geçirmeden hemen önce `Finally` bloğuna geçer. Bu, `Try` yapısı içinde herhangi bir yerde bir özel durum gerçekleşse bile geçerlidir.

Bir `Finally` bloğu, bir özel durum olsa bile yürütülmesi gereken herhangi bir kodu çalıştırmak için yararlıdır. `Try...Catch` bloğunun çıkış şeklinden bağımsız olarak denetim `Finally` bloğuna geçirilir.

`Finally` bloğundaki kod, kodunuz `Try` veya `Catch` bloğunda bir `Return` ifadesiyle karşılaşırsa bile çalışır. Denetim, aşağıdaki durumlarda bir `Try` veya `Catch` bloğundan karşılık gelen `Finally` bloğuna geçmiyor:

- `Try` veya `Catch` bloğunda bir [End ifadesiyle](end-statement.md) karşılaşıldı.

- `Try` veya `Catch` bloğunda bir <xref:System.StackOverflowException> oluşturulur.

Yürütmeyi `Finally` bloğuna açıkça aktarmak geçerli değildir. Bir özel durum dışında `Finally` bloğunun yürütülmesini aktarma geçerli değildir.

Bir `Try` deyimin en az bir `Catch` bloğu yoksa, bir `Finally` bloğu içermesi gerekir.

> [!TIP]
> Belirli özel durumları yakalamada, `Using` ifade `Try…Finally` bir blok gibi davranır ve bloğundan nasıl çıktığınızda bağımsız olarak kaynakların elden çıkarılmasını garanti eder. Bu, işlenmeyen bir özel durumla bile geçerlidir. Daha fazla bilgi için bkz. [using deyimleri](using-statement.md).

## <a name="exception-argument"></a>Özel durum bağımsız değişkeni

`Catch` Block `exception` bağımsız değişkeni, <xref:System.Exception> sınıfının veya `Exception` sınıfından türetilen bir sınıfın bir örneğidir. `Exception` sınıfı örneği, `Try` bloğunda oluşan hataya karşılık gelir.

`Exception` nesnesinin özellikleri, bir özel durumun nedenini ve konumunu belirlemesine yardımcı olur. Örneğin, <xref:System.Exception.StackTrace%2A> özelliği, özel duruma yol eden çağrılan yöntemleri listeler ve hatanın kodda nerede oluştuğunu bulmanıza yardımcı olur. <xref:System.Exception.Message%2A>, özel durumu açıklayan bir ileti döndürür. <xref:System.Exception.HelpLink%2A> ilişkili bir yardım dosyasının bağlantısını döndürür. <xref:System.Exception.InnerException%2A>, geçerli özel duruma neden olan `Exception` nesnesini döndürür veya orijinal `Exception`yoksa `Nothing` döndürüyor.

## <a name="considerations-when-using-a-trycatch-statement"></a>TRY kullanırken dikkat edilecek noktalar... Catch ekstresi

Yalnızca olağan dışı veya beklenmeyen program olaylarının oluşumunu göstermek için bir `Try…Catch` ifadesini kullanın. Bunun nedenleri şunları içerir:

- Çalışma zamanında özel durumları yakalama, ek yük oluşturur ve özel durumların önüne geçmek için önceden denetlenmekten daha yavaş olabilir.

- `Catch` bloğu doğru işlenmezse, özel durum kullanıcılara doğru şekilde raporlanmayabilir.

- Özel durum işleme bir programı daha karmaşık hale getirir.

Gerçekleşmesi muhtemel bir koşulu denetlemek için her zaman bir `Try…Catch` bildirimine ihtiyacınız yoktur. Aşağıdaki örnek, açmayı denemeden önce bir dosyanın var olup olmadığını denetler. Bu, <xref:System.IO.File.OpenText%2A> metodu tarafından oluşturulan özel durum yakalama gereksinimini azaltır.

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

`Catch` bloklardaki kodun, iş parçacığı güvenli günlüğe kaydetme veya uygun iletiler aracılığıyla kullanıcılara özel durumları düzgün şekilde bildirediğinden emin olun. Aksi takdirde, özel durumlar bilinmiyor olarak kalabilir.

## <a name="async-methods"></a>Zaman uyumsuz yöntemler

[Zaman uyumsuz](../modifiers/async.md) değiştiriciyle bir yöntemi işaretlerseniz, yönteminde [await](../operators/await-operator.md) işlecini kullanabilirsiniz. `Await` işleci olan bir ifade, beklenen görev tamamlanana kadar yöntemi yürütmeyi askıya alır. Görev, devam eden işi temsil eder. `Await` işleci ile ilişkili görev tamamlandığında, yürütme aynı yöntemde devam eder. Daha fazla bilgi için bkz. [zaman uyumsuz programlarda denetim akışı](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).

Zaman uyumsuz bir yöntem tarafından döndürülen bir görev, işlenmemiş bir özel durum nedeniyle tamamlanmadığını belirten hatalı bir durumda bitemeyebilir. Bir görev iptal edildi durumunda da bitebileceği için, await ifadesinin dışında bir `OperationCanceledException` oluşur. Her iki özel durum türünü yakalamak için, görevle ilişkili `Await` ifadesini bir `Try` bloğunda yerleştirin ve özel durumu `Catch` bloğunda yakalayın. Bu konunun ilerleyen kısımlarında bir örnek verilmiştir.

Bir görev hatalı bir durumda olabilir, çünkü hatalı bir şekilde birden çok özel durum sorumludur. Örneğin, görev bir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>çağrısının sonucu olabilir. Böyle bir görevi bekleyolduğunuzda, yakalanan özel durum yalnızca özel durumlardan biridir ve hangi özel durumun yakalanıp yakalanmayacak olduğunu tahmin edemeyecektir. Bu konunun ilerleyen kısımlarında bir örnek verilmiştir.

`Await` ifadesi `Catch` bloğu veya `Finally` bloğu içinde olamaz.

## <a name="iterators"></a>Yineleyiciler

Yineleyici işlevi veya `Get` erişimcisi bir koleksiyon üzerinde özel bir yineleme gerçekleştirir. Bir yineleyici, tek seferde koleksiyonun her bir öğesini döndürmek için bir [yield](yield-statement.md) ifadesini kullanır. Her biri Için bir kullanarak bir yineleyici işlevi çağırın [... Sonraki Ifade](for-each-next-statement.md).

`Yield` bir ifade `Try` bloğunun içinde olabilir. Bir `Yield` ifadesini içeren `Try` bloğu `Catch` bloklara sahip olabilir ve bir `Finally` bloğuna sahip olabilir. Bir örnek için [yineleyicilerin](../../programming-guide/concepts/iterators.md) "Visual Basic blokları dene" bölümüne bakın.

`Yield` bir ifade `Catch` bloğunun veya `Finally` bloğunun içinde olamaz.

`For Each` gövdesi (Yineleyici işlevi dışında) bir özel durum oluşturursa, yineleyici işlevindeki bir `Catch` bloğu yürütülmez, ancak Yineleyici işlevindeki bir `Finally` bloğu yürütülür. Yineleyici işlevi içindeki bir `Catch` bloğu yalnızca Yineleyici işlevinin içinde oluşan özel durumları yakalar.

## <a name="partial-trust-situations"></a>Kısmi güven durumları

Bir ağ paylaşımında barındırılan bir uygulama gibi kısmi güven durumlarında `Try...Catch...Finally`, çağrıyı içeren yöntemden önce oluşan güvenlik özel durumlarını yakalamaz. Aşağıdaki örnek, bir sunucu paylaşımında yerleştirip buradan çalıştırdığınızda "System. Security. SecurityException: Istek başarısız oldu" hatasını üretir. Güvenlik özel durumları hakkında daha fazla bilgi için <xref:System.Security.SecurityException> sınıfına bakın.

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

Böyle bir kısmi güven durumunda `Process.Start` ifadesini ayrı bir `Sub`yerleştirmeniz gerekir. `Sub` ilk çağrısı başarısız olur. Bu, `Try...Catch`, `Process.Start` içeren `Sub` ve güvenlik özel durumu üretilmadan önce yakalayıp yakalamayacağını sağlar.

## <a name="examples"></a>Örnekler

### <a name="the-structure-of-trycatchfinally"></a>TRY yapısı... Yakala... Son olarak

Aşağıdaki örnek `Try...Catch...Finally` deyimin yapısını gösterir.

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>Try bloğundan çağrılan bir yöntemde özel durum

Aşağıdaki örnekte `CreateException` yöntemi bir `NullReferenceException`oluşturur. Özel durumu üreten kod `Try` bloğunda değil. Bu nedenle `CreateException` yöntemi özel durumu işlemez. `CreateException` yöntemine yapılan çağrı bir `Try` bloğunda olduğundan `RunSample` yöntemi özel durumu işler.

Örnek, çok sayıda özel durum türü için en çok genel olarak sıralanmış `Catch` deyimlerini içerir.

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>Catch while ekstresi

Aşağıdaki örnek, bir `Catch When` deyiminin koşullu bir ifadeye filtre uygulamak için nasıl kullanılacağını gösterir. Koşullu ifade `True`olarak değerlendirilirse, `Catch` bloğundaki kod çalışır.

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>İç içe deneme deyimleri

Aşağıdaki örnek, bir `Try` bloğunda bulunan bir `Try…Catch` bildirimine sahiptir. İç `Catch` bloğu, `InnerException` özelliği özgün özel duruma ayarlanmış bir özel durum oluşturur. Dış `Catch` bloğu kendi özel durumunu ve iç özel durumu raporlar.

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>Zaman uyumsuz metotlar için özel durum işleme

Aşağıdaki örnek, zaman uyumsuz metotlar için özel durum işlemeyi gösterir. Zaman uyumsuz bir görev için geçerli olan bir özel durumu yakalamak için, `Await` ifadesi çağıranın `Try` bir bloğunda ve özel durum `Catch` bloğunda yakalanır.

Özel durum işlemeyi göstermek için örnekteki `Throw New Exception` satırının açıklamasını kaldırın. Özel durum `Catch` bloğunda yakalanmışsa, görevin `IsFaulted` özelliği `True`olarak ayarlanır ve görevin `Exception.InnerException` özelliği özel duruma ayarlanır.

Zaman uyumsuz bir işlemi iptal ettiğinizde ne olacağını göstermek için `Throw New OperationCancelledException` çizginin açıklamasını kaldırın. Özel durum `Catch` bloğunda yakalanır ve görevin `IsCanceled` özelliği `True`olarak ayarlanır. Ancak, bu örnek için geçerli olmayan bazı koşullar altında, `IsFaulted` `True` olarak ayarlanır ve `IsCanceled` `False`olarak ayarlanır.

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>Zaman uyumsuz metotlarda birden çok özel durumu işleme

Aşağıdaki örnekte, birden çok görevin birden çok özel durum ile sonuçlanbildiği özel durum işleme gösterilmektedir. `Try` bloğunun <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> döndürülen görev için `Await` ifadesi vardır. <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> uygulandığı üç görev tamamlandığında görev tamamlanır.

Üç görevin her biri özel duruma neden olur. `Catch` bloğu, `Task.WhenAll` döndürülen görevin `Exception.InnerExceptions` özelliğinde bulunan özel durumlar boyunca yinelenir.

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Exit Deyimi](exit-statement.md)
- [On Error Deyimi](on-error-statement.md)
- [Kod Parçacıkları İçin En İyi Uygulamalar](/visualstudio/ide/best-practices-for-using-code-snippets)
- [Özel Durum İşleme](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Throw Deyimi](throw-statement.md)
