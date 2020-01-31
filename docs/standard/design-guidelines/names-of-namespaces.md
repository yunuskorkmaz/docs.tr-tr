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
ms.openlocfilehash: 52fee0dfaff284c2c1a6afcb8aa7530c28a60d65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744145"
---
# <a name="names-of-namespaces"></a>Ad Alanlarının Adları
Diğer adlandırma kılavuzlarında olduğu gibi, ad alanlarını Adlandırmanın amacı, programlama çerçevesini kullanarak, ad alanının içeriğinin büyük olasılıkla ne olduğunu hemen bilmenin ne kadar anlaşılır olduğunu oluşturmaktır. Aşağıdaki şablon ad alanlarını adlandırmak için genel kuralı belirtir:

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 Aşağıda örnekler verilmiştir:

 `Fabrikam.Math` `Litware.Security`

 farklı şirketlerin ad alanlarının aynı ada sahip olmasını engellemek için, önek ad alanı adlarını bir şirket adıyla ✔️.

 ✔️ bir ad alanı adının ikinci düzeyinde kararlı, sürümden bağımsız bir ürün adı kullanın.

 ❌, şirketler içindeki Grup adları kısa süreli olmaya eğiltiğinden, ad alanı hiyerarşilerindeki adların temeli olarak kurumsal hiyerarşileri kullanmayın. İlgili teknolojilerin grupları etrafında ad alanlarının hiyerarşisini düzenleyin.

 ✔️ Pascalbüyük harfleri kullanır ve ad alanı bileşenlerini noktalarla ayırın (örn. `Microsoft.Office.PowerPoint`). Markanız geleneksel olmayan büyük harfe kullanıyorsa, normal ad alanı büyük küçük harfe göre farklılık gösterir olsa da markanız tarafından tanımlanan büyük/küçük harfleri izlemeniz gerekir.

 ✔️ Çoğul ad alanı adlarını kullanmayı göz önünde bulundurun.

 Örneğin, `System.Collection`yerine `System.Collections` kullanın. Ancak, marka adları ve kısaltmalar bu kuralın istisnalardır. Örneğin, `System.IOs`yerine `System.IO` kullanın.

 ❌ ad alanı için aynı adı ve bu ad alanındaki türü kullanmaz.

 Örneğin, `Debug` ad alanı adı olarak kullanmayın ve ayrıca aynı ad alanında `Debug` adlı bir sınıf sağlayın. Çeşitli derleyiciler, bu tür türlerin tam nitelikli olmasını gerektirir.

### <a name="namespaces-and-type-name-conflicts"></a>Ad alanları ve tür adı çakışmaları
 ❌ `Element`, `Node`, `Log`ve `Message`gibi genel tür adları sunmaz.

 Bunu yapmanın çok büyük bir olasılığı, yaygın senaryolarda tür adı çakışmalarına yol açacaktır. Genel tür adlarını (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`) nitelemeniz gerekir.

 Farklı ad alanları kategorileri için tür adı çakışmalarını önlemeye yönelik özel yönergeler vardır.

- **Uygulama modeli ad alanları**

     Tek bir uygulama modeline ait olan ad alanları birlikte çok sık kullanılır, ancak bunlar, diğer uygulama modelleriyle ilgili ad alanları ile neredeyse hiç kullanılmaz. Örneğin, <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı <xref:System.Web.UI?displayProperty=nameWithType> ad alanıyla birlikte çok seyrek kullanılır. Aşağıda, iyi bilinen uygulama modeli ad alanı gruplarının listesi verilmiştir:

     `System.Windows*` `System.Web.UI*`

     ❌, tek bir uygulama modeli içindeki ad alanlarında bulunan türlere aynı adı vermez.

     Örneğin, <xref:System.Web.UI?displayProperty=nameWithType> ad alanı zaten `Page`adlı bir tür içerdiğinden, <xref:System.Web.UI.Adapters?displayProperty=nameWithType> ad alanına `Page` adlı bir tür eklemeyin.

- **Altyapı ad alanları**

     Bu grup, ortak uygulamaların geliştirilmesi sırasında nadiren içeri aktarılan ad alanlarını içerir. Örneğin, `.Design` ad alanları genellikle programlama araçları geliştirilirken kullanılır. Bu ad alanlarında bulunan çakışmaları önleme kritik değildir.

- **Çekirdek ad alanları**

     Çekirdek ad alanları, uygulama modellerinin ad alanları ve altyapı ad alanları hariç tüm `System` ad alanlarını içerir. Temel ad alanları, diğerleri, `System`, `System.IO`, `System.Xml`ve `System.Net`arasında yer alır.

     ❌, çekirdek ad alanlarında herhangi bir türle çakışacak tür adları vermez.

     Örneğin, hiçbir `Stream` tür adı olarak kullanmayın. Yaygın olarak kullanılan bir tür olan <xref:System.IO.Stream?displayProperty=nameWithType>ile çakışır.

- **Teknoloji ad alanı grupları**

     Bu kategori, `Microsoft.Build.Utilities` ve `Microsoft.Build.Tasks`gibi aynı ilk iki ad alanı düğümüne sahip tüm ad alanlarını içerir `(<Company>.<Technology>*`). Tek bir teknolojiye ait olan türlerin birbirleriyle çakışmaması önemlidir.

     ❌, tek bir teknoloji içindeki diğer türlerle çakışacak tür adları atamayın.

     ❌, teknoloji ad alanları ve uygulama modeli ad alanındaki türler arasında tür adı çakışmaları sunmaz (teknoloji uygulama modeliyle kullanılmak amaçlanmamışsa).

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
