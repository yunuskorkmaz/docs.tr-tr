---
title: Kayıtsız COM Birlikte Çalışma
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ae92232b1d50d1381b6873e21a4c185db6efd25
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051643"
---
# <a name="registration-free-com-interop"></a>Kayıtsız COM Birlikte Çalışma
Kayıtsız COM birlikte çalışması, derleme bilgilerini depolamak için Windows kayıt defteri kullanmadan bir bileşeni etkinleştirir. Dağıtım sırasında bir bileşeni bir bilgisayara kaydetmek yerine, tasarım zamanında, bağlama ve etkinleştirme hakkında bilgi içeren Win32 stili bildirim dosyaları oluşturursunuz. Kayıt defteri anahtarları yerine, bir nesnenin etkinleştirilmesini doğrudan bu bildirim dosyaları.  
  
 Dağıtım sırasında bunları kaydetmek yerine derlemeleriniz için kayıtsız etkinleştirme kullanmak iki avantaj sunar:  
  
- Bilgisayara birden fazla sürüm yüklendiğinde hangi DLL sürümünün etkinleştirildiğini denetleyebilirsiniz.  
  
- Son kullanıcılar, uygulamanızı bilgisayarlarında uygun bir dizine kopyalamak için XCOPY veya FTP kullanabilir. Uygulama daha sonra bu dizinden çalıştırılabilir.  
  
 Bu bölümde, kayıtsız COM birlikte çalışması için gereken iki tür bildirim açıklanmaktadır: uygulama ve bileşen bildirimleri. Bu bildirimler XML dosyalarıdır. Uygulama geliştiricisi tarafından oluşturulan bir uygulama bildirimi, derlemeleri ve derleme bağımlılıklarını açıklayan meta verileri içerir. Bileşen geliştiricisi tarafından oluşturulan bir bileşen bildirimi, Windows kayıt defterinde bulunmayan bilgiler içerir.  
  
### <a name="requirements-for-registration-free-com-interop"></a>Kayıtsız COM birlikte çalışma gereksinimleri  
  
1. Kayıtsız COM birlikte çalışma desteği, kitaplık derlemesinin türüne göre biraz farklılık gösterir; Özellikle, derlemenin yönetilmeyen olup olmadığı (COM yan yana) veya yönetilme (. NET tabanlı). Aşağıdaki tabloda her derleme türü için işletim sistemi ve .NET Framework sürüm gereksinimleri gösterilmektedir.  
  
    |Bütünleştirilmiş kod türü|İşletim sistemi|.NET Framework sürümü|  
    |-------------------|----------------------|----------------------------|  
    |COM yan yana|Microsoft Windows XP|Gerekli değildir.|  
    |. NET tabanlı|SP2 ile Windows XP|NET Framework sürüm 1,1 veya üzeri.|  
  
     Windows Server 2003 ailesi, için kayıtsız COM birlikte çalışabilirliği de destekler. NET tabanlı derlemeler.  
  
     İçin. AĞ tabanlı sınıf COM 'dan kayıt defteri içermeyen etkinleştirme ile uyumlu olacak şekilde, sınıf parametresiz bir oluşturucuya sahip olmalıdır ve public olmalıdır.  
  
### <a name="configuring-com-components-for-registration-free-activation"></a>Kayıt-ücretsiz etkinleştirme için COM bileşenlerini yapılandırma  
  
1. Bir COM bileşeninin kayıt için ücretsiz etkinleştirmeye katılması için, yan yana derleme olarak dağıtılması gerekir. Yan yana derlemeler yönetilmeyen derlemelerdir.  Daha fazla bilgi için bkz. [yan yana derlemeler kullanma](/windows/desktop/SbsCs/using-side-by-side-assemblies).  
  
     COM yan yana derlemelerini kullanmak için bir. NET tabanlı uygulama geliştiricisi, bağlama ve etkinleştirme bilgilerini içeren bir uygulama bildirimi sağlamalıdır. Yönetilmeyen yan yana derlemeler için destek, Windows XP işletim sisteminde yerleşik olarak bulunur. İşletim sistemi tarafından desteklenen COM çalışma zamanı, etkinleştirilen bileşen kayıt defterinde olmadığında etkinleştirme bilgileri için bir uygulama bildirimini tarar.  
  
     Kayıt-ücretsiz etkinleştirme, Windows XP 'de yüklü COM bileşenleri için isteğe bağlıdır. Bir uygulamaya yan yana derleme ekleme hakkında ayrıntılı yönergeler için bkz. [yan yana derlemeler kullanma](/windows/desktop/SbsCs/using-side-by-side-assemblies).  
  
    > [!NOTE]
    > Yan yana yürütme, çalışma zamanının birden çok sürümünün yanı sıra çalışma zamanının bir sürümünü kullanan uygulamaların ve bileşenlerin birden çok sürümünü aynı anda aynı bilgisayarda çalıştırmak için sağlayan bir .NET Framework özelliğidir. Yan yana yürütme ve yan yana derlemeler yan yana işlevsellik sağlamaya yönelik farklı mekanizmalarda bulunur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kayıt-ücretsiz etkinleştirme için .NET Framework tabanlı COM bileşenlerini yapılandırma](configure-net-framework-based-com-components-for-reg.md)
