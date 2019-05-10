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
author: KrzysztofCwalina
ms.openlocfilehash: 36e1f62ab1b236d48a55f7c255ed406cc0efa488
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615233"
---
# <a name="enum-design"></a>Sabit Listesi Tasarımı
Numaralandırmalar özel türde bir değer türü var. İki enum türü vardır: Basit sabit listeleri ve bayrak sabit listeleri.  
  
 Basit numaralandırmalar küçük kapalı seçenek kümeleri temsil eder. Yaygın olarak karşılaşılan örneklerden basit Enum renkleri kümesidir.  
  
 Bayrak sabit listeleri, sabit listesi değerlerinin bit düzeyinde işlemler destekleyecek şekilde tasarlanmıştır. Yaygın olarak karşılaşılan örneklerden bayrak sabit listesinin seçenekleri listesidir.  
  
 **✓ DO** döndürülen değer kümesini temsil eden değerler ve kesin tür parametreleri, özellikler, için bir numaralandırma kullanın.  
  
 **✓ DO** enum yerine statik sabitleri kullanarak ayrıcalık tanıma.  
  
 **X DO NOT** enum (örneğin, işletim sistemi sürümü, adlarını arkadaşlarınız, vb.) açık kümeleri için kullanın.  
  
 **X DO NOT** gelecekte kullanılmak üzere tasarlanmıştır ayrılmış enum değerleri sağlayın.  
  
 Her zaman yalnızca var olan bir enum değerleri daha sonraki bir aşamada ekleyebilirsiniz. Bkz: [numaralandırmalar değerlere ekleme](#add_value) numaralandırmalar için değer ekleme hakkında daha fazla bilgi. Ayrılmış bir değerler yalnızca gerçek değerler kümesini pollute ve kullanıcı hatalarına neden eğilimindedir.  
  
 **X AVOID** genel olarak tek bir değer ile numaralandırmaları gösterme.  
  
 C API'lerinin sonra genişletilebilmek sağlamaya yönelik yaygın bir uygulama, yöntem imzaları için ayrılmış parametreler eklemektir. Ayrılmış tür parametreleri sabit listeleri ile tek bir varsayılan değer olarak ifade edilebilir. Bu yönetilen API'leri yapılmalıdır değil. Yöntem aşırı yükleme parametreleri gelecek sürümleri ekleme sağlar.  
  
 **X DO NOT** numaralandırmaları sentinel değerler içerir.  
  
 Bazen framework geliştiricilere yararlı olmasına rağmen sentinel değerleri framework kullanıcıları için kafa karıştırıcı olabilir. Enum tarafından temsil edilen kümesinden şu değerlerden birini yerine enum durumunu izlemek için kullanılır.  
  
 **✓ DO** basit numaralandırmalar sıfır değerini sağlamalısınız.  
  
 Değer "None." gibi bir şey çağırmayı düşünün Bu tür bir değer bu belirli enum için uygun değilse, temel alınan değeri sıfır enum için en sık kullanılan varsayılan değer atanmalıdır.  
  
 **✓ CONSIDER** kullanarak <xref:System.Int32> (varsayılan olarak çoğu programlama dilleri) enum temel alınan türü olarak aşağıdakilerin doğru değilse:  
  
- Sabit listesi flags sabit listesi olduğu ve 32'den fazla bayraklarınız veya ileride daha fazlasına sahip olmayı beklediğiniz.  
  
- Temel alınan türü farklı olması gereken <xref:System.Int32> boyutu farklı numaralandırmalar bekleniyor yönetilmeyen kod ile daha kolay birlikte çalışabilirlik.  
  
- Küçük temel alınan türü alan önemli ölçüde tasarruf sonuçlanır. Denetim akışı için bir bağımsız değişken olarak esas olarak kullanılmak üzere enum bekliyorsanız, boyutu küçük fark eder. Boyut tasarrufları önemli değilse:  
  
    - Beklediğiniz alan çok sık örneklenmiş yapısı veya sınıf olarak kullanılacak sabit.  
  
    - Büyük diziler veya koleksiyonları numaralandırma örnekleri oluşturmak için kullanıcıları beklediğiniz.  
  
    - Çok sayıda serileştirilecek enum örneklerini beklediğiniz.  
  
 Bellek içi kullanım için yönetilen nesneler her zaman olduğunu unutmayın `DWORD`-hizalı etkili bir şekilde birden fazla sıralanmış sabit veya bir örneğindeki toplam örnek boyutu her zaman olduğu için daha küçük bir enum ile paketini bir fark yaratmak için diğer küçük yapıları gerekir en fazla yuvarlanacak giderek bir `DWORD`.  
  
 **✓ DO** ad bayrağı numaralandırmaları çoğul adlar ve isim ifadeler ile ve basit numaralandırmaları tekil isimleri veya isim deyimleri ile.  
  
 **X DO NOT** genişletmek <xref:System.Enum?displayProperty=nameWithType> doğrudan.  
  
 <xref:System.Enum?displayProperty=nameWithType> özel bir türü CLR tarafından kullanıcı tanımlı sabit listeleri oluşturmak için kullanılır. Çoğu programlama dili, erişim için bu işlevi sağlayan bir programlama öğesi sağlar. Örneğin, C# dilinde `enum` anahtar sözcüğü bir numaralandırma tanımlamak için kullanılır.  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a>Tasarlama bayrak sabit listeleri  
 **✓ DO** uygulamak <xref:System.FlagsAttribute?displayProperty=nameWithType> bayrağı numaralandırmalar için. Bu öznitelik basit numaralandırmalar için geçerli değildir.  
  
 **✓ DO** bayrak enum değerleri için iki tabanların kullandığından, bunlar serbestçe bit düzeyinde OR işlemi kullanılarak birleştirilebilir.  
  
 **✓ CONSIDER** özel enum değerleri için yaygın olarak sağlayarak kullanılan bayrakları birleşimlerini.  
  
 Bit düzeyinde işlemler, Gelişmiş bir kavram olarak oldukça basittir ve Basit görevler için gerekli olmamalıdır. <xref:System.IO.FileAccess.ReadWrite> özel bir değere örneğidir.  
  
 **X AVOID** burada belirli değerleri birleşimleridir geçersiz bayrak numaralandırmaları oluşturma.  
  
 **X AVOID** kullanarak bayrak enum değerleri sıfır sürece değeri "tüm bayraklar temizlenmiştir" temsil eder ve uygun şekilde, bir sonraki kural tarafından belirlenen olarak adlandırılır.  
  
 **✓ DO** bayrağı numaralandırmalar sıfır değeri adı `None`. Bayrak sabit listesi için değer her zaman "tüm bayraklar temizlenir." ortalama gerekir  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a>Numaralandırmalar için değer ekleme  
 Zaten kullanıma sonra bir sabit listesi için değerleri eklemeniz gerektiğini bulmak için çok yaygındır. Bir olası uygulama uyumluluğu sorun var. mevcut bir API'ye yeni eklenen değer döndürüldüğünde kötü yazılmış uygulamaları yeni değeri doğru şekilde işlememesi çünkü  
  
 **✓ CONSIDER** küçük uyumluluk riski rağmen numaralandırmaları değerleri ekleme.  
  
 Uygulama uyumsuzlukları enum eklemeler nedeni ile ilgili gerçek veriler varsa, yeni ve eski değerleri döndüren yeni bir API eklemeyi göz önünde bulundurun ve yalnızca eski değerler döndüren sürmelidir eski API'yi kullanımdan. Bu işlem, mevcut uygulamalarınızı uyumlu kalmasını sağlayacaktır.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
