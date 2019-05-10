---
title: Kavramlar ve terimler (işlevsel dönüşüm) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
ms.openlocfilehash: 1a2dd2fe835ada29fdb6639905673b4e0b60aca6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642023"
---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a>Kavramlar ve terimler (işlevsel dönüşüm) (Visual Basic)
Bu konu, saf işlevsel dönüşümlere terimleri ve kavramları tanıtır. Veri dönüştürme işlevsel dönüşüm yaklaşım genellikle programa daha ifadesel ve daha kolay hata ayıklaması ve bakımı daha geleneksel, zorunlu programlama daha hızlı kod üretir.  
  
 Bu bölümdeki konularda, tam olarak işlevsel programlama açıklamak üzere amaçlanmamıştır unutmayın. Bunun yerine, bu konularda bazı XML bir şekle Dönüştür daha kolay hale getirmek işlevsel programlama özelliklerini tanımlayın.  
  
## <a name="what-is-pure-functional-transformation"></a>Saf işlevsel dönüşüm nedir?  
 İçinde *saf işlevsel dönüşüm*, çağrılan işlevler bir dizi *saf işlevler*, yapılandırılmış verileri özgün biçimlerinde bir dizi başka bir biçime dönüştürmek nasıl tanımlayın. "Saf" sözcüğü işlevleri gösterir *birleştirilebilir*, olmalarını gerektirir:  
  
- *Müstakil*, böylece bunlar kullanılabilir serbestçe sıralı ve entanglement veya programın geri kalanını ile bağımlılıkları olmadan düzenlenmeyecek. Saf dönüştürmeleri hakkında bilgi sahibi ya da kendi ortamlarında üzerinde etkisi vardır. Diğer bir deyişle, dönüşümünde işlevleri yok *yan etkileri*.  
  
- *Durum bilgisi olmayan*, böylece aynı işlev veya belirli işlevler kümesi aynı giriş yürütülen her zaman aynı çıktısında neden olur. Saf dönüşümleri önceki kullanımları bellek var.  
  
> [!IMPORTANT]
>  Bu öğreticinin geri kalanını içinde "saf işlev" terimi, genel anlamda programlama bir yaklaşım ve belirli bir dil özelliği belirtmek için kullanılır.  
>   
>  Saf işlevler Visual Basic'te işlevler olarak uygulanması gerektiğini unutmayın.  
>   
>  Ayrıca, saf işlevleri saf sanal C++ yöntemleri ile farklıdır. İkincisi, içerilen sınıf soyuttur ve herhangi bir yöntem gövdesi verilmesi gerektiğini gösterir.  
  
### <a name="functional-programming"></a>İşlevsel programlama  
 *İşlevsel programlama* saf işlevsel dönüşüm doğrudan destekleyen programlama bir yaklaşımdır.  
  
 Tarihsel olarak, ML, düzeni, Haskell, genel amaçlı işlevsel programlama dilleri ve F#, öncelikle, akademik topluluk olmuştur. Her zaman Visual Basic'te saf işlevsel dönüşümlere yazmayı mümkün olsa da, zorluk Bunun yapılması, bu nedenle, çoğu programcıları için çekici bir seçenek yapılmadı. Lambda ifadeleri ve tür çıkarımı işlevsel programlama çok daha kolay ve daha üretken hale gibi Visual Basic sonraki sürümleriyle ancak yeni dil oluşturur.  
  
 İşlevsel programlama hakkında daha fazla bilgi için bkz. [işlevsel Programlama vs. Kesin programlama karşılaştırması (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).  
  
#### <a name="domain-specific-fp-languages"></a>FP etki alanına özgü diller  
 Genel fonksiyonel programlama dillerinin geniş uyarlanmıştır değil olsa da, özel etki alanına özgü fonksiyonel programlama dillerinin daha iyi başarı kalmışlardır. Örneğin, geçişli stil sayfaları (CSS), birçok Web sayfası Görünüm ve yapısını belirlemek için kullanılır ve Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) stil sayfaları, XML veri işleme yaygın olarak kullanılır. XSLT hakkında daha fazla bilgi için bkz: [XSLT dönüşümleri](../../../../standard/data/xml/xslt-transformations.md).  
  
## <a name="terminology"></a>Terminoloji  
 Aşağıdaki tabloda bazı terimler için işlevsel dönüşümlere ilgili tanımlar.  
  
 daha yüksek sıralı (ilk sınıf) işlevi  
 Programlı bir nesnesi olarak davranılıp bir işlev. Örneğin, yüksek sıralı işlev geçirilen veya diğer işlevlerden döndürülebilir. Visual Basic'te, temsilciler ve lambda ifadeleri, daha yüksek sıralı işlev destekleyen dili özelliği şunlardır. Yüksek sıralı işlev yazmak için temsilciler almak için bir veya daha fazla bağımsız değişken bildirme ve genellikle lambda ifadeleri çağırırken kullanırsınız. Standart sorgu işleçlerinin çoğu, daha yüksek sıralı işlevlerdir.  
  
 Daha fazla bilgi için [standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 Lambda ifadesi  
 Bir temsilci türünün beklendiği her yerde kullanılabilir esas olarak, bir satır içi anonim işlev. Bu basitleştirilmiş bir tanımı lambda ifadeleri, ancak bu öğreticinin amaçları doğrultusunda yeterli.  
  
 Hakkında daha fazla bilgi için bkz: [Lambda ifadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
  koleksiyonu  
 Veri, genellikle bir Tekdüzen türü yapılandırılmış bir dizi. LINQ ile uyumlu olacak şekilde bir koleksiyon uygulamalıdır <xref:System.Collections.IEnumerable> arabirimi veya <xref:System.Linq.IQueryable> arabirimi (veya genel karşılıkları <xref:System.Collections.Generic.IEnumerator%601> veya <xref:System.Linq.IQueryable%601>).  
  
 Tanımlama grubu (anonim türler)  
 Matematiksel bir kavram, bir tanımlama grubu sınırlı nesneleri belirli bir türdeki her dizisidir. Bir tanımlama grubu olarak da bilinen sıralı bir listesidir. Anonim türler bir adsız sınıf türü bildirimi etkinleştiren bir dil uygulama bu kavram ve aynı anda örneği için bu türde bir nesne var.  
  
 Daha fazla bilgi için [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
 tür çıkarımı (örtülü yazma)  
 Bir açık tür bildirimi olmadığında bir değişkenin türünü belirlemek için bir derleyici yeteneğidir.  
  
 Daha fazla bilgi için [yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Ertelenmiş yürütme ve geç değerlendirme  
 Çözümlenen değerine kadar bir ifadenin değerlendirmesine geciktirme gerçekten gerekli değildir. Ertelenmiş yürütme koleksiyonlarında desteklenir.  
  
 Daha fazla bilgi için [temel sorgu işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) ve [ertelenmiş yürütme ve geç değerlendirme LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
 Kod örnekleri bu bölümü boyunca bu dil özellikleri kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saf işlevsel dönüşümlere (Visual Basic) giriş](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [İşlevsel Programlama ve Kesin programlama karşılaştırması (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
