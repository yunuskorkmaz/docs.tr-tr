---
title: ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)
description: Meta veri belgelerinden veya hizmet modeli kodundan gelen meta veri belgelerinden WFC hizmet modeli kodu oluşturan ServiceModel meta veri yardımcı programı hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], building
- endpoints [WCF]
- Svcutil.exe
- clients [WCF], consuming services
ms.assetid: 1abf3d9f-b420-46f1-b628-df238751f308
ms.openlocfilehash: 9f8e8e0239f8f8cd149bc6e8b1d7921124731087
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245954"
---
# <a name="servicemodel-metadata-utility-tool-svcutilexe"></a>ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)

ServiceModel meta veri yardımcı programı Aracı, meta veri belgelerinden hizmet modeli kodu ve hizmet modeli kodundan gelen meta veri belgeleri oluşturmak için kullanılır.

## <a name="svcutilexe"></a>SvcUtil.exe

ServiceModel meta veri yardımcı programı Aracı, özellikle *%ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin*Windows SDK yükleme konumunda bulunabilir.

### <a name="functionalities"></a>İşlevler

Aşağıdaki tabloda, bu araç tarafından sunulan çeşitli işlevler ve nasıl kullanıldığını ele alan ilgili konu özetlenmektedir:

|Görev|Konu başlığı|
|----------|-----------|
|Çalışan hizmetlerden veya statik meta veri belgelerinden kod oluşturur.|[Hizmet Meta Verilerinden WCF İstemcisi Oluşturma](./feature-details/generating-a-wcf-client-from-service-metadata.md)|
|Derlenen koddan meta veri belgelerini dışarı aktarır.|[Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma](./feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)|
|Derlenmiş hizmet kodunu doğrular.|[Nasıl yapılır: Derlenmiş Hizmet Kodunu Doğrulamak için Svcutil.exe Kullanma](./feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)|
|Çalışan hizmetlerden meta veri belgelerini indirir.|[Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma](./feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)|
|Serileştirme kodu oluşturur.|[Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)|

> [!CAUTION]
> Svcutil, parametre olarak sağlanan adların özdeş olması halinde bir diskteki mevcut dosyaların üzerine yazar. Bu, kod dosyalarını, yapılandırmayı veya meta veri dosyalarını içerebilir. Kodu ve yapılandırma dosyalarını oluştururken bunu önlemek için `/mergeConfig` anahtarını kullanın.
>
> Ayrıca, `/r` `/ct` başvuru türleri için ve anahtarları veri sözleşmeleri oluşturmak içindir. Bu anahtarlar XmlSerializer kullanılırken çalışmaz.

### <a name="timeout"></a>Zaman aşımı

Araç meta verileri alırken beş dakikalık bir zaman aşımı süresine sahiptir. Bu zaman aşımı yalnızca ağ üzerinden meta verileri almak için geçerlidir. Bu meta verilerin herhangi bir işlemesi için uygulanmaz.

### <a name="multi-targeting"></a>Çoklu hedefleme

Araç Çoklu hedefleme 'yi desteklemez. *svcutil.exe*bir .NET 4 yapıtı oluşturmak istiyorsanız, .NET 4 SDK 'daki *svcutil.exe* kullanın. .NET 3,5 yapıtı oluşturmak için, .NET 3,5 SDK ' dan yürütülebilir dosyayı kullanın.

### <a name="accessing-wsdl-documents"></a>WSDL belgelerine erişme

Bir güvenlik belirteci hizmeti (STS) başvurusu olan bir WSDL belgesine erişmek için Svcutil kullandığınızda, Svcutil STS 'ye bir WS-MetadataExchange çağrısı yapar. Ancak hizmet, WSDL belgelerini WS-MetadataExchange veya HTTP GET kullanarak kullanıma sunabilir. Bu nedenle, STS yalnızca HTTP GET kullanarak WSDL belgesi açıkmışsa, WinFX 'de yazılmış bir istemci başarısız olur. .NET Framework 3,5 ' de yazılan istemciler için Svcutil, STS WSDL 'yi almak için hem WS-MetadataExchange hem de HTTP GET kullanmaya çalışır.

## <a name="using-svcutilexe"></a>SvcUtil.exe kullanma

### <a name="common-usages"></a>Ortak kullanımlar

Aşağıdaki tabloda bu araç için bazı yaygın olarak kullanılan seçenekler gösterilmektedir:

|Seçenek|Description|
|------------|-----------------|
|dosyalar/Dizin\<directory>|Dosya oluşturulacak dizin.<br /><br /> Varsayılan: geçerli dizin.<br /><br /> Kısa biçim:`/d`|
|/help|Araç için komut sözdizimini ve seçenekleri görüntüler.<br /><br /> Kısa biçim:`/?`|
|/noLogo|Telif hakkı ve başlık iletisini gizleyin.|
|/svcutilConfig:\<configFile>|App.config dosyası yerine kullanılacak özel bir yapılandırma dosyasını belirtir. Bu, aracın yapılandırma dosyasını değiştirmeden System. serviceModel uzantılarını kaydetmek için kullanılabilir.|
|/Target\<output type>|Araç tarafından üretilecek çıktıyı belirtir.<br /><br /> Geçerli değerler Code, metadata veya xmlSerializer ' dir.<br /><br /> Kısa biçim:`/t`|

### <a name="code-generation"></a>Kod Üretimi

Svcutil.exe, meta veri belgelerinden hizmet sözleşmeleri, istemciler ve veri türleri için kod oluşturabilir. Bu meta veri belgeleri, dayanıklı bir depolama üzerinde olabilir veya çevrimiçi olarak alınabilir. Çevrimiçi alma WS-Metadata Exchange Protokolü veya DISCO protokolünü izler (Ayrıntılar için bkz. meta veriler Indirme bölümü).

*SvcUtil.exe* aracını kullanarak, önceden TANıMLANMıŞ bir wsdl belgesini temel alan hizmet ve veri sözleşmeleri oluşturabilirsiniz. /ServiceContract anahtarını kullanın ve WSDL belgesinin indirilebileceği veya bulunabileceği bir URL veya dosya konumu belirtin. Bu, daha sonra bir şikayet hizmeti uygulamak için kullanılabilecek WSDL belgesinde tanımlanan hizmet ve veri sözleşmelerini oluşturur. Daha fazla bilgi için bkz. [nasıl yapılır: meta verileri alma ve uyumlu bir hizmet uygulama](./feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md).

BasicHttpContextBinding uç noktası olan bir hizmet için *Svcutil.exe* , `allowCookies` özniteliği olarak ayarlanmış bir BasicHttpBinding oluşturur `true` . Tanımlama bilgileri, sunucuda bağlam için kullanılır. Hizmet tanımlama bilgilerini kullandığında istemcideki bağlamı yönetmek isterseniz, yapılandırmayı bir bağlam bağlama kullanacak şekilde el ile değiştirebilirsiniz.

> [!CAUTION]
> Svcutil.exe, hizmetten alınan WSDL veya ilke dosyasını temel alarak istemciyi oluşturur. Kullanıcı asıl adı (UPN), Kullanıcı adı, " \@ " ve tam nitelikli etki alanı adı (FQDN) ile birleştirerek oluşturulur. Ancak, Active Directory kaydolan kullanıcılar için bu biçim geçerli değildir ve araç tarafından oluşturulan UPN, Kerberos kimlik doğrulamasında "oturum açma girişimi başarısız oldu" hata iletisiyle başarısız olur. Bu sorunu çözmek için, bu araç tarafından oluşturulan istemci dosyasını el ile düzeltmelisiniz.

`svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>`

|Bağımsız Değişken|Description|
|--------------|-----------------|
|`epr`|WS-Metadata Exchange destekleyen bir hizmet uç noktası için WS-Addressing EndpointReference içeren bir XML dosyasının yolu. Daha fazla bilgi için bkz. meta veri Indirme bölümü.|
|`metadataDocumentPath`|Koda (. wsdl,. xsd,. WSPolicy veya. wsmex) aktarılacak sözleşmeyi içeren bir meta veri belgesinin (*WSDL* veya *XSD*) yolu.<br /><br /> Svcutil, meta veriler için uzak bir URL belirttiğinizde içeri aktarmaları ve içerir. Ancak, yerel dosya sisteminde meta veri dosyalarını işlemek istiyorsanız, bu bağımsız değişkende tüm dosyaları belirtmeniz gerekir. Bu şekilde, ağ bağımlılıkları olmayan bir yapı ortamında Svcutil kullanabilirsiniz. Bu bağımsız değişken için joker karakterler (*. xsd, \* . wsdl) kullanabilirsiniz.|
|`url`|Çevrimiçi barındırılan bir meta veri veya bir meta veri belgesi sağlayan bir hizmet uç noktasının URL 'SI. Bu belgelerin nasıl alındığı hakkında daha fazla bilgi için bkz. Metadata Download bölümü.|

|Seçenek|Description|
|------------|-----------------|
|/Async|Hem zaman uyumlu hem de zaman uyumsuz yöntem imzaları üretir.<br /><br /> Varsayılan: yalnızca zaman uyumlu yöntem imzaları oluşturun.<br /><br /> Kısa biçim:`/a`|
|türünde\<type>|Bir WCF istemcisi için liste koleksiyonu türünü belirtir.<br/><br /> Varsayılan: koleksiyon türü System. Array. <br /><br /> Kısa biçim:`/ct`|
|/config\<configFile>|Oluşturulan yapılandırma dosyası için dosya adını belirtir.<br /><br /> Varsayılan: output.config|
|/dataContractOnly|Yalnızca veri sözleşmesi türleri için kod üretir. Hizmet sözleşmesi türleri oluşturulmaz.<br /><br /> Bu seçenek için yalnızca yerel meta veri dosyalarını belirtmeniz gerekir.<br /><br /> Kısa biçim:`/dconly`|
|/enableDataBinding|<xref:System.ComponentModel.INotifyPropertyChanged>Veri bağlamayı etkinleştirmek için tüm veri anlaşması türlerinde arabirimini uygular.<br /><br /> Kısa biçim:`/edb`|
|/excludeType:\<type>|Başvurulan anlaşma türlerinden hariç tutulacak tam veya bütünleştirilmiş kod nitelikli bir tür adı belirtir.<br /><br /> Bu anahtarı `/r` ayrı dll 'lerden birlikte kullanırken, xsd sınıfının tam adına başvurulur.<br /><br /> Kısa biçim:`/et`|
|/ImportXmlTypes|Veri sözleşmesi serileştiricisini, veri olmayan sözleşme türlerini IXmlSerializable türleri olarak içeri aktarmak üzere yapılandırır.|
|/Internal|İç olarak işaretlenmiş sınıflar oluşturur. Varsayılan: yalnızca ortak sınıflar oluşturun.<br /><br /> Kısa biçim:`/i`|
|/Language\<language>|Kod üretimi için kullanılacak programlama dilini belirtir. Machine.config dosyasında kayıtlı bir dil adı ya da öğesinden devralan bir sınıfın tam adı sağlamalısınız <xref:System.CodeDom.Compiler.CodeDomProvider> .<br /><br /> Değerler: c#, CS, CSharp, vb, VisualBasic, c++, cpp<br /><br /> Varsayılan: CSharp<br /><br /> Kısa biçim:`/l`|
|/mergeConfig|Oluşturulan yapılandırmayı varolan dosyanın üzerine yazmak yerine var olan bir dosyada birleştirir.|
|/messageContract|Ileti anlaşması türleri oluşturur.<br /><br /> Kısa biçim:`/mc`|
|/Namespace\<string,string>|Bir WSDL veya XML şeması targetNamespace 'ten CLR ad alanına bir eşleme belirtir. \*TargetNamespace için ' ' kullanılması, bu CLR ad alanına açık bir eşleme olmadan tüm targetNamespace 'ler eşler.<br /><br /> İleti sözleşmesi adının işlem adıyla çakışmadığından emin olmak için, tür başvurusunu ile nitelemeniz `::` ya da adların benzersiz olduğundan emin olmanız gerekir.<br /><br /> Varsayılan: veri sözleşmeleri için şema belgesinin hedef ad alanından türetilir. Varsayılan ad alanı, diğer tüm oluşturulan türler için kullanılır.<br /><br /> Kısa biçim: `/n` **Note:** XmlSerializer ile kullanılacak türler oluşturulurken yalnızca tek bir ad alanı eşlemesi desteklenir. Tüm oluşturulan türler varsayılan ad alanında veya ' * ' tarafından belirtilen ad alanında olacak.|
|/noConfig|Yapılandırma dosyaları oluşturmamayın.|
|/noStdLib|Standart kitaplıklara başvurulmayın.<br /><br /> Varsayılan: Mscorlib.dll ve System.servicemodel.dll başvurulur.|
|/Out\<file>|Oluşturulan kodun dosya adını belirtir.<br /><br /> Varsayılan: bir şemalardan birinin WSDL tanım adı, WSDL hizmeti adı veya hedef ad alanından türetilir.<br /><br /> Kısa biçim:`/o`|
|/Reference\<file path>|Belirtilen derlemedeki türlere başvurur. İstemcileri oluştururken, içeri aktarılmakta olan meta verileri temsil eden türleri içerebilen derlemeleri belirtmek için bu seçeneği kullanın.<br /><br /> Bu anahtarı kullanarak ileti sözleşmeleri ve <xref:System.Xml.Serialization.XmlSerializer> türleri belirtemezsiniz.<br /><br /> <xref:System.DateTimeOffset>Bu tür başvuruluyorsa, yeni bir tür oluşturmak yerine kullanılır. Uygulama .NET Framework 3,5 kullanılarak yazılmışsa, <xref:System.DateTimeOffset> otomatik olarak SvcUtil.exe başvuruları.<br /><br /> Kısa biçim:`/r`|
|/Serializable|Seri hale getirilebilir özniteliğiyle işaretlenmiş sınıfları oluşturur.<br /><br /> Kısa biçim:`/s`|
|/serviceContract|Yalnızca hizmet sözleşmeleri için kod oluşturun. İstemci sınıfı ve yapılandırması oluşturulmayacak<br /><br /> Kısa biçim:`/sc`|
|/serileştirici: otomatik|Seri hale getirici 'yi otomatik olarak seçin. Bu, veri sözleşmesi serileştiricisini kullanmaya çalışır ve başarısız olursa XmlSerializer 'ı kullanır.<br /><br /> Kısa biçim:`/ser`|
|/Serializer: DataContractSerializer|Serileştirme ve seri durumdan çıkarma için veri anlaşması Serileştiricisini kullanan veri türleri oluşturur.<br /><br /> Kısa biçim:`/ser:DataContractSerializer`|
|/Serializer: XmlSerializer|<xref:System.Xml.Serialization.XmlSerializer>Serileştirme ve seri durumdan çıkarma için kullanan veri türleri oluşturur.<br /><br /> Kısa biçim:`/ser:XmlSerializer`|
|/targetClientVersion|Uygulamanın hangi .NET Framework sürümünü hedeflediğinden belirleyin. Geçerli değerler `Version30` ve ' dir `Version35` . Varsayılan değer: `Version30`.<br /><br /> Kısa biçim:`/tcv`<br /><br /> `Version30`: `/tcv:Version30` WinFX kullanan istemciler için kod oluşturuyorsanız kullanın.<br /><br /> `Version35`: `/tcv:Version35` .NET Framework 3,5 kullanan istemciler için kod oluşturuyorsanız kullanın. Anahtarla kullanırken `/tcv:Version35` `/async` , olay tabanlı ve geri arama/temsilci tabanlı zaman uyumsuz yöntemler oluşturulur. Ayrıca, LINQ özellikli veri kümeleri için destek ve <xref:System.DateTimeOffset> etkinleştirilir.|
|/sarmalanmış|Sarmalanmış parametrelere sahip belge-sabit biçimlendirilmiş belgeler için özel kullanım büyük küçük harf kullanılıp kullanılmayacağını denetler. Normal büyük harfleri belirtmek için [hizmet modeli meta verileri yardımcı programı Aracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) aracıyla **/Sarmalanan** anahtarı kullanın.|

> [!NOTE]
> Hizmet bağlama sistem tarafından belirtilen bağlamalardan biri olduğunda (bkz. [sistem tarafından sağlanmış bağlamalar](system-provided-bindings.md)) ve <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliği ya da olarak ayarlanırsa `None` `Sign` , Svcutil [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) beklenen sistem tarafından sağlanmış öğe yerine öğesini kullanarak bir yapılandırma dosyası oluşturur. Örneğin, hizmet `<wsHttpBinding>` `ProtectionLevel` olarak ayarla öğesini kullanıyorsa `Sign` , oluşturulan yapılandırma `<customBinding>` yerine Bindings bölümünde bulunur `<wsHttpBinding>` . Koruma düzeyi hakkında daha fazla bilgi için bkz. [koruma düzeyini anlama](understanding-protection-level.md).

### <a name="metadata-export"></a>Meta veri dışarı aktarma

Svcutil.exe, derlenmiş derlemelerdeki hizmetler, sözleşmeler ve veri türleri için meta verileri dışarı aktarabilir. Bir hizmetin meta verilerini dışarı aktarmak için, `/serviceName` dışarı aktarmak istediğiniz hizmeti belirtmek üzere seçeneğini kullanmanız gerekir. Bir derleme içindeki tüm veri anlaşması türlerini dışarı aktarmak için seçeneğini kullanmanız gerekir `/dataContractOnly` . Varsayılan olarak, meta veriler giriş derlemelerindeki tüm hizmet sözleşmeleri için verilir.

`svcutil.exe [/t:metadata] [/serviceName:<serviceConfigName>] [/dataContractOnly] <assemblyPath>*`

|Bağımsız Değişken|Description|
|--------------|-----------------|
|`assemblyPath`|Aktarılacak Hizmetleri, sözleşmeleri veya veri anlaşması türlerini içeren bir derlemenin yolunu belirtir. Standart komut satırı joker karakterleri, giriş olarak birden çok dosya sağlamak için kullanılabilir.|

|Seçenek|Description|
|------------|-----------------|
|/serviceName:\<serviceConfigName>|Aktarılacak bir hizmetin yapılandırma adını belirtir. Bu seçenek kullanılırsa, ilişkili yapılandırma dosyası olan bir çalıştırılabilir derlemenin giriş olarak geçirilmesi gerekir. Svcutil.exe, hizmet yapılandırması için ilişkili tüm yapılandırma dosyalarını arar. Yapılandırma dosyaları herhangi bir uzantı türü içeriyorsa, bu türleri içeren derlemelerin GAC 'de olması veya seçeneği kullanılarak açıkça sağlanması gerekir `/reference` .|
|/Reference\<file path>|Belirtilen derlemeyi tür başvurularını çözümlemek için kullanılan derleme kümesine ekler. Yapılandırmada kayıtlı olan 3. taraf uzantıları (davranışlar, bağlamalar ve BindingElements) kullanan bir hizmeti dışarı aktarıyor veya doğrulduysanız, GAC 'de olmayan uzantı derlemelerini bulmak için bu seçeneği kullanın.<br /><br /> Kısa biçim:`/r`|
|/dataContractOnly|Yalnızca veri sözleşmesi türleri üzerinde çalışır. Hizmet sözleşmeleri işlenmedi.<br /><br /> Bu seçenek için yalnızca yerel meta veri dosyalarını belirtmeniz gerekir.<br /><br /> Kısa biçim:`/dconly`|
|/excludeType:\<type>|Dışarı aktarmanın dışında tutulacak bir türün tam veya derleme nitelikli adını belirtir. Bu seçenek, bir hizmet için meta verileri dışarı aktarırken veya türlerin dışarı aktarılmasını hariç tutmak için bir hizmet sözleşmeleri kümesi ile kullanılabilir. Bu seçenek, seçeneğiyle birlikte kullanılamaz `/dconly` .<br /><br /> Birden çok hizmet içeren tek bir derlemeniz varsa ve her biri aynı XSD adına sahip ayrı sınıflar kullanıyorsa, bu anahtar için XSD sınıf adı yerine hizmet adını belirtmeniz gerekir.<br /><br /> XSD veya veri anlaşması türleri desteklenmez.<br /><br /> Kısa biçim:`/et`|

### <a name="service-validation"></a>Hizmet doğrulama

Doğrulama hizmeti, hizmet uygulamalarında hizmeti barındırmadan hataları algılamak için kullanılabilir. `/serviceName`Doğrulamak istediğiniz hizmeti belirtmek için seçeneğini kullanmanız gerekir.

`svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*`

|Bağımsız Değişken|Description|
|--------------|-----------------|
|`assemblyPath`|Doğrulanacak hizmet türlerini içeren bir derlemenin yolunu belirtir. Derleme, hizmet yapılandırması sağlamak için ilişkili bir yapılandırma dosyasına sahip olmalıdır. Standart komut satırı joker karakterleri, birden çok derleme sağlamak için kullanılabilir.|

|Seçenek|Description|
|------------|-----------------|
|/Validate|Seçeneği tarafından belirtilen bir hizmet uygulamasını doğrular `/serviceName` . Bu seçenek kullanılırsa, ilişkili yapılandırma dosyası olan bir çalıştırılabilir derlemenin giriş olarak geçirilmesi gerekir.<br /><br /> Kısa biçim:`/v`|
|/serviceName:\<serviceConfigName>|Doğrulanacak bir hizmetin yapılandırma adını belirtir. Svcutil.exe, hizmet yapılandırması için tüm giriş derlemelerinin ilişkili tüm yapılandırma dosyalarını arar. Yapılandırma dosyaları herhangi bir uzantı türü içeriyorsa, bu türleri içeren derlemelerin GAC 'de olması veya seçeneği kullanılarak açıkça sağlanması gerekir `/reference` .|
|/Reference\<file path>|Belirtilen derlemeyi tür başvurularını çözümlemek için kullanılan derleme kümesine ekler. Yapılandırmada kayıtlı olan 3. taraf uzantıları (davranışlar, bağlamalar ve BindingElements) kullanan bir hizmeti dışarı aktarıyor veya doğrulduysanız, GAC 'de olmayan uzantı derlemelerini bulmak için bu seçeneği kullanın.<br /><br /> Kısa biçim:`/r`|
|/dataContractOnly|Yalnızca veri sözleşmesi türleri üzerinde çalışır. Hizmet sözleşmeleri işlenmedi.<br /><br /> Bu seçenek için yalnızca yerel meta veri dosyalarını belirtmeniz gerekir.<br /><br /> Kısa biçim:`/dconly`|
|/excludeType:\<type>|Doğrulamadan dışlanacak bir türün tam veya derleme nitelikli adını belirtir.<br /><br /> Kısa biçim:`/et`|

### <a name="metadata-download"></a>Meta veri Indirme

Svcutil.exe, çalışan hizmetlerden meta verileri indirmek için kullanılabilir ve meta verileri yerel dosyalara kaydedebilir. Meta verileri indirmek için seçeneğini belirtmeniz gerekir `/t:metadata` . Aksi halde, istemci kodu oluşturulur. HTTP ve HTTPS URL şemaları için, Svcutil.exe WS-Metadata Exchange ve DISCO kullanarak meta verileri almaya çalışır. Diğer tüm URL şemaları için Svcutil.exe yalnızca WS-Metadata Exchange kullanır.

Svcutil, meta verileri almak için eşzamanlı olarak aşağıdaki meta veri isteklerini yayınlar.

- Sağlanan adrese MEX (WS-transfer) isteği

- /MEX eklenmiş adresine sağlanan adrese MEX isteği

- DISCO isteği (ASMX öğesinden DiscoveryClientProtocol kullanılarak) sağlanan adrese.

Varsayılan olarak, Svcutil.exe <xref:System.ServiceModel.Description.MetadataExchangeBindings> MEX isteklerini yapmak için sınıfında tanımlanan bağlamaları kullanır. WS-Metadata Exchange için kullanılan bağlamayı yapılandırmak için, yapılandırmada IMetadataExchange sözleşmesini kullanan bir istemci uç noktası tanımlamanız gerekir. Bu, Svcutil.exe yapılandırma dosyasında ya da seçeneği kullanılarak belirtilen başka bir yapılandırma dosyasında tanımlanabilir `/svcutilConfig` .

`svcutil.exe /t:metadata  <url>* | <epr>`

|Bağımsız Değişken|Description|
|--------------|-----------------|
|`url`|Çevrimiçi barındırılan bir meta veri veya bir meta veri belgesi sağlayan bir hizmet uç noktasının URL 'SI.|
|`epr`|WS-Metadata Exchange destekleyen bir hizmet uç noktası için WS-Addressing EndpointReference içeren bir XML dosyasının yolu.|

### <a name="xmlserializer-type-generation"></a>XmlSerializer türü oluşturma

<xref:System.Xml.Serialization.XmlSerializer>Çalışma zamanında bu veri türleri için Oluştur ve derle serileştirme kodu kullanılarak seri hale getirilebilir veri türlerini kullanan hizmet ve istemci uygulamaları, yavaş başlangıç performansına yol açabilir.

> [!NOTE]
> Önceden oluşturulmuş serileştirme kodu, hizmetlerde değil yalnızca istemci uygulamalarında kullanılabilir.

Svcutil.exe, uygulamanın derlenmiş derlemelerinden gerekli C# serileştirme kodunu oluşturabilir ve bu sayede bu uygulamalar için başlangıç performansını geliştirir. Daha fazla bilgi için bkz. [nasıl yapılır: XmlSerializer kullanarak WCF Istemci uygulamalarının başlangıç zamanını geliştirme](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).

> [!NOTE]
> Svcutil.exe yalnızca giriş derlemelerinde bulunan hizmet sözleşmeleri tarafından kullanılan türler için kod üretir.

`svcutil.exe /t:xmlSerializer  <assemblyPath>*`

|Bağımsız Değişken|Description|
|--------------|-----------------|
|`assemblyPath`|Hizmet sözleşmesi türlerini içeren bir derlemenin yolunu belirtir. Serileştirme türleri her sözleşmede tüm XML serileştirilebilir türler için oluşturulur.|

|Seçenek|Description|
|------------|-----------------|
|/Reference\<file path>|Belirtilen derlemeyi tür başvurularını çözümlemek için kullanılan derleme kümesine ekler.<br /><br /> Kısa biçim:`/r`|
|/excludeType:\<type>|Dışarı aktarma veya doğrulama dışında tutulacak bir türün tam nitelenmiş veya derleme nitelikli adını belirtir.<br /><br /> Kısa biçim:`/et`|
|/Out\<file>|Oluşturulan kodun dosya adını belirtir. Bu seçenek, araca giriş olarak birden çok derleme geçirildiğinde yok sayılır.<br /><br /> Varsayılan: derleme adından türetilir.<br /><br /> Kısa biçim:`/o`|
|/UseSerializerForFaults|<xref:System.Xml.Serialization.XmlSerializer>Varsayılan yerine, hataları okumak ve yazmak için kullanılması gerektiğini belirtir <xref:System.Runtime.Serialization.DataContractSerializer> .|

## <a name="examples"></a>Örnekler

Aşağıdaki komut, çalışan bir hizmetten veya çevrimiçi meta veri belgelerinden istemci kodu oluşturur.

`svcutil http://service/metadataEndpoint`

Aşağıdaki komut, yerel meta veri belgelerinden istemci kodu oluşturur.

`svcutil *.wsdl *.xsd /language:C#`

Aşağıdaki komut yerel şema belgelerinden Visual Basic veri sözleşmesi türleri oluşturur.

`svcutil /dconly *.xsd /language:VB`

Aşağıdaki komut, çalışan hizmetlerden meta veri belgelerini indirir.

`svcutil /t:metadata http://service/metadataEndpoint`

Aşağıdaki komut, bir derlemede hizmet sözleşmeleri ve ilişkili türler için meta veri belgeleri oluşturur.

`svcutil myAssembly.dll`

Aşağıdaki komut, bir hizmet için meta veri belgelerini ve bir derlemedeki tüm ilişkili hizmet sözleşmelerini ve veri türlerini üretir.

`svcutil myServiceHost.exe /serviceName:myServiceName`

Aşağıdaki komut, bir derlemedeki veri türleri için meta veri belgeleri oluşturur.

`svcutil myServiceHost.exe /dconly`

Aşağıdaki komut, hizmet barındırmayı doğrular.

`svcutil /validate /serviceName:myServiceName myServiceHost.exe`

Aşağıdaki komut, <xref:System.Xml.Serialization.XmlSerializer> derlemedeki herhangi bir hizmet sözleşmesi tarafından kullanılan türler için serileştirme türleri oluşturur.

`svcutil /t:xmlserializer myContractLibrary.exe`

## <a name="maximum-nametable-character-count-quota"></a>Maksimum NameTable karakter sayısı kotası

Bir hizmet için meta verileri oluşturmak üzere svcutil kullanırken aşağıdaki iletiyi alabilirsiniz:

Hata: `http://localhost:8000/somesservice/mex` XML verileri okunurken en yüksek NameTable karakter sayısı kotasının (16384) meta verileri alınamıyor. NameTable, XML işleme sırasında karşılaşılan dizeleri depolamak için kullanılan bir veri yapısıdır. yinelenmeyen öğe adları olan uzun XML belgeleri, öznitelik adları ve öznitelik değerleri bu kotayı tetikleyebilir. Bu kota, XML okuyucusu oluşturulurken kullanılan XmlDictionaryReaderQuotas nesnesindeki MaxNameTableCharCount özelliği değiştirilerek artırılabilir.

Bu hata, meta verilerini istediğinizde büyük bir WSDL dosyası döndüren bir hizmetin oluşmasına neden olabilir. Sorun, svcutil.exe aracı için karakter kotasının aşılmadır. Bu değer, hizmet reddi (DOS) saldırılarını önlemeye yardımcı olmak için ayarlanır. Svcutil için aşağıdaki yapılandırma dosyasını belirterek bu kotayı artırabilirsiniz.

Aşağıdaki yapılandırma dosyasında Svcutil için okuyucu kotaları ayarlama gösterilmektedir

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

svcutil.exe.config adlı yeni bir dosya oluşturun ve XML örnek kodunu buna kopyalayın. Sonra dosyayı svcutil.exe aynı dizine yerleştirin. svcutil.exe bir sonraki çalıştırılışında yeni ayarları seçer.

## <a name="security-concerns"></a>Güvenlik sorunları

Svcutil.exe yükleme klasörünü, Svcutil.config ve tarafından işaret edilen dosyaları korumak için uygun Access Control listesini (ACL) kullanmanız gerekir `/svcutilConfig` . Bu, kötü amaçlı uzantıların kaydedilmesini ve çalıştırılmasını engelleyebilir.

Ayrıca, güvenliğin tehlikeye düşmesi olasılığını en aza indirmek için, güvenilmeyen uzantıları sistemin parçası olarak eklememelisiniz veya Svcutil.exe ile güvenilmeyen kod sağlayıcıları kullanmamalısınız.

Son olarak, aracı uygulamanızın orta katmanında kullanmamalısınız, çünkü hizmet reddi geçerli işleme yol açabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Nasıl yapılır: İstemci Oluşturma](how-to-create-a-wcf-client.md)
