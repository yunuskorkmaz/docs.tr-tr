---
title: ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- clients [WCF], building
- endpoints [WCF]
- Svcutil.exe
- clients [WCF], consuming services
ms.assetid: 1abf3d9f-b420-46f1-b628-df238751f308
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ce66f98f064ec5c9460dd1909f8eb7bc44c26f76
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
---
# <a name="servicemodel-metadata-utility-tool-svcutilexe"></a>ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)
ServiceModel meta veri yardımcı programracı meta veri belgelerini ve meta veri belgelerini hizmet modeli kodundan hizmet modeli kodu oluşturmak için kullanılır.  
  
## <a name="svcutilexe"></a>SvcUtil.exe  
 ServiceModel meta veri yardımcı Programracı Windows SDK yükleme konumunda bulunabilir özellikle, C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin  
  
### <a name="functionalities"></a>İşlevler  
 Aşağıdaki tabloda, bu aracı ve nasıl kullanıldığı açıklanır ilgili konu tarafından sağlanan çeşitli işlevleri özetlenmiştir.  
  
|Görev|Konu|  
|----------|-----------|  
|Hizmet veya statik meta veri belgelerini çalışmasını kod oluşturur.|[Hizmet Meta Verilerinden WCF İstemcisi Oluşturma](../../../docs/framework/wcf/feature-details/generating-a-wcf-client-from-service-metadata.md)|  
|Meta veri belgelerini derlenmiş kodundan dışa aktarır.|[Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)|  
|Derlenmiş hizmet kodunu doğrular.|[Nasıl yapılır: Derlenmiş Hizmet Kodunu Doğrulamak için Svcutil.exe Kullanma](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)|  
|Meta veri belgelerini Hizmetleri çalıştıran indirir.|[Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)|  
|Seri hale getirme kod oluşturur.|[Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)|  
  
> [!CAUTION]
>  Parametre olarak sağlanan adlarının özdeş ise Svcutil bir disk üzerinde var olan dosyaların üzerine yazar. Bu kod dosyaları, yapılandırma veya meta veri dosyaları içerebilir. Bu kod ve yapılandırma uçarak oluştururken önlemek için `/mergeConfig` geçin.  
>   
>  Ayrıca, `/r` ve `/ct` türlerine başvurma için anahtarlar şunlardır veri sözleşmeleri oluşturmak için. XmlSerializer kullanırken, bu anahtarlar çalışmaz.  
  
### <a name="timeout"></a>Zaman aşımı  
 Araç, meta verileri alınırken bir 5 dakikalık zaman aşımı sahiptir.  Bu zaman aşımı yalnızca ağ üzerinden meta verilerini alma için geçerlidir. Bu meta verileri herhangi bir işlem için geçerli değildir.  
  
### <a name="multi-targetting"></a>Çoklu atamak  
 Aracı çoklu sürüm desteği desteklemez. Svcutil.exe .NET 4 yapı oluşturmak istiyorsanız, .NET 4 SDK svcutil.exe kullanmak zorunda. .NET 3.5 yapı oluşturmak için yürütülebilir dosyadan .NET 3.5 SDK'yı kullanın.  
  
### <a name="accessing-wsdl-documents"></a>WSDL belgeleri erişme  
 Bir güvenlik belirteci hizmeti (STS) başvuruyor WSDL belgeye erişmek için Svcutil kullandığınızda Svcutil STS çağrısı bir WS-MetadataExchange yapar. Ancak, hizmet WS-MetadataExchange veya HTTP GET kullanarak kendi WSDL belgeleri getirebilir. Bu nedenle, STS yalnızca kullanıma sunulan, HTTP GET, yazılan bir istemci kullanarak WSDL belgesi [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] başarısız olur. Yazılan istemciler için [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], Svcutil hem WS-MetadataExchange kullanmak deneyecek ve HTTP GET STS WSDL elde edilir.  
  
## <a name="using-svcutilexe"></a>Using SvcUtil.exe  
  
### <a name="common-usages"></a>Ortak kullanımlar  
 Aşağıdaki tabloda bazı yaygın olarak bu araç için kullanılan seçenekler gösterilmektedir.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|/ directory:\<dizin >|Dosyaları oluşturmak için dizin.<br /><br /> Varsayılan: Geçerli dizin.<br /><br /> Kısa biçimi: `/d`|  
|/help|Araç için komut sözdizimini ve seçenekleri görüntüler.<br /><br /> Kısa biçimi: `/?`|  
|/noLogo|Telif hakkı ve başlık iletisi engelleyin.|  
|/svcutilConfig:\<configFile>|App.config dosyasında yerine kullanılacak özel bir yapılandırma dosyasına belirtir. Bu aracın yapılandırma dosyası değiştirmeden system.serviceModel uzantıları kaydetmek için kullanılabilir.|  
|/ target:\<çıktı türü >|Aracı tarafından oluşturulan çıkış belirtir.<br /><br /> Geçerli kod, meta verileri veya xmlSerializer değerleridir.<br /><br /> Kısa biçimi: `/t`|  
  
### <a name="code-generation"></a>Kod Üretimi  
 Svcutil.exe meta verileri belgelerden Hizmet sözleşmeleri, istemciler ve veri türleri için kod oluşturabilirsiniz. Bu meta veri belgelerini dayanıklı bir depolama üzerinde olabilir ya da çevrimiçi alınmalıdır. İçin (ayrıntıları meta veri yükleme bölümüne bakın) WS-Metadata değişimi veya DISCO Protokolü ya da çevrimiçi alma izler.  
  
 Önceden tanımlanmış bir WSDL belgeyi temel alarak hizmeti ve veri sözleşmeleri oluşturmak için SvcUtil.exe aracını kullanabilirsiniz. /ServiceContract anahtarını kullanın ve burada WSDL belgesinde indirilen bulunamadı veya değiştirilebilir URL veya dosya konumu belirtin. Bu, daha sonra uyumlu hizmet uygulamak için kullanılabilir WSDL belgesinde tanımlanan hizmeti ve veri sözleşmeleri oluşturur. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Nasıl yapılır: meta verileri alma ve uyumlu bir hizmet ekleme](../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md).  
  
 BasicHttpContextbinding uç noktası ile bir hizmet için Svcutil.exe BasicHttpBinding ile oluşturur `allowCookies` özniteliğini `true` yerine. Tanımlama bilgileri, sunucu üzerindeki bağlamı için kullanılır. Hizmet tanımlama bilgileri kullandığında istemcide bağlam yönetmek istiyorsanız, bir bağlam bağlama kullanmak üzere yapılandırma el ile değiştirebilirsiniz.  
  
> [!CAUTION]
>  Svcutil.exe hizmetinden alınan WSDL veya ilke dosyası bağlı olarak istemciye oluşturur. Kullanıcı adı, birleştirerek kullanıcı asıl adı (UPN) oluşturulan "@" ve tam etki alanı adı (FQDN). Ancak, Active Directory'de kayıtlı kullanıcılar için bu biçimi geçerli değil ve aracı tarafından oluşturulan UPN "oturum açma girişimi başarısız oldu" hata iletisiyle Kerberos kimlik doğrulamasındaki hata neden olur. Bu sorunu gidermek için bu aracı tarafından oluşturulan istemci dosyası el ile düzeltmeniz.  
  
 `svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>`  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`epr`|WS-adresleme EndpointReference WS-Metadata değişimi destekleyen bir hizmet uç noktası için içeren bir XML dosyası yolu. Daha fazla bilgi için meta veri yükleme bölümüne bakın.|  
|`metadataDocumentPath`|Koda (.wsdl, .xsd, .wspolicy veya .wsmex) almak için sözleşme içeren bir meta veri belgesi (wsdl veya xsd) yolu.<br /><br /> Svcutil içeri aktarmalar izler ve meta verileri için uzak bir URL belirttiğinizde içerir. Ancak, yerel dosya sistemi meta veri dosyalarını işlemek istiyorsanız, tüm dosyaları bu bağımsız değişkeni belirtmeniz gerekir. Bu şekilde, ağ bağımlılıkları burada olamaz Svcutil bir yapı ortamı kullanabilirsiniz. Joker karakterleri kullanabilirsiniz (*.xsd, \*.wsdl) bu bağımsız değişken için.|  
|`url`|Meta veri sağlayan bir hizmet uç noktası veya çevrimiçi barındırılan bir meta veri belgesi URL'si. Bu belgeleri nasıl alınır daha fazla bilgi için meta veri yükleme bölümüne bakın.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|/Async|Her iki zaman uyumlu ve zaman uyumsuz yöntem imzaları oluşturur.<br /><br /> Varsayılan: yalnızca zaman uyumlu yöntemi imzalar oluşturur.<br /><br /> Kısa biçimi: `/a`|  
|/collectionType:\<türü >|Liste koleksiyonu türü WCF istemcisi için belirtir.<br/><br /> Varsayılan: Koleksiyon System.Array türüdür. <br /><br /> Kısa biçimi: `/ct`|  
|/config:\<configFile>|Oluşturulan yapılandırma dosyası için dosya adını belirtir.<br /><br /> Varsayılan: output.config|  
|/dataContractOnly|Veri sözleşmesi yalnızca türleri için kod oluşturur. Hizmet sözleşmesi türleri oluşturulmaz.<br /><br /> Yalnızca yerel meta veri dosyaları için bu seçeneği belirtmeniz gerekir.<br /><br /> Kısa biçimi: `/dconly`|  
|/enableDataBinding|Implements <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi veri bağlamasını etkinleştirmek için tüm veri sözleşmesi türler.<br /><br /> Kısa biçimi: `/edb`|  
|/excludeType:\<türü >|Başvurulan sözleşme türlerinden çıkarılacak tam veya bütünleştirilmiş kod tam tür adını belirtir.<br /><br /> Bu anahtarı ile birlikte kullanırken `/r` ayrı DLL'lerden XSD sınıfın tam adını başvuruluyor.<br /><br /> Kısa biçimi: `/et`|  
|/importXmlTypes|Veri sözleşmesi türleri IXmlSerializable türleri olarak almak için veri sözleşmesi seri hale getirici yapılandırır.|  
|/ İç|Dahili olarak işaretlenmiş sınıfları oluşturur. Varsayılan: yalnızca genel sınıfları oluşturur.<br /><br /> Kısa biçimi: `/i`|  
|/Language:\<dil >|Kod oluşturma için kullanılacak programlama dilini belirtir. Machine.config dosyasında kayıtlı bir dil adı veya öğesinden devralınan bir sınıf tam adı sağlamalıdır <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Değerler: c#, cs, csharp, vb, visualbasic'tir, c ++, cpp<br /><br /> Varsayılan: csharp<br /><br /> Kısa form: `/l` **Not:** anahtar yalnızca Visual Studio 2005 SP1 ile birlikte gelen kod sağlayıcısı için C++ destekler.|  
|/mergeConfig|Varolan dosyanın üzerine yerine varolan bir dosyanın, üretilen yapılandırma birleştirir.|  
|/messageContract|İleti sözleşmesi türleri oluşturur.<br /><br /> Kısa biçimi: `/mc`|  
|/ Namespace:\<dize, dize >|WSDL veya XML Şeması targetNamespace eşleme CLR ad belirtir. Kullanarak '\*' targetNamespace o CLR ad alanına açık bir eşleme olmadan tüm targetNamespaces eşler için.<br /><br /> İleti sözleşmesi adı işlemi adıyla birbiriyle çakışır değil, emin olmak için ya da türü başvurusuyla nitelemek `::`, veya adlarının benzersiz olduğundan emin olun.<br /><br /> Varsayılan: şema belgesi hedef ad alanından veri sözleşmeleri için türetilmiş. Varsayılan ad alanı diğer oluşturulan türleri için kullanılır.<br /><br /> Kısa süreli: `/n` **Not:** XmlSerializer ile kullanmak için türlerinden oluştururken, yalnızca tek bir ad eşlemesi desteklenir. Tüm oluşturulan türleri ya da varsayılan ad alanını veya tarafından belirtilen ad alanı olacak ' *'.|  
|/noConfig|Yapılandırma dosyaları oluşturmaz.|  
|/noStdLib|Standart kitaplıkları başvuruda bulunmayın.<br /><br /> Varsayılan: Mscorlib.dll ve System.servicemodel.dll başvurulur.|  
|/ out:\<dosyası >|Oluşturulan kodun dosya adını belirtir.<br /><br /> Varsayılan: WSDL tanımı adından türetilen, WSDL hizmet adı veya ad alanı şemalardan birine hedefleyin.<br /><br /> Kısa biçimi: `/o`|  
|/ reference:\<dosya yolu >|Belirtilen derleme başvuruları türleri. Ne zaman oluşturma istemciler, bu seçenek içeri aktarılan meta verileri temsil eden türleri içerebilir derlemeleri belirtmek için kullanın.<br /><br /> İleti sözleşmeleri belirtemezsiniz ve <xref:System.Xml.Serialization.XmlSerializer> bu anahtarı kullanarak türleri.<br /><br /> Varsa <xref:System.DateTimeOffset> başvurulan, bu türü yeni bir tür oluşturan yerine kullanılır. Uygulama kullanılarak yazılmışsa [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], SvcUtil.exe başvuruları <xref:System.DateTimeOffset> otomatik olarak.<br /><br /> Kısa biçimi: `/r`|  
|/ seri hale getirilebilir|Seri hale getirilebilir özniteliğiyle işaretlenmiş sınıfları oluşturur.<br /><br /> Kısa biçimi: `/s`|  
|/serviceContract|Yalnızca hizmet sözleşmeleri için kod oluşturur. İstemci sınıfı ve yapılandırma oluşturulmaz<br /><br /> Kısa biçimi: `/sc`|  
|/serializer:Auto|Otomatik olarak seri hale getirici seçin. Bu veri sözleşmesi seri hale getirici kullanmayı dener ve başarısız olursa XmlSerializer kullanır.<br /><br /> Kısa biçimi: `/ser`|  
|/serializer:DataContractSerializer|Veri sözleşmesi seri hale getirici seri hale getirme ve seri durumundan çıkarma için kullandığınız veri türleri oluşturur.<br /><br /> Kısa biçimi: `/ser:DataContractSerializer`|  
|/serializer:XmlSerializer|Kullandığınız veri türleri oluşturur <xref:System.Xml.Serialization.XmlSerializer> seri hale getirme ve seri durumundan çıkarma için.<br /><br /> Kısa biçimi: `/ser:XmlSerializer`|  
|/targetClientVersion|Hangi sürümünü belirtin [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uygulama hedefleme. Geçerli değerler `Version30` ve `Version35`. Varsayılan değer `Version30` şeklindedir.<br /><br /> Kısa biçimi: `/tcv`<br /><br /> `Version30`: Kullanın `/tcv:Version30` kullanan istemciler için kod oluşturma, [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)].<br /><br /> `Version35`: Kullanın `/tcv:Version35` kullanan istemciler için kod oluşturma, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Kullanırken `/tcv:Version35` ile `/async` geçin, hem olay tabanlı ve geri çağırma/temsilci tabanlı zaman uyumsuz yöntemleri oluşturulur. Ayrıca, veri kümeleri için LINQ etkin destekler ve <xref:System.DateTimeOffset> etkinleştirilir.|  
|/ Sarmalanan|Özel büyük/küçük harf Sarmalanan parametrelerle belgeleri biçimlendirilmiş belge-sabit değer için kullanılıp kullanılmadığını denetler. Kullanım **/ Sarmalanan** anahtarı ile [hizmet Model meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) normal büyük/küçük harf belirtmek için aracı.|  
  
> [!NOTE]
>  Hizmet bağlaması olduğunda sistem tarafından sağlanan bağlamalar birini (bkz [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md)) ve <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliği ayarlanmış olarak `None` veya `Sign`, Svcutil oluşturur kullanarak bir yapılandırma dosyası [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) beklenen Sistem tarafından sağlanan öğe yerine öğesi. Hizmeti kullanıyorsa, örneğin, `<wsHttpBinding>` öğeyle `ProtectionLevel` kümesine `Sign`, oluşturulan yapılandırmasına sahip `<customBinding>` yerine bağlamaları bölümündeki `<wsHttpBinding>`. Koruma düzeyi hakkında daha fazla bilgi için bkz: [anlama koruma düzeyi](../../../docs/framework/wcf/understanding-protection-level.md).  
  
### <a name="metadata-export"></a>Meta veri dışarı aktarma  
 Svcutil.exe Hizmetleri, sözleşmeler ve derlenmiş derlemelerde veri türlerini meta verilerini dışa aktarabilirsiniz. Bir hizmet için meta verileri dışarı aktarmak için kullanmanız gerekir `/serviceName` seçeneği dışarı aktarmak istediğiniz hizmeti belirtin. Derlemedeki tüm veri sözleşme türleri dışarı aktarmak için kullanmalısınız `/dataContractOnly` seçeneği. Varsayılan olarak, tüm hizmet sözleşmeleri giriş derlemelerde meta verileri dışarı aktarılır.  
  
 `svcutil.exe [/t:metadata] [/serviceName:<serviceConfigName>] [/dataContractOnly] <assemblyPath>*`  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`assemblyPath`|Dışa aktarılacak Hizmetleri, sözleşmeler ya da veri sözleşmesi türlerini içeren bir derleme yolu belirtir. Standart komut satırı joker karakterleri, birden çok dosya giriş olarak sağlamak için kullanılabilir.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|/serviceName:\<serviceConfigName>|Dışa aktarılacak bir hizmet yapılandırması adını belirtir. Bu seçenek kullanılırsa, ilişkili bir yapılandırma dosyası yürütülebilir bir derleme giriş olarak geçirilmelidir. Svcutil.exe hizmeti yapılandırması için tüm ilişkili yapılandırma dosyalarını arar. Yapılandırma dosyalarını herhangi bir uzantı türü içeriyorsa, bu tür içeren derlemeler ya da GAC içinde olmalıdır ya da açıkça kullanarak sağlanan `/reference` seçeneği.|  
|/ reference:\<dosya yolu >|Belirtilen derleme, tür başvuruları çözümlemek için kullanılan derlemeler kümesini ekler. Dışarı aktarma veya kullanan bir hizmet doğrulama yapılandırmada 3. taraf uzantıları (davranışları, bağlamaları ve BindingElements) kayıtlı, GAC içinde olmayan uzantısı derlemeleri bulmak için bu seçeneği kullanın.<br /><br /> Kısa biçimi: `/r`|  
|/dataContractOnly|Yalnızca sözleşme türleri veriler üzerinde çalışıyor. Hizmet sözleşmeleri işlenmez.<br /><br /> Yalnızca yerel meta veri dosyaları için bu seçeneği belirtmeniz gerekir.<br /><br /> Kısa biçimi: `/dconly`|  
|/excludeType:\<türü >|Verme etki alanından çıkarılacak bir türün tam veya bütünleştirilmiş kod tam adını belirtir. Dışarı aktarılan türlerini dışarıda bırakmak bir dizi Hizmet sözleşmeleri veya bir hizmet için meta verileri dışarı aktarılırken bu seçeneği kullanılabilir. Bu seçenek ile birlikte kullanılamaz `/dconly` seçeneği.<br /><br /> Birden çok hizmetleri içeren tek bir derleme varsa ve her ayrı sınıf ile aynı XSD adı kullanır, bu anahtar için XSD sınıf adı yerine hizmet adı belirtmeniz gerekir.<br /><br /> XSD veya veri sözleşme türleri desteklenmez.<br /><br /> Kısa biçimi: `/et`|  
  
### <a name="service-validation"></a>Hizmet doğrulama  
 Doğrulama hataları barındırma hizmeti olmadan hizmet uygulamalarında algılamak için kullanılabilir. Kullanmalısınız `/serviceName` doğrulamak istediğiniz hizmetin belirtmek için seçenek.  
  
 `svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*`  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`assemblyPath`|Doğrulanacak hizmet türlerini içeren bir derleme yolu belirtir. Derleme hizmet yapılandırmasını sağlamak için ilişkili bir yapılandırma dosyası olmalıdır. Standart komut satırı joker karakterleri, birden çok derleme sağlamak için kullanılabilir.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|/ Doğrula|Bir hizmet uygulaması tarafından belirtilen doğrular `/serviceName` seçeneği. Bu seçenek kullanılırsa, ilişkili bir yapılandırma dosyası yürütülebilir bir derleme giriş olarak geçirilmelidir.<br /><br /> Kısa biçimi: `/v`|  
|/serviceName:\<serviceConfigName>|Doğrulanacak hizmetin yapılandırma adını belirtir. Svcutil.exe hizmeti yapılandırması için tüm giriş derlemelerin tüm ilişkili yapılandırma dosyalarını arar. Yapılandırma dosyalarını herhangi bir uzantı türü içeriyorsa, bu tür içeren derlemeler ya da GAC içinde olmalıdır ya da açıkça kullanarak sağlanan `/reference` seçeneği.|  
|/ reference:\<dosya yolu >|Belirtilen derleme, tür başvuruları çözümlemek için kullanılan derlemeler kümesini ekler. Dışarı aktarma veya kullanan bir hizmet doğrulama yapılandırmada 3. taraf uzantıları (davranışları, bağlamaları ve BindingElements) kayıtlı, GAC içinde olmayan uzantısı derlemeleri bulmak için bu seçeneği kullanın.<br /><br /> Kısa biçimi: `/r`|  
|/dataContractOnly|Yalnızca sözleşme türleri veriler üzerinde çalışıyor. Hizmet sözleşmeleri işlenmez.<br /><br /> Yalnızca yerel meta veri dosyaları için bu seçeneği belirtmeniz gerekir.<br /><br /> Kısa biçimi: `/dconly`|  
|/excludeType:\<türü >|Doğrulamanın dışında bırakılması için bir türü tam veya bütünleştirilmiş kod tam adını belirtir.<br /><br /> Kısa biçimi: `/et`|  
  
### <a name="metadata-download"></a>Meta veri yükleme  
 Svcutil.exe Hizmetleri çalıştıran meta verileri indirir ve yerel dosya meta verileri kaydetmek için kullanılabilir. Meta veri indirmek için belirtmelisiniz `/t:metadata` seçeneği. Aksi durumda, istemci kodu oluşturulur. HTTP ve HTTPS URL'si şemaları için Svcutil.exe WS-Metadata değişimi ve DISCO kullanarak meta verilerini almaya çalışır. Diğer tüm URL şemalarını için Svcutil.exe yalnızca WS-Metadata değişimi kullanır.  
  
 Svcutil aynı anda meta verilerini almak için şu meta veri isteklerini verir.  
  
-   Sağlanan adresi isteğine MEX (WS-aktarımı)  
  
-   Eklenen /mex ile sağlanan adresine MEX isteği  
  
-   (ASMX gelen DiscoveryClientProtocol kullanarak) DISCO isteğine sağlanan adresi.  
  
 Varsayılan olarak tanımlanan bağlamaları Svcutil.exe kullanır <xref:System.ServiceModel.Description.MetadataExchangeBindings> sınıfı MEX olun ister. WS-Metadata değişimi için kullanılan bağlama yapılandırmak için bir istemci uç noktası IMetadataExchange sözleşme kullanan yapılandırmasında tanımlamanız gerekir. Bu Svcutil.exe yapılandırma dosyasında ya da başka bir yapılandırma dosyası kullanarak belirtilen tanımlanabilir `/svcutilConfig` seçeneği.  
  
 `svcutil.exe /t:metadata  <url>* | <epr>`  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`url`|Meta veri sağlayan bir hizmet uç noktası veya çevrimiçi barındırılan bir meta veri belgesi URL'si.|  
|`epr`|WS-adresleme EndpointReference WS-Metadata değişimi destekleyen bir hizmet uç noktası için içeren bir XML dosyası yolu.|  
  
### <a name="xmlserializer-type-generation"></a>XmlSerializer türü oluşturma  
 Hizmetler ve seri hale getirilebilir kullanarak veri türlerini kullanan istemci uygulamaları <xref:System.Xml.Serialization.XmlSerializer> oluşturmak ve bu yavaş başlatma performansının düşmesine neden olabilir çalışma zamanında veri türleri için seri hale getirme kodu derleyin.  
  
> [!NOTE]
>  Önceden oluşturulmuş serileştirme kod yalnızca istemci uygulamaları ve Hizmetleri kullanılabilir.  
  
 Svcutil.exe, böylelikle bu uygulamalar için başlangıç performansı iyileştirme derlenmiş derlemelerden uygulama için gerekli C# seri hale getirme kodu oluşturabilir. Daha fazla bilgi için bkz: [nasıl yapılır: Başlangıç saati, WCF istemci XmlSerializer kullanarak uygulamaları geliştirmek](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
> [!NOTE]
>  Svcutil.exe yalnızca giriş derlemelerde bulunan hizmet sözleşmeleri tarafından kullanılan türleri için kod oluşturur.  
  
 `svcutil.exe /t:xmlSerializer  <assemblyPath>*`  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`assemblyPath`|Hizmet sözleşmesi türlerini içeren bir derleme yolu belirtir. Seri hale getirme türlerinde, her sözleşme içindeki tüm Xml seri hale getirilebilir türler için oluşturulur.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|/ reference:\<dosya yolu >|Belirtilen derleme, tür başvuruları çözümlemek için kullanılan derlemeler kümesini ekler.<br /><br /> Kısa biçimi: `/r`|  
|/excludeType:\<türü >|Dışarı aktarma veya doğrulama çıkarılacak bir türün tam veya bütünleştirilmiş kod tam adını belirtir.<br /><br /> Kısa biçimi: `/et`|  
|/ out:\<dosyası >|Oluşturulan kod için dosya adını belirtir. Bu seçenek, aracı giriş olarak birden çok derleme geçirildiğinde yoksayılır.<br /><br /> Varsayılan: Derleme adından türetilmiş.<br /><br /> Kısa biçimi: `/o`|  
|/UseSerializerForFaults|Belirleyen <!--zz <xref:System.Xml.XmlSerializer> --> `xref:System.Xml.XmlSerializer ` okuma ve yazma hataları, varsayılan yerine için kullanılması gereken <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, çalışan bir hizmeti veya çevrimiçi meta veri belgelerini istemci kodu oluşturur.  
  
 `svcutil http://service/metadataEndpoint`  
  
 Aşağıdaki komutu, yerel meta verileri belgelerden istemci kodu oluşturur.  
  
 `svcutil *.wsdl *.xsd /language:C#`  
  
 Aşağıdaki komutu, yerel şema belgelerden Visual Basic'te Veri sözleşme türleri oluşturur.  
  
 `svcutil /dconly *.xsd /language:VB`  
  
 Aşağıdaki komut, meta veri belgelerini Hizmetleri çalıştıran indirir.  
  
 `svcutil /t:metadata http://service/metadataEndpoint`  
  
 Aşağıdaki komutu, bir derlemede Hizmet sözleşmeleri ve ilişkili türleri için meta veri belgelerini oluşturur.  
  
 `svcutil myAssembly.dll`  
  
 Aşağıdaki komut, bir hizmet için meta veri belgelerini oluşturur ve ilişkili tüm hizmet sözleşmeleri ve derlemedeki veri türleri.  
  
 `svcutil myServiceHost.exe /serviceName:myServiceName`  
  
 Aşağıdaki komut, bir derlemede veri türleri için meta veri belgelerini oluşturur.  
  
 `svcutil myServiceHost.exe /dconly`  
  
 Aşağıdaki komut, barındırma hizmeti doğrular.  
  
 `svcutil /validate /serviceName:myServiceName myServiceHost.exe`  
  
 Aşağıdaki komut, seri hale getirme türlerinde oluşturur <xref:System.Xml.Serialization.XmlSerializer> türleri derlemedeki tüm hizmet sözleşmeleri tarafından kullanılır.  
  
 `svcutil /t:xmlserializer myContractLibrary.exe`  
  
## <a name="maximum-nametable-character-count-quota"></a>Maksimum ad tablosu karakter sayısı kotası  
 Bir hizmet için meta verileri oluşturmak için svcutil kullanırken, aşağıdaki ileti alabilirsiniz:  
  
 Hata: 8000/somesservice/mex XML verileri okunurken maksimum ad tablosu karakter sayısı kotası (16384) aşıldı gelen meta veri alınamıyor. Ad tablosu XML işleme sırasında karşılaşılan dizeleri depolamak için kullanılan bir veri yapısıdır - yinelenmeyen öğe adları, öznitelik adları ve öznitelik değerlerine sahip uzun XML belgeleri bu kotayı tetikleyebilir. Bu kota XML okuyucusu oluşturulurken kullanılan XmlDictionaryReaderQuotas nesnesindeki MaxNameTableCharCount özelliği değiştirerek artırılabilir.  
  
 Büyük bir WSDL dosya meta verilerini istediğinde döndüren bir hizmeti tarafından bu hataya neden. Svcutil.exe aracı karakter kota aşılırsa sorunudur. (Dos) hizmet reddi saldırılarını önlemeye yardımcı olmak için bu değeri ayarlayın. Bu Kotayı artırmak için svcutil için aşağıdaki yapılandırma dosyası.  
  
 Aşağıdaki yapılandırma dosyası svcutil okuyucu kotaları ayarlama gösterir  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <customBinding>  
                <binding name="MyBinding">  
                    <textMessageEncoding>  
                        <readerQuotas maxDepth="2147483647" maxStringContentLength="2147483647"  
                            maxArrayLength="2147483647" maxBytesPerRead="2147483647" maxNameTableCharCount="2147483647" />  
                    </textMessageEncoding>  
                    <httpTransport maxReceivedMessageSize="2147483647" maxBufferSize="2147483647" />  
                </binding>  
            </customBinding>  
        </bindings>  
        <client>  
            <endpoint binding="customBinding" bindingConfiguration="MyBinding"  
                contract="IMetadataExchange"  
                name="http" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
 Svcutil.exe.config adlı yeni bir dosya oluşturun ve XML örnek kodu buraya kopyalayın. Ardından dosyayı svcutil.exe aynı dizine koyun. Svcutil.exe bir sonraki çalıştırmanızda yeni ayarları seçer.  
  
## <a name="security-concerns"></a>Güvenlik sorunları  
 Svcutil.exe's yükleme klasörü, Svcutil.config ve işaret dosyaları korumak için uygun erişim denetimi listesi (ACL) kullanması gereken `/svcutilConfig`. Bu, kayıtlı ve Çalıştır gelen amaçlı olabilecek uzantılar engelleyebilir.  
  
 Ayrıca, güvenliği tehlikeye olasılığını en aza indirmek için sistem parçası olarak güvenilmeyen uzantıları ekleyin, veya gerekir güvenilmeyen kod sağlayıcıları ile Svcutil.exe kullanma.  
  
 Son olarak, reddi hizmet geçerli işlem için neden olabileceğinden aracı orta katman içinde uygulamanızın kullanmamalısınız.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Nasıl yapılır: İstemci Oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
