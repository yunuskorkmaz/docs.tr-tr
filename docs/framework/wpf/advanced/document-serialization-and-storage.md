---
title: Belge Serileştirme ve Depolama
ms.date: 03/30/2017
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
ms.openlocfilehash: b60b3964ff8e1b1f05b6c0820c63ec06d9ea0f4c
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859648"
---
# <a name="document-serialization-and-storage"></a>Belge Serileştirme ve Depolama

Microsoft .NET Framework, yüksek kaliteli belgeleri görüntülemek ve oluşturmak için güçlü bir ortam sağlar.  Sabit belgeler hem akış Gelişmiş belgelerini destekleyen gelişmiş özellikler ile güçlü 2B görüntüleme denetimleri, birleştirilmiş ve 3B grafik özellikleri .NET Framework uygulamaları, kalite ve kullanıcı deneyimi yepyeni bir düzeye taşıyın.  Esnek bir bellek içi temsili bir belgenin yönetebilmek .NET Framework'ün temel bir özelliği ve verimli bir şekilde kaydedin ve bir veri deposundan belge yükleme neredeyse her uygulamanın.  Bir belge bir dış veri deposuna iç bellek içi gösterimden dönüştürme işlemi, serileştirme olarak adlandırılır.  Bir veri deposunun okuma ve orijinal bellek içi örnek yeniden ters işlemi seri durumundan çıkarma olarak adlandırılır.

<a name="AboutSerialization"></a>

## <a name="about-document-serialization"></a>Belge Serileştirme hakkında

İdeal olarak seri hale getirme ve bir belge, gelen ve ardından geri belleğe seri kaldırma işlemi uygulamaya saydamdır.  Uygulama "yöntemi, bir seri durumdan çıkarıcının"yöntem veri deposu erişir ve bellek özgün örneğinde yeniden oluşturur okurken"belgeyi kaydetmek için yazma" seri hale getirici çağırır.  Veriler depolanır belirli biçimi, genel olarak serileştirme uzun ve belge için özgün biçimlerinde Yedekleme işleminin oluşturduğu seri durumdan uygulamanın önemli değil.

Uygulamalar genellikle farklı Orta veya farklı bir biçim belgeleri kaydetmek kullanıcı izin veren birden fazla seri hale getirme seçeneği sağlar.  Örneğin, bir uygulama bir disk dosyası, veritabanı veya web hizmeti için bir belge depolamak için "Farklı Kaydet" seçeneğini sunar.  Benzer şekilde, farklı seri hale getiricileri genişletme farklı biçimlerde olduğu gibi HTML, RTF, XML, XPS veya bir üçüncü taraf biçimine alternatif belge saklayabilirsiniz.  Uygulamaya serileştirme depolama ortamına her özel seri hale getirici uygulamasında ayrıntılarını yalıtan bir arabirim tanımlar.  Depolama ayrıntıları, .NET Framework şifreleme avantajları yanı sıra <xref:System.Windows.Documents.Serialization> API'leri, çeşitli önemli özellikleri sağlar.

### <a name="features-of-net-framework-30-document-serializers"></a>.NET Framework 3.0 belge seri hale getiricileri genişletme özellikleri

- Üst düzey belge nesneleri (mantıksal ağaç ve görseller) doğrudan erişim verimli depolama sayfalandırılmış içeriği, 2B/3B öğeleri, görüntüleri, medya, köprüler, ek açıklamalar ve diğer destek içeriği etkinleştirin.

- Zaman uyumlu ve zaman uyumsuz işlem.

- Gelişmiş Özellikler ile eklenti seri hale getiricileri genişletme desteği:

  - Tüm .NET Framework uygulamaları tarafından kullanılmak üzere sistem genelinde erişim.

  - Eklenti bulunabilirliği basit uygulaması.

  - Basit Dağıtım, yükleme ve güncelleştirme özel üçüncü taraf eklentileri için.

  - Özel çalışma zamanı ayarları ve seçenekleri için kullanıcı arabirimi desteği.

### <a name="xps-print-path"></a>XPS yazdırma yolu

Microsoft .NET Framework [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] yazdırma yolu ayrıca çıktıda aracılığıyla belgeleri yazdırma için genişletilebilir bir mekanizma sağlar.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] hem bir belge dosyası biçimi görev yapar ve yerel yazdırma biriktiricisi biçimi [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] belgeleri doğrudan gönderilebilir [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-uyumlu yazıcılara Ara biçime dönüştürme gereksinimi olmadan.  Bkz: [yazdırma genel bakış](printing-overview.md) yazdırma yolu çıkış seçenekler ve özellikler hakkında daha fazla bilgi için.

<a name="PluginSerializers"></a>

## <a name="plug-in-serializers"></a>Eklenti seri hale getiricileri genişletme

<xref:System.Windows.Documents.Serialization> API'leri Eklenti serileştiricileri ve uygulamadan ayrı olarak yüklenmiş bağlantılı serileştiriciler için destek sağlar, çalışma zamanında bağlayın ve kullanılarak erişilen <xref:System.Windows.Documents.Serialization.SerializerProvider> keşif mekanizması.  Eklenti seri hale getiricileri genişletme, dağıtım ve sistem genelinde kullanım kolaylığı için Gelişmiş yararlar.  Bağlantılı seri hale getiricileri genişletme de uygulanabilir için kısmi güven ortamları gibi [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] Eklenti serileştiricileri olmadığı erişilebilir.  Bağlantılı bir türetilmiş uygulamasına dayalı serileştiricileri <xref:System.Windows.Documents.Serialization.SerializerWriter> sınıfı derlenir ve doğrudan uygulamaya bağlı.  Eklenti serileştiricileri ve bağlı seri hale getiricileri genişletme ile aynı genel yöntemler çalışır ve kolaylaştırmak olayları aynı uygulamada biri veya her ikisi türlerinden birini kullanın.

Eklenti serileştiricileri uygulama geliştiricileri için olası her biçim doğrudan yapı zamanında kod gerek kalmadan yeni depolama tasarımları ve dosya biçimleri için genişletilebilirlik sağlayarak yardımcı.  Eklenti serileştiricileri dağıtma, yüklemek ve sistem erişilebilir eklentileri özel veya özel dosya biçimleri için güncelleştirme için standartlaştırılmış bir yol sağlayarak üçüncü taraf geliştiriciler de yararlanabilir.

### <a name="using-a-plug-in-serializer"></a>Eklenti serileştirici kullanma

Eklenti serileştiricileri kullanmak daha kolaydır.  <xref:System.Windows.Documents.Serialization.SerializerProvider> Sınıfı numaralandırır bir <xref:System.Windows.Documents.Serialization.SerializerDescriptor> sistemde yüklü olan her eklenti için nesne.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> Özelliği, geçerli yapılandırmanız temelinde yüklü eklentiler filtreler ve seri hale getirici yüklenebilir ve uygulama tarafından kullanılan olduğunu doğrular.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor> Ayrıca diğer özellikleri gibi sağlar <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> ve <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>, uygulama için kullanılabilir çıktı biçimi serileştirici kullanıcıdan istemek için kullanabilirsiniz.  Bir varsayılan eklenti için seri hale getirici [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] .NET Framework ile birlikte sağlanır ve her zaman numaralandırılmış alan şeklinde.  Kullanıcı bir çıkış biçimini seçtikten sonra <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> yöntemi oluşturmak için kullanılan bir <xref:System.Windows.Documents.Serialization.SerializerWriter> belirli biçimi.  <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> yöntemi daha sonra veri deposunu belge akışa çıktısını almak için çağrılabilir.

Aşağıdaki örnekte kullanan bir uygulamayı <xref:System.Windows.Documents.Serialization.SerializerProvider> "PlugInFileFilter" özellik yöntemi.  PlugInFileFilter yüklü eklentiler numaralandırır ve kullanılabilir bir dosya seçenekleri içeren bir filtre dizesi oluşturur bir <xref:Microsoft.Win32.SaveFileDialog>.

[!code-csharp[DocumentSerialize#DocSerializeFileFilter](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]

Çıkış dosyası adı kullanıcı tarafından seçilen sonra aşağıdaki örnek, kullanımını gösterir. <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> belirli bir belge belirtilen bir biçimde depolamak için yöntemi.

[!code-csharp[DocumentSerialize#DocSerializePlugIn](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]

<a name="InstallingPluginSerializers"></a>

### <a name="installing-plug-in-serializers"></a>Eklenti Serileştiricileri Yükleme

<xref:System.Windows.Documents.Serialization.SerializerProvider> Sınıfı eklenti seri hale getirici bulma ve erişim için üst düzey uygulama arabirimi sağlar.  <xref:System.Windows.Documents.Serialization.SerializerProvider> bulur ve uygulama yüklenir ve sistemdeki erişilebilir seri hale getiricileri genişletme listesini sağlar.  Seri hale getiricileri genişletme yüklü ayrıntılarını kayıt defteri ayarları tanımlanır.  Eklenti serileştiricileri eklenebilir kayıt defterine kullanarak <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> yöntem; ya da .NET Framework değil henüz yüklü eklenti yükleme komut dosyasını doğrudan ayarlayabilirsiniz kendisini kayıt defteri değerleri.  <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> Yöntemi, daha önce yüklenen kaldırmak için kullanılabilir eklenti veya kayıt defteri ayarlarını benzer şekilde bir kaldırma komut dosyası tarafından sıfırlanabilir.

### <a name="creating-a-plug-in-serializer"></a>Bir eklenti seri hale getirici oluşturma

Eklenti serileştiricileri ve bağlı seri hale getiricileri genişletme aynı sunulan genel yöntemleri ve olayları kullanın ve zaman uyumlu veya zaman uyumsuz olarak çalışmasına benzer şekilde tasarlanabilir.  Normalde bir eklenti seri hale getirici oluşturmak için izlenen üç temel adım vardır:

1. Uygulama ve seri hale getirici bağlantılı bir serileştirici olarak ilk hatalarını ayıklayın.  Başlangıçta derlenir ve bir test uygulaması doğrudan bağlı seri hale getirici oluşturma, test etmek için tam erişim kesme noktaları ve diğer yararlı hata ayıklama hizmetleri sağlar.

2. Seri hale getirici tam olarak test edildikten sonra bir <xref:System.Windows.Documents.Serialization.ISerializerFactory> arabirimi eklenti oluşturma eklenir.  <xref:System.Windows.Documents.Serialization.ISerializerFactory> Arabirimi mantıksal ağaç içeren tüm .NET Framework nesnelere tam erişim veren <xref:System.Windows.UIElement> nesneleri <xref:System.Windows.Documents.IDocumentPaginatorSource>, ve <xref:System.Windows.Media.Visual> öğeleri.  Ayrıca <xref:System.Windows.Documents.Serialization.ISerializerFactory> aynı zaman uyumlu ve zaman uyumsuz yöntemleri ve bağlantılı serileştiriciler tarafından kullanılan olayları sağlar.  Büyük belgelerin çıkış sürebilir olduğundan, zaman uyumsuz işlemler duyarlı kullanıcı etkileşimini korumak ve veri deposuyla ilgili bir sorun oluşursa, bir "İptal" seçeneği sunmak için önerilir.

3. Eklenti seri hale getirici oluşturulduktan sonra bir yükleme betiği dağıtmak için uygulanır ve yükleme (ve kaldırma) eklenti (bkz. Yukarıdaki "[eklentisi Serileştiricileri Yükleme](#InstallingPluginSerializers)").

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Documents.Serialization>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
- [XML Kağıt Belirtimi: Genel Bakış](https://go.microsoft.com/fwlink?LinkID=106246)
