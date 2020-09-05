---
ms.openlocfilehash: ccba3cf98a1ca9e199d9a48f00e254bf34b93f72
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496449"
---
### <a name="binaryformatter-can-fail-to-find-type-from-loadfrom-context"></a>BinaryFormatter, LoadFrom bağlamından tür bulamıyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 itibariyle, bir dizi değişiklik, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> LoadFrom bağlamına yüklenmiş türlerin serisini kaldırmak için kullanılırken seri durumundan çıkarma farklılıklarına neden olabilir. Bu değişiklikler, yeni yollarla, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> daha sonra bu tür için seri durumdan çıkarma denemesi yapıldığında farklı davranışa neden olan bir türü yüklemeleridir. Varsayılan serileştirme Bağlayıcısı LoadFrom bağlamını otomatik olarak aramaz, ancak bu, XmlSerializer 'ın eski davranışına göre bazı koşullarda çalıştıolabilir. Değişiklikler nedeniyle, bir tür farklı bir bağlamda yüklenmiş bir derlemeden yüklenirken, bir durum oluşturulabilir <xref:System.IO.FileNotFoundException?displayProperty=fullName> .

#### <a name="suggestion"></a>Öneri

Bu özel durum görülecektir, <code>Binder</code> öğesinin özelliği <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> doğru türü bulacak bir özel cilde ayarlanabilir.<pre><code class="lang-csharp">var formatter = new BinaryFormatter { Binder = new TypeFinderBinder() }&#13;&#10;</code></pre>Ve ardından özel bağlayıcı:<pre><code class="lang-csharp">public class TypeFinderBinder : SerializationBinder&#13;&#10;{&#13;&#10;private static readonly string s_assemblyName = Assembly.GetExecutingAssembly().FullName;&#13;&#10;&#13;&#10;public override Type BindToType(string assemblyName, string typeName)&#13;&#10;{&#13;&#10;return Type.GetType(String.Format(CultureInfo.InvariantCulture, &quot;{0}, {1}&quot;, typeName, s_assemblyName));&#13;&#10;}&#13;&#10;}&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter`
- `M:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)`

-->
