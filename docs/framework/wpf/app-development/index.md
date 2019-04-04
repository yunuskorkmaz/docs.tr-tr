---
title: Uygulama Geliştirme
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: 979a5324fe9cb6c3469660e061d5df7f312ef2c4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365141"
---
# <a name="application-development"></a>Uygulama Geliştirme
<a name="introduction"></a> Windows Presentation Foundation (WPF), aşağıdaki türde uygulamaları geliştirmek için kullanılan bir sunu çerçevesidir:  
  
-   Tek başına uygulamalar (Geleneksel bir stil [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] için yüklü olan ve istemci bilgisayardan çalıştırma yürütülebilir derlemelere olarak derlenen uygulamalar).  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] (uygulama yürütülebilir derlemelere oluşturulur ve Web tarayıcıları tarafından gibi barındırılan Gezinti sayfalarının oluşan [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] veya Mozilla Firefox).  
  
-   Özel denetim kitaplığı (yeniden kullanılabilir denetimler içeren yürütülebilir olmayan derlemeler).  
  
-   Sınıf kitaplıkları (yeniden kullanılabilir sınıfları içeren yürütülebilir olmayan derlemeler).  
  
> [!NOTE]
>  WPF türlerini kullanarak bir Windows hizmetinde kesinlikle önerilmez. Bir Windows hizmetinde bu özellikleri kullanmaya çalışırsanız, bunlar düzenleme beklendiği gibi çalışmayabilir.  
  
 Bu uygulama, kümenizi oluşturmak için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bir ana bilgisayar Hizmetleri uygular. Bu konu, bu hizmetleri ve daha fazla bilgi nereye genel bir bakış sağlar.  
  

  
<a name="Application_Management"></a>   
## <a name="application-management"></a>Uygulama Yönetimi  
 Yürütülebilir dosya [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar genellikle aşağıdakileri içeren işlev bir çekirdek kümesi gerektirir:  
  
-   Oluşturma ve ortak uygulama altyapısı (oluşturma, bir giriş noktası yönteminin ve sistem ve giriş iletileri almak için Windows ileti döngüsü gibi) yönetme.  
  
-   İzleme ve uygulama yaşam süresi ile etkileşim kurma.  
  
-   Alma ve işleme komut satırı parametreleri.  
  
-   Uygulama kapsamı özelliklerini paylaşma ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kaynakları.  
  
-   Algılama ve işlenmeyen özel durumları işleme.  
  
-   Çıkış kodları döndürme.  
  
-   Tek başına uygulamalar Windows yönetme.  
  
-   Gezinti bölmesinde İzleme [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]ve gezinti windows ve çerçeveleri ile tek başına uygulamalar.  
  
 Bu özellikler tarafından uygulanan <xref:System.Windows.Application> kullanarak uygulamalarınıza ekleyin sınıfı bir *uygulama tanımı*.  
  
 Daha fazla bilgi için [uygulama yönetimine genel bakış](application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a>WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gömülü kaynaklar için Microsoft .NET Framework core desteği yürütülebilir olmayan veri dosyalarının üç tür için destekle genişletir: kaynak, içerik ve veri. Daha fazla bilgi için [WPF Uygulama kaynağı, içerik ve veri dosyalarını](wpf-application-resource-content-and-data-files.md).  
  
 WPF yürütülebilir olmayan veri dosyaları için desteği için temel bileşen tanımlamak ve bunları kullanarak benzersiz bir yükleme yeteneğidir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Daha fazla bilgi için [paketi URI ' WPF'de](pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a>Windows ve iletişim kutuları  
 Kullanıcılar etkileşimde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tek başına uygulamalar windows aracılığıyla. Bir pencere amacı, uygulama içeriğini barındırmak ve genellikle içeriklerle etkileşim olanağı tanıyan uygulama işlevselliği kullanıma sunma oluşturmaktır. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], windows tarafından alınır <xref:System.Windows.Window> sınıfı, hangi destekler:  
  
-   Oluşturma ve windows gösteriliyor.  
  
-   Sahibi ve sahip penceresi ilişkileri oluşturma.  
  
-   Pencere görünümü (örneğin, boyut, konum, simgeler, başlık çubuğu metni, kenarlık) yapılandırma.  
  
-   İzleme ve bir pencere ömrü ile etkileşim kurma.  
  
 Daha fazla bilgi için [WPF Windows genel bakış](wpf-windows-overview.md).  
  
 <xref:System.Windows.Window> bir iletişim kutusu olarak biliniyordu özel bir tür oluşturma özelliğini destekler. Kalıcı ve kalıcı olmayan iletişim kutuları tür oluşturulabilir.  
  
 Kolaylık sağlamak ve ölçeklendirilebileceği ve uygulamalar arasında tutarlı bir kullanıcı deneyimi için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] üç Windows ortak iletişim kutularının kullanıma sunar: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, ve <xref:System.Windows.Controls.PrintDialog>.  
  
 Bir ileti kutusu önemli metin tabanlı bilgiler kullanıcılara gösterilmesi ve basit Evet/Hayır/Tamam/iptal sorular sormak için iletişim kutusunun özel bir türdür. Kullandığınız <xref:System.Windows.MessageBox> sınıfı oluşturun ve ileti kutuları göstermek için.  
  
 Daha fazla bilgi için [iletişim kutularına genel bakış](dialog-boxes-overview.md).  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Gezinti  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sayfaları kullanarak Web stili gezintiyi destekler (<xref:System.Windows.Controls.Page>) ve köprüleri (<xref:System.Windows.Documents.Hyperlink>). Gezinti bir çeşitli şekillerde aşağıdakileri içeren uygulanabilir:  
  
-   Bir Web tarayıcısında barındırılan tek başına sayfa.  
  
-   Sayfaların derlenmiş içine bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bir Web tarayıcısında barındırılır.  
  
-   Sayfaları bir tek başına uygulamasına derlenmiş ve gezinti pencere tarafından barındırılan (<xref:System.Windows.Navigation.NavigationWindow>).  
  
-   Çerçeve tarafından barındırılan sayfaları (<xref:System.Windows.Controls.Frame>) barındırılması bir tek başına sayfasında veya bir sayfa ya derlenmiş bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ya da tek başına bir uygulama.  
  
 Gezinti, kolaylaştırmak için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aşağıdaki uygular:  
  
-   <xref:System.Windows.Navigation.NavigationService>, paylaşılan Gezinti altyapısı tarafından kullanılan Gezinti isteklerini işlemek için <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] içi uygulama gezinti desteklemek için.  
  
-   Gezinti başlatmak için Gezinti yöntemleri.  
  
-   İzleme ve gezinti ömrü ile etkileşim kurmak için Gezinti olayları'nı tıklatın.  
  
-   Geri ve İleri gezinme bir günlüğünü kullanarak hatırlamak, hangi ayrıca inceledi ve yönetilmesine.  
  
 Bilgi için [gezintiye genel bakış](navigation-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Ayrıca, özel yapılandırılmış gezintiye bilinen Gezinti türünü destekler. Yapılandırılmış gezintiye işlevlerini çağırma ile tutarlıdır yapılandırılmış ve öngörülebilir bir şekilde veri döndüren bir veya daha fazla sayfa çağırmak için kullanılabilir. Bu özellik bağlıdır <xref:System.Windows.Navigation.PageFunction%601> daha ayrıntılı açıklanmıştır sınıfı [yapılandırılmış gezintiye genel bakış](structured-navigation-overview.md). <xref:System.Windows.Navigation.PageFunction%601> Ayrıca anlatılan karmaşık gezinti topolojileri oluşturulmasını kolaylaştırmak için hizmet [gezinti topolojilerine genel bakış](navigation-topologies-overview.md).  
  
<a name="Hosting"></a>   
## <a name="hosting"></a>Barındırma  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] içinde barındırılan [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] ya da Firefox. Her bir barındırma modeli ele alınmaktadır kısıtlamaları ile ilgili önemli noktalar ve kendi ayarlanmış [barındırma](hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a>Yapılandırma ve Dağıtma  
 Basit olsa da [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] komut satırı derleyicilerini kullanarak bir komut isteminden uygulamaları derlenebilir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ile tümleşir [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] geliştirme ve derleme işlemi Basitleştirilmiş ek destek sağlamak için. Daha fazla bilgi için [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md).  
  
 Oluşturduğunuz uygulama türüne bağlı olarak, aralarından seçim yapabileceğiniz bir veya daha fazla dağıtım seçenekleri vardır. Daha fazla bilgi için [bir WPF uygulamasını dağıtma](deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Uygulama Yönetimine Genel Bakış](application-management-overview.md)|Genel bir bakış sağlar <xref:System.Windows.Application> uygulama ömrü, windows, uygulama kaynakları ve gezinti da dahil olmak üzere sınıfı.|  
|[WPF’de Windows](windows-in-wpf-applications.md)|Uygulamanızda nasıl kullanılacağını dahil olmak üzere windows yönetme ayrıntıları sağlar <xref:System.Windows.Window> sınıfı ve iletişim kutuları.|  
|[Gezintiye Genel Bakış](navigation-overview.md)|Uygulamanızın sayfalar arasında gezinti yönetmeye genel bakış sağlar.|  
|[Barındırma](hosting-wpf-applications.md)|Genel bir bakış sağlar [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].|  
|[Derleme ve Dağıtma](building-and-deploying-wpf-applications.md)|WPF uygulaması derleme ve dağıtma işlemini açıklamaktadır.|  
|[Visual Studio’da WPF’ye Giriş](../getting-started/introduction-to-wpf-in-vs.md)|WPF ana özelliklerini açıklar.|  
|[İzlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|Uygulamayı kullanarak bir WPF oluşturmak için sayfa gezinti, düzen, denetimler, resim, nasıl gösterir stilleri bir kılavuz ve bağlama.|
