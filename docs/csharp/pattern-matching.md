---
title: Desen eşleştirme C# Kılavuzu
description: C# ' ifadelerin eşleşen kalıbı hakkında bilgi edinin
ms.date: 01/24/2017
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: 7bdb41085a1a110f5a097ad3fa2cb645237fcefd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="pattern-matching"></a>Desen Eşleştirme #

Desenler test değerine belirli bir sahip *şekil*ve *ayıklamak* eşleşen şekil olduğunda değeri bilgileri. Desen eşleştirme zaten günümüzde kullandığınız algoritmalar için daha az sözdizimi sağlar. Zaten varolan sözdizimini kullanarak algoritmaları eşleşen kalıbı oluşturursunuz. Yazdığınız `if` veya `switch` test değerleri deyimleri. Ardından, bu deyimleri eşleştiğinde, ayıklayın ve bu değeri bilgileri kullanın. Yeni söz dizimi öğeleri, zaten aşina deyimleri uzantıları: `is` ve `switch`. Bu yeni uzantılar bir değer test etme ve bu bilgileri ayıklama birleştirin.

Bu konuda, biz nasıl okunabilir, kısa kod etkinleştirir göstermek için yeni sözdizimine göreceğiz. Desen eşleştirme burada veri ve kod, burada veri ve üzerlerinde değişiklik yöntemleri sıkı şekilde bağlı nesne yönelimli tasarımları ayrılır deyimleri sağlar.

Bu yeni deyimleri göstermek için şimdi deyimleri eşleşen kalıbı kullanarak geometrik şekiller temsil eden yapılar ile çalışır. Sınıf hiyerarşileri oluşturma ve oluşturma ile biliyor [sanal ve geçersiz kılınan yöntemleri](methods.md#inherited) nesne çalışma zamanı türüne göre nesne davranışını özelleştirebilirsiniz.

Bu teknikler sınıf hiyerarşisinde yapılandırılmaz veri mümkün değil. Veri ve yöntemleri farklı olduğunda, diğer araçlar gerekir. Yeni *desen eşleştirme* yapıları verileri incelemek ve bu verilerin herhangi bir koşula dayalı akış denetimi işlemek temizleyici sözdizimi etkinleştirin. Zaten yazma `if` deyimleri ve `switch` bir değişkenin değeri sınayın. Yazdığınız `is` bir değişken türü test deyimleri. *Desen eşleştirme* bu deyimleri için yeni özellikleri ekler.

Bu konuda, farklı geometrik şekiller alanını hesaplar bir yöntem yapı. Ancak, nesne yönelimli teknikleri yeniden ayırma ve farklı şekiller için sınıf hiyerarşisi oluşturmak olmadan gerçekleştirirsiniz.
Kullanacağınız *desen eşleştirme* yerine. Devralma kullanmıyorsanız, her şekli hale getireceğiz daha fazla vurgulamak için bir `struct` yerine bir sınıf. Bu farklı Not `struct` türleri, ortak bir kullanıcı tanımlı temel türü, böylece devralma olası tasarım belirtemezsiniz.
Bu örnek geçerken bu kodu nasıl, bir nesne hiyerarşisi yapılandırılmış olması ile karşılaştırın. Desen eşleştirme işlemek ve gereken sorgu veri sınıf hiyerarşisinin olmadığı durumlarda, çok Zarif tasarımları sağlar.

Bir Özet şekli tanımıyla başlatma ve farklı belirli şekil sınıfları ekleme yerine, bunun yerine basit verilerle tanımları geometrik şekillerin her biri için yalnızca başlayalım:

[!code-csharp[ShapeDefinitions](../../samples/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

Bu yapıları, bazı şekil alanı hesaplar bir yöntem yazalım.

## <a name="the-is-type-pattern-expression"></a>`is` Deseni ifadesi yazın

C# 7.0 önce her tür bir dizi test gerekir `if` ve `is` deyimleri:

[!code-csharp[ClassicIsExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

Yukarıdaki kod klasik bir ifade olduğunu *türü düzeni*: türünü ve bu türüne göre farklı bir eylem getirmeden belirlemek için bir değişken test ettiğiniz.

Bu kodu daha basit hale uzantıları kullanarak `is` ifadesi bir değişken IF test atamak için başarılı olur:

[!code-csharp[IsPatternExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

Bu güncelleştirilmiş sürüm `is` ifade değişkeni testleri hem uygun türde yeni bir değişkene atar. Ayrıca, bu sürüm içeren bildirim `Rectangle` türü olan bir `struct`. Yeni `is` ifadesi başvuru türleri yanı sıra değer türleri ile çalışır.

Desen eşleştirme ifadeler için dil kuralları bir eşleşme ifadesi sonuçlarını kötüye önlemenize yardımcı olur. Değişkenleri yukarıdaki örnekte `s`, `c`, ve `r` yalnızca kapsamındaki ve ilgili desen eşleşme ifadeleri olduğunda kesinlikle atanan `true` sonuçları. Başka bir konumda ya da değişken kullanmayı denerseniz, kodunuzu derleyici hataları oluşturur.

Ayrıntılı kapsam ile başlayarak, bu kuralların her ikisi de inceleyelim. Değişkeni `c` kapsamında olup yalnızca `else` ilk dalı `if` deyimi. Değişkeni `s` yöntemi kapsamında yer `ComputeArea`. Çünkü her dalı bir `if` deyimi değişkenleri için ayrı bir kapsam oluşturur. Ancak, `if` deyimi kendisini desteklemez. İçinde bildirilen değişkenlerin anlamına `if` deyimi aynı kapsamı olan `if` deyimi (Bu durumda yöntemi.) Bu davranış desen eşleştirme için özel değildir ancak değişken kapsamlar için tanımlanmış bir davranıştır ve `if` ve `else` deyimleri.

Değişkenleri `c` ve `s` ne zaman atanmış olan ilgili `if` deyimleri true nedeniyle kesinlikle atanan zaman true mekanizması.

> [!TIP]
> Bu konudaki örnekler önerilen yapı Desen eşleştirmesi kullanın `is` ifade kesinlikle eşleşme değişkeninde atar `true` dalı `if` deyimi.
> Mantığı tarafından bildiren tersine çevirebilir `if (!(shape is Square s))` değişkeni `s` kesinlikle yalnızca atanmış olur `false` dal. Bu geçerli bir C# olmakla birlikte, mantığı izlenecek daha karmaşık olduğu için önerilmez.

Bu kurallar bu desene karşılanmadığı yanlışlıkla bir desen eşleştirme ifadesi sonucu erişmeye olası anlamına gelir.

## <a name="using-pattern-matching-switch-statements"></a>Desen eşleştirme kullanılarak `switch` deyimleri

Zaman gibi diğer şekil türlerini desteklemek gerekebilir. Test ettiğiniz koşullar sayısı arttıkça, kullanmanın bulabilirsiniz `is` ifadeleri eşleşen kalıbı sıkıcı dönüşebilir. Gerektiren ek olarak `if` denetlemek istediğiniz her türündeki deyimleri `is` ifadeleri giriş tek bir türü eşleşirse test sınırlıdır. Bu durumda, bulacaksınız `switch` desen eşleştirme ifadeleri daha iyi bir seçim haline gelir. 

Geleneksel `switch` deyimi olan bir desen ifadesini: sabit düzeni desteklenir.
Kullanılan sabit bir değişkene karşılaştırmak bir `case` deyimi:

[!code-csharp[ClassicSwitch](../../samples/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

Tarafından desteklenen tek düzeni `switch` deyimi sabit düzeni oluştu. Daha fazla sınırlı sayısal türler oluştu ve `string` türü.
Bu kısıtlamaları kaldırıldı ve artık yazabilirsiniz bir `switch` türü desenini kullanarak deyimi:

[!code-csharp[Switch Type Pattern](../../samples/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

Desen eşleştirme `switch` deyimini kullanan geleneksel C tarzı kullanmış olan geliştiricilere bilinen sözdizimini `switch` deyimi. Her `case` değerlendirilir ve kod giriş değişkeni eşleşen koşul altında yürütülür. Kod yürütmeyi "bir servis talebi ifadesinden sonraki geçemez"; söz dizimi `case` deyimi gerektirir, her `case` sonunda bir `break`, `return`, veya `goto`.

> [!NOTE]
> `goto` Başka bir etiket için atlamak için deyimleri yalnızca sabit düzeni için Klasik switch deyimi geçerli.

Yöneten önemli yeni kurallar vardır `switch` deyimi. Değişken türü kısıtlamalar `switch` ifadesi kaldırıldı.
Gibi herhangi türdeki `object` Bu örnekte, kullanılabilir. Case ifadeleri artık sabit değerleri için sınırlı değildir. Bu sınırlama kaldırılması anlamına gelir, yeniden sıralama `switch` bölümler, programın davranışını değişebilir.

Birden fazla sabit değerleri için sınırlı olduğunda `case` etiket değeri eşleşebilecek `switch` ifade. Kuralla birleştirmek, her `switch` bölüm gerekir değil atlayabilir sonraki bölüme ve, ardından `switch` bölümleri düzenlenmeyecek herhangi bir sırada davranışı etkilemeden.
Şimdi, genelleştirilmiş daha fazla ile `switch` ifadeleri, her bölüm sırası önemlidir. `switch` İfadeleri metinsel sırayla değerlendirilir. Yürütme aktarır ilk `switch` eşleşen etiket `switch` ifade.  
Unutmayın `default` durumda, yalnızca diğer durum etiketi eşleşiyorsa yürütülür. `default` Durumda son olarak, kendi metinsel sipariş bağımsız olarak değerlendirildi. Varsa hiçbir `default` çalışması ve diğer hiçbiri `case` deyimleri eşleşmesi, deyimi aşağıdaki yürütülmeye `switch` deyimi. Hiçbiri `case` etiketleri kod gerçekleştirilir.

## <a name="when-clauses-in-case-expressions"></a>`when` yan tümcelerinde `case` ifadeleri

Özel durumlar kullanarak 0 alanı olan bu şekiller için yapabileceğiniz bir `when` yan tümcesi `case` etiketi. Bir kare yan uzunluğu 0 ile ya da RADIUS 0 olan bir daire 0 bir alana sahip. Bu koşul kullanarak belirttiğiniz bir `when` yan tümcesi `case` etiketi:  

[!code-csharp[ComputeDegenerateShapes](../../samples/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

Bu değişiklik birkaç önemli noktaları yeni söz dizimi hakkında gösterir. İlk olarak, çoklu `case` etiketleri için uygulanabilir `switch` bölümü. İfade bloğu yürütülen etiketlerin hiçbirinde olduğunda `true`. Bu örnekte, `switch` ifadesi bir daire veya kare 0 alan ile yöntem sabiti 0 döndürür.

Bu örnek iki iki farklı değişkenleri tanıtır `case` ilk kez etiketleri `switch` bloğu. Dikkat bu deyimlerinde `switch` bloğu ya da değişkenleri kullanmayın `c` (için daire) veya `s` (için kare).
Bu değişkenleri hiçbiri kesinlikle bu atanan `switch` bloğu.
Bu durumların herhangi birini eşleşiyorsa değişkenleri açıkça birini atanmıştır.
Ancak, bildirmek mümkün değildir *hangi* derleme zamanında, her iki durumda çalışma zamanında eşleştiğinden atanmıştır. Bu nedenle, çoğu kez kullandığınızda, birden çok `case` etiketleri aynı bloğu için yeni bir değişkende tanıtmak olmaz `case` deyimi veya yalnızca kullanacağınız değişkende `when` yan tümcesi.

Bu şekiller 0 alan ile eklenir birkaç daha fazla şekil türleri ekleyelim: dikdörtgen ve bir üçgen:

[!code-csharp[AddRectangleAndTriangle](../../samples/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 Bu değişiklik kümesini ekler `case` bozuk durumda, etiketleri ve etiketleri ve her yeni şekiller blokları. 

Son olarak, ekleyebileceğiniz bir `null` bağımsız değişken değil emin olmak için durum `null`:

[!code-csharp[NullCase](../../samples/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

İçin özel bir davranış `null` düzeni ilginç çünkü sabiti `null` desende bir türe sahip değil, ancak herhangi bir başvuru türü veya boş değer atanabilir tür dönüştürülebilir. Yerine Dönüştür bir `null` herhangi bir türü için dili tanımlayan bir `null` değer değişkenin derleme zamanı türünden bağımsız olarak herhangi bir tür modeliyle eşleşmez. Bu davranış yeni yapar `switch` türü desenine ile tutarlı `is` deyimi: `is` deyimleri her zaman geri `false` denetlenen değer olduğunda `null`. Ayrıca basittir: türü işaretlendiğinde, ek bir null denetimi gerekmez. Hiçbir null bulunmasına yukarıdaki örnekleri servis talebi bloklarını hiçbirinde denetler görebilirsiniz: boş olmayan bir değer türü desen eşleştirme garanti beri gerekli değildir.

## <a name="var-declarations-in-case-expressions"></a>`var` bildirimlerinde `case` ifadeleri

Giriş `var` gibi bir eşleşme ifadeleri desen eşleştirme yeni kurallar tanıtır.

İlk kural olan `var` bildirimini normal türü çıkarım kuralları izler: türü anahtar ifadesi statik türünde olmasını algılanır. Bu kuraldan türü her zaman eşleşir.

İkinci kuralı olan bir `var` bildirimi diğer tür düzeni ifadeler içeren null denetimi sahip değil. Bu değişken null olabilir ve bu durumda null denetimi gereklidir anlamına gelir.

Bu iki kural çoğu durumda, diğer bir deyişle bir `var` bildiriminde bir `case` ifadeyle eşleşen aynı koşullarda bir `default` ifade.
Herhangi bir varsayılan olmayan durumu için tercih edilen olduğundan `default` durumda `default` durumu hiçbir zaman yürütülecek.

> [!NOTE]
> Derleyici Uyarısı bu durumlarda yayma değil burada bir `default` durumda yazıldı, ancak hiçbir zaman yürütülür. Bu tutarlıdır geçerli `switch` burada tüm olası durumların listelenen deyimi davranışı.

Üçüncü kural kullanır tanıtır burada bir `var` durumda yararlı olabilir. Burada, Giriş bir dize ve bilinen komut değerlerini aradığınız bir desen eşleştirmesi yaptıklarını düşünün. Şöyle yazabilirsiniz:

[!code-csharp[VarCaseExpression](../../samples/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

`var` Durumda eşleşmeleri `null`, boş dize veya yalnızca boşluk içeriyor herhangi bir dize. Önceki kod kullanan bildirimi `?.` onu değil yanlışlıkla throw emin olmak için işleci bir <xref:System.NullReferenceException>. `default` Durumunu işler bu komutu ayrıştırıcı tarafından anlaşılmayan herhangi bir dize değeri.

Bu bir yere göz önünde bulundurun isteyebilirsiniz örnektir bir `var` durumda farklıdır ifade bir `default` ifade.

## <a name="conclusions"></a>Sonuçları

*Desen eşleştirme yapıları* denetim akışı farklı değişkenleri ve devralma hiyerarşisi tarafından ilgili olmayan türleri arasında kolayca yönetmenize olanak sağlar. Değişkeni test herhangi bir koşul kullanmak için mantığı de denetleyebilirsiniz. Desenleri ve veri ve bu verileri işlemek yöntemleri ayrı nerede daha dağıtılmış uygulamalar oluşturmak daha sık gerekir deyimleri sağlar. Bu örnekte kullanılan şekli yapılar herhangi bir yöntem içermiyor fark edeceksiniz yalnızca salt okunur özellikler.
Desen eşleştirme herhangi bir veri türü ile çalışır. Nesne inceleyin ifadeleri yazmak ve bu koşullara göre denetim akışı kararlar.

Bu örnek için bir Özet sınıf hiyerarşisi oluşturma izlersiniz tasarım ile koddan karşılaştırmak `Shape` ve türetilmiş özel şekiller her alanını hesaplamak için sanal bir yöntem, kendi uygulama. Desen eşleştirme ifadeleri verilerle çalışmak ve veri depolama sorunları davranışı kaygılarını ayırmak istediğiniz zaman çok kullanışlı bir aracı olabilir genellikle bulabilirsiniz.

