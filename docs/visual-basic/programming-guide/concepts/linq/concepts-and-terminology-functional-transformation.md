---
title: Kavramları ve terminolojiyi (işlev dönüştürme) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
ms.openlocfilehash: 67986e36333ac9a1aba7bec3c1b6c248b4faf55f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644426"
---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a>Kavramları ve terminolojiyi (işlev dönüştürme) (Visual Basic)
Bu konu, kavramları ve terminolojiyi saf işlevsel Dönüşümlerin tanıtır. Veri dönüştürme işlev dönüştürme yaklaşım program, daha açıklayıcı ve daha kolay hata ayıklama ve sürdürmek daha geleneksel, kesinlik temelli programlama için genellikle hızlıdır kodunu üretir.  
  
 Bu bölümdeki konular, tam olarak işlevsel programlama açıklamak için amaçlanmamıştır unutmayın. Bunun yerine, bu konularda bazı XML bir şekle Dönüştür kolaylaştırmak işlevsel programlama özelliklerini tanımlayın.  
  
## <a name="what-is-pure-functional-transformation"></a>Saf işlev dönüştürme nedir?  
 İçinde *saf işlev dönüştürme*, çağrılan işlevler kümesi *saf işlevleri*, özgün formuna yapılandırılmış veri kümesi başka bir biçime dönüştürmek nasıl tanımlayın. "Saf" word işlevleri gösterir *birleştirilebilir*, olmalarını gerektirir:  
  
-   *Kendi içinde bulunan*, böylece bunlar kullanılabilir ücretsiz olarak sipariş ve entanglement veya program kalanıyla bağımlılıklarını olmadan düzenlenmeyecek. Saf dönüşümleri hiçbir bilgisi veya ortamlarına üzerinde etkisi vardır. Diğer bir deyişle, dönüşümünde işlevleri yok *yan etkileri*.  
  
-   *Durum bilgisiz*, böylece aynı işlev veya işlev belirli kümesi aynı giriş, yürütülen her zaman aynı çıktısında neden olur. Saf dönüşümleri önceki kullanım hiçbir bellek yok.  
  
> [!IMPORTANT]
>  Bu öğreticinin geri kalanını içinde "saf işlev" terimi genel anlamda programlama bir yaklaşım ve belirli bir dil özelliği belirtmek için kullanılır.  
>   
>  Saf işlevleri, Visual Basic'te işlev olarak uygulanmalıdır unutmayın.  
>   
>  Ayrıca, saf işlevleri C++ saf sanal yöntemlerle karıştırmamalısınız. İkinci içeren Sınıf soyut ve hiçbir yöntem gövdesi sağlanan gösterir.  
  
### <a name="functional-programming"></a>İşlevsel programlama  
 *İşlevsel programlama* saf işlev dönüştürme doğrudan destekleyen programlama bir yaklaşımdır.  
  
 Tarihsel olarak, genel amaçlı işlevsel gibi programlama dilleri, ML, şema, Haskell ve F #'ta, öncelikle akademik topluluk ilgi olmuştur. Bu her zaman saf işlevsel dönüşümleri Visual Basic'te yazma mümkün olsa da, bunun zorluk bu nedenle, çoğu programcıları için çekici bir seçenek yapılmadı. Lambda ifadeleri ve tür çıkarımı işlevsel programlama çok daha kolay ve daha üretken kolaylaştırır gibi Visual Basic sonraki sürümleri ile ancak yeni dil oluşturur.  
  
 İşlevsel programlama hakkında daha fazla bilgi için bkz: [işlevsel Programlama vs. Kesinlik temelli programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).  
  
#### <a name="domain-specific-fp-languages"></a>Etki alanına özgü FP dilleri  
 Genel işlevsel programlama dilleri yaygın uyarlanmıştır değil de, belirli etki alanına özgü işlevsel programlama dilleri daha iyi başarı beklendiğinden. Örneğin, geçişli stil sayfaları (CSS) birçok Web sayfalarının Görünüm ve yapısını belirlemek için kullanılır ve Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) stil sayfaları, XML veri işleme yaygın olarak kullanılır. XSLT hakkında daha fazla bilgi için bkz: [XSLT dönüştürmeleri](../../../../standard/data/xml/xslt-transformations.md).  
  
## <a name="terminology"></a>Terminoloji  
 Aşağıdaki tabloda işlevsel dönüşümleri ilgili bazı koşullarını tanımlar.  
  
 daha yüksek sıralı (birinci sınıf) işlevi  
 Programlama nesnesi olarak kabul bir işlev. Örneğin, daha yüksek sıralı işlevi geçirilen veya diğer işlevleri döndürdü. Visual Basic'te Temsilciler ve lambda ifadeleri daha yüksek sıralı işlevlerini destekleyen dil özellikleridir. Daha yüksek sıralı işlevi yazmak için temsilciler almak için bir veya daha fazla bağımsız değişken bildirme ve genellikle lambda ifadeleri, çağrılırken kullanılır. Standart sorgu işleçleri birçoğu, daha yüksek sıralı işlevlerdir.  
  
 Daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 lambda ifadesi  
 Bir temsilci türü bekleniyor her yerde kullanılabilir esas olarak, bir satır içi anonim işlev. Bu bir lambda ifadeleri Basitleştirilmiş tanımıdır, ancak bu öğreticinin amaçları doğrultusunda yeterli.  
  
 Hakkında daha fazla bilgi için bkz: [Lambda ifadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 koleksiyon  
 Veri, genellikle bir Tekdüzen türü yapılandırılmış kümesi. LINQ ile uyumlu olacak şekilde bir koleksiyon uygulamalıdır <xref:System.Collections.IEnumerable> arabirimi veya <xref:System.Linq.IQueryable> arabirimi (veya genel dekiler <xref:System.Collections.Generic.IEnumerator%601> veya <xref:System.Linq.IQueryable%601>).  
  
 Tuple (anonim türler)  
 Matematik kavram, bir tanımlama grubu sınırlı nesneleri, belirli bir türdeki her dizisidir. Bir tanımlama grubu olarak da bilinen sıralı bir listesidir. Anonim türler bir adlandırılmamış sınıf türü bildirilmesine olanak sağlayan bir dil uygulaması bu kavramı ve aynı anda örneğinin oluşturulması için bu türde bir nesne var.  
  
 Daha fazla bilgi için bkz: [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
 tür çıkarımı (örtük yazarak)  
 Bir açık tür bildirimi eksik bir değişkende türünü belirlemek için bir derleyici yeteneği.  
  
 Daha fazla bilgi için bkz: [yerel türü çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Ertelenmiş yürütme ve geç değerlendirme  
 Çözümlenen değer kadar bir ifadenin değerlendirmesine geciktirme gerçekten gerekli değildir. Ertelenmiş yürütme koleksiyonlarda desteklenir.  
  
 Daha fazla bilgi için bkz: [temel sorgu işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) ve [ertelenmiş yürütme ve LINQ-XML (Visual Basic) geç değerlendirme](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
 Bu dil özellikleri kod örnekleri bu bölümde boyunca kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Giriş saf işlevsel Dönüşümleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [İşlevsel Programlama ve Kesinlik temelli programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
