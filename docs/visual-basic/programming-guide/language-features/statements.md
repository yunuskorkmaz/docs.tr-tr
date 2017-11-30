---
title: Visual Basic'deki Deyimler
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 210637105e54244ba829dabd73feab0b43ec7c6c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="statements-in-visual-basic"></a>Visual Basic'deki Deyimler
Bir deyimde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tam bir yönerge olması. Anahtar sözcükler, işleçler, değişkenleri, sabitleri ve ifadeleri içerebilir. Her deyimi aşağıdaki kategorilerde birine ait:  
  
-   **Bildirim deyimleri**, bu değişken, sabit veya yordam adı ve bir veri türü de belirtebilirsiniz.  
  
-   **Executable deyimleri**, Eylemler başlatın. Bu deyimler yöntemi veya işlev çağırabilir ve döngü veya kod bloklarını dal. Executable deyimleri dahil **atama deyimleri**, hangi atamak bir değer veya ifade bir değişken veya sabiti.  
  
 Bu konu, her kategori açıklar. Ayrıca, bu konuda tek bir satıra birden çok deyime birleştirmek ve bir deyim birden çok satır devam açıklar.  
  
## <a name="declaration-statements"></a>Bildirim Deyimleri  
 Bildirim deyimleri adlandırın ve yordamları, değişkenleri, özellikleri, dizileri ve sabitleri tanımlamak için kullanın. Bir programlama öğesi bildirirken veri türü, erişim düzeyi ve kapsam tanımlayabilirsiniz. Daha fazla bilgi için bkz: [bildirilen öğe özellikleri](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
 Aşağıdaki örnek, üç bildirimleri içerir.  
  
 [!code-vb[VbVbalrStatements#80](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_1.vb)]  
  
 İlk bildirimi `Sub` deyimi. Kendi eşleşen birlikte `End Sub` deyim, adlandırılmış bir yordam bildirir `applyFormat`. Ayrıca, belirtir `applyFormat` olan `Public`, yani başvurduğu herhangi bir kod da çağırabilirsiniz.  
  
 İkinci bildirimi `Const` sabiti bildirir deyimi `limit`, belirten `Integer` veri türü ve 33 değeri.  
  
 Üçüncü bildirimi `Dim` değişkeni bildirir deyimi `thisWidget`. Veri türü belirli bir nesne, nesnenin oluşturulduğu öğesine `Widget` sınıfı. Herhangi bir başlangıç veri türü veya kullanmakta olduğunuz uygulamada gösterilen herhangi bir nesne türünün olması için bir değişken bildirebilirsiniz.  
  
### <a name="initial-values"></a>İlk değerleri  
 Bir bildirim deyimi içeren kod çalıştığında, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bildirilen öğe için gerekli bellek ayırır. Öğe bir değer tutuyorsa [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kendi veri türü için varsayılan değere başlatır. Daha fazla bilgi için bkz: "Davranışı" [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
 Aşağıdaki örnekte gösterildiği gibi bildirimindeki bir parçası olarak bir değişken için bir başlangıç değeri atayabilirsiniz.  
  
 [!code-vb[VbVbalrStatements#81](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_2.vb)]  
  
 Bir değişken bir nesne değişkeni ise kullanarak bildirme zaman açıkça kendi sınıfının bir örneğini oluşturabilirsiniz [New işleci](../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğü, aşağıdaki örnek olarak gösterilmiştir.  
  
 [!code-vb[VbVbalrStatements#82](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_3.vb)]  
  
 Bildirim deyimi yürütme ulaşana kadar bildirimi deyiminde belirttiğiniz başlangıç değeri bir değişkene atanmadı unutmayın. O zamana kadar değişken veri türü için varsayılan değer içeriyor.  
  
## <a name="executable-statements"></a>Executable deyimleri  
 Bir yürütülebilir deyimi bir eylem gerçekleştirir. Kodda, birkaç deyimleri döngü başka bir yere dalının bir yordam çağırma veya bir ifade değerlendirme yükleyebilir. Bir atama deyimi yürütülebilir deyiminin özel bir durumdur.  
  
 Aşağıdaki örnek kullanan bir `If...Then...Else` kontrol farklı bir değişkeni değere göre kod bloklarını çalıştırmak için yapısı. Her bir bloğunda kodu, içinden bir `For...Next` döngü belirtilen kaç kez çalışır.  
  
 [!code-vb[VbVbalrStatements#83](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_4.vb)]  
  
 `If` Önceki örnekte deyimi denetler parametresinin değeri `clockwise`. Değer ise `True`, çağırır `spinClockwise` yöntemi `aWidget`. Değer ise `False`, çağırır `spinCounterClockwise` yöntemi `aWidget`. `If...Then...Else` Denetim yapısı bitip ile `End If`.  
  
 `For...Next` Döngü her bloğu içinde uygun yöntemini çağırır birkaç kez değerine eşit `revolutions` parametresi.  
  
## <a name="assignment-statements"></a>Atama deyimleri  
 Atama deyimleri atama işlecinin sağ tarafında değeri kabul oluşur atama işlemleri yürütmek (`=`) ve aşağıdaki örnekteki gibi sol taraftaki öğesindeki depolama.  
  
 [!code-vb[VbVbalrStatements#73](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_5.vb)]  
  
 Önceki örnekte atama deyimi değişkeni değişmez değeri 42 depolar `v`.  
  
### <a name="eligible-programming-elements"></a>Uygun programlama öğeleri  
 Atama işlecinin sol tarafındaki programlama öğesi kabul edin ve bir değeri depolamak kurabilmesi gerekir. Bu değişken veya olmayan özellik olmalıdır anlamına gelir [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), veya bir dizi öğesi olması gerekir. Bu tür bir öğe bazen olarak adlandırılan bir atama deyimi bağlamında bir *lvalue*, "sol değeri."  
  
 Atama işlecinin sağ tarafında değeri değişmez değerleri, sabitleri, değişkenleri, özellikleri, dizi öğeleri, diğer ifadeler veya işlev çağrıları herhangi bir birleşimini içerebilir bir ifade tarafından oluşturulur. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrStatements#74](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_6.vb)]  
  
 Önceki örnekte değişkende tutulan değeri ekler `y` değişkende tutulan değerine `z`ve işlev çağrısı tarafından döndürülen değer ekler `findResult`. Bu ifade toplam değerini sonra değişkeninde depolanan `x`.  
  
### <a name="data-types-in-assignment-statements"></a>Atama deyimleri veri türleri  
 Sayısal değerler yanı sıra atama işleci de atayabilirsiniz `String` değerlerini aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-vb[VbVbalrStatements#75](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_7.vb)]  
  
 Ayrıca atayabilirsiniz `Boolean` değerlerini kullanarak bir `Boolean` değişmez değer veya bir `Boolean` ifade, aşağıdaki örnek olarak gösterilmiştir.  
  
 [!code-vb[VbVbalrStatements#76](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_8.vb)]  
  
 Benzer şekilde, uygun değerleri programlama öğelerine atayabilirsiniz `Char`, `Date`, veya `Object` veri türü. Bu örneği oluşturulduğu sınıfı olarak bildirilen bir öğe için bir nesne örneği de atayabilirsiniz.  
  
### <a name="compound-assignment-statements"></a>Bileşik atama deyimleri  
 *Bileşik atama deyimleri* önce bir programlama öğesi atamadan önce bir ifade üzerinde bir işlemi gerçekleştirin. Aşağıdaki örnekte bu işleçlere birini gösterilmektedir `+=`, sağdaki ifadenin değerini işlecinin sol tarafındaki değişken değerini artırır.  
  
 [!code-vb[VbVbalrStatements#77](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_9.vb)]  
  
 Önceki örnekte 1 değerine ekler `n`ve ardından yeni değeri depolayan `n`. Bir toplu özelliktir aşağıdaki deyiminin eşdeğer:  
  
 [!code-vb[VbVbalrStatements#78](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_10.vb)]  
  
 Bileşik atama işlemleri, çeşitli, bu tür işleçleri kullanılarak gerçekleştirilebilir. Bu işleçlere ve bunlarla ilgili daha fazla bilgi listesi için bkz: [atama işleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md).  
  
 Birleştirme atama işleci (`&=`), mevcut sonuna bir dize eklemek için yararlıdır aşağıdaki örnekte gösterildiği gibi dizeleri.  
  
 [!code-vb[VbVbalrStatements#79](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_11.vb)]  
  
### <a name="type-conversions-in-assignment-statements"></a>Atama deyimleri tür dönüşümleri  
 Değer bir değişkeni, özelliği veya dizi öğesi ata o hedef öğeye uygun bir veri türünde olmalıdır. Genel olarak, hedef öğeyle aynı veri türü değeri üretmek denemelisiniz. Ancak, bazı türleri, atama sırasında diğer türlerine dönüştürülebilir.  
  
 Veri türleri arasında dönüştürme hakkında daha fazla bilgi için bkz: [Visual Basic'de tür dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md). Kısaca, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] otomatik olarak belirli bir türde bir değer widens, başka bir türüne dönüştürür. A *dönüştürme genişletme* olduğu her zaman çalışma zamanında başarılı ve herhangi bir veri kesintisi olmaması, birinde. Örneğin, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dönüştüren bir `Integer` değeri `Double` , çünkü uygun olduğunda `Integer` için widens `Double`. Daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 *Daraltma dönüşümleri* (olanlar değil genişletme) çalışma zamanında hata veya veri kaybı riski uygulayın. Tür dönüştürme işlevi kullanarak daraltma dönüşümü açıkça gerçekleştirebilir veya tüm dönüştürmeler örtük olarak ayarlayarak gerçekleştirmek için derleyici doğrudan `Option Strict Off`. Daha fazla bilgi için bkz: [dolaylı ve açık dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## <a name="putting-multiple-statements-on-one-line"></a>Tek bir satırda birden çok deyime koyma  
 Virgül ile ayrılmış tek bir satıra birden çok deyime olabilir (`:`) karakter. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrStatements#70](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_12.vb)]  
  
 Bazen kullanışlı olsa, bu formu sözdizimi kodunuzu okuyun ve korumak sabit yapar. Bu nedenle, bir satır için bir deyim tutmanız önerilir.  
  
## <a name="continuing-a-statement-over-multiple-lines"></a>Bir deyim birden çok satır etmeden  
 Bir deyim genellikle tek bir satırda uygun, ancak çok uzun olduğunda, bir alt çizgi karakteriyle bir boşluk oluşan bir satır devamlılığı sırası kullanılarak sonraki satıra üzerine devam edebilirsiniz (`_`) bir satır başı ve ardından. Aşağıdaki örnekte, `MsgBox` yürütülebilir deyimi üzerinde iki satır devam edilir.  
  
 [!code-vb[VbVbalrStatements#71](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_13.vb)]  
  
### <a name="implicit-line-continuation"></a>Örtük satır devamlılığı  
 Çoğu durumda, alt çizgi karakteri (_) kullanmadan bir deyim sonraki ardışık satırda devam edebilirsiniz. Aşağıdaki tabloda, kodun sonraki satırında örtük olarak continue deyimi sözdizimi öğeleri listeler.  
  
|Sözdizimi öğesi|Örnek|  
|---|---|  
|Virgül sonra (`,`).|[!code-vb[VbVbalrLineContinuation#1](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_14.vb)]|  
|Bir açma ayracı sonra (`(`) veya bu tarihten önce bir kapanış ayracı (`)`).|[!code-vb[VbVbalrLineContinuation#2](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_15.vb)]|  
|Bir açık kuşak sonra (`{`) veya bir kapanış kuşak önce (`}`).|[!code-vb[VbVbalrLineContinuation#3](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_16.vb)]<br /><br /> Daha fazla bilgi için bkz: [nesne başlatıcıları: adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) veya [koleksiyon başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
|Açık sonra katıştırılmış ifade (`<%=`) veya katıştırılmış bir ifade kapatma önce (`%>`) içinde bir XML değişmez değeri.|[!code-vb[VbVbalrLineContinuation#4](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_17.vb)]<br /><br /> Daha fazla bilgi için bkz: [XML'de katıştırılmış ifadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
|Birleştirme işleci sonra (`&`).|[!code-vb[VbVbcnConventions#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_18.vb)]<br /><br /> Daha fazla bilgi için bkz: [işleçleri listelenen işlevselliğe göre](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Atama İşleçleri sonra (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`).|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br /><br /> Daha fazla bilgi için bkz: [işleçleri listelenen işlevselliğe göre](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|İkili işleçler sonra (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) içinde bir ifade.|[!code-vb[VbVbalrLineContinuation#7](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_20.vb)]<br /><br /> Daha fazla bilgi için bkz: [işleçleri listelenen işlevselliğe göre](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Sonra `Is` ve `IsNot` işleçler.|[!code-vb[VbVbalrLineContinuation#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_21.vb)]<br /><br /> Daha fazla bilgi için bkz: [işleçleri listelenen işlevselliğe göre](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Üye niteleyicisi karakterinden sonraki (`.`) ve üye adından önce. Ancak, bir üye niteleyicisi karakter kullanırken aşağıdaki satır devamlılığı karakteri (_) içermelidir `With` deyimi veya bir tür için başlatma listesindeki değerlerin sağlama. Atama işleci sonra satır sonu göz önünde bulundurun (örneğin, `=`) kullanırken `With` deyimleri veya nesne başlatma listeler.|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br />[!code-vb[VbVbalrLineContinuation#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_22.vb)]<br /><br /> Daha fazla bilgi için bkz: [ile... End With deyimi](../../../visual-basic/language-reference/statements/with-end-with-statement.md) veya [nesne başlatıcıları: adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).|  
|XML eksen özelliği niteleyicisi sonra (`.` veya `.@` veya `...`). Ancak, kullanırken bir üye niteleyici belirttiğinizde satır devamlılığı karakteri (_) içermelidir `With` anahtar sözcüğü.|[!code-vb[VbVbalrLineContinuation#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_23.vb)]<br /><br /> Daha fazla bilgi için bkz: [XML eksen özellikleri](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).|  
|Daha az sonra-işareti (<) veya büyüktür önce-oturum'den (`>`) bir öznitelik belirttiğinizde. Ayrıca sonra bir büyük-oturum'den (`>`) bir öznitelik belirttiğinizde. Ancak, derleme düzeyi veya modül düzeyi öznitelikleri belirttiğinizde satır devamlılığı karakteri (_) içermelidir.|[!code-vb[VbVbalrLineContinuation#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_24.vb)]<br /><br /> Daha fazla bilgi için bkz: [öznitelikleri genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md).|  
|Önce ve sonra sorgu işleçleri (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, ve `Descending`). Birden çok anahtar sözcüklerini yapılan sorgu işleçleri anahtar arasında bir satır sonu olamaz (`Order By`, `Group Join`, `Take While`, ve `Skip While`).|[!code-vb[VbVbalrLineContinuation#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_25.vb)]<br /><br /> Daha fazla bilgi için bkz: [sorguları](../../../visual-basic/language-reference/queries/queries.md).|  
|Sonra `In` in anahtar sözcüğü bir `For Each` deyimi.|[!code-vb[VbVbalrLineContinuation#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_26.vb)]<br /><br /> Daha fazla bilgi için bkz: [For Each... Sonraki deyim](../../../visual-basic/language-reference/statements/for-each-next-statement.md).|  
|Sonra `From` koleksiyon Başlatıcısı anahtar sözcük.|[!code-vb[VbVbalrLineContinuation#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_27.vb)]<br /><br /> Daha fazla bilgi için bkz: [koleksiyon başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
  
## <a name="adding-comments"></a>Açıklama ekleme  
 Kaynak kodu her zaman bile yazdığı Programcı açıklayıcı değil. Kendi kodlarını belge yardımcı olmak için bu nedenle, çoğu programcıları katıştırılmış açıklamaları serbest kullanılmasını sağlamak. Kod açıklamaları bir yordam veya herkese okuma veya ile daha sonra çalışan belirli bir yönerge açıklanır. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]derleme sırasında açıklamaları yok sayar ve derlenen kod etkilemez.  
  
 Yorum Satırları tırnak işaretiyle başlayan (`'`) veya `REM` bir boşluk bırakarak. Bunlar herhangi bir yerde kodda dışında bir dizede eklenebilir. Bir deyim için bir açıklama eklemek için bir kesme işareti ekleme veya `REM` ve ardından yorumun deyimi sonra. Açıklamalar, kendi ayrı bir satırda de gidebilirsiniz. Aşağıdaki örnek, bu olanakları gösterir.  
  
 [!code-vb[VbVbalrStatements#72](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_28.vb)]  
  
## <a name="checking-compilation-errors"></a>Derleme hataları denetleniyor  
 Sonra bir kod satırı yazarsanız, satır (bir hata iletisi de görünebilir) dalgalı mavi alt çizgi ile görüntülenir, ifadede sözdizimi hatası var. (Görev listesinde arayan veya fare işaretçisini hatasıyla üzerine gelerek veya onları ve hata iletisi okuyarak) deyimiyle nerede olduğunu bulun ve düzeltin. Kodunuzda tüm sözdizimi hataları düzelttikten kadar programınızı doğru şekilde derlenmesi başarısız olur.  
  
## <a name="related-sections"></a>İlgili Bölümler  
  
|Terim|Tanım|  
|---|---|  
|[Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)|Atama İşleçleri gibi kapsayan dil başvurusu sayfalar için bağlantılar sağlar `=`, `*=`, ve `&=`.|  
|[İşleçler ve ifadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)|Yeni değerler verim işleçlerle öğeleri birleştirin gösterilmektedir.|  
|[Nasıl yapılır: kodda deyimleri bölme ve birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Tek bir deyimde birden çok çizgiye bölün ve aynı satıra birden çok deyime yerleştirin gösterir.|  
|[Nasıl yapılır: Etiket deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Bir kod satırı etiket kullanmayı gösterir.|
