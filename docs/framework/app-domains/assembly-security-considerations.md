---
title: Derleme Güvenliği Konuları
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53b33bdc70f00d5c824d502043a69f4ee05acc71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927972"
---
# <a name="assembly-security-considerations"></a>Derleme Güvenliği Konuları
<a name="top"></a>Bir derleme oluşturduğunuzda, derlemenin çalışması için gereken bir izin kümesi belirtebilirsiniz. Bir derlemeye belirli izinlerin verilip verilmediği kanıta göre belirlenir.  
  
 Kanıtın kullanıldığı iki farklı yol vardır:  
  
- Giriş kanıtı yükleyici tarafından toplanan kanıtla birleştirilerek ilke çözümlemesi için kullanılacak olan son kanıt kümesini oluşturur. Bu anlam kullanan Yöntemler **Assembly. Load**, **Assembly. LoadFrom**ve **Etkinleştirici. CreateInstance**' yı içerir.  
  
- Giriş kanıtı, ilke çözümlemesi için kullanılan son kanıt kümesi olarak değiştirilmeden kullanılır. Bu anlam kullanan Yöntemler **Assembly. Load (Byte [])** ve **AppDomain. DefineDynamicAssembly ()** içerir.  
  
 İsteğe bağlı izinler, derlemenin çalışacağı bilgisayarda ayarlanan [güvenlik ilkesi](../../../docs/framework/misc/code-access-security-basics.md) tarafından verilebilir. Kodunuzun tüm olası güvenlik özel durumlarını işlemesini istiyorsanız, aşağıdakilerden birini yapabilirsiniz:  
  
- Kodunuzun sahip olması gereken tüm izinler için bir izin isteği ekleyin ve izinler verilmezse gerçekleşecek yükleme zamanı hatasını önden işleyin.  
  
- Kodunuzun ihtiyacı olabilecek izinleri almak için bir izin isteği kullanmayın, ancak izinler verilmezse oluşacak güvenlik özel durumlarını işlemeye hazır olun.  
  
    > [!NOTE]
    > Güvenlik karmaşık bir alandır ve pek çok seçeneğiniz vardır. Daha fazla bilgi için bkz. [temel güvenlik kavramları](../../standard/security/key-security-concepts.md).  
  
 Yükleme zamanında derlemenin kanıtı güvenlik ilkesine giriş olarak kullanılır. Güvenlik ilkesi, kuruluş ve bilgisayar yöneticisinin yanı sıra kullanıcı ilke ayarları tarafından belirlenir ve yürütüldüklerinde tüm yönetilen kodlara verilen izinler kümesini belirler. Güvenlik ilkesi derlemenin yayımcısı için (imzalama aracıyla oluşturulmuş bir imzaya sahipse), derlemenin indirildiği Web sitesi ve bölge için (Internet Explorer terimiyle) veya derlemenin tanımlayıcı adı için belirlenebilir. Örneğin bir bilgisayarın yöneticisi, bir Web sitesinden indirilen ve belirli bir yazılım şirketi tarafından imzalanan tüm kodların bir bilgisayardaki veritabanına erişmesine izin veren, ancak bilgisayarın diskine yazmasına izin vermeyen bir güvenlik ilkesi belirleyebilir.  
  
## <a name="strong-named-assemblies-and-signing-tools"></a>Katı Ada Sahip Derlemeler ve İmzalama Araçları  

 > [!WARNING]
 > Güvenlik için tanımlayıcı adlara güvenmeyin. Yalnızca benzersiz bir kimlik sağlarlar.

 Bir derlemeyi iki farklı ancak tamamlayıcı şekilde imzalayabilirsiniz: bir tanımlayıcı ad ile veya [SignTool. exe (Imza aracı)](../../../docs/framework/tools/signtool-exe.md)kullanarak. Bir derlemeyi güçlü bir adla imzalamak, derleme bildirimini içeren dosyaya ortak anahtar şifrelemesi ekler. Tanımlayıcı ad imzalaması ad benzersizliğini doğrulamaya, ad sahtekarlığını önlemeye ve bir referans çözüldüğünde çağıranlara kimlik sağlamaya yardımcı olur.  
  
 Herhangi bir güven düzeyi, bir tanımlayıcı ad ile ilişkilendirilmediği için [SignTool. exe (Imza aracı)](../../../docs/framework/tools/signtool-exe.md) önemli olur. İki imzalama aracı, bir yayımcının kimliğini üçüncü taraf bir yetkiliye kanıtlamasını ve bir sertifika almasını gerektirir. Bu sertifika ardından dosyanıza katıştırılır ve bir yönetici tarafından kodunuzun orijinalliğine güvenip güvenmemeye karar vermek için kullanılabilir.  
  
 Bir derlemeye [SignTool. exe (Imza aracı)](../../../docs/framework/tools/signtool-exe.md) kullanılarak oluşturulmuş bir tanımlayıcı ad ve dijital imzaya sahip olabilir veya tek başına kullanabilirsiniz. İki imzalama aracı aynı anda yalnızca tek bir dosya imzalayabilir; bir çoklu dosya derlemesi için derleme bildirimini içeren dosyayı imzalarsınız. Tanımlayıcı ad, derleme bildirimini içeren dosyada depolanır, ancak [SignTool. exe (Imza aracı)](../../../docs/framework/tools/signtool-exe.md) kullanılarak oluşturulan bir imza, derleme bildirimini içeren taşınabilir ÇALıŞTıRıLABILIR (PE) dosyasında ayrılmış bir yuvaya depolanır. Bir derlemeyi SignTool. exe (imza [Aracı)](../../../docs/framework/tools/signtool-exe.md) kullanarak imzalama, zaten [SignTool. exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) tarafından oluşturulan imzaların kullanıldığı bir güven hiyerarşiniz varsa veya ilkeniz yalnızca anahtar kısmını kullandığında kullanılabilir (tanımlayıcı bir ad olmadan). ve bir güven zinciri denetlemez.  
  
> [!NOTE]
> Bir derleme üzerinde hem tanımlayıcı ad hem de bir imzalama aracı imzası kullanırken, tanımlayıcı ad önce atanmalıdır.  
  
 Ortak dil çalışma zamanı bir karma doğrulaması da gerçekleştirir; derleme bildirimi derlemeyi oluşturan tüm dosyaların listesini, her dosyanın bildirim oluşturulduğu zamanki karması ile birlikte içerir. Dosyaların her biri yüklenirken, içindekilerin karması alınır ve bildirimde saklanan karma değeriyle karşılaştırılır. Eğer iki karma eşleşmezse, derleme yüklemesi başarısız olur.  
  
 [SignTool. exe (Imza aracı)](../../../docs/framework/tools/signtool-exe.md) kullanarak tanımlayıcı adlandırma ve imzalama tutarlılığı garanti ettiğinden, bu iki derleme bulgusunda kod erişimi güvenlik ilkesi temel alabilirsiniz. [SignTool. exe (Imza aracı)](../../../docs/framework/tools/signtool-exe.md) kullanarak tanımlayıcı adlandırma ve imzalama, dijital imzalar ve sertifikalar aracılığıyla bütünlüğü garanti eder. Belirtilen tüm teknolojiler (karma doğrulama, tanımlayıcı adlandırma ve [SignTool. exe (Imza aracı)](../../../docs/framework/tools/signtool-exe.md)kullanılarak imzalama), derlemenin herhangi bir şekilde değiştirilmediğinden emin olmak için birlikte çalışır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [SignTool.exe (İmza Aracı)](../../../docs/framework/tools/signtool-exe.md)
