---
title: LINQ to XML güvenliği (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d99b4af2-d447-4a3b-991b-6da0231a8637
ms.openlocfilehash: fb811b86eef9123bf079b9eb45ff1eaa29fde7b3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839710"
---
# <a name="linq-to-xml-security-visual-basic"></a>LINQ to XML güvenliği (Visual Basic)
Bu konu LINQ to XML ile ilgili güvenlik sorunları açıklar. Ayrıca, güvenlik açığı azaltma için bazı yönergeler sağlar.  
  
## <a name="linq-to-xml-security-overview"></a>LINQ to XML güvenliği genel bakış  
 LINQ to XML daha katı güvenlik gereksinimleri olan sunucu tarafı uygulamalar için daha kullanışlı programlama için tasarlanmıştır. Bir sunucuya yüklenen güvenilmeyen XML belgeleri işleme yerine işleme güvenilen XML belgeleri XML senaryo oluşur. LINQ to XML bu senaryolar için optimize edilmiştir.  
  
 Bilinmeyen kaynaklardan güvenilmeyen verilerini işlemelisiniz, Microsoft örneğini kullanmanızı önerir <xref:System.Xml.XmlReader> bilinen XML hizmet reddi (DoS) saldırıları filtrelemek için yapılandırılmış olduğu sınıf.  
  
 Yapılandırdıysanız bir <xref:System.Xml.XmlReader> hizmet reddi saldırılarını azaltmak için bu okuyucu LINQ Programcı üretkenliği iyileştirmeleriyle XML faydalanmaya devam edebilirsiniz ve bir LINQ to XML ağacı doldurma için kullanabilirsiniz. Birçok azaltma teknikleri, güvenlik sorunu gidermek için yapılandırılan okuyucu oluşturma ve ardından bir XML ağacı yapılandırılan okuyucu ile örnekleme içerir.  
  
 Belgeleri boyutu, derinliği, öğe adı boyutunu ve daha fazla sınırsız olduğundan XML doğası gereği reddi saldırılarına karşı savunmasızdır. İşlem XML kullanan bileşen ne olursa olsun, her zaman aşırı kaynakları kullanıyorsa, uygulama etki alanı geri dönüştürmek için hazırlıklı olmalıdır.  
  
## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>XML ve XSD, XPath ve XSLT saldırılarını azaltma  
 LINQ to XML üzerine kurulmuştur <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>. Uzantı yöntemleri ile LINQ to XML destekler XSD ve XPath <xref:System.Xml.Schema?displayProperty=nameWithType> ve <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanları. Kullanarak <xref:System.Xml.XmlReader>, <xref:System.Xml.XPath.XPathNavigator>, ve <xref:System.Xml.XmlWriter> sınıfları LINQ to XML ile birlikte XML ağaçlarını dönüştürmek için XSLT çağırma.  
  
 Daha az güvenli bir ortamda çalışıyorsanız, XML ile ilişkili güvenlik sorunlarını bir dizi ve vardır sınıflarda kullanımını <xref:System.Xml?displayProperty=nameWithType>, <xref:System.Xml.Schema?displayProperty=nameWithType>, <xref:System.Xml.XPath?displayProperty=nameWithType>, ve <xref:System.Xml.Xsl?displayProperty=nameWithType>. Bu sorunları içerir ancak bunlarla sınırlı değildir:  
  
-   XSD ve XPath XSLT dize tabanlı diller çok fazla zaman veya bellek kullanan işlemleri belirtebileceğiniz var. XSD, XPath veya XSLT dizeleri dizeleri kötü niyetli olmadığını doğrulamak için veya izlemek ve bu dizelerin değerlendirme aşırı sisteme önünü açacak olasılığını azaltmak için güvenilir olmayan kaynaklardan yararlanın uygulama programcılara sorumluluğudur kaynak tüketimi.  
  
-   XSD şemaları (satır içi şema dahil), hizmet reddi saldırılarını için kendiliğinden savunmasız; güvenilir olmayan kaynaklardan gelen şemaları kabul.  
  
-   XSD ve XSLT diğer dosyalara başvuruları ekleyebilirsiniz ve bölgeler arası ve etki alanları arası saldırılarında böyle başvurular neden olabilir.  
  
-   Dış DTD varlıklarda bölgeler arası ve etki alanları arası saldırılarında neden olabilir.  
  
-   DTD'ler reddi saldırılarına karşı savunmasızdır.  
  
-   Yayılan derin XML belgeleri sorunları hizmet reddi oluşturabilir; XML belgeleri derinliğini sınırlamak isteyebilirsiniz.  
  
-   Destekleyici bileşenleri gibi kabul <xref:System.Xml.NameTable>, <xref:System.Xml.XmlNamespaceManager>, ve <xref:System.Xml.XmlResolver> nesnelerden güvenilmeyen derlemeler.  
  
-   Büyük Belge saldırıları azaltmak için öbekler halinde veri okuma.  
  
-   Komut dosyası blokları XSLT stil sayfası içinde saldırıları sayısı üzerinden kullanıma sunabilirsiniz.  
  
-   Dikkatli bir şekilde dinamik XPath ifadeleri oluşturmadan önce doğrulayın.  
  
## <a name="linq-to-xml-security-issues"></a>LINQ to XML güvenlik sorunları  
 Bu konuda güvenlik sorunları herhangi belirli bir sırada sunulmaz. Tüm sorunları önemli olduğunu ve uygun şekilde izlenmelidir.  
  
 Başarılı bir ayrıcalık yükseltme saldırısı, kötü amaçlı bir derleme, ortam üzerinde daha fazla denetim sağlar. Başarılı bir ayrıcalık yükseltme saldırısı, veri, hizmet reddi ve daha fazlası açığa çıkmasına neden olabilir.  
  
 Uygulamalar bu verileri görmek için yetkilendirilmemiş kullanıcılar verileri ifşa değil.  
  
 Hizmet reddi saldırılarını aşırı miktarda bellek ve CPU süresi kullanmak için XML XML Ayrıştırıcısı veya LINQ neden. Hizmet reddi saldırılarını ayrıcalık saldırılarının yükselmesini veya veriler saldırılar açıklanması daha az önemli olarak değerlendirilir. Ancak, bunlar bir sunucu güvenilir olmayan kaynaklardan gelen XML belgeleri işlemek için gereken yere senaryosunda önemlidir.  
  
### <a name="exceptions-and-error-messages-might-reveal-data"></a>Veri açığa çıkarabilir, özel durumlar ve hata iletileri  
 Bir hatanın açıklamasını dönüştürülen veriler gibi verileri Göster, dosya adları ya da uygulama ayrıntıları. Hata iletileri güvenilir olmayan arayanlara sunulmamalıdır. Tüm yakalamalısınız hataları ve kendi özel hata iletileri ile rapor hataları.  
  
### <a name="do-not-call-codeaccesspermissionsassert-in-an-event-handler"></a>Olay işleyicisinde CodeAccessPermissions.Assert çağırmayın  
 Bir derlemenin daha düşük olabilir ya da daha büyük izinler. Büyük izinlerine sahip bir derleme, bilgisayar ve kendi ortamlarını üzerinde daha fazla denetime sahiptir.  
  
 Daha kapsamlı izinlere sahip bir derleme kodunda çağırırsa <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> bir olay işleyicisi sonra XML ağacı kötü amaçlı bir derlemeye olan kısıtlanmış izinler, kötü amaçlı derlemenin can neden olduğunu oluşturulması için bir olay geçirilir. Olay büyük izinlerle derlemedeki kod çalıştığından, kötü amaçlı derlemenin yükseltilmiş ayrıcalıklarla sonra işletim.  
  
 Microsoft, hiçbir zaman çağrı önerir <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> bir olay işleyicisi.  
  
### <a name="dtds-are-not-secure"></a>Güvenli olmayan DTD'ler olan  
 DTD'ler varlıkları güvenli kendiliğinden değil. Ayrıştırıcının tüm bellek ve CPU süresi, bir hizmet reddi saldırısına neden kullanmak neden bir DTD'nin içeren bir kötü amaçlı XML belgesi için mümkündür. Bu nedenle, içinde bir LINQ to XML DTD işleme varsayılan olarak kapalıdır. Güvenilir olmayan kaynaklardan gelen DTD'ler kabul.  
  
 Güvenilir olmayan kaynaklardan gelen DTD'ler kabul eden bir örnek Web bir DTD'nin başvuran bir XML dosyası ve bir DTD'nin dosya karşıya yükleme olanağı tanıyan bir Web uygulamasıdır. Doğrulama dosyasının bir hizmet reddi saldırısı sunucunuzdaki kötü amaçlı bir DTD'nin yürütebilir. Anonim FTP erişim veren bir ağ paylaşımındaki bir DTD'nin başvurmak için güvenilir olmayan kaynaklardan gelen DTD'ler kabul eden başka bir örnek verilmiştir.  
  
### <a name="avoid-excessive-buffer-allocation"></a>Aşırı arabellek ayırma kaçının  
 Uygulama geliştiricileri çok büyük veri kaynakları için Kaynak Tükenmesi ve hizmet reddi saldırılarını açabilir bilmeniz gerekir.  
  
 Kötü niyetli bir kullanıcı gönderdiğinde ya da çok büyük bir XML belgesi yükler, LINQ XML aşırı sistem kaynaklarının kullanılmasına neden olabilir. Bu, bir saldırı hizmet reddi oluşturabilir. Bunu önlemek için ayarlayabileceğiniz <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> özelliği ve ardından sınırlı bir okuyucu yükleyebileceği belgesinin boyutu oluşturun. XML ağacı oluşturmak için okuyucu kullanın.  
  
 Örneğin, maksimum boyutu güvenilmeyen bir kaynaktan gelen XML belgelerinin beklenen biliyorsanız 50'den az K bayt olması, ayarlama <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> 100.000 için. Bu, XML belgelerinin işlenmesini encumber değil ve aynı zamanda büyük miktarda bellek kullanılmasına neden olur, burada belgeler karşıya hizmet reddi tehditlerine riskini azaltır.  
  
### <a name="avoid-excess-entity-expansion"></a>Aşırı varlık genişletme kaçının  
 Bilinen bir DTD'nin kullanırken hizmet reddi saldırılarını birini aşırı varlık genişletme neden olan bir belgedir. Bunu önlemek için ayarlayabileceğiniz <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=nameWithType> özelliği ve ardından sınırlı bir okuyucu varlık genişletme neden olan karakter sayısı oluşturun. XML ağacı oluşturmak için okuyucu kullanın.  
  
### <a name="limit-the-depth-of-the-xml-hierarchy"></a>XML hiyerarşinin derinliği sınırı  
 Olası bir saldırı hizmet reddi aşırı hiyerarşi derinliğini sahip bir belge gönderildiği andır. Bunu önlemek için kaydırılabilir bir <xref:System.Xml.XmlReader> kendi sınıfında öğeleri derinliğini sayar. Derinlik önceden belirlenmiş bir makul düzeyde aşarsa, kötü amaçlı belge işlenmesini sonlandırabilirsiniz.  
  
### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>XmlReader veya XmlWriter uygulamaları güvenilmeyen karşı koruma  
 Yöneticiler, tüm harici olarak sağlanan olduğunu doğrulamalıdır <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter> uygulamaları tanımlayıcı adları ve makine yapılandırmasında kayıtlı. Bu, kötü amaçlı kod okuyucu veya gelen yüklenen yazıcı olarak davranan engeller.  
  
### <a name="periodically-free-objects-that-reference-xname"></a>Düzenli aralıklarla bu başvuru XName nesneleri ücretsiz  
 Belirli türdeki saldırılarına karşı korumak için uygulama programcılarının başvuran tüm nesneleri ücretsiz bir <xref:System.Xml.Linq.XName> düzenli aralıklarla uygulama etki alanındaki nesne.  
  
### <a name="protect-against-random-xml-names"></a>Rasgele XML adları karşı koruma  
 Güvenilmeyen kaynaklardan veri yararlanan uygulamalar göz önünde bulundurmalıdır kullanarak bir <xref:System.Xml.XmlReader> rasgele XML adları ve ad alanları olasılığını incelemek için diğer bir deyişle sarmalanmış olarak özel kod. Bu tür rasgele XML adları ve ad alanları algılanırsa, uygulama ardından kötü amaçlı belge işlenmesini sonlandırabilirsiniz.  
  
 (Hiçbir ad alanı içinde adları dahil) belirtilen ad alanı adları sayısını sınırlamak makul bir sınır isteyebilirsiniz.  
  
### <a name="annotations-are-accessible-by-software-components-that-share-a-linq-to-xml-tree"></a>Ek Açıklamalar LINQ to XML ağacı paylaşan yazılım bileşenleri tarafından erişilebilir  
 LINQ to XML, farklı uygulama bileşenleri yüklemek, doğrulama, sorgu, dönüştürme, güncelleştirme ve XML ağaçlarını olarak bileşenleri arasında geçirilen XML verileri kaydetmek işlem komut zincirleri oluşturmak için kullanılabilir. Yükleme ve XML metin nesneleri serileştirmek işleriyle uğraşmak yerine yalnızca bir işlem hattı ucunda yapıldığı için bu, performansı en iyi duruma yardımcı olabilir. Geliştiriciler ancak tüm ek açıklamaları ve olay işleyicileri bir bileşen tarafından oluşturulan diğer bileşenler için erişilebilir olduğunu aklınızda bulundurun gerekir. Bileşenleri farklı güven düzeyleri varsa bu birtakım güvenlik açıkları oluşturabilir. Daha az güvenilir bileşenlerinde güvenli işlem hatları oluşturmak için LINQ XML metin XML nesnelere güvenilmeyen bir bileşen için verileri geçirmeden önce seri gerekir.  
  
 Ortak dil çalışma zamanı tarafından (CLR) bazı güvenlik sağlanır. Örneğin, özel bir sınıf içermeyen bir bileşeni, sınıf tarafından Anahtarlanan ek açıklamaları erişemez. Ancak, ek açıklamalar, bunları okunamıyor bileşenleri tarafından silinebilir. Bu değiştirme bir saldırı olarak kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
