---
title: '.NET Framework başlatma hataları: Kullanıcı deneyimini yönetme'
ms.date: 03/30/2017
helpviewer_keywords:
- no framework found experience
- initialization errors [.NET Framework]
- .NET Framework, initialization errors
ms.assetid: 680a7382-957f-4f6e-b178-4e866004a07e
ms.openlocfilehash: 73a0ffd4a39b144a61bf559ac424414728fb9a3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716449"
---
# <a name="net-framework-initialization-errors-managing-the-user-experience"></a>.NET Framework başlatma hataları: Kullanıcı deneyimini yönetme

Ortak dil çalışma süresi (CLR) etkinleştirme sistemi, yönetilen uygulama kodunu çalıştırmak için kullanılacak CLR sürümünü belirler. Bazı durumlarda, etkinleştirme sistemi clr yüklemek için bir sürümünü bulmak mümkün olmayabilir. Bu durum genellikle bir uygulama geçersiz veya belirli bir bilgisayarda yüklü olmayan bir CLR sürümü gerektiriyorsa oluşur. İstenen sürüm bulunamazsa, CLR etkinleştirme sistemi çağrılan işlev veya arabirimden bir HRESULT hata kodu döndürür ve uygulamayı çalıştıran kullanıcıya bir hata iletisi görüntüleyebilir. Bu makalede, HRESULT kodlarının bir listesi sağlar ve hata iletisinin görüntülenmesini nasıl önleyeceğiniz açıklanmaktadır.

CLR, CLR etkinleştirme sorunlarını nasıl karşılandığı gibi hata ayıklamanıza yardımcı olacak günlük altyapısı [sağlar: Hata Ayıklama CLR Etkinleştirme Sorunları.](how-to-debug-clr-activation-issues.md) Bu altyapı tamamen farklı [derleme bağlama günlükleri](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)ile karıştırılmamalıdır.

## <a name="clr-activation-hresult-codes"></a>CLR aktivasyon HRESULT kodları

CLR etkinleştirme API'leri, etkinleştirme işleminin sonucunu bir ana bilgisayara bildirmek için HRESULT kodlarını döndürer. CLR ana bilgisayarları, ek işlemlere devam etmeden önce her zaman bu iade değerlerine başvurmalıdır.

- CLR_E_SHIM_RUNTIMELOAD

- CLR_E_SHIM_RUNTIMEEXPORT

- CLR_E_SHIM_INSTALLROOT

- CLR_E_SHIM_INSTALLCOMP

- CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND

- CLR_E_SHIM_SHUTDOWNINPROGRESS

## <a name="ui-for-initialization-errors"></a>Başlatma hataları için UI

CLR etkinleştirme sistemi bir uygulama tarafından gerekli olan çalışma zamanının doğru sürümünü yükleyemiyorsa, kullanıcılara bilgisayarlarının uygulamayı çalıştırmak için düzgün bir şekilde yapılandırılmadığını bildiren bir hata iletisi görüntüler ve durumu düzeltmek için fırsat. Aşağıdaki hata iletisi genellikle bu durumda sunulur. Kullanıcı, uygulama için doğru .NET Framework sürümünü indirebilecekleri bir Microsoft web sitesine gitmek için **Evet'i** seçebilir.

![.NET Framework Initialization Error iletişim kutusu](./media/initialization-errors-managing-the-user-experience/initialization-error-dialog.png "Başlatma hataları için tipik hata iletisi")

## <a name="resolving-the-initialization-error"></a>Başlatma hatasını çözme

Geliştirici olarak,.NET Framework başlatma hata iletisini denetlemek için çeşitli seçenekleriniz vardır. Örneğin, bir sonraki bölümde açıklandığı gibi iletinin görüntülenmesini önlemek için bir API bayrağı kullanabilirsiniz. Ancak, uygulamanızın istenen çalışma süresini yüklemesini engelleyen sorunu yine de çözmeniz gerekir. Aksi takdirde, uygulamanız hiç çalışmayabilir veya bazı işlevler kullanılamayabilir.

Altta yatan sorunları gidermek ve en iyi kullanıcı deneyimini (daha az hata iletisi) sağlamak için aşağıdakileri öneririz:

- .NET Framework 3.5 (ve önceki) uygulamalar için: .NET Framework 4 veya sonraki sürümlerini destekleyecek şekilde uygulamanızı yapılandırın [(yönergelere](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)bakın).

- .NET Framework 4 uygulamaları için: .NET Framework 4 yeniden dağıtılabilir paketini uygulama kurulumuzun bir parçası olarak yükleyin. [Geliştiriciler için Dağıtım Kılavuzu'na](deployment-guide-for-developers.md)bakın.

## <a name="controlling-the-error-message"></a>Hata iletisini denetleme

İstenen .NET Framework sürümünün bulunamadığını bildirmek için bir hata iletisi görüntülenmek, kullanıcılar için yararlı bir hizmet veya küçük bir sıkıntı olarak görülebilir. Her iki durumda da, etkinleştirme API'lerine bayraklar geçirerek bu UI'yi denetleyebilirsiniz.

[ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi giriş olarak [METAHOST_POLICY_FLAGS](../unmanaged-api/hosting/metahost-policy-flags-enumeration.md) numaralandırma üyesi kabul eder. CLR'nin istenen sürümü bulunamazsa hata iletisi istemek için METAHOST_POLICY_SHOW_ERROR_DIALOG bayrağı ekleyebilirsiniz. Varsayılan olarak, hata iletisi görüntülenmez. [(ICLRMetaHost::GetRuntime](../unmanaged-api/hosting/iclrmetahost-getruntime-method.md) yöntemi bu bayrağı kabul etmez ve hata iletisini görüntülemek için başka bir yol sağlamaz.)

Windows, işlemiçinde çalışan kod sonucunda hata iletilerinin gösterilmesini isteyip istemediğinizi bildirmek için kullanabileceğiniz bir [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) işlevi sağlar. Hata iletisinin görüntülenmesini önlemek için SEM_FAILCRITICALERRORS bayrağını belirtebilirsiniz.

Ancak, bazı senaryolarda, bir uygulama işlemi tarafından ayarlanan SEM_FAILCRITICALERRORS ayarını geçersiz kılmak önemlidir. Örneğin, CLR'yi barındıran ve SEM_FAILCRITICALERRORS ayarlandığı bir işlemde barındırılan yerel bir COM bileşeniniz varsa, belirli bir uygulama sürecinde hata iletileri görüntülemenin etkisine bağlı olarak bayrağı geçersiz kılmak isteyebilirsiniz. Bu durumda, SEM_FAILCRITICALERRORS geçersiz kılmak için aşağıdaki bayraklardan birini kullanabilirsiniz:

- [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi ile METAHOST_POLICY_IGNORE_ERROR_MODE kullanın.

- [GetRequestedRuntimeInfo](../unmanaged-api/hosting/getrequestedruntimeinfo-function.md) işlevi ile RUNTIME_INFO_IGNORE_ERROR_MODE kullanın.

## <a name="ui-policy-for-clr-provided-hosts"></a>CLR tarafından sağlanan ana bilgisayarlar için Ara bilgi ilkesi

CLR çeşitli senaryolar için ana bilgisayar ları içerir ve bu ana bilgisayarların tümü, çalışma zamanının gerekli sürümünü yüklerken sorunlarla karşılaştıklarında bir hata iletisi görüntüler. Aşağıdaki tablo, ana bilgisayarların ve hata iletisi ilkelerinin bir listesini sağlar.

|CLR ana bilgisayar|Açıklama|Hata iletisi ilkesi|Hata iletisi devre dışı alınabilir mi?|
|--------------|-----------------|--------------------------|------------------------------------|
|Yönetilen EXE ana bilgisayar|Yönetilen EXE'leri başlatır.|Eksik bir .NET Framework sürümü nde gösterilir|Hayır|
|Yönetilen COM ana bilgisayar|Yönetilen COM bileşenlerini bir işleme yükler.|Eksik bir .NET Framework sürümü nde gösterilir|Evet, SEM_FAILCRITICALERRORS bayrağı nı ayarlayarak|
|ClickOnce ana bilgisayar|ClickOnce uygulamalarını başlatın.|.NET Framework 4.5 ile başlayan bir .NET Framework sürümü eksik durumunda gösterilir|Hayır|
|XBAP ana bilgisayar|WPF XBAP uygulamalarını başlatın.|.NET Framework 4.5 ile başlayan bir .NET Framework sürümü eksik durumunda gösterilir|Hayır|

## <a name="windows-8-behavior-and-ui"></a>Windows 8 davranışı ve UI

CLR etkinleştirme sistemi, CLR 2.0 yükleme sorunlarıyla karşılaşmadığı sürece, Windows 8'de windows işletim sisteminin diğer sürümlerinde olduğu gibi aynı davranışı ve kullanıcı kullanıcı yanını sağlar. Windows 8, CLR 4.5 kullanan .NET Framework 4.5'i içerir. Ancak, Windows 8,clr 2.0 kullanan .NET Framework 2.0, 3.0 veya 3.5'i içermez. Sonuç olarak, CLR 2.0'a bağlı uygulamalar varsayılan olarak Windows 8'de çalışmaz. Bunun yerine, kullanıcıların .NET Framework 3.5'i yüklemesini sağlamak için aşağıdaki iletişim kutusunu görüntülerler. Kullanıcılar denetim panelinde .NET Framework 3.5'i de etkinleştirebilir. Her iki seçenek de makalede [Windows 10, Windows 8.1 ve Windows 8'de .NET Framework 3.5'i yükleyin.](../install/dotnet-35-windows-10.md)

![Windows 8'de 3,5 yükleme için iletişim kutusu](./media/initialization-errors-managing-the-user-experience/install-framework-on-demand-dialog.png "Talep üzerine .NET Framework 3.5'i yüklemek için istek")

> [!NOTE]
> .NET Framework 4.5, kullanıcının bilgisayarındaki .NET Framework 4'ün (CLR 4) yerini alır. Bu nedenle, .NET Framework 4 uygulamaları, bu iletişim kutusunu görüntülemeden Windows 8'de sorunsuz bir şekilde çalışır.

.NET Framework 3.5 yüklendiğinde, kullanıcılar Windows 8 bilgisayarlarında .NET Framework 2.0, 3.0 veya 3.5'e bağlı uygulamaları çalıştırabilir. Bu uygulamalar açıkça yalnızca .NET Framework 1.0 veya 1.1 üzerinde çalışacak şekilde yapılandırılmamış olması koşuluyla ,NET Framework 1.0 ve 1.1 uygulamalarını da çalıştırabilirler. Bkz. [.NET Framework 1.1'den Geçiş](../migration-guide/migrating-from-the-net-framework-1-1.md).

.NET Framework 4.5 ile başlayarak, CLR etkinleştirme günlüğe kaydetme nin ne zaman ve neden başlatıldığını kaydeden günlük girişlerini içerecek şekilde geliştirilmiştir. Daha fazla bilgi için [bkz: Hata Ayıklama CLR Etkinleştirme Sorunları.](how-to-debug-clr-activation-issues.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştiriciler için Dağıtım Kılavuzu](deployment-guide-for-developers.md)
- [Nasıl yapilir: Bir uygulamayı .NET Framework 4 veya sonraki sürümlerini destekleyecek şekilde yapılandırın](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Nasıl Yapılır: CLR Etkinleştirme Sorunlarında Hata Ayıklama](how-to-debug-clr-activation-issues.md)
- [Windows 10, Windows 8.1 ve Windows 8’de .NET Framework 3.5 Yükleme](../install/dotnet-35-windows-10.md)
