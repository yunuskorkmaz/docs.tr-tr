---
title: Hizmet Meta Verilerinden WCF İstemcisi Oluşturma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9eedf84d1dccb8bc2540aca7e6bd338b4e58326d
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="generating-a-wcf-client-from-service-metadata"></a>Hizmet Meta Verilerinden WCF İstemcisi Oluşturma
Bu konu, meta veri belgelerden istemcileri oluşturmak için Svcutil.exe içinde çeşitli anahtarları kullanmayı açıklar.  
  
 Meta veri belgelerini dayanıklı bir depolama alanında olabilir veya çevrimiçi alınmalıdır. Çevrimiçi alma WS-MetadataExchange veya Microsoft Discovery (DISCO) protokolü da izler. Aynı anda meta verilerini almak için şu meta veri isteklerini svcutil.exe verir:  
  
-   Sağlanan adresi isteğine WS-MetadataExchange (MEX).  
  
-   İle sağlanan adresine MEX isteği `/mex` eklenmiş.  
  
-   DISCO isteği (kullanarak [DiscoveryClientProtocol](http://go.microsoft.com/fwlink/?LinkId=94777) ASP.NET Web hizmetlerinden) için sağlanan adresi.  
  
 Svcutil.exe hizmetinden alınan Web Hizmetleri Açıklama Dili (WSDL) veya ilke dosyası bağlı olarak istemciye oluşturur. Kullanıcı adı ile birleştirerek kullanıcı asıl adı (UPN) oluşturulan "@" ve sonra bir tam etki alanı adı (FQDN) ekleme. Ancak, Active Directory'de kayıtlı kullanıcılar için bu biçimi geçerli değil ve aracı üretir UPN Kerberos kimlik doğrulaması şu hata iletisiyle neden olan hata: **oturum açma girişimi başarısız oldu.** Bu sorunu gidermek için el ile aracı oluşturulan istemci dosyası düzeltin.  
  
```  
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## <a name="referencing-and-sharing-types"></a>Başvuran ve türleri paylaşımı  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/ reference:\<dosya yolu >**|Belirtilen derleme başvuruları türleri. Ne zaman oluşturma istemciler, bu seçenek içeri aktarılan meta verileri temsil eden türleri içerebilir derlemeleri belirtmek için kullanın.<br /><br /> Kısa biçimi: `/r`|  
|**/excludeType:\<türü >**|Başvurulan sözleşme türlerinden çıkarılacak tam veya bütünleştirilmiş kod tam tür adını belirtir.<br /><br /> Kısa biçimi: `/et`|  
  
## <a name="choosing-a-serializer"></a>Seri hale getirici seçme  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/serializer:Auto**|Seri hale getirici otomatik olarak seçer. Bu kullanır `DataContract` seri hale getirici. Bu başarısız olursa, `XmlSerializer` kullanılır.<br /><br /> Kısa biçimi: `/ser:Auto`|  
|**/serializer:DataContractSerializer**|Kullandığınız veri türleri oluşturur `DataContract` seri hale getirme ve seri durumundan çıkarma için serileştirici.<br /><br /> Kısa biçimi: `/ser:DataContractSerializer`|  
|**/serializer:XmlSerializer**|Kullandığınız veri türleri oluşturur `XmlSerializer` seri hale getirme ve seri durumundan çıkarma için.<br /><br /> Kısa biçimi: `/ser:XmlSerializer`|  
|**/importXmlTypes**|Yapılandırır `DataContract` olmayan içeri aktarmak için seri hale getirici`DataContract` olarak türleri `IXmlSerializable` türleri.<br /><br /> Kısa biçimi: `/ixt`|  
|**/dataContractOnly**|İçin kod oluşturur `DataContract` yalnızca türleri. `ServiceContract` türleri oluşturulur.<br /><br /> Yalnızca yerel meta veri dosyaları için bu seçeneği belirtmeniz gerekir.<br /><br /> Kısa biçimi: `/dconly`|  
  
## <a name="choosing-a-language-for-the-client"></a>İstemci için bir dil seçme  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Language:\<dil >**|Kod oluşturma için kullanılacak programlama dilini belirtir. Machine.config dosyasının veya öğesinden devralınan bir sınıf tam adını kayıtlı ya da bir dil adı sağlayın <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Değerler: c#, cs, csharp, vb, vbs, visualbasic'tir, vbscript, javascript, c ++, mc, cpp<br /><br /> Varsayılan: csharp<br /><br /> Kısa biçimi: `/l`<br /><br /> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [CodeDomProvider sınıfı](http://go.microsoft.com/fwlink/?LinkId=94778).|  
  
## <a name="choosing-a-namespace-for-the-client"></a>İstemci için bir Namespace seçme  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/ Namespace:\<dize, dize >**|WSDL veya XML Şeması eşlemesinden belirtir `targetNamespace` bir ortak dil çalışma zamanı (CLR) ad. Joker karakter (*) kullanarak `targetNamespace` tüm eşlemeleri `targetNamespaces` bu CLR ad alanına açık bir eşleme olmadan.<br /><br /> İleti sözleşmesi adı işlemi adıyla birbiriyle çakışır değil, emin olmak için ya da çift iki nokta üst üste türü başvurusuyla nitelemek (`::`) veya adlarının benzersiz olduğundan emin olun.<br /><br /> Varsayılan: hedef ad alanı için şema belgenin türetilmiş `DataContracts`. Varsayılan ad alanı diğer oluşturulan türleri için kullanılır.<br /><br /> Kısa biçimi: `/n`|  
  
## <a name="choosing-a-data-binding"></a>Veri bağlama seçme  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/enableDataBinding**|Implements <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi tüm `DataContract` veri bağlamasına olanak sağlayan türleri.<br /><br /> Kısa biçimi: `/edb`|  
  
## <a name="generating-configuration"></a>Yapılandırma oluşturma  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/ config:\<configFile >**|Oluşturulan yapılandırma dosyası için dosya adını belirtir.<br /><br /> Varsayılan: output.config|  
|**/mergeConfig**|Varolan dosyanın üzerine yerine varolan bir dosyanın, üretilen yapılandırma birleştirir.|  
|**/noConfig**|Yapılandırma dosyaları oluşturmaz.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Meta Veri Mimarisine Genel Bakış](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
