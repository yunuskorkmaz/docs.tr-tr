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
ms.openlocfilehash: 0f6f6fa8afe2e4aaea6e9f2b96329542b7fe5292
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607688"
---
# <a name="assembly-security-considerations"></a>Derleme Güvenliği Konuları
<a name="top"></a> Bir derleme oluşturduğunuzda, derlemenin çalışması için gerekli izinler kümesi belirtebilirsiniz. Bir derlemeye belirli izinlerin verilip verilmediği kanıta göre belirlenir.  
  
 Kanıtın kullanıldığı iki farklı yol vardır:  
  
- Giriş kanıtı yükleyici tarafından toplanan kanıtla birleştirilerek ilke çözümlemesi için kullanılacak olan son kanıt kümesini oluşturur. Bu semantiği kullanan yöntemlerden **Assembly.Load**, **Assembly.LoadFrom**, ve **Activator.CreateInstance**.  
  
- Giriş kanıtı, ilke çözümlemesi için kullanılan son kanıt kümesi olarak değiştirilmeden kullanılır. Bu semantiği kullanan yöntemlerden **Assembly.Load(byte[])** ve **AppDomain.DefineDynamicAssembly()**.  
  
 Tarafından isteğe bağlı izinler verilebilir [Güvenlik İlkesi](../../../docs/framework/misc/code-access-security-basics.md) derlemenin çalışacağı bilgisayarda ayarlayın. Kodunuzun tüm olası güvenlik özel durumlarını işlemesini istiyorsanız, aşağıdakilerden birini yapabilirsiniz:  
  
- Kodunuzun sahip olması gereken tüm izinler için bir izin isteği ekleyin ve izinler verilmezse gerçekleşecek yükleme zamanı hatasını önden işleyin.  
  
- Kodunuzun ihtiyacı olabilecek izinleri almak için bir izin isteği kullanmayın, ancak izinler verilmezse oluşacak güvenlik özel durumlarını işlemeye hazır olun.  
  
    > [!NOTE]
    >  Güvenlik karmaşık bir alandır ve pek çok seçeneğiniz vardır. Daha fazla bilgi için [temel güvenlik kavramları](../../../docs/standard/security/key-security-concepts.md).  
  
 Yükleme zamanında derlemenin kanıtı güvenlik ilkesine giriş olarak kullanılır. Güvenlik ilkesi, kuruluş ve bilgisayar yöneticisinin yanı sıra kullanıcı ilke ayarları tarafından belirlenir ve yürütüldüklerinde tüm yönetilen kodlara verilen izinler kümesini belirler. Güvenlik ilkesi derlemenin yayımcısı için (imzalama aracıyla oluşturulmuş bir imzaya sahipse), derlemenin indirildiği Web sitesi ve bölge için (Internet Explorer terimiyle) veya derlemenin tanımlayıcı adı için belirlenebilir. Örneğin bir bilgisayarın yöneticisi, bir Web sitesinden indirilen ve belirli bir yazılım şirketi tarafından imzalanan tüm kodların bir bilgisayardaki veritabanına erişmesine izin veren, ancak bilgisayarın diskine yazmasına izin vermeyen bir güvenlik ilkesi belirleyebilir.  
  
## <a name="strong-named-assemblies-and-signing-tools"></a>Katı Ada Sahip Derlemeler ve İmzalama Araçları  

 > [!WARNING]
 > Güvenlik için tanımlayıcı adlar güvenmeyin. Benzersiz bir kimliğe sağlarlar.

 Bir derlemeyi iki farklı ancak tamamlayıcı şekilde imzalayabilirsiniz: katı bir adla veya kullanarak [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md). Bir derlemeyi katı bir adla imzalamak, dosyaya derleme bildirimini içeren ortak anahtar şifrelemesi ekler. Tanımlayıcı ad imzalaması ad benzersizliğini doğrulamaya, ad sahtekarlığını önlemeye ve bir referans çözüldüğünde çağıranlara kimlik sağlamaya yardımcı olur.  
  
 Hiçbir güven düzeyi sağlayan bir tanımlayıcı ad ile ilişkilendirilen [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) önemli. İki imzalama aracı, bir yayımcının kimliğini üçüncü taraf bir yetkiliye kanıtlamasını ve bir sertifika almasını gerektirir. Bu sertifika ardından dosyanıza katıştırılır ve bir yönetici tarafından kodunuzun orijinalliğine güvenip güvenmemeye karar vermek için kullanılabilir.  
  
 Hem bir tanımlayıcı ad hem de kullanılarak oluşturulan bir dijital imza verebilirsiniz [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) bir derlemeye veya kullanabilirsiniz tek başına. İki imzalama aracı aynı anda yalnızca tek bir dosya imzalayabilir; bir çoklu dosya derlemesi için derleme bildirimini içeren dosyayı imzalarsınız. Tanımlayıcı ad derleme bildirimini içeren dosyada saklanır, ancak kullanarak oluşturulan bir imza [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) derleme bildirimini içeren taşınabilir yürütülebilir (PE) dosyanın içinde ayrılmış bir bölümde depolanır. Kullanarak bir derlemeyi imzalamak [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) (ile veya bir tanımlayıcı ad olmadan) kullanılabilir dayanan bir güven hiyerarşisine zaten varsa[SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) üretilen imzaları veya ne zaman ilkeniz yalnızca anahtar bölümünü kullanıp güven zinciri denetlemez.  
  
> [!NOTE]
>  Bir derleme üzerinde hem tanımlayıcı ad hem de bir imzalama aracı imzası kullanırken, tanımlayıcı ad önce atanmalıdır.  
  
 Ortak dil çalışma zamanı bir karma doğrulaması da gerçekleştirir; derleme bildirimi derlemeyi oluşturan tüm dosyaların listesini, her dosyanın bildirim oluşturulduğu zamanki karması ile birlikte içerir. Dosyaların her biri yüklenirken, içindekilerin karması alınır ve bildirimde saklanan karma değeriyle karşılaştırılır. Eğer iki karma eşleşmezse, derleme yüklemesi başarısız olur.  
  
 Strong adlandırma ve kullanarak imzalama çünkü [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) bütünlüğü bu iki derleme kanıtı üzerinde kod erişim güvenlik ilkesini temel alabilir. Tanımlayıcı adlandırma ve kullanarak imzalama [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md) dijital imzalar ve sertifikalar aracılığıyla bütünlüğü garanti. Bahsedilen tüm teknolojiler — karma doğrulama, tanımlayıcı adlandırma ve kullanarak imzalama [SignTool.exe (imza aracı)](../../../docs/framework/tools/signtool-exe.md)— birlikte derlemenin hiçbir şekilde değiştirilmediğinden emin olmak için iş.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [SignTool.exe (İmza Aracı)](../../../docs/framework/tools/signtool-exe.md)
