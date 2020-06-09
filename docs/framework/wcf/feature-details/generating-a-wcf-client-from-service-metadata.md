---
title: Hizmet Meta Verilerinden WCF İstemcisi Oluşturma
ms.date: 03/30/2017
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
ms.openlocfilehash: ebf124b75e7c2b0feabfffb8c7e790b44749edb5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597377"
---
# <a name="generating-a-wcf-client-from-service-metadata"></a>Hizmet Meta Verilerinden WCF İstemcisi Oluşturma
Bu konu başlığı altında, meta veri belgelerinden istemciler oluşturmak için Svcutil. exe ' de çeşitli anahtarların nasıl kullanılacağı açıklanmaktadır.  
  
 Meta veri belgeleri, dayanıklı bir depolama üzerinde veya çevrimiçi olarak alınabilir. Çevrimiçi alma, WS-MetadataExchange protokolünü veya Microsoft Discovery (DISCO) protokolünü izler. Svcutil. exe meta verileri almak için eşzamanlı olarak aşağıdaki meta veri isteklerini yayınlar:  
  
- Belirtilen adrese WS-MetadataExchange (MEX) isteği.  
  
- Sağlanan adrese eklenen MEX isteği `/mex` eklendi.  
  
- DISCO isteği ( <xref:System.Web.Services.Discovery.DiscoveryClientProtocol> from ASP.NET Web hizmetlerinden yararlanarak) sağlanan adrese.  
  
 Svcutil. exe, hizmetten alınan Web Hizmetleri Açıklama Dili (WSDL) veya ilke dosyasını temel alarak istemciyi oluşturur. Kullanıcı asıl adı (UPN), Kullanıcı adının "" ile bitiştirerek \@ ve tam nitelikli etki alanı adı (FQDN) eklenerek oluşturulur. Ancak, Active Directory kaydolan kullanıcılar için, bu biçim geçerli değil ve aracın oluşturduğu UPN Kerberos kimlik doğrulamasında şu hata iletisiyle bir hataya neden oluyor: **oturum açma girişimi başarısız oldu.** Bu sorunu çözmek için, aracın ürettiği istemci dosyasını el ile onarın.  
  
```console
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## <a name="referencing-and-sharing-types"></a>Başvuru ve paylaşım türleri  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Reference\<file path>**|Belirtilen derlemedeki türlere başvurur. İstemcileri oluştururken, içeri aktarılmakta olan meta verileri temsil eden türleri içerebilen derlemeleri belirtmek için bu seçeneği kullanın.<br /><br /> Kısa biçim:`/r`|  
|**/excludeType:\<type>**|Başvurulan anlaşma türlerinden hariç tutulacak tam veya bütünleştirilmiş kod nitelikli bir tür adı belirtir.<br /><br /> Kısa biçim:`/et`|  
  
## <a name="choosing-a-serializer"></a>Serileştirici seçme  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/serileştirici: otomatik**|Seri hale getirici 'yi otomatik olarak seçer. Bu, `DataContract` serileştirici kullanır. Bu başarısız olursa, `XmlSerializer` kullanılır.<br /><br /> Kısa biçim:`/ser:Auto`|  
|**/Serializer: DataContractSerializer**|`DataContract`Serileştirme ve seri durumdan çıkarma için seri hale getirici kullanan veri türleri oluşturur.<br /><br /> Kısa biçim:`/ser:DataContractSerializer`|  
|**/Serializer: XmlSerializer**|`XmlSerializer`Serileştirme ve seri durumdan çıkarma için kullanan veri türleri oluşturur.<br /><br /> Kısa biçim:`/ser:XmlSerializer`|  
|**/ImportXmlTypes**|`DataContract`Seri hale getirici türlerini tür olarak içeri aktarmak için yapılandırır `DataContract` `IXmlSerializable` .<br /><br /> Kısa biçim:`/ixt`|  
|**/dataContractOnly**|Yalnızca türler için kod üretir `DataContract` . `ServiceContract`türler oluşturulur.<br /><br /> Bu seçenek için yalnızca yerel meta veri dosyalarını belirtmeniz gerekir.<br /><br /> Kısa biçim:`/dconly`|  
  
## <a name="choosing-a-language-for-the-client"></a>Istemci için dil seçme  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Language\<language>**|Kod üretimi için kullanılacak programlama dilini belirtir. Machine. config dosyasında kayıtlı bir dil adı ya da öğesinden devralan bir sınıfın tam adı sağlayın <xref:System.CodeDom.Compiler.CodeDomProvider> .<br /><br /> Değerler: c#, CS, CSharp, vb, vbs, VisualBasic, VBScript, JavaScript, c++, MC, cpp<br /><br /> Varsayılan: CSharp<br /><br /> Kısa biçim:`/l`<br /><br /> Daha fazla bilgi için bkz <xref:System.CodeDom.Compiler.CodeDomProvider> . sınıf.|  
  
## <a name="choosing-a-namespace-for-the-client"></a>Istemci için ad alanı seçme  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Namespace\<string,string>**|Bir WSDL veya XML şemasından `targetNamespace` ortak dil çalışma zamanı (CLR) ad alanına bir eşleme belirtir. `targetNamespace` `targetNamespaces` Bu clr ad alanına açık eşleme olmadan, haritalar için bir joker karakter (*) kullanın.<br /><br /> İleti sözleşmesi adının işlem adıyla çakışmadığından emin olmak için tür başvurusunu çift iki nokta () ile niteleyin `::` ya da adların benzersiz olduğundan emin olun.<br /><br /> Varsayılan: için şema belgesinin hedef ad alanından türetilir `DataContracts` . Varsayılan ad alanı, diğer tüm oluşturulan türler için kullanılır.<br /><br /> Kısa biçim:`/n`|  
  
## <a name="choosing-a-data-binding"></a>Veri bağlamayı seçme  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/enableDataBinding**|<xref:System.ComponentModel.INotifyPropertyChanged> `DataContract` Veri bağlamayı etkinleştirmek için tüm türlerde arabirimini uygular.<br /><br /> Kısa biçim:`/edb`|  
  
## <a name="generating-configuration"></a>Yapılandırma üretiliyor  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/config\<configFile>**|Oluşturulan yapılandırma dosyası için dosya adını belirtir.<br /><br /> Varsayılan: output. config|  
|**/mergeConfig**|Oluşturulan yapılandırmayı varolan dosyanın üzerine yazmak yerine var olan bir dosyada birleştirir.|  
|**/noConfig**|Yapılandırma dosyaları oluşturmamayın.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Verileri Kullanma](using-metadata.md)
- [Meta Veri Mimarisi Genel Bakış](metadata-architecture-overview.md)
