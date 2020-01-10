---
title: Koleksiyonlar için yönergeler
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: 231d8b04c11f19c4440e184533e1eeaded72b70b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709328"
---
# <a name="guidelines-for-collections"></a>Koleksiyonlar için yönergeler
Özellikle bir nesne grubunu işlemek için tasarlanan herhangi bir tür, bir koleksiyon olarak düşünülebilir. <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601>uygulamak üzere bu tür türler için neredeyse her zaman uygundur, bu nedenle bu arabirimlerin yalnızca birini ya da her ikisini de koleksiyonlar olarak uygulayan türleri göz önünde bulundurarız.  
  
 **X DO NOT** zayıf yazılan koleksiyonları genel API'leri kullanın.  
  
 Koleksiyon öğelerini temsil eden tüm dönüş değerlerinin ve parametrelerinin türü, temel türlerinden hiçbirini değil, tam öğe türü olmalıdır (Bu yalnızca koleksiyonun genel üyeleri için geçerlidir).  
  
 **X DO NOT** kullanmak <xref:System.Collections.ArrayList> veya <xref:System.Collections.Generic.List%601> ortak API'lerde.  
  
 Bu türler, genel API 'lerde değil, iç uygulamada kullanılmak üzere tasarlanan veri yapılarıdır. `List<T>`, API 'lerin ve esnekliğin Temizleme maliyetiyle performans ve güç için iyileştirilmiştir. Örneğin, `List<T>`döndürmeniz durumunda, istemci kodu koleksiyonu değiştirdiğinde hiçbir zaman bildirim alamazsınız. Ayrıca, çok sayıda senaryoda yararlı olmayan veya geçerli olmayan <xref:System.Collections.Generic.List%601.BinarySearch%2A>gibi birçok üye `List<T>` sunar. Aşağıdaki iki bölümde, genel API 'lerde kullanılmak üzere özel olarak tasarlanan türler (soyutlamalar) açıklanır.  
  
 **X DO NOT** kullanmak `Hashtable` veya `Dictionary<TKey,TValue>` ortak API'lerde.  
  
 Bu türler, iç uygulamada kullanılmak üzere tasarlanan veri yapılarıdır. Ortak API 'Ler <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`veya arabirimlerin birini ya da her ikisini birden uygulayan özel bir tür kullanmalıdır.  
  
 **X DO NOT** kullanmak <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, veya dönüş türü olarak ya da bu arabirimi uygulayan dışında herhangi bir türü bir `GetEnumerator` yöntemi.  
  
 `GetEnumerator` dışındaki yöntemlerden Numaralandırıcı döndüren türler `foreach` ifadesiyle kullanılamaz.  
  
 **X DO NOT** her ikisini de uygulamak `IEnumerator<T>` ve `IEnumerable<T>` aynı türünde. Aynı, genel olmayan arabirimler `IEnumerator` ve `IEnumerable`için de geçerlidir.  
  
## <a name="collection-parameters"></a>Koleksiyon parametreleri  
 **✓ DO** en az özelleştirilmiş türü olası parametre türü olarak kullanın. Koleksiyonları parametre olarak alan çoğu üye `IEnumerable<T>` arabirimini kullanır.  
  
 **X AVOID** kullanarak <xref:System.Collections.Generic.ICollection%601> veya <xref:System.Collections.ICollection> yalnızca erişmek için bir parametre olarak `Count` özelliği.  
  
 Bunun yerine, `IEnumerable<T>` veya `IEnumerable` kullanmayı ve nesnenin `ICollection<T>` veya `ICollection`uygulayıp uygulamadığını dinamik olarak denetlemeyi düşünün.  
  
## <a name="collection-properties-and-return-values"></a>Koleksiyon özellikleri ve dönüş değerleri  
 **X DO NOT** ayarlanabilir koleksiyon özellikleri sağlar.  
  
 Kullanıcılar, önce koleksiyonu temizleyerek ve sonra yeni içerikleri ekleyerek koleksiyonun içeriğini değiştirebilir. Tüm koleksiyonu değiştirmek ortak bir senaryodur, koleksiyonda `AddRange` yöntemi sağlamayı düşünün.  
  
 **✓ DO** kullanmak `Collection<T>` veya bir alt sınıfı `Collection<T>` özellikleri veya return temsil eden okuma/yazma koleksiyonları değerler için.  
  
 `Collection<T>`, bazı gereksinimleri karşılamıyorsa (örneğin, koleksiyon <xref:System.Collections.IList>uygulamamalı), `IEnumerable<T>`, `ICollection<T>`veya <xref:System.Collections.Generic.IList%601>uygulayarak özel bir koleksiyon kullanın.  
  
 **✓ DO** kullanmak <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, öğesinin bir alt `ReadOnlyCollection<T>`, veya nadir durumlarda `IEnumerable<T>` özellikleri veya return temsil eden salt okunur koleksiyonlar değerler için.  
  
 Genel olarak `ReadOnlyCollection<T>`tercih edin. Bir gereksinimi karşılamıyorsa (örneğin, koleksiyon `IList`uygulamamalı), `IEnumerable<T>`, `ICollection<T>`veya `IList<T>`uygulayarak özel bir koleksiyon kullanın. Özel bir salt okuma koleksiyonu uygularsanız, `true`döndürmek için `ICollection<T>.IsReadOnly` uygulayın.  
  
 Yalnızca ileri düzey yineleme olduğundan, desteklemek istediğiniz tek senaryonun yalnızca iletme yinelemesi olduğundan emin olmanız durumunda yalnızca `IEnumerable<T>`kullanabilirsiniz.  
  
 **✓ CONSIDER** koleksiyonlar doğrudan kullanmak yerine genel temel koleksiyonlar alt sınıflarının kullanarak.  
  
 Bu, daha iyi bir ad sağlar ve temel koleksiyon türlerinde bulunmayan yardımcı Üyeler ekler. Bu, özellikle üst düzey API 'Ler için geçerlidir.  
  
 **✓ CONSIDER** öğesinin bir alt kümesi döndüren `Collection<T>` veya `ReadOnlyCollection<T>` çok sık kullanılan yöntemleri ve özellikleri.  
  
 Bu, daha sonra yardımcı yöntemler eklemenizi veya koleksiyon uygulamasını değiştirmenizi mümkün hale getirir.  
  
 **✓ CONSIDER** koleksiyonda depolanan öğeler benzersiz anahtarlar varsa anahtarlı bir koleksiyonunu kullanarak (ad, kimlikleri, vs.). Anahtarlı koleksiyonlar, hem bir tamsayı hem de anahtar tarafından dizinlenebilir ve genellikle `KeyedCollection<TKey,TItem>`devralınarak uygulanabilir koleksiyonlardır.  
  
 Anahtarlı koleksiyonlar genellikle daha büyük bellek baskılarına sahiptir ve bellek ek yükü anahtarlara sahip olmanın avantajlarından yararlanıyorsa kullanılmamalıdır.  
  
 **X DO NOT** koleksiyon özellikleri veya koleksiyonları döndüren yöntemler null değerleri döndürür. Bunun yerine boş bir koleksiyon veya boş bir dizi döndürün.  
  
 Genel kural, null ve boş (0 öğe) koleksiyonlarının veya dizilerinin aynı kabul edilmesidir.  
  
### <a name="snapshots-versus-live-collections"></a>Anlık görüntüler ve canlı Koleksiyonlar  
 Bir zaman noktasında bir durumu temsil eden koleksiyonlara anlık görüntü koleksiyonları denir. Örneğin, bir veritabanı sorgusundan döndürülen satırları içeren bir koleksiyon bir anlık görüntü olacaktır. Geçerli durumu her zaman temsil eden koleksiyonlara canlı koleksiyonlar denir. Örneğin, `ComboBox` öğelerinin bir koleksiyonu canlı bir koleksiyondur.  
  
 **X DO NOT** anlık görüntü koleksiyonları özelliklerinden döndürür. Özellikler canlı koleksiyonlar döndürmelidir.  
  
 Özellik alıcıları çok hafif işlemler olmalıdır. Anlık görüntü döndürmek için bir O (n) işleminde iç koleksiyonun kopyasının oluşturulması gerekir.  
  
 **✓ DO** bir anlık görüntü koleksiyon veya bir canlı kullanmak `IEnumerable<T>` (veya onun alt) volatile koleksiyonları temsil etmek için (yani, değiştirebilirsiniz açıkça koleksiyonu değiştirmeden).  
  
 Genel olarak, paylaşılan bir kaynağı (örneğin, bir dizindeki dosyalar) temsil eden tüm koleksiyonlar geçici bir uygulamadır. Uygulama yalnızca ileri bir Numaralandırıcı değilse, bu tür koleksiyonlar canlı koleksiyonlar olarak uygulamak oldukça zordur veya imkansız olur.  
  
## <a name="choosing-between-arrays-and-collections"></a>Diziler ve koleksiyonlar arasında seçim yapma  
 **✓ DO** koleksiyonları diziler tercih.  
  
 Koleksiyonlar içerik üzerinde daha fazla denetim sağlar, zaman içinde gelişiyor ve daha fazla kullanılabilir. Ayrıca, diziyi kopyalama maliyeti yüksek olduğundan, salt okuma senaryolarında diziler kullanılması önerilmez. Kullanılabilirlik çalışmaları, bazı geliştiricilerin koleksiyon tabanlı API 'Leri kullanarak daha rahat olduğunu göstermiştir.  
  
 Ancak, alt düzey API 'Ler geliştiriyorsanız, okuma-yazma senaryolarında dizileri kullanmak daha iyi olabilir. Diziler, çalışma kümesini azaltmaya yardımcı olan daha küçük bir bellek parmak izine sahiptir ve çalışma zamanı tarafından iyileştirildiğinden, bir dizideki öğelere erişim daha hızlıdır.  
  
 **✓ CONSIDER** bellek tüketimini en aza indirmek ve performansı en üst düzeye çıkarmak için alt düzey API'leri dizileri kullanma.  
  
 **✓ DO** bayt dizileri bayt koleksiyon yerine kullanın.  
  
 **X DO NOT** özelliği özellik alıcısı adlı her zaman yeni bir dizi (örneğin, bir iç dizisinin bir kopyasını) dönmek zorunda kalırsanız diziler özellikler için kullanın.  
  
## <a name="implementing-custom-collections"></a>Özel Koleksiyonlar uygulama  
 **✓ CONSIDER** içinden devralma `Collection<T>`, `ReadOnlyCollection<T>`, veya `KeyedCollection<TKey,TItem>` yeni koleksiyonları tasarlarken.  
  
 **✓ DO** uygulamak `IEnumerable<T>` yeni koleksiyonları tasarlarken. `ICollection<T>`, hatta anlamlı olduğu yerde `IList<T>` uygulamayı düşünün.  
  
 Böyle bir özel koleksiyon uygularken, `Collection<T>` tarafından belirlenen API düzenine ve mümkün olduğunca yakından `ReadOnlyCollection<T>` uygulayın. Diğer bir deyişle, aynı üyeleri açıkça uygular, parametreleri bu iki koleksiyon gibi adlandırın ve daha fazlasını yapın.  
  
 **✓ CONSIDER** nongeneric koleksiyonu arabirimler uygulama (`IList` ve `ICollection`) koleksiyon genellikle API'leri için girdi olarak bu arabirimleri alma geçirilir durumunda.  
  
 **X AVOID** koleksiyon arabirimleri türlerinde bir koleksiyon kavramı, ilgisiz karmaşık API'leri ile uygulama.  
  
 **X DO NOT** nongeneric temel koleksiyonlarından gibi devral `CollectionBase`. Bunun yerine `Collection<T>`, `ReadOnlyCollection<T>`ve `KeyedCollection<TKey,TItem>` kullanın.  
  
### <a name="naming-custom-collections"></a>Özel koleksiyonları adlandırma  
 Koleksiyonlar (`IEnumerable`uygulayan türler) genellikle iki nedenden dolayı oluşturulur: (1) yapıya özgü işlemlere sahip yeni bir veri yapısı ve genellikle varolan veri yapılarından (örn., <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>) ve (2) belirli bir öğe kümesini tutmak için özel bir koleksiyon oluşturmak için (örn., <xref:System.Collections.Specialized.StringCollection>). Veri yapıları genellikle uygulamaların ve kitaplıkların iç uygulamalarında kullanılır. Özel Koleksiyonlar genellikle API 'lerde (özellik ve parametre türleri olarak) gösterilmelidir.  
  
 **✓ DO** uygulama soyutlamalar adlarında "Sözlük" soneki kullanan `IDictionary` veya `IDictionary<TKey,TValue>`.  
  
 **✓ DO** uygulama türleri adlarında "Toplama" soneki kullanan `IEnumerable` (veya bunların alt öğeleri) ve öğelerin listesini temsil eden.  
  
 **✓ DO** özel veri yapıları için uygun veri yapısı adını kullanın.  
  
 **X AVOID** koleksiyonu soyutlamalar adlarında "LinkedList" veya "Hashtable," gibi belirli bir uygulamaya olduğunu belirtmek sonekleri kullanarak.  
  
 **✓ CONSIDER** koleksiyon adları öğesi türünün adı ile önek. Örneğin, `Address` türünde öğeleri depolayan bir koleksiyon (`IEnumerable<Address>`uygulayan) `AddressCollection`olarak adlandırılmalıdır. Öğe türü bir arabirimse, öğe türünün "I" öneki atlanabilir. Bu nedenle, <xref:System.IDisposable> öğelerinin bir koleksiyonu `DisposableCollection`çağrılabilir.  
  
 **✓ CONSIDER** karşılık gelen bir yazılabilir koleksiyon eklenebilir ya da Framework'te zaten varsa, salt okunur koleksiyonlar adlarında "Salt okunur" önekini kullanarak.  
  
 Örneğin, salt okunurdur bir dize koleksiyonu `ReadOnlyStringCollection`çağrılmalıdır.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
