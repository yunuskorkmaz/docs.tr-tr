---
title: Modern masaüstü uygulamalarını geçirme
description: Modern masaüstü uygulamalarına yönelik geçiş süreci hakkında bilmeniz gereken her şey.
ms.date: 05/12/2020
ms.openlocfilehash: 2108aa0b99cabfbb0f3263f094ba8277f953ed6a
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423301"
---
# <a name="migrating-modern-desktop-applications"></a>Modern masaüstü uygulamalarını geçirme

Bu bölümde, var olan bir uygulamayı .NET Framework .NET Core 'a geçirirken en yaygın sorunları ve sorunları araştırıyoruz.

Karmaşık bir masaüstü uygulaması yalıtımta çalışmaz ve yerel makinede veya uzak bir sunucuda bulunabilecek alt sistemler ile ilgili bir tür etkileşime ihtiyaç duyuyor. Büyük olasılıkla yerel olarak veya uzaktan bir kalıcılık depolaması olarak bağlanmak için bir tür veritabanına ihtiyacı olacaktır. Internet ve hizmet odaklı mimarilerin yaptığı gibi, uygulamanızın uzak bir sunucuda veya bulutta bulunan bir hizmet sıralaması ile bağlantılı olması yaygındır. Bazı işlevleri uygulamak için makine dosya sistemine erişmeniz gerekebilir. Alternatif olarak, uygulamanızın dışında bir COM nesnesi içinde bulunan bir işlev parçası kullanıyor olabilirsiniz, örneğin, kuruluşunuzda Office derlemelerini Tümleştirdiğiniz durumlarda yaygın bir senaryo olur.

Bunun yanı sıra, API yüzeyinde .NET Framework ve .NET Core tarafından sunulan farklar vardır ve .NET Framework sunulan bazı özellikler .NET Core 'da kullanılamaz. Bu nedenle, bir geçiş planlarken bunları bilmeniz ve dikkate almanız önemlidir.

## <a name="configuration-files"></a>Yapılandırma dosyaları

Yapılandırma dosyaları, çalışma zamanında okunan özellik kümelerini depolamayı ve bir veritabanının nerede bulunacağı veya bir döngünün kaç kez yürütüleceğini gösteren uygulamalarımızın davranışını etkileme olasılığını sunar. Bu tekniğin, yeniden kodlanmadan ve yeniden derlemenize gerek kalmadan uygulamanın bazı yönlerini değiştiremeyeceğiniz bir yöntemdir. Örneğin, aynı uygulama kodu bir geliştirme ortamında belirli bir yapılandırma değerleri kümesiyle ve farklı bir şekilde üretimde çalıştırıldığında bu yararlı gelir.

### <a name="configuration-on-net-framework"></a>.NET Framework yapılandırma

Çalışan bir .NET Framework masaüstü uygulamanız varsa, ad alanından sınıfından erişilen bir *app. config* dosyasına sahip olursunuz <xref:System.Configuration.AppSettingsSection> `System.Configuration` .

.NET Framework altyapısı içinde, üst öğelerinden özellikleri devralan yapılandırma dosyalarının bir hiyerarşisi vardır. Herhangi bir alt yapılandırma dosyasında kullanılabilecek veya geçersiz kılınabilen birçok özelliği ve yapılandırma bölümünü tanımlayan bir *Machine. config* dosyası bulabilirsiniz.

### <a name="configuration-on-net-core"></a>.NET Core üzerinde yapılandırma

.NET Core dünyasında *Machine. config* dosyası yoktur. Eski tip ad alanını kullanmaya devam edebilse de <xref:System.Configuration> , <xref:Microsoft.Extensions.Configuration> iyi sayıda geliştirme sunan modern 'e geçmeyi düşünebilirsiniz.

Yapılandırma API 'SI yapılandırma sağlayıcısı kavramını destekler, bu da yapılandırmayı yüklemek için kullanılacak veri kaynağını tanımlar. Farklı türlerde yerleşik sağlayıcılar vardır, örneğin:

- Bellek içi .NET nesneleri
- INı dosyaları
- JSON dosyaları
- XML dosyaları
- Komut satırı bağımsız değişkenleri
- Ortam değişkenleri
- Şifrelenmiş kullanıcı deposu

 Ya da kendi kendinizinkini oluşturabilirsiniz.

Yeni yapılandırma, çok düzeyli bir hiyerarşide gruplandırılabilen ad-değer çiftleri listesine izin verir. Depolanan herhangi bir değer bir dizeye eşlenir ve ayarları özel bir düz eski CLR nesne (POCO) nesnesine serisini kaldırmanıza olanak sağlayan yerleşik bağlama desteği vardır.

<xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>Nesnesi, tercihinizi çözümlemek için öncelik kuralını kullanarak uygulamanız için ihtiyacınız olabilecek birçok yapılandırma sağlayıcısı eklemenize olanak tanır. Bu nedenle, kodunuzda eklediğiniz son sağlayıcı diğerlerini geçersiz kılar. Geliştirme, test ve üretim ortamları için farklı konfigürasyonlar tanımlayabileceğinizden ve bunları kodunuzun içindeki tek bir işlevde yönetebilmeniz için, yürütme için farklı ortamları yönetmeye yönelik harika bir özelliktir.

### <a name="migrating-configuration-files"></a>Yapılandırma dosyalarını geçirme

Mevcut App. config XML dosyanızı kullanmaya devam edebilirsiniz. Bununla birlikte, yapılandırmanızı .NET Core 'da yapılan çeşitli geliştirmelerden yararlanmak için geçirebilirsiniz.

Eski stil bir *app. config* dosyasından yeni bir yapılandırma dosyasına geçiş yapmak için, bir XML BIÇIMI ve JSON biçimi arasında seçim yapmanız gerekir.

XML seçerseniz, dönüştürme basittir. İçerik aynı olduğundan, *app. config* dosyasını XML uzantılı bir dosya olarak yeniden adlandırmanız yeterlidir. Daha sonra, sınıfını kullanmak için AppSettings 'e başvuran kodu değiştirin `ConfigurationBuilder` . Bu değişiklik kolay olmalıdır.

Bir JSON biçimi kullanmak istiyorsanız ve el ile geçiş yapmak istemiyorsanız, .NET Core 'da bir *app. config* dosyasını bir JSON yapılandırma dosyasına dönüştürebilen [DotNet-config2json](https://www.nuget.org/packages/dotnet-config2json/) adlı bir araç mevcuttur.

*Machine. config* dosyasında tanımlanan yapılandırma bölümlerini kullanırken bazı sorunlarla karşılaşabilirsiniz. Örneğin, aşağıdaki yapılandırmayı göz önünde bulundurun:

```xml
<configuration>
    <system.diagnostics>
        <switches>
            <add name="General" value="4" />
        </switches>
        <trace autoflush="true" indentsize="2">
            <listeners>
                <add name="myListener"
                     type="System.Diagnostics.TextWriterTraceListener,
                           System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
                     initializeData="MyListener.log"
                     traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />
            </listeners>
        </trace>
    </system.diagnostics>
</configuration>
```

Bu yapılandırmayı bir .NET Core 'a alırsanız, bir özel durum alırsınız:

Tanınmayan yapılandırma bölümü System. Diagnostics

Bu özel durum, bu bölüm ve bu bölümü işlemekten sorumlu olan *Machine. config* dosyasında tanımlanmasından sorumlu olduğu için oluşur.

Sorunu kolayca çözebilmeniz için, Bölüm tanımını eski *Machine. config* 'nizden yeni yapılandırma dosyanıza kopyalayabilirsiniz:

```xml
<configSections>
    <section name="system.diagnostics"
             type="System.Diagnostics.SystemDiagnosticsSection,
                   System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
</configSections>
```

## <a name="accessing-databases"></a>Veritabanlarına erişme

Neredeyse her masaüstü uygulamasının bir tür veritabanına ihtiyacı vardır. Masaüstü için, masaüstü uygulaması ve veritabanı altyapısı arasında doğrudan bağlantıyla istemci-sunucu mimarilerini bulmak yaygın bir uygulamadır. Bu veritabanları, farklı kullanıcılar arasında bilgi paylaşma gereksinimine bağlı olarak yerel veya uzak olabilir.

Kod perspektifinden, geliştiricilere bir veritabanını bağlama, sorgulama ve güncelleştirme olanağı sağlamak için birçok teknoloji ve çerçeve daha vardır.

Windows masaüstü uygulaması hakkında konuşurken bulabileceğiniz en yaygın veritabanı örnekleri, Microsoft Access ve Microsoft SQL Server. Masaüstüne yönelik 20 yıldan daha fazla deneyim yaşarsanız, ODBC, OLEDB, RDO, ADO, ADO.NET, LINQ ve Entity Framework gibi adlar tanıdık gelecektir.

### <a name="odbc"></a>ODBC

Microsoft `System.Data.Odbc` kitaplığı .NET Standard 2,0 ile uyumlu olduğundan, .NET Core ÜZERINDE ODBC kullanmaya devam edebilirsiniz.

### <a name="ole-db"></a>OLE DB

[OLE DB](https://msdn.microsoft.com/library/ms722784(v=vs.85).aspx)   , çeşitli veri kaynaklarına tek bir şekilde erişmenin harika bir yoludur. Ancak bu, yalnızca Windows teknolojisi olan ve .NET Core gibi platformlar arası bir teknolojinin en iyi şekilde uyum sağlayan COM 'a dayalıdır. Ayrıca, 2014 ve üzeri sürümlerde SQL Server de desteklenmez. Bu nedenlerden dolayı OLE DB .NET Core tarafından desteklenmez.

### <a name="adonet"></a>ADO.NET

.NET Core 'da mevcut masaüstü kodunuzla ADO.NET kullanmaya devam edebilirsiniz. Yalnızca bazı NuGet paketlerini güncelleştirmeniz gerekir.

### <a name="ef-core-vs-ef6"></a>EF Core vs. EF6

Entity Framework (EF), Entity Framework 6 (EF6) ve EF Core desteklenen iki sürümü vardır.

.NET Framework dünyanın bir parçası olarak yayınlanan en son teknoloji, en son sürüm olan 6,4 ile Entity Framework. Microsoft, .NET Core 'u başlatarak Entity Framework göre yeni bir veri erişim yığını da yayımladı ve Entity Framework Core çağırılır.

Hem .NET Framework hem de .NET Core EF Core EF 6,4 ve kullanabilirsiniz. Bu nedenle, iki arasında karar vermeye yardımcı olacak karar etmenleri nelerdir?

EF 6,3, .NET Core üzerinde çalışabilen ve platformlar arası iş üzerinde çalışan ilk EF6 sürümüdür. Aslında, bu yayının ana amacı, EF6 kullanan mevcut uygulamaları .NET Core 'a geçirmeyi daha kolay hale sağlamaktır.

EF Core, EF6 benzer bir geliştirici deneyimi sağlamak için tasarlanmıştır. En üst düzey API 'lerin çoğu aynı kalır, bu nedenle EF Core, EF6 kullanan geliştiricilere tanıdık gelecektir.

Uyumlu olsa da, bir karar vermeden önce kontrol etmeniz gereken uygulama farklılıkları vardır.
Daha fazla bilgi için bkz. [Compare EF Core & EF6](/ef/efcore-and-ef6/).

Şu durumlarda EF Core kullanımı önerilir:

* Uygulamanın .NET Core 'un özelliklerine ihtiyacı vardır.
* EF Core, uygulamanın gerektirdiği tüm özellikleri destekler.

Aşağıdaki koşulların her ikisi de doğruysa EF6 kullanmayı düşünün:

* Uygulama Windows ve .NET Framework 4,0 veya üzeri sürümlerde çalışır.
* EF6, uygulamanın gerektirdiği tüm özellikleri destekler.

### <a name="relational-databases"></a>İlişkisel veritabanları

#### <a name="sql-server"></a>SQL Server

SQL Server, masaüstü için birkaç yıl önce geliştirildiğinizi tercih ettiğiniz veritabanlarından biridir. .NET Framework kullanımı ile <xref:System.Data.SqlClient> , veritabanına özgü protokolleri kapsülleyen SQL Server sürümlerine erişebilirsiniz.

.NET Core 'da, `SqlClient` .NET Framework var olan, ancak kitaplıkta bulunan yeni bir sınıf bulabilirsiniz <xref:Microsoft.Data.SqlClient> . Yalnızca [Microsoft. Data. SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/) NuGet paketine bir başvuru eklemeniz ve ad alanları için birkaç yeniden adlandırma yapmanız ve her şeyin beklendiği gibi çalışması gerekir.

#### <a name="microsoft-access"></a>Microsoft Access

Microsoft Access, gelişmiş ve daha ölçeklenebilir SQL Server gerekmeyen yıllar için kullanılmıştır. Kitaplığı kullanarak Microsoft Access 'e yine de bağlanabilirsiniz <xref:System.Data.Odbc> .

## <a name="consuming-services"></a>Hizmetleri kullanma

Hizmet odaklı mimarilerin yerine, masaüstü uygulamaları, bir istemci-sunucu modelinden üç katmanlı yaklaşıma gelişmeye başlamıştır. İstemci-sunucu yaklaşımında, genellikle tek bir EXE dosyasının içinde iş mantığını tutan istemciden doğrudan bir veritabanı bağlantısı oluşturulur. Öte yandan, üç katmanlı yaklaşım, daha iyi güvenlik, ölçeklenebilirlik ve yeniden kullanılabilirlik sağlayan iş mantığı ve veritabanı erişimi uygulayan bir ara hizmet katmanı oluşturur. Veri veri kümeleri ile doğrudan çalışmak yerine, katman yaklaşımı, sözleşmeleri uygulayan bir dizi hizmete dayanır ve veri aktarımını uygulamak için bir yöntem olarak nesneleri ayarlar.

WCF hizmetini kullanan bir masaüstü uygulamanız varsa ve bunu .NET Core 'a geçirmek istiyorsanız göz önünde bulundurmanız gereken bazı noktalar vardır.

İlk şey, hizmete erişmek için yapılandırmanın çözümlenme yöntemi olur. Yapılandırma .NET Core üzerinde farklı olduğundan, yapılandırma dosyanızda bazı güncelleştirmeler yapmanız gerekir.

İkinci olarak, hizmet istemcisini Visual Studio 2019 ' de bulunan yeni araçlarla yeniden oluşturmanız gerekir. Bu adımda, istemciyi mevcut kodunuzla uyumlu hale getirmek için zaman uyumlu işlemlerin oluşturulmasını etkinleştirmeyi düşünmelisiniz.

Geçişten sonra, .NET Core 'da mevcut olmayan kitaplıkların olduğunu fark ederseniz, [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) NuGet paketine bir başvuru ekleyebilir ve eksik işlevlerin orada olup olmadığını görebilirsiniz.

<xref:System.Net.WebRequest>Web hizmeti çağrılarını gerçekleştirmek için sınıfını kullanıyorsanız, .NET Core ile ilgili bazı farklılıklar bulabilirsiniz. Bunun yerine System .net. http. HttpClient kullanılması önerilir.

## <a name="consuming-a-com-object"></a>COM nesnesi kullanma

Şu anda, .NET Core ile kullanmak üzere Visual Studio 2019 ' den bir COM nesnesine başvuru eklemenin bir yolu yoktur. Bu nedenle, proje dosyasını el ile değiştirmeniz gerekir.

`COMReference`Proje dosyasının içine aşağıdaki örnekteki gibi bir yapı ekleyin:

```xml
<ItemGroup>
    <COMReference Include="MSHTML">
        <Guid>{3050F1C5-98B5-11CF-BB82-00AA00BDCE0B}\</Guid>
        <VersionMajor>4</VersionMajor>
        <VersionMinor>0</VersionMinor>
        <Lcid>0</Lcid>
        <WrapperTool>primary</WrapperTool>
        <Isolated>false</Isolated>
    </COMReference>
</ItemGroup>
```

## <a name="more-things-to-consider"></a>Dikkate alınması gereken şeyler

.NET Framework kitaplıkları için kullanılabilen çeşitli teknolojiler .NET Core için kullanılamaz. Kodunuz Bu teknolojilerden bazılarını kullanıyorsa, bu bölümde özetlenen alternatif yaklaşımları göz önünde bulundurun.

[Windows Uyumluluk Paketi](../../core/porting/windows-compat-pack.md) , daha önce yalnızca .NET Framework için kullanılabilir olan API 'lere erişim sağlar. .NET Core ve .NET Standard projelerinde kullanılabilir.

API uyumluluğu hakkında daha fazla bilgi için, konumundaki son değişiklikler ve kullanım dışı/eski API 'Ler hakkında belge bulabilirsiniz <https://docs.microsoft.com/dotnet/core/compatibility/fx-core> .

### <a name="appdomains"></a>Uygulama

Uygulama etki alanları (AppDomain), uygulamaları birbirinden ayırır. AppDomain, çalışma zamanı desteği gerektirir ve pahalıdır. Ek uygulama etki alanlarının oluşturulması desteklenmez. Kod yalıtımı için, farklı süreçler veya kapsayıcılar kullanmanın alternatif olarak kullanılması önerilir. Derlemelerin dinamik yüklemesi için yeni  <xref:System.Runtime.Loader.AssemblyLoadContext> sınıfı öneririz.

Kod .NET Framework geçişini daha kolay hale getirmek için .NET Core, AppDomain API yüzeyini bir kısmını ortaya çıkarır. API 'lerden bazıları normal olarak çalışır (örneğin,  <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType> ), bazı Üyeler hiçbir şey yapmaz (örneğin,)  <xref:System.AppDomain.SetCachePath%2A> ve bazıları <xref:System.PlatformNotSupportedException> (örneğin,  <xref:System.AppDomain.CreateDomain%2A> ).

### <a name="remoting"></a>Uzaktan iletişim

.NET Remoting, artık desteklenmeyen geçici AppDomain iletişimi için kullanıldı. Ayrıca, uzaktan Iletişim için, bakım açısından pahalı olan çalışma zamanı desteği gerekir. Bu nedenlerle .NET Core üzerinde .NET uzaktan Iletişim desteklenmez.

İşlemler arasında iletişim için, veya sınıfı gibi uzaktan iletişim (IPC) mekanizmalarını bir alternatif olarak düşünmeniz gerekir <xref:System.IO.Pipes?displayProperty=nameWithType> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> .

Makineler arasında, alternatif olarak ağ tabanlı bir çözüm kullanın. Tercihen, HTTP gibi düşük ek bir düz metin protokolü kullanın. ASP.NET Core tarafından kullanılan Web sunucusu olan Kestrel Web sunucusu, burada bir seçenektir.

### <a name="code-access-security-cas"></a>Kod Erişimi Güvenliği (CAS)

Yönetilen bir uygulamanın veya kitaplığın hangi kaynakları kullanacağını veya çalıştığını kısıtlamak için çalışma zamanına veya çerçeveye dayanan korumalı alana alma, .NET Core üzerinde desteklenmez.

İşletim sistemi tarafından sunulan sanallaştırma, kapsayıcılar veya en düşük ayrıcalık kümesi ile işlem çalıştırmak için Kullanıcı hesapları gibi güvenlik sınırlarını kullanın.

### <a name="security-transparency"></a>Güvenlik saydamlığı

CA 'lara benzer şekilde, güvenlik saydamlığı, korumalı kodu bildirimle güvenlik açısından kritik koddan ayırır, ancak artık güvenlik sınırı olarak desteklenmez.

İşletim sistemi tarafından sunulan sanallaştırma, kapsayıcılar veya en az ayrıcalık kümesiyle işlem çalıştırmak için Kullanıcı hesapları gibi güvenlik sınırlarını kullanın.

>[!div class="step-by-step"]
>[Önceki](whats-new-dotnet-core.md ) 
> [Sonraki](windows-migration.md)
