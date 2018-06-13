---
title: Try...Catch...Finally Deyimi (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 5e7037d1f89d56d1c65fe94e7c5fbafc7b3c40f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605491"
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally Deyimi (Visual Basic)
Belirli bir kod bloğu içinde hala kod çalıştırılırken ortaya çıkabilecek bazı veya tüm olası hataları işlemek için bir yol sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`Catch`|İsteğe bağlı. Birden çok `Catch` izin engeller. Bir özel durum işleme sırasında oluşursa `Try` engellemek, her `Catch` deyimi, özel durum ile işleme olup olmadığını belirlemek için metinsel sırayla incelenir `exception` oluşturuldu özel durumu temsil eden.|  
|`exception`|İsteğe bağlı. Herhangi bir değişken adı. Başlangıç değeri `exception` atılmış hata değeri. İle kullanılan `Catch` hata belirtmek için yakalandı. Atlanırsa, `Catch` deyimi özel durumları yakalar.|  
|`type`|İsteğe bağlı. Sınıf filtre türünü belirtir. Varsa değerini `exception` tarafından belirtilen türde `type` veya türetilmiş bir tür tanımlayıcı için özel durum nesnesi bağlı olur.|  
|`When`|İsteğe bağlı. A `Catch` deyimiyle bir `When` yan tümcesi özel durumları yakalar yalnızca `expression` değerlendiren `True`. A `When` yan tümcesi, yalnızca özel durum türünü denetledikten sonra uygulanır ve `expression` özel durumu temsil eden tanımlayıcı başvurabilir.|  
|`expression`|İsteğe bağlı. Örtük olarak dönüştürülebilir olmalıdır `Boolean`. Genel filtre açıklar herhangi bir ifade. Genellikle, hata numarasına göre filtre uygulamak için kullanılır. İle kullanılan `When` koşullar altında hata belirledi belirtmek için anahtar sözcüğü.|  
|`catchStatements`|İsteğe bağlı. Deyim ilişkili oluşan hataları işlemek için `Try` bloğu. Bileşik deyim olabilir.|  
|`Exit Try`|İsteğe bağlı. İşyeri dışında keser anahtar sözcüğü `Try...Catch...Finally` yapısı. Yürütme hemen koduyla sürdürür `End Try` deyimi. `Finally` Deyimi hala yürütülür. İçinde izin verilmiyor `Finally` engeller.|  
|`Finally`|İsteğe bağlı. A `Finally` blok yürütme herhangi bir kısmını ayrıldığında her zaman yürütülür `Try...Catch` deyimi.|  
|`finallyStatements`|İsteğe bağlı. Tüm diğer işlenirken hata gerçekleştikten sonra yürütülür deyim.|  
|`End Try`|Sonlandırır `Try...Catch...Finally` yapısı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Belirli bir özel durum kodu belirli bir bölümü sırasında oluşabilecek bekliyorsanız, kod yerleştirecek bir `Try` engelleme ve kullanmak bir `Catch` denetimi korumak ve bu durum oluşursa özel durumu işlemek için blok.  
  
 A `Try…Catch` deyimi oluşur bir `Try` blok izlenen bir veya daha fazla tarafından `Catch` yan tümceleri çeşitli özel durumlar için işleyiciler belirleyin. Ne zaman özel durum bir `Try` engellemek, Visual Basic arar `Catch` özel durumu işler deyimi. Eşleşen bir varsa `Catch` deyimi bulunamadı, Visual Basic geçerli yöntemi, vb. çağrı yığını çağrılan yöntemi inceler. Öyle değilse `Catch` blok bulunursa, Visual Basic kullanıcı için bir işlenmeyen özel durum iletisi görüntülenir ve programın yürütülmesi durdurulur.  
  
 Birden fazla kullanabilirsiniz `Catch` deyiminde bir `Try…Catch` deyimi. Bu sırasını yaparsanız `Catch` yan tümceleri olduğundan önemli sırayla incelenir. Daha fazla özel durum daha az yayına önce yakalar.  
  
 Aşağıdaki `Catch` deyimi koşullar az özgüdür ve tüm yakalar öğesinden türetilen özel durumları <xref:System.Exception> sınıfı. Normalde bu değişimler birini son kullanmalıdır `Catch` engelleyin `Try...Catch...Finally` beklediğiniz tüm belirli özel durumları yakalama sonra yapısı. Denetim akışı hiçbir zaman ulaşmak bir `Catch` ya da bu değişimler izler bloğu.  
  
-   `type` Olan `Exception`, örneğin: `Catch ex As Exception`  
  
-   Deyim sahip olmayan `exception` değişken, örneğin: `Catch`  
  
 Zaman bir `Try…Catch…Finally` deyimi iç içe başka bir programda `Try` bloğu, Visual Basic önce inceler her `Catch` ise en içteki deyiminde `Try` bloğu. Eşleşme varsa `Catch` deyimi bulunursa, aramaya devam eder `Catch` bilgilerinin dış `Try…Catch…Finally` bloğu.  
  
 Yerel değişkenler arasından bir `Try` blok kullanılabilir olmayan bir `Catch` ayrı blokları olduklarından engelleyin. Birden fazla bloğu içinde bir değişken kullanmak istiyorsanız, dışında değişkeni bildirme `Try...Catch...Finally` yapısı.  
  
> [!TIP]
>  `Try…Catch…Finally` Deyimi bir IntelliSense kod parçacığı olarak kullanılabilir. Kod parçacıkları Yöneticisi'nde **kod düzenleri - varsa, her biri için Try Catch, özellik, vb.** ve ardından **hata işleme (özel durumlar)**. Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="finally-block"></a>Finally bloğu  
 Çıkmadan önce çalıştırmanız gereken bir veya daha fazla deyimleri varsa `Try` yapısı, kullanan bir `Finally` bloğu. Denetim geçtiği `Finally` yalnızca dışı geçirmeden önce engelle `Try…Catch` yapısı. İçinde herhangi bir yerden bir özel durum oluştuğunda dahi, bu durum geçerlidir `Try` yapısı.  
  
 A `Finally` blok, bir özel durum olsa bile, herhangi bir kod çalıştırmasını yürütmeniz gerekir için yararlıdır. Denetim iletilir `Finally` bağımsız olarak nasıl blok `Try...Catch` engelleme çıkar.  
  
 Kodda bir `Finally` kodunuzu karşılaşırsa bile çalışır engelleme bir `Return` deyiminde bir `Try` veya `Catch` bloğu. Denetim gelen geçirmek olmayan bir `Try` veya `Catch` engelleme karşılık gelen `Finally` aşağıdaki durumlarda engelle:  
  
-   Bir [End deyimi](../../../visual-basic/language-reference/statements/end-statement.md) içinde karşılaştı `Try` veya `Catch` bloğu.  
  
-   A <xref:System.StackOverflowException> durum oluşur `Try` veya `Catch` bloğu.  
  
 Açıkça yürütme içine aktarmak için geçerli değil bir `Finally` bloğu. Yürütülmesi dışarı aktarma bir `Finally` blok bir özel durum geçerli değil, dışında.  
  
 Varsa bir `Try` deyimi en az bir içermiyor `Catch` bloğu içermesi gereken bir `Finally` bloğu.  
  
> [!TIP]
>  Özel durumları yakalamak yoksa `Using` deyimi davranır gibi bir `Try…Finally` bloğu ve blok çıkmak nasıl bakılmaksızın kaynakların garanti elden. İşlenmeyen bir özel durumla bile bu geçerlidir. Daha fazla bilgi için bkz: [kullanarak deyimi](../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="exception-argument"></a>Özel durum bağımsız değişken  
 `Catch` Blok `exception` bağımsız değişkeni bir örneğidir <xref:System.Exception> sınıf veya türeyen bir sınıf `Exception` sınıfı. `Exception` Karşılık gelen sınıf örneği oluştu hata `Try` bloğu.  
  
 Özelliklerini `Exception` nesne neden ve bir özel durum konumunu belirlemek için Yardım. Örneğin, <xref:System.Exception.StackTrace%2A> özelliği için kod hatanın oluştuğu bulmanıza yardımcı olacak özel neden çağrılan yöntemler listeler. <xref:System.Exception.Message%2A> özel durumu açıklayan bir ileti döndürür. <xref:System.Exception.HelpLink%2A> bir bağlantı için ilişkili bir Yardım dosyası döndürür. <xref:System.Exception.InnerException%2A> döndürür `Exception` veya geçerli özel durumun nedeni nesnesi döndüren `Nothing` hiçbir özgün ise `Exception`.  
  
## <a name="considerations-when-using-a-trycatch-statement"></a>Try kullanmayla ilgili konular... Catch deyimi  
 Kullanım bir `Try…Catch` deyimi yalnızca olağan dışı ya da beklenmeyen program olayları oluşumunu sinyal. Bunun nedeni şunlardır:  
  
-   Çalışma zamanında özel durumları yakalama ek yükü oluşturur ve özel durumları önlemek için önceden denetimi daha yavaş olması olasıdır.  
  
-   Varsa bir `Catch` blok doğru şekilde işlenmez, özel durum kullanıcılara doğru bildirmemiş.  
  
-   Özel durum işleme bir programı daha karmaşık hale getirir.  
  
 Her zaman ihtiyacınız olmayan bir `Try…Catch` deyimi oluştuğu için bir koşul denetleyin. Aşağıdaki örnek, bir dosyayı açmaya denemeden önce mevcut olup olmadığını denetler. Bu tarafından oluşturulan bir özel durum yakalama gereksinimini azaltır <xref:System.IO.File.OpenText%2A> yöntemi.  
  
 [!code-vb[VbVbalrStatements#94](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_1.vb)]  
  
 Bu kodu olun `Catch` blokları düzgün raporlama yapabilir, kullanıcılara özel durumları iş parçacığı günlüğü veya uygun iletileri üzerinden. Aksi takdirde, özel durumlar bilinmeyen kalabilir.  
  
## <a name="async-methods"></a>Zaman uyumsuz yöntemleri  
 Bir yöntem ile işaretlerseniz [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md) kullanabileceğiniz değiştiricisi, [bekleme](../../../visual-basic/language-reference/operators/await-operator.md) yönteminde işleci. With deyimi `Await` işleci awaited görevi tamamlanana kadar yönteminin yürütülmesi askıya alır. Görev devam eden iş temsil eder. Zaman ile ilişkili görevi `Await` işleci tamamlandıktan, aynı yönteminde yürütme sürdürür. Daha fazla bilgi için bkz: [zaman uyumsuz programlarda denetim akışı](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
 Zaman uyumsuz yöntem tarafından döndürülen bir görev, işlenmeyen bir özel durum nedeniyle tamamlandı belirten bir hatalı durumda bitebilir. Bir görev ayrıca sonuçlanan bir iptal edilmiş durumda sonuna bir `OperationCanceledException` bekleme ifade dışında oluşturulan. Özel durum iki tür çekmek için koyun `Await` görevde ile ilişkili ifade bir `Try` engelleme ve catch özel durum `Catch` blok. Bir örnek, bu konunun ilerleyen bölümlerinde sağlanmıştır.  
  
 Birden çok özel durum, hatalı için sorumlu için bir görev hatalı bir durumda olabilir. Örneğin, görev için bir çağrı sonucunu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Bu tür bir görev await, yakalanan özel durum yalnızca özel durumlar biridir ve hangi özel durumu yakalandı tahmin edilemez. Bir örnek, bu konunun ilerleyen bölümlerinde sağlanmıştır.  
  
 Bir `Await` ifade içinde olamaz bir `Catch` blok veya `Finally` bloğu.  
  
## <a name="iterators"></a>Yineleyiciler  
 Yineleyici işlevi veya `Get` erişimci gerçekleştiren özel bir yineleme içinde bir koleksiyon. Yineleyici kullanan bir [verim](../../../visual-basic/language-reference/statements/yield-statement.md) deyimi her birer birer koleksiyonun bir öğesi döndürür. Kullanarak bir yineleyici işlevi çağırmak bir [For Each... Sonraki deyim](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 A `Yield` deyimi içinde bulunabilir bir `Try` bloğu. A `Try` içeren blok bir `Yield` deyimi olabilir `Catch` engeller ve olabilir bir `Finally` bloğu. "Deneyin blokları Visual Basic" bölümüne bakın [yineleyiciler](../../programming-guide/concepts/iterators.md) bir örnek.  
  
 A `Yield` deyimi içinde olamaz bir `Catch` blok veya `Finally` bloğu.  
  
 Varsa `For Each` gövdesi (dışında yineleyici işlevi) bir özel durum oluşturur bir `Catch` yineleyici işlevi bloğunda yürütülmez, ancak bir `Finally` yineleyici işlevi bloğunda gerçekleştirilir. A `Catch` yineleyici işlevi bloğunda yineleyici işlevinin içinde oluşan özel durumlarını yakalar.  
  
## <a name="partial-trust-situations"></a>Kısmi güven durumları  
 Kısmi güven durumlarda, bir ağ paylaşımında barındırılan bir uygulama gibi `Try...Catch...Finally` çağrı içeren yöntemi çağrılmadan önce oluşan güvenlik özel durumları yakalamaz. Aşağıdaki örnek, onu bir sunucu paylaşımı ve Çalıştır buradan geçirdiğinizde, hata üretir "System.Security.SecurityException: isteği başarısız oldu." Güvenlik özel durumları hakkında daha fazla bilgi için bkz: <xref:System.Security.SecurityException> sınıfı.  
  
 [!code-vb[VbVbalrStatements#85](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_2.vb)]  
  
 Böyle bir kısmi güven durumda, yerine koymak zorunda `Process.Start` ayrı bir deyimde `Sub`. İlk çağrısı `Sub` başarısız olur. Böylece `Try...Catch` önce yakalamak için `Sub` içeren `Process.Start` başlatılır ve güvenlik özel durum üretti.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yapısını gösterilmektedir `Try...Catch...Finally` deyimi.  
  
 [!code-vb[VbVbalrStatements#86](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `CreateException` yöntemi atar bir `NullReferenceException`. Özel durum oluşturur kodu kullanımda olmayan bir `Try` bloğu. Bu nedenle, `CreateException` yöntemi özel durum işlemez. `RunSample` Olduğundan, yöntemi özel durum işleme çağrısı `CreateException` yöntemi olan bir `Try` bloğu.  
  
 Örnek içerir `Catch` deyimleri için özel durumlar, çeşitli türlerde sıralı en belirli en genel.  
  
 [!code-vb[VbVbalrStatements#91](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_4.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösteren bir `Catch When` koşullu bir deyime filtre ifadesi. Koşullu ifade değerlendirilirse `True`, kodda `Catch` engelleme çalıştırır.  
  
 [!code-vb[VbVbalrStatements#92](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_5.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sahip bir `Try…Catch` bulunan deyimi bir `Try` bloğu. İç `Catch` blok sahip bir özel durum oluşturur, `InnerException` özelliği için orijinal özel durumu için ayarlanmış. Dış `Catch` blok raporlarını kendi özel ve iç özel durum.  
  
 [!code-vb[VbVbalrStatements#93](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_6.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özel durum işleme için zaman uyumsuz yöntemleri gösterilmektedir. Bir zaman uyumsuz görev için geçerli bir özel durum yakalamak için `Await` ifade konusu bir `Try` bloğunu çağıran ve özel durum yakalandı içinde `Catch` bloğu.  
  
 Açıklamadan çıkarın `Throw New Exception` özel durum işleme göstermek için örnekte satır. Özel durumun yakalandığı `Catch` engellemek, görevin `IsFaulted` özelliği ayarlanmış `True`ve görevin `Exception.InnerException` özelliği, özel durumu ayarlanır.  
  
 Açıklamadan çıkarın `Throw New OperationCancelledException` satır zaman uyumsuz bir işlem iptal ettiğinizde ne olacağını gösterir. Özel durumun yakalandığı `Catch` bloğu ve görevin `IsCanceled` özelliği ayarlanmış `True`. Ancak, bu örnek için uygulama bazı koşullar altında `IsFaulted` ayarlanır `True` ve `IsCanceled` ayarlanır `False`.  
  
 [!code-vb[csAsyncExceptions#1](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_7.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birden çok görev birden çok özel durumları burada sonuçlanabilir özel durum işleme gösterilmektedir. `Try` Bloğu `Await` ifade görev için <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> döndürdü. Üç için görevleri, görev tamamlandığında <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> uygulanan tamamlandığından.  
  
 Her biri üç görev bir özel durum oluşur. `Catch` Blok tekrarlanan bulunan özel durumlar aracılığıyla `Exception.InnerExceptions` görev özelliği, `Task.WhenAll` döndürdü.  
  
 [!code-vb[csAsyncExceptions#3](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_8.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:System.Exception>  
 [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [On Error Deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Kod Parçacıkları İçin En İyi Uygulamalar](/visualstudio/ide/best-practices-for-using-code-snippets)  
 [Özel Durum İşleme](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)  
 [Throw Deyimi](../../../visual-basic/language-reference/statements/throw-statement.md)
