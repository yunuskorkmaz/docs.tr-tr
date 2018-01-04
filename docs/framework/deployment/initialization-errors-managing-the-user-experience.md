---
title: ".NET Framework Başlatma Hataları: Kullanıcı Deneyimini Yönetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- no framework found experience
- initialization errors [.NET Framework]
- .NET Framework, initialization errors
ms.assetid: 680a7382-957f-4f6e-b178-4e866004a07e
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8679e930b1f12119211a6463289fb37a18692d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="net-framework-initialization-errors-managing-the-user-experience"></a>.NET Framework Başlatma Hataları: Kullanıcı Deneyimini Yönetme
Ortak dil çalışma zamanı (CLR) etkinleştirme sistemi yönetilen uygulama kodu çalıştırmak için kullanılan CLR sürümü belirler. Bazı durumlarda, etkinleştirme sistemine yüklemek için CLR sürümü bulunamıyor mümkün olmayabilir. Bu durum genellikle uygulamanın belirli bir bilgisayarda yüklü değil veya geçersiz bir CLR sürümü gerektirdiğinde oluşur. İstenen sürüm bulunamazsa, CLR etkinleştirme sistemine HRESULT hata kodu işlev veya çağrıldı ve uygulama çalıştıran kullanıcı bir hata iletisi görüntülenebilir arabirimi döndürür. Bu makalede HRESULT kodlarının listesini sağlar ve nasıl görüntülenmesini hata iletisini önlemek açıklanmaktadır.  
  
 CLR CLR etkinleştirme sorunlarında hata ayıklama açıklandığı gibi yardımcı olması için günlüğü altyapı sağlar [nasıl yapılır: CLR etkinleştirme sorunlarında hata ayıklama](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md). Bu altyapı ile karıştırılmamalıdır [derleme günlükleri bağlama](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), tamamen farklı olduğu.  
  
## <a name="clr-activation-hresult-codes"></a>CLR etkinleştirme HRESULT kodu  
 CLR etkinleştirme API'leri bir ana bilgisayara bir etkinleştirme işleminin sonucu bildirmek için HRESULT kodlarını döndürür. CLR konakları her zaman ek işlemleri işlemine devam etmeden önce bu dönüş değerleri danışmalısınız.  
  
-   CLR_E_SHIM_RUNTIMELOAD  
  
-   CLR_E_SHIM_RUNTIMEEXPORT  
  
-   CLR_E_SHIM_INSTALLROOT  
  
-   CLR_E_SHIM_INSTALLCOMP  
  
-   CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND  
  
-   CLR_E_SHIM_SHUTDOWNINPROGRESS  
  
## <a name="ui-for-initialization-errors"></a>Başlatma hataları için kullanıcı Arabirimi  
 CLR etkinleştirme sistemine doğru bir uygulama tarafından istenen çalışma zamanı sürümü yüklenemiyor, hata iletisi bilgisayarlarını uygulamayı çalıştırmak için düzgün yapılandırılmamış ve bunlarla sağlar bildirmek için kullanıcılara görüntülediği bir Bu durumu düzeltmek için fırsat. Aşağıdaki hata iletisini genellikle bu durumda sunulur. Kullanıcı seçebilir **Evet** burada bunlar yükleyebilir doğru .NET Framework sürümü uygulama için Microsoft Web sitesine gidin.  
  
 ![.NET framework başlatma hata iletişim kutusu](../../../docs/framework/deployment/media/initerrordialog.png "InitErrorDialog")  
Başlatma hataları için normal hata iletisi  
  
## <a name="resolving-the-initialization-error"></a>Başlatma hatası çözme  
 Bir geliştirici olarak, .NET Framework başlatma hata iletisi denetleme seçenekleri çeşitli sahip. Örneğin, ileti görüntülenmesini, sonraki bölümde açıklandığı gibi önlemek için bir API bayrağı kullanabilirsiniz. Ancak, uygulamanızın istenen çalışma zamanının yüklenmesini önleyen sorunu çözmek çözümlenmedi. Aksi durumda, uygulamanızın hiç çalışmayabilir veya bazı işlevleri kullanılamayabilir.  
  
 Temel alınan sorunları çözün ve en iyi kullanıcı deneyimi (daha az hata iletileri) sağlamak için şunları öneririz:  
  
-   .NET Framework 3.5 (ve önceki) uygulamaları için: .NET Framework 4 veya 4.5 desteklemek için uygulamanızın yapılandırma (bkz [yönergeleri](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)).  
  
-   .NET Framework 4 uygulamaları için: uygulamanızın kurulumunun bir parçası olarak .NET Framework 4 yeniden dağıtılabilir paketini yükleyin. Bkz: [geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md).  
  
## <a name="controlling-the-error-message"></a>Hata iletisi denetleme  
 İstenen bir .NET Framework sürümü bulunamadı iletişim kurmak için bir hata iletisi görüntüleme yararlı bir hizmet veya kullanıcıların küçük bir sıkıntı getirir olarak görüntülenebilir. Her iki durumda da etkinleştirme API'leri bayrakları geçirerek bu UI kontrol edebilirsiniz.  
  
 [Iclrmetahostpolicy::getrequestedruntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi kabul eden bir [metahost_polıcy_flags](../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) giriş olarak numaralandırma üyesi. CLR istenen sürümü bulunamazsa, bir hata iletisi istemek için METAHOST_POLICY_SHOW_ERROR_DIALOG bayrağı dahil edebilirsiniz. Varsayılan olarak, hata iletisi görüntülenmez. ( [Iclrmetahost::getruntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) yöntemi bu bayrak kabul etmez ve hata iletisini görüntülemek için başka bir yol sağlamaz.)  
  
 Windows sağlayan bir [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkID=255242) işlemi içinde çalıştırılan kod sonucunda gösterilecek hata iletileri isteyip istemediğinizi bildirmek için kullanabileceğiniz işlevi. Hata iletisi görüntülenmesini önlemek için SEM_FAILCRITICALERRORS bayrağını belirtebilirsiniz.  
  
 Ancak, bazı senaryolarda, bir uygulama işlemi tarafından SEM_FAILCRITICALERRORS ayarını geçersiz kılmak önemlidir. Örneğin, yerel bir COM bileşeni CLR'ye barındıran varsa ve SEM_FAILCRITICALERRORS ayarlandığı bir işlemde barındırılan, belirli bir uygulamayı işlem içinde hata iletilerini görüntüleme etkisine bağlı olarak bayrağı geçersiz kılabilir isteyebilirsiniz. Bu durumda, SEM_FAILCRITICALERRORS geçersiz kılmak için aşağıdaki bayraklar birini kullanabilirsiniz:  
  
-   METAHOST_POLICY_IGNORE_ERROR_MODE ile kullanmak [Iclrmetahostpolicy::getrequestedruntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi.  
  
-   RUNTIME_INFO_IGNORE_ERROR_MODE ile kullanmak [Getrequestedruntimeınfo](../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) işlevi.  
  
## <a name="ui-policy-for-clr-provided-hosts"></a>CLR tarafından sağlanan ana bilgisayarlar için kullanıcı Arabirimi İlkesi  
 CLR çeşitli senaryoları için konak kümesini içerir ve gerekli çalışma zamanı sürümü yüklerken sorunlarla karşılaşırsanız, bu konaklar tüm hata iletisi görüntüler. Aşağıdaki tabloda, konakları ve hata iletisi ilkelerini listesini sağlar.  
  
|CLR ana bilgisayarı|Açıklama|Hata ileti İlkesi|Hata iletisi devre dışı bırakılabilir?|  
|--------------|-----------------|--------------------------|------------------------------------|  
|Yönetilen EXE konağı|Başlatır exe yönetilen.|Eksik bir .NET Framework sürüm durumunda gösterilir|Hayır|  
|Yönetilen COM konağı|Yükleri COM bileşenlerini süreç içine yönetilen.|Eksik bir .NET Framework sürüm durumunda gösterilir|Evet, SEM_FAILCRITICALERRORS ayarlayarak bayrak|  
|ClickOnce ana bilgisayar|ClickOnce uygulamaları başlatır.|İle başlayan eksik bir .NET Framework sürüm durumunda gösterilir[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|Hayır|  
|XBAP ana bilgisayar|WPF XBAP uygulamaları başlatır.|İle başlayan eksik bir .NET Framework sürüm durumunda gösterilir[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|Hayır|  
  
## <a name="includewin8includeswin8-mdmd-behavior-and-ui"></a>[!INCLUDE[win8](../../../includes/win8-md.md)]Davranışını ve kullanıcı Arabirimi  
 CLR etkinleştirme sistem üzerinde aynı davranışı ve kullanıcı Arabirimi sağlayan [!INCLUDE[win8](../../../includes/win8-md.md)] diğer Windows işletim sistemi sürümlerinde olduğu gibi CLR 2.0 yükleme sorunları karşılaştığında dışındaki. [!INCLUDE[win8](../../../includes/win8-md.md)]içeren [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], CLR 4.5 kullanır. Ancak, [!INCLUDE[win8](../../../includes/win8-md.md)] .NET Framework 2.0, 3.0 veya 3.5, tüm CLR 2.0 kullanan içermez. Sonuç olarak, CLR 2.0 bağımlı olan uygulamalar çalıştırmayın [!INCLUDE[win8](../../../includes/win8-md.md)] varsayılan olarak. Bunun yerine, kullanıcıların .NET Framework 3.5 yüklemek aşağıdaki iletişim kutusunu görüntüleyin. Kullanıcılar, .NET Framework 3.5 Denetim Masası'nda etkinleştirebilirsiniz. Her iki seçenek makalede açıklanan [Windows 10, Windows 8.1 ve Windows 8 .NET Framework 3.5 yüklemek](../../../docs/framework/install/dotnet-35-windows-10.md).  
  
 ![Windows 8 3.5 Yükle iletişim kutusunu](../../../docs/framework/deployment/media/installdialog.png "installdialog")  
İsteğe bağlı olarak .NET Framework 3.5 yüklemek için istemleri  
  
> [!NOTE]
>  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Kullanıcının bilgisayarda .NET Framework 4 (CLR 4) yerini alır. Bu nedenle, .NET Framework 4 uygulamaları sorunsuz bir şekilde, üzerinde bu iletişim kutusu görüntülenmeden çalıştırmak [!INCLUDE[win8](../../../includes/win8-md.md)].  
  
 .NET Framework 3.5 yüklü olduğunda, kullanıcılar .NET Framework 2.0, 3.0 veya 3.5 bağımlı uygulamaları çalıştırabilir kendi [!INCLUDE[win8](../../../includes/win8-md.md)] bilgisayarlar. Bu uygulamaları açıkça yalnızca .NET Framework 1.0 veya 1.1 çalışacak şekilde yapılandırılmış olması koşuluyla de .NET Framework 1.0 ve 1.1 uygulamalarını çalıştırabilirler. Bkz: [.NET Framework 1.1 geçirme](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).  
  
 İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], CLR etkinleştirme günlüğe kaydetme, ne zaman ve neden başlatma hata iletisi görüntülenir kayıt günlük girişlerini dahil etmek üzere geliştirilmiştir. Daha fazla bilgi için bkz: [nasıl yapılır: CLR etkinleştirme sorunlarında hata ayıklama](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Nasıl yapılır: Bir Uygulamayı .NET Framework 4 veya 4.5'i Destekleyecek Şekilde Yapılandırma](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)  
 [Nasıl Yapılır: CLR Etkinleştirme Sorunlarında Hata Ayıklama](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md)  
 [Windows 10, Windows 8.1 ve Windows 8’de .NET Framework 3.5 Yükleme](../../../docs/framework/install/dotnet-35-windows-10.md)
