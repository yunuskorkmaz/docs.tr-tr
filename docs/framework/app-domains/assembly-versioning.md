---
title: "Derleme Sürümü Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a956e0c4521e4a1079b331868e811e68af2e710d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-versioning"></a>Derleme Sürümü Oluşturma
Ortak dil çalışma zamanını kullanan tüm derlemelerin sürüm oluşturma işlemi, derleme düzeyinde gerçekleşir. Bir derlemenin belirli sürümü ve bağımlı derlemelerin sürümleri, derlemenin bildirimine kaydedilir. Çalışma zamanı için varsayılan sürüm ilkesi, yapılandırma dosyalarındaki sürüm ilkelerinde açıkça geçersiz kılınmadığı sürece (uygulama yapılandırma dosyası, yayımcı ilke dosyası ve bilgisayar yöneticisinin yapılandırma dosyası) uygulamaların yalnızca yapılandırıldığı ve test edildiği sürümlerle çalışmasıdır.  
  
> [!NOTE]
>  Sürüm oluşturma yalnızca tanımlayıcı ada sahip derlemeler üzerinde yapılır.  
  
 Çalışma zamanı, bir derleme bağlama isteğini çözmek için birkaç adım gerçekleştirir:  
  
1.  Bağlanacak derlemenin sürümünü belirlemek için orijinal derleme başvurusunu denetler.  
  
2.  Sürüm ilkesini uygulamak için uygulanabilir tüm yapılandırma dosyalarını denetler.  
  
3.  Orijinal derleme başvurusundan ve yapılandırma dosyalarında belirtilen yeniden yönlendirmelerden doğru derlemeyi belirler ve çağıran derlemeye bağlanacak olan sürümü belirler.  
  
4.  Genel derleme önbelleği denetler, olarak kullanılabilecek kod temeli yapılandırma dosyalarını ve uygulamanın dizin ve alt dizinleri algılama kurallarını kullanarak içinde açıklanan sonra denetimleri içinde belirtilen [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Aşağıdaki resim bu adımları gösterir.  
  
 ![.Assembly extern myAssembly](../../../docs/framework/app-domains/media/versioningover.gif "versioningover")  
Bir derleme bağlama isteğinin çözülmesi  
  
 Uygulamaları yapılandırma hakkında daha fazla bilgi için bkz: [yapılandırma uygulamaları](../../../docs/framework/configure-apps/index.md). Bağlama ilkesi hakkında daha fazla bilgi için bkz: [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
## <a name="version-information"></a>Sürüm Bilgileri  
 Her derlemenin sürüm bilgisini ifade etmek için iki farklı yolu vardır:  
  
-   Derleme adı ve kültür bilgisiyle birlikte derlemenin kimliğinin bir parçası olan derleme sürüm numarası. Bu numara çalışma zamanı tarafından sürüm ilkesini uygulamak için kullanılır ve çalışma zamanında tür çözümleme işleminde önemli bir rol oynar.  
  
-   Sadece bilgi amaçlı olarak eklenen ek sürüm bilgilerini temsil eden bir dize olan bilgilendirme sürümü.  
  
### <a name="assembly-version-number"></a>Derleme Sürüm Numarası  
 Her derleme, kimliğinin bir parçası olarak bir sürüm numarasına sahiptir. Bu nedenle, sürüm numarası farklı olan iki derleme, çalışma zamanı tarafından tamamen farklı derlemeler olarak değerlendirilir. Bu sürüm numarası, fiziksel olarak aşağıdaki biçime sahip dört bölümlü bir dize olarak temsil edilir:  
  
 \<*ana sürüm*>.\< *alt sürüm*>.\< *yapı numarası*>.\< *düzeltme*>  
  
 Örneğin, 1.5.1254.0 sürümü ana sürüm olarak 1, alt sürüm olarak 5, yapı numarası olarak 1254 ve düzeltme numarası olarak da 0 belirtir.  
  
 Sürüm numarası, derleme adı ve ortak anahtarı içeren kimlik bilgisinin yanı sıra ilişkiler hakkında bilgi ve uygulamayla bağlı olan diğer derlemelerin kimlikleriyle birlikte derleme bildiriminde saklanır.  
  
 Bir derleme yapılandırıldığında, geliştirme aracı derleme bildiriminde atıf yapılan her derleme için bağımlılık bilgisi kaydeder. Çalışma zamanı bu sürüm numaralarını bir yönetici, uygulama veya yayımcı tarafından ayarlanan yapılandırma bilgisiyle birlikte kullanarak başvurulan bir derlemenin uygun sürümünü yükler.  
  
 Çalışma zamanı, normal ve tanımlayıcı ada sahip derlemeleri sürüm oluşturma amacıyla ayırt eder. Sürüm denetleme yalnızca tanımlayıcı ada sahip derlemelerde gerçekleşir.  
  
 Sürüm bağlama ilkeleri belirtme hakkında daha fazla bilgi için bkz: [yapılandırma uygulamaları](../../../docs/framework/configure-apps/index.md). Sürüm bilgileri çalışma zamanı belirli bir derleme bulmak için nasıl kullandığı hakkında daha fazla bilgi için bkz: [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
### <a name="assembly-informational-version"></a>Derleme Bilgilendirme Sürümü  
 Bilgilendirme sürümü, bir derlemeye yalnızca bilgilendirme amacıyla ek sürüm bilgileri ekleyen bir dizedir; bu bilgi çalışma zamanında kullanılmaz. Metin tabanlı bilgilendirme sürümü, ürünün pazarlama belgelerine, paketlemesine veya ürün adına karşılık gelir ve çalışma zamanı tarafından kullanılmaz. Örneğin, bir bilgilendirme sürümü "Ortak Dil Çalışma Zamanı sürüm 1.0" veya "NET Control SP 2" olabilir. Microsoft Windows'daki dosya özellikleri iletişim kutusunun Sürüm sekmesinde, bu bilgi "Ürün Sürümü" öğesinde görünür.  
  
> [!NOTE]
>  Herhangi bir metni ayarlayabilseniz de dize derleme sürüm numarası tarafından kullanılan biçimde değilse veya o biçimdeyse ancak jokerler içeriyorsa derleme esnasında bir uyarı iletisi görünür. Uyarı zararsız budur.  
  
 Bilgilendirme sürümü <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType> özel özniteliği kullanılarak temsil edilir. Bilgilendirme sürümü özniteliği hakkında daha fazla bilgi için bkz: [ayarı derleme özniteliklerinin](../../../docs/framework/app-domains/set-assembly-attributes.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma zamanı derlemeleri nasıl bulur](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Uygulamaları yapılandırma](../../../docs/framework/configure-apps/index.md)  
 [Derleme özniteliklerini ayarlama](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 [Ortak dil çalışma zamanı derlemeleri](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
