---
title: Koleksiyonlar için yönergeler
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5a1bb81a23a180c3f7738d811398a5a45abd9122
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="guidelines-for-collections"></a>Koleksiyonlar için yönergeler
Özellikle bir grup bazı ortak özelliğe sahip nesneleri yönetmek üzere tasarlanmış herhangi bir tür bir koleksiyon kabul edilebilir. Neredeyse her zaman böyle türleri uygulamak uygun olan <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601>, bu bölümde biz yalnızca birini veya her ikisini bu arabirimleri uygulama türlerini koleksiyonları olması için göz önünde bulundurun.  
  
 **X yok** zayıf yazılan koleksiyonları genel API'leri kullanın.  
  
 Tüm dönüş değerleri ve parametre koleksiyonu öğelerini temsil eden türünü (yalnızca koleksiyon ortak üyeleri için geçerlidir) temel türlerinden herhangi tam öğesi türü olmalıdır.  
  
 **X yok** kullanmak <xref:System.Collections.ArrayList> veya <xref:System.Collections.Generic.List%601> ortak API'lerde.  
  
 Bu ortak API'ler değil, iç uygulamasında kullanılmak üzere tasarlanmış veri yapılarını türleridir. `List<T>` Performans ve güç cleanness API'leri ve esnekliği artırılabilir için optimize edilmiştir. Örneğin, geri `List<T>`, size herhangi bir zamanda istemci kodu koleksiyonu değiştirdiğinde bildirimleri almak mümkün olmaz. Ayrıca, `List<T>` çok sayıda üye gibi sunan <xref:System.Collections.Generic.List%601.BinarySearch%2A>, olmayan kullanışlı veya birçok senaryoda uygulanabilir. Aşağıdaki iki bölümü özellikle ortak API'ler kullanılmak üzere tasarlanmış türleri (soyutlamalar) açıklanmaktadır.  
  
 **X yok** kullanmak `Hashtable` veya `Dictionary<TKey,TValue>` ortak API'lerde.  
  
 Bu veri yapılarını iç uygulamasında kullanılmak üzere tasarlanmış türleridir. Ortak API'ler kullanması gereken <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`, ya birini veya her ikisini arabirimler uygulama özel bir tür.  
  
 **X yok** kullanmak <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, veya dönüş türü olarak ya da bu arabirimi uygulayan dışında herhangi bir türü bir `GetEnumerator` yöntemi.  
  
 Numaralandırmalar yöntemleri dışında döndürme türleri `GetEnumerator` kullanılamaz `foreach` deyimi.  
  
 **X yok** her ikisini de uygulamak `IEnumerator<T>` ve `IEnumerable<T>` aynı türünde. Aynı nongeneric arabirimleri için geçerlidir `IEnumerator` ve `IEnumerable`.  
  
## <a name="collection-parameters"></a>Toplama parametrelerini  
 **✓ YAPMAK** en az özelleştirilmiş türü olası parametre türü olarak kullanın. Çoğu üyeleri parametrelerini kullanırken koleksiyonları `IEnumerable<T>` arabirimi.  
  
 **KAÇININ x** kullanarak <xref:System.Collections.Generic.ICollection%601> veya <xref:System.Collections.ICollection> yalnızca erişmek için bir parametre olarak `Count` özelliği.  
  
 Bunun yerine, kullanmayı `IEnumerable<T>` veya `IEnumerable` ve dinamik olarak nesne uygulayan olup olmadığını denetleme `ICollection<T>` veya `ICollection`.  
  
## <a name="collection-properties-and-return-values"></a>Koleksiyon Özellikleri ve dönüş değerleri  
 **X yok** ayarlanabilir koleksiyon özellikleri sağlar.  
  
 Kullanıcılar, koleksiyon ilk temizlenmesi ve yeni içeriği ekleme koleksiyonunun içeriğini değiştirebilirsiniz. Tüm koleksiyon değiştirme yaygın bir senaryo ise, sağlamayı düşünün `AddRange` yöntemi koleksiyonu.  
  
 **✓ YAPMAK** kullanmak `Collection<T>` veya bir alt sınıfı `Collection<T>` özellikleri veya return temsil eden okuma/yazma koleksiyonları değerler için.  
  
 Varsa `Collection<T>` bazı gereksinimini karşılamıyor (örn., toplama olmayan uygulamalıdır <xref:System.Collections.IList>), özel bir koleksiyona uygulayarak kullanmak `IEnumerable<T>`, `ICollection<T>`, veya <xref:System.Collections.Generic.IList%601>.  
  
 **✓ YAPMAK** kullanmak <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, öğesinin bir alt `ReadOnlyCollection<T>`, veya nadir durumlarda `IEnumerable<T>` özellikleri veya return temsil eden salt okunur koleksiyonlar değerler için.  
  
 Genel olarak, tercih `ReadOnlyCollection<T>`. Bazı gereksinimi karşılamıyorsa (örn., toplama olmayan uygulamalıdır `IList`), özel bir koleksiyona uygulayarak kullanmak `IEnumerable<T>`, `ICollection<T>`, veya `IList<T>`. Özel bir salt okunur koleksiyonun uygularsanız, uygulama `ICollection<T>.IsReadOnly` döndürülecek `true`.  
  
 Herhangi bir zamanda istediğiniz desteklemek için tek senaryo yalnızca ileri yineleme emin olduğu durumlarda, yalnızca kullanabileceğiniz `IEnumerable<T>`.  
  
 **✓ DÜŞÜNÜN** koleksiyonlar doğrudan kullanmak yerine genel temel koleksiyonlar alt sınıflarının kullanarak.  
  
 Bu, daha iyi bir ad ve temel koleksiyon türlerinde mevcut olmayan Yardımcısı üyeleri eklemek için sağlar. Bu, özellikle üst düzey API'leri için geçerlidir.  
  
 **✓ DÜŞÜNÜN** öğesinin bir alt kümesi döndüren `Collection<T>` veya `ReadOnlyCollection<T>` çok sık kullanılan yöntemleri ve özellikleri.  
  
 Bu, sizin için yardımcı yöntemleri eklemek veya koleksiyon uygulama gelecekte değiştirmek mümkün hale getirir.  
  
 **✓ DÜŞÜNÜN** koleksiyonda depolanan öğeler benzersiz anahtarlar varsa anahtarlı bir koleksiyonunu kullanarak (ad, kimlikleri, vs.). Anahtarlanmış koleksiyonlar olan bir tamsayı ve bir anahtar tarafından sıralanabilir ve genellikle devralarak uygulanan koleksiyonları `KeyedCollection<TKey,TItem>`.  
  
 Anahtarlanmış koleksiyonlar genellikle daha büyük bellek in sahip ve bellek ek yüküne anahtarına sahip avantajlarını ağır varsa kullanılmamalıdır.  
  
 **X yok** koleksiyon özellikleri veya koleksiyonları döndüren yöntemler null değerleri döndürür. Bunun yerine boş bir koleksiyon ya da boş bir dizi döndürür.  
  
 Genel kural null ve boş (0 öğe) koleksiyonları veya dizi olması gerektiğini olduğu aynı kabul edilir.  
  
### <a name="snapshots-versus-live-collections"></a>Anlık görüntü dinamik koleksiyonlar karşılaştırması  
 Koleksiyonlar bir durumda, belirli bir noktada zamanında temsil eden anlık görüntü koleksiyonları denir. Örneğin, bir veritabanı sorgusundan döndürülen satır içeren bir koleksiyon bir anlık görüntüsü olur. Her zaman geçerli durumunu temsil eden koleksiyonları dinamik koleksiyonlar denir. Örneğin, bir koleksiyonu `ComboBox` öğeleri canlı bir derlemesidir.  
  
 **X yok** anlık görüntü koleksiyonları özelliklerinden döndürür. Özellikleri, Canlı koleksiyonları döndürmelidir.  
  
 Özellik alıcıları çok basit işlemleri olmalıdır. Bir anlık görüntü döndüren bir o(n) iç koleksiyonun bir kopyasını oluşturmanız gerekir.  
  
 **✓ YAPMAK** bir anlık görüntü koleksiyon veya bir canlı kullanmak `IEnumerable<T>` (veya onun alt) volatile koleksiyonları temsil etmek için (yani, değiştirebilirsiniz açıkça koleksiyonu değiştirmeden).  
  
 Genel olarak, paylaşılan bir kaynak (örneğin, bir dizindeki dosyaları) temsil eden tüm volatile koleksiyonlarıdır. Bu tür, çok zor veya uygulama sadece bir salt iletme Numaralandırıcı olmadıkça Canlı koleksiyon olarak uygulamak imkansız koleksiyonlarıdır.  
  
## <a name="choosing-between-arrays-and-collections"></a>Diziler ve Koleksiyonlar arasında seçim yapma  
 **✓ YAPMAK** koleksiyonları diziler tercih.  
  
 Koleksiyonlar içeriği üzerinde daha fazla denetim sağlamak, zaman içinde gelişmesi ve daha kullanışlı. Dizi kopyalama maliyetini engelleyici olduğundan ek olarak, salt okunur senaryoları için kullanarak dizileri önerilmez. Bazı geliştiriciler koleksiyon tabanlı API'lerini kullanarak daha rahat eşitleyerek kullanılabilirlik incelemeleri göstermiştir.  
  
 Ancak, alt düzey API'leri geliştiriyorsanız diziler için okuma-yazma senaryoları kullanmak daha iyi olabilir. Diziler çalışma kümesi azaltılmasına yardımcı olur, bir küçük bellek parmak izine sahip ve bu durum, çalışma zamanı tarafından en iyi hale getirildiğinden, bir dizideki öğeler için erişim hızlıdır.  
  
 **✓ DÜŞÜNÜN** bellek tüketimini en aza indirmek ve performansı en üst düzeye çıkarmak için alt düzey API'leri dizileri kullanma.  
  
 **✓ YAPMAK** bayt dizileri bayt koleksiyon yerine kullanın.  
  
 **X yok** özelliği özellik alıcısı adlı her zaman yeni bir dizi (örneğin, bir iç dizisinin bir kopyasını) dönmek zorunda kalırsanız diziler özellikler için kullanın.  
  
## <a name="implementing-custom-collections"></a>Özel koleksiyonlar uygulama  
 **✓ DÜŞÜNÜN** içinden devralma `Collection<T>`, `ReadOnlyCollection<T>`, veya `KeyedCollection<TKey,TItem>` yeni koleksiyonları tasarlarken.  
  
 **✓ YAPMAK** uygulamak `IEnumerable<T>` yeni koleksiyonları tasarlarken. Uygulayın `ICollection<T>` ve hatta `IList<T>` burada anlamlı.  
  
 Bu tür özel koleksiyon uygularken tarafından oluşturulan API desenler izleyen `Collection<T>` ve `ReadOnlyCollection<T>` mümkün olduğunca yakın. Diğer bir deyişle, aynı üyelerini açıkça uygulama, bu iki koleksiyon adı bunları ve vb. gibi parametreleri adı.  
  
 **✓ DÜŞÜNÜN** nongeneric koleksiyonu arabirimler uygulama (`IList` ve `ICollection`) koleksiyon genellikle API'leri için girdi olarak bu arabirimleri alma geçirilir durumunda.  
  
 **KAÇININ x** koleksiyon arabirimleri türlerinde bir koleksiyon kavramı, ilgisiz karmaşık API'leri ile uygulama.  
  
 **X yok** nongeneric temel koleksiyonlarından gibi devral `CollectionBase`. Kullanım `Collection<T>`, `ReadOnlyCollection<T>`, ve `KeyedCollection<TKey,TItem>` yerine.  
  
### <a name="naming-custom-collections"></a>Özel koleksiyonlar adlandırma  
 Koleksiyonlar (türleri uygulayan `IEnumerable`) çoğunlukla iki nedenden dolayı oluşturulur: (1) farklı performans özellikleri olan veri yapılarının daha yeni bir veri yapısı yapısı özgü işlemleri ve genellikle oluşturmak için (örn., <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>) ve (2) belirli bir öğe kümesini tutmak için özel bir koleksiyon oluşturmak için (örneğin, <xref:System.Collections.Specialized.StringCollection>). Veri yapıları, uygulamalar ve kitaplıklar iç uygulamasında en sık kullanılır. Özel (olarak özellik ve parametre türleri) API'lerde çoğunlukla açığa koleksiyonlarıdır.  
  
 **✓ YAPMAK** uygulama soyutlamalar adlarında "Sözlük" soneki kullanan `IDictionary` veya `IDictionary<TKey,TValue>`.  
  
 **✓ YAPMAK** uygulama türleri adlarında "Toplama" soneki kullanan `IEnumerable` (veya bunların alt öğeleri) ve öğelerin listesini temsil eden.  
  
 **✓ YAPMAK** özel veri yapıları için uygun veri yapısı adını kullanın.  
  
 **KAÇININ x** koleksiyonu soyutlamalar adlarında "LinkedList" veya "Hashtable," gibi belirli bir uygulamaya olduğunu belirtmek sonekleri kullanarak.  
  
 **✓ DÜŞÜNÜN** koleksiyon adları öğesi türünün adı ile önek. Örneğin, bir koleksiyon türü saklanması `Address` (uygulama `IEnumerable<Address>`) adlı `AddressCollection`. Öğe türü bir arabirim ise, "t" önek öğesi türü atlanabilir. Bu nedenle, bir koleksiyonu <xref:System.IDisposable> öğeleri çağrılabilir `DisposableCollection`.  
  
 **✓ DÜŞÜNÜN** karşılık gelen bir yazılabilir koleksiyon eklenebilir ya da Framework'te zaten varsa, salt okunur koleksiyonlar adlarında "Salt okunur" önekini kullanarak.  
  
 Örneğin, dizeleri salt okunur koleksiyonu çağrılmalıdır `ReadOnlyStringCollection`.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
