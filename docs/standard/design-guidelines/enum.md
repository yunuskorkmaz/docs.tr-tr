---
title: Sabit Listesi Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: 3b24bfefd3edb0585e9c6369e9b8151b17151661
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741706"
---
# <a name="enum-design"></a>Sabit Listesi Tasarımı

Numaralandırmalar özel bir tür değer türüdür. İki tür numaralandırmalar vardır: basit numaralandırmalar ve bayrak Numaralandırmalar.

Basit numaralandırmalar küçük kapalı seçim kümelerini temsil eder. Basit sabit listesinin yaygın bir örneği bir renk kümesidir.

Bayrak numaralandırmalarında, sabit listesi değerlerinde bit düzeyinde işlemleri destekleyecek şekilde tasarlanmıştır. Flags numaralandırmasının ortak bir örneği, seçeneklerin listesidir.

✔️, parametreleri, özellikleri ve değer kümelerini temsil eden dönüş değerlerini kesin bir şekilde yazmak için enum kullanın.

✔️ statik sabitler yerine bir numaralandırma kullanmayı tercih edin.

❌, açık kümeler (örneğin, işletim sistemi sürümü, arkadaşlarınızın adları vb.) için bir sabit listesi kullanmaz.

❌, gelecekte kullanılmak üzere tasarlanan ayrılmış sabit listesi değerleri sağlamaz.

Daha sonraki bir aşamada mevcut sabit listesine her zaman bir değer ekleyebilirsiniz. Numaralandırmaların değerlerini ekleme hakkında daha fazla ayrıntı için bkz. [numaralandırmalar Için değer ekleme](#add_value) . Ayrılmış değerler yalnızca gerçek değerler kümesini Pollute ve Kullanıcı hatalarına neden olacak şekilde eğilimlidir.

❌, Numaralandırmaların tek bir değerle genel olarak kullanıma sunulmasını ÖNLEYIN.

C API 'Lerinde gelecekteki genişletilebilirliği sağlamaya yönelik yaygın bir uygulama, ayrılmış parametreleri Yöntem imzalarına eklemektir. Bu tür ayrılmış parametreler, tek bir varsayılan değer ile enum olarak ifade edilebilir. Bu, yönetilen API 'lerde yapılmamalıdır. Yöntem aşırı yüklemesi gelecekteki sürümlerde parametre eklenmesine izin verir.

❌ numaralandırmalarda Sentinel değerlerini dahil etmez.

Bazen Framework geliştiricilerine faydalı olsalar da, Sentinel değerleri Framework kullanıcılarına kafa karıştırıcı olur. Numaralandırıcılardan temsil edilen kümeden biri yerine sabit listesinin durumunu izlemek için kullanılırlar.

✔️ basit numaralandırmalar üzerinde sıfır değeri sağlar.

"None" gibi bir değer çağırmayı düşünün. Böyle bir değer bu sabit listesi için uygun değilse, sabit listesi için en yaygın varsayılan değere sıfır değeri atanmış olmalıdır.

✔️, aşağıdakilerden herhangi biri doğru olmadığı sürece bir sabit listesinin temel alınan türü olarak <xref:System.Int32> (çoğu programlama dilinde varsayılan değer) kullanmayı göz önünde bulundurun:

- Sabit listesi bir bayrak numaralandırıcıdır ve 32 ' den fazla bayrak veya daha fazlasını bekliyor olabilir.

- Temel alınan türün, farklı boyutlu numaralandırmalar bekleyen yönetilmeyen kodla daha kolay birlikte çalışabilirlik için <xref:System.Int32> 'den farklı olması gerekir.

- Daha küçük bir temel alınan tür, alana önemli ölçüde tasarruf oluşmasına neden olur. Numaralandırmanın genellikle denetim akışı için bağımsız değişken olarak kullanılmasını bekleliyorsanız, boyut biraz fark yapar. Boyut tasarrufları önemli olabilir:

  - Sabit listesinin çok sık oluşturulan bir yapıda veya sınıfta bir alan olarak kullanılmasını beklediğinizi.

  - Kullanıcıların, sabit listesi örneklerinin büyük dizilerini veya koleksiyonlarını oluşturmasını bekleolursunuz.

  - Sabit listesinin serileştirilmesi için çok sayıda örnek beklemeniz gerekir.

Bellek içi kullanım için, yönetilen nesnelerin her zaman `DWORD`hizalı olduğunu unutmayın. bu nedenle, fark oluşturmak için bir örnekte birden çok sabit listesi veya diğer küçük yapıların, bir farklılık yapmak üzere bir örnek olarak daha küçük bir numaralandırma paketleyeceğinden, her zaman bir `DWORD`yukarı yuvarlanmasını sağlamak için.

✔️, çoğul isimler veya isim tümcecikleriyle sabit numaralandırmalar ve tekil isimler veya isim tümcecikleriyle basit Numaralandırmalar.

❌ doğrudan <xref:System.Enum?displayProperty=nameWithType> genişletmez.

<xref:System.Enum?displayProperty=nameWithType>, CLR tarafından Kullanıcı tanımlı numaralandırmalar oluşturmak için kullanılan özel bir türdür. Çoğu programlama dili, bu işlevselliğe erişmenizi sağlayan bir programlama öğesi sağlar. Örneğin, C# `enum` anahtar sözcüğü bir sabit listesini tanımlamak için kullanılır.

<a name="design"></a>

### <a name="designing-flag-enums"></a>Bayrak numaralandırmaları tasarlama

✔️ numaralandırmalarını işaretlemek için <xref:System.FlagsAttribute?displayProperty=nameWithType> uygulayın. Bu özniteliği basit Numaralandırmalar için uygulamayın.

✔️, bir bit düzeyinde OR işlemi kullanılarak serbestçe birleştirilebilmesi için bayrak Enum değerleri için ikinin üslerini kullanır.

✔️, bayrakların yaygın olarak kullanılan birleşimleri için özel Enum değerleri sağlamayı düşünün.

Bit düzeyinde işlemler gelişmiş bir kavramdır ve basit görevler için gerekli olmamalıdır. <xref:System.IO.FileAccess.ReadWrite>, bu tür özel bir değere örnektir.

❌ belirli değer birleşimlerinin geçersiz olduğu bayrak numaralandırmalarını oluşturmaktan KAÇıNıN.

değer "tüm bayraklar temizlenmedi" ve uygun şekilde adlandırılmış ve bir sonraki kılavuz tarafından belirtilen şekilde adlandırılmadığı sürece, sıfıra bayrak Enum değerlerini kullanmaktan KAÇıNıN. ❌

✔️ `None`bayrak Numaralandırmaların sıfır değeri. Bayrak numaralandırması için, değer her zaman "tüm bayraklar temizlenmelidir." anlamına gelir.

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a>Numaralandırmalar için değer ekleme

Zaten sevk ettikten sonra bir sabit listesine değer eklemeniz gerektiğini saptamak çok yaygındır. Varolan bir API 'den yeni eklenen değer döndürüldüğünde olası bir uygulama uyumluluk sorunu vardır, çünkü kötü yazılmış uygulamalar yeni değeri doğru şekilde işleyemeyebilir.

✔️, küçük bir uyumluluk riskine karşın Numaralandırmaların değerlerini eklemeyi düşünün.

Bir sabit listesine eklemelere neden olan uygulama uyumsuzluklarını hakkında gerçek verileriniz varsa, yeni ve eski değerleri döndüren yeni bir API eklemeyi ve eski API 'yi kullanımdan kaldırmayı ve yalnızca eski değerleri döndürmeye devam etmeyi göz önünde bulundurun. Bu, mevcut uygulamalarınızın uyumlu kalmasını sağlayacaktır.

*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
