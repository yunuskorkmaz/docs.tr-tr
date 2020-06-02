---
title: Ad Alanlarının Adları
description: .NET kitaplıklarını genişleten ve bunlarla etkileşime geçen kitaplıklar tasarlamanın bir parçası olarak ad alanlarını adlandırmak için bu yönergeleri kullanın.
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: e435e0281165b4a9f12bbccbeb10401b57375dcb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290207"
---
# <a name="names-of-namespaces"></a>Ad Alanlarının Adları
Diğer adlandırma kılavuzlarında olduğu gibi, ad alanlarını Adlandırmanın amacı, programlama çerçevesini kullanarak, ad alanının içeriğinin büyük olasılıkla ne olduğunu hemen bilmenin ne kadar anlaşılır olduğunu oluşturmaktır. Aşağıdaki şablon ad alanlarını adlandırmak için genel kuralı belirtir:

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 Aşağıda örnekleri verilmektedir:

 `Fabrikam.Math` `Litware.Security`

 farklı şirketlerin ad alanlarının aynı ada sahip olmasını engellemek için, önek ad alanı adlarını bir şirket adıyla ✔️.

 ✔️ bir ad alanı adının ikinci düzeyinde kararlı, sürümden bağımsız bir ürün adı kullanın.

 ❌Kurumların içindeki Grup adları kısa süreli olmaya eğiltiğinden, kuruluş hiyerarşilerini ad alanı hiyerarşilerindeki adların temeli olarak kullanmayın. İlgili teknolojilerin grupları etrafında ad alanlarının hiyerarşisini düzenleyin.

 ✔️ Pascalbüyük harfleri kullanır ve ad alanı bileşenlerini noktalarla ayırın (ör. `Microsoft.Office.PowerPoint` ). Markanız geleneksel olmayan büyük harfe kullanıyorsa, normal ad alanı büyük küçük harfe göre farklılık gösterir olsa da markanız tarafından tanımlanan büyük/küçük harfleri izlemeniz gerekir.

 ✔️ Çoğul ad alanı adlarını kullanmayı göz önünde bulundurun.

 Örneğin `System.Collection` yerine `System.Collections` kullanın. Ancak, marka adları ve kısaltmalar bu kuralın istisnalardır. Örneğin `System.IOs` yerine `System.IO` kullanın.

 ❌Ad alanı için aynı adı ve bu ad alanındaki türü kullanmayın.

 Örneğin, `Debug` ad alanı adı olarak kullanmayın ve ayrıca `Debug` aynı ad alanında adlı bir sınıf sağlayın. Çeşitli derleyiciler, bu tür türlerin tam nitelikli olmasını gerektirir.

### <a name="namespaces-and-type-name-conflicts"></a>Ad alanları ve tür adı çakışmaları
 ❌,, Ve gibi genel tür adları sunmaz `Element` `Node` `Log` `Message` .

 Bunu yapmanın çok büyük bir olasılığı, yaygın senaryolarda tür adı çakışmalarına yol açacaktır. Genel tür adlarını (,,,) nitelemeniz gerekir `FormElement` `XmlNode` `EventLog` `SoapMessage` .

 Farklı ad alanları kategorileri için tür adı çakışmalarını önlemeye yönelik özel yönergeler vardır.

- **Uygulama modeli ad alanları**

     Tek bir uygulama modeline ait olan ad alanları birlikte çok sık kullanılır, ancak bunlar, diğer uygulama modelleriyle ilgili ad alanları ile neredeyse hiç kullanılmaz. Örneğin, ad alanı, <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanıyla birlikte çok seyrek kullanılır <xref:System.Web.UI?displayProperty=nameWithType> . Aşağıda, iyi bilinen uygulama modeli ad alanı gruplarının listesi verilmiştir:

     `System.Windows*` `System.Web.UI*`

     ❌Tek bir uygulama modelinde ad alanlarında bulunan türlere aynı adı vermeyin.

     Örneğin, ad alanı `Page` <xref:System.Web.UI.Adapters?displayProperty=nameWithType> <xref:System.Web.UI?displayProperty=nameWithType> zaten adlı bir tür içerdiğinden ad alanına adlı bir tür eklemeyin `Page` .

- **Altyapı ad alanları**

     Bu grup, ortak uygulamaların geliştirilmesi sırasında nadiren içeri aktarılan ad alanlarını içerir. Örneğin, `.Design` ad alanları genellikle programlama araçları geliştirilirken kullanılır. Bu ad alanlarında bulunan çakışmaları önleme kritik değildir.

- **Çekirdek ad alanları**

     Çekirdek ad alanları `System` , uygulama modellerinin ad alanları ve altyapı ad alanları hariç tüm ad alanlarını içerir. Çekirdek ad alanları, diğerleri,,, ve arasında bulunur `System` `System.IO` `System.Xml` `System.Net` .

     ❌Çekirdek ad alanlarında herhangi bir türle çakışabilecek tür adları vermeyin.

     Örneğin, hiçbir koşulda `Stream` tür adı olarak kullanmayın. <xref:System.IO.Stream?displayProperty=nameWithType>Yaygın olarak kullanılan bir tür ile çakışır.

- **Teknoloji ad alanı grupları**

     Bu kategori, ve gibi aynı ilk iki ad alanı düğümüne sahip tüm ad alanlarını içerir `(<Company>.<Technology>*` `Microsoft.Build.Utilities` `Microsoft.Build.Tasks` . Tek bir teknolojiye ait olan türlerin birbirleriyle çakışmaması önemlidir.

     ❌Tek bir teknoloji içindeki diğer türlerle çakışacak tür adları atamayın.

     ❌Teknoloji ad alanları ve uygulama modeli ad alanındaki türler arasında tür adı çakışmalarını tanıtmayın (teknoloji uygulama modeliyle kullanılmak amaçlanmamışsa).

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Adlandırma yönergeleri](naming-guidelines.md)
