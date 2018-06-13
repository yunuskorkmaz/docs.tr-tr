---
title: Derlemeler ve Genel Derleme Önbelleği ile Çalışma
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91e780ed7e841809f21130822babe55ad4935670
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744310"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a>Derlemeler ve Genel Derleme Önbelleği ile Çalışma
Eğer bir derlemeyi birden çok uygulama arasında paylaşmak istiyorsanız, bu derlemeyi genel bütünleştirilmiş kod önbelleğine yükleyebilirsiniz. Ortak dil çalışma zamanının yüklü olduğu tüm bilgisayarlar, makine düzeyindeki bu kod önbelleğine sahiptir. Genel Derleme Önbelleği özellikle bilgisayarda çeşitli uygulamalar tarafından paylaşılmak üzere belirtilen derlemelerini depolar. Bir derlemenin genel bütünleştirilmiş kod önbelleğine yüklenebilmesi için tanımlayıcı ada sahip olması gerekir.  
  
> [!NOTE]
>  Genel bütünleştirilmiş kod önbelleğine yerleştirilen derlemeler aynı derleme adı ve dosya adına sahip olmalıdır (dosya adı uzantısı dahil değil). Örneğin, myAssembly derleme adına sahip bir derlemenin, myAssembly.exe ya da myAssembly.dll dosya adı olmalıdır.  
  
 Derlemeleri, yalnızca gerektiğinde genel bütünleştirilmiş kod önbelleğine yükleyerek paylaşmalısınız. Derlemeyi paylaşmanız kesinlikle gerekli olmadığı sürece, genel bir kılavuz olarak, derleme bağımlılıklarını özel tutun ve derlemeleri uygulama dizinine yerleştirin. Ek olarak, derlemeleri COM ile birlikte çalışmaya veya yönetilmeyen koda erişilebilir yapmak için genel bütünleştirilmiş kod önbelleğine yüklemeniz gerekli değildir.  
  
 Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklemek istemeniz için birkaç neden vardır:  
  
-   Paylaşılan konum.  
  
     Uygulamalar tarafından kullanılması gereken derlemeler genel bütünleştirilmiş kod önbelleğine konulabilir. Örneğin, eğer tüm uygulamaların genel bütünleştirilmiş kod önbelleğinde bulunan bir derlemeyi kullanması gerekiyorsa bir sürüm ilkesi, başvuruları derlemeye yeniden yönlendiren Machine.config dosyasına eklenebilir.  
  
-   Dosya güvenliği.  
  
     Yöneticiler, yazma ve yürütme erişimini denetlemek için systemroot dizinini genellikle bir Erişim Denetim Listesi (ACL) kullanarak korur. Genel bütünleştirilmiş kod önbelleği systemroot dizininde yüklü olduğu için, bu dizinin ACL'sini devralır. Yalnızca yönetici ayrıcalıklarına sahip kullanıcılar, Genel Derleme Önbelleği'nden dosyalarını silmek için izin önerilir.  
  
-   Yan yana sürüm oluşturma.  
  
     Genel bütünleştirilmiş kod önbelleğinde derlemelerin aynı ada ancak farklı sürüm bilgisine sahip olan birden çok kopyası tutulabilir.  
  
-   Ek arama konumu.  
  
     Ortak dil çalışma zamanı, bir yapılandırma dosyasındaki kod temeli bilgisini algılamadan veya kullanmadan önce, derleme isteğiyle eşleşen bir derleme için genel bütünleştirilmiş kod önbelleğini kontrol eder.  
  
 Bir derlemeyi genel bütünleştirilmiş kod önbelleğine açıkça yüklemek istemeyeceğiniz senaryolar olduğuna dikkat edin. Eğer bir uygulamayı oluşturan derlemelerden birini genel bütünleştirilmiş kod önbelleğine yerleştirirseniz, uygulama dizinini kopyalamak için XCOPY'i kullanarak uygulamayı artık çoğaltamaz veya yükleyemezsiniz. Bu durumda, derlemeyi de genel bütünleştirilmiş kod önbelleğine taşımanız gerekir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Bir Bütünleştirilmiş Kodu Genel Derleme Önbelleğine Yükleme](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 Bir derlemeyi genel bütünleştirilmiş kod belleğine yükleme yöntemlerini açıklar.  
  
 [Nasıl yapılır: Genel Derleme Önbelleğinin İçeriğini Görüntüleme](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)  
 Nasıl kullanılacağı açıklanmaktadır [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) genel derleme önbelleğinin içeriğini görüntülemek için.  
  
 [Nasıl yapılır: Bir Bütünleştirilmiş Kodu Genel Derleme Önbelleğinden Kaldırma](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 Nasıl kullanılacağı açıklanmaktadır [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) bir derlemeyi Genel Derleme Önbelleği'nden kaldırmak için.  
  
 [Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 Hizmet verilen bileşenlerin (yönetilen COM+ bileşenleri) neden genel bütünleştirilmiş kod önbelleğine yerleştirilmesi gerektiğini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
 Derleme oluşturmaya genel bir bakış sağlar.  
  
 [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)  
 Genel bütünleştirilmiş kod önbelleğini açıklar.  
  
 [Nasıl yapılır: Bütünleştirilmiş Kod İçeriklerini Görüntüleme](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Nasıl kullanılacağı açıklanmaktadır [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) bir derlemede Microsoft Ara dili (MSIL) bilgilerini görüntülemek için.  
  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Ortak dil çalışma zamanının uygulamanızı oluşturan derlemeleri nasıl konumlandırdığını ve yüklediğini açıklar.  
  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Yönetilen uygulamaların yapı taşları olan derlemeleri açıklar.
