---
title: LINQ to XML güvenlik-LINQ to XML
description: LINQ to XML güvenlik sorunları ve güvenlik görünürlüğünü azaltmaya yönelik yollar hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: ef2c0dc9-ecf9-4c17-b24e-144184ab725f
ms.openlocfilehash: 72dd2bfe2a3f0edb69645daf4625ba24fb56732b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553333"
---
# <a name="linq-to-xml-security"></a>LINQ to XML güvenliği

Bu makalede, LINQ to XML ilişkili güvenlik sorunları açıklanmakta ve güvenlik açısından etkilenme konusunda rehberlik sunulmaktadır.

## <a name="linq-to-xml-security-overview"></a>LINQ to XML güvenliğe genel bakış

LINQ to XML, katı güvenlik gereksinimlerine sahip sunucu tarafı uygulamalardan daha fazla programlama kolaylığı için tasarlanmıştır. Çoğu XML senaryosu, bir sunucuya yüklenen güvenilmeyen XML belgelerini işlemek yerine, güvenilen XML belgelerinin işlenmesini içerir. LINQ to XML, bu senaryolar için iyileştirilmiştir.

Bilinmeyen kaynaklardan güvenilmeyen verileri işlemek istiyorsanız, Microsoft, <xref:System.Xml.XmlReader> BILINEN XML hizmet reddi (DOS) saldırılarını filtrelemek için yapılandırılmış bir sınıfının örneğini kullanmanızı önerir.

<xref:System.Xml.XmlReader>Hizmet reddi saldırılarını azaltmak için bir yapılandırdıysanız, bu okuyucuyu bir LINQ to XML ağacı doldurmak ve LINQ to XML programcı üretkenlik geliştirmelerinden faydalanmaya devam etmek için kullanabilirsiniz. Birçok azaltma tekniği, güvenlik sorununu hafifletmek üzere yapılandırılmış okuyucular oluşturmayı ve sonra yapılandırılmış okuyucu aracılığıyla bir XML ağacını örneklamayı içerir.

Belgeler boyut, derinlik, öğe adı boyutu ve daha fazlası için sınırsız olduğundan, XML, hizmet reddi saldırılarına karşı doğası gereği açıktır. XML işlemek için kullandığınız bileşenden bağımsız olarak, aşırı kaynak kullanıyorsa uygulama etki alanını geri dönüştürmeye her zaman hazırlıklı olmalısınız.

## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>XML, XSD, XPath ve XSLT saldırıları üzerinde risk azaltma

LINQ to XML, ve üzerine <xref:System.Xml.XmlReader> kurulmuştur <xref:System.Xml.XmlWriter> . LINQ to XML, <xref:System.Xml.Schema?displayProperty=nameWithType> ve ad alanlarındaki genişletme yöntemleri aracılığıyla XSD ve XPath 'i destekler <xref:System.Xml.XPath?displayProperty=nameWithType> . <xref:System.Xml.XmlReader>, <xref:System.Xml.XPath.XPathNavigator> , Ve <xref:System.Xml.XmlWriter> sınıflarını LINQ to XML Ile birlikte kullanarak XML AĞAÇLARıNı dönüştürmek için XSLT 'yi çağırabilirsiniz.

Daha az güvenli bir ortamda çalışıyorsanız, XML ile ilişkili birçok güvenlik sorunu ve,, ve içinde sınıfların kullanımı vardır <xref:System.Xml?displayProperty=nameWithType> <xref:System.Xml.Schema?displayProperty=nameWithType> <xref:System.Xml.XPath?displayProperty=nameWithType> <xref:System.Xml.Xsl?displayProperty=nameWithType> . Bu sorunlar şunlardır, ancak bunlarla sınırlı değildir:

- XSD, XPath ve XSLT, çok fazla zamanı veya belleği kullanan işlemleri belirtebileceğiniz dize tabanlı dillerdir. Bu, dizelerin kötü amaçlı olduğunu doğrulamak üzere güvenilmeyen kaynaklardan XSD, XPath veya XSLT dizeleri alan uygulama programcılarının sorumluluğundadır veya bu dizeleri değerlendirme olasılığını izleyip, sistem kaynak tüketimine yol açacağından emin olur.
- XSD şemaları (satır içi şemalar dahil), doğal olarak hizmet reddi saldırılarına karşı savunmasız kalır; Güvenilmeyen kaynaklardan şemaları kabul etmemeniz gerekir.
- XSD ve XSLT diğer dosyalara başvurular içerebilir ve bu tür başvurular, bölgeler arası ve etki alanları arası saldırılara yol açabilir.
- DTD 'lerde dış varlıklar, bölgeler arası ve etki alanları arası saldırılara yol açabilir.
- DTD 'Ler hizmet reddi saldırılarına karşı savunmasızdır.
- Daha fazla derin XML belgesi, hizmet reddi sorunları oluşturabilir; XML belgelerinin derinliğini kısıtlamak isteyebilirsiniz.
- <xref:System.Xml.NameTable> <xref:System.Xml.XmlNamespaceManager> Güvenilmeyen derlemelerden,, ve nesneleri gibi destekleyici bileşenleri kabul etmeyin <xref:System.Xml.XmlResolver> .
- Büyük belge saldırılarını azaltmak için öbeklerdeki verileri okuyun.
- XSLT stil sayfalarındaki betik blokları çok sayıda saldırı sunabilir.
- Dinamik XPath ifadelerini oluşturmadan önce dikkatle doğrulayın.

## <a name="linq-to-xml-security-issues"></a>LINQ to XML güvenlik sorunları

Bu makaledeki güvenlik sorunları belirli bir sırada sunulmaz. Tüm sorunlar önemlidir ve uygun şekilde ele alınmalıdır.

Başarılı bir ayrıcalık yükselmesi saldırısı, kendi ortamı üzerinde kötü amaçlı bir derlemeye daha fazla denetim sağlar. Başarılı bir ayrıcalık yükseltme saldırısı, verilerin açığa çıkmasına, hizmet reddine ve daha fazlasına neden olabilir.

Uygulamalar, verileri görme yetkisine sahip olmayan kullanıcılara verileri açıklamamalıdır.

Hizmet reddi saldırıları, XML ayrıştırıcısının veya LINQ to XML aşırı miktarda belleği veya CPU süresini kullanmasına neden olur. Hizmet reddi saldırıları, ayrıcalık saldırılarının yükseltilmesinin veya veri saldırılarının açıklanmasının daha az önemli olduğu kabul edilir. Ancak, bir sunucunun güvenilmeyen kaynaklardan XML belgelerini işlemesi gereken bir senaryoda önemli olurlar.

### <a name="dont-expose-error-messages-to-untrusted-callers"></a>Güvenilmeyen çağıranlara hata iletileri gösterme

Bir hatanın açıklaması, dönüştürülen veriler, dosya adları veya uygulama ayrıntıları gibi verileri açığa çıkarmayabilir. Hata iletileri güvenilmeyen çağıranlara gösterilmemelidir. Kendi özel hata mesajlarınız ile tüm hataları ve rapor hatalarını yakalamalı.

### <a name="dont-call-codeaccesspermissionsassert-in-an-event-handler"></a>CodeAccessPermissions çağrısı yapmayın. bir olay işleyicisindeki onaylama

Bir derlemenin daha az veya daha fazla izni olabilir. Daha fazla izne sahip bir derleme, bilgisayar ve ortamları üzerinde daha fazla denetime sahiptir.

Daha fazla izinlere sahip bir derlemedeki kod <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> bir olay işleyicide çağrılamışsa ve sonra XML ağacı kısıtlanmış izinlere sahip kötü amaçlı bir derlemeye geçirilirse, kötü amaçlı derleme bir olayın oluşturulmasına neden olabilir. Olay derlemede daha fazla izinle kod çalıştırdığı için kötü amaçlı derleme yükseltilmiş ayrıcalıklarla çalışır.

Microsoft bir olay işleyicisinde hiçbir şekilde çağrı yapmanızı önerir <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> .

### <a name="dont-accept-dtds-from-untrusted-sources"></a>Güvenilmeyen kaynaklardan DTD 'Leri kabul etme

DTD 'lerde varlıklar, doğal olarak güvenli değildir. Bir DTD içeren kötü amaçlı bir XML belgesi, ayrıştırıcısının tüm belleği ve CPU süresini kullanmasına neden olur ve bu da hizmet reddi saldırısına neden olur. Bu nedenle, LINQ to XML öğesinde DTD işleme varsayılan olarak kapalıdır. Güvenilmeyen kaynaklardan DTD 'Leri kabul etmemeniz gerekir.

Güvenilmeyen kaynaklardan DTD 'Leri kabul etmenin bir örneği, Web kullanıcılarının bir DTD 'ye ve DTD dosyasına başvuran bir XML dosyasını karşıya yüklemesine izin veren bir Web uygulamasıdır. Dosyanın doğrulanması sırasında, kötü amaçlı bir DTD sunucunuz üzerinde bir hizmet reddi saldırısı yürütebilir. Güvenilmeyen kaynaklardan DTD 'Lerin kabul edilmesi için başka bir örnek de, anonim FTP erişimine izin veren bir ağ paylaşımındaki bir DTD 'ye başvurulmalıdır.

### <a name="avoid-excessive-buffer-allocation"></a>Aşırı arabellek ayırmayı önleyin

Uygulama geliştiricileri, son derece büyük veri kaynaklarının kaynak tükenmesi ve hizmet reddi saldırılarına yol açabileceğini bilmelidir.

Kötü amaçlı bir Kullanıcı çok büyük bir XML belgesi gönderdiğinde veya karşıya yüklediğinde, LINQ to XML aşırı sistem kaynağı kullanmasına neden olabilir. Bu, bir hizmet reddi saldırısı oluşturabilir. Bunu engellemek için <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> özelliği ayarlayabilir ve daha sonra yükleyebilen belgenin boyutuyla sınırlı bir okuyucu oluşturabilirsiniz. Ardından, XML ağacı oluşturmak için okuyucuyu kullanın.

Örneğin, güvenilir olmayan bir kaynaktan gelen XML belgelerinin beklenen en büyük boyutunun 50K bayttan daha az olacağını biliyorsanız, <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> 100.000 olarak ayarlayın. Bu, XML belgelerinin işlenmesini içermez ve aynı zamanda, belgelerin karşıya yüklenmesi, büyük miktarlarda bellek tüketebileceği hizmet reddi tehditleri ortadan kaldırılır.

### <a name="avoid-excess-entity-expansion"></a>Aşırı varlık genişletmesinin önleyin

DTD kullanırken bilinen hizmet reddi saldırılarına bir, aşırı varlık genişlemesine neden olan bir belgedir. Bunu engellemek için <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=nameWithType> özelliğini ayarlayabilir ve daha sonra varlık genişletmesinden kaynaklanan karakter sayısında sınırlı bir okuyucu oluşturabilirsiniz. Ardından, XML ağacı oluşturmak için okuyucuyu kullanın.

### <a name="limit-the-depth-of-the-xml-hierarchy"></a>XML hiyerarşisinin derinliğini sınırlayın

Olası bir hizmet reddi saldırısı, çok sayıda hiyerarşi içeren bir belge gönderildiğinde gönderilir. Bunu engellemek için, <xref:System.Xml.XmlReader> öğelerin derinliğini sayan kendi sınıfınızla sardırabilirsiniz. Derinlik önceden belirlenmiş makul bir düzeyi aşarsa, kötü amaçlı belgeyi işlemeyi sonlandırabilirsiniz.

### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>Güvenilmeyen XmlReader veya XmlWriter uygulamalarına karşı koruma

Yöneticiler dışarıdan sağlanan <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter> uygulamaların, güçlü adlara sahip olduğunu ve makine yapılandırmasında kayıtlı olduğunu doğrulamalıdır. Bu, kötü amaçlı kodun bir okuyucu veya yazıcının yüklenmesini önler.

### <a name="periodically-free-objects-that-reference-xname"></a>XName 'e başvuran düzenli olarak ücretsiz nesneler

Uygulama programcılarının belirli türlerde saldırılara karşı korunması için, <xref:System.Xml.Linq.XName> uygulama etki alanındaki bir nesneye düzenli olarak başvuran tüm nesneleri boşaltmalıdır.

### <a name="protect-against-random-xml-names"></a>Rastgele XML adlarına karşı koruma

Güvenilmeyen kaynaklardan veri alan uygulamalar <xref:System.Xml.XmlReader> , rastgele XML adları ve ad alanları olasılığını denetlemek için özel kodda Sarmalanan bir kullanmayı göz önünde bulundurmalıdır. Bu tür rastgele XML adları ve ad alanları algılanırsa, uygulama kötü amaçlı belgenin işlenmesini sonlandırabilir.

Belirli bir ad alanındaki (ad alanı olmayan adlar dahil) ad sayısını makul bir sınıra sınırlamak isteyebilirsiniz.

### <a name="serialize-linq-to-xml-objects-to-xml-text-before-passing-the-data-to-an-untrusted-component"></a>Verileri güvenilmeyen bir bileşene geçirmeden önce nesneleri XML metnine serileştirme LINQ to XML

LINQ to XML, farklı uygulama bileşenlerinin XML ağaçları olarak bileşenler arasında geçirilen XML verilerini yükleme, doğrulama, sorgulama, dönüştürme, güncelleştirme ve kaydetme işlem hatlarını oluşturmak için kullanılabilir. Bu, XML metnine nesne yükleme ve serileştirilmesinin yükü yalnızca işlem hattının sonunda yapıldığından performansı iyileştirmenize yardımcı olabilir. Ancak geliştiriciler, bir bileşen tarafından oluşturulan tüm ek açıklamaların ve olay işleyicilerinin diğer bileşenler tarafından erişilebilir olduğunu bilmelidir. Bu, bileşenlerin farklı düzeylerde güven düzeyine sahip olması halinde bir dizi güvenlik açığı oluşturabilir. Daha az güvenilir bileşenlere güvenli işlem hatları oluşturmak için, verileri güvenilmeyen bir bileşene geçirmeden önce LINQ to XML nesneleri XML metnine serileştirmelidir.

Bazı güvenlik, ortak dil çalışma zamanı (CLR) tarafından sağlanır. Örneğin, özel bir sınıf içermeyen bir bileşen, bu sınıf tarafından anahtarlanan ek açıklamaların erişimine erişemez. Ancak, ek açıklamalar bunları okuyamıyorum bileşenler tarafından silinebilir. Bu, bir izinsiz saldırı olarak kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML genel bakış](linq-xml-overview.md)
