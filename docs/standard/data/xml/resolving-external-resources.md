---
title: Dış kaynakları çözümleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef31d101769dca00f5cff545c72b3afbd59bc638
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208737"
---
# <a name="resolving-external-resources"></a>Dış kaynakları çözümleme
**XmlResolver** özelliği **XmlDocument** tarafından kullanılan **XmlDocument** XML verisindeki dış belge türü gibi satır içi olmayan kaynakları bulmak için sınıfı tanımları (DTD'ler), varlıkları ve şemalar. Bu öğeleri bir ağ veya yerel bir sürücüde bulunan olabilir ve bir Tekdüzen Kaynak Tanımlayıcısı (URI) tarafından tanımlanabilir. Böylece **XmlDocument** çözümlenecek **EntityReference** belgede mevcut olduğundan ve doğrulamak belgenin dış DTD'nin veya şema göre düğümleri.  
  
## <a name="fully-trusted-xmldocument"></a>XmlDocument tam güvenilir  
 **XmlResolver** özelliği işlevselliğini etkiler **XmlDocument.Load** yöntemi. Aşağıdaki tabloda gösterildiği nasıl **XmlDocument.XmlResolver** özelliği çalışır **XmlDocument** nesne tam güvenilir değil. Aşağıdaki tabloda **XmlDocument.Load** yük giriş olduğunda yöntemleri bir **TextReader**, **dize**, **Stream**, veya  **URI**. Bu tablo için geçerli değildir **yük** yöntemi varsa **XmlDocument** gelen yüklü olduğu bir **XmlReader**.  
  
|XmlResolver özelliği|İşlev|Notlar|  
|--------------------------|--------------|-----------|  
|Özellik ayarlamak bir **XmlResolver** daha önce oluşturduğunuz ve zaten üzerinde kullanıcı tarafından ayarlanan özellikler olan sınıf.|**XmlDocument** kullanan **XmlResolver** DTD'ler ve varlık şemalarını gibi dış kaynaklara başvuruları çözümlemek için dosya adlarını çözümlemek için verilir.<br /><br /> **XmlResolver** ekleme veya düğümleri düzenlerken gereken dış kaynakları çözümleme yaparken de kullanılan **XmlDocument**.|**XmlResolver** verilen **XmlDocument** bulunan ve çözümlenen dış kaynaklara ihtiyaç duyduğunuzda, kullanılan çözümleyici.|  
|Özellik kümesine **null** (**hiçbir şey** Microsoft Visual Basic. NET'te).|Bir dış kaynağa gerektiren özellikler, dış bir şema veya DTD'nin bulma gibi desteklenmez. Ya da dış varlıklar çözümlenir ve gerçekleştirme İşlevler, düzenleme çözülmesi gereken varlık düğümleri ekleme gibi desteklenmez.|**XmlDocument** yükleri anonim olarak dosyaları ve diğer tüm kaynakları çözmek çalışmaz.|  
|Özelliği ayarlamak, ancak kalan varsayılan durumunda.|Bir **XmlUrlResolver** NULL ile kimlik bilgileri örneği ve tarafından kullanılan **XmlDocument** dış DTD, varlıkları ve şemaları, bulma, dosya adları çözümlerken ve **null** düğümleri düzenlerken kimlik bilgileri kullanılır.||  
  
 Aşağıdaki tabloda **XmlDocument.Load** yöntemi, giriş **yük** olduğu bir **XmlReader** ve **XmlDocument** olduğu tam olarak güvenilir.  
  
|XmlResolver özelliği|İşlev|Notlar|  
|--------------------------|--------------|-----------|  
|**XmlResolver** sınıfı tarafından kullanılan **XmlDocument** tarafından kullanılan aynı sınıfta **XmlReader**.|**XmlDocument** kullanan **XmlResolver** için atanma **XmlReader**.<br /><br /> **XmlDocument.Resolver** özelliği ayarlanmışsa, bakılmaksızın olamaz **XmlDocument** hale geliyor çünkü güven düzeyi, bir **XmlResolver** gelen  **XmlReader**. Ayarlarını geçersiz kılma girişiminde olamaz **XmlReaders**' **XmlResolver** ayarlayarak **XmlResolver** özelliği **XmlDocument**.|**XmlReader** olabilir **XmlTextReader**, **XmlValidatingReader**, veya özel olarak yazılmış bir okuyucu. Kullanılan okuyucu varlık çözümleme destekliyorsa, dış varlıklar çözümlenir. Okuyucu aktarılırsa varlık başvuruları, ardından başvuruları çözümlenmedi varlık desteklemez.|  
  
## <a name="semi-trusted-xmldocument"></a>Yarı güvenilir XmlDocument  
 Aşağıdaki tabloda nasıl **XmlDocument.XmlResolver** özelliği, nesne yarı güvenilir olduğunda çalışır. Bu tabloda uygulandığı **XmlDocument.Load** yük giriş olduğunda yöntemleri bir **TextReader**, **dize**, **Stream**, veya  **URI**. Bu tablo için geçerli değildir **yük** yöntemi varsa **XmlDocument** gelen yüklü olduğu bir **XmlReader**.  
  
|XmlResolver özelliği|İşlev|Notlar|  
|--------------------------|--------------|-----------|  
|Yarı güvenilir senaryoda **XmlResolver** null dışında hiçbir şeye özelliği ayarlanamaz.|Bir **XmlUrlResolver** ile **null** örneği ve tarafından kullanılan kimlik bilgilerini **XmlDocument** dış DTD, varlıklar, bulma, dosya adları çözümlerken ve şemaları ve **null** düğümleri düzenlerken kimlik bilgileri kullanılır.|Bu davranış, davranıştır aynıdır, **XmlResolver** özelliği değil ayarlayın, ancak kalan varsayılan durumunda.<br /><br /> **XmlDocument** tüm eylemler için anonim izinleri kullanır.|  
|Özellik kümesine **null** (**hiçbir şey** Microsoft Visual Basic. NET'te).|Bir dış şema veya DTD'nin bulma gibi bir dış kaynağa gerektiren herhangi bir özellik desteklenir. Ya da dış varlıklar çözümlenir ve gerçekleştirme, çözülmesi gereken varlık düğümleri ekleme gibi işlevleri düzenleme desteklenmiyor.|Özelliği olduğunda **null**, bakılmaksızın aynı ise davranıştır **XmlDocument** tam olarak güvenilen veya yarı güvenilir.|  
|Özelliği ayarlamak, ancak kalan varsayılan durumunda.|Bir **XmlUrlResolver** ile **null** örneği ve tarafından kullanılan kimlik bilgilerini **XmlDocument** dış DTD, varlıklar, bulma, dosya adları çözümlerken ve şemaları ve **null** düğümleri düzenlerken kimlik bilgileri kullanılır.|**XmlDocument** tüm eylemler için anonim izinleri kullanır.|  
  
 Bu tabloda uygulandığı **XmlDocument.Load** yöntemi, giriş **yük** olan bir **XmlReader**ve **XmlDocument** olan Yarı güvenilir.  
  
|XmlResolver özelliği|İşlev|Notlar|  
|--------------------------|--------------|-----------|  
|**XmlResolver** sınıfı tarafından kullanılan **XmlDocument** tarafından kullanılan hizmet örneğiyle aynı olan **XmlReader**.|**XmlDocument** kullanan **XmlResolver** için atanma **XmlReader**.<br /><br /> **XmlDocument.Resolver** özelliği ayarlanmışsa, bakılmaksızın olamaz **XmlDocument** hale geliyor çünkü güven düzeyi, bir **XmlResolver** gelen  **XmlReader**. Ayarlarını geçersiz kılma girişiminde olamaz **XmlReaders** **XmlResolver** ayarlayarak **XmlResolver** özelliği **XmlDocument**.|**XmlReader** olabilir **XmlTextReader**, doğrulama <xref:System.Xml.XmlReader>, veya özel olarak yazılmış bir okuyucu. Kullanılan okuyucu varlık çözümleme destekliyorsa, dış varlıklar çözümlenir. Geçirilen okuyucu varlık başvuruları desteklemiyorsa, varlık başvuruları çözümlenmiyor.|  
  
 XmlResolver doğru kimlik bilgilerini içerecek şekilde ayarlanması, dış kaynaklara erişim sağlar.  
  
> [!NOTE]
>  Alınacak bir yolu yoktur **XmlResolver** özelliği. Bir kullanıcının Engellemesi yardımcı olan bir **XmlResolver** hangi kimlik bilgilerini ayarlayın. Ayrıca, bir **XmlTextReader** veya doğrulama <xref:System.Xml.XmlReader> yüklemek için kullanılan **XmlDocument** ve **XmlDocument** gelen Çözümleyicileri ayarlanmış bir çözümleyici sahip Bu okuyucular tarafından önbelleğe alınmaz **XmlDocument** sonra **yük** aşama olduğundan, bu da güvenlik riski oluşturur.  
  
 Daha fazla bilgi için Açıklamalar bölümüne bakın. <xref:System.Xml.XmlResolver> başvuru sayfası.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
