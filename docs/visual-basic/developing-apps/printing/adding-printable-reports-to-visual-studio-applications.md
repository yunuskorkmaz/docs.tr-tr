---
title: Visual Studio Uygulamalarına Yazdırılabilir Raporlar Ekleme
ms.date: 07/20/2015
helpviewer_keywords:
- printing [Visual Studio], reports
- reports [Visual Basic], printing in Visual Studio
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
ms.openlocfilehash: 65264deea3aeff1a633ea6888b3f175031b7fba5
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212020"
---
# <a name="adding-printable-reports-to-visual-studio-applications"></a>Visual Studio Uygulamalarına Yazdırılabilir Raporlar Ekleme
Visual Studio, çeşitli zengin, Visual Basic uygulamalarınıza raporlama verileri eklemek yardımcı olması için raporlama çözümleri destekler. ReportViewer denetimleri, Crystal Reports veya SQL Server Raporlama Hizmetleri'ni kullanarak raporlar ekleyin ve oluşturun.  

  
## <a name="overview-of-microsoft-reporting-technology-in-visual-basic-applications"></a>Microsoft Visual Basic uygulamalarındaki teknoloji raporlama genel bakış  
 Bir Microsoft teknoloji uygulamanızdaki reporting kullanmak için aşağıdaki yaklaşımlardan seçin:  
  
-   ReportViewer denetimi bir veya daha fazla örneğini bir Visual Basic Windows uygulamaya ekleyin.  
  
-   SQL Server Reporting Services rapor sunucusu Web hizmetine çağrı yaparak programlı bir şekilde tümleştirin.  
  
-   ReportViewer denetimi ve Microsoft SQL Server 2005 Raporlama Hizmetleri rapor işlemci olarak bir Rapor Görüntüleyicisi ve rapor sunucusu denetimini kullanarak birlikte kullanın. (Bir rapor sunucusu ve ReportViewer denetimi birlikte kullanmak istiyorsanız, Reporting Services SQL Server 2005 sürümünü kullanmanız gerektiğini unutmayın).  
  
## <a name="using-reportviewer-controls"></a>ReportViewer denetimleri kullanma  
 Rapor işlevlerini bir Visual Basic Windows uygulamasına eklemek için en kolay yolu, uygulamanızdaki bir forma ReportViewer denetimi eklemektir. Denetim rapor özellikleri doğrudan uygulamanıza işleme ekler ve bir tümleşik Rapor Tasarımcısı sağlar, böylece, herhangi bir ADO.NET veri nesne verilerden kullanarak raporlar oluşturabilirsiniz. Tam özellikli bir API, denetimin programlı erişim sağlar ve böylece, çalışma zamanı işlevleri yapılandırabilirsiniz raporlar.  
  
 ReportViewer yerleşik rapor işleme ve özellik tek, ücretsiz olarak dağıtılabilen veri denetiminde görüntüleme sağlar. Aşağıdaki rapor işlevlerini gerekiyorsa ReportViewer denetimleri seçin:  
  
-   Rapor, istemci uygulamasına işleme. İşlenen bir raporu denetim tarafından sağlanan bir görünüm alanında görünür.  
  
-   ADO.NET veri tablolarını veri bağlama. Kullanan raporlar oluşturabilirsiniz <xref:System.Data.DataTable> denetimi için sağlanan örnekleri. Ayrıca, doğrudan iş nesnelere bağlayabilirsiniz.  
  
-   Uygulamanıza dahil edebileceğiniz yeniden dağıtılabilen denetimler.  
  
-   Sayfa gezintisi, yazdırma, arama ve dışarı aktarma gibi çalışma zamanı işlevleri biçimlendirir. ReportViewer araç çubuğu bu işlemler için destek sağlar.  
  
 ReportViewer denetimi kullanmak için ondan sürükleyebilirsiniz **veri** bir formda bir Visual Basic Windows uygulamanızı Visual Studio Toolbox bölümü.  
  
### <a name="creating-reports-in-visual-studio-for-reportviewer-controls"></a>ReportViewer denetimleri için Visual Studio'da rapor oluşturma  
 ReportViewer'ı çalışan bir rapor oluşturmak için Ekle bir **rapor** projenize. Visual Studio, istemci rapor tanımı (.rdlc) dosya oluşturur, dosyayı projenize ekler ve Visual Studio çalışma alanında bir tümleşik Rapor Tasarımcısı'nı açar.  
  
 Visual Studio Rapor Tasarımcısı ile tümleşir **veri kaynakları** penceresi. Bir alanı sürüklediğinizde **veri kaynakları** raporu, Rapor Tasarımcısı penceresinde rapor tanım dosyasına veri kaynağıyla ilgili meta verileri kopyalar. Bu meta veriler, ReportViewer denetimi tarafından otomatik olarak veri bağlama kodunu oluşturmak için kullanılır.  
  
 Visual Studio Rapor Tasarımcısı, rapor Önizleme işlevleri içermez. Raporunuzu önizlemek için uygulamayı çalıştırmak ve katıştırılmış raporu önizleyin.  
  
|Temel rapor işlev uygulamanıza eklemek için|  
|---|    
|1.  Bir ReportViewer denetimi **veri** sekmesinde **araç kutusu** formunuza.<br />2.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**. İçinde **Yeni Öğe Ekle** iletişim kutusunda **rapor** simgesi ve tıklatın **Ekle**.<br />     Geliştirme ortamında Rapor Tasarımcısı açılır ve bir rapor (.rdlc) dosyası projenize eklenir.<br />3.  Rapor öğeleri sürükleyin **araç kutusu** üzerinde rapor düzeni ve istediğiniz gibi bunları düzenleyin.<br />4.  Alanlarını sürükleyin **veri kaynakları** rapor düzenini rapor öğelerinde penceresinden.|  
  
## <a name="using-reporting-services-in-visual-basic-applications"></a>Raporlama Hizmetleri Visual Basic uygulamaları kullanma  
 Reporting Services SQL Server ile birlikte sağlanan bir sunucu tabanlı raporlama teknolojisidir. Reporting Services ReportViewer denetimleri bulunmayan ek özellikler içerir. Aşağıdaki özelliklerin herhangi birine ihtiyaç duyuyorsanız Reporting Services'ı seçin:  
  
-   Genişleme dağıtımı ve sunucu tarafı rapor işleme, karmaşık veya uzun süre çalışan raporları ve yüksek hacimli rapor etkinliği için Gelişmiş performans sağlar.  
  
-   Tümleşik veri ve rapor işleme ile özel rapor denetimleri ve Zengin Çıkış biçimleri oluşturma desteği.  
  
-   Zamanlanmış rapor işlemi tam olarak rapor çalıştırıldığında belirtebilirsiniz.  
  
-   E-posta aracılığıyla veya dosya paylaşımı konumlara abone tabanlı rapor dağıtımı.  
  
-   Böylece iş kullanıcıları raporlar oluşturabilir, gerektiği gibi ad hoc raporlama.  
  
-   Çıkış özelleştirilmiş rapor dinamik alıcıların listesi için rota veri tabanlı abonelikler.  
  
-   Veri işleme, rapor teslimi, özel kimlik doğrulama ve rapor oluşturma için özel uzantıları.  
  
 Rapor sunucusu Web hizmeti olarak uygulanır. Uygulama kodunuz, raporlar ve diğer meta veriler erişmek için Web hizmetine çağrı içermelidir. Web hizmeti bir rapor sunucusu örneği tam programlı erişim sağlar.  
  
 Reporting Services Web tabanlı bir raporlama teknoloji olduğundan, varsayılan Görüntüleyicisi işlenen raporları HTML biçiminde gösterir. HTML varsayılan rapor sunu biçimini kullanmak istemiyorsanız uygulamanız için bir özel rapor Görüntüleyici yazma gerekecektir.  
  
### <a name="creating-reports-in-visual-studio-for-reporting-services"></a>Raporlama Hizmetleri için Visual Studio'da rapor oluşturma  
 Bir rapor sunucusunda çalışan raporlar oluşturmak için rapor tanımı (.rdl) dosyaları Visual Studio Business Intelligence Development Studio aracılığıyla SQL Server 2005'te dahil edildiği oluşturabilir.  
  
 Business Intelligence Development Studio, SQL Server bileşenleri için özel proje şablonları ekler. Raporlar oluşturmak için seçebileceğiniz **rapor sunucusu projesi** veya **rapor sunucusu projesi Sihirbazı** şablonları. Veri kaynağı bağlantıları ve veri kaynağı türleri, SQL Server, Oracle, Analysis Services, XML ve SQL Server Integration Services de dahil olmak üzere çeşitli sorgular belirtebilirsiniz. Bir **veri** sekmesinde **Düzen** sekmesinde ve **Önizleme** sekmesi verileri tanımlamak için bir rapor düzenini oluşturup aynı çalışma alanındaki tüm rapor Önizleme sağlar.  
  
 Denetim veya rapor sunucusu için yapı rapor tanımları her iki teknoloji yeniden kullanılabilir.  
  
|Bir rapor sunucusunda çalışan bir rapor oluşturmak için|  
|---|    
|1.  Üzerinde **dosya** menüsünde seçin **yeni**.<br />     **Yeni proje** iletişim kutusu açılır.<br />2.  İçinde **proje türleri** bölmesinde tıklayın **Business Intelligence Projeleri**.<br />3.  Şablonlar bölmesinde seçin **rapor sunucusu projesi** veya **rapor sunucusu projesi Sihirbazı**.|  
  
## <a name="using-reportviewer-controls-and-sql-server-reporting-services-together"></a>ReportViewer denetimleri ve SQL Server Raporlama hizmetlerini birlikte kullanarak  
 ReportViewer denetimleri ve SQL Server 2005 Raporlama Hizmetleri aynı uygulama içinde birlikte kullanılabilir.  
  
-   ReportViewer denetimi uygulamanızda raporları görüntülemek için kullanılan bir Görüntüleyici sunar.  
  
-   Raporlama Hizmetleri raporları sağlar ve bir uzak sunucuda tüm işlemleri gerçekleştirir.  
  
 ReportViewer denetimi, uzak bir Raporlama Hizmetleri rapor sunucusunda depolanan ve işlenen raporları göstermek için yapılandırılabilir. Bu tür bir yapılandırma olarak adlandırılır *uzaktan işleme modu*. Uzaktan işleme modunda, bir uzak rapor sunucusunda depolanan bir rapor denetim ister. Rapor sunucusu, tüm rapor işleme, veri işleme ve rapor işleme gerçekleştirir. Bittiğinde, işlenmiş rapor denetime döndürdü ve görünüm alanında görüntülenen.  
  
 Bir rapor sunucusu desteği ek çalışan raporları biçimleri ver, farklı rapor Parametreleştirme uygulamasına sahipseniz, rapor sunucusu tarafından desteklenir ve rol tabanlı yetkilendirme modeli aracılığıyla erişilen veri kaynağı türlerini kullanma Rapor sunucusu.  
  
 Uzaktan işleme modunu kullanmak için bir sunucu rapor yolu ve URL ReportViewer denetimi yapılandırırken belirtin.
