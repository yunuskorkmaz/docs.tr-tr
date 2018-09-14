---
title: Ad alanlarının adları
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
ms.openlocfilehash: 6d68966f60c5039fd67195a03facc1586b9ed154
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591730"
---
# <a name="names-of-namespaces"></a>Ad alanlarının adları
Olarak diğer adlandırma kuralları ile hedef ad alanları adlandırırken yeterli netlik ad alanı içeriğini olma olasılığı nedir hemen bilmek framework kullanarak programcısı için oluşturuyor. Aşağıdaki şablonu genel bir kural ad alanlarını adlandırma belirtir:  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 Örnekler şunlardır:  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ DO** önek ad alanı adları ile aynı ada sahip öğesinden farklı şirketler ad alanlarını önlemek için bir şirket adı.  
  
 **✓ DO** ad alanı adı ikinci düzeyde kararlı ve sürüm bağımsız ürün adı kullanın.  
  
 **X DO NOT** grup adlarını kuruluşlar içinde kısa süreli olma eğilimindedir için kuruluş hiyerarşileri temel olarak ad alanı hiyerarşileri adları kullanın. İlgili teknolojiler gruplarının çevresinde ad alanları hiyerarşisi düzenleyin.  
  
 **✓ DO** PascalCasing ve ayrı ad alanı bileşenler süreleriyle kullanır (örn., `Microsoft.Office.PowerPoint`). Markanızı nontraditional büyük/küçük harf içeriyorsa, bu normal bir ad alanı büyük küçük harflerini öğesinden farklılık göstermesi bile markanızı tarafından tanımlanan büyük/küçük harf izlemelidir.  
  
 **✓ CONSIDER** uygun olan yerlerde çoğul ad alanı adlarını kullanarak.  
  
 Örneğin, `System.Collections` yerine `System.Collection`. Bu kuralın istisnası, marka adları ve kısaltmalar ancak uygulanır. Örneğin, `System.IO` yerine `System.IOs`.  
  
 **X DO NOT** bu ad alanında bir ad alanı ve türü için aynı adı kullanın.  
  
 Örneğin, kullanmayın `Debug` bir ad alanı olarak adlandırın ve sonra da adlı bir sınıf sağlayın `Debug` ad. Bazı derleyiciler gibi türler tam olmasını gerektirir.  
  
### <a name="namespaces-and-type-name-conflicts"></a>Ad alanları ve tür adı çakışıyor  
 **X DO NOT** genel tür adları gibi tanıtmak `Element`, `Node`, `Log`, ve `Message`.  
  
 Ad önünü açacak yapılması, ortak senaryolar çakışıyor çok yüksek bir olasılık yoktur. Genel tür adları nitelemeniz (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).  
  
 Belirli ad alanları farklı kategorileri için tür adı çakışmalarını önleme ilkeleri vardır.  
  
-   **Uygulama modeli ad alanları**  
  
     Tek bir uygulama modeline ait olan ad alanları sıklıkla birlikte kullanılır, ancak diğer uygulama modellerini ad alanları ile neredeyse hiçbir zaman kullanılır. Örneğin, <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı ile birlikte kullanılan nadiren <xref:System.Web.UI?displayProperty=nameWithType> ad alanı. İyi bilinen uygulama modeli ad gruplarının listesi verilmiştir:  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X DO NOT** tek bir uygulama modeli içindeki ad alanlarında türleri için aynı adı verin.  
  
     Örneğin, adlı bir tür eklemeyin `Page` için <xref:System.Web.UI.Adapters?displayProperty=nameWithType> ad alanı, çünkü <xref:System.Web.UI?displayProperty=nameWithType> ad alanını adlı bir tür zaten var. `Page`.  
  
-   **Altyapı ad alanları**  
  
     Bu grup, nadiren uygulamaların ortak bir geliştirme sırasında içeri aktarılan ad alanlarını içerir. Örneğin, `.Design` ad alanları programlama geliştirme araçları oluştururken temel olarak kullanılır. Bu ad alanlarında türleri ile çakışmaları önleme önemli değildir.  
  
-   **Temel ad alanları**  
  
     Temel ad alanlarını dahil tüm `System` ad alanları, uygulama modellerin ad alanları ve altyapı ad alanlarını hariç. Temel ad alanlarını içeren diğerleriyle birlikte, `System`, `System.IO`, `System.Xml`, ve `System.Net`.  
  
     **X DO NOT** verin çekirdek ad alanlarında herhangi bir türü ile çakışan adları türleri.  
  
     Örneğin, hiçbir zaman kullanmayın `Stream` olarak bir tür adı. İle çakışmadığı <xref:System.IO.Stream?displayProperty=nameWithType>, çok kullanılan tür.  
  
-   **Teknoloji ad grupları**  
  
     Bu kategori, tüm ad alanları ile aynı ilk iki ad alanı düğümleri içerir `(<Company>.<Technology>*`), aşağıdakiler gibi `Microsoft.Build.Utilities` ve `Microsoft.Build.Tasks`. Türler için tek bir teknoloji ait birbiriyle çakışmadığından emin önemlidir.  
  
     **X DO NOT** tek bir teknoloji içindeki diğer türleriyle çakışabilir tür adları atayın.  
  
     **X DO NOT** (teknoloji uygulama modeli ile kullanılmak üzere tasarlanmamıştır sürece) teknolojisi ad alanlarında türleri ve bir uygulama model ad arasındaki ad çakışmalarının türü tanıtır.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
