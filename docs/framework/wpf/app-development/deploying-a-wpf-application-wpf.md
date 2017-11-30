---
title: "Bir WPF Uygulamasını Dağıtma (WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 860549d444bcef3a25af753923955b2e3e1a3677
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-a-wpf-application-wpf"></a>Bir WPF Uygulamasını Dağıtma (WPF)
Sonra [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] uygulamaları yerleşiktir, dağıtılması gerekiyor. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]ve [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] birkaç dağıtım teknolojilerini içerir. Dağıtmak için kullanılan dağıtım teknolojisi bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama uygulama türüne bağlıdır. Bu konu, her dağıtım teknolojisi kısa bir genel bakış ve her dağıtım gereksinimleri ile birlikte nasıl kullanıldıkları sağlar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama türü.  
  
   
<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>Dağıtım teknolojileri  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]ve [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] dahil olmak üzere çeşitli dağıtım teknolojileri şunları içerir:  
  
-   XCopy dağıtımı.  
  
-   [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]dağıtımı.  
  
-   [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)]dağıtımı.  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>XCopy dağıtımı  
 XCopy dağıtımı dosyaları bir konumdan diğerine kopyalamak için XCopy komut satırı programı kullanımını gösterir. XCopy dağıtımı aşağıdaki durumlarda uygundur:  
  
-   Uygulama birbirinden bağımsızdır. Çalıştıran istemci güncelleştirmek gerekmez.  
  
-   Uygulama dosyaları taşınması gerekir bir konumdan diğerine gibi bir yapı konumundan (yerel disk [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] dosya paylaşımı vb.) için bir yayımlama konumu (Web sitesi [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] dosya paylaşımı vb.).  
  
-   Uygulama kabuk tümleştirmesi (Başlat menüsü kısayolu, Masaüstü simgesi vb.) gerektirmez.  
  
 XCopy basit dağıtım senaryoları için uygun olsa da, daha karmaşık dağıtım yetenekleri gerekli olduğunda sınırlıdır. Özellikle, genellikle XCopy kullanarak oluşturmak, yürütme ve dağıtım sağlam bir şekilde yönetmek için komutlar sürdürmek için ek yük doğurur. Ayrıca, XCopy sürüm oluşturma, kaldırma veya geri alma desteklemiyor.  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Windows Installer  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]kolayca istemcilere dağıtılan ve kendi başına yürütülebilen paketlenmiş uygulamalar sağlar. Ayrıca, [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] ile yüklenen [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ve Masaüstü, Başlat menüsüne ve programlar Denetim Masası ile tümleştirme sağlar.  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]Yükleme ve kaldırma uygulamalarının kolaylaştırır, ancak yüklü uygulamaların sürüm oluşturma açısından güncel kalmasını sağlamaya yönelik olanakları sağlamaz.  
  
 Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)], bkz: [Windows Installer dağıtımı](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce dağıtımı  
 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)]Web olmayan uygulamalar için Web stili uygulama dağıtımı sağlar. Uygulamalar için yayımlanan ve Web veya dosya sunucusundan dağıtılır. Ancak [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] tam desteklemiyor istemci aralığını özellikleri [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]-yüklü uygulamalar yapmak için aşağıdakileri içeren bir alt kümesini destekler:  
  
-   Başlat menüsü ve programlar Denetim Masası ile tümleştirme.  
  
-   Sürüm oluşturma, geri alma ve kaldırma.  
  
-   Her zaman bir uygulama dağıtım konumdan başlatan çevrimiçi yükleme modunu.  
  
-   Yeni sürümler yayımlandığında otomatik güncelleştirme.  
  
-   Dosya uzantıları kaydı.  
  
 Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)], bkz: [ClickOnce güvenliği ve dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>WPF Uygulamalarını Dağıtma  
 Dağıtım seçenekleri bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama uygulama türüne bağlıdır. Bir dağıtım açısından [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] üç önemli uygulama türü vardır:  
  
-   Bağımsız uygulamalar.  
  
-   Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulamalar.  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>Tek başına uygulamaları dağıtma  
 Bağımsız uygulamalar kullanılarak dağıtılır [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] veya [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Her iki durumda da, tek başına uygulamaları çalıştırmak için tam güven gerektirir. Tam güven olduğundan otomatik olarak verilen kullanılarak dağıtılan bağımsız uygulamalar için [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Kullanılarak dağıtılan uygulamalara [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] otomatik olarak tam güven verilmez. Bunun yerine, [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] güvenlik iletişim bağımsız uygulama yüklenmeden önce kullanıcıların kabul etmesi gerekir uyarı görüntüler. Onayladığınızda, tek başına uygulama yüklenir ve tam güven verilir. Aksi durumda, tek başına uygulama yüklü değil.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>Yalnızca biçimlendirme XAML uygulamaları dağıtma  
 Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları genellikle yayımlanır Web sunucularına gibi [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] sayfaları ve kullanılarak görüntülenebilir [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]. Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları Internet bölgesi izin kümesi tarafından tanımlanan bir kısıtlama olmadan bir kısmi güven güvenlik sandbox içinde çalıştırın. Bu bir eşdeğer güvenlik sandbox sağlar [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]-tabanlı Web uygulamaları.  
  
 İçin güvenlik hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar, bkz [güvenlik](../../../../docs/framework/wpf/security-wpf.md).  
  
 Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları yüklenebilir yerel dosya sistemine XCopy kullanarak veya [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Bu sayfaları kullanılarak görüntülenebilir [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] veya [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] Explorer.  
  
 XAML hakkında daha fazla bilgi için bkz: [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>XAML tarayıcısı uygulamaları dağıtma  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]Dağıtılacak aşağıdaki üç dosyayı gerektiren derlenmiş uygulamalar şunlardır:  
  
-   *ApplicationName*.exe: çalıştırılabilir derleme uygulama dosyası.  
  
-   *ApplicationName*.xbap: dağıtım bildirimi.  
  
-   *ApplicationName*. exe.manifest: uygulama bildirimi.  
  
> [!NOTE]
>  Dağıtım ve uygulama bildirimleri hakkında daha fazla bilgi için bkz: [WPF uygulaması oluşturma](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
 Bu dosyalar üretilen olduğunda bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] yerleşik olarak bulunur. Daha fazla bilgi için bkz: [nasıl yapılır: yeni bir WPF tarayıcı uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/72ef4d90-e163-42a1-8df0-ea7ccfd1901f). Yalnızca biçimlendirme gibi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] genellikle bir Web sunucusuna yayımlanır ve kullanarak görüntülenebilir [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)].  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]dağıtım tekniklerden herhangi birini kullanarak istemcilere dağıtılabilir. Ancak, [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] önerilir çünkü aşağıdaki yetenekleri sağlar:  
  
1.  Yeni bir sürümü yayımlandığında otomatik güncelleştirmeler.  
  
2.  İçin ayrıcalıklar yükseltme [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] tam güven ile çalışan.  
  
 Varsayılan olarak, uygulama dosyalarını .deploy uzantısı ile ClickOnce yayımlar. Bu bir sorun olabilir, ancak devre dışı bırakılabilir. Daha fazla bilgi için bkz: [sunucu ve istemci yapılandırma sorunları ClickOnce Dağıtımları içinde](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Dağıtma hakkında daha fazla bilgi için [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)], bkz: [WPF XAML tarayıcısı uygulamaları genel bakış](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>.NET Framework2ü yükleme  
 Çalıştırmak için bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] istemcide yüklü olmalıdır. [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]otomatik olarak istemciler ile yüklü olup olmadığını algılar [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] zaman [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tarayıcıda barındırılan uygulamalar görüntülendiğinde. Varsa [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] yüklü değil, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] kullanıcıların yüklemesini ister.  
  
 Algılamak için olup olmadığını [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] yüklü olduğu [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] geri dönüş olarak kayıtlı bir önyükleyici uygulama içerir [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] şu uzantılara sahip içerik dosyaları için işleyici: .xaml, .xps, .xbap ve .application. Bu dosya türlerini giderseniz ve [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] yüklü değil istemci üzerinde önyükleyici uygulama yüklemek için izin ister. İzni, tipleri sağlanmamışsa [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] veya uygulama yüklenir.  
  
 İzin verilirse [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] indirir ve yükler [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] kullanarak [!INCLUDE[TLA#tla_bits](../../../../includes/tlasharptla-bits-md.md)]. Başarılı yüklemesinden sonra [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)], ilk olarak istenen dosyanın yeni bir tarayıcı penceresinde açılır.  
  
 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]otomatik algılamayı edinilebilir [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxpsp2](../../../../includes/tlasharptla-winxpsp2-md.md)], ve [!INCLUDE[TLA#tla_winnetsvrfamsp1](../../../../includes/tlasharptla-winnetsvrfamsp1-md.md)] sahip istemciler [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] veya sonraki bir sürümü yüklü.  
  
 Daha fazla bilgi için bkz: [.NET Framework ve uygulamaları dağıtma](../../../../docs/framework/deployment/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF uygulaması oluşturma](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Güvenlik](../../../../docs/framework/wpf/security-wpf.md)
