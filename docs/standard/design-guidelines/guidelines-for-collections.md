---
title: Koleksiyonlar için yönergeler
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: 50497de6569b448ab036af8a1fbf76a47565e2bb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741870"
---
# <a name="guidelines-for-collections"></a>Koleksiyonlar için yönergeler
Özellikle bir nesne grubunu işlemek için tasarlanan herhangi bir tür, bir koleksiyon olarak düşünülebilir. <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601>uygulamak üzere bu tür türler için neredeyse her zaman uygundur, bu nedenle bu arabirimlerin yalnızca birini ya da her ikisini de koleksiyonlar olarak uygulayan türleri göz önünde bulundurarız.

 ❌ ortak API 'lerde zayıf türsüz koleksiyonlar kullanmayın.

 Koleksiyon öğelerini temsil eden tüm dönüş değerlerinin ve parametrelerinin türü, temel türlerinden hiçbirini değil, tam öğe türü olmalıdır (Bu yalnızca koleksiyonun genel üyeleri için geçerlidir).

 ❌ ortak API 'lerde <xref:System.Collections.ArrayList> veya <xref:System.Collections.Generic.List%601> kullanmayın.

 Bu türler, genel API 'lerde değil, iç uygulamada kullanılmak üzere tasarlanan veri yapılarıdır. `List<T>`, API 'lerin ve esnekliğin Temizleme maliyetiyle performans ve güç için iyileştirilmiştir. Örneğin, `List<T>`döndürmeniz durumunda, istemci kodu koleksiyonu değiştirdiğinde hiçbir zaman bildirim alamazsınız. Ayrıca, çok sayıda senaryoda yararlı olmayan veya geçerli olmayan <xref:System.Collections.Generic.List%601.BinarySearch%2A>gibi birçok üye `List<T>` sunar. Aşağıdaki iki bölümde, genel API 'lerde kullanılmak üzere özel olarak tasarlanan türler (soyutlamalar) açıklanır.

 ❌ ortak API 'lerde `Hashtable` veya `Dictionary<TKey,TValue>` kullanmayın.

 Bu türler, iç uygulamada kullanılmak üzere tasarlanan veri yapılarıdır. Ortak API 'Ler <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`veya arabirimlerin birini ya da her ikisini birden uygulayan özel bir tür kullanmalıdır.

 ❌, bir `GetEnumerator` yönteminin dönüş türü dışında, bu arabirimlerden birini uygulayan <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>veya başka herhangi bir türü kullanmayın.

 `GetEnumerator` dışındaki yöntemlerden Numaralandırıcı döndüren türler `foreach` ifadesiyle kullanılamaz.

 ❌, `IEnumerator<T>` ve `IEnumerable<T>` aynı türde uygulamaz. Aynı, genel olmayan arabirimler `IEnumerator` ve `IEnumerable`için de geçerlidir.

## <a name="collection-parameters"></a>Koleksiyon parametreleri
 ✔️, bir parametre türü olarak mümkün olan en az özelleştirilmiş türü kullanır. Koleksiyonları parametre olarak alan çoğu üye `IEnumerable<T>` arabirimini kullanır.

 ❌ <xref:System.Collections.Generic.ICollection%601> veya <xref:System.Collections.ICollection> `Count` özelliğine erişmek için parametre olarak kullanmaktan kaçının.

 Bunun yerine, `IEnumerable<T>` veya `IEnumerable` kullanmayı ve nesnenin `ICollection<T>` veya `ICollection`uygulayıp uygulamadığını dinamik olarak denetlemeyi düşünün.

## <a name="collection-properties-and-return-values"></a>Koleksiyon özellikleri ve dönüş değerleri
 ❌ ayarlanabilir koleksiyon özellikleri sağlamaz.

 Kullanıcılar, önce koleksiyonu temizleyerek ve sonra yeni içerikleri ekleyerek koleksiyonun içeriğini değiştirebilir. Tüm koleksiyonu değiştirmek ortak bir senaryodur, koleksiyonda `AddRange` yöntemi sağlamayı düşünün.

 ✔️, okuma/yazma koleksiyonlarını temsil eden özellikler veya dönüş değerleri için `Collection<T>` veya `Collection<T>` bir alt sınıfı kullanın.

 `Collection<T>`, bazı gereksinimleri karşılamıyorsa (örneğin, koleksiyon <xref:System.Collections.IList>uygulamamalı), `IEnumerable<T>`, `ICollection<T>`veya <xref:System.Collections.Generic.IList%601>uygulayarak özel bir koleksiyon kullanın.

 ✔️ <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, `ReadOnlyCollection<T>`veya nadir durumlarda, salt okunurdur koleksiyonları temsil eden özellikler veya dönüş değerleri için `IEnumerable<T>` kullanın.

 Genel olarak `ReadOnlyCollection<T>`tercih edin. Bir gereksinimi karşılamıyorsa (örneğin, koleksiyon `IList`uygulamamalı), `IEnumerable<T>`, `ICollection<T>`veya `IList<T>`uygulayarak özel bir koleksiyon kullanın. Özel bir salt okuma koleksiyonu uygularsanız, `true`döndürmek için `ICollection<T>.IsReadOnly` uygulayın.

 Yalnızca ileri düzey yineleme olduğundan, desteklemek istediğiniz tek senaryonun yalnızca iletme yinelemesi olduğundan emin olmanız durumunda yalnızca `IEnumerable<T>`kullanabilirsiniz.

 ✔️, koleksiyonları doğrudan kullanmak yerine genel temel koleksiyonların alt sınıflarını kullanmayı düşünün.

 Bu, daha iyi bir ad sağlar ve temel koleksiyon türlerinde bulunmayan yardımcı Üyeler ekler. Bu, özellikle üst düzey API 'Ler için geçerlidir.

 ✔️, yaygın olarak kullanılan yöntemler ve özelliklerden `Collection<T>` veya `ReadOnlyCollection<T>` bir alt sınıfını döndürmeyi düşünün.

 Bu, daha sonra yardımcı yöntemler eklemenizi veya koleksiyon uygulamasını değiştirmenizi mümkün hale getirir.

 Koleksiyonda depolanan öğelerin benzersiz anahtarları (adlar, kimlikler vb.) varsa, bir anahtarlı koleksiyon kullanmayı düşünün ✔️. Anahtarlı koleksiyonlar, hem bir tamsayı hem de anahtar tarafından dizinlenebilir ve genellikle `KeyedCollection<TKey,TItem>`devralınarak uygulanabilir koleksiyonlardır.

 Anahtarlı koleksiyonlar genellikle daha büyük bellek baskılarına sahiptir ve bellek ek yükü anahtarlara sahip olmanın avantajlarından yararlanıyorsa kullanılmamalıdır.

 ❌ koleksiyon özelliklerinden veya koleksiyonlar döndüren metotlardan null değerler döndürmez. Bunun yerine boş bir koleksiyon veya boş bir dizi döndürün.

 Genel kural, null ve boş (0 öğe) koleksiyonlarının veya dizilerinin aynı kabul edilmesidir.

### <a name="snapshots-versus-live-collections"></a>Anlık görüntüler ve canlı Koleksiyonlar
 Bir zaman noktasında bir durumu temsil eden koleksiyonlara anlık görüntü koleksiyonları denir. Örneğin, bir veritabanı sorgusundan döndürülen satırları içeren bir koleksiyon bir anlık görüntü olacaktır. Geçerli durumu her zaman temsil eden koleksiyonlara canlı koleksiyonlar denir. Örneğin, `ComboBox` öğelerinin bir koleksiyonu canlı bir koleksiyondur.

 ❌, özelliklerden anlık görüntü koleksiyonları döndürmez. Özellikler canlı koleksiyonlar döndürmelidir.

 Özellik alıcıları çok hafif işlemler olmalıdır. Anlık görüntü döndürmek için bir O (n) işleminde iç koleksiyonun kopyasının oluşturulması gerekir.

 ✔️ geçici olan (yani, koleksiyonu açıkça değiştirmeden değişen) koleksiyonları temsil etmek için bir anlık görüntü koleksiyonu veya bir canlı `IEnumerable<T>` (ya da onun alt türü) kullanın.

 Genel olarak, paylaşılan bir kaynağı (örneğin, bir dizindeki dosyalar) temsil eden tüm koleksiyonlar geçici bir uygulamadır. Uygulama yalnızca ileri bir Numaralandırıcı değilse, bu tür koleksiyonlar canlı koleksiyonlar olarak uygulamak oldukça zordur veya imkansız olur.

## <a name="choosing-between-arrays-and-collections"></a>Diziler ve koleksiyonlar arasında seçim yapma
 ✔️ diziler üzerinde koleksiyonları tercih ediyor.

 Koleksiyonlar içerik üzerinde daha fazla denetim sağlar, zaman içinde gelişiyor ve daha fazla kullanılabilir. Ayrıca, diziyi kopyalama maliyeti yüksek olduğundan, salt okuma senaryolarında diziler kullanılması önerilmez. Kullanılabilirlik çalışmaları, bazı geliştiricilerin koleksiyon tabanlı API 'Leri kullanarak daha rahat olduğunu göstermiştir.

 Ancak, alt düzey API 'Ler geliştiriyorsanız, okuma-yazma senaryolarında dizileri kullanmak daha iyi olabilir. Diziler, çalışma kümesini azaltmaya yardımcı olan daha küçük bir bellek parmak izine sahiptir ve çalışma zamanı tarafından iyileştirildiğinden, bir dizideki öğelere erişim daha hızlıdır.

 ✔️ bellek tüketimini en aza indirmek ve performansı en üst düzeye çıkarmak için alt düzey API 'lerde dizileri kullanmayı düşünün.

 ✔️ bayt koleksiyonları yerine bayt dizilerini kullanın.

 Özellik alıcısı her çağrıldığında özelliğin yeni bir dizi (örn. bir iç dizinin kopyası) döndürmesi gerekiyorsa ❌ özellikler için diziler kullanmayın.

## <a name="implementing-custom-collections"></a>Özel Koleksiyonlar uygulama
 ✔️, yeni koleksiyonlar tasarlarken `Collection<T>`, `ReadOnlyCollection<T>`veya `KeyedCollection<TKey,TItem>` devralmayı düşünün.

 yeni koleksiyonlar tasarlarken `IEnumerable<T>` uygulama ✔️. `ICollection<T>`, hatta anlamlı olduğu yerde `IList<T>` uygulamayı düşünün.

 Böyle bir özel koleksiyon uygularken, `Collection<T>` tarafından belirlenen API düzenine ve mümkün olduğunca yakından `ReadOnlyCollection<T>` uygulayın. Diğer bir deyişle, aynı üyeleri açıkça uygular, parametreleri bu iki koleksiyon gibi adlandırın ve daha fazlasını yapın.

 Koleksiyon genellikle bu arabirimleri giriş olarak alan API 'lere geçiriliyorsa, genel olmayan koleksiyon arabirimlerini (`IList` ve `ICollection`) uygulamayı düşünün ✔️.

 ❌ koleksiyon kavramıyla ilgisi olmayan karmaşık API 'Ler olan türlerde koleksiyon arabirimleri uygulamaktan KAÇıNıN.

 ❌, `CollectionBase`gibi genel olmayan taban koleksiyonlarından kalıtımla almalardır. Bunun yerine `Collection<T>`, `ReadOnlyCollection<T>`ve `KeyedCollection<TKey,TItem>` kullanın.

### <a name="naming-custom-collections"></a>Özel koleksiyonları adlandırma
 Koleksiyonlar (`IEnumerable`uygulayan türler) genellikle iki nedenden dolayı oluşturulur: (1) yapıya özgü işlemlere sahip yeni bir veri yapısı ve genellikle varolan veri yapılarından (örn., <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>) ve (2) belirli bir öğe kümesini tutmak için özel bir koleksiyon oluşturmak için (örn., <xref:System.Collections.Specialized.StringCollection>). Veri yapıları genellikle uygulamaların ve kitaplıkların iç uygulamalarında kullanılır. Özel Koleksiyonlar genellikle API 'lerde (özellik ve parametre türleri olarak) gösterilmelidir.

 ✔️ `IDictionary` veya `IDictionary<TKey,TValue>`uygulayan soyutlamalar adlarında "Sözlük" sonekini kullanın.

 ✔️, `IEnumerable` (veya alt öğelerinden herhangi biri) uygulayan ve öğelerin bir listesini temsil eden türlerin adlarında "Collection" sonekini kullanır.

 ✔️ özel veri yapıları için uygun veri yapısı adını kullanın.

 ❌, koleksiyon soyutlamaları adlarında "LinkedList" veya "Hashtable" gibi belirli bir uygulamadan oluşan herhangi bir sonek kullanmaktan kaçının.

 ✔️ koleksiyon adlarını öğe türü adı ile önek olarak kullanmayı düşünün. Örneğin, `Address` türünde öğeleri depolayan bir koleksiyon (`IEnumerable<Address>`uygulayan) `AddressCollection`olarak adlandırılmalıdır. Öğe türü bir arabirimse, öğe türünün "I" öneki atlanabilir. Bu nedenle, <xref:System.IDisposable> öğelerinin bir koleksiyonu `DisposableCollection`çağrılabilir.

 ✔️ ilgili yazılabilir bir koleksiyon eklenirse veya çerçevede zaten mevcutsa, salt okunur koleksiyonların adlarında "ReadOnly" önekini kullanmayı düşünün.

 Örneğin, salt okunurdur bir dize koleksiyonu `ReadOnlyStringCollection`çağrılmalıdır.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
