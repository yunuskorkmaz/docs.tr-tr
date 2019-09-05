---
title: Belge Serileştirme ve Depolama
ms.date: 03/30/2017
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
ms.openlocfilehash: 7ddd887eefd67a3300795396dac26e855f30989e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254118"
---
# <a name="document-serialization-and-storage"></a>Belge Serileştirme ve Depolama

Microsoft .NET Framework, yüksek kaliteli belgeler oluşturmak ve görüntülemek için güçlü bir ortam sağlar.  Hem sabit belgeleri hem de akış belgelerini destekleyen gelişmiş özellikler, güçlü 2B ve 3B grafik özellikleriyle birleştirilmiş gelişmiş görüntüleme denetimleri, .NET Framework uygulamaları yeni bir kalite ve Kullanıcı deneyimi düzeyine götürür.  Bir belgenin bellek içi gösterimini esnek bir şekilde yönetebilmek, .NET Framework temel bir özelliktir ve bir veri deposundan belgeleri verimli bir şekilde kaydedip yükleyebilmekte olan neredeyse her uygulamanın bir ihtiyacı vardır.  Bir belgeyi dahili bir bellek içi gösterimden dış veri deposuna dönüştürme işlemi serileştirme olarak adlandırılır.  Bir veri deposunu okumayı ve özgün bellek içi örneği yeniden oluşturmayı yeniden oluşturma işlemi, seri durumdan çıkarma işlemini geri adlandırılmış hale getirilir.

<a name="AboutSerialization"></a>

## <a name="about-document-serialization"></a>Belge serileştirme hakkında

İdeal olarak, bir belgeyi serileştirmek ve seri durumdan çıkarmak ve sonra da uygulamaya geri dönmek için idealdir.  Uygulama, seri hale getirici "okuma" yöntemi veri deposuna eriştiğinde ve özgün örneği bellekte yeniden oluşturur.  Verilerin depolandığı belirli biçim genellikle serileştirme ve seri durumdan çıkarma işlemi belgeyi özgün biçimine geri oluşturursa uygulamanın bir sorunu değildir.

Uygulamalar genellikle kullanıcının belgeleri farklı bir ortama veya farklı bir biçime kaydetmesine izin veren birden çok serileştirme seçeneği sağlar.  Örneğin, bir uygulama bir belgeyi disk dosyasında, veritabanında veya Web hizmetinde depolamak için "farklı kaydet" seçeneğini sunabilir.  Benzer şekilde, farklı serileştiriciler belgeyi HTML, RTF, XML, XPS gibi farklı biçimlerde veya alternatif olarak üçüncü taraf bir biçimde saklayabilir.  Seri hale getirme, her belirli bir seri hale getiricinin uygulamasındaki depolama ortamının ayrıntılarını yalıtan bir arabirim tanımlar.  Depolama ayrıntılarının kapsüllenmesi avantajlarına ek olarak .NET Framework <xref:System.Windows.Documents.Serialization> API 'leri, diğer birçok önemli özelliği de sağlar.

### <a name="features-of-net-framework-30-document-serializers"></a>.NET Framework 3,0 belge serileştiricilerinin özellikleri

- Üst düzey belge nesnelerine (mantıksal ağaç ve görseller) doğrudan erişim, sayfalandırılmış içeriğin, 2B/3B öğelerin, görüntülerin, medyanın, köprülerin, ek açıklamaların ve diğer destek içeriğinin verimli bir şekilde depolanmasını sağlar.

- Zaman uyumlu ve zaman uyumsuz işlem.

- Gelişmiş özelliklerde Eklenti serileştiricileri desteği:

  - Tüm .NET Framework uygulamalar tarafından kullanım için sistem genelinde erişim.

  - Basit uygulama eklentisi bulunabilirliği.

  - Özel üçüncü taraf eklentileri için basit dağıtım, yükleme ve güncelleştirme.

  - Özel çalışma zamanı ayarları ve seçenekleri için Kullanıcı arabirimi desteği.

### <a name="xps-print-path"></a>XPS yazdırma yolu

Microsoft .NET Framework XPS yazdırma yolu Ayrıca, Yazdırma çıktısı aracılığıyla belge yazmak için genişletilebilir bir mekanizma sağlar.  XPS, bir belge dosyası biçimi olarak hizmet verir ve için [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]yerel yazdırma biriktirme biçimidir.  XPS belgeleri, bir ara biçime dönüştürmeye gerek olmadan doğrudan XPS uyumlu yazıcılara gönderilebilir.  Yazdırma yolu çıkış seçenekleri ve özellikleri hakkında daha fazla bilgi için bkz. [yazdırmayla Ilgili genel bakış](printing-overview.md) .

<a name="PluginSerializers"></a>

## <a name="plug-in-serializers"></a>Eklenti serileştiricileri

API 'ler, hem Eklenti serileştiricileri hem de uygulamadan ayrı olarak yüklenen bağlantılı serileştiriciler için destek sağlar, çalışma zamanında bağlanır ve <xref:System.Windows.Documents.Serialization.SerializerProvider> bulma mekanizması kullanılarak erişilir. <xref:System.Windows.Documents.Serialization>  Eklenti serileştiricileri, dağıtım ve sistem genelinde kullanım kolaylığı için gelişmiş avantajlar sunar.  Bağlı serileştiriciler, Eklenti serileştiricileri erişilebilir olmadığı gibi [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] kısmi güven ortamları için de uygulanabilir.  <xref:System.Windows.Documents.Serialization.SerializerWriter> Sınıfının türetilmiş bir uygulamasını temel alan bağlantılı serileştiriciler derlenir ve doğrudan uygulamaya bağlanır.  Hem Eklenti serileştiricileri hem de bağlantılı serileştiriciler aynı uygulamada her iki seri hale getirme türünü kullanmayı kolaylaştıran aynı ortak Yöntemler ve olaylar aracılığıyla çalışır.

Eklenti serileştiricileri, derleme zamanında her olası biçim için doğrudan kod oluşturmaya gerek kalmadan yeni depolama tasarımlarına ve dosya biçimlerine genişletilebilirlik sağlayarak uygulama geliştiricilerine yardımcı olur.  Eklenti serileştiricileri, özel veya özel dosya biçimleri için sistem tarafından erişilebilir eklentileri dağıtmak, yüklemek ve güncelleştirmek için standartlaştırılmış bir yol sunarak üçüncü taraf geliştiricilere de yararlanır.

### <a name="using-a-plug-in-serializer"></a>Eklenti serileştirici kullanma

Eklenti serileştiricileri kullanımı basittir.  Sınıfı <xref:System.Windows.Documents.Serialization.SerializerProvider> , sistemde yüklü <xref:System.Windows.Documents.Serialization.SerializerDescriptor> olan her eklenti için bir nesneyi numaralandırır.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> Özelliği, geçerli yapılandırmaya bağlı olarak yüklenen eklentileri filtreler ve seri hale getiricinin uygulama tarafından yüklenip kullanılabileceğini doğrular.  , <xref:System.Windows.Documents.Serialization.SerializerDescriptor> <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> Ve gibi<xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>diğer özellikleri de sağlar. Bu, uygulamanın, kullanıcının kullanılabilir çıkış biçimi için bir serileştirici seçmesini istemek için kullanabileceği.  XPS için varsayılan bir eklenti serileştirici .NET Framework ile sağlanır ve her zaman numaralandırılır.  Kullanıcı bir çıkış biçimi seçtikten sonra, <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> yöntemi belirli bir <xref:System.Windows.Documents.Serialization.SerializerWriter> biçim için oluşturmak üzere kullanılır.  <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> daha sonra yöntem, belge akışını veri deposuna çıkarmak için çağrılabilir.

Aşağıdaki örnek, "pluginfilefilter" özelliğindeki <xref:System.Windows.Documents.Serialization.SerializerProvider> yöntemi kullanan bir uygulamayı gösterir.  PlugInFileFilter yüklü eklentileri numaralandırır ve için <xref:Microsoft.Win32.SaveFileDialog>kullanılabilir dosya seçenekleriyle bir filtre dizesi oluşturur.

[!code-csharp[DocumentSerialize#DocSerializeFileFilter](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]

Bir çıkış dosyası adı Kullanıcı tarafından seçildikten sonra aşağıdaki örnek, belirtilen bir belgeyi belirli bir biçimde depolamak için <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> yönteminin kullanımını gösterir.

[!code-csharp[DocumentSerialize#DocSerializePlugIn](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]

<a name="InstallingPluginSerializers"></a>

### <a name="installing-plug-in-serializers"></a>Eklenti serileştiricileri yükleniyor

<xref:System.Windows.Documents.Serialization.SerializerProvider> Sınıfı, eklenti seri hale getirici bulma ve erişim için üst düzey uygulama arabirimi sağlar.  <xref:System.Windows.Documents.Serialization.SerializerProvider>, uygulamayı bulur ve sistemde yüklü ve erişilebilir olan serileştiricilerin bir listesini sağlar.  Yüklü serileştiricilerin özellikleri, kayıt defteri ayarları aracılığıyla tanımlanır.  Eklenti serileştiricileri, <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> yöntemi kullanılarak kayıt defterine eklenebilir veya .NET Framework henüz yüklenmemişse, eklenti yükleme betiği kayıt defteri değerlerinin kendisini doğrudan ayarlayabilir.  <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> Yöntemi, daha önce yüklenmiş bir eklentiyi kaldırmak için kullanılabilir veya kayıt defteri ayarları bir kaldırma betiği ile aynı şekilde sıfırlanabilir.

### <a name="creating-a-plug-in-serializer"></a>Eklenti serileştirici oluşturma

Hem Eklenti serileştiricileri hem de bağlantılı serileştiriciler aynı açık ortak yöntemleri ve olayları kullanır ve benzer şekilde, eş zamanlı veya zaman uyumsuz olarak çalışacak şekilde tasarlanabilir.  Genellikle bir eklenti serileştirici oluşturmak için üç temel adım vardır:

1. Önce serileştiriciyi bir bağlı seri hale getirici olarak uygulayın ve hata ayıklayın.  Başlangıçta derlenerek derlenen ve doğrudan bir test uygulamasında bağlanan seri hale getirici oluşturulması, kesme noktalarına ve diğer hata ayıklama hizmetlerine tam erişim sağlayarak test edilmesine yardımcı olur.

2. Serileştirici tamamen test edildikten sonra eklenti oluşturmak <xref:System.Windows.Documents.Serialization.ISerializerFactory> için bir arabirim eklenir.  Arabirim, mantıksal ağacı, <xref:System.Windows.UIElement> nesneleri, <xref:System.Windows.Documents.IDocumentPaginatorSource>ve <xref:System.Windows.Media.Visual> öğelerini içeren tüm .NET Framework nesnelerine tam erişim sağlar. <xref:System.Windows.Documents.Serialization.ISerializerFactory>  Ayrıca <xref:System.Windows.Documents.Serialization.ISerializerFactory> , bağlı serileştiriciler tarafından kullanılan aynı zaman uyumlu ve zaman uyumsuz yöntemleri ve olayları sağlar.  Büyük belgeler çıkışa zaman götürebileceği için, yanıt veren kullanıcı etkileşimini sürdürmek için zaman uyumsuz işlemler önerilir ve veri deposuyla ilgili bir sorun oluşursa bir "Iptal" seçeneği sunar.

3. Eklenti serileştirici oluşturulduktan sonra, eklentinin dağıtılması ve yüklenmesi (ve kaldırılması) için bir yükleme betiği uygulanır (bkz. yukarıdaki "[Eklenti serileştiricileri yükleme](#InstallingPluginSerializers)").

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Documents.Serialization>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
- [XML Kağıt Belirtimi: Genel Bakış](https://go.microsoft.com/fwlink?LinkID=106246)
