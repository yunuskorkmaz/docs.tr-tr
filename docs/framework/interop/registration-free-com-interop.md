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
ms.openlocfilehash: fbdc6f795aff5e84debd2e83485a22f1d42b31d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185308"
---
# <a name="registration-free-com-interop"></a>Kayıtsız COM Birlikte Çalışma
Kayıtsız COM birlikte çalışma bütünleştirilmiş kod bilgileri depolamak için Windows kayıt defteri kullanmadan bir bileşen etkinleştirir. Dağıtım sırasında bir bilgisayarda bir bileşen kaydetmek yerine Win32 stili bildirim dosyalarını, bağlama ve etkinleştirme hakkında bilgiler içeren tasarım zamanında oluşturun. Bu bildirim dosyaları yerine kayıt defteri anahtarları, bir nesnenin etkinleştirme doğrudan.  
  
 Kayıtsız etkinleştirme için bunları dağıtım sırasında kayıt yerine derlemelerinizin kullanarak iki avantaj sağlar:  
  
-   Bir bilgisayar üzerinde birden fazla sürümü yüklendiğinde hangi DLL sürümü etkinleştirilir denetleyebilirsiniz.  
  
-   Son kullanıcılar, XCOPY veya FTP, uygulamanızı bilgisayarlarında uygun bir dizine kopyalamak için kullanabilirsiniz. Uygulama bu dizinden çalıştırabilirsiniz.  
  
 Kayıtsız COM birlikte çalışması için gereken bildirimleri iki tür Bu bölümde açıklanmaktadır: uygulama ve bileşen bildirimleri. Bu bildirimler, XML dosyalarıdır. Bir uygulama geliştiricisi tarafından oluşturulan bir uygulama bildirimi, derlemeler ve derleme bağımlılıklarını açıklayan meta veriler içerir. Bir bileşen bildirimini oluşturulan bir bileşen geliştirici tarafından aksi takdirde Windows kayıt defterinde yer alan bilgiler içerir.  
  
### <a name="requirements-for-registration-free-com-interop"></a>Kayıtsız COM birlikte çalışma için gereksinimler  
  
1.  Kayıtsız COM birlikte çalışma için destek, kitaplık derlemesine türüne bağlı olarak biraz farklılık gösterir; Özellikle, derleme yönetilmeyen (COM yan yana) olan olup yönetilen (. NET-based). Aşağıdaki tabloda, işletim sistemi ve .NET Framework sürüm gereksinimleri her derleme türünü gösterir.  
  
    |Derleme türü|İşletim sistemi|.NET Framework sürümü|  
    |-------------------|----------------------|----------------------------|  
    |COM yan yana|Microsoft Windows XP|Gerekli değildir.|  
    |. AĞ tabanlı|Windows XP SP2|.NET Framework sürüm 1.1 veya üzeri.|  
  
     Windows Server 2003 ailesinin Kayıtsız COM birlikte çalışması için de destekler. Ağ-bazlı derlemeleri.  
  
     İçin bir. Kayıtsız etkinleştirme COM, sınıf işleminden ile uyumlu olacak şekilde sınıf ağ tabanlı bir varsayılan oluşturucusu olmalıdır ve ortak olmalıdır.  
  
### <a name="configuring-com-components-for-registration-free-activation"></a>Kayıtsız etkinleştirme için COM bileşenlerini yapılandırma  
  
1.  Bir COM bileşeni kayıtsız etkinleştirme ' katılmak bir yan yana derleme olarak dağıtılmalıdır. Yan yana derlemeler yönetilmeyen derlemelerdir.  Daha fazla bilgi için [USING yan yana derlemeler](/windows/desktop/SbsCs/using-side-by-side-assemblies).  
  
     COM yan yana derlemeler, kullanılacak bir. AĞ tabanlı uygulama geliştirme, bağlama ve etkinleştirme bilgilerini içeren bir uygulama bildirimi sağlamanız gerekir. Yönetilmeyen yan yana derlemeler için desteği Windows XP işletim sisteminde yerleşik olarak bulunur. Etkinleştirilmekte olan bileşen kayıt defterinde olmadığında COM işletim sistemi tarafından desteklenen çalışma zamanı, uygulama bildiriminde etkinleştirme bilgilerini tarar.  
  
     Kayıtsız etkinleştirme, COM bileşenleri yüklü Windows XP için isteğe bağlıdır. Yan yana derleme, uygulamaya ekleme ile ilgili ayrıntılı yönergeler için bkz [USING yan yana derlemeler](/windows/desktop/SbsCs/using-side-by-side-assemblies).  
  
    > [!NOTE]
    >  Yan yana yürütme, çalışma zamanının birden çok sürümünü ve uygulamaları ve bileşenleri aynı bilgisayarda aynı anda çalıştırmak için çalışma zamanının bir sürümünü kullanan birden çok sürümünü sağlayan bir .NET Framework özelliğidir. Yan yana yürütme ve yan yana derlemeleri yan yana işlevselliği sağlamak için farklı mekanizmasıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma](../../../docs/framework/interop/configure-net-framework-based-com-components-for-reg.md)
