---
title: Koleksiyonlar için yönergeler
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: cc853be2310cf72c4eb559f625c6a37a44ed7db8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276055"
---
# <a name="guidelines-for-collections"></a>Koleksiyonlar için yönergeler
Özellikle bir nesne grubunu işlemek için tasarlanan herhangi bir tür, bir koleksiyon olarak düşünülebilir. Bu tür türler için neredeyse her zaman uygundur <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> . Bu bölümde, bu arabirimlerin yalnızca birini veya her ikisini de koleksiyonlar olarak uygulayan türler dikkate aldık.

 ❌Ortak API 'lerde zayıf türsüz koleksiyonlar kullanmayın.

 Koleksiyon öğelerini temsil eden tüm dönüş değerlerinin ve parametrelerinin türü, temel türlerinden hiçbirini değil, tam öğe türü olmalıdır (Bu yalnızca koleksiyonun genel üyeleri için geçerlidir).

 ❌<xref:System.Collections.ArrayList> <xref:System.Collections.Generic.List%601> Ortak API 'leri kullanmayın.

 Bu türler, genel API 'lerde değil, iç uygulamada kullanılmak üzere tasarlanan veri yapılarıdır. `List<T>`, API 'lerin ve esnekliğin Temizleme maliyetiyle performans ve güç için iyileştirilmiştir. Örneğin, öğesini döndürdüğünüzde `List<T>` , istemci kodu koleksiyonu değiştirdiğinde hiçbir zaman bildirim alamazsınız. Ayrıca, çok sayıda `List<T>` <xref:System.Collections.Generic.List%601.BinarySearch%2A> senaryoda yararlı olmayan veya geçerli olmayan birçok üye sunar. Aşağıdaki iki bölümde, genel API 'lerde kullanılmak üzere özel olarak tasarlanan türler (soyutlamalar) açıklanır.

 ❌`Hashtable` `Dictionary<TKey,TValue>` Ortak API 'leri kullanmayın.

 Bu türler, iç uygulamada kullanılmak üzere tasarlanan veri yapılarıdır. Ortak API 'Ler <xref:System.Collections.IDictionary> , `IDictionary <TKey, TValue>` arabirimlerinden birini ya da her ikisini birden uygulayan özel bir tür kullanmalıdır.

 ❌<xref:System.Collections.Generic.IEnumerator%601> <xref:System.Collections.IEnumerator> Bir yöntemin dönüş türü hariç, bu arabirimlerden birini uygulayan, ya da başka bir tür kullanmayın `GetEnumerator` .

 Dışındaki metotlardan döndürülen Numaralandırıcılar `GetEnumerator` ifadesiyle birlikte kullanılamaz `foreach` .

 ❌Hem hem de `IEnumerator<T>` `IEnumerable<T>` aynı türde uygulamayın. Aynı, genel olmayan arabirimler ve için geçerlidir `IEnumerator` `IEnumerable` .

## <a name="collection-parameters"></a>Koleksiyon parametreleri
 ✔️, bir parametre türü olarak mümkün olan en az özelleştirilmiş türü kullanır. Koleksiyonları parametre olarak alan çoğu üye arabirimini kullanır `IEnumerable<T>` .

 ❌<xref:System.Collections.Generic.ICollection%601> <xref:System.Collections.ICollection> Yalnızca özelliğine erişmek için parametre olarak veya parametresi kullanmaktan kaçının `Count` .

 Bunun yerine, veya öğesini kullanarak `IEnumerable<T>` `IEnumerable` nesnenin mi yoksa dinamik olarak mı kontrol ettiğine dikkat edin `ICollection<T>` `ICollection` .

## <a name="collection-properties-and-return-values"></a>Koleksiyon özellikleri ve dönüş değerleri
 ❌Ayarlanabilir koleksiyon özellikleri sağlamaın.

 Kullanıcılar, önce koleksiyonu temizleyerek ve sonra yeni içerikleri ekleyerek koleksiyonun içeriğini değiştirebilir. Tüm koleksiyonu değiştirmek ortak bir senaryodur, `AddRange` yöntemi koleksiyona sağlamayı düşünün.

 `Collection<T>` `Collection<T>` okuma/yazma koleksiyonlarını temsil eden özellikler veya dönüş değerleri için ✔️ veya alt sınıfını kullanın.

 `Collection<T>`Bazı gereksinimleri karşılamıyorsa (örn. koleksiyon uygulanmamalıdır),, <xref:System.Collections.IList> veya uygulayarak özel bir koleksiyon kullanın `IEnumerable<T>` `ICollection<T>` <xref:System.Collections.Generic.IList%601> .

 ✔️ kullanımı <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> , bir alt sınıfı `ReadOnlyCollection<T>` ya da `IEnumerable<T>` salt okunurdur koleksiyonları temsil eden özellikler veya dönüş değerleri için nadir durumlarda.

 Genel olarak, tercih edin `ReadOnlyCollection<T>` . Bir gereksinimi karşılamıyorsa (örn. koleksiyon uygulanmamalıdır),, `IList` veya uygulayarak özel bir koleksiyon kullanın `IEnumerable<T>` `ICollection<T>` `IList<T>` . Özel bir salt okuma koleksiyonu uygularsanız, `ICollection<T>.IsReadOnly` döndürmek için uygulayın `true` .

 Yalnızca ileri düzey yineleme olduğundan desteklemek istediğiniz tek senaryonun yalnızca iletme yinelemesi olduğundan emin olmanız durumunda yalnızca ' i kullanabilirsiniz `IEnumerable<T>` .

 ✔️, koleksiyonları doğrudan kullanmak yerine genel temel koleksiyonların alt sınıflarını kullanmayı düşünün.

 Bu, daha iyi bir ad sağlar ve temel koleksiyon türlerinde bulunmayan yardımcı Üyeler ekler. Bu, özellikle üst düzey API 'Ler için geçerlidir.

 ✔️ `Collection<T>` `ReadOnlyCollection<T>` çok yaygın olarak kullanılan yöntemler ve özelliklerden veya bir alt SıNıFıNı döndürmeyi düşünün.

 Bu, daha sonra yardımcı yöntemler eklemenizi veya koleksiyon uygulamasını değiştirmenizi mümkün hale getirir.

 Koleksiyonda depolanan öğelerin benzersiz anahtarları (adlar, kimlikler vb.) varsa, bir anahtarlı koleksiyon kullanmayı düşünün ✔️. Anahtarlı koleksiyonlar, hem tamsayı hem de anahtar tarafından dizinlenebilir ve genellikle Devralındığı şekilde uygulanır `KeyedCollection<TKey,TItem>` .

 Anahtarlı koleksiyonlar genellikle daha büyük bellek baskılarına sahiptir ve bellek ek yükü anahtarlara sahip olmanın avantajlarından yararlanıyorsa kullanılmamalıdır.

 ❌Koleksiyon özelliklerinden veya koleksiyonlar döndüren metotlardan null değerler döndürme. Bunun yerine boş bir koleksiyon veya boş bir dizi döndürün.

 Genel kural, null ve boş (0 öğe) koleksiyonlarının veya dizilerinin aynı kabul edilmesidir.

### <a name="snapshots-versus-live-collections"></a>Anlık görüntüler ve canlı Koleksiyonlar
 Bir zaman noktasında bir durumu temsil eden koleksiyonlara anlık görüntü koleksiyonları denir. Örneğin, bir veritabanı sorgusundan döndürülen satırları içeren bir koleksiyon bir anlık görüntü olacaktır. Geçerli durumu her zaman temsil eden koleksiyonlara canlı koleksiyonlar denir. Örneğin, bir `ComboBox` öğe koleksiyonu canlı bir koleksiyondur.

 ❌Özelliklerden anlık görüntü koleksiyonları döndürme. Özellikler canlı koleksiyonlar döndürmelidir.

 Özellik alıcıları çok hafif işlemler olmalıdır. Anlık görüntü döndürmek için bir O (n) işleminde iç koleksiyonun kopyasının oluşturulması gerekir.

 ✔️ `IEnumerable<T>` geçici olan (yani, koleksiyonu açıkça değiştirmeden değişen) koleksiyonları temsil eden bir anlık görüntü koleksiyonu veya canlı (veya alt türü) kullanın.

 Genel olarak, paylaşılan bir kaynağı (örneğin, bir dizindeki dosyalar) temsil eden tüm koleksiyonlar geçici bir uygulamadır. Uygulama yalnızca ileri bir Numaralandırıcı değilse, bu tür koleksiyonlar canlı koleksiyonlar olarak uygulamak oldukça zordur veya imkansız olur.

## <a name="choosing-between-arrays-and-collections"></a>Diziler ve koleksiyonlar arasında seçim yapma
 ✔️ diziler üzerinde koleksiyonları tercih ediyor.

 Koleksiyonlar içerik üzerinde daha fazla denetim sağlar, zaman içinde gelişiyor ve daha fazla kullanılabilir. Ayrıca, diziyi kopyalama maliyeti yüksek olduğundan, salt okuma senaryolarında diziler kullanılması önerilmez. Kullanılabilirlik çalışmaları, bazı geliştiricilerin koleksiyon tabanlı API 'Leri kullanarak daha rahat olduğunu göstermiştir.

 Ancak, alt düzey API 'Ler geliştiriyorsanız, okuma-yazma senaryolarında dizileri kullanmak daha iyi olabilir. Diziler, çalışma kümesini azaltmaya yardımcı olan daha küçük bir bellek parmak izine sahiptir ve çalışma zamanı tarafından iyileştirildiğinden, bir dizideki öğelere erişim daha hızlıdır.

 ✔️ bellek tüketimini en aza indirmek ve performansı en üst düzeye çıkarmak için alt düzey API 'lerde dizileri kullanmayı düşünün.

 ✔️ bayt koleksiyonları yerine bayt dizilerini kullanın.

 ❌Özellik alıcısı her çağrıldığında özelliğin yeni bir dizi (örn. iç dizinin bir kopyası) döndürmesi gerekiyorsa özellikler için diziler kullanmayın.

## <a name="implementing-custom-collections"></a>Özel Koleksiyonlar uygulama
 `Collection<T>` `ReadOnlyCollection<T>` yeni koleksiyonlar tasarlarken,, veya ' den devralmayı düşünün ✔️ `KeyedCollection<TKey,TItem>` .

 `IEnumerable<T>`yeni koleksiyonlar tasarlarken uygulamayı ✔️. Uygulamayı, `ICollection<T>` hatta `IList<T>` mantıklı olduğunu düşünün.

 Böyle bir özel koleksiyon uygularken, tarafından sağlanan API modelini `Collection<T>` ve mümkün olduğunca `ReadOnlyCollection<T>` yakından izleyin. Diğer bir deyişle, aynı üyeleri açıkça uygular, parametreleri bu iki koleksiyon gibi adlandırın ve daha fazlasını yapın.

 ✔️ Genel olmayan koleksiyon arabirimlerini uygulamayı düşünün ( `IList` ve `ICollection` ) koleksiyon genellikle bu arabirimleri giriş olarak alan API 'lere geçiriliyorsa.

 ❌Koleksiyon kavramıyla ilgisi olmayan karmaşık API 'Ler olan türlerde koleksiyon arabirimleri uygulamaktan KAÇıNıN.

 ❌Gibi genel olmayan temel koleksiyonlardan devralma `CollectionBase` . `Collection<T>`Yerine, `ReadOnlyCollection<T>` ve kullanın `KeyedCollection<TKey,TItem>` .

### <a name="naming-custom-collections"></a>Özel koleksiyonları adlandırma
 Koleksiyonlar (uygulayan türler `IEnumerable` ) genellikle iki nedenden dolayı oluşturulur: (1) yapıya özgü işlemlere sahip yeni bir veri yapısı ve genellikle var olan veri yapılarından (örn.,,, <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.LinkedList%601> <xref:System.Collections.Generic.Stack%601> ) ve (2) belirli bir öğe kümesinin tutulması için özel bir koleksiyon oluşturmak için (örn. <xref:System.Collections.Specialized.StringCollection> ). Veri yapıları genellikle uygulamaların ve kitaplıkların iç uygulamalarında kullanılır. Özel Koleksiyonlar genellikle API 'lerde (özellik ve parametre türleri olarak) gösterilmelidir.

 ✔️, veya uygulayan soyutlamalar adlarında "Sözlük" sonekini kullanın `IDictionary` `IDictionary<TKey,TValue>` .

 ✔️, `IEnumerable` (veya alt öğelerinden herhangi biri) uygulayan ve öğelerin listesini temsil eden tür adlarında "Collection" sonekini kullanır.

 ✔️ özel veri yapıları için uygun veri yapısı adını kullanın.

 ❌Koleksiyon soyutlamaları adlarında "LinkedList" veya "Hashtable" gibi belirli bir uygulamadan oluşan herhangi bir sonek kullanmaktan kaçının.

 ✔️ koleksiyon adlarını öğe türü adı ile önek olarak kullanmayı düşünün. Örneğin, türü öğeleri depolayan bir koleksiyon `Address` (uygulama) olarak `IEnumerable<Address>` adlandırılmalıdır `AddressCollection` . Öğe türü bir arabirimse, öğe türünün "I" öneki atlanabilir. Bu nedenle, bir <xref:System.IDisposable> öğe koleksiyonu çağrılabilir `DisposableCollection` .

 ✔️ ilgili yazılabilir bir koleksiyon eklenirse veya çerçevede zaten mevcutsa, salt okunur koleksiyonların adlarında "ReadOnly" önekini kullanmayı düşünün.

 Örneğin, salt okunurdur bir dize koleksiyonu çağrılmalıdır `ReadOnlyStringCollection` .

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Kullanım yönergeleri](usage-guidelines.md)
