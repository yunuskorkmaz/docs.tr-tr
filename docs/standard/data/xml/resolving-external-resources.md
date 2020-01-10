---
title: Dış Kaynakları Çözümleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
ms.openlocfilehash: 05cc41cef7da07581d4f0ec8e584858b913d1a80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710277"
---
# <a name="resolving-external-resources"></a>Dış Kaynakları Çözümleme
**XmlDocument** 'un **XMLRESOLVER** özelliği, XML verilerinde satır içi olmayan kaynakları bulmak için **XmlDocument** sınıfı tarafından, dış belge türü tanımları (DTD 'ler), varlıklar ve şemalar gibi kullanılır. Bu öğeler bir ağda veya yerel bir sürücüde bulunabilir ve bir Tekdüzen Kaynak tanımlayıcısı (URI) ile tanımlanabilir. Bu, **XmlDocument** 'nin belgede bulunan **EntityReference** düğümlerini ÇÖZÜMLEMESINE ve belgeyi dış DTD veya şemaya göre doğrulamasına olanak sağlar.  
  
## <a name="fully-trusted-xmldocument"></a>Tam güvenilir XmlDocument  
 **XmlResolver** özelliği, **XmlDocument. Load** yönteminin işlevlerini etkiler. Aşağıdaki **tabloda, XmlDocument nesnesi tam** olarak güvenilir olduğunda **XmlDocument. XmlResolver** özelliğinin nasıl çalıştığı gösterilmektedir. Aşağıdaki tabloda, Load girişi bir **TextReader**, **String**, **Stream**veya **URI**olduğunda **XmlDocument. Load** yöntemleri gösterilmektedir. **XmlDocument** bir **XmlReader**'dan yüklenirse, bu tablo **Load** yöntemine uygulanmaz.  
  
|XmlResolver özelliği|İşlev|Notlar|  
|--------------------------|--------------|-----------|  
|Özelliği, daha önce oluşturulmuş bir **XmlResolver** sınıfına ayarlanır ve Kullanıcı tarafından önceden ayarlanmış özellikler vardır.|**XmlDocument** , DTD 'ler, varlıklar ve şemalar gibi dış kaynaklara yönelik başvuruları çözümlemek için dosya adlarını çözümlemek Için verilen **XmlResolver** 'ı kullanır.<br /><br /> **XmlResolver** , **XmlDocument**içindeki düğümleri eklerken veya düzenlenirken gereken dış kaynakları çözümlerken de kullanılır.|**XmlDocument** 'A verilen **XmlResolver** , dış kaynakların bulunması ve çözümlenmesi gerektiğinde kullanılan çözümleyicindedir.|  
|Özelliği **null** (Microsoft Visual Basic .net 'te**hiçbir şey** ) olarak ayarlanır.|Dış bir kaynak gerektiren özellikler desteklenmez, örneğin bir dış şemayı veya DTD 'yi bulma. Dış varlıklar da çözülür ve çözümleme gerektiren varlık düğümleri ekleme gibi Düzenle işlevlerinin gerçekleştirilmesi desteklenmez.|**XmlDocument** dosyaları anonim olarak yükler ve diğer kaynakları çözmeyi denemez.|  
|Özellik ayarlanmadı, ancak varsayılan durumunda kaldı.|NULL kimlik bilgilerine sahip bir **XmlUrlResolver** , dosya adlarını çözümlemede, dış DTD 'lerin, varlıkların ve şemaların yerini alırken ve düğüm düzenlenirken **null** kimlik bilgileri kullanılırken **XmlDocument** tarafından oluşturulur.||  
  
 Aşağıdaki tabloda, **Load** girişi bir **XmlReader** olduğunda ve **XmlDocument** tam güvenilir olduğunda **XmlDocument. Load** yöntemi gösterilmektedir.  
  
|XmlResolver özelliği|İşlev|Notlar|  
|--------------------------|--------------|-----------|  
|**XmlDocument** tarafından kullanılan **XmlResolver** sınıfı, **XmlReader**tarafından kullanılan sınıftır.|**XmlDocument** , **XmlReader**'a atanan **XmlResolver** 'ı kullanır.<br /><br /> XmlDocument **. Resolver** özelliği, **XmlReader**'dan bir **XmlResolver** alındığından, **XmlDocument** güven düzeyinden bağımsız olarak ayarlanamaz. **XmlDocument**'un **XmlResolver** özelliğini ayarlayarak **xmlokuyucuları**' **XmlResolver** 'ın ayarlarını geçersiz kılmayı deneyemezsiniz.|**XmlReader** , **XmlTextReader**, **XmlValidatingReader**veya özel yazılı bir okuyucu olabilir. Kullanılan okuyucu varlık çözünürlüğünü destekliyorsa, dış varlıklar çözümlenir. Geçirilen okuyucu varlık başvurularını desteklemiyorsa, varlık başvuruları çözümlenmez.|  
  
## <a name="semi-trusted-xmldocument"></a>Yarı güvenilir XmlDocument  
 Aşağıdaki tabloda, nesne yarı güvenilir olduğunda **XmlDocument. XmlResolver** özelliğinin nasıl çalıştığı gösterilmektedir. Bu tablo, Load girişi bir **TextReader**, **String**, **Stream**veya **URI**olduğunda **XmlDocument. Load** yöntemleri için geçerlidir. **XmlDocument** bir **XmlReader**'dan yüklenirse, bu tablo **Load** yöntemine uygulanmaz.  
  
|XmlResolver özelliği|İşlev|Notlar|  
|--------------------------|--------------|-----------|  
|Yarı güvenilir senaryoda, **XmlResolver** özelliği null dışında bir şeye ayarlanamaz.|**Null** kimlik bilgilerine sahip bir **XmlUrlResolver** , dosya adlarını çözümlemede, dış DTD 'lerin, varlıkların ve şemaların yerini alırken ve düğüm düzenlenirken **null** kimlik bilgileri kullanılırken **XmlDocument** tarafından oluşturulur.|Bu davranış, **XmlResolver** özelliği ayarlanmamışsa, ancak varsayılan durumunda bırakılırsa, davranışla aynıdır.<br /><br /> **XmlDocument** tüm eylemler için anonim izinleri kullanır.|  
|Özelliği **null** (Microsoft Visual Basic .net 'te**hiçbir şey** ) olarak ayarlanır.|Dış bir şemayı veya DTD 'yi bulma gibi bir dış kaynak gerektirmeyen hiçbir özellik desteklenmez. Dış varlıklar da çözümlenir ve çözümleme gerektiren varlık düğümleri ekleme gibi işlevleri de gerçekleştirmek desteklenmez.|Özelliği **null**olduğunda, **XmlDocument** tamamen güvenilir veya yarı güvenilir olmasına bakılmaksızın davranış aynı olur.|  
|Özellik ayarlanmadı, ancak varsayılan durumunda kaldı.|**Null** kimlik bilgilerine sahip bir **XmlUrlResolver** , dosya adlarını çözümlemede, dış DTD 'lerin, varlıkların ve şemaların yerini alırken ve düğüm düzenlenirken **null** kimlik bilgileri kullanılırken **XmlDocument** tarafından oluşturulur.|**XmlDocument** tüm eylemler için anonim izinleri kullanır.|  
  
 Bu tablo, **Load** girişi bir **XmlReader**olduğunda ve **XmlDocument** yarı güvenilir olduğunda **XmlDocument. Load** yöntemi için geçerlidir.  
  
|XmlResolver özelliği|İşlev|Notlar|  
|--------------------------|--------------|-----------|  
|**XmlDocument** tarafından kullanılan **XmlResolver** sınıfı, **XmlReader**tarafından kullanılan bir.|**XmlDocument** , **XmlReader**'a atanan **XmlResolver** 'ı kullanır.<br /><br /> XmlDocument **. Resolver** özelliği, **XmlReader**'dan bir **XmlResolver** alındığından, **XmlDocument** güven düzeyinden bağımsız olarak ayarlanamaz. **XmlDocument**'un **XmlResolver** özelliğini ayarlayarak **xmlokuyucuları** **XmlResolver** 'ın ayarlarını geçersiz kılmayı deneyemezsiniz.|**XmlReader** , **xmltextreader**, <xref:System.Xml.XmlReader>veya özel olarak yazılmış bir okuyucu olabilir. Kullanılan okuyucu varlık çözünürlüğünü destekliyorsa, dış varlıklar çözümlenir. Geçirilen okuyucu varlık başvurularını desteklemiyorsa, varlık başvuruları çözümlenmez.|  
  
 XmlResolver 'ın doğru kimlik bilgilerini içerecek şekilde ayarlanması, dış kaynaklara erişime izin verir.  
  
> [!NOTE]
> **XmlResolver** özelliğini almanın bir yolu yoktur. Bu, bir kullanıcının kimlik bilgilerinin ayarlandığı bir **XmlResolver** 'ı yeniden kullanmasını önlemeye yardımcı olur. Ayrıca, **XmlDocument** 'yi yüklemek Için bir **XmlTextReader** veya doğrulama <xref:System.Xml.XmlReader> kullanılırsa ve **XmlDocument** ayarlanmış bir çözümleyici 'ye sahipse, bu okuyuculardan gelen çözümleyiciler **yükleme** aşamasından sonra **XmlDocument** tarafından önbelleğe alınmaz, çünkü bu da bir güvenlik riski oluşturur.  
  
 Daha fazla bilgi için <xref:System.Xml.XmlResolver> başvuru sayfasının açıklamalar bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
