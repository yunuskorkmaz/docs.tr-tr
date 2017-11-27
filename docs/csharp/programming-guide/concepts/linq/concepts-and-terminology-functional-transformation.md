---
title: "Kavramları ve terminolojiyi (işlev dönüştürme) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 03defb3a-7e17-4ab1-8efa-4dd66621e860
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c62aadc84f9c62429ffe59b78de386aac0f5cf63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="concepts-and-terminology-functional-transformation-c"></a>Kavramları ve terminolojiyi (işlev dönüştürme) (C#)
Bu konu, kavramları ve terminolojiyi saf işlevsel Dönüşümlerin tanıtır. Veri dönüştürme işlev dönüştürme yaklaşım program, daha açıklayıcı ve daha kolay hata ayıklama ve sürdürmek daha geleneksel, kesinlik temelli programlama için genellikle hızlıdır kodunu üretir.  
  
 Bu bölümdeki konular, tam olarak işlevsel programlama açıklamak için amaçlanmamıştır unutmayın. Bunun yerine, bu konularda bazı XML bir şekle Dönüştür kolaylaştırmak işlevsel programlama özelliklerini tanımlayın.  
  
## <a name="what-is-pure-functional-transformation"></a>Saf işlev dönüştürme nedir?  
 İçinde *saf işlev dönüştürme*, çağrılan işlevler kümesi *saf işlevleri*, özgün formuna yapılandırılmış veri kümesi başka bir biçime dönüştürmek nasıl tanımlayın. "Saf" word işlevleri gösterir *birleştirilebilir*, olmalarını gerektirir:  
  
-   *Kendi içinde bulunan*, böylece bunlar kullanılabilir ücretsiz olarak sipariş ve entanglement veya program kalanıyla bağımlılıklarını olmadan düzenlenmeyecek. Saf dönüşümleri hiçbir bilgisi veya ortamlarına üzerinde etkisi vardır. Diğer bir deyişle, dönüşümünde işlevleri yok *yan etkileri*.  
  
-   *Durum bilgisiz*, böylece aynı işlev veya işlev belirli kümesi aynı giriş, yürütülen her zaman aynı çıktısında neden olur. Saf dönüşümleri önceki kullanım hiçbir bellek yok.  
  
> [!IMPORTANT]
>  Bu öğreticinin geri kalanını içinde "saf işlev" terimi genel anlamda programlama bir yaklaşım ve belirli bir dil özelliği belirtmek için kullanılır.  
>   
>  Saf işlevleri C# yöntemi olarak uygulanmalıdır unutmayın.  
>   
>  Ayrıca, saf işlevleri C++ saf sanal yöntemlerle karıştırmamalısınız. İkinci içeren Sınıf soyut ve hiçbir yöntem gövdesi sağlanan gösterir.  
  
### <a name="functional-programming"></a>İşlevsel programlama  
 *İşlevsel programlama* saf işlev dönüştürme doğrudan destekleyen programlama bir yaklaşımdır.  
  
 Tarihsel olarak, genel amaçlı işlevsel gibi programlama dilleri, ML, şema, Haskell ve F #'ta, öncelikle akademik topluluk ilgi olmuştur. Bu her zaman C# ' ta saf işlevsel dönüşümleri yazmaya mümkün olsa da, bunun zorluk bu nedenle, çoğu programcıları için çekici bir seçenek yapılmadı. Lambda ifadeleri ve tür çıkarımı işlevsel programlama çok daha kolay ve daha üretken kolaylaştırır gibi son sürümlerinde C#, ancak yeni dil oluşturur.  
  
 İşlevsel programlama hakkında daha fazla bilgi için bkz: [işlevsel Programlama vs. Kesinlik temelli programlama (C#)](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).  
  
#### <a name="domain-specific-fp-languages"></a>Etki alanına özgü FP dilleri  
 Genel işlevsel programlama dilleri yaygın uyarlanmıştır değil de, belirli etki alanına özgü işlevsel programlama dilleri daha iyi başarı beklendiğinden. Örneğin, geçişli stil sayfaları (CSS) birçok Web sayfalarının Görünüm ve yapısını belirlemek için kullanılır ve Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) stil sayfaları, XML veri işleme yaygın olarak kullanılır. XSLT hakkında daha fazla bilgi için bkz: [XSLT dönüştürmeleri](../../../../standard/data/xml/xslt-transformations.md).  
  
## <a name="terminology"></a>Terminoloji  
 Aşağıdaki tabloda işlevsel dönüşümleri ilgili bazı koşullarını tanımlar.  
  
 daha yüksek sıralı (birinci sınıf) işlevi  
 Programlama nesnesi olarak kabul bir işlev. Örneğin, daha yüksek sıralı işlevi geçirilen veya diğer işlevleri döndürdü. C'de #c, temsilciler ve lambda ifadeleri daha yüksek sıralı işlevlerini destekleyen dil özellikleridir. Daha yüksek sıralı işlevi yazmak için temsilciler almak için bir veya daha fazla bağımsız değişken bildirme ve genellikle lambda ifadeleri, çağrılırken kullanılır. Standart sorgu işleçleri birçoğu, daha yüksek sıralı işlevlerdir.  
  
 Daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 lambda ifadesi  
 Bir temsilci türü bekleniyor her yerde kullanılabilir esas olarak, bir satır içi anonim işlev. Bu bir lambda ifadeleri Basitleştirilmiş tanımıdır, ancak bu öğreticinin amaçları doğrultusunda yeterli.  
  
 Hakkında daha fazla bilgi için bkz: [Lambda ifadeleri](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 koleksiyon  
 Veri, genellikle bir Tekdüzen türü yapılandırılmış kümesi. LINQ ile uyumlu olacak şekilde bir koleksiyon uygulamalıdır <xref:System.Collections.IEnumerable> arabirimi veya <xref:System.Linq.IQueryable> arabirimi (veya genel dekiler <xref:System.Collections.Generic.IEnumerator%601> veya <xref:System.Linq.IQueryable%601>).  
  
 Tuple (anonim türler)  
 Matematik kavram, bir tanımlama grubu sınırlı nesneleri, belirli bir türdeki her dizisidir. Bir tanımlama grubu olarak da bilinen sıralı bir listesidir. Anonim türler bir adlandırılmamış sınıf türü bildirilmesine olanak sağlayan bir dil uygulaması bu kavramı ve aynı anda örneğinin oluşturulması için bu türde bir nesne var.  
  
 Daha fazla bilgi için bkz: [anonim türler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 tür çıkarımı (örtük yazarak)  
 Bir açık tür bildirimi eksik bir değişkende türünü belirlemek için bir derleyici yeteneği.  
  
 Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Ertelenmiş yürütme ve geç değerlendirme  
 Çözümlenen değer kadar bir ifadenin değerlendirmesine geciktirme gerçekten gerekli değildir. Ertelenmiş yürütme koleksiyonlarda desteklenir.  
  
 Daha fazla bilgi için bkz: [LINQ sorgularını (C#) giriş](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md) ve [ertelenmiş yürütme ve LINQ-XML (C#) geç değerlendirme](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
 Bu dil özellikleri kod örnekleri bu bölümde boyunca kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Giriş saf işlevsel Dönüşümleri (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [İşlevsel Programlama vs. Kesinlik temelli programlama (C#)](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
