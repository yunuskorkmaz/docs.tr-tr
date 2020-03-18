---
title: Derleme güvenliği hakkında dikkate alınması gerekenler
ms.date: 08/20/2019
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
ms.openlocfilehash: 77c9f9131b556e0b8fa639cd723bf1ca8cd6602e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73972302"
---
# <a name="assembly-security-considerations"></a>Derleme güvenliği hakkında dikkate alınması gerekenler
Bir derleme oluşturduğunuzda, derlemenin çalışması için gereken izinler kümesini belirtebilirsiniz. Bir derlemeye belirli izinlerin verilip verilmediği kanıta göre belirlenir.  
  
 Kanıtın kullanıldığı iki farklı yol vardır:  
  
- Giriş kanıtı yükleyici tarafından toplanan kanıtla birleştirilerek ilke çözümlemesi için kullanılacak olan son kanıt kümesini oluşturur. Bu semantik kullanan yöntemler **Assembly.Load,** **Assembly.LoadFrom**ve **Activator.CreateInstance**içerir.  
  
- Giriş kanıtı, ilke çözümlemesi için kullanılan son kanıt kümesi olarak değiştirilmeden kullanılır. Bu anlamsal kullanan yöntemler **Assembly.Load(bayt[])** ve **AppDomain.DefineDynamicAssembly()** içerir.  
  
  İsteğe bağlı izinler, derlemenin çalışacağı bilgisayarda ayarlanan [güvenlik ilkesi](../../framework/misc/code-access-security-basics.md) tarafından verilebilir. Kodunuzun tüm olası güvenlik özel durumlarını işlemesini istiyorsanız, aşağıdakilerden birini yapabilirsiniz:  
  
- Kodunuzun sahip olması gereken tüm izinler için bir izin isteği ekleyin ve izinler verilmezse gerçekleşecek yükleme zamanı hatasını önden işleyin.  
  
- Kodunuzun ihtiyacı olabilecek izinleri almak için bir izin isteği kullanmayın, ancak izinler verilmezse oluşacak güvenlik özel durumlarını işlemeye hazır olun.  
  
  > [!NOTE]
  > Güvenlik karmaşık bir alandır ve pek çok seçeneğiniz vardır. Daha fazla bilgi için [Temel Güvenlik Kavramları'na](../../standard/security/key-security-concepts.md)bakın.  
  
 Yükleme zamanında derlemenin kanıtı güvenlik ilkesine giriş olarak kullanılır. Güvenlik ilkesi, kuruluş ve bilgisayar yöneticisinin yanı sıra kullanıcı ilke ayarları tarafından belirlenir ve yürütüldüklerinde tüm yönetilen kodlara verilen izinler kümesini belirler. Güvenlik ilkesi derlemenin yayımcısı için (imzalama aracıyla oluşturulmuş bir imzaya sahipse), derlemenin indirildiği Web sitesi ve bölge için (Internet Explorer terimiyle) veya derlemenin tanımlayıcı adı için belirlenebilir. Örneğin bir bilgisayarın yöneticisi, bir Web sitesinden indirilen ve belirli bir yazılım şirketi tarafından imzalanan tüm kodların bir bilgisayardaki veritabanına erişmesine izin veren, ancak bilgisayarın diskine yazmasına izin vermeyen bir güvenlik ilkesi belirleyebilir.  
  
## <a name="strong-named-assemblies-and-signing-tools"></a>Güçlü adlandırılmış derlemeler ve imzalama araçları  

 > [!WARNING]
 > Güvenlik için güçlü isimlere güvenmeyin. Yalnızca benzersiz bir kimlik sağlarlar.

 Bir derlemeyi iki farklı ama tamamlayıcı şekilde imzalayabilirsiniz: güçlü bir adla veya [SignTool.exe (Sign Tool)](../../framework/tools/signtool-exe.md)kullanarak. Güçlü bir ada sahip bir derlemeyi imzalamak, derleme bildirimini içeren dosyaya ortak anahtar şifrelemesi ekler. Tanımlayıcı ad imzalaması ad benzersizliğini doğrulamaya, ad sahtekarlığını önlemeye ve bir referans çözüldüğünde çağıranlara kimlik sağlamaya yardımcı olur.  
  
 Hiçbir güven düzeyi [SignTool.exe (Sign Tool)](../../framework/tools/signtool-exe.md) önemli kılan güçlü bir ad ile ilişkilidir. İki imzalama aracı, bir yayımcının kimliğini üçüncü taraf bir yetkiliye kanıtlamasını ve bir sertifika almasını gerektirir. Bu sertifika ardından dosyanıza katıştırılır ve bir yönetici tarafından kodunuzun orijinalliğine güvenip güvenmemeye karar vermek için kullanılabilir.  
  
 [SignTool.exe (Sign Tool)](../../framework/tools/signtool-exe.md) kullanılarak oluşturulan güçlü bir adı ve dijital imzayı bir derlemeye verebilir veya tek başına kullanabilirsiniz. İki imzalama aracı aynı anda yalnızca tek bir dosya imzalayabilir; bir çoklu dosya derlemesi için derleme bildirimini içeren dosyayı imzalarsınız. Montaj bildirimini içeren dosyada güçlü bir ad depolanır, ancak [SignTool.exe (İşaret Aracı)](../../framework/tools/signtool-exe.md) kullanılarak oluşturulan bir imza, derleme bildirimini içeren taşınabilir yürütülebilir (PE) dosyasında ayrılmış bir yuvada depolanır. [SignTool.exe (İşaret Aracı)](../../framework/tools/signtool-exe.md) kullanarak bir derlemenin imzalanması, [SignTool.exe (Sign Tool)](../../framework/tools/signtool-exe.md) oluşturulan imzalara dayanan bir güven hiyerarşiniz olduğunda veya ilkeniz yalnızca anahtar kısmını kullandığında ve bir güven zincirini denetlemediğinde (güçlü bir adla veya güçlü bir ad olmadan) kullanılabilir.  
  
> [!NOTE]
> Bir derleme üzerinde hem tanımlayıcı ad hem de bir imzalama aracı imzası kullanırken, tanımlayıcı ad önce atanmalıdır.  
  
 Ortak dil çalışma zamanı bir karma doğrulaması da gerçekleştirir; derleme bildirimi derlemeyi oluşturan tüm dosyaların listesini, her dosyanın bildirim oluşturulduğu zamanki karması ile birlikte içerir. Dosyaların her biri yüklenirken, içindekilerin karması alınır ve bildirimde saklanan karma değeriyle karşılaştırılır. Eğer iki karma eşleşmezse, derleme yüklemesi başarısız olur.  
  
 [SignTool.exe (Sign Tool)](../../framework/tools/signtool-exe.md) kullanarak güçlü adlandırma ve imzalama bütünlüğü garanti ettiği için, kod erişim güvenliği ilkesini bu iki derleme kanıtı biçimine dayandırabilirsiniz. [SignTool.exe (Sign Tool)](../../framework/tools/signtool-exe.md) kullanarak güçlü adlandırma ve imzalama, dijital imzalar ve sertifikalar aracılığıyla bütünlüğü garanti eder. Belirtilen tüm teknolojiler-karma doğrulama, güçlü adlandırma ve [SignTool.exe (Sign Tool)](../../framework/tools/signtool-exe.md)kullanarak imzalama —derlemenin herhangi bir şekilde değiştirilmediğinden emin olmak için birlikte çalışır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güçlü adlandırılmış derlemeler](strong-named.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
- [SignTool.exe (İmza Aracı)](../../framework/tools/signtool-exe.md)
