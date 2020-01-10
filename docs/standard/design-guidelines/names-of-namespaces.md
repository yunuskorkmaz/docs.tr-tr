---
title: Ad Alanlarının Adları
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 0678f695e3ae7c40660031862c9073a21fd72491
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709237"
---
# <a name="names-of-namespaces"></a>Ad Alanlarının Adları
Diğer adlandırma kılavuzlarında olduğu gibi, ad alanlarını Adlandırmanın amacı, programlama çerçevesini kullanarak, ad alanının içeriğinin büyük olasılıkla ne olduğunu hemen bilmenin ne kadar anlaşılır olduğunu oluşturmaktır. Aşağıdaki şablon ad alanlarını adlandırmak için genel kuralı belirtir:  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 Aşağıda örnekler verilmiştir:  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ DO** önek ad alanı adları ile aynı ada sahip öğesinden farklı şirketler ad alanlarını önlemek için bir şirket adı.  
  
 **✓ DO** ad alanı adı ikinci düzeyde kararlı ve sürüm bağımsız ürün adı kullanın.  
  
 **X DO NOT** grup adlarını kuruluşlar içinde kısa süreli olma eğilimindedir için kuruluş hiyerarşileri temel olarak ad alanı hiyerarşileri adları kullanın. İlgili teknolojilerin grupları etrafında ad alanlarının hiyerarşisini düzenleyin.  
  
 **✓ DO** PascalCasing ve ayrı ad alanı bileşenler süreleriyle kullanır (örn., `Microsoft.Office.PowerPoint`). Markanız geleneksel olmayan büyük harfe kullanıyorsa, normal ad alanı büyük küçük harfe göre farklılık gösterir olsa da markanız tarafından tanımlanan büyük/küçük harfleri izlemeniz gerekir.  
  
 **✓ CONSIDER** uygun olan yerlerde çoğul ad alanı adlarını kullanarak.  
  
 Örneğin, `System.Collection`yerine `System.Collections` kullanın. Ancak, marka adları ve kısaltmalar bu kuralın istisnalardır. Örneğin, `System.IOs`yerine `System.IO` kullanın.  
  
 **X DO NOT** bu ad alanında bir ad alanı ve türü için aynı adı kullanın.  
  
 Örneğin, `Debug` ad alanı adı olarak kullanmayın ve ayrıca aynı ad alanında `Debug` adlı bir sınıf sağlayın. Çeşitli derleyiciler, bu tür türlerin tam nitelikli olmasını gerektirir.  
  
### <a name="namespaces-and-type-name-conflicts"></a>Ad alanları ve tür adı çakışmaları  
 **X DO NOT** genel tür adları gibi tanıtmak `Element`, `Node`, `Log`, ve `Message`.  
  
 Bunu yapmanın çok büyük bir olasılığı, yaygın senaryolarda tür adı çakışmalarına yol açacaktır. Genel tür adlarını (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`) nitelemeniz gerekir.  
  
 Farklı ad alanları kategorileri için tür adı çakışmalarını önlemeye yönelik özel yönergeler vardır.  
  
- **Uygulama modeli ad alanları**  
  
     Tek bir uygulama modeline ait olan ad alanları birlikte çok sık kullanılır, ancak bunlar, diğer uygulama modelleriyle ilgili ad alanları ile neredeyse hiç kullanılmaz. Örneğin, <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı <xref:System.Web.UI?displayProperty=nameWithType> ad alanıyla birlikte çok seyrek kullanılır. Aşağıda, iyi bilinen uygulama modeli ad alanı gruplarının listesi verilmiştir:  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X DO NOT** tek bir uygulama modeli içindeki ad alanlarında türleri için aynı adı verin.  
  
     Örneğin, <xref:System.Web.UI?displayProperty=nameWithType> ad alanı zaten `Page`adlı bir tür içerdiğinden, <xref:System.Web.UI.Adapters?displayProperty=nameWithType> ad alanına `Page` adlı bir tür eklemeyin.  
  
- **Altyapı ad alanları**  
  
     Bu grup, ortak uygulamaların geliştirilmesi sırasında nadiren içeri aktarılan ad alanlarını içerir. Örneğin, `.Design` ad alanları genellikle programlama araçları geliştirilirken kullanılır. Bu ad alanlarında bulunan çakışmaları önleme kritik değildir.  
  
- **Çekirdek ad alanları**  
  
     Çekirdek ad alanları, uygulama modellerinin ad alanları ve altyapı ad alanları hariç tüm `System` ad alanlarını içerir. Temel ad alanları, diğerleri, `System`, `System.IO`, `System.Xml`ve `System.Net`arasında yer alır.  
  
     **X DO NOT** verin çekirdek ad alanlarında herhangi bir türü ile çakışan adları türleri.  
  
     Örneğin, hiçbir `Stream` tür adı olarak kullanmayın. Yaygın olarak kullanılan bir tür olan <xref:System.IO.Stream?displayProperty=nameWithType>ile çakışır.  
  
- **Teknoloji ad alanı grupları**  
  
     Bu kategori, `Microsoft.Build.Utilities` ve `Microsoft.Build.Tasks`gibi aynı ilk iki ad alanı düğümüne sahip tüm ad alanlarını içerir `(<Company>.<Technology>*`). Tek bir teknolojiye ait olan türlerin birbirleriyle çakışmaması önemlidir.  
  
     **X DO NOT** tek bir teknoloji içindeki diğer türleriyle çakışabilir tür adları atayın.  
  
     **X DO NOT** (teknoloji uygulama modeli ile kullanılmak üzere tasarlanmamıştır sürece) teknolojisi ad alanlarında türleri ve bir uygulama model ad arasındaki ad çakışmalarının türü tanıtır.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
