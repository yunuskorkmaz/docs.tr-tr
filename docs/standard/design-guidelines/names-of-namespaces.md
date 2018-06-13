---
title: Ad alanı adları
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e0b6c5ac60474cfe984b3802e880eb58b017722
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576438"
---
# <a name="names-of-namespaces"></a>Ad alanı adları
Olarak diğer adlandırma kuralları ile ad alanlarını adlandırırken hedef yeterli netlik hemen ad içeriği büyük olasılıkla ne olduğunu bilmeniz framework kullanarak programcı için oluşturuyor. Aşağıdaki şablonu ad alanları adlandırma genel kural belirtir:  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 Örnekleri aşağıda verilmiştir:  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ YAPMAK** önek ad alanı adları ile aynı ada sahip öğesinden farklı şirketler ad alanlarını önlemek için bir şirket adı.  
  
 **✓ YAPMAK** ad alanı adı ikinci düzeyde kararlı ve sürüm bağımsız ürün adı kullanın.  
  
 **X yok** grup adlarını kuruluşlar içinde kısa süreli olma eğilimindedir için kuruluş hiyerarşileri temel olarak ad alanı hiyerarşileri adları kullanın. İlgili teknolojiler grupları geçici ad alanları hiyerarşisi düzenleyin.  
  
 **✓ YAPMAK** PascalCasing ve ayrı ad alanı bileşenler süreleriyle kullanır (örn., `Microsoft.Office.PowerPoint`). Marka nontraditional büyük/küçük harf içeriyorsa, gelen normal ad büyük/küçük harf farklılık göstermesi olsa bile, marka tarafından tanımlanan büyük küçük harf izlemelisiniz.  
  
 **✓ DÜŞÜNÜN** uygun olan yerlerde çoğul ad alanı adlarını kullanarak.  
  
 Örneğin, `System.Collections` yerine `System.Collection`. Marka adlar ve kısaltmalar bu kuralın ancak durumlardır. Örneğin, `System.IO` yerine `System.IOs`.  
  
 **X yok** bu ad alanında bir ad alanı ve türü için aynı adı kullanın.  
  
 Örneğin, kullanmayın `Debug` bir ad alanı olarak adlandırın ve ayrıca adlı bir sınıf sağlayın `Debug` aynı ad alanında. Birkaç derleyicileri gibi türler tam olmasını gerektirir.  
  
### <a name="namespaces-and-type-name-conflicts"></a>Ad alanları ve türü ad çakışmaları  
 **X yok** genel tür adları gibi tanıtmak `Element`, `Node`, `Log`, ve `Message`.  
  
 Adı yazmaya yol açacaktır böylece ortak senaryolar çakışmaları çok büyük bir olasılıkla yoktur. Genel tür adları nitelemeniz (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).  
  
 Ad alanları farklı kategorileri için tür adı çakışmaları önleme için belirli yönergeler vardır.  
  
-   **Uygulama modeli ad alanları**  
  
     Neredeyse hiçbir zaman başka uygulama modelleri ad alanları ile kullanılan ancak tek bir uygulama modeline ait olan ad alanları çok sık birlikte kullanılır. Örneğin, <xref:System.Windows.Forms?displayProperty=nameWithType> ad ile birlikte kullanılan nadiren <xref:System.Web.UI?displayProperty=nameWithType> ad alanı. İyi bilinen uygulama modeli ad grupları listesi aşağıdadır:  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X yok** tek bir uygulama modeli içindeki ad alanlarında türleri için aynı adı verin.  
  
     Örneğin, adlı tür eklemeyin `Page` için <xref:System.Web.UI.Adapters?displayProperty=nameWithType> ad alanı, çünkü <xref:System.Web.UI?displayProperty=nameWithType> ad alanı zaten var. adlı tür `Page`.  
  
-   **Altyapı ad alanları**  
  
     Bu grup, nadiren ortak uygulamaları geliştirme sırasında içeri aktarılan ad alanları içerir. Örneğin, `.Design` ad alanları programlama geliştirme araçları, temel olarak kullanılır. Bu ad alanlarında türleri ile çakışmaları önleme kritik değildir.  
  
-   **Çekirdek ad alanları**  
  
     Çekirdek ad alanlarını dahil tüm `System` ad alanları, bir uygulama modelini ad alanları ve altyapı ad alanlarını hariç. Çekirdek ad alanlarını dahil, başka şeylerin yanı sıra `System`, `System.IO`, `System.Xml`, ve `System.Net`.  
  
     **X yok** verin çekirdek ad alanlarında herhangi bir türü ile çakışan adları türleri.  
  
     Örneğin, hiçbir zaman kullanmayın `Stream` bir tür adı olarak. İle çakışabilir <xref:System.IO.Stream?displayProperty=nameWithType>, bir çok kullanılan türü.  
  
-   **Teknoloji ad grupları**  
  
     Bu kategorideki tüm ad alanlarını aynı ilk iki ad alanı düğümlerle içeren `(<Company>.<Technology>*`), aşağıdaki gibi `Microsoft.Build.Utilities` ve `Microsoft.Build.Tasks`. Tek bir teknoloji ait türleri birbirleri ile çakışmadığını önemlidir.  
  
     **X yok** tek bir teknoloji içindeki diğer türleriyle çakışabilir tür adları atayın.  
  
     **X yok** (teknoloji uygulama modeli ile kullanılmak üzere tasarlanmamıştır sürece) teknolojisi ad alanlarında türleri ve bir uygulama model ad arasındaki ad çakışmalarının türü tanıtır.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
