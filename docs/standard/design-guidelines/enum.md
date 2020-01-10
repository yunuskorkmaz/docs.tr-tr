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
ms.openlocfilehash: 130e9b4e7f8d7076d1dc3f21f51dc07a68799bbe
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709458"
---
# <a name="enum-design"></a>Sabit Listesi Tasarımı

Numaralandırmalar özel bir tür değer türüdür. İki tür numaralandırmalar vardır: basit numaralandırmalar ve bayrak Numaralandırmalar.

Basit numaralandırmalar küçük kapalı seçim kümelerini temsil eder. Basit sabit listesinin yaygın bir örneği bir renk kümesidir.

Bayrak numaralandırmalarında, sabit listesi değerlerinde bit düzeyinde işlemleri destekleyecek şekilde tasarlanmıştır. Flags numaralandırmasının ortak bir örneği, seçeneklerin listesidir.

**✓ DO** döndürülen değer kümesini temsil eden değerler ve kesin tür parametreleri, özellikler, için bir numaralandırma kullanın.

**✓ DO** enum yerine statik sabitleri kullanarak ayrıcalık tanıma.

**X DO NOT** enum (örneğin, işletim sistemi sürümü, adlarını arkadaşlarınız, vb.) açık kümeleri için kullanın.

**X DO NOT** gelecekte kullanılmak üzere tasarlanmıştır ayrılmış enum değerleri sağlayın.

Daha sonraki bir aşamada mevcut sabit listesine her zaman bir değer ekleyebilirsiniz. Numaralandırmaların değerlerini ekleme hakkında daha fazla ayrıntı için bkz. [numaralandırmalar Için değer ekleme](#add_value) . Ayrılmış değerler yalnızca gerçek değerler kümesini Pollute ve Kullanıcı hatalarına neden olacak şekilde eğilimlidir.

**X AVOID** genel olarak tek bir değer ile numaralandırmaları gösterme.

C API 'Lerinde gelecekteki genişletilebilirliği sağlamaya yönelik yaygın bir uygulama, ayrılmış parametreleri Yöntem imzalarına eklemektir. Bu tür ayrılmış parametreler, tek bir varsayılan değer ile enum olarak ifade edilebilir. Bu, yönetilen API 'lerde yapılmamalıdır. Yöntem aşırı yüklemesi gelecekteki sürümlerde parametre eklenmesine izin verir.

**X DO NOT** numaralandırmaları sentinel değerler içerir.

Bazen Framework geliştiricilerine faydalı olsalar da, Sentinel değerleri Framework kullanıcılarına kafa karıştırıcı olur. Numaralandırıcılardan temsil edilen kümeden biri yerine sabit listesinin durumunu izlemek için kullanılırlar.

**✓ DO** basit numaralandırmalar sıfır değerini sağlamalısınız.

"None" gibi bir değer çağırmayı düşünün. Böyle bir değer bu sabit listesi için uygun değilse, sabit listesi için en yaygın varsayılan değere sıfır değeri atanmış olmalıdır.

**✓ CONSIDER** kullanarak <xref:System.Int32> (varsayılan olarak çoğu programlama dilleri) enum temel alınan türü olarak aşağıdakilerin doğru değilse:

- Sabit listesi bir bayrak numaralandırıcıdır ve 32 ' den fazla bayrak veya daha fazlasını bekliyor olabilir.

- Temel alınan türün, farklı boyutlu numaralandırmalar bekleyen yönetilmeyen kodla daha kolay birlikte çalışabilirlik için <xref:System.Int32> 'den farklı olması gerekir.

- Daha küçük bir temel alınan tür, alana önemli ölçüde tasarruf oluşmasına neden olur. Numaralandırmanın genellikle denetim akışı için bağımsız değişken olarak kullanılmasını bekleliyorsanız, boyut biraz fark yapar. Boyut tasarrufları önemli olabilir:

  - Sabit listesinin çok sık oluşturulan bir yapıda veya sınıfta bir alan olarak kullanılmasını beklediğinizi.

  - Kullanıcıların, sabit listesi örneklerinin büyük dizilerini veya koleksiyonlarını oluşturmasını bekleolursunuz.

  - Sabit listesinin serileştirilmesi için çok sayıda örnek beklemeniz gerekir.

Bellek içi kullanım için, yönetilen nesnelerin her zaman `DWORD`hizalı olduğunu unutmayın. bu nedenle, fark oluşturmak için bir örnekte birden çok sabit listesi veya diğer küçük yapıların, bir farklılık yapmak üzere bir örnek olarak daha küçük bir numaralandırma paketleyeceğinden, her zaman bir `DWORD`yukarı yuvarlanmasını sağlamak için.

**✓ DO** ad bayrağı numaralandırmaları çoğul adlar ve isim ifadeler ile ve basit numaralandırmaları tekil isimleri veya isim deyimleri ile.

**X DO NOT** genişletmek <xref:System.Enum?displayProperty=nameWithType> doğrudan.

<xref:System.Enum?displayProperty=nameWithType>, CLR tarafından Kullanıcı tanımlı numaralandırmalar oluşturmak için kullanılan özel bir türdür. Çoğu programlama dili, bu işlevselliğe erişmenizi sağlayan bir programlama öğesi sağlar. Örneğin, C# `enum` anahtar sözcüğü bir sabit listesini tanımlamak için kullanılır.

<a name="design"></a>

### <a name="designing-flag-enums"></a>Bayrak numaralandırmaları tasarlama

**✓ DO** uygulamak <xref:System.FlagsAttribute?displayProperty=nameWithType> bayrağı numaralandırmalar için. Bu özniteliği basit Numaralandırmalar için uygulamayın.

**✓ DO** bayrak enum değerleri için iki tabanların kullandığından, bunlar serbestçe bit düzeyinde OR işlemi kullanılarak birleştirilebilir.

**✓ CONSIDER** özel enum değerleri için yaygın olarak sağlayarak kullanılan bayrakları birleşimlerini.

Bit düzeyinde işlemler gelişmiş bir kavramdır ve basit görevler için gerekli olmamalıdır. <xref:System.IO.FileAccess.ReadWrite>, bu tür özel bir değere örnektir.

**X AVOID** burada belirli değerleri birleşimleridir geçersiz bayrak numaralandırmaları oluşturma.

**X AVOID** kullanarak bayrak enum değerleri sıfır sürece değeri "tüm bayraklar temizlenmiştir" temsil eder ve uygun şekilde, bir sonraki kural tarafından belirlenen olarak adlandırılır.

**✓ DO** bayrağı numaralandırmalar sıfır değeri adı `None`. Bayrak numaralandırması için, değer her zaman "tüm bayraklar temizlenmelidir." anlamına gelir.

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a>Numaralandırmalar için değer ekleme

Zaten sevk ettikten sonra bir sabit listesine değer eklemeniz gerektiğini saptamak çok yaygındır. Varolan bir API 'den yeni eklenen değer döndürüldüğünde olası bir uygulama uyumluluk sorunu vardır, çünkü kötü yazılmış uygulamalar yeni değeri doğru şekilde işleyemeyebilir.

**✓ CONSIDER** küçük uyumluluk riski rağmen numaralandırmaları değerleri ekleme.

Bir sabit listesine eklemelere neden olan uygulama uyumsuzluklarını hakkında gerçek verileriniz varsa, yeni ve eski değerleri döndüren yeni bir API eklemeyi ve eski API 'yi kullanımdan kaldırmayı ve yalnızca eski değerleri döndürmeye devam etmeyi göz önünde bulundurun. Bu, mevcut uygulamalarınızın uyumlu kalmasını sağlayacaktır.

*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*

## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
