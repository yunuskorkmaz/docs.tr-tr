---
title: Enum tasarım
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 544f617ca3a352814504125d7a61d70db5a81566
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="enum-design"></a>Enum tasarım
Numaralandırmalar özel türde bir değer türü var. Numaralandırmalar iki tür vardır: Basit numaralandırmaları ve bayrağı numaralandırmaları.  
  
 Basit numaralandırmaları seçenek küçük kapalı kümeleri temsil eder. Basit liste yaygın bir örneği, renkler kümesidir.  
  
 Bayrak numaralandırmalarında enum değerlerin Bitsel işlemleri desteklemek için tasarlanmıştır. Bir ortak bayrakları enum seçeneklerin bir listesini örnektir.  
  
 **✓ YAPMAK** döndürülen değer kümesini temsil eden değerler ve kesin tür parametreleri, özellikler, için bir numaralandırma kullanın.  
  
 **✓ YAPMAK** enum yerine statik sabitleri kullanarak ayrıcalık tanıma.  
  
 **X yok** enum (örneğin, işletim sistemi sürümü, adlarını arkadaşlarınız, vb.) açık kümeleri için kullanın.  
  
 **X yok** gelecekte kullanılmak üzere tasarlanmıştır ayrılmış enum değerleri sağlayın.  
  
 Her zaman yalnızca daha sonraki bir aşamada varolan enum değerleri ekleyebilirsiniz. Bkz: [numaralandırmaları değerleri ekleyerek](#add_value) numaralandırmalar için değer ekleme hakkında daha fazla bilgi. Ayrılmış değerler yalnızca gerçek değerleri kümesi pollute ve kullanıcı hatalarına neden olma eğilimi gösterir.  
  
 **KAÇININ x** genel olarak tek bir değer ile numaralandırmaları gösterme.  
  
 C API'leri gelecekteki genişletilebilirlik sağlamaya yönelik yaygın bir yöntemi imzalar için ayrılmış parametreler eklemek için uygulamadır. Bu tür ayrılmış parametreleri tek varsayılan bir değerle numaralandırmaları olarak ifade edilebilir. Bu yönetilen API'leri yapılmalıdır değil. Yöntem aşırı yükleme parametrelerini gelecekteki Sunumlarda eklemeye izin verir.  
  
 **X yok** numaralandırmaları sentinel değerler içerir.  
  
 Bazen framework geliştiricileri için faydalı olsa da, sentinel framework kullanıcılar için kafa karıştırıcı değerlerdir. Enum tarafından temsil edilen kümesinden olma değerlerden biri yerine enum durumunu izlemek için kullanılır.  
  
 **✓ YAPMAK** basit numaralandırmalar sıfır değerini sağlamalısınız.  
  
 Değer "None" gibi bir şey çağırmayı düşünün Böyle bir değer bu belirli enum için uygun değilse, temel alınan değerin sıfır enum için en sık kullanılan varsayılan değer atanmalıdır.  
  
 **✓ DÜŞÜNÜN** kullanarak <xref:System.Int32> (varsayılan olarak çoğu programlama dilleri) enum temel alınan türü olarak aşağıdakilerin doğru değilse:  
  
-   Enum bayrakları enum olduğu ve 32'den fazla bayrakları sahip veya gelecekte daha fazla olmasını bekler.  
  
-   Temel alınan türü farklı olması gereken <xref:System.Int32> boyutu farklı numaralandırmaları bekleniyor yönetilmeyen kod ile daha kolay birlikte çalışabilirlik.  
  
-   Bir küçük temel alınan Tür alanında önemli tasarrufu neden olur. Çoğunlukla akış denetimi için bağımsız değişken olarak kullanılacak enum bekliyorsanız, boyutu çok az fark etmez. Boyut tasarrufları önemli varsa:  
  
    -   Çok sık örneklenen yapısı veya sınıf alanı olarak kullanılacak enum bekler.  
  
    -   Enum örneklerinin koleksiyonlarını veya büyük diziler oluşturmak için kullanıcıların bekler.  
  
    -   Çok sayıda serileştirilmesi için enum örneklerini bekler.  
  
 Bellek içi kullanım için yönetilen nesneler her zaman olduğunu unutmayın `DWORD`-hizalı birden çok numaralandırmaları veya diğer küçük yapıları örneğindeki toplam örnek boyutu her zaman olduğu için bir fark yapmak için daha küçük bir enum ile paketlemek için etkili bir şekilde gerekiyor en fazla yuvarlanmasını devam eden bir `DWORD`.  
  
 **✓ YAPMAK** ad bayrağı numaralandırmaları çoğul adlar ve isim ifadeler ile ve basit numaralandırmaları tekil isimleri veya isim deyimleri ile.  
  
 **X yok** genişletmek <xref:System.Enum?displayProperty=nameWithType> doğrudan.  
  
 <xref:System.Enum?displayProperty=nameWithType> özel bir türü CLR tarafından kullanıcı tanımlı numaralandırmalar oluşturmak için kullanılır. Bu işlevsellik, erişim sağlayan bir programlama öğesi çoğu programlama dilleri belirtin. Örneğin, C# ' ta `enum` anahtar sözcüğü bir numaralandırma tanımlamak için kullanılır.  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a>Tasarlama bayrağı numaralandırmaları  
 **✓ YAPMAK** uygulamak <xref:System.FlagsAttribute?displayProperty=nameWithType> bayrağı numaralandırmalar için. Bu öznitelik basit Enum değerleri için geçerli değildir.  
  
 **✓ YAPMAK** bayrak enum değerleri için iki tabanların kullandığından, bunlar serbestçe bit düzeyinde OR işlemi kullanılarak birleştirilebilir.  
  
 **✓ DÜŞÜNÜN** özel enum değerleri için yaygın olarak sağlayarak kullanılan bayrakları birleşimlerini.  
  
 Bit düzeyinde işlemler, Gelişmiş bir kavramıdır ve basit görevleri için gerekli olmamalıdır. <xref:System.IO.FileAccess.ReadWrite> özel bir değere örneğidir.  
  
 **KAÇININ x** burada belirli değerleri birleşimleridir geçersiz bayrak numaralandırmaları oluşturma.  
  
 **KAÇININ x** kullanarak bayrak enum değerleri sıfır sürece değeri "tüm bayraklar temizlenmiştir" temsil eder ve uygun şekilde, bir sonraki kural tarafından belirlenen olarak adlandırılır.  
  
 **✓ YAPMAK** bayrağı numaralandırmalar sıfır değeri adı `None`. Bayrak enum için değeri her zaman "tüm bayraklar temizlenmiştir." anlamı gerekir  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a>Numaralandırmalar için değer ekleme  
 Zaten sevk olan sonra bir enum değerleri eklemeniz gerekir bulmak için çok yaygındır. Bir olası uygulama uyumluluğu sorun var. Varolan bir API öğesinden yeni eklenen değer döndürüldüğünde kötü yazılmış uygulamalar yeni değer düzgün bir şekilde işler değil çünkü  
  
 **✓ DÜŞÜNÜN** küçük uyumluluk riski rağmen numaralandırmaları değerleri ekleme.  
  
 Enum eklemeler nedeni uygulama uyumsuzlukları ile ilgili gerçek veri varsa, yeni ve eski değerleri döndürür yeni bir API eklemeyi göz önünde bulundurun ve yalnızca eski değerler döndüren devam etmesi gerektiğini eski API alanı onaylanamadı. Bu, mevcut uygulamalarınızı uyumlu kalmasını güvence altına alır.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
