---
title: "Visual Studio Uygulamalarına Yazdırılabilir Raporlar Ekleme"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- printing [Visual Studio], reports
- reports [Visual Basic], printing in Visual Studio
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ce2a8b12d8202a9f201a82b0d4a571249210d48
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="adding-printable-reports-to-visual-studio-applications"></a>Visual Studio Uygulamalarına Yazdırılabilir Raporlar Ekleme
Visual Studio, Visual Basic uygulamalarınız için raporlama zengin veri eklemenize yardımcı olmak için raporlama çözümleri çeşitli destekler. ReportViewer denetimleri, Crystal Reports veya SQL Server Reporting Services kullanarak raporlar ekleyin ve yaratın.  
  
> [!NOTE]
>  SQL Server Reporting Services Visual Studio yerine SQL Server 2005'in bir parçasıdır. Reporting Services SQL Server 2005'in yüklü olduğu sürece, sisteminizde yüklü değil.  
  
## <a name="overview-of-microsoft-reporting-technology-in-visual-basic-applications"></a>Microsoft Visual Basic uygulamalarındaki teknolojisi Reporting genel bakış  
 Microsoft teknolojisi, uygulamanızda reporting kullanmak için aşağıdaki yaklaşımlar ile seçin:  
  
-   ReportViewer Denetimi'ni bir veya daha fazla örneğini bir Visual Basic Windows uygulamasına ekleyin.  
  
-   SQL Server Raporlama Hizmetleri rapor sunucusu Web hizmeti çağrıları yaparak program aracılığıyla tümleştirin.  
  
-   Microsoft SQL Server 2005 Reporting Services ve ReportViewer Denetimi'ni birlikte denetimi bir Rapor Görüntüleyicisi'ni ve bir rapor sunucusu rapor işlemci olarak kullanarak kullanın. (Bir rapor sunucusu ve ReportViewer Denetimi'ni birlikte kullanmak istiyorsanız, Reporting Services SQL Server 2005 sürümü kullanmanız gerektiğini unutmayın).  
  
## <a name="using-reportviewer-controls"></a>ReportViewer denetimlerini kullanma  
 Visual Basic Windows uygulamasına rapor işlevleri katıştırmak için en kolay yolu, uygulamanızdaki bir forma ReportViewer Denetimi'ni eklemektir. Denetim rapor özelliklerini uygulamanıza doğrudan işleme ekler ve herhangi bir ADO.NET veri nesnesi verileri kullanarak raporları oluşturabilmeleri bir tümleşik Rapor Tasarımcısı sağlar. Tam özellikli bir API denetimi programlı erişim sağlar ve böylece çalışma zamanı işlevselliği yapılandırabilirsiniz raporlar.  
  
 ReportViewer yerleşik rapor işleme ve yetenek tek, ücretsiz olarak dağıtılabilen veri denetiminde görüntüleme sağlar. Aşağıdaki rapor işlevleri gerekiyorsa ReportViewer denetimleri seçin:  
  
-   Rapor istemci uygulamasında işleme. İşlenen raporun denetimi tarafından sağlanan bir görünüm alanında görüntülenir.  
  
-   ADO.NET veri tabloları veri bağlama. Tüketen raporlar oluşturabilirsiniz <xref:System.Data.DataTable> denetime sağlanan örnekleri. Ayrıca, doğrudan iş nesnelere bağlayabilirsiniz.  
  
-   Uygulamanıza dahil yeniden dağıtılabilen denetimler.  
  
-   Çalışma zamanı işlevselliği sayfa gezintisi, yazdırma, arama ve dışarı aktarma gibi biçimlendirir. ReportViewer araç, bu işlemler için destek sağlar.  
  
 ReportViewer denetimi kullanmak için ondan sürükleyebilirsiniz **veri** Visual Studio araç kutusu, Visual Basic Windows uygulamanızda forma bölümü.  
  
### <a name="creating-reports-in-visual-studio-for-reportviewer-controls"></a>ReportViewer denetimleri için Visual Studio'da raporları oluşturma  
 ReportViewer içinde çalışan bir rapor oluşturmak için Ekle bir **rapor** projenize şablonu. Visual Studio istemci rapor tanım dosyası (.rdlc) oluşturur, dosyayı projenize ekler ve Visual Studio çalışma alanında bir tümleşik Rapor Tasarımcısı'nı açar.  
  
 Visual Studio Rapor Tasarımcısı ile tümleştirilir **veri kaynakları** penceresi. Bir alan sürüklediğinizde **veri kaynakları** raporu Rapor Tasarımcısı penceresine rapor tanımı dosyasına veri kaynağı ile ilgili meta verileri kopyalar. Bu meta veriler ReportViewer denetimi tarafından otomatik olarak veri bağlama kodu oluşturmak için kullanılır.  
  
 Visual Studio Rapor Tasarımcısı rapor Önizleme işlevleri içermez. Raporunuzu önizlemek için uygulamayı çalıştırın ve katıştırılmış rapor Önizleme.  
  
|Temel rapor işlevselliği uygulamanıza eklemek için|  
|---|    
|1.  ReportViewer denetimden sürükleyin **veri** sekmesinde **araç** formunuza.<br />2.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**. İçinde **Yeni Öğe Ekle** iletişim kutusunda **rapor** simgesi ve tıklatın **Ekle**.<br />     Rapor Tasarımcısı geliştirme ortamında açar ve bir rapor (.rdlc) dosyası projeye eklenir.<br />3.  Sürükleme rapor öğeleri **araç** rapor düzenini üzerinde ve bunları istediğiniz gibi düzenleyin.<br />4.  Sürükleme alanlardan **veri kaynakları** rapor öğeleri rapor düzenini penceresine.|  
  
## <a name="using-reporting-services-in-visual-basic-applications"></a>Raporlama Hizmetleri Visual Basic uygulamalarında kullanma  
 Reporting Services SQL Server'ın içerdiği bir sunucu tabanlı raporlama teknolojisidir. Raporlama Hizmetleri ReportViewer denetimleri bulunmayan ek özellikler içerir. Şu özellikler gerektiriyorsa Reporting Services'ı seçin:  
  
-   Genişleme dağıtımı ve karmaşık veya uzun süre çalışan raporları ve yüksek hacimli rapor etkinliği için Gelişmiş performans sağlayan sunucu tarafı rapor işleme.  
  
-   Tümleşik veri ve özel rapor denetimleri ve zengin işleme desteğiyle rapor işleme çıktı biçimleri.  
  
-   Böylece tam olarak rapor çalıştırıldığında belirtebilirsiniz rapor işleme zamanlanan.  
  
-   Abonelik tabanlı rapor dağıtım e-posta yoluyla veya dosya paylaşım konumları.  
  
-   Böylece iş kullanıcıları raporları gerektiği gibi oluşturabilirsiniz ad hoc raporlama.  
  
-   Çıktı özelleştirilmiş rapor dinamik alıcıların listesi için rota veri tabanlı abonelikler.  
  
-   Veri işleme, rapor teslimini, özel kimlik doğrulama ve rapor işleme için özel uzantıları.  
  
 Rapor sunucusu Web hizmeti olarak uygulanır. Uygulama kodunuz, raporlar ve diğer meta verilere erişmek için Web hizmeti çağrıları eklemeniz gerekir. Web hizmeti bir rapor sunucusu örneği tam programlı erişim sağlar.  
  
 Reporting Services raporlama teknolojisi Web tabanlı olduğundan, varsayılan Görüntüleyici işlendiğini raporları HTML biçiminde gösterir. HTML varsayılan rapor sunu biçimi kullanmak istemiyorsanız, uygulamanız için bir özel rapor Görüntüleyici yazma gerekecektir.  
  
### <a name="creating-reports-in-visual-studio-for-reporting-services"></a>Visual Studio için Raporlama Hizmetleri raporları oluşturma  
 Bir rapor sunucusunda çalıştırın raporlar oluşturmak için rapor tanımı (.rdl) dosyaları Business Intelligence Development Studio aracılığıyla Visual Studio ile SQL Server 2005 dahil edildiği oluşturun.  
  
> [!NOTE]
>  SQL Server 2005'in SQL Server Reporting Services ve Business Intelligence Development Studio kullanılabilmesi için yüklü olması gerekir.  
  
 Business Intelligence Development Studio SQL Server bileşenleri için özel proje şablonları ekler. Raporları oluşturmak için seçebileceğiniz **rapor sunucusu projesi** veya **rapor sunucusu Proje Sihirbazı** şablonları. Veri kaynağı bağlantılarını ve sorguları veri kaynağı türleri, SQL Server, Oracle, Analysis Services, XML ve SQL Server Integration Services de dahil olmak üzere çeşitli belirtebilirsiniz. A **veri** sekmesinde **düzeni** sekmesinde ve **Önizleme** sekmesini verileri tanımlamak, rapor düzenini oluşturma ve tüm aynı çalışma alanında rapor Önizleme olanak sağlar.  
  
 Derleme denetimi veya rapor sunucusu için rapor tanımları ya da teknoloji yeniden kullanılabilir.  
  
|Bir rapor sunucusunda çalışan bir rapor oluşturmak için|  
|---|    
|1.  Üzerinde **dosya** menüsünde seçin **yeni**.<br />     **Yeni proje** iletişim kutusu açılır.<br />2.  İçinde **proje türleri** bölmesinde tıklatın **Business Intelligence Projeleri**.<br />3.  Şablonlar bölmesinde seçin **rapor sunucusu projesi** veya **rapor sunucusu Proje Sihirbazı**.|  
  
## <a name="using-reportviewer-controls-and-sql-server-reporting-services-together"></a>ReportViewer denetimleri ve SQL Server Raporlama hizmetlerini birlikte kullanarak  
 ReportViewer denetimleri ve SQL Server 2005 Raporlama Hizmetleri, aynı uygulamada birlikte kullanılabilir.  
  
-   ReportViewer Denetimi'ni uygulamanızda raporları görüntülemek için kullanılan bir Görüntüleyici sağlar.  
  
-   Raporlama Hizmetleri raporları sağlar ve uzak bir sunucuda tüm işleme gerçekleştirir.  
  
 ReportViewer denetimi, bir uzak Raporlama Hizmetleri rapor sunucusunda depolanan ve işlenen raporları göstermek için yapılandırılabilir. Bu tür bir yapılandırma olarak adlandırılır *uzaktan işleme modunu*. Uzaktan işleme modunda, bir uzak rapor sunucusunda depolanan bir rapor denetimi ister. Rapor sunucusu, tüm rapor işleme, veri işleme ve rapor işleme gerçekleştirir. Tamamlanan, işlenen bir rapor denetime döndürülen ve görünümü bölmesinde görüntülenir.  
  
 Bir rapor sunucusu desteği üzerine ek çalıştırmak raporları verme biçimleri, farklı rapor parametrelemeyi uygulamasına sahipseniz, rapor sunucusu tarafından desteklenir ve rol tabanlı yetkilendirme modeli aracılığıyla erişilen veri kaynağı türleri kullanma Rapor sunucusu.  
  
 Uzaktan işleme modunu kullanmak için bir sunucu rapor için yol ve URL ReportViewer Denetimi'ni yapılandırırken belirtin.
