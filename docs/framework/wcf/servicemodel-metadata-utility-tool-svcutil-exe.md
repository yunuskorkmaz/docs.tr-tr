---
title: ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], building
- endpoints [WCF]
- Svcutil.exe
- clients [WCF], consuming services
ms.assetid: 1abf3d9f-b420-46f1-b628-df238751f308
ms.openlocfilehash: 29b030708f2174b55386b13931f1088d15f4eb4f
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582702"
---
# <a name="servicemodel-metadata-utility-tool-svcutilexe"></a>ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)

ServiceModel meta veri yardımcı programracı meta veri belgelerini ve hizmet modeli kodu meta veri belgelerinden hizmet modeli kodu oluşturmak için kullanılır.

## <a name="svcutilexe"></a>SvcUtil.exe

ServiceModel meta veri yardımcı Programracı Windows SDK'sını yükleme konumunda, özellikle bulunabilir *%ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin*.

### <a name="functionalities"></a>İşlevler

Aşağıdaki tabloda, bu araç ve nasıl kullanıldığı açıklanır ilgili konu tarafından sağlanan çeşitli işlevler özetlenmektedir:

|Görev|Konu|
|----------|-----------|
|Hizmetleri veya statik meta veri belgelerinden çalışmasını kod oluşturur.|[Hizmet Meta Verilerinden WCF İstemcisi Oluşturma](../../../docs/framework/wcf/feature-details/generating-a-wcf-client-from-service-metadata.md)|
|Meta veri belgelerini derlenmiş koddan dışa aktarır.|[Nasıl yapılır: Meta verileri derlenmiş hizmet kodundan dışarı aktarmak için svcutil.exe kullanma](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)|
|Derlenmiş hizmet kodunu doğrular.|[Nasıl yapılır: Derlenmiş hizmet kodunu doğrulamak için svcutil.exe kullanma](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)|
|Meta veri belgelerini Hizmetleri çalışmasını indirir.|[Nasıl yapılır: Meta veri belgelerini indirmek için svcutil.exe kullanma](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)|
|Serileştirme kod oluşturur.|[Nasıl yapılır: Başlangıç zamanı, WCF istemci XmlSerializer kullanarak uygulamaları geliştirin](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)|

> [!CAUTION]
> Parametre olarak sağlanan adları aynıysa Svcutil bir diskte mevcut dosyaların üzerine yazar. Bu, kod dosyaları, yapılandırma ve meta veri dosyaları içerebilir. Bu kod ve yapılandırma dosyalarını oluştururken önlemek için `/mergeConfig` geçin.
>
> Ayrıca, `/r` ve `/ct` başvuru türleri için anahtarlar şunlardır veri sözleşmeleri oluşturmak için. XmlSerializer'ı kullanırken, bu anahtarlar çalışmaz.

### <a name="timeout"></a>zaman aşımı

Araç, meta verileri alınırken bir beş dakikalık zaman aşımı vardır. Bu zaman aşımı, yalnızca ağ üzerinden meta veri alma için geçerlidir. Bu meta verilere herhangi bir işlem için geçerli değildir.

### <a name="multi-targeting"></a>Çoklu sürüm desteği

Aracı, multi-targeting'e desteklemez. .NET 4 yapıdan oluşturmak istiyorsanız *svcutil.exe*, kullanın *svcutil.exe* .NET 4 SDK. .NET 3.5 yapıt üretmek için yürütülebilir dosyadan .NET 3.5 SDK'yı kullanın.

### <a name="accessing-wsdl-documents"></a>WSDL belgeleri erişme

Svcutil bir başvuru yapan bir güvenlik belirteci hizmeti (STS) bir WSDL belgesi erişmek için kullandığınız zaman Svcutil bir WS-MetadataExchange STS'ye çağrı yapar. Ancak, hizmet, WS-MetadataExchange ya da HTTP GET kullanarak WSDL belgelerini kullanıma sunabilirsiniz. Bu nedenle, STS yalnızca kullanıma, HTTP GET, yazılan bir istemci kullanarak WSDL belgesi [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] başarısız olur. Yazılan istemciler için [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], hem WS-MetadataExchange kullanma girişiminde Svcutil ve HTTP GET STS WSDL elde edilir.

## <a name="using-svcutilexe"></a>SvcUtil.exe kullanma

### <a name="common-usages"></a>Ortak kullanımlar

Aşağıdaki tabloda, bazı yaygın olarak bu araç için kullanılan seçenekler gösterilmektedir:

|Seçenek|Açıklama|
|------------|-----------------|
|/ directory:\<dizin >|Dosyaların oluşturulacağı dizin.<br /><br /> Varsayılan: Geçerli dizin.<br /><br /> Kısa biçim: `/d`|
|/help|Araç için komut sözdizimini ve seçenekleri görüntüler.<br /><br /> Kısa biçim: `/?`|
|/ nologo|Telif hakkı ve başlık iletisini gösterme.|
|/svcutilConfig:\<configFile>|App.config dosyasında yerine kullanılacak özel yapılandırma dosyasını belirtir. Bu aracın yapılandırma dosyası değiştirmeden system.serviceModel uzantıları kaydetmek için kullanılabilir.|
|/ target:\<çıkış türü >|Araç tarafından oluşturulacak çıkış belirtir.<br /><br /> Kod, meta verileri veya xmlSerializer değerler geçerlidir.<br /><br /> Kısa biçim: `/t`|

### <a name="code-generation"></a>Kod Üretimi

Svcutil.exe meta veri belgelerinden Hizmet sözleşmeleri, istemciler ve veri türleri için kod oluşturur. Bu meta veri belgelerini, dayanıklı bir depolama alanında olabilir veya çevrimiçi olarak alınabilir. (Ayrıntıları meta verilerini yükleme bölümüne bakın için) WS-Metadata Exchange veya DISCO Protokolü ya da çevrimiçi alma izler.

Kullanabileceğiniz *SvcUtil.exe* aracını üzerinde önceden tanımlanmış bir WSDL belgesi tabanlı hizmet ve veri sözleşmeleri oluşturmak için. /ServiceContract anahtarını kullanın ve burada WSDL belgesinde bulunamadı veya İndirilebilecek URL veya dosya konumu belirtin. Bu, ardından uyumlu hizmet uygulamak için kullanılan WSDL belgesinde tanımlanan hizmet ve veri sözleşmeleri oluşturur. Daha fazla bilgi için [nasıl yapılır: Meta veri alma ve uyumlu bir hizmet ekleme](../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md).

Bir hizmetin BasicHttpContextBinding uç noktası ile *Svcutil.exe* ile bir BasicHttpBinding oluşturur `allowCookies` özniteliğini `true` yerine. Tanımlama bilgileri, sunucu üzerindeki bağlamı için kullanılır. Hizmet tanımlama bilgilerini kullandığında istemcide bağlam yönetmek istiyorsanız, bağlam bağlama kullanmak için yapılandırmayı el ile değiştirebilirsiniz.

> [!CAUTION]
> Svcutil.exe hizmetinden alınan WSDL veya ilke dosyası bağlı olarak istemciye oluşturur. Kullanıcı asıl adı (UPN) kullanıcı adı, birleştirilerek oluşturulan "\@" ve tam etki alanı adı (FQDN). Ancak, Active Directory'de kayıtlı kullanıcılar için bu biçimi geçerli değil ve aracı tarafından oluşturulan UPN "oturum açma girişimi başarısız oldu" hata iletisiyle Kerberos kimlik doğrulamasındaki bir hata neden olur. Bu sorunu gidermek için bu aracı tarafından oluşturulan istemci dosyası el ile düzeltmeniz.

`svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>`

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`epr`|Bir WS-Metadata Exchange'i destekleyen bir hizmet uç noktası için WS-Addressing EndpointReference içeren bir XML dosyası yolu. Daha fazla bilgi için meta verileri indirme bölümüne bakın.|
|`metadataDocumentPath`|Meta veri belgesinin yolu (*wsdl* veya *xsd*) koda (.wsdl, .xsd, .wspolicy veya .wsmex) içeri aktarmak için sözleşme içeriyor.<br /><br /> Svcutil aşağıdaki içeri aktarmaları ve uzak meta veri URL'sini belirttiğinizde içerir. Ancak, yerel dosya sisteminde meta veri dosyalarını işlemek istiyorsanız, tüm dosyalar bu bağımsız değişkeni belirtmeniz gerekir. Bu şekilde, bir derleme ortamında Ağ bağımlılıkları burada olamaz Svcutil kullanabilirsiniz. Joker karakterler kullanabilirsiniz (*.xsd, \*.wsdl) bu bağımsız değişkeni.|
|`url`|Meta veri sağlayan bir hizmet uç noktası ya da çevrimiçi barındırılan bir meta veri belgesi URL'si. Bu belgeleri nasıl alınır daha fazla bilgi için meta veri yükleme bölümüne bakın.|

|Seçenek|Açıklama|
|------------|-----------------|
|/Async|Her iki zaman uyumlu ve zaman uyumsuz yöntem imzaları oluşturur.<br /><br /> Varsayılan: yalnızca zaman uyumlu yöntem imzaları oluşturur.<br /><br /> Kısa biçim: `/a`|
|/collectionType:\<türü >|Bir WCF istemcisi için liste koleksiyon türünü belirtir.<br/><br /> Varsayılan: Koleksiyon System.Array türüdür. <br /><br /> Kısa biçim: `/ct`|
|/ config:\<configFile >|Oluşturulan yapılandırma dosyası için dosya adını belirtir.<br /><br /> Varsayılan: output.config|
|/dataContractOnly|Yalnızca veri sözleşmesi türleri için kod oluşturur. Hizmet sözleşmesi türleri oluşturulmaz.<br /><br /> Yalnızca yerel meta veri dosyaları için bu seçeneği belirtmeniz gerekir.<br /><br /> Kısa biçim: `/dconly`|
|/enableDataBinding|Implements <xref:System.ComponentModel.INotifyPropertyChanged> veri bağlamayı etkinleştirmek için tüm veri anlaşması türleri arabirimi.<br /><br /> Kısa biçim: `/edb`|
|/excludeType:\<türü >|Başvurulan anlaşma türlerinin dışlanacak tam veya bütünleştirilmiş kodla nitelenen tür adı belirtir.<br /><br /> Bu anahtar ile birlikte kullanırken `/r` ayrı DLL'lerden XSD sınıfın tam adını başvurulur.<br /><br /> Kısa biçim: `/et`|
|/importXmlTypes|Veri sözleşmesi serileştiricisi'veri anlaşması olmayan türleri IXmlSerializable türü olarak içeri aktarmak için yapılandırır.|
|/ İç|İç olarak işaretlenmiş sınıflar oluşturur. Varsayılan: yalnızca Genel sınıflar oluşturun.<br /><br /> Kısa biçim: `/i`|
|/Language:\<dil >|Kod oluşturma için kullanılacak programlama dilini belirtir. Machine.config dosyasında kayıtlı bir dil adı veya devralınan bir sınıf tam nitelikli adı sağlamanız gerekir <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Değerler: c#, cs, csharp, vb, visualbasic, c ++, cpp<br /><br /> Varsayılan: csharp<br /><br /> Kısa biçim: `/l`|
|/mergeConfig|Varolan dosyanın üzerine yazmak yerine var olan bir dosya, oluşturulan yapılandırma birleştirir.|
|/messageContract|İleti sözleşmesi türleri oluşturur.<br /><br /> Kısa biçim: `/mc`|
|/ Namespace:\<string, string >|Bir eşleme bir WSDL veya XML Schema Targetnamespace'ten CLR ad alanını belirtir. Kullanarak '\*' targetNamespace söz konusu CLR ad alanına açık bir eşleme olmaksızın tüm Targetnamespace'ler eşlenir.<br /><br /> İleti sözleşmesi adı işlem adına sahip birbiriyle çakışır değil emin emin olmak için ya da tür başvurusu ile nitelemeniz `::`, veya adlarının benzersiz olduğundan emin olun.<br /><br /> Varsayılan: Veri anlaşmaları için şema belgesinin hedef ad alanından türetilir. Varsayılan ad alanı diğer oluşturulan tüm türleri için kullanılır.<br /><br /> Kısa biçim: `/n` **Not:**  XmlSerializer ile kullanılacak türlerini oluştururken, yalnızca tek bir ad alanı eşleme desteklenir. Oluşturulan tüm türleri ya da varsayılan ad alanı ya da tarafından belirtilen ad alanı olacaktır ' *'.|
|/ noconfig|Yapılandırma dosyaları oluşturmaz.|
|/noStdLib|Standart kitaplıkları başvuruda bulunmayın.<br /><br /> Varsayılan: Mscorlib.dll ve System.servicemodel.dll başvurulur.|
|/ out:\<dosyası >|Oluşturulan kodun dosya adını belirtir.<br /><br /> Varsayılan: WSDL tanımı adından türetilir, WSDL hizmet adı veya hedef bir şema ad alanı.<br /><br /> Kısa biçim: `/o`|
|/ reference:\<dosya yolu >|Belirtilen bütünleştirilmiş kod başvuruları türleri. Oluşturma istemciler kullandığınızda bu seçeneği alınan meta verileri temsil eden türleri içerebilecek bütünleştirilmiş kodlar belirtmek için.<br /><br /> İleti sözleşmeleri belirtilemez ve <xref:System.Xml.Serialization.XmlSerializer> bu anahtarı kullanarak türleri.<br /><br /> Varsa <xref:System.DateTimeOffset> başvurulan, bu türü yeni bir tür üretmek yerine kullanılır. Uygulamayı kullanarak yazılmışsa [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], SvcUtil.exe başvuruları <xref:System.DateTimeOffset> otomatik olarak.<br /><br /> Kısa biçim: `/r`|
|/ seri hale getirilebilir|Seri hale getirilebilir özniteliği ile işaretlenmiş sınıflar oluşturur.<br /><br /> Kısa biçim: `/s`|
|/serviceContract|Hizmet sözleşmeleri ile yalnızca kod oluşturur. İstemci sınıfı ve yapılandırma oluşturulmaz<br /><br /> Kısa biçim: `/sc`|
|/serializer:Auto|Otomatik olarak seri hale getirici'ı seçin. Bu işlem, veri sözleşme seri hale getirici kullanmayı dener ve bu başarısız olursa XmlSerializer kullanır.<br /><br /> Kısa biçim: `/ser`|
|/serializer:DataContractSerializer|Serileştirme ve seri durumundan çıkarma için veri sözleşmesi serileştiricisi kullanan veri türlerini oluşturur.<br /><br /> Kısa biçim: `/ser:DataContractSerializer`|
|/serializer:XmlSerializer|Kullanan türleri oluşturur <xref:System.Xml.Serialization.XmlSerializer> serileştirme ve seri durumundan çıkarma için.<br /><br /> Kısa biçim: `/ser:XmlSerializer`|
|/targetClientVersion|Uygulamanın hangi .NET Framework sürümünü hedefliyor belirtin. Geçerli değerler `Version30` ve `Version35`. Varsayılan değer `Version30` şeklindedir.<br /><br /> Kısa biçim: `/tcv`<br /><br /> `Version30`: Kullanma `/tcv:Version30` kullanan istemciler için kod üretiyorsanız [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)].<br /><br /> `Version35`: Kullanma `/tcv:Version35` kullanan istemciler için kod üretiyorsanız [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Kullanırken `/tcv:Version35` ile `/async` geçin, olay tabanlı ve geri çağırma/temsilci tabanlı zaman uyumsuz yöntemler oluşturulur. Ayrıca, veri kümeleri için LINQ özellikli destekler ve <xref:System.DateTimeOffset> etkinleştirilir.|
|/ Sarmalanan|Sarmalanan parametrelerle Belge stilinde belgesi-değişmez değeri için özel büyük/küçük harf kullanılıp kullanılmadığını denetler. Kullanım **/ sarmalanmış** anahtarı ile [Service Model meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) normal büyük/küçük harf belirlemek için aracı.|

> [!NOTE]
> Hizmet bağlaması olduğunda sistem tarafından sağlanan bağlamalar birini (bkz [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md)) ve <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliği ayarlandığında ya `None` veya `Sign`, Svcutil üretir yapılandırma dosyası kullanma [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) beklenen Sistem tarafından sağlanan öğesi yerine öğesi. Hizmet kullanıyorsa, örneğin, `<wsHttpBinding>` öğeyle `ProtectionLevel` kümesine `Sign`, oluşturulan yapılandırmasına sahip `<customBinding>` yerine bağlamaları bölümünde `<wsHttpBinding>`. Koruma düzeyi hakkında daha fazla bilgi için bkz: [anlama koruma düzeyi](../../../docs/framework/wcf/understanding-protection-level.md).

### <a name="metadata-export"></a>Meta veri dışarı aktarma

Svcutil.exe Hizmetleri, sözleşmeler ve derlenmiş bütünleştirilmiş kodlar içindeki veri türleri için meta verileri dışarı aktarabilirsiniz. Bir hizmet için meta verileri dışarı aktarmak için kullanmanız gerekir `/serviceName` dışarı aktarmak istediğiniz hizmet belirtmek için seçeneği. Derlemedeki tüm veri anlaşması türleri dışarı aktarmak için kullanmalısınız `/dataContractOnly` seçeneği. Varsayılan olarak, tüm hizmet sözleşmelerinde giriş derlemeleri için meta verileri dışarı aktarılır.

`svcutil.exe [/t:metadata] [/serviceName:<serviceConfigName>] [/dataContractOnly] <assemblyPath>*`

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`assemblyPath`|Dışa aktarılacak Hizmetleri, sözleşmeler ya da veri anlaşması türleri içeren bir bütünleştirilmiş kod yolu belirtir. Standart komut satırı joker karakterleri, birden çok dosya giriş olarak sağlamak için kullanılabilir.|

|Seçenek|Açıklama|
|------------|-----------------|
|/serviceName:\<serviceConfigName>|Dışa aktarılacak bir hizmet yapılandırma adını belirtir. Bu seçenek kullanılırsa, yürütülebilir bir derleme ile ilişkili bir yapılandırma dosyası, giriş olarak geçirilmelidir. Svcutil.exe hizmet yapılandırması tüm ilişkili yapılandırma dosyalarını arar. Yapılandırma dosyalarını herhangi bir uzantı türleri içeriyorsa, bu türleri içeren derlemeler GAC içinde ya da olmalıdır veya sağlanan kullanarak açıkça `/reference` seçeneği.|
|/ reference:\<dosya yolu >|Belirtilen derleme, tür başvurularını çözümlemek için kullanılan derlemeler kümesini ekler. Dışarı aktarma veya doğrulama kullanan bir hizmet yapılandırmasında 3. taraf uzantıları (davranışları, bağlamalar ve BindingElements) kayıtlı, GAC'de olmayan uzantısı derlemeleri bulmak için bu seçeneği kullanın.<br /><br /> Kısa biçim: `/r`|
|/dataContractOnly|Veri sözleşmesi türleri yalnızca çalışır. Hizmet sözleşmeleri işlenmez.<br /><br /> Yalnızca yerel meta veri dosyaları için bu seçeneği belirtmeniz gerekir.<br /><br /> Kısa biçim: `/dconly`|
|/excludeType:\<türü >|Dışarı aktarma hariç tutulacak bir türün tam veya bütünleştirilmiş kodla nitelenen adını belirtir. Dışarı aktarılan türler hariç tutmak bir dizi Hizmet sözleşmeleri veya bir hizmet için meta verileri dışa aktarırken bu seçeneği kullanılabilir. Bu seçeneği ile birlikte kullanılamaz `/dconly` seçeneği.<br /><br /> Birden çok hizmetleri içeren tek bir derleme varsa ve her ayrı sınıfları aynı XSD adıyla kullanır, bu anahtar için XSD sınıfı adı yerine hizmet adını belirtmeniz gerekir.<br /><br /> XSD veya veri anlaşması türleri desteklenmez.<br /><br /> Kısa biçim: `/et`|

### <a name="service-validation"></a>Hizmet doğrulama

Doğrulama, barındırma hizmeti olmadan hizmet uygulamalarında hataları algılamak için kullanılabilir. Kullanmalısınız `/serviceName` doğrulamak istediğiniz hizmeti göstermek için seçenek.

`svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*`

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`assemblyPath`|Doğrulanacak hizmet türlerini içeren bir bütünleştirilmiş kod yolu belirtir. Derleme hizmeti yapılandırması sağlamak için ilişkili bir yapılandırma dosyası olmalıdır. Birden çok derleme sağlamak için standart bir komut satırı joker karakterler kullanılabilir.|

|Seçenek|Açıklama|
|------------|-----------------|
|/ validate|Bir hizmet uygulaması tarafından belirtilen doğrular `/serviceName` seçeneği. Bu seçenek kullanılırsa, yürütülebilir bir derleme ile ilişkili bir yapılandırma dosyası, giriş olarak geçirilmelidir.<br /><br /> Kısa biçim: `/v`|
|/serviceName:\<serviceConfigName>|Doğrulanacak bir hizmetin yapılandırma adı belirtir. Svcutil.exe, tüm giriş derleme hizmeti yapılandırması tüm ilişkili yapılandırma dosyalarını arar. Yapılandırma dosyalarını herhangi bir uzantı türleri içeriyorsa, bu türleri içeren derlemeler GAC içinde ya da olmalıdır veya sağlanan kullanarak açıkça `/reference` seçeneği.|
|/ reference:\<dosya yolu >|Belirtilen derleme, tür başvurularını çözümlemek için kullanılan derlemeler kümesini ekler. Dışarı aktarma veya doğrulama kullanan bir hizmet yapılandırmasında 3. taraf uzantıları (davranışları, bağlamalar ve BindingElements) kayıtlı, GAC'de olmayan uzantısı derlemeleri bulmak için bu seçeneği kullanın.<br /><br /> Kısa biçim: `/r`|
|/dataContractOnly|Veri sözleşmesi türleri yalnızca çalışır. Hizmet sözleşmeleri işlenmez.<br /><br /> Yalnızca yerel meta veri dosyaları için bu seçeneği belirtmeniz gerekir.<br /><br /> Kısa biçim: `/dconly`|
|/excludeType:\<türü >|Doğrulamanın dışında tutulacak bir türün tam veya bütünleştirilmiş kodla nitelenen adını belirtir.<br /><br /> Kısa biçim: `/et`|

### <a name="metadata-download"></a>Meta verileri indirme

Svcutil.exe Hizmetleri çalışmasını meta verileri indirin ve yerel dosyalar için meta verileri kaydetmek için kullanılabilir. Meta verileri indirilemedi, belirtmelisiniz `/t:metadata` seçeneği. Aksi takdirde, istemci kodu oluşturulur. HTTP ve HTTPS URL'si düzenleri için Svcutil.exe WS-Metadata Exchange ve DISCO kullanarak meta verilerini almayı dener. Diğer tüm URL şemalarını için Svcutil.exe yalnızca WS-Metadata Exchange kullanır.

Svcutil aynı anda meta verilerini almak için aşağıdaki meta veri isteği yayınlar.

- Sağlanan adresi isteğine MEX (WS-aktarımı)

- MEX isteğine eklenen /mex ile sağlanan adresi

- Sağlanan adresine DISCO isteği (ASMX DiscoveryClientProtocol kullanarak).

Varsayılan olarak, içinde tanımlanan bağlamalardan Svcutil.exe kullanır <xref:System.ServiceModel.Description.MetadataExchangeBindings> sınıfı MEX yapmak ister. WS-Metadata değişimi için kullanılan bir bağlama yapılandırmak için istemci uç noktası IMetadataExchange sözleşmesi kullanan yapılandırmasında tanımlamanız gerekir. Bu yapılandırma dosyasını Svcutil.exe veya başka bir yapılandırma dosyası kullanarak belirtilen tanımlanabilir `/svcutilConfig` seçeneği.

`svcutil.exe /t:metadata  <url>* | <epr>`

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`url`|Meta veri sağlayan bir hizmet uç noktası ya da çevrimiçi barındırılan bir meta veri belgesi URL'si.|
|`epr`|Bir WS-Metadata Exchange'i destekleyen bir hizmet uç noktası için WS-Addressing EndpointReference içeren bir XML dosyası yolu.|

### <a name="xmlserializer-type-generation"></a>XmlSerializer tür oluşturma

Hizmetler ve seri hale getirilebilir kullanarak veri türlerini kullanan istemci uygulamalar <xref:System.Xml.Serialization.XmlSerializer> oluşturmak ve yavaş başlatma performansı düşürebilir çalışma zamanında bu veri türleri için serileştirme kodu derleyin.

> [!NOTE]
> Önceden oluşturulan serileştirme kod, yalnızca istemci uygulamaları ve Hizmetleri kullanılabilir.

Svcutil.exe gerekli C# serileştirme kodu, bu nedenle bu uygulamaları için başlatma performansını iyileştirme derlenmiş bütünleştirilmiş uygulama oluşturabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Başlangıç zamanı, istemci XmlSerializer kullanarak WCF uygulamalarının geliştirilmesine](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).

> [!NOTE]
> Svcutil.exe, yalnızca hizmet sözleşmeleri giriş derlemelerde bulunan tarafından kullanılan türleri için kod oluşturur.

`svcutil.exe /t:xmlSerializer  <assemblyPath>*`

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`assemblyPath`|Hizmet sözleşmesi türleri içeren bir bütünleştirilmiş kod yolu belirtir. Seri hale getirme türlerinde, her sözleşme tüm Xml seri hale getirilebilir türler için oluşturulur.|

|Seçenek|Açıklama|
|------------|-----------------|
|/ reference:\<dosya yolu >|Belirtilen derleme, tür başvurularını çözümlemek için kullanılan derlemeler kümesini ekler.<br /><br /> Kısa biçim: `/r`|
|/excludeType:\<türü >|Dışarı aktarma veya doğrulama hariç tutulacak bir türün tam veya bütünleştirilmiş kodla nitelenen adını belirtir.<br /><br /> Kısa biçim: `/et`|
|/ out:\<dosyası >|Oluşturulan kodun dosya adını belirtir. Birden çok derleme aracı için giriş olarak geçirildiğinde, bu seçenek göz ardı edilir.<br /><br /> Varsayılan: Derleme adından türetilir.<br /><br /> Kısa biçim: `/o`|
|/ UseSerializerForFaults|Belirten <xref:System.Xml.Serialization.XmlSerializer> hataları, varsayılan yerine yazma ve okuma için kullanılması gereken <xref:System.Runtime.Serialization.DataContractSerializer>.|

## <a name="examples"></a>Örnekler

Aşağıdaki komutu, çalışan bir hizmete veya çevrimiçi meta veri belgelerinden istemci kodu oluşturur.

`svcutil http://service/metadataEndpoint`

Aşağıdaki komut, yerel meta veri belgelerinden istemci kodu oluşturur.

`svcutil *.wsdl *.xsd /language:C#`

Aşağıdaki komutu, Visual Basic'te yerel şema belgelerden veri sözleşmesi türleri oluşturur.

`svcutil /dconly *.xsd /language:VB`

Aşağıdaki komut, meta veri belgelerini Hizmetleri çalışmasını indirir.

`svcutil /t:metadata http://service/metadataEndpoint`

Hizmet sözleşmeleri ve ilişkili türleri için meta veri belgelerini, aşağıdaki komutu bir derlemede oluşturur.

`svcutil myAssembly.dll`

Aşağıdaki komutu bir hizmet için meta veri belgelerini oluşturur ve tüm ilişkili hizmet sözleşmeleri ve bir derleme içindeki veri türleri.

`svcutil myServiceHost.exe /serviceName:myServiceName`

Aşağıdaki komut, veri türleri için meta veri belgelerini bir derlemede oluşturur.

`svcutil myServiceHost.exe /dconly`

Aşağıdaki komut, barındırma hizmeti doğrular.

`svcutil /validate /serviceName:myServiceName myServiceHost.exe`

Aşağıdaki komutu için seri hale getirme türlerinde oluşturur <xref:System.Xml.Serialization.XmlSerializer> derleme hiçbir hizmet sözleşmelerinde tarafından kullanılan türler.

`svcutil /t:xmlserializer myContractLibrary.exe`

## <a name="maximum-nametable-character-count-quota"></a>En fazla ad tablosu karakter sayısı kotası

Svcutil bir hizmet için meta verileri oluşturmak için kullanırken aşağıdaki iletiyi alabilirsiniz:

Hata: Meta verileri alınamıyor `http://localhost:8000/somesservice/mex` XML verileri okunurken, en fazla ad tablosu karakter sayısı kotası (16384) aşıldı. Ad tablosu XML işlenirken karşılaşılan dizeleri depolamak için kullanılan bir veri yapısıdır - uzun XML belgeleri yinelenmeyen öğe adları, öznitelik adları ve öznitelik değerleri bu kotayı tetikleyebilir. Bu kota XML okuyucusu oluşturulurken kullanılan XmlDictionaryReaderQuotas nesnesindeki MaxNameTableCharCount özelliği değiştirilerek artırılabilir.

Bu hata büyük bir WSDL dosyası meta verilerini istediğinde döndüren bir hizmet tarafından neden olabilir. Sorun için svcutil.exe aracını karakterle kota aşılırsa olmasıdır. Bu değer, (dos) hizmet reddi saldırılarını önlemeye yardımcı olmak için ayarlanır. Svcutil için aşağıdaki yapılandırma dosyası belirterek bu kotayı artırabilir.

Aşağıdaki yapılandırma dosyası svcutil okuyucu kotaları ayarlama işlemi gösterilmektedir

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

Svcutil.exe.config adlı yeni bir dosya oluşturun ve içine XML örnek kodu kopyalayın. Ardından dosyayı svcutil.exe aynı dizine koyun. Gelecek sefer svcutil.exe çalıştırdığınızda, yeni ayarları seçin.

## <a name="security-concerns"></a>Güvenlik konuları

Svcutil.exe ait yükleme klasörü, Svcutil.config ve tarafından işaret edilen dosyaları korumak için uygun erişim denetimi listesi (ACL) kullanmalıdır `/svcutilConfig`. Bu, kayıtlı ve çalıştırma gelen kötü amaçlı uzantılar engelleyebilir.

Ayrıca, güvenliği tehlikeye olasılığını en aza indirmek için sistemin bir parçası olmanız ya da Svcutil.exe ile güvenilmeyen kod sağlayıcıları kullanan güvenilmeyen uzantılar eklemeyin.

Son olarak, engelleme hizmet geçerli işlem için neden olabileceğinden aracı orta katman içinde uygulamanızın kullanmamalısınız.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Nasıl yapılır: Bir istemci oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
