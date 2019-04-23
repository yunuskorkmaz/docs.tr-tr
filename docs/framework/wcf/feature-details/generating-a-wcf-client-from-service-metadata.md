---
title: Hizmet Meta Verilerinden WCF İstemcisi Oluşturma
ms.date: 03/30/2017
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
ms.openlocfilehash: 5cfbfc1e4be0003b3699f818212fbcd959f3ad91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078258"
---
# <a name="generating-a-wcf-client-from-service-metadata"></a>Hizmet Meta Verilerinden WCF İstemcisi Oluşturma
Bu konuda, meta veri belgelerinden istemci üretmek için Svcutil.exe içinde çeşitli anahtarları kullanmayı açıklar.  
  
 Meta veri belgelerini dayanıklı bir depolama alanında olabilir veya çevrimiçi olarak alınabilir. Çevrimiçi alma WS-MetadataExchange veya Microsoft bulma (ma) protokolü ya da izler. Aynı anda meta verilerini almak için aşağıdaki meta veri isteği svcutil.exe verir:  
  
-   Sağlanan adresi isteğine WS-MetadataExchange (MEX).  
  
-   İle sağlanan adresine MEX isteği `/mex` eklenir.  
  
-   DISCO isteği (kullanarak [DiscoveryClientProtocol](https://go.microsoft.com/fwlink/?LinkId=94777) ASP.NET Web hizmetlerinden) için sağlanan adresi.  
  
 Hizmetten alınan Web Hizmetleri Açıklama Dili (WSDL) veya ilke dosyasını bağlı olarak istemciye svcutil.exe oluşturur. Kullanıcı asıl adı (UPN) kullanıcı adı ile birleştirerek oluşturulur "\@" ve sonra bir tam etki alanı adı (FQDN) ekleme. Ancak, Active Directory'de kayıtlı kullanıcılar için bu biçimi geçerli değil ve aracının oluşturduğu UPN Kerberos kimlik doğrulaması şu hata iletisi ile neden olan hata: **Oturum açma girişimi başarısız oldu.** Bu sorunu çözmek için el ile aracı oluşturulan istemci dosyasını düzeltin.  
  
```  
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## <a name="referencing-and-sharing-types"></a>Başvuru ve tür paylaşımı  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/ reference:\<dosya yolu >**|Belirtilen bütünleştirilmiş kod başvuruları türleri. Oluşturma istemciler kullandığınızda bu seçeneği alınan meta verileri temsil eden türleri içerebilecek bütünleştirilmiş kodlar belirtmek için.<br /><br /> Kısa biçim: `/r`|  
|**/excludeType:\<türü >**|Başvurulan anlaşma türlerinin dışlanacak tam veya bütünleştirilmiş kodla nitelenen tür adı belirtir.<br /><br /> Kısa biçim: `/et`|  
  
## <a name="choosing-a-serializer"></a>Seri hale getirici seçme  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/serializer:Auto**|Serileştiriciyi otomatik olarak seçer. Bu kullanır `DataContract` serileştirici. Bu başarısız olursa, `XmlSerializer` kullanılır.<br /><br /> Kısa biçim: `/ser:Auto`|  
|**/serializer:DataContractSerializer**|Kullanan türleri oluşturur `DataContract` serileştirme ve seri durumundan çıkarma için seri hale getirici.<br /><br /> Kısa biçim: `/ser:DataContractSerializer`|  
|**/serializer:XmlSerializer**|Kullanan türleri oluşturur `XmlSerializer` serileştirme ve seri durumundan çıkarma için.<br /><br /> Kısa biçim: `/ser:XmlSerializer`|  
|**/importXmlTypes**|Yapılandırır `DataContract` olmayan içeri aktarmak için seri hale getirici`DataContract` olarak türleri `IXmlSerializable` türleri.<br /><br /> Kısa biçim: `/ixt`|  
|**/dataContractOnly**|İçin kod oluşturur `DataContract` yalnızca türleri. `ServiceContract` türler üretilir.<br /><br /> Yalnızca yerel meta veri dosyaları için bu seçeneği belirtmeniz gerekir.<br /><br /> Kısa biçim: `/dconly`|  
  
## <a name="choosing-a-language-for-the-client"></a>İstemci için dil seçme  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Language:\<dil >**|Kod oluşturma için kullanılacak programlama dilini belirtir. Öğesinden devralınan bir sınıf tam adı veya Machine.config dosyasında kayıtlı ya da bir dil adı sağlayın <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Değerler: c#, cs, csharp, vb, vbs, visualbasic, vbscript, javascript, c ++, mc, cpp<br /><br /> Varsayılan: csharp<br /><br /> Kısa biçim: `/l`<br /><br /> Daha fazla bilgi için [CodeDomProvider sınıfı](https://go.microsoft.com/fwlink/?LinkId=94778).|  
  
## <a name="choosing-a-namespace-for-the-client"></a>İstemci için bir Namespace seçme  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/ Namespace:\<string, string >**|Bir WSDL veya XML şema eşlemeyi belirtir `targetNamespace` için ortak dil çalışma zamanı (CLR) ad alanı. Joker karakter (*) kullanarak `targetNamespace` tüm eşler `targetNamespaces` söz konusu CLR ad alanına açık bir eşleme olmaksızın.<br /><br /> İleti sözleşmesi adı işlem adına sahip birbiriyle çakışır değil emin emin olmak için tür referansı çift iki nokta üst üste ile ya da uygun (`::`) veya adlarının benzersiz olduğundan emin olun.<br /><br /> Varsayılan: İçin şema belgesinin hedef ad alanından türetilir `DataContracts`. Varsayılan ad alanı diğer oluşturulan tüm türleri için kullanılır.<br /><br /> Kısa biçim: `/n`|  
  
## <a name="choosing-a-data-binding"></a>Veri bağlama seçme  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/enableDataBinding**|Implements <xref:System.ComponentModel.INotifyPropertyChanged> tüm arabirimi `DataContract` türleri veri bağlamasını etkinleştirmek için.<br /><br /> Kısa biçim: `/edb`|  
  
## <a name="generating-configuration"></a>Yapılandırma oluşturma  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/ config:\<configFile >**|Oluşturulan yapılandırma dosyası için dosya adını belirtir.<br /><br /> Varsayılan: output.config|  
|**/mergeConfig**|Varolan dosyanın üzerine yazmak yerine var olan bir dosya, oluşturulan yapılandırma birleştirir.|  
|**/ noconfig**|Yapılandırma dosyaları oluşturmaz.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Meta Veri Mimarisine Genel Bakış](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
