---
title: "Kayıtsız COM Birlikte Çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1eee55b2036028dd491dc82f9bce7c51aca878fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="registration-free-com-interop"></a>Kayıtsız COM Birlikte Çalışma
Kayıtsız COM birlikte çalışma derleme bilgilerini depolamak için Windows kayıt defteri kullanmadan bir bileşen etkinleştirir. Bir bilgisayarda bir bileşen dağıtımı sırasında kayıt yerine, Win32 stil bildirim dosyaları bağlama ve etkinleştirme hakkında bilgi içeren tasarım zamanında oluşturun. Bu bildirim dosyası yerine kayıt defteri anahtarları, bir nesne etkinleştirme doğrudan.  
  
 Dağıtım sırasında kaydetme yerine derlemeleriniz için kayıtsız etkinleştirme kullanarak iki avantajları sağlar:  
  
-   Bir bilgisayarda birden fazla sürümü yüklü olduğunda hangi DLL sürümü etkinleştirilir kontrol edebilirsiniz.  
  
-   Son kullanıcılar, XCOPY veya FTP, uygulamanız kendi bilgisayarında uygun bir dizine kopyalamak için kullanabilirsiniz. Uygulama, diğer dizinden çalıştırabilirsiniz.  
  
 Bu bölüm bildirimlerin Kayıtsız COM birlikte çalışma için gereken iki tür açıklar: uygulama ve bileşen bildirimleri. Bu bildirimler XML dosyalarıdır. Bir uygulama geliştiricisi tarafından oluşturulmuş bir uygulama bildirimi derlemeler ve derleme bağımlılıkları açıklayan meta veriler içerir. Bileşen bildirimi bileşen geliştirici tarafından oluşturulan Aksi takdirde Windows kayıt defterinde bulunan bilgileri içerir.  
  
### <a name="requirements-for-registration-free-com-interop"></a>Kayıtsız COM birlikte çalışma için gereksinimleri  
  
1.  Kayıtsız COM birlikte çalışma için destek Kitaplık derlemesi türüne bağlı olarak biraz değişiklik gösterir; Özellikle, olup derleme yönetilmeyen (COM yan yana) olan veya yönetilen (. NET-based). Aşağıdaki tabloda işletim sistemi ve .NET Framework sürüm gereksinimlerini her derleme türü için gösterir.  
  
    |Derleme türü|İşletim sistemi|.NET Framework sürümü|  
    |-------------------|----------------------|----------------------------|  
    |COM yan yana|Microsoft Windows XP|Gerekli değildir.|  
    |. NET tabanlı|Windows XP SP2|.NET Framework sürüm 1.1 veya üstünün.|  
  
     Windows Server 2003 ailesinin Kayıtsız COM birlikte çalışma için de destekler. NET tabanlı derlemeler.  
  
     İçin bir. Kayıt defteri boş etkinleştirmeden COM, sınıf ile uyumlu olacak şekilde sınıfı NET tabanlı bir varsayılan oluşturucuya sahip olmalıdır ve ortak olmalıdır.  
  
### <a name="configuring-com-components-for-registration-free-activation"></a>COM bileşenlerini kayıtsız etkinleştirme için yapılandırma  
  
1.  Bir COM bileşeni kayıtsız etkinleştirme katılmak yan yana derleme olarak dağıtılmalıdır. Yan yana derlemeler yönetilmeyen derlemeleri ' dir.  Daha fazla bilgi için bkz: [kullanarak yan yana derlemeler](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).  
  
     COM yan yana derlemeleri kullanmak için bir. NET tabanlı uygulama geliştiricisi bağlama ve etkinleştirme bilgilerini içeren bir uygulama bildirimi sağlamanız gerekir. Yönetilmeyen yan yana derlemeler için destek Windows XP işletim sisteminde yerleşik olarak bulunur. Etkinleştirilmekte olan bileşen kayıt defterinde olmadığında işletim sistemi tarafından desteklenen COM çalışma zamanı etkinleştirme bilgileri için bir uygulama bildirimi tarar.  
  
     Kayıtsız etkinleştirme Windows XP üzerinde yüklü COM bileşenleri için isteğe bağlıdır. Uygulamaya bir yan yana derleme ekleme hakkında ayrıntılı yönergeler için bkz: [kullanarak yan yana derlemeler](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).  
  
    > [!NOTE]
    >  Yan yana yürütme çalışma zamanı birden fazla sürümünü ve uygulamaları ve çalışma zamanı sürümü aynı bilgisayarda aynı anda çalıştırmak için kullandığınız bileşenleri birden fazla sürümünü sağlayan bir .NET Framework özelliğidir. Yan yana yürütme ve yan yana derlemeler yan yana işlevselliği sağlamak için farklı mekanizmalardır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma](../../../docs/framework/interop/configure-net-framework-based-com-components-for-reg.md)
