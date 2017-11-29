---
title: "Uygulama Geliştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff8f8ab85cda7bdbf66b000a89d8a862e765d561
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="application-development"></a>Uygulama Geliştirme
<a name="introduction"></a>
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]Aşağıdaki uygulama türlerini geliştirmek için kullanılan bir sunu çerçevesidir:  
  
-   Tek başına uygulamaları (Geleneksel stili [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] yükleneceğini ve istemci bilgisayardan çalıştırılan yürütülebilir derlemeleri olarak oluşturulan uygulamalar).  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)](uygulamalar oluşan yürütülebilir derlemeleri olarak oluşturulan ve Web tarayıcıları tarafından gibi barındırılan Gezinti sayfalarının [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] veya Mozilla Firefox).  
  
-   Özel denetim kitaplıkları (yapılamayan derlemeleri yeniden kullanılabilir denetimler içeren).  
  
-   Sınıf kitaplıkları (yeniden kullanılabilir sınıfları içeren yapılamayan derlemeler).  
  
> [!NOTE]
>  Bir Windows hizmetinde WPF türlerini kullanarak kesinlikle önerilmez. Bu özellikler bir Windows hizmetinde kullanmayı denerseniz, bunlar düzenleme beklendiği gibi çalışmayabilir.  
  
 Bu uygulamalar, kümesi oluşturmak için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bir ana bilgisayar Hizmetleri uygular. Bu konu, bu hizmetleri ve daha fazla bilgi nerede genel bakış sağlar.  
  

  
<a name="Application_Management"></a>   
## <a name="application-management"></a>Uygulama Yönetimi  
 Yürütülebilir dosya [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar genellikle şunlardır işlev çekirdek kümesi gerektirir:  
  
-   Oluşturma ve yönetme (bir giriş noktası yöntemi ve sistem ve giriş iletileri almak için bir Windows ileti döngüsü oluşturma dahil) ortak uygulama altyapısı.  
  
-   İzleme ve uygulama yaşam süresi ile etkileşim.  
  
-   Komut satırı parametreleri işlenirken ve alma.  
  
-   Uygulama kapsam özellikleri paylaşımı ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kaynakları.  
  
-   Algılama ve işlenmeyen özel durum işleme.  
  
-   Çıkış kodları döndürme.  
  
-   Bağımsız uygulamalar Windows yönetme.  
  
-   Gezinti bölmesinde İzleme [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]ve tek başına uygulamalarıyla gezinme windows ve çerçeveleri.  
  
 Bu özellikler tarafından uygulanan <xref:System.Windows.Application> kullanarak uygulamalarınızı eklediğiniz sınıfı bir *uygulama tanımı*.  
  
 Daha fazla bilgi için bkz: [uygulama yönetimine genel bakış](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a>WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Çekirdek desteği genişletir [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] yapılamayan veri dosyaları üç tür desteğiyle gömülü kaynaklar için: kaynak, içeriğini ve veri. Daha fazla bilgi için bkz: [WPF Uygulama kaynağı, içerik ve veri dosyalarını](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 WPF yapılamayan veri dosyaları için destek kilit bir bileşeni belirlemek ve benzersiz bir kullanarak bunları yüklemek yeteneğidir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Daha fazla bilgi için bkz: [Pack URI WPF'de](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a>Windows ve iletişim kutuları  
 Kullanıcıların etkileşimde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tek başına uygulamalar windows aracılığıyla. Uygulama içeriğini barındırmak ve genellikle içerik ile etkileşime girmesine izin veren uygulama işlevselliği kullanıma sunmak için bir pencere amacı budur. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], windows tarafından kapsüllenmiş <xref:System.Windows.Window> sınıfı, hangi destekler:  
  
-   Oluşturma ve windows gösterme.  
  
-   Pencere ilişkileri sahibi ve ait oluşturma.  
  
-   Pencere görünümü (örneğin, boyutu, konum, simgeler, başlık çubuğu metni, sınır) yapılandırma.  
  
-   İzleme ve bir pencere etkin kalma süresi ile etkileşim.  
  
 Daha fazla bilgi için bkz: [WPF Windows genel bakış](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).  
  
 <xref:System.Windows.Window>özel türde bir iletişim kutusu olarak bilinen penceresi oluşturma olanağı destekler. Kalıcı ve kalıcı olmayan iletişim kutuları türleri oluşturulabilir.  
  
 Kolaylık sağlamak ve yeniden kullanılırlığı ve uygulamalar arasında tutarlı bir kullanıcı deneyimi avantajları [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] üç genel kullanıma sunan [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] iletişim kutuları: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, ve <xref:System.Windows.Controls.PrintDialog>.  
  
 Bir ileti kutusu iletişim kutusu kullanıcılara önemli metinsel bilgileri göstermek için ve basit Evet/Hayır/Tamam/iptal sorular sormak için özel bir türde değil. Kullandığınız <xref:System.Windows.MessageBox> oluşturmak ve ileti kutuları göstermek için sınıf.  
  
 Daha fazla bilgi için bkz: [iletişim kutularına genel bakış](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Gezinme  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]sayfalarını kullanarak Web stili Gezinti destekler (<xref:System.Windows.Controls.Page>) ve köprüleri (<xref:System.Windows.Documents.Hyperlink>). Gezinti çeşitli şunlardır şekillerde uygulanabilir:  
  
-   Bir Web tarayıcısında barındırılan tek başına sayfa.  
  
-   Sayfaları derlenmiş içine bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bir Web tarayıcısında barındırılan.  
  
-   Sayfaları bir tek başına uygulamasına derlenmiş ve bir gezinti pencere tarafından barındırılan (<xref:System.Windows.Navigation.NavigationWindow>).  
  
-   Bir çerçeve tarafından barındırılan sayfaları (<xref:System.Windows.Controls.Frame>), hangi barındırılması bir tek başına sayfasında veya bir sayfa derlenmiş ya da bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ya da tek başına bir uygulama.  
  
 Gezinti, kolaylaştırmak için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aşağıdaki uygular:  
  
-   <xref:System.Windows.Navigation.NavigationService>, paylaşılan gezinti motoru tarafından kullanılan Gezinti isteklerini işlemek için <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, ve [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] içi uygulama gezinti desteklemek için.  
  
-   Gezinti başlatmak için Gezinti yöntemleri.  
  
-   İzleme ve gezinti ömrü ile etkileşim kurmak için Gezinti olaylar.  
  
-   Geri ve İleri gezinti bir günlüğünü kullanarak hatırlamak, hangi de sahip denetlenir ve yönetilmesine.  
  
 Bilgi için bkz: [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Ayrıca özel türde bir gezinti yapılandırılmış Gezinti bilinen destekler. Yapılandırılmış Gezinti işlevleri çağırma ile tutarlıdır yapılandırılmış ve tahmin edilebilir şekilde dönüş verileri bir veya daha fazla sayfa çağırmak için kullanılabilir. Bu özellik bağımlı <xref:System.Windows.Navigation.PageFunction%601> daha ayrıntılı açıklanmıştır sınıfı [yapılandırılmış Gezinti genel bakış](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md). <xref:System.Windows.Navigation.PageFunction%601>Ayrıca açıklanan karmaşık gezinti topolojileri oluşturma işlemini basitleştirmek için hizmet [gezinti topolojilerine genel bakış](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md).  
  
<a name="Hosting"></a>   
## <a name="hosting"></a>Barındırma  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]içinde barındırılan [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] ya da Firefox. Her bir barındırma modeli hakkında önemli noktalar ve ele alınmaktadır kısıtlamalar kendi ayarlanmış [barındırma](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a>Yapılandırma ve Dağıtma  
 Basit rağmen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları komut satırı derleyicileri kullanarak bir komut isteminden oluşturulabilen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ile tümleştirilir [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] geliştirme ve yapı işlemi Basitleştirilmiş ek destek sağlamak için. Daha fazla bilgi için bkz: [WPF uygulaması oluşturma](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
 Oluşturduğunuz uygulama türüne bağlı olarak, içinden seçim yapabileceğiniz bir veya daha fazla dağıtım seçenekleri vardır. Daha fazla bilgi için bkz: [WPF uygulaması dağıtma](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Uygulama yönetimine genel bakış](../../../../docs/framework/wpf/app-development/application-management-overview.md)|Genel bir bakış sağlar <xref:System.Windows.Application> uygulama yaşam süresi, windows, uygulama kaynakları ve gezinti yönetme de dahil olmak üzere sınıfı.|  
|[WPF içinde pencereler](../../../../docs/framework/wpf/app-development/windows-in-wpf-applications.md)|Windows nasıl kullanılacağı dahil olmak üzere, uygulamanızda yönetme ayrıntıları sağlar <xref:System.Windows.Window> sınıfı ve iletişim kutuları.|  
|[Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md)|Uygulamanızın sayfaları arasında gezinme yönetimine genel bir bakış sağlar.|  
|[Barındırma](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md)|Genel bir bakış sağlar [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].|  
|[Derleme ve dağıtma](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md)|Derleme ve WPF uygulamanızı dağıtmak açıklar.|  
|[Visual Studio 2015'te WPF'ye giriş](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)|WPF ana özelliklerini açıklar.|  
|[İzlenecek yol: İlk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|Gösterir uygulamasını kullanarak bir WPF oluşturmak için sayfa nasıl gezinme, düzeni, denetimleri, görüntüler, stil bir gözden geçirme ve bağlama.|
