---
ms.openlocfilehash: ccba3cf98a1ca9e199d9a48f00e254bf34b93f72
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496449"
---
### <a name="binaryformatter-can-fail-to-find-type-from-loadfrom-context"></a><span data-ttu-id="6a7fa-101">BinaryFormatter, LoadFrom bağlamından tür bulamıyor</span><span class="sxs-lookup"><span data-stu-id="6a7fa-101">BinaryFormatter can fail to find type from LoadFrom context</span></span>

#### <a name="details"></a><span data-ttu-id="6a7fa-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6a7fa-102">Details</span></span>

<span data-ttu-id="6a7fa-103">.NET Framework 4,5 itibariyle, bir dizi değişiklik, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> LoadFrom bağlamına yüklenmiş türlerin serisini kaldırmak için kullanılırken seri durumundan çıkarma farklılıklarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6a7fa-103">As of .NET Framework 4.5, a number of <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> changes may cause differences in deserialization when using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> to deserialize types that had been loaded in the LoadFrom context.</span></span> <span data-ttu-id="6a7fa-104">Bu değişiklikler, yeni yollarla, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> daha sonra bu tür için seri durumdan çıkarma denemesi yapıldığında farklı davranışa neden olan bir türü yüklemeleridir.</span><span class="sxs-lookup"><span data-stu-id="6a7fa-104">These changes are due to the new ways <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> now loads a type which causes different behavior when a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> attempts to deserialize to that type later on.</span></span> <span data-ttu-id="6a7fa-105">Varsayılan serileştirme Bağlayıcısı LoadFrom bağlamını otomatik olarak aramaz, ancak bu, XmlSerializer 'ın eski davranışına göre bazı koşullarda çalıştıolabilir.</span><span class="sxs-lookup"><span data-stu-id="6a7fa-105">The default serialization binder does not automatically search the LoadFrom context, although it may have worked in some circumstances based on the old behavior of XmlSerializer.</span></span> <span data-ttu-id="6a7fa-106">Değişiklikler nedeniyle, bir tür farklı bir bağlamda yüklenmiş bir derlemeden yüklenirken, bir durum oluşturulabilir <xref:System.IO.FileNotFoundException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="6a7fa-106">Due to the changes, when a type is being loaded from an assembly loaded in a different context, a <xref:System.IO.FileNotFoundException?displayProperty=fullName> may be thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6a7fa-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="6a7fa-107">Suggestion</span></span>

<span data-ttu-id="6a7fa-108">Bu özel durum görülecektir, <code>Binder</code> öğesinin özelliği <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> doğru türü bulacak bir özel cilde ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6a7fa-108">If this exception is seen, the <code>Binder</code> property of the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> can be set to a custom binder that will find the correct type.</span></span><pre><code class="lang-csharp">var formatter = new BinaryFormatter { Binder = new TypeFinderBinder() }&#13;&#10;</code></pre><span data-ttu-id="6a7fa-109">Ve ardından özel bağlayıcı:</span><span class="sxs-lookup"><span data-stu-id="6a7fa-109">And then the custom binder:</span></span><pre><code class="lang-csharp">public class TypeFinderBinder : SerializationBinder&#13;&#10;{&#13;&#10;private static readonly string s_assemblyName = Assembly.GetExecutingAssembly().FullName;&#13;&#10;&#13;&#10;public override Type BindToType(string assemblyName, string typeName)&#13;&#10;{&#13;&#10;return Type.GetType(String.Format(CultureInfo.InvariantCulture, &quot;{0}, {1}&quot;, typeName, s_assemblyName));&#13;&#10;}&#13;&#10;}&#13;&#10;</code></pre>

| <span data-ttu-id="6a7fa-110">Name</span><span class="sxs-lookup"><span data-stu-id="6a7fa-110">Name</span></span>    | <span data-ttu-id="6a7fa-111">Değer</span><span class="sxs-lookup"><span data-stu-id="6a7fa-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6a7fa-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="6a7fa-112">Scope</span></span>   |<span data-ttu-id="6a7fa-113">Edge</span><span class="sxs-lookup"><span data-stu-id="6a7fa-113">Edge</span></span>|
|<span data-ttu-id="6a7fa-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6a7fa-114">Version</span></span>|<span data-ttu-id="6a7fa-115">4,5</span><span class="sxs-lookup"><span data-stu-id="6a7fa-115">4.5</span></span>|
|<span data-ttu-id="6a7fa-116">Tür</span><span class="sxs-lookup"><span data-stu-id="6a7fa-116">Type</span></span>|<span data-ttu-id="6a7fa-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="6a7fa-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="6a7fa-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6a7fa-118">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter`
- `M:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)`

-->
