---
title: LINQ-XML güvenlik (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d99b4af2-d447-4a3b-991b-6da0231a8637
ms.openlocfilehash: 3f75377502b30b03090bb2a5fe720faf4e12a028
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-xml-security-visual-basic"></a>LINQ-XML güvenlik (Visual Basic)
Bu konu LINQ-XML ile ilgili güvenlik sorunları açıklar. Ayrıca, güvenlik açıklarını Azaltıcı için bazı yönergeler sağlar.  
  
## <a name="linq-to-xml-security-overview"></a>LINQ-XML güvenliğine genel bakış  
 LINQ-XML daha sıkı güvenlik gereksinimleri olan sunucu tarafı uygulamalar için daha kullanışlı programlama için tasarlanmıştır. Bir sunucuya yüklenen güvenilmeyen XML belgelerini işleme yerine güvenilen XML belgelerini işleme çoğu XML senaryosu oluşur. LINQ-XML bu senaryoları için optimize edilmiştir.  
  
 Bilinmeyen kaynaklardan gelen güvenilmeyen verileri işlemek, Microsoft örneğini kullanmanızı önerir <xref:System.Xml.XmlReader> bilinen XML hizmet reddi (DoS) saldırılarını filtrelemek için yapılandırılmış sınıfı.  
  
 Yapılandırdıysanız bir <xref:System.Xml.XmlReader> hizmet reddi saldırılarını azaltmak için okuyucu bir LINQ to XML ağaç doldurmak ve hala LINQ Programcı üretkenlik iyileştirmeleriyle XML yararlanmak için kullanabilirsiniz. Birçok azaltma teknikleri güvenlik sorunu azaltmak için yapılandırılmış okuyucular oluşturma ve bir XML ağacı yapılandırılmış okuyucu ile başlatmasını içerir.  
  
 Belgeleri boyutu, derinlik, öğe adı boyut ve daha fazla sınırsız olduğundan XML doğası gereği hizmet reddi saldırılarını önlemek için savunmasızdır. İşlem XML kullandığınız bileşen bağımsız olarak, her zaman aşırı kaynakları kullanıyorsa, uygulama etki alanı geri dönüştürmek için hazırlıklı olmalıdır.  
  
## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>XML, XSD, XPath ve XSLT saldırılarını azaltma  
 LINQ-XML üzerine üretilmiştir <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>. LINQ-XML XSD ve destekler XPath uzantı yöntemleri aracılığıyla <xref:System.Xml.Schema?displayProperty=nameWithType> ve <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanları. Kullanarak <xref:System.Xml.XmlReader>, <xref:System.Xml.XPath.XPathNavigator>, ve <xref:System.Xml.XmlWriter> sınıfları LINQ-XML ile birlikte XML ağaçları dönüştürmek için XSLT çağırma.  
  
 Daha az güvenli bir ortamda işletim varsa bir dizi XML ile ilişkili güvenlik sorunlarını ve sınıflarda kullanımını <xref:System.Xml?displayProperty=nameWithType>, <xref:System.Xml.Schema?displayProperty=nameWithType>, <xref:System.Xml.XPath?displayProperty=nameWithType>, ve <xref:System.Xml.Xsl?displayProperty=nameWithType>. Bu sorunlar dahil ancak bunlarla sınırlı değildir:  
  
-   XSD, XPath ve XSLT dize tabanlı diller zaman veya bellek çok tüketen işlemleri belirtebilirsiniz verilebilir. Dizeleri kötü niyetli olmadığını doğrulamak veya izlemek ve bu dizeler değerlendirme aşırı sisteme götürür olasılığını azaltmak için güvenilir olmayan kaynaklardan gelen XSD, XPath veya XSLT dizeleri ele uygulama programcıları sorumluluğundadır kaynak tüketimini.  
  
-   XSD şemaları (satır içi şema dahil) hizmet reddi saldırılarını önlemek için kendiliğinden etkilenir; güvenilir olmayan kaynaklardan gelen şemaları kabul.  
  
-   XSD ve XSLT diğer dosyalara başvurular içerebilir ve bu tür başvuruları çapraz bölge ve etki alanları arası saldırılarına neden olabilir.  
  
-   DTD dış varlıklarda çapraz bölge ve etki alanları arası saldırılarına neden olabilir.  
  
-   DTD, hizmet reddi saldırılarını önlemek için etkilenir.  
  
-   Olağanüstü derin XML belgeleri hizmet sorunlarını Reddi oluşturabilir; XML belgeleri derinliğini sınırlamak isteyebilirsiniz.  
  
-   Destekleyen bileşenler gibi kabul <xref:System.Xml.NameTable>, <xref:System.Xml.XmlNamespaceManager>, ve <xref:System.Xml.XmlResolver> güvenilmeyen derlemelerden nesneleri.  
  
-   Parçalar büyük belge saldırıları azaltmak için veri okuma.  
  
-   XSLT stil sayfaları komut dosyası bloklarında saldırıları sayısı getirebilir.  
  
-   Dinamik XPath ifadeleri oluşturmak önce dikkatle doğrulayın.  
  
## <a name="linq-to-xml-security-issues"></a>LINQ-XML güvenlik sorunları  
 Bu konuda güvenlik sorunları, belirli bir sırada sunulmayan. Tüm sorunları önemlidir ve uygun şekilde ele alınması.  
  
 Başarılı bir ayrıcalık yükseltme saldırısı kötü amaçlı bir derleme ortamından üzerinde daha fazla denetim sağlar. Başarılı bir ayrıcalık yükseltme saldırısı, verileri, hizmet reddi ve daha fazlasını açığa çıkmasına neden olabilir.  
  
 Uygulamalar verileri görmek için yetkilendirilmemiş kullanıcılar verilere açığa çıkarmamak.  
  
 Hizmet reddi saldırılarını aşırı miktarda bellek veya CPU süresi kullanmak için XML XML parser veya LINQ neden. Hizmet reddi saldırılarını ayrıcalıkların yükseltilmesi saldırılarını veya açığa veri saldırıların daha az önemli olarak değerlendirilir. Ancak, bunlar burada güvenilir olmayan kaynaklardan gelen XML belgelerini işlemek için bir sunucu gerektiren bir senaryo önemli değildir.  
  
### <a name="exceptions-and-error-messages-might-reveal-data"></a>Özel durumlar ve hata iletileri veri ortaya çıkarabilir  
 Hata açıklaması dönüştürülmekte olan verileri gibi veri ortaya, dosya adları ya da uygulama ayrıntıları. Hata iletileri güvenilmeyen arayanlara açılmamalıdır değil. Tüm catch hataları ve kendi özel hata iletileri ile rapor hataları.  
  
### <a name="do-not-call-codeaccesspermissionsassert-in-an-event-handler"></a>Bir olay işleyicisi CodeAccessPermissions.Assert çağırmayın  
 Bir derlemeyi küçük olabilir veya büyük izinleri. Büyük izinlerine sahip bir derleme bilgisayarı ve onun ortamları büyük denetime sahiptir.  
  
 Büyük izinlere sahip bir bütünleştirilmiş kod çağırırsa <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> olay işleyicisi sonra XML ağaç kötü amaçlı bir derlemeye sahip kısıtlı izinleri, kötü amaçlı derleme can neden olduğunu oluşturulması için bir olay geçirilir. Kötü amaçlı derleme, ardından olay büyük izinlerle bütünleştirilmiş kodları çalıştığından, yükseltilmiş ayrıcalıklarla işletim.  
  
 Microsoft, hiçbir zaman çağrı önerir <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> bir olay işleyicisi.  
  
### <a name="dtds-are-not-secure"></a>DTD değil güvenli olan  
 DTD varlıklarda güvenli kendiliğinden değil. İçin tüm bellek ve CPU süresi, bir hizmet reddi saldırısına neden kullanmak ayrıştırıcı neden DTD içeren bir kötü amaçlı bir XML belgesi mümkündür. Bu nedenle, içinde LINQ-XML DTD işleme varsayılan olarak kapalıdır. Güvenilir olmayan kaynaklardan gelen DTD'leri kabul.  
  
 Güvenilir olmayan kaynaklardan gelen DTD'leri kabul etmenin bir DTD başvuruda bulunan bir XML dosyası ve DTD dosyasını karşıya yüklemek Web kullanıcılarına sağlayan bir Web uygulaması örnektir. Doğrulama dosyasının bir hizmet reddi saldırısına sunucunuzda kötü amaçlı bir DTD yürütebilir. Ayrıca anonim FTP erişimine olanak tanıyan bir ağ paylaşımındaki bir DTD başvurmak için DTD'leri güvenilmeyen kaynaklardan kabul, başka bir örnek verilmiştir.  
  
### <a name="avoid-excessive-buffer-allocation"></a>Aşırı arabellek ayırma kaçının  
 Uygulama geliştiricilerinin son derece büyük veri kaynakları Kaynak Tükenmesi ve hizmet reddi saldırılarını açabilir bilmeniz gerekir.  
  
 Kötü niyetli bir kullanıcının gönderdiğinde ya da çok büyük bir XML belgesi yükler, aşırı sistem kaynaklarını tüketebilir XML'e LINQ neden olabilir. Bu, bir hizmet reddi saldırısına oluşturabilecek. Bunu önlemek için ayarlayabileceğiniz <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> özelliği ve ardından sınırlı bir okuyucu yükleyebileceği belge boyutunda oluşturun. Okuyucu ardından XML ağacı oluşturmak için kullanın.  
  
 Örneğin, maksimum boyutu güvenilmeyen bir kaynaktan gelen XML belgelerinin beklenen biliyorsanız 50'den az K bayt olması, ayarlamak <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> 100.000 için. Bu, XML belgelerinin işlenmesini encumber değil ve aynı anda reddi büyük miktarlarda bellek kullanır, belgeleri karşıya hizmet tehditleri azaltmak.  
  
### <a name="avoid-excess-entity-expansion"></a>Aşırı varlık genişletme kaçının  
 Bilinen bir DTD kullanırken hizmet reddi saldırılarını aşırı varlık genişletme neden olan bir belgeyi biridir. Bunu önlemek için ayarlayabileceğiniz <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=nameWithType> özelliği ve ardından sınırlı bir okuyucu varlık genişletme neden karakter sayısını oluşturun. Okuyucu ardından XML ağacı oluşturmak için kullanın.  
  
### <a name="limit-the-depth-of-the-xml-hierarchy"></a>XML hiyerarşisinin derinliğini sınırla  
 Bir belge hiyerarşisi aşırı derinliği olan gönderildiğinde bir olası hizmet reddi saldırısı ' dir. Bunu önlemek için kayabilir bir <xref:System.Xml.XmlReader> kendi sınıfında öğelerinin derinliği sayar. Önceden belirlenmiş bir makul düzeyi aşıyor, kötü amaçlı belge işlenmesini sonlandırabilir.  
  
### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>XmlReader veya XmlWriter uygulamaları güvenilmeyen karşı koruma  
 Yöneticiler, herhangi bir harici olarak sağlanan olduğunu doğrulamalıdır <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter> uygulamaları güçlü adlara sahip ve makine yapılandırmada kayıtlı. Bu, kötü amaçlı kod okuyucu veya yüklenen gelen yazıcı olarak davranan engeller.  
  
### <a name="periodically-free-objects-that-reference-xname"></a>Düzenli aralıklarla serbest nesneleri bu başvuru XName  
 Belirli türdeki saldırılarına karşı korumak için uygulama programcıları başvuru tüm nesneleri serbest bir <xref:System.Xml.Linq.XName> düzenli olarak uygulama etki alanındaki nesne.  
  
### <a name="protect-against-random-xml-names"></a>Rastgele XML adları karşı koruma  
 Güvenilmeyen kaynaklardan veri yararlanan uygulamalar kullanarak düşünmelisiniz bir <xref:System.Xml.XmlReader> rastgele XML adları ve ad alanlarını olasılığını incelemek için diğer bir deyişle, Sarmalanan özel kod. Bu tür rastgele XML adları ve ad alanlarını algılanmazsa, uygulama sonra zararlı belgeyi işlenmesini sonlandırabilir.  
  
 (Adları yok ad alanına dahil) herhangi bir verilen ad alanlarındaki sayısını sınırlamak makul bir sınır isteyebilirsiniz.  
  
### <a name="annotations-are-accessible-by-software-components-that-share-a-linq-to-xml-tree"></a>Ek açıklamalar bir LINQ to XML ağaç paylaşmak yazılım bileşenleri tarafından erişilebilir  
 LINQ-XML, farklı uygulama bileşenleri yüklemek, doğrulamak, sorgu, dönüştürme, güncelleştirme ve XML ağaçlar bileşenleri arasında geçirilen XML verileri kaydetmek işleme ardışık düzen oluşturmak için kullanılabilir. Yükleme ve XML metni nesneleri seri hale getirme yükünü yalnızca ardışık düzen ucunda yapıldığından bu performansı en iyi duruma getirme yardımcı olabilir. Geliştiriciler ancak, tüm ek açıklamaları ve bir bileşen tarafından oluşturulan olay işleyicileri için diğer bileşenleri erişilebilir olduğunu aklınızda bulundurun gerekir. Farklı güven düzeyleri bileşenleri varsa, bu bir dizi güvenlik açıkları oluşturabilir. Daha az güvenilen bileşenlerinde güvenli ardışık düzen oluşturmak için LINQ XML metni için XML nesnelere güvenilmeyen bir bileşen verileri geçirmeden önce seri hale gerekir.  
  
 Bazı güvenlik ortak dil çalışma zamanı tarafından (CLR) sağlanır. Örneğin, özel bir sınıf içermeyen bir bileşeni o sınıf tarafından Anahtarlanan ek açıklamaları erişemiyor. Ancak, ek açıklamalar, bunları okuyamıyor bileşenleri tarafından silinebilir. Bu değiştirme bir saldırı olarak kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlama Kılavuzu (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
