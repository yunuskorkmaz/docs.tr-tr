---
title: Koleksiyonlar için yönergeler
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
author: KrzysztofCwalina
ms.openlocfilehash: a8e8672d71500478dbbe28512e413e8ada501f45
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587140"
---
# <a name="guidelines-for-collections"></a>Koleksiyonlar için yönergeler
Özellikle bazı genel özelliği içeren nesnelerin bir grup yönetmek üzere tasarlanmış herhangi bir türü bir koleksiyon kabul edilebilir. Neredeyse her zaman böyle türleri uygulamak uygun olan <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601>, bu bölümde biz yalnızca birini veya her ikisini bu arabirimleri uygulayan türleri, koleksiyonları olmasını düşünün.  
  
 **X DO NOT** zayıf yazılan koleksiyonları genel API'leri kullanın.  
  
 Tüm dönüş değerleri ve parametre koleksiyonu öğeleri temsil eden türünü (yalnızca koleksiyonun Genel üyeler için geçerlidir) temel türlerinden hiçbir tam öğe türü olmalıdır.  
  
 **X DO NOT** kullanmak <xref:System.Collections.ArrayList> veya <xref:System.Collections.Generic.List%601> ortak API'lerde.  
  
 Bu değil genel API'leri, iç uygulamada kullanılmak üzere tasarlanmış veri yapılarını türleridir. `List<T>` Performans ve esneklik ve API'leri cleanness karşılığında power için optimize edilmiştir. Örneğin, iade ettiğiniz `List<T>`, hiç kod istemci koleksiyonu değiştirdiğinde bildirim almak mümkün olmayacaktır. Ayrıca, `List<T>` gibi çok sayıda üye sunan <xref:System.Collections.Generic.List%601.BinarySearch%2A>, olmayan kullanışlı veya birçok senaryoda uygulanabilir. Aşağıdaki iki bölümü, ortak API'lerde kullanılmak üzere özel olarak tasarlanmış türleri (soyutlama) açıklanmaktadır.  
  
 **X DO NOT** kullanmak `Hashtable` veya `Dictionary<TKey,TValue>` ortak API'lerde.  
  
 Bu veri yapılarını iç uygulamasında kullanılmak üzere tasarlanmış türleridir. Ortak API'lerde kullanması gereken <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`, ya da birini veya her ikisini arabirimleri uygulayan özel bir tür.  
  
 **X DO NOT** kullanmak <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, veya dönüş türü olarak ya da bu arabirimi uygulayan dışında herhangi bir türü bir `GetEnumerator` yöntemi.  
  
 Numaralandırıcılar yöntemleri dışında döndüren türleri `GetEnumerator` kullanılamaz `foreach` deyimi.  
  
 **X DO NOT** her ikisini de uygulamak `IEnumerator<T>` ve `IEnumerable<T>` aynı türünde. Aynı jenerik olmayan arabirimleri için geçerlidir `IEnumerator` ve `IEnumerable`.  
  
## <a name="collection-parameters"></a>Toplama parametrelerini  
 **✓ DO** en az özelleştirilmiş türü olası parametre türü olarak kullanın. Koleksiyonları parametreleri kullanma gibi birçok üye `IEnumerable<T>` arabirimi.  
  
 **X AVOID** kullanarak <xref:System.Collections.Generic.ICollection%601> veya <xref:System.Collections.ICollection> yalnızca erişmek için bir parametre olarak `Count` özelliği.  
  
 Bunun yerine, kullanmayı `IEnumerable<T>` veya `IEnumerable` ve dinamik olarak nesne uygulayan olup olmadığını denetleyerek `ICollection<T>` veya `ICollection`.  
  
## <a name="collection-properties-and-return-values"></a>Koleksiyon Özellikleri ve dönüş değerleri  
 **X DO NOT** ayarlanabilir koleksiyon özellikleri sağlar.  
  
 Kullanıcılar, koleksiyon ilk temizlemek ve ardından yeni içerik ekleyerek koleksiyonun içeriğini değiştirebilir. Tüm koleksiyon değiştirerek yaygın bir senaryo ise sağlamayı göz önüne alın `AddRange` yöntemi koleksiyonu.  
  
 **✓ DO** kullanmak `Collection<T>` veya bir alt sınıfı `Collection<T>` özellikleri veya return temsil eden okuma/yazma koleksiyonları değerler için.  
  
 Varsa `Collection<T>` bazı gereksinimleri karşılamıyor (örn, toplama olmayan uygulamalıdır <xref:System.Collections.IList>), özel bir koleksiyona uygulayarak kullanma `IEnumerable<T>`, `ICollection<T>`, veya <xref:System.Collections.Generic.IList%601>.  
  
 **✓ DO** kullanmak <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, öğesinin bir alt `ReadOnlyCollection<T>`, veya nadir durumlarda `IEnumerable<T>` özellikleri veya return temsil eden salt okunur koleksiyonlar değerler için.  
  
 Genel olarak, tercih ettiğiniz `ReadOnlyCollection<T>`. Bazı gereksinimi karşılamıyorsa (örneğin, koleksiyon değil uygulamalıdır `IList`), özel bir koleksiyona uygulayarak kullanın `IEnumerable<T>`, `ICollection<T>`, veya `IList<T>`. Özel bir salt okunur koleksiyon uygularsanız, uygulama `ICollection<T>.IsReadOnly` döndürülecek `true`.  
  
 Hiç olmadığı kadar desteklemek istediğiniz tek senaryo yalnızca iletme yineleme olduğundan emin olduğu durumlarda, yalnızca kullanabilirsiniz `IEnumerable<T>`.  
  
 **✓ CONSIDER** koleksiyonlar doğrudan kullanmak yerine genel temel koleksiyonlar alt sınıflarının kullanarak.  
  
 Bu, daha iyi bir adı ve temel koleksiyon türleri üzerinde mevcut olmayan Yardımcısı üye ekleme için sağlar. Bu, özellikle de üst düzey API'ler için geçerlidir.  
  
 **✓ CONSIDER** öğesinin bir alt kümesi döndüren `Collection<T>` veya `ReadOnlyCollection<T>` çok sık kullanılan yöntemleri ve özellikleri.  
  
 Bu, sizin için yardımcı yöntemler ekler veya gelecekte koleksiyonu uygulama değiştirmek mümkün hale getirir.  
  
 **✓ CONSIDER** koleksiyonda depolanan öğeler benzersiz anahtarlar varsa anahtarlı bir koleksiyonunu kullanarak (ad, kimlikleri, vs.). Anahtarlanmış koleksiyonlar olan bir tamsayı ve bir anahtar tarafından sıralanabilir ve genellikle devralarak uygulanan koleksiyonları `KeyedCollection<TKey,TItem>`.  
  
 Anahtarlanmış koleksiyonlar, genellikle daha büyük bellek kaplama sahip ve bellek yükü anahtarına sahip avantajları ağır varsa kullanılmamalıdır.  
  
 **X DO NOT** koleksiyon özellikleri veya koleksiyonları döndüren yöntemler null değerleri döndürür. Bunun yerine boş bir koleksiyon ya da boş bir dizi döndürür.  
  
 Genel kural null ve boş (0 öğe) koleksiyonları veya dizi olması gerekliliğidir aynı kabul edilir.  
  
### <a name="snapshots-versus-live-collections"></a>Canlı koleksiyonları ve anlık görüntüleri  
 Anlık görüntü koleksiyonlarını belirli bir noktada bir durum saati temsil eden koleksiyon çağrılır. Örneğin, bir veritabanı sorgusundan döndürülen satır içeren bir koleksiyon bir anlık görüntü olacaktır. Canlı koleksiyonları her zaman geçerli durumu temsil eden koleksiyon çağrılır. Örneğin, bir koleksiyonunu `ComboBox` öğeleri canlı bir derlemesidir.  
  
 **X DO NOT** anlık görüntü koleksiyonları özelliklerinden döndürür. Özellikleri, Canlı koleksiyon döndürmelidir.  
  
 Özellik alıcılar, basit bir işlem olmalıdır. Bir anlık görüntü döndüren bir o(n) iç bir koleksiyonun bir kopyasını oluşturmak için gerekir.  
  
 **✓ DO** bir anlık görüntü koleksiyon veya bir canlı kullanmak `IEnumerable<T>` (veya onun alt) volatile koleksiyonları temsil etmek için (yani, değiştirebilirsiniz açıkça koleksiyonu değiştirmeden).  
  
 Genel olarak, paylaşılan bir kaynağa (örneğin, bir dizindeki dosyaları) temsil eden tüm geçici koleksiyonlarıdır. Bu, çok zor veya imkansız uygulaması yalnızca iletme Numaralandırıcı yalnızca olmadıkça Canlı koleksiyon olarak uygulamak koleksiyonlarıdır.  
  
## <a name="choosing-between-arrays-and-collections"></a>Diziler ve Koleksiyonlar arasında seçim yapma  
 **✓ DO** koleksiyonları diziler tercih.  
  
 Koleksiyonlar içerikleri üzerinde daha fazla denetim sağlamak, zamanla gelişmesinin ve daha kullanışlı. Dizi kopyalama maliyeti engelleyici olduğundan ek olarak, dizi salt okunur senaryoları için kullanılması önerilmez. Kullanılabilirlik incelemeleri bazı geliştiriciler koleksiyon tabanlı API'leri daha ettirebilecek olduğunu göstermiştir.  
  
 Ancak, alt düzey API'ler geliştiriyorsanız diziler için okuma-yazma senaryolarını kullanmak daha iyi olabilir. Çalışma kümesi azaltılmasına yardımcı olur, bir küçük bellek Ayak izi diziler sahip ve çalışma zamanı tarafından iyileştirildiği bir dizideki öğelerin erişimi daha hızlıdır.  
  
 **✓ CONSIDER** bellek tüketimini en aza indirmek ve performansı en üst düzeye çıkarmak için alt düzey API'leri dizileri kullanma.  
  
 **✓ DO** bayt dizileri bayt koleksiyon yerine kullanın.  
  
 **X DO NOT** özelliği özellik alıcısı adlı her zaman yeni bir dizi (örneğin, bir iç dizisinin bir kopyasını) dönmek zorunda kalırsanız diziler özellikler için kullanın.  
  
## <a name="implementing-custom-collections"></a>Uygulama özel koleksiyonlar  
 **✓ CONSIDER** içinden devralma `Collection<T>`, `ReadOnlyCollection<T>`, veya `KeyedCollection<TKey,TItem>` yeni koleksiyonları tasarlarken.  
  
 **✓ DO** uygulamak `IEnumerable<T>` yeni koleksiyonları tasarlarken. Uygulamayı düşünün `ICollection<T>` ve hatta `IList<T>` burada anlamlı.  
  
 Bu tür özel bir koleksiyon uygularken tarafından oluşturulan API desenler izleyen `Collection<T>` ve `ReadOnlyCollection<T>` mümkün olduğunca yakın. Diğer bir deyişle, aynı üyelerini açıkça uygulama, bunları vb. Bu iki koleksiyon adı gibi parametreler adlandırın.  
  
 **✓ CONSIDER** nongeneric koleksiyonu arabirimler uygulama (`IList` ve `ICollection`) koleksiyon genellikle API'leri için girdi olarak bu arabirimleri alma geçirilir durumunda.  
  
 **X AVOID** koleksiyon arabirimleri türlerinde bir koleksiyon kavramı, ilgisiz karmaşık API'leri ile uygulama.  
  
 **X DO NOT** nongeneric temel koleksiyonlarından gibi devral `CollectionBase`. Kullanım `Collection<T>`, `ReadOnlyCollection<T>`, ve `KeyedCollection<TKey,TItem>` yerine.  
  
### <a name="naming-custom-collections"></a>Özel koleksiyonlar adlandırma  
 Koleksiyonlar (türleri uygulayan `IEnumerable`) genellikle iki nedenden dolayı oluşturulur: (1) varolan veri yapılarına değerinden farklı performans özellikleri yapısı özgü işlemleri ve genellikle yeni bir veri yapısı oluşturmak için (örneğin, <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>) ve özel bir koleksiyon için oluşturma (2) belirli bir öğe kümesini bulunduran (örneğin, <xref:System.Collections.Specialized.StringCollection>). Veri yapıları, uygulamaları ve kitaplıkları iç uygulamasında en sık kullanılır. Özelleştirilmiş koleksiyonlar çoğunlukla API (özelliği, parametre türleri) olarak gösterilmesini üzeresiniz.  
  
 **✓ DO** uygulama soyutlamalar adlarında "Sözlük" soneki kullanan `IDictionary` veya `IDictionary<TKey,TValue>`.  
  
 **✓ DO** uygulama türleri adlarında "Toplama" soneki kullanan `IEnumerable` (veya bunların alt öğeleri) ve öğelerin listesini temsil eden.  
  
 **✓ DO** özel veri yapıları için uygun veri yapısı adını kullanın.  
  
 **X AVOID** koleksiyonu soyutlamalar adlarında "LinkedList" veya "Hashtable," gibi belirli bir uygulamaya olduğunu belirtmek sonekleri kullanarak.  
  
 **✓ CONSIDER** koleksiyon adları öğesi türünün adı ile önek. Örneğin, bir koleksiyon öğe türü depolama `Address` (uygulama `IEnumerable<Address>`) adlandırılmalıdır `AddressCollection`. Öğe türü bir arabirim ise, "t" öneki öğenin türü atlanabilir. Bu nedenle, bir koleksiyonunu <xref:System.IDisposable> öğeleri çağrılabilir `DisposableCollection`.  
  
 **✓ CONSIDER** karşılık gelen bir yazılabilir koleksiyon eklenebilir ya da Framework'te zaten varsa, salt okunur koleksiyonlar adlarında "Salt okunur" önekini kullanarak.  
  
 Örneğin, dizelerin bir salt okunur koleksiyon çağrılmalıdır `ReadOnlyStringCollection`.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
