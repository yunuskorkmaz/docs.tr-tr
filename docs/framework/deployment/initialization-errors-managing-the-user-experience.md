---
title: '.NET Framework başlatma hataları: Kullanıcı deneyimini yönetme'
ms.date: 03/30/2017
helpviewer_keywords:
- no framework found experience
- initialization errors [.NET Framework]
- .NET Framework, initialization errors
ms.assetid: 680a7382-957f-4f6e-b178-4e866004a07e
ms.openlocfilehash: 73a0ffd4a39b144a61bf559ac424414728fb9a3f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716449"
---
# <a name="net-framework-initialization-errors-managing-the-user-experience"></a>.NET Framework başlatma hataları: Kullanıcı deneyimini yönetme

Ortak dil çalışma zamanı (CLR) etkinleştirme sistemi, yönetilen uygulama kodunu çalıştırmak için kullanılacak CLR sürümünü belirler. Bazı durumlarda, etkinleştirme sistemi, yüklemek için CLR 'nin bir sürümünü bulamamayabilir. Bu durum genellikle bir uygulama, belirli bir bilgisayarda geçersiz veya yüklü olmayan bir CLR sürümü gerektirdiğinde oluşur. İstenen sürüm bulunmazsa, CLR etkinleştirme sistemi çağrılan işlevden veya arabirimden bir HRESULT hata kodu döndürür ve uygulamayı çalıştıran kullanıcıya bir hata iletisi görüntüleyebilir. Bu makale, HRESULT kodlarının bir listesini sağlar ve hata iletisinin görüntülenmesini nasıl engelleyebileceğinizi açıklar.

Clr, CLR etkinleştirme [sorunlarını ayıklama](how-to-debug-clr-activation-issues.md)bölümünde açıklandığı gıbı, CLR etkinleştirme sorunlarını ayıklamanıza yardımcı olmak için günlük altyapısı sağlar. Bu altyapı, tamamen farklı olan [bütünleştirilmiş kod bağlama günlükleriyle](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)karıştırılmamalıdır.

## <a name="clr-activation-hresult-codes"></a>CLR etkinleştirme HRESULT kodları

CLR etkinleştirme API 'Leri bir etkinleştirme işleminin sonucunu bir konağa bildirmek için HRESULT kodlarını döndürür. CLR Konakları ek işlemlere geçmeden önce bu dönüş değerlerine her zaman başvurmalıdır.

- CLR_E_SHIM_RUNTIMELOAD

- CLR_E_SHIM_RUNTIMEEXPORT

- CLR_E_SHIM_INSTALLROOT

- CLR_E_SHIM_INSTALLCOMP

- CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND

- CLR_E_SHIM_SHUTDOWNINPROGRESS

## <a name="ui-for-initialization-errors"></a>Başlatma hataları için Kullanıcı arabirimi

CLR etkinleştirme sistemi bir uygulama için gerekli olan çalışma zamanının doğru sürümünü yükleyemiyorsa, kullanıcıların, uygulamayı çalıştırmak için düzgün şekilde yapılandırılmadığını bilgilendirmek üzere kullanıcılara bir hata iletisi görüntüler ve durumu çözmek için fırsat. Aşağıdaki hata iletisi genellikle bu durumda sunulur. Kullanıcı, uygulamanın doğru .NET Framework sürümünü indirebilecekleri bir Microsoft Web sitesine gitmek için **Evet** ' i seçebilirler.

![.NET Framework başlatma hatası iletişim kutusu](./media/initialization-errors-managing-the-user-experience/initialization-error-dialog.png "Başlatma hataları için tipik hata iletisi")

## <a name="resolving-the-initialization-error"></a>Başlatma hatası çözümleniyor

Geliştirici olarak, .NET Framework başlatma hatası iletisini denetlemek için kullanabileceğiniz çeşitli seçenekleriniz vardır. Örneğin, sonraki bölümde açıklandığı gibi, iletinin görüntülenmesini engellemek için bir API bayrağı kullanabilirsiniz. Ancak, uygulamanızın istenen çalışma zamanını yüklemesini önleyen sorunu çözmeniz hala gerekir. Aksi takdirde, uygulamanız hiç çalışmayabilir veya bazı işlevler kullanılamayabilir.

Temeldeki sorunları çözümlemek ve en iyi kullanıcı deneyimini (daha az hata iletisi) sağlamak için şunları öneririz:

- .NET Framework 3,5 (ve önceki sürümler) uygulamaları için: uygulamanızı .NET Framework 4 veya sonraki sürümlerini destekleyecek şekilde yapılandırın (bkz. [yönergeler](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)).

- .NET Framework 4 uygulamaları için: uygulama kurulumlarınızın bir parçası olarak .NET Framework 4 yeniden dağıtılabilir paketini yükleme. Bkz. [geliştiriciler Için dağıtım kılavuzu](deployment-guide-for-developers.md).

## <a name="controlling-the-error-message"></a>Hata iletisini denetleme

İstenen bir .NET Framework sürümünün bulunamadığını bildirmek için bir hata iletisi görüntüleme, kullanıcılar için faydalı bir hizmet veya küçük bir açıklama olarak görüntülenebilir. Her iki durumda da, bu kullanıcı arabirimini, bayrakları etkinleştirme API 'Lerine geçirerek kontrol edebilirsiniz.

[ICLRMetaHostPolicy:: GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi girdi olarak bir [METAHOST_POLICY_FLAGS](../unmanaged-api/hosting/metahost-policy-flags-enumeration.md) numaralandırma üyesini kabul eder. CLR 'nin istenen sürümü bulunamazsa bir hata mesajı istemek için METAHOST_POLICY_SHOW_ERROR_DIALOG bayrağını ekleyebilirsiniz. Varsayılan olarak, hata iletisi görüntülenmez. ( [ICLRMetaHost:: GetRuntime](../unmanaged-api/hosting/iclrmetahost-getruntime-method.md) yöntemi bu bayrağı kabul etmez ve hata iletisini göstermek için başka bir yol sağlamaz.)

Windows, işlem içinde çalışan kodun sonucu olarak hata iletilerinin gösterilip gösterilmeyeceğini bildirmek için kullanabileceğiniz bir [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) işlevi sağlar. Hata iletisinin görüntülenmesini engellemek için SEM_FAILCRITICALERRORS bayrağını belirtebilirsiniz.

Ancak bazı senaryolarda, bir uygulama işlemi tarafından ayarlanan SEM_FAILCRITICALERRORS ayarının geçersiz kılınması önemlidir. Örneğin, CLR 'yi barındıran ve SEM_FAILCRITICALERRORS ayarlandığı bir işlemde barındırılan yerel bir COM bileşeniniz varsa, bu belirli uygulama sürecinde hata iletilerinin görüntülenmesine bağlı olarak bayrağını geçersiz kılmak isteyebilirsiniz. Bu durumda, SEM_FAILCRITICALERRORS geçersiz kılmak için aşağıdaki bayraklardan birini kullanabilirsiniz:

- [ICLRMetaHostPolicy:: GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemiyle METAHOST_POLICY_IGNORE_ERROR_MODE kullanın.

- [GetRequestedRuntimeInfo](../unmanaged-api/hosting/getrequestedruntimeinfo-function.md) işleviyle birlikte RUNTIME_INFO_IGNORE_ERROR_MODE kullanın.

## <a name="ui-policy-for-clr-provided-hosts"></a>CLR tarafından sağlanmış konaklar için Kullanıcı Arabirimi ilkesi

CLR çeşitli senaryolar için bir dizi ana bilgisayar içerir ve bu konaklar, çalışma zamanının gerekli sürümünü yüklerken sorunlarla karşılaştığında bir hata mesajı görüntüler. Aşağıdaki tabloda, ana bilgisayarların listesi ve bunların hata ileti ilkeleri verilmiştir.

|CLR Konağı|Açıklama|Hata iletisi ilkesi|Hata iletisi devre dışı bırakılabilir mi?|
|--------------|-----------------|--------------------------|------------------------------------|
|Yönetilen EXE ana bilgisayarı|Yönetilen EXEs 'leri başlatır.|Eksik bir .NET Framework sürümü durumunda gösterilir|Hayır|
|Yönetilen COM ana bilgisayarı|Yönetilen COM bileşenlerini bir işleme yükler.|Eksik bir .NET Framework sürümü durumunda gösterilir|Evet, SEM_FAILCRITICALERRORS bayrağını ayarlayarak|
|ClickOnce ana bilgisayarı|ClickOnce uygulamalarını başlatır.|Eksik bir .NET Framework sürümünde gösterilmiştir .NET Framework 4,5 ile başlar|Hayır|
|XBAP Konağı|WPF XBAP uygulamalarını başlatır.|Eksik bir .NET Framework sürümünde gösterilmiştir .NET Framework 4,5 ile başlar|Hayır|

## <a name="windows-8-behavior-and-ui"></a>Windows 8 davranışı ve Kullanıcı arabirimi

CLR etkinleştirme sistemi, Windows 8 ' de aynı davranışı ve Kullanıcı arabirimini, Windows işletim sisteminin diğer sürümlerinde olduğu gibi, CLR 2,0 yükleme sorunlarıyla karşılaştığında de sağlar. Windows 8, CLR 4,5 kullanan .NET Framework 4,5 ' i içerir. Ancak, Windows 8, tüm CLR 2,0 kullanan 2,0, 3,0 veya 3,5 .NET Framework içermez. Sonuç olarak, CLR 2,0 ' ye bağımlı uygulamalar varsayılan olarak Windows 8 üzerinde çalışmaz. Bunun yerine, kullanıcıların 3,5 .NET Framework yüklemesine olanak tanımak için aşağıdaki iletişim kutusunu görüntüler. Kullanıcılar ayrıca Denetim Masası 'nda .NET Framework 3,5 ' i etkinleştirebilir. Her iki seçenek de, [Windows 10, Windows 8.1 ve Windows 8 ' de .NET Framework 3,5 ' i yüklein](../install/dotnet-35-windows-10.md)makalesinde açıklanmaktadır.

![Windows 8 ' de 3,5 yüklemesi için iletişim kutusu](./media/initialization-errors-managing-the-user-experience/install-framework-on-demand-dialog.png "İsteğe bağlı .NET Framework 3,5 yükleme istemi")

> [!NOTE]
> .NET Framework 4,5, kullanıcının bilgisayarındaki .NET Framework 4 ' ün (CLR 4) yerini almıştır. Bu nedenle, Windows 8 ' de bu iletişim kutusunu görüntülemeden .NET Framework 4 uygulama sorunsuz bir şekilde çalışır.

.NET Framework 3,5 yüklendiğinde, kullanıcılar Windows 8 bilgisayarlarında 2,0, 3,0 veya 3,5 .NET Framework bağlı olan uygulamaları çalıştırabilir. Ayrıca, bu uygulamaların yalnızca .NET Framework 1,0 veya 1,1 üzerinde çalışmak üzere açıkça yapılandırılmaları kaydıyla, .NET Framework 1,0 ve 1,1 uygulamalarını da çalıştırabilirler. Bkz. [.NET Framework 1,1 ' den geçiş](../migration-guide/migrating-from-the-net-framework-1-1.md).

.NET Framework 4,5 ' den başlayarak, CLR etkinleştirme günlüğü, başlatma hatası iletisinin ne zaman ve neden görüntüleneceğini kaydeden günlük girdilerini içerecek şekilde geliştirilmiştir. Daha fazla bilgi için bkz. [nasıl yapılır: CLR etkinleştirme sorunlarını ayıklama](how-to-debug-clr-activation-issues.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştiriciler için Dağıtım Kılavuzu](deployment-guide-for-developers.md)
- [Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Nasıl Yapılır: CLR Etkinleştirme Sorunlarında Hata Ayıklama](how-to-debug-clr-activation-issues.md)
- [Windows 10, Windows 8.1 ve Windows 8’de .NET Framework 3.5 Yükleme](../install/dotnet-35-windows-10.md)
