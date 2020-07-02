---
title: Uygulama Geliştirme
description: Windows Presentation Foundation (WPF) çerçevesini kullanarak çeşitli uygulamalar oluşturmayı öğrenin.
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: ac4227785f2fc398217b3aa8984176844264bbaa
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613741"
---
# <a name="application-development"></a>Uygulama Geliştirme
<a name="introduction"></a>Windows Presentation Foundation (WPF), aşağıdaki uygulama türlerini geliştirmek için kullanılabilen bir sunum çerçevesidir:  
  
- Tek başına uygulamalar (geleneksel stil Windows uygulamaları, istemci bilgisayara yüklenmiş ve bu bilgisayardan çalıştırılan yürütülebilir derlemeler olarak oluşturulur).  
  
- XAML tarayıcı uygulamaları (XBAP 'ler) (yürütülebilir derlemeler olarak oluşturulan ve Microsoft Internet Explorer veya Mozilla Firefox gibi Web tarayıcıları tarafından barındırılan gezinti sayfalarından oluşan uygulamalar).  
  
- Özel denetim kitaplıkları (yeniden kullanılabilir denetimleri içeren yürütülebilir olmayan derlemeler).  
  
- Sınıf kitaplıkları (yeniden kullanılabilir sınıfları içeren yürütülebilir olmayan derlemeler).  
  
> [!NOTE]
> Windows hizmetinde WPF türlerinin kullanılması kesinlikle önerilmez. Bu özellikleri bir Windows hizmetinde kullanmaya çalışırsanız, beklendiği gibi çalışmayabilir.  
  
 Bu uygulama kümesini oluşturmak için WPF bir hizmet ana bilgisayarı uygular. Bu konuda bu hizmetlere genel bir bakış sağlanır ve daha fazla bilgi bulabilirsiniz.  

<a name="Application_Management"></a>
## <a name="application-management"></a>Uygulama Yönetimi  
 Yürütülebilir WPF uygulamaları, genellikle aşağıdakileri içeren bir çekirdek işlev kümesi gerektirir:  
  
- Ortak uygulama altyapısını oluşturma ve yönetme (bir giriş noktası yöntemi ve sistem ve giriş iletilerini almak için bir Windows ileti döngüsü oluşturma dahil).  
  
- Bir uygulamanın yaşam süresi ile izleme ve etkileşim kurma.  
  
- Komut satırı parametrelerini alma ve işleme.  
  
- Uygulama kapsamı özelliklerini ve kaynaklarını paylaşma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .  
  
- İşlenmeyen özel durumları algılama ve işleme.  
  
- Çıkış kodları döndürülüyor.  
  
- Windows 'ı tek başına uygulamalarda yönetme.  
  
- XAML tarayıcı uygulamalarında (XBAP) ve gezinti pencereleri ve çerçevelerle tek başına uygulamalarda gezinmeyi izleme.  
  
 Bu yetenekler <xref:System.Windows.Application> , *uygulama tanımı*kullanarak uygulamalarınıza eklediğiniz sınıfı tarafından uygulanır.  
  
 Daha fazla bilgi için bkz. [uygulama yönetimine genel bakış](application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a>WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları  
 WPF, ekli kaynaklar için Microsoft .NET çerçevesindeki temel desteği üç tür yürütülebilir olmayan veri dosyası desteğiyle genişletir: kaynak, içerik ve veri. Daha fazla bilgi için bkz. [WPF uygulama kaynağı, içerik ve veri dosyaları](wpf-application-resource-content-and-data-files.md).  
  
 WPF yürütülebilir olmayan veri dosyaları desteğinin temel bileşeni, benzersiz bir URI kullanarak bunları belirleyip yükleyebilme olanağıdır. Daha fazla bilgi için bkz. [WPF 'de paket URI 'leri](pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a>Pencereler ve Iletişim kutuları  
 Kullanıcılar Windows aracılığıyla WPF tek başına uygulamalarıyla etkileşime geçer. Bir pencerenin amacı, uygulama içeriğini barındırmak ve genellikle kullanıcıların içerikle etkileşime geçmesini sağlayan uygulama işlevlerini kullanıma sunmasıdır. WPF 'de, Windows şunları destekleyen sınıfı tarafından kapsüllenir <xref:System.Windows.Window> :  
  
- Windows oluşturuluyor ve gösteriliyor.  
  
- Sahip/sahip pencere ilişkileri oluşturuluyor.  
  
- Pencere görünümünü yapılandırma (örneğin, boyut, konum, simgeler, başlık çubuğu metni, kenarlık).  
  
- Bir pencerenin ömrü ile izleme ve etkileşim kurma.  
  
 Daha fazla bilgi için bkz. [WPF Windows 'A genel bakış](wpf-windows-overview.md).  
  
 <xref:System.Windows.Window>iletişim kutusu olarak bilinen özel bir pencere türü oluşturma yeteneğini destekler. Hem kalıcı hem de kalıcı olmayan iletişim kutusu türleri oluşturulabilir.  
  
 WPF, daha kolay ve uygulamalar arasında tutarlı bir kullanıcı deneyimi sağlamak için, yaygın Windows iletişim kutularından üçünü kullanıma sunar: <xref:Microsoft.Win32.OpenFileDialog> , <xref:Microsoft.Win32.SaveFileDialog> ve <xref:System.Windows.Controls.PrintDialog> .  
  
 İleti kutusu, kullanıcılara önemli metin bilgileri göstermek ve basit Evet/Hayır/Tamam/Iptal soruları sormak için özel bir iletişim kutusu türüdür. <xref:System.Windows.MessageBox>İleti kutuları oluşturmak ve göstermek için sınıfını kullanın.  
  
 Daha fazla bilgi için bkz. [Iletişim kutularına genel bakış](dialog-boxes-overview.md).  
  
<a name="Navigation"></a>
## <a name="navigation"></a>Gezinti  
 WPF, Pages ( <xref:System.Windows.Controls.Page> ) ve köprüleri () kullanarak Web stili gezintiyi destekler <xref:System.Windows.Documents.Hyperlink> . Gezinti, aşağıdakiler dahil olmak üzere çeşitli yollarla uygulanabilir:  
  
- Bir Web tarayıcısında barındırılan tek başına sayfalar.  
  
- Bir Web tarayıcısında barındırılan bir XBAP 'ye derlenen sayfalar.  
  
- Tek başına bir uygulamada derlenen ve bir gezinti penceresi () tarafından barındırılan sayfalar <xref:System.Windows.Navigation.NavigationWindow> .  
  
- <xref:System.Windows.Controls.Frame>Tek başına bir sayfada veya BIR XBAP ya da tek başına uygulama olarak derlenen bir sayfada barındırılan bir çerçeve () tarafından barındırılan sayfalar.  
  
 Gezintiyi kolaylaştırmak için WPF aşağıdakileri uygular:  
  
- <xref:System.Windows.Navigation.NavigationService>, <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.NavigationWindow> ve,, ve XBAP tarafından uygulama içi gezintiyi desteklemek için kullanılan gezinti isteklerini işlemeye yönelik paylaşılan gezinti motoru.  
  
- Gezinmeyi başlatmak için gezinti yöntemleri.  
  
- Gezinti ömrünü izlemek ve bunlarla etkileşime geçmek için gezinti olayları.  
  
- Bir günlük kullanarak geri ve ileri gezinmesini hatırlayıp, aynı zamanda incelenebilir ve işlenebilir.  
  
 Daha fazla bilgi için bkz. [gezintiye genel bakış](navigation-overview.md).  
  
 WPF, yapılandırılmış gezinti olarak bilinen özel bir gezinti türünü de destekler. Yapılandırılmış gezinti, çağırma işlevleriyle tutarlı yapılandırılmış ve öngörülebilir bir şekilde veri döndüren bir veya daha fazla sayfayı çağırmak için kullanılabilir. Bu özellik <xref:System.Windows.Navigation.PageFunction%601> , [yapılandırılmış gezintiye genel bakış](structured-navigation-overview.md)bölümünde açıklanan sınıfa bağlıdır. <xref:System.Windows.Navigation.PageFunction%601>Ayrıca, [gezinti topolojilerine genel bakış](navigation-topologies-overview.md)bölümünde açıklanan karmaşık gezinti topolojileri oluşturmayı basitleştirmeye de olanak sağlar.  
  
<a name="Hosting"></a>
## <a name="hosting"></a>Hosting  
 XBAP 'ler, Microsoft Internet Explorer veya Firefox içinde barındırılabilir. Her barındırma modelinin, [barındırma](hosting-wpf-applications.md)kapsamında yer alan kendi konuları ve kısıtlamaları vardır.  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a>Yapılandırma ve Dağıtma  
 Basit WPF uygulamaları komut satırı derleyicileri kullanılarak bir komut isteminden oluşturulabilir, ancak WPF geliştirme ve oluşturma sürecini basitleştirerek ek destek sağlamak için Visual Studio ile tümleşir. Daha fazla bilgi için bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md).  
  
 Oluşturduğunuz uygulamanın türüne bağlı olarak, aralarından seçim yapabileceğiniz bir veya daha fazla dağıtım seçeneği vardır. Daha fazla bilgi için bkz. [WPF uygulaması dağıtma](deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Uygulama Yönetimine Genel Bakış](application-management-overview.md)|<xref:System.Windows.Application>Uygulama ömrü, Windows, uygulama kaynakları ve gezinmeyi yönetme dahil olmak üzere sınıfa genel bir bakış sağlar.|  
|[WPF’de Windows](windows-in-wpf-applications.md)|Uygulamanızda, <xref:System.Windows.Window> sınıfın ve iletişim kutularının kullanımı dahil olmak üzere yönetme hakkında ayrıntılı bilgi sağlar.|  
|[Gezintiye Genel Bakış](navigation-overview.md)|Uygulamanızın sayfaları arasında gezinmeyi yönetmeye ilişkin bir genel bakış sağlar.|  
|[Hosting](hosting-wpf-applications.md)|XAML tarayıcı uygulamalarına (XBAP 'ler) genel bir bakış sağlar.|  
|[Derleme ve Dağıtma](building-and-deploying-wpf-applications.md)|WPF uygulamanızı derleyip dağıtmayı açıklar.|  
|[Visual Studio’da WPF’ye Giriş](../getting-started/introduction-to-wpf-in-vs.md)|WPF 'nin ana özelliklerini açıklar.|  
|[İzlenecek Yol: İlk WPF masaüstü uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|Sayfa gezintisi, düzen, denetimler, görüntüler, stiller ve bağlamayı kullanarak bir WPF uygulamasının nasıl oluşturulduğunu gösteren bir izlenecek yol.|
