---
title: Belge Serileştirme ve Depolama
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6b1cc63b5118280a0a06fe63961c6e54792ed09
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="document-serialization-and-storage"></a>Belge Serileştirme ve Depolama
Microsoft .NET Framework yüksek kaliteli belgeleri görüntülemek ve oluşturmak için güçlü bir ortam sağlar.  Sabit belgeler ve akış Gelişmiş belgelerini destekleyen gelişmiş özellikler görüntüleme denetimleri, güçlü 2B ile birlikte ve kalite ve kullanıcı deneyimi, yeni bir düzeyi .NET Framework uygulama 3B grafik özellikleri gerçekleştirin.  Esnek bir bellek içi temsili bir belgenin yönetme kabiliyeti .NET Framework'ün bir anahtar özellik ve verimli bir şekilde belgeleri kaydetme ve bir veri deposundan yükleme yapamamasına neredeyse her uygulamanın.  Bir belgeyi iç bellek içi gösteriminden bir dış veri deposuna dönüştürme işlemi, serileştirme olarak adlandırılır.  Bir veri deposu okuma ve özgün bellek içi örneğini yeniden tersine çevirme işlemi seri olarak adlandırılır.  
  
 
  
<a name="AboutSerialization"></a>   
## <a name="about-document-serialization"></a>Belge Serileştirme hakkında  
 İdeal olarak seri hale getirme ve bir belgeyi gelen ve ardından geri belleğe seri durumdan Çıkarmada işlemi uygulamaya saydamdır.  Uygulama "write yöntemi seri kaldırıcı"yöntemi veri deposuna erişip bellek içinde özgün örneği yeniden oluşturur okurken"belgeyi kaydetmek için" seri hale getirici çağırır.  Veriler depolanır belirli biçimi genelde olarak serileştirme uzun ve belgenin geri özgün formuna işlem oluşturduğu seri durumdan uygulamasının ilgili bir sorun değildir.  
  
 Uygulamalar genellikle farklı ortama veya farklı bir biçim belgeleri kaydetmek kullanıcı izin veren birden fazla seri hale getirme seçeneği sağlar.  Örneğin, bir uygulama bir disk dosyası, veritabanı veya web hizmeti için bir belge depolamak için "Farklı Kaydet" seçenekleri sunabilir.  Benzer şekilde, farklı serileştiricileri farklı biçimlerde gibi HTML, RTF, XML, XPS veya alternatif bir üçüncü taraf biçimine belge saklayabilirsiniz.  Uygulama için seri hale getirme her belirli serileştiricinin uygulamasında depolama ortamı ayrıntılarını yalıtan bir arabirim tanımlar.  Depolama ayrıntıları, .NET Framework Kapsüllenen avantajlarını yanı sıra <xref:System.Windows.Documents.Serialization> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] çeşitli önemli özellikler sağlar.  
  
### <a name="features-of-net-framework-30-document-serializers"></a>.NET Framework 3.0 belge serileştirici özellikleri  
  
-   Üst düzey belge nesnelerine (mantıksal ağacının ve görselleri) doğrudan erişim numaralı içerik, 2B/3B öğelerin, görüntüleri, ortam, köprüler, ek açıklamalar ve diğer destek içeriğinin verimli depolama etkinleştirin.  
  
-   Zaman uyumlu ve zaman uyumsuz işlem.  
  
-   Gelişmiş özellikleri ile Eklenti serileştiricileri desteği:  
  
    -   Tüm .NET Framework uygulamaları tarafından kullanılmak üzere sistem genelinde erişim.  
  
    -   Basit uygulama eklentisi bulunabilirliği.  
  
    -   Basit Dağıtım, yükleme ve güncelleştirme özel üçüncü taraf eklentiler için.  
  
    -   Özel çalışma zamanı ayarları ve seçenekleri için kullanıcı arabirimi desteği.  
  
### <a name="xps-print-path"></a>XPS yazdırma yolu  
 Microsoft .NET Framework [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] yazdırma yolu da belge yazdırma çıkış aracılığıyla yazmak için genişletilebilir bir mekanizma sağlar.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] Her iki bir belge dosya biçimi olarak hizmet verir ve yerel yazdırma biriktirme biçimi [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] belgeleri doğrudan gönderilebilir [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-Ara biçime dönüştürmeye gerek kalmadan uyumlu yazıcılar.  Bkz: [yazdırma genel bakış](../../../../docs/framework/wpf/advanced/printing-overview.md) yazdırma yolu çıkış seçenekler ve özellikler hakkında daha fazla bilgi için.  
  
<a name="PluginSerializers"></a>   
## <a name="plug-in-serializers"></a>Eklenti serileştiricileri  
 <xref:System.Windows.Documents.Serialization> API'leri Eklenti serileştiricileri ve uygulamadan ayrı olarak yüklenmiş bağlantılı serileştiricileri için destek sağlayabilirsiniz, çalışma zamanında bağlamak ve kullanılarak erişilen <xref:System.Windows.Documents.Serialization.SerializerProvider> bulma mekanizması.  Eklenti serileştiricileri, dağıtım ve sistem çapında kullanım kolaylığı için geliştirilmiş yararlar.  Bağlantılı serileştiricileri de uygulanabilir için kısmi güven ortamları gibi [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] burada Eklenti serileştiricileri olmayan erişilebilir.  Bağlantılı bir türetilmiş uygulamasına dayalı serileştiricileri <xref:System.Windows.Documents.Serialization.SerializerWriter> sınıfı, derlenir ve doğrudan uygulamaya bağlanırlar.  Eklenti serileştiricileri ve bağlantılı serileştiricileri aynı ortak yöntemler çalışır ve kolaylaştıran olaylar aynı uygulamada birini veya her ikisini türlerinden birini kullanın.  
  
 Eklenti serileştiricileri derleme zamanında her olası biçim için doğrudan kod gerek kalmadan yeni depolama tasarımlarına ve dosya biçimleri için genişletilebilirlik sağlayarak uygulama geliştiricileri yardımcı.  Eklenti serileştiricileri dağıtmak, yüklemek ve sistem erişilebilir eklentilerini özel ya da özel dosya biçimleri için güncelleştirmek için standartlaştırılmış bir yol sağlayarak üçüncü taraf geliştiricilere de yararlanabilir.  
  
### <a name="using-a-plug-in-serializer"></a>Eklenti serileştirici kullanma  
 Eklenti serileştiricileri kullanımı çok basittir.  <xref:System.Windows.Documents.Serialization.SerializerProvider> Sınıfı numaralandırır bir <xref:System.Windows.Documents.Serialization.SerializerDescriptor> sistemde yüklü olan her eklenti için nesne.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> Özelliği geçerli yapılandırmasını temel alarak yüklü eklentileri filtreler ve seri hale getirici yüklenebilir ve uygulama tarafından kullanılan olduğunu doğrular.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor> Ayrıca diğer özellikleri gibi sağlar <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> ve <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>, uygulama kullanıcıdan kullanılabilir çıktı biçimi için serileştirici için kullanabilirsiniz.  İçin bir varsayılan eklenti serileştirici [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] .NET Framework ile birlikte sağlanır ve her zaman numaralandırılır.  Kullanıcı bir çıkış biçimini seçtikten sonra <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> yöntemi oluşturmak için kullanılan bir <xref:System.Windows.Documents.Serialization.SerializerWriter> belirli biçim için.  <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> yöntemi, veri deposu belge akışı çıktısını almak için sonra çağrılabilir.  
  
 Aşağıdaki örnek kullanan bir uygulama gösterilmektedir <xref:System.Windows.Documents.Serialization.SerializerProvider> "PlugInFileFilter" özelliği yöntemi.  PlugInFileFilter yüklü eklentileri numaralandırır ve bir filtre dizesi için kullanılabilir bir dosya seçeneklerle derlemeler bir <xref:Microsoft.Win32.SaveFileDialog>.  
  
 [!code-csharp[DocumentSerialize#DocSerializeFileFilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]  
  
 Aşağıdaki örnek bir çıktı dosyası adı kullanıcı tarafından seçilen sonra kullanımını göstermektedir <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> verilen belgeyi belirtilen biçimde saklamak için yöntem.  
  
 [!code-csharp[DocumentSerialize#DocSerializePlugIn](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]  
  
<a name="InstallingPluginSerializers"></a>   
### <a name="installing-plug-in-serializers"></a>Eklenti Serileştiricileri Yükleme  
 <xref:System.Windows.Documents.Serialization.SerializerProvider> Sınıf, eklenti serileştiricisi bulma ve erişimi için üst düzey uygulama arayüzü sağlar.  <xref:System.Windows.Documents.Serialization.SerializerProvider> bulur ve uygulama yüklenir ve sistem üzerindeki erişilebilir serileştiricileri listesini sağlar.  Yüklü serileştiricileri ayrıntılarını kayıt defteri ayarları aracılığıyla tanımlanır.  Eklenti serileştiricileri eklenebilir kayıt defterine kullanarak <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> yöntemi; veya .NET Framework değil henüz yüklü, eklenti yükleme komut dosyasını doğrudan ayarlayabilirsiniz kendisini kayıt defteri değerleri.  <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> Yöntemi, önceden yüklenmiş kaldırmak için kullanılabilir eklentisini veya kayıt defteri ayarlarını benzer şekilde bir kaldırma komut dosyası tarafından sıfırlanabilir.  
  
### <a name="creating-a-plug-in-serializer"></a>Eklenti serileştirici oluşturma  
 Eklenti serileştiricileri ve bağlantılı serileştiricileri aynı sunulan genel yöntemleri ve olayları kullanın ve benzer şekilde eşzamanlı veya zaman uyumsuz olarak çalışması için tasarlanmış olabilir.  Eklenti bir seri hale getirici oluşturmak için normalde ardından üç temel adımlar verilmiştir:  
  
1.  Uygulama ve seri hale getirici bağlantılı bir seri hale getirici önce hata ayıklama.  Başlangıçta derlenmiş ve bir sınama uygulamasına doğrudan bağlanmış serileştirici oluşturma test etmek için kesme noktaları ve yararlı diğer hata ayıklama hizmetlerine tam erişim sağlar.  
  
2.  Serileştirici tamamen test edildikten sonra bir <xref:System.Windows.Documents.Serialization.ISerializerFactory> arabirimi eklenti oluşturmak için eklenir.  <xref:System.Windows.Documents.Serialization.ISerializerFactory> Arabirimi mantıksal ağacının içeren tüm .NET Framework nesnelere tam erişim verir <xref:System.Windows.UIElement> nesneleri <xref:System.Windows.Documents.IDocumentPaginatorSource>, ve <xref:System.Windows.Media.Visual> öğeleri.  Ayrıca <xref:System.Windows.Documents.Serialization.ISerializerFactory> aynı zaman uyumlu ve zaman uyumsuz yöntemleri ve bağlantılı serileştiricileri tarafından kullanılan olayları sağlar.  Büyük belgeleri çıktı sürebilir olduğundan, zaman uyumsuz işlemleri esnek kullanıcı etkileşimini korumak ve veri deposuyla ilgili bir sorun oluşursa, "İptal" seçeneğini sunmak için önerilir.  
  
3.  Eklenti serileştiricisi oluşturulduktan sonra bir yükleme komut dosyası dağıtılmasında uygulanır ve yükleme (ve kaldırma) Eklentisi (bkz: Yukarıdaki "[Eklenti Serileştiricileri Yükleme](#InstallingPluginSerializers)").  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Documents.Serialization>  
 <xref:System.Windows.Xps.XpsDocumentWriter>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Yazdırmaya Genel Bakış](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [XML Kağıt Belirtimi: genel bakış](http://go.microsoft.com/fwlink?LinkID=106246)
