---
title: "Dış kaynaklara çözme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 824a35ee5d4ecafc45167ff3f4bc89802af4ed96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="resolving-external-resources"></a>Dış kaynaklara çözme
**XmlResolver** özelliği **XmlDocument** tarafından kullanılan **XmlDocument** satır dış belge türü gibi XML verileri içinde olmayan kaynakları bulmak için sınıfı tanımları (DTD), varlıkları ve şemaları. Bu öğeler bir ağda veya yerel bir sürücüde yer alabilir ve bir Tekdüzen Kaynak Tanımlayıcısı (URI) göre tanımlanabilir. Böylece **XmlDocument** çözmek için **EntityReference** belgede mevcuttur ve dış DTD ya da şema göre belgeyi doğrulamak düğüm.  
  
## <a name="fully-trusted-xmldocument"></a>Tam güvenilir XmlDocument  
 **XmlResolver** özelliği işlevselliğini etkiler **XmlDocument.Load** yöntemi. Aşağıdaki tabloda gösterildiği nasıl **XmlDocument.XmlResolver** özelliği çalışır **XmlDocument** nesne tam olarak güvenilir değil. Aşağıdaki tabloda **XmlDocument.Load** giriş yük olduğunda yöntemleri bir **TextReader**, **dize**, **akış**, veya  **URI**. Bu tablo için geçerli değildir **yük** yöntemi varsa **XmlDocument** gelen yüklü olduğu bir **XmlReader**.  
  
|XmlResolver özelliği|İşlev|Notlar|  
|--------------------------|--------------|-----------|  
|Özellik kümesine bir **XmlResolver** daha önce oluşturduğunuz ve özellikleri zaten üzerinde kullanıcı tarafından ayarlanmış olan sınıf.|**XmlDocument** kullanan **XmlResolver** DTD, varlıkları ve şemaları gibi dış kaynaklara başvurular çözümlemek için dosya adları çözümlemek için verilir.<br /><br /> **XmlResolver** de ekleme veya düğümleri düzenlerken gerekli dış kaynaklara çözümlerken kullanılır **XmlDocument**.|**XmlResolver** verilen **XmlDocument** dış kaynaklara bulunan ve Çözüldü gerektiğinde, kullanılan çözümleyici.|  
|Özellik kümesine **null** (**hiçbir şey** Microsoft Visual Basic .NET içinde).|Dış kaynak gerektiren özellikleri, dış Şeması veya DTD bulma gibi desteklenmez. Ya da dış varlıklar çözümlenir ve gerçekleştirme İşlevler, düzenleme, çözüm gerektiren varlık düğümler ekleme gibi desteklenmez.|**XmlDocument** yükleri anonim olarak dosyaları ve diğer kaynakları çözümlemek çalışmaz.|  
|Özelliği ayarlanmış, ancak sol varsayılan durumu.|Bir **XmlUrlResolver** NULL ile kimlik bilgileri örneği ve olması tarafından kullanılan **XmlDocument** dış DTD, varlıkları ve şemaları, dosya adları çözümlerken ve **null** düğümleri düzenlerken kimlik bilgileri kullanılır.||  
  
 Aşağıdaki tabloda **XmlDocument.Load** yöntemi zaman girdisi **yük** olan bir **XmlReader** ve **XmlDocument** olduğu tam olarak güvenilir.  
  
|XmlResolver özelliği|İşlev|Notlar|  
|--------------------------|--------------|-----------|  
|**XmlResolver** sınıfı tarafından kullanılan **XmlDocument** tarafından kullanılan aynı sınıfı **XmlReader**.|**XmlDocument** kullanan **XmlResolver** için atanma **XmlReader**.<br /><br /> **XmlDocument.Resolver** özellik ayarlanmışsa, ne olursa olsun, olamaz **XmlDocument** elde etmektir çünkü güven düzeyi, bir **XmlResolver** gelen  **XmlReader**. Ayarlarını geçersiz kılmak girişimi olamaz **XmlReaders**' **XmlResolver** ayarlayarak **XmlResolver** özelliği **XmlDocument**.|**XmlReader** olabilir **XmlTextReader**, **XmlValidatingReader**, veya özel olarak yazılmış bir okuyucu. Kullanılan okuyucu varlık çözümleme destekliyorsa, dış varlıklar çözümlenir. Okuyucu aktarılırsa varlık başvuruları, ardından varlık başvuruları güvenilmedi desteklemez.|  
  
## <a name="semi-trusted-xmldocument"></a>Yarı güvenilen XmlDocument  
 Aşağıdaki tabloda nasıl **XmlDocument.XmlResolver** özelliği nesne yarı güvenilen olduğunda çalışır. Bu tablo uygulandığı **XmlDocument.Load** giriş yük olduğunda yöntemleri bir **TextReader**, **dize**, **akış**, veya  **URI**. Bu tablo için geçerli değildir **yük** yöntemi varsa **XmlDocument** gelen yüklü olduğu bir **XmlReader**.  
  
|XmlResolver özelliği|İşlev|Notlar|  
|--------------------------|--------------|-----------|  
|Yarı güvenilen senaryoda **XmlResolver** özelliği, null dışında bir şey için ayarlanamaz.|Bir **XmlUrlResolver** ile **null** örneği ve tarafından kullanılan kimlik bilgilerini **XmlDocument** dış DTD, varlıklar, bulma, dosya adları çözümlerken ve şemalar, ve **null** düğümleri düzenlerken kimlik bilgileri kullanılır.|Bu davranış için davranış aynı olduğunda **XmlResolver** özelliği olmayan ayarlanmış, ancak sol varsayılan durumu.<br /><br /> **XmlDocument** anonim izinlerini tüm eylemler için kullanır.|  
|Özellik kümesine **null** (**hiçbir şey** Microsoft Visual Basic .NET içinde).|Bir dış şema veya DTD bulma gibi dış kaynak gerektiren hiçbir özellikleri desteklenir. Ya da dış varlıklar çözümlenir ve gerçekleştirme çözümleme gerektiren varlık düğümler ekleme gibi işlevleri düzenleme desteklenmez.|Özellik olduğunda **null**, davranışı aynı bakılmaksızın ise **XmlDocument** tam olarak güvenilen veya yarı güvenilir.|  
|Özelliği ayarlanmış, ancak sol varsayılan durumu.|Bir **XmlUrlResolver** ile **null** örneği ve tarafından kullanılan kimlik bilgilerini **XmlDocument** dış DTD, varlıklar, bulma, dosya adları çözümlerken ve şemalar, ve **null** düğümleri düzenlerken kimlik bilgileri kullanılır.|**XmlDocument** anonim izinlerini tüm eylemler için kullanır.|  
  
 Bu tablo uygulandığı **XmlDocument.Load** yöntemi zaman girdisi **yük** olan bir **XmlReader**ve **XmlDocument** olduğu Yarı güvenilir.  
  
|XmlResolver özelliği|İşlev|Notlar|  
|--------------------------|--------------|-----------|  
|**XmlResolver** sınıfı tarafından kullanılan **XmlDocument** aynı tarafından kullanılmakta olan **XmlReader**.|**XmlDocument** kullanan **XmlResolver** için atanma **XmlReader**.<br /><br /> **XmlDocument.Resolver** özellik ayarlanmışsa, ne olursa olsun, olamaz **XmlDocument** elde etmektir çünkü güven düzeyi, bir **XmlResolver** gelen  **XmlReader**. Ayarlarını geçersiz kılmak girişimi olamaz **XmlReaders** **XmlResolver** ayarlayarak **XmlResolver** özelliği **XmlDocument**.|**XmlReader** olabilir **XmlTextReader**, doğrulama <xref:System.Xml.XmlReader>, veya özel olarak yazılmış bir okuyucu. Kullanılan okuyucu varlık çözümleme destekliyorsa, dış varlıklar çözümlenir. Geçirilen okuyucu varlık başvuruları desteklemiyorsa, varlık başvuruları çözümlenmeyen.|  
  
 Doğru kimlik bilgilerini içerecek şekilde XmlResolver ayarı dış kaynaklara erişim izni verir.  
  
> [!NOTE]
>  Almak mümkün **XmlResolver** özelliği. Bir kullanıcı yeniden kullanmalarını engellemek için bu yardımcı olan bir **XmlResolver** hangi kimlik bilgilerini ayarlayın. Ayrıca, bir **XmlTextReader** veya doğrulama <xref:System.Xml.XmlReader> yüklemek için kullanılan **XmlDocument** ve **XmlDocument** gelen çözümleyiciler ayarlanmış bir çözümleyici sahip Bu okuyucular tarafından önbelleğe alınmaz **XmlDocument** sonra **yük** aşama beri bu da güvenlik riski oluşturur.  
  
 Daha fazla bilgi için Açıklamalar bölümüne bakın <xref:System.Xml.XmlResolver> başvuru sayfası.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML belge nesne modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
