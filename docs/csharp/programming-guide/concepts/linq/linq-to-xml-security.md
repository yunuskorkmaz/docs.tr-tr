---
title: LINQ' dan XML Security'ye (C#)
ms.date: 07/20/2015
ms.assetid: ef2c0dc9-ecf9-4c17-b24e-144184ab725f
ms.openlocfilehash: 5b7eb815b058cba008f1db2cf683c8934c19b743
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73423370"
---
# <a name="linq-to-xml-security-c"></a>LINQ' dan XML Security'ye (C#)
Bu konu, LINQ ile XML ile ilişkili güvenlik sorunlarını açıklar. Buna ek olarak, güvenlik maruziyetini hafifletmek için bazı kılavuzlar sağlar.  
  
## <a name="linq-to-xml-security-overview"></a>LINQ - XML Güvenlik Genel Bakış  
 LINQ to XML, sıkı güvenlik gereksinimleriolan sunucu tarafındaki uygulamalardan çok programlama kolaylığı için tasarlanmıştır. Çoğu XML senaryosu, sunucuya yüklenen güvenilmeyen XML belgelerini işlemek yerine güvenilir XML belgelerini işlemekten oluşur. LINQ xml bu senaryolar için optimize edilsin.  
  
 Bilinmeyen kaynaklardan gelen güvenilmeyen verileri işlemeniz gerekiyorsa, Microsoft bilinen <xref:System.Xml.XmlReader> XML hizmet reddi (DoS) saldırılarını filtrelemek için yapılandırılan sınıfın bir örneğini kullanmanızı önerir.  
  
 Hizmet reddi saldırılarını <xref:System.Xml.XmlReader> azaltmak için bir yapıya sahipseniz, bu okuyucuyu bir LINQ'u XML ağacına doldurmak ve linq'in XML'e programlayıcı üretkenlik geliştirmelerinden yararlanmak için kullanabilirsiniz. Birçok azaltma tekniği, güvenlik sorununu azaltmak için yapılandırılan okuyucular oluşturmayı ve sonra yapılandırılmış okuyucu aracılığıyla bir XML ağacını anında oluşturmayı içerir.  
  
 Belgelerin boyutu, derinliği, öğe adı boyutu ve daha fazlası ile sınırsız olduğundan XML, hizmet reddi saldırılarına karşı özünde savunmasızdır. XML'i işlemek için kullandığınız bileşenden bağımsız olarak, aşırı kaynak kullanıyorsa uygulama etki alanını geri dönüştürmeye her zaman hazırlıklı olmalısınız.  
  
## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>XML, XSD, XPath ve XSLT Saldırılarının azaltılması  
 LinQ XML üzerine <xref:System.Xml.XmlReader> inşa <xref:System.Xml.XmlWriter>edilmiş ve . LINQ xml ve <xref:System.Xml.Schema?displayProperty=nameWithType> <xref:System.Xml.XPath?displayProperty=nameWithType> ad boşluklarında uzantı yöntemleri ile XSD ve XPath destekler. LINQ <xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator>ile <xref:System.Xml.XmlWriter> XML ile birlikte , ve sınıfları kullanarak, XML ağaçlarını dönüştürmek için XSLT'yi çağırabilirsiniz.  
  
 Daha az güvenli bir ortamda çalışıyorsanız, XML ile ilişkili bir dizi güvenlik sorunu ve <xref:System.Xml?displayProperty=nameWithType>sınıfların <xref:System.Xml.XPath?displayProperty=nameWithType>kullanımı <xref:System.Xml.Xsl?displayProperty=nameWithType>, , <xref:System.Xml.Schema?displayProperty=nameWithType>, ve . Bu sorunlar şunlardır, ancak bunlarla sınırlı değildir:  
  
- XSD, XPath ve XSLT, çok fazla zaman veya bellek tüketen işlemleri belirtebileceğiniz dize tabanlı dillerdir. Dizelerin kötü amaçlı olmadığını doğrulamak veya bu dizeleri değerlendirmenin aşırı sisteme yol açma olasılığını izlemek ve azaltmak için güvenilmeyen kaynaklardan XSD, XPath veya XSLT dizelerini alan uygulama programcılarının sorumluluğundadır. kaynak tüketimi.  
  
- XSD şemaları (satır içi şemalar dahil) hizmet reddi saldırılarına karşı doğal olarak savunmasızdır; güvenilir olmayan kaynaklardan şema kabul etmemelisiniz.  
  
- XSD ve XSLT diğer dosyalara başvurular içerebilir ve bu tür başvurular bölge ler arası ve etki alanları arası saldırılara neden olabilir.  
  
- DTD'ler dış varlıklar çapraz bölge ve etki alanları arası saldırılara neden olabilir.  
  
- DTD'ler hizmet reddi saldırılarına karşı savunmasızdır.  
  
- Son derece derin XML belgeleri hizmet reddi sorunları oluşturabilir; XML belgelerinin derinliğini sınırlamak isteyebilirsiniz.  
  
- Güvenilmeyen derlemelerden , , <xref:System.Xml.NameTable> <xref:System.Xml.XmlNamespaceManager>ve <xref:System.Xml.XmlResolver> nesneler gibi destekleyici bileşenleri kabul etmeyin.  
  
- Büyük belge saldırılarını azaltmak için verileri yığınlar halinde okuyun.  
  
- XSLT stil sayfalarındaki komut dosyası blokları bir dizi saldırıyı ortaya çıkarabilir.  
  
- Dinamik XPath ifadeleri oluşturmadan önce dikkatlice doğrulayın.  
  
## <a name="linq-to-xml-security-issues"></a>LINQ - XML Güvenlik Sorunları  
 Bu konudaki güvenlik sorunları belirli bir sırada sunulmaz. Tüm konular önemlidir ve uygun şekilde ele alınmalıdır.  
  
 Ayrıcalık saldırısının başarılı bir şekilde yükseltilen bir yükseklik, kötü amaçlı bir derlemeye çevresi üzerinde daha fazla denetim sağlar. Ayrıcalık saldırısının başarılı bir şekilde yükselmesi verilerin açıklanmasına, hizmet reddine ve daha fazlasında neden olabilir.  
  
 Uygulamalar, verileri bu verileri görme yetkisi olmayan kullanıcılara açıklamamalıdır.  
  
 Hizmet reddi saldırıları, XML parlayıcısının veya LINQ'nin XML'e kadar aşırı miktarda bellek veya CPU süresi tüketmesine neden olur. Hizmet reddi saldırıları, ayrıcalık saldırılarının yükselmesinden veya veri saldırılarının açıklanmasından daha az şiddetli olarak kabul edilir. Ancak, bir sunucunun XML belgelerini güvenilmeyen kaynaklardan işlemesi gereken bir senaryoda önemlidir.  
  
### <a name="exceptions-and-error-messages-might-reveal-data"></a>Özel Durumlar ve Hata İletileri Verileri Ortaya Çıkarabilir  
 Bir hatanın açıklaması, dönüştürülen veriler, dosya adları veya uygulama ayrıntıları gibi verileri ortaya çıkarabilir. Hata iletileri güvenilmeyen arayanlara maruz kalınmamalıdır. Tüm hataları yakalamalı ve kendi özel hata iletilerinizle hataları bildirmelisiniz.  
  
### <a name="do-not-call-codeaccesspermissionsassert-in-an-event-handler"></a>CodeAccessPermissions'u Aramayın.Bir Olay İşleyicisinde Öne Sür  
 Bir derlemenin daha az veya daha büyük izinleri olabilir. Daha büyük izinlere sahip bir derleme, bilgisayar ve ortamları üzerinde daha fazla denetime sahiptir.  
  
 Daha büyük izinlere sahip bir <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> derlemedeki kod bir olay işleyicisini çağırırsa ve ardından XML ağacı izinleri kısıtlanmış kötü amaçlı bir derlemeye geçerse, kötü amaçlı derleme bir olayın yükseltilmesine neden olabilir. Olay, derlemede daha büyük izinlerle kod çalıştırdığından, kötü amaçlı derleme daha sonra yükseltilmiş ayrıcalıklarla çalışır.  
  
 Microsoft, bir olay <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> işleyicisi aramanızı önermez.  
  
### <a name="dtds-are-not-secure"></a>DTD'ler Güvenli Değil  
 DTD'deki varlıklar doğal olarak güvenli değildir. Bir DTD içeren kötü amaçlı bir XML belgesinin, ayrıştırıcının tüm bellek ve CPU süresini kullanmasına neden olması ve hizmet reddi saldırısına neden olması mümkündür. Bu nedenle, LINQ'dan XML'e, DTD işleme varsayılan olarak kapatılır. Güvenilmeyen kaynaklardan DTD'leri kabul etmemelisiniz.  
  
 Güvenilmeyen kaynaklardan DTD'leri kabul etmeye bir örnek, Web kullanıcılarının Bir DTD ve DTD dosyasına başvuran bir XML dosyası yüklemesine olanak tanıyan bir Web uygulamasıdır. Dosyanın doğrulanması üzerine, kötü amaçlı bir DTD sunucunuzda bir hizmet reddi saldırısı gerçekleştirebilir. Güvenilmeyen kaynaklardan DTD kabul etmenin bir başka örneği de anonim FTP erişimine izin veren bir ağ paylaşımında DTD'ye başvurmaktır.  
  
### <a name="avoid-excessive-buffer-allocation"></a>Aşırı Arabellek Ayırmakaçının  
 Uygulama geliştiricileri, son derece büyük veri kaynaklarının kaynak tükenmesine ve hizmet reddi saldırılarına yol açabileceğini bilmelidir.  
  
 Kötü niyetli bir kullanıcı çok büyük bir XML belgesi gönderir veya yüklerse, LINQ'un XML'ye aşırı sistem kaynaklarını tüketmesine neden olabilir. Bu, hizmet reddi saldırısı oluşturabilir. Bunu önlemek için özelliği <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> ayarlayabilir ve yükleyebileceği belge boyutuyla sınırlı bir okuyucu oluşturabilirsiniz. Daha sonra XML ağacı oluşturmak için okuyucu kullanın.  
  
 Örneğin, güvenilmeyen bir kaynaktan gelen XML belgelerinizin beklenen maksimum boyutunun 100.000 olarak <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> ayarlanmış 50.0K bayttan az olacağını biliyorsanız. Bu, XML belgelerini işlemenizi engellemeyecek ve aynı zamanda büyük miktarda bellek tüketecek belgelerin yüklenebileceği hizmet reddi tehditlerini de azaltacaktır.  
  
### <a name="avoid-excess-entity-expansion"></a>Fazla Varlık Genişlemesinden Kaçının  
 DTD kullanırken bilinen hizmet reddi saldırılarından biri, aşırı varlık genişlemesine neden olan bir belgedir. Bunu önlemek için, <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=nameWithType> özelliği ayarlayabilir ve daha sonra varlık genişlemesinden kaynaklanan karakter sayısı yla sınırlı bir okuyucu oluşturabilirsiniz. Daha sonra XML ağacı oluşturmak için okuyucu kullanın.  
  
### <a name="limit-the-depth-of-the-xml-hierarchy"></a>XML Hiyerarşisinin Derinliğini Sınırlayın  
 Olası hizmet reddi saldırı, aşırı hiyerarşi derinliğine sahip bir belgenin gönderilmesidir. Bunu önlemek için, öğelerin derinliğini sayar kendi sınıfında bir <xref:System.Xml.XmlReader> sarın. Derinlik önceden belirlenmiş makul bir düzeyi aşarsa, kötü amaçlı belgenin işlenmesini sonlandırabilirsiniz.  
  
### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>Güvenilmeyen XmlReader veya XmlWriter Uygulamalarına Karşı Koruyun  
 Yöneticiler, dışarıdan sağlanan <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter> sağlanan uygulamaların güçlü adlara sahip olduğunu ve makine yapılandırmasında kaydedildiğini doğrulamalıdır. Bu, okuyucu veya yazar kılığına giren kötü amaçlı kodların yüklenmesini önler.  
  
### <a name="periodically-free-objects-that-reference-xname"></a>XName'ye Başvuran Periyodik Olarak Ücretsiz Nesneler  
 Belirli türdeki saldırılara karşı korunmak için, uygulama programcıları uygulama etki alanında bir <xref:System.Xml.Linq.XName> nesneye başvuran tüm nesneleri düzenli olarak serbest etmelidir.  
  
### <a name="protect-against-random-xml-names"></a>Rastgele XML Adlarına Karşı Koru  
 Güvenilmeyen kaynaklardan veri alan uygulamalar, rasgele <xref:System.Xml.XmlReader> XML adları ve ad alanları olasılığını incelemek için özel kodla sarılmış bir kullanarak düşünmelisiniz. Bu tür rasgele XML adları ve ad alanları algılanırsa, uygulama daha sonra kötü amaçlı belgenin işlenmesini sonlandırabilir.  
  
 Belirli bir ad alanındaki ad sayısını (ad alanında olmayan adlar dahil) makul bir sınırla sınırlamak isteyebilirsiniz.  
  
### <a name="annotations-are-accessible-by-software-components-that-share-a-linq-to-xml-tree"></a>Ek Açıklamalara, XML Ağacıyla LINQ Paylaşan Yazılım Bileşenleri Tarafından Erişilebilir  
 LINQ'dan XML'e, farklı uygulama bileşenlerinin XML ağaçları olarak bileşenler arasında geçirilen XML verilerini yüklediği, doğruladığı, sorguladığı, dönüştürdüğettiği, güncellediği ve kaydettiği işleme ardışık hatları oluşturmak için kullanılabilir. XML metnine nesneleri yükleme ve serileştirme yükü yalnızca ardışık yapının uçlarında yapıldığından, bu durum performansı en iyi duruma getirmede yardımcı olabilir. Ancak geliştiriciler, bir bileşen tarafından oluşturulan tüm ek açıklamaların ve olay işleyicilerinin diğer bileşenler tarafından erişilebilir olduğunun farkında olmalıdır. Bileşenlerin farklı güven düzeyleri varsa, bu güvenlik açıkları bir dizi oluşturabilirsiniz. Daha az güvenilen bileşenler arasında güvenli ardışık hatlar oluşturmak için, verileri güvenilmeyen bir bileşene aktarmadan önce LINQ'u XML nesnelerine XML metne seri hale getirmek gerekir.  
  
 Bazı güvenlik ortak dil çalışma zamanı (CLR) tarafından sağlanır. Örneğin, özel bir sınıf içermeyen bir bileşen, bu sınıf tarafından anahtarlanan ek açıklamalara erişemez. Ancak, ek açıklamalar onları okuyamayan bileşenler tarafından silinebilir. Bu bir tahrif atağı olarak kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu (LINQ - XML) (C#)](linq-to-xml-overview.md)
