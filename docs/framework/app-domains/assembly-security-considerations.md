---
title: "Derleme Güvenliği Konuları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], security
- signcodes
- names [.NET Framework], assemblies
- strong-named assemblies, security considerations
- signing assemblies
- assemblies [.NET Framework], signing
- granting permissions, assemblies
- assemblies [.NET Framework], strong-named
- names [.NET Framework], strong names
- permissions [.NET Framework], assemblies
- security [.NET Framework], assemblies
- integrity with assemblies
ms.assetid: 1b5439c1-f3d5-4529-bd69-01814703d067
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 11c66af3a855dac649d5f09944d68fb77a0e8619
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-security-considerations"></a>Derleme Güvenliği Konuları
<a name="top"></a>Bir derlemeyi derlerken, derleme çalıştırılması için gerekli izinleri belirtebilirsiniz. Bir derlemeye belirli izinlerin verilip verilmediği kanıta göre belirlenir.  
  
 Kanıtın kullanıldığı iki farklı yol vardır:  
  
-   Giriş kanıtı yükleyici tarafından toplanan kanıtla birleştirilerek ilke çözümlemesi için kullanılacak olan son kanıt kümesini oluşturur. Bu anlam kullanan yöntemleri dahil **Assembly.Load**, **Assembly.LoadFrom**, ve **Activator.CreateInstance**.  
  
-   Giriş kanıtı, ilke çözümlemesi için kullanılan son kanıt kümesi olarak değiştirilmeden kullanılır. Bu anlam kullanan yöntemleri dahil **Assembly.Load(byte[])** ve **AppDomain.DefineDynamicAssembly()**.  
  
 İsteğe bağlı olanağı verilir tarafından [Güvenlik İlkesi](../../../docs/framework/misc/code-access-security-basics.md) derleme çalıştırılacağı bilgisayarda ayarlayın. Kodunuzun tüm olası güvenlik özel durumlarını işlemesini istiyorsanız, aşağıdakilerden birini yapabilirsiniz:  
  
-   Kodunuzun sahip olması gereken tüm izinler için bir izin isteği ekleyin ve izinler verilmezse gerçekleşecek yükleme zamanı hatasını önden işleyin.  
  
-   Kodunuzun ihtiyacı olabilecek izinleri almak için bir izin isteği kullanmayın, ancak izinler verilmezse oluşacak güvenlik özel durumlarını işlemeye hazır olun.  
  
    > [!NOTE]
    >  Güvenlik karmaşık bir alandır ve pek çok seçeneğiniz vardır. Daha fazla bilgi için bkz: [temel güvenlik kavramları](../../../docs/standard/security/key-security-concepts.md).  
  
 Yükleme zamanında derlemenin kanıtı güvenlik ilkesine giriş olarak kullanılır. Güvenlik ilkesi, kuruluş ve bilgisayar yöneticisinin yanı sıra kullanıcı ilke ayarları tarafından belirlenir ve yürütüldüklerinde tüm yönetilen kodlara verilen izinler kümesini belirler. Güvenlik ilkesi derlemenin yayımcısı için (imzalama aracıyla oluşturulmuş bir imzaya sahipse), derlemenin indirildiği Web sitesi ve bölge için (Internet Explorer terimiyle) veya derlemenin tanımlayıcı adı için belirlenebilir. Örneğin bir bilgisayarın yöneticisi, bir Web sitesinden indirilen ve belirli bir yazılım şirketi tarafından imzalanan tüm kodların bir bilgisayardaki veritabanına erişmesine izin veren, ancak bilgisayarın diskine yazmasına izin vermeyen bir güvenlik ilkesi belirleyebilir.  
  
## <a name="strong-named-assemblies-and-signing-tools"></a>Katı Ada Sahip Derlemeler ve İmzalama Araçları  
 İki farklı ancak birbirini tamamlayıcı şekilde derlemeyi imzalamak: güçlü bir adla veya kullanarak [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md). Bir derlemeyi tanımlayıcı adla imzalama ortak anahtar şifrelemesi derleme bildirimi içeren dosyasına ekler. Tanımlayıcı ad imzalaması ad benzersizliğini doğrulamaya, ad sahtekarlığını önlemeye ve bir referans çözüldüğünde çağıranlara kimlik sağlamaya yardımcı olur.  
  
 Ancak, hiçbir güven düzeyini sağlayan güçlü bir ad ile ilişkilendirilmiş [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) önemli. İki imzalama aracı, bir yayımcının kimliğini üçüncü taraf bir yetkiliye kanıtlamasını ve bir sertifika almasını gerektirir. Bu sertifika ardından dosyanıza katıştırılır ve bir yönetici tarafından kodunuzun orijinalliğine güvenip güvenmemeye karar vermek için kullanılabilir.  
  
 Güçlü bir ad ve kullanılarak oluşturulan bir dijital imza verebilirsiniz [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) bir derleme veya kullanabilirsiniz tek başına. İki imzalama aracı aynı anda yalnızca tek bir dosya imzalayabilir; bir çoklu dosya derlemesi için derleme bildirimini içeren dosyayı imzalarsınız. Tanımlayıcı ad içeren derleme bildirimi dosyasında depolanır, ancak bir imza kullanılarak oluşturulan [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) ayrılmış bir yuva derleme bildirimi içeren taşınabilir yürütülebilir (PE) dosyasında depolanır. Kullanarak bir derlemenin imzalama [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) (veya ile güçlü bir ad olmadan) kullanılabilir dayanan bir güven hiyerarşisi zaten varsa[SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) imzalar, oluşturulan veya ilkeniz yalnızca anahtar bölümü kullanır ve bir güven zinciri denetlemez.  
  
> [!NOTE]
>  Bir derleme üzerinde hem tanımlayıcı ad hem de bir imzalama aracı imzası kullanırken, tanımlayıcı ad önce atanmalıdır.  
  
 Ortak dil çalışma zamanı bir karma doğrulaması da gerçekleştirir; derleme bildirimi derlemeyi oluşturan tüm dosyaların listesini, her dosyanın bildirim oluşturulduğu zamanki karması ile birlikte içerir. Dosyaların her biri yüklenirken, içindekilerin karması alınır ve bildirimde saklanan karma değeriyle karşılaştırılır. Eğer iki karma eşleşmezse, derleme yüklemesi başarısız olur.  
  
 Güçlü adlandırma ve kullanarak imzalama çünkü [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) bütünlüğünü garanti derleme kanıt, iki yöntemden birini kod erişimi güvenlik ilkesi temel alabilir. Güçlü adlandırma ve kullanarak imzalama [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) dijital imzalar ve sertifikalar ile bütünlüğü garanti. Belirtilen tüm teknolojileri — karma doğrulama, güçlü adlandırma ve kullanarak imzalama [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md)— birlikte derleme herhangi bir şekilde değiştirilmediğini emin olmak için çalışır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanımlayıcı adlı derlemeler](../../../docs/framework/app-domains/strong-named-assemblies.md)  
 [Ortak dil çalışma zamanı derlemeleri](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md)
