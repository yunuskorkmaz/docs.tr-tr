---
title: Uygulama Geliştirme
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: 5ff9f58b72982f79e70b80f60c10828c3b54e5bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185997"
---
# <a name="application-development"></a>Uygulama Geliştirme
<a name="introduction"></a>Windows Sunu Temeli (WPF), aşağıdaki uygulama türlerini geliştirmek için kullanılabilecek bir sunu çerçevesidir:  
  
- Bağımsız Uygulamalar (istemci bilgisayara yüklenen ve istemci bilgisayardan çalıştırılan yürütülebilir derlemeler olarak oluşturulmuş geleneksel stil Windows uygulamaları).  
  
- XAML tarayıcı uygulamaları (XBAPs) (yürütülebilir derlemeler olarak oluşturulan ve Microsoft Internet Explorer veya Mozilla Firefox gibi Web tarayıcıları tarafından barındırılan gezinti sayfalarından oluşan uygulamalar).  
  
- Özel Denetim Kitaplıkları (yeniden kullanılabilir denetimler içeren yürütülemez derlemeler).  
  
- Sınıf Kitaplıkları (yeniden kullanılabilir sınıflar içeren yürütülemeyen derlemeler).  
  
> [!NOTE]
> Bir Windows hizmetinde WPF türlerinin kullanılması nın önerilmesi kuvvetle yapılır. Bu özellikleri bir Windows hizmetinde kullanmaya çalışırsanız, bunlar beklendiği gibi çalışmayabilir.  
  
 Bu uygulama kümesini oluşturmak için WPF bir dizi hizmet uygular. Bu konu, bu hizmetlere genel bir bakış sağlar ve nerede daha fazla bilgi bulabilirsiniz.  

<a name="Application_Management"></a>
## <a name="application-management"></a>Uygulama Yönetimi  
 Çalıştırılabilir WPF uygulamaları genellikle aşağıdakileri içeren bir temel işlevsellik kümesi gerektirir:  
  
- Ortak uygulama altyapısı oluşturma ve yönetme (sistem ve giriş iletileri almak için bir giriş noktası yöntemi ve Windows ileti döngüsü oluşturma dahil).  
  
- Bir uygulamanın kullanım ömrü boyunca izleme ve etkileşimde  
  
- Komut satırı parametrelerini alma ve işleme.  
  
- Uygulama kapsamı özelliklerini [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve kaynaklarını paylaşma.  
  
- İşlenmemiş özel durumları algılama ve işleme.  
  
- Çıkış kodlarını iade ediyor.  
  
- Bağımsız uygulamalarda pencereleri yönetme.  
  
- XAML tarayıcı uygulamalarında (XBAP' lar) gezinmeyi ve navigasyon pencerelerini ve çerçevelerini içeren bağımsız uygulamaları izleme.  
  
 Bu özellikler, *uygulama*tanımı <xref:System.Windows.Application> kullanılarak uygulamalarınıza eklediğiniz sınıf tarafından uygulanır.  
  
 Daha fazla bilgi için [Uygulama Yönetimine Genel Bakış'a](application-management-overview.md)bakın.  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a>WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları  
 WPF, microsoft .NET Framework'deki temel desteği, yürütülemeyen üç tür veri dosyası için destek le birlikte gömülü kaynaklar için genişletir: kaynak, içerik ve veri. Daha fazla bilgi için [Bkz. WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları.](wpf-application-resource-content-and-data-files.md)  
  
 WPF yürütülemeyen veri dosyaları için desteğin önemli bir bileşeni, bunları benzersiz bir URI kullanarak tanımlama ve yükleme yeteneğidir. Daha fazla bilgi için [WPF'deki Paket URI'leri'ne](pack-uris-in-wpf.md)bakın.  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a>Windows ve İletişim Kutuları  
 Kullanıcılar windows üzerinden WPF bağımsız uygulamaları ile etkileşim. Pencerenin amacı, uygulama içeriğini barındırmak ve genellikle kullanıcıların içerikle etkileşimkurmasına olanak tanıyan uygulama işlevselliğini ortaya çıkarmaktır. WPF'de <xref:System.Windows.Window> pencereler, aşağıdakileri destekleyen sınıf tarafından kapsüllenir:  
  
- Pencereleroluşturma ve gösterme.  
  
- Sahip/sahip olunan pencere ilişkilerini kurma.  
  
- Pencere görünümünü yapılandırma (örneğin, boyut, konum, simgeler, başlık çubuğu metni, kenarlık).  
  
- Bir pencerenin ömrü boyunca izleme ve etkileşim.  
  
 Daha fazla bilgi için Bkz. [WPF Windows Genel Bakış.](wpf-windows-overview.md)  
  
 <xref:System.Windows.Window>iletişim kutusu olarak bilinen özel bir pencere türünü oluşturma yeteneğini destekler. Hem modal hem de modeless iletişim kutuları türleri oluşturulabilir.  
  
 Kolaylık sağlamak ve yeniden kullanılabilirlik ve uygulamalar arasında tutarlı bir kullanıcı deneyiminin avantajları için WPF, <xref:Microsoft.Win32.SaveFileDialog>ortak <xref:System.Windows.Controls.PrintDialog>Windows iletişim kutularından üçünü ortaya çıkarır: <xref:Microsoft.Win32.OpenFileDialog>, ve .  
  
 İleti kutusu, kullanıcılara önemli metin bilgilerini göstermek ve basit Evet/Hayır/Tamam/İptal soruları sormak için özel bir iletişim kutusu türüdür. İleti kutuları <xref:System.Windows.MessageBox> oluşturmak ve göstermek için sınıfı kullanırsınız.  
  
 Daha fazla bilgi için İletişim [Kutularına Genel Bakış'a](dialog-boxes-overview.md)bakın.  
  
<a name="Navigation"></a>
## <a name="navigation"></a>Gezinti  
 WPF, sayfaları ( )<xref:System.Windows.Controls.Page>ve köprüleri<xref:System.Windows.Documents.Hyperlink>( ) kullanarak Web tarzı gezinmeyi destekler. Gezinme aşağıdakileri içeren çeşitli şekillerde uygulanabilir:  
  
- Web tarayıcısında barındırılan bağımsız sayfalar.  
  
- Web tarayıcısında barındırılan bir XBAP'da derlenen sayfalar.  
  
- Bağımsız bir uygulamada derlenen ve gezinti penceresi<xref:System.Windows.Navigation.NavigationWindow>tarafından barındırılan sayfalar ( ).  
  
- Bağımsız bir sayfada barındırılabilen bir çerçeve (),<xref:System.Windows.Controls.Frame>veya XBAP veya bağımsız bir uygulama olarak derlenmiş bir sayfa tarafından barındırılan sayfalar.  
  
 Gezinmeyi kolaylaştırmak için WPF aşağıdakileri uygular:  
  
- <xref:System.Windows.Navigation.NavigationService>, uygulama içi gezinmeyi desteklemek için <xref:System.Windows.Controls.Frame>XBAP'lar <xref:System.Windows.Navigation.NavigationWindow>ve XBAP'lar tarafından kullanılan gezinti isteklerini işlemek için paylaşılan gezinti motoru.  
  
- Gezinmeyi başlatmak için gezinme yöntemleri.  
  
- Gezinme ömrünü izlemek ve bunlarla etkileşimde kalmak için gezinme olayları.  
  
- Ayrıca denetlenebilir ve manipüle edilebilir bir günlük kullanarak ileri ve geri navigasyon hatırlama.  
  
 Daha fazla bilgi için [Gezintiye Genel Bakış'a](navigation-overview.md)bakın.  
  
 WPF ayrıca yapılandırılmış gezinti olarak bilinen özel bir gezinti türünü de destekler. Yapılandırılmış gezinti, verileri arama işlevleriyle tutarlı yapılandırılmış ve öngörülebilir bir şekilde döndüren bir veya daha fazla sayfayı çağırmak için kullanılabilir. Bu özellik, Yapılandırılmış <xref:System.Windows.Navigation.PageFunction%601> [Gezintiye Genel Bakış'ta](structured-navigation-overview.md)daha fazla açıklanan sınıfa bağlıdır. <xref:System.Windows.Navigation.PageFunction%601>ayrıca [Navigasyon Topolojileri Genel Bakış](navigation-topologies-overview.md)açıklanan karmaşık navigasyon topolojileri, oluşturulmasını kolaylaştırmak için hizmet vermektedir.  
  
<a name="Hosting"></a>
## <a name="hosting"></a>Barındırma  
 XBAPs Microsoft Internet Explorer veya Firefox'ta barındırılabilir. Her barındırma [modeli, Barındırma](hosting-wpf-applications.md)kapsamında olan kendi değerlendirmeleri ve kısıtlamaları vardır.  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a>Yapılandırma ve Dağıtma  
 Basit WPF uygulamaları komut satırı derleyicileri kullanılarak komut isteminden oluşturulabilse de, Geliştirme ve oluşturma işlemini basitleştiren ek destek sağlamak için WPF Visual Studio ile tümleşir. Daha fazla bilgi için [wpf uygulaması oluşturma](building-a-wpf-application-wpf.md)bilgisine bakın.  
  
 Oluşturduğunuz uygulamatürüne bağlı olarak, aralarından seçim yapabileceğiniz bir veya daha fazla dağıtım seçeneği vardır. Daha fazla bilgi için [wpf uygulaması dağıtma'ya](deploying-a-wpf-application-wpf.md)bakın.  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Uygulama Yönetimine Genel Bakış](application-management-overview.md)|Uygulama ömrü, <xref:System.Windows.Application> windows, uygulama kaynakları ve gezinmeyi yönetme dahil olmak üzere sınıfa genel bir bakış sağlar.|  
|[WPF’de Windows](windows-in-wpf-applications.md)|Uygulamanızda sınıf ve iletişim kutularının nasıl <xref:System.Windows.Window> kullanılacağı nı içeren pencereleri yönetme ayrıntıları sağlar.|  
|[Gezintiye Genel Bakış](navigation-overview.md)|Uygulamanızın sayfaları arasında gezinmeyi yönetmeye genel bir bakış sağlar.|  
|[Barındırma](hosting-wpf-applications.md)|XAML tarayıcı uygulamalarına (XBAP) genel bakış sağlar.|  
|[Derleme ve Dağıtma](building-and-deploying-wpf-applications.md)|WPF uygulamanızı nasıl oluşturup dağıtılacak yapılacağını açıklar.|  
|[Visual Studio’da WPF’ye Giriş](../getting-started/introduction-to-wpf-in-vs.md)|WPF'nin temel özelliklerini açıklar.|  
|[İzlenecek Yol: İlk WPF masaüstü uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|Sayfa gezintisi, düzen, denetimler, resimler, stiller ve bağlama yı kullanarak wpf uygulamasının nasıl oluşturulurulur' u gösteren bir yol için.|
