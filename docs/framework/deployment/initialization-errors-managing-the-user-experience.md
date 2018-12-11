---
title: '.NET framework başlatma hataları: Kullanıcı deneyimini yönetme'
ms.date: 03/30/2017
helpviewer_keywords:
- no framework found experience
- initialization errors [.NET Framework]
- .NET Framework, initialization errors
ms.assetid: 680a7382-957f-4f6e-b178-4e866004a07e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21dd9926684f51412384235d7b3af1aac280957a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155177"
---
# <a name="net-framework-initialization-errors-managing-the-user-experience"></a>.NET framework başlatma hataları: Kullanıcı deneyimini yönetme
Ortak dil çalışma zamanı (CLR) etkinleştirme sistemi yönetilen uygulama kodu çalıştırmak için kullanılan CLR sürümünü belirler. Bazı durumlarda, etkinleştirme sistemine yüklenecek CLR sürümünü bulmak mümkün olmayabilir. Bu durum, genellikle uygulamanın geçersiz veya belirli bir bilgisayarda yüklü olan bir CLR sürümü gerektiren oluşur. İstenen sürüm bulunmazsa, CLR etkinleştirme sistemine HRESULT hata kodu işlev veya çağrıldı ve uygulamayı çalıştıran kullanıcıya bir hata iletisi görüntülenebilir arabirimi döndürür. Bu makale, HRESULT kodlarının listesini sağlar ve görüntülenmesini hata iletisini nasıl engelleyebilir açıklar.  
  
 CLR açıklandığı CLR etkinleştirme sorunlarında hata ayıklamanıza yardımcı olmak için günlük kaydı altyapısı sağlar [nasıl yapılır: CLR etkinleştirme sorunlarında hata ayıklama](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md). Bu altyapı ile karıştırılmamalıdır [derleme bağlama günlüklerini](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), tamamen farklı olan.  
  
## <a name="clr-activation-hresult-codes"></a>CLR etkinleştirme HRESULT kodları  
 CLR etkinleştirme API'leri bir konağa bir etkinleştirme işleminin sonucu bildirmek için kodları HRESULT döndürür. CLR konakları, her zaman ek işlemler devam etmeden önce bu dönüş değerleri başvurmanız gerekir.  
  
-   CLR_E_SHIM_RUNTIMELOAD  
  
-   CLR_E_SHIM_RUNTIMEEXPORT  
  
-   CLR_E_SHIM_INSTALLROOT  
  
-   CLR_E_SHIM_INSTALLCOMP  
  
-   CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND  
  
-   CLR_E_SHIM_SHUTDOWNINPROGRESS  
  
## <a name="ui-for-initialization-errors"></a>Başlatma hataları için kullanıcı Arabirimi  
 CLR etkinleştirme sistemine doğru bir uygulama için gereken çalışma zamanı sürümü yüklenemiyor, hata iletisi bilgisayarlarının uygulamayı çalıştırmak için düzgün yapılandırılmamış ve bunları sağlar bildirmek amacıyla kullanıcılara görüntüler bir Bu durumu ortadan kaldırmak için bir fırsat. Aşağıdaki hata iletisini, bu durumda genellikle sunulur. Kullanıcı seçebilir **Evet** nerede bunlar yükleyebilir doğru .NET Framework sürümünü uygulama için bir Microsoft Web sitesine gidin.  
  
 ![.NET framework başlatma hatası iletişim kutusu](../../../docs/framework/deployment/media/initerrordialog.png "InitErrorDialog")  
Başlatma hataları için tipik bir hata iletisi  
  
## <a name="resolving-the-initialization-error"></a>Başlatma hatası çözümleme  
 Bir geliştirici olarak, .NET Framework başlatma hatası iletisi denetleme seçenekleri çeşitli sahip. Örneğin, bir API bayrağı iletinin görüntülenmesini, sonraki bölümde açıklandığı gibi önlemek için kullanabilirsiniz. Ancak, yine de uygulamanızı istenen çalışma zamanının yüklenmesini önleyen sorunu çözmek zorunda. Aksi halde, uygulamanız hiç çalışmayabilir veya bazı işlevler kullanılamayabilir.  
  
 Temel alınan sorunları çözün ve en iyi kullanıcı deneyimi (daha az hata iletileri) sağlamak için şunları öneririz:  
  
-   .NET Framework 3.5 (ve önceki) uygulamaları için: Uygulamanızı .NET Framework 4 veya 4.5 destekleyecek şekilde yapılandırma (bkz [yönergeleri](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)).  
  
-   .NET Framework 4 uygulamaları için: .NET Framework 4 yeniden dağıtılabilir paket, uygulamanızın kurulumunun bir parçası olarak yükleyin. Bkz: [geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md).  
  
## <a name="controlling-the-error-message"></a>Hata iletisi denetleme  
 İstenen bir .NET Framework sürümü bulunamadı iletişim kurmak için bir hata iletisini gösteren yararlı bir hizmet veya kullanıcıların küçük bir sıkıntı getirir olarak görüntülenebilir. Her iki durumda da etkinleştirme API'leri bayrakları geçirerek bu UI kontrol edebilirsiniz.  
  
 [Iclrmetahostpolicy::getrequestedruntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi kabul bir [metahost_polıcy_flags](../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) giriş olarak sabit listesi üyesi. İstenen CLR sürümünü bulunamazsa, bir hata iletisi istemek için METAHOST_POLICY_SHOW_ERROR_DIALOG bayrağı dahil edebilirsiniz. Varsayılan olarak, hata iletisi görüntülenmez. ( [Iclrmetahost::getruntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) yöntemi bu bayrağı kabul etmez ve hata iletisini görüntülemek için diğer bir yöntem sağlamaz.)  
  
 Windows sağlayan bir [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkID=255242) hata iletileri, işleminizde çalışan kodun sonucu olarak gösterilmesini isteyip istemediğinizi bildirmek için kullanabileceğiniz işlevi. Hata iletisinin görüntülenmesini engellemek için SEM_FAILCRITICALERRORS bayrağı belirtebilirsiniz.  
  
 Ancak, bazı senaryolarda, bir uygulama işlemi tarafından SEM_FAILCRITICALERRORS ayarı geçersiz kılmak önemlidir. Örneğin, yerel bir COM bileşeni barındıran CLR'e sahipseniz ve SEM_FAILCRITICALERRORS ayarlandığı bir işlemde barındırılan belirli uygulama işlem içinde hata iletilerini görüntüleme etkisine bağlı olarak bayrağı geçersiz kılmak isteyebilirsiniz. Bu durumda, SEM_FAILCRITICALERRORS geçersiz kılmak için aşağıdaki bayraklarından birini kullanabilirsiniz:  
  
-   İle METAHOST_POLICY_IGNORE_ERROR_MODE kullanın [Iclrmetahostpolicy::getrequestedruntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi.  
  
-   İle RUNTIME_INFO_IGNORE_ERROR_MODE kullanın [Getrequestedruntimeınfo](../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) işlevi.  
  
## <a name="ui-policy-for-clr-provided-hosts"></a>CLR tarafından sağlanan ana bilgisayar için kullanıcı Arabirimi İlkesi  
 CLR çeşitli senaryoları için konak kümesini içerir ve bunlar gerekli çalışma zamanı sürümünü yüklerken sorunla karşılaştığınızda, tüm bu konaklar bir hata iletisi görüntüler. Aşağıdaki tabloda, konaklar ve hata iletisi ilkelerini listesini sağlar.  
  
|CLR konak|Açıklama|Hata ileti İlkesi|Hata iletisi devre dışı bırakılabilir mi?|  
|--------------|-----------------|--------------------------|------------------------------------|  
|Yönetilen EXE konağı|Başlatılan exe yönetilen.|Eksik bir .NET Framework sürümünü durumunda gösterilir|Hayır|  
|Yönetilen COM konağı|Yükleri COM bileşenlerini bir işleme yönetilen.|Eksik bir .NET Framework sürümünü durumunda gösterilir|Evet, SEM_FAILCRITICALERRORS ayarlayarak bayrak|  
|ClickOnce konak|ClickOnce uygulamaları başlatır.|Eksik bir .NET Framework sürümü ile başlayarak, durumunda gösterilir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|Hayır|  
|XBAP konak|WPF XBAP uygulamaları başlatır.|Eksik bir .NET Framework sürümü ile başlayarak, durumunda gösterilir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|Hayır|  
  
## <a name="includewin8includeswin8-mdmd-behavior-and-ui"></a>[!INCLUDE[win8](../../../includes/win8-md.md)] Davranışını ve kullanıcı Arabirimi  
 CLR etkinleştirme sistemine üzerinde aynı davranışı ve kullanıcı Arabirimi sağlayan [!INCLUDE[win8](../../../includes/win8-md.md)] diğer Windows işletim sistemi sürümlerinde olduğu gibi CLR 2.0 yüklerken sorun bulduğu durumlar hariç. [!INCLUDE[win8](../../../includes/win8-md.md)] içerir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], CLR 4.5 kullanır. Ancak, [!INCLUDE[win8](../../../includes/win8-md.md)] .NET Framework 2.0, 3.0 veya 3.5 CLR 2.0 kullanan tüm hangi içermez. Sonuç olarak, CLR 2.0 bağlı uygulamalar çalıştırmayın [!INCLUDE[win8](../../../includes/win8-md.md)] varsayılan olarak. Bunun yerine, .NET Framework 3.5 yüklemek kullanıcıları etkinleştirmek için aşağıdaki iletişim kutusunu görüntüler. Kullanıcılar, Denetim Masası'nda .NET Framework 3.5 de etkinleştirebilirsiniz. İki seçenek de makalesinde açıklanan [Windows 10, Windows 8.1 ve Windows 8 üzerinde .NET Framework 3.5 yükleme](../../../docs/framework/install/dotnet-35-windows-10.md).  
  
 ![Windows 8 yükle 3.5 için iletişim kutusu](../../../docs/framework/deployment/media/installdialog.png "installdialog")  
İsteğe bağlı olarak .NET Framework 3.5 yükleme istemi  
  
> [!NOTE]
>  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Kullanıcının bilgisayarında .NET Framework 4 (CLR 4) değiştirir. Bu nedenle, .NET Framework 4 uygulamalarını sorunsuz bir şekilde, bu iletişim kutusunu görüntüleme olmadan çalıştırmak [!INCLUDE[win8](../../../includes/win8-md.md)].  
  
 Kullanıcılar, .NET Framework 3.5 yüklendiğinde .NET Framework 2.0, 3.0 veya 3.5 kullanan uygulamalar çalıştırabilir, [!INCLUDE[win8](../../../includes/win8-md.md)] bilgisayarlar. Söz konusu uygulamaların açıkça yalnızca .NET Framework 1.0 veya 1.1 üzerinde çalıştırmak için yapılandırılmış olması koşuluyla, .NET Framework 1.0 ve 1.1 uygulamaları da çalıştırabilirsiniz. Bkz: [.NET Framework 1.1 geçiş](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).  
  
 İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], CLR etkinleştirme günlüğe kaydetme, ne zaman ve neden başlatma hata iletisi görüntülenir kayıt günlük girişlerini dahil etmek üzere geliştirilmiştir. Daha fazla bilgi için [nasıl yapılır: CLR etkinleştirme sorunlarında hata ayıklama](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [Geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
- [Nasıl Yapılır: Bir uygulamayı .NET Framework 4 veya 4.5 destekleyecek şekilde yapılandırma](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)  
- [Nasıl Yapılır: CLR etkinleştirme sorunlarında hata ayıklama](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md)  
- [Windows 10, Windows 8.1 ve Windows 8’de .NET Framework 3.5 Yükleme](../../../docs/framework/install/dotnet-35-windows-10.md)
