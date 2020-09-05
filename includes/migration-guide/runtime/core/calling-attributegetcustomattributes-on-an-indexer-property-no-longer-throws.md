---
ms.openlocfilehash: f61e5670334f4d3674fd0b008d1a476b14c7ba4e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497528"
---
### <a name="calling-attributegetcustomattributes-on-an-indexer-property-no-longer-throws-ambiguousmatchexception-if-the-ambiguity-can-be-resolved-by-indexs-type"></a><span data-ttu-id="8388c-101">Bir Indexer özelliğinde Attribute. GetCustomAttributes çağrısı, belirsizlik dizinin türüne göre çözümlenebiliyorsa, artık AmbiguousMatchException oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="8388c-101">Calling Attribute.GetCustomAttributes on an indexer property no longer throws AmbiguousMatchException if the ambiguity can be resolved by index's type</span></span>

#### <a name="details"></a><span data-ttu-id="8388c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8388c-102">Details</span></span>

<span data-ttu-id="8388c-103">.NET Framework 4,6 ' den önce, <code>GetCustomAttribute(s)</code> yalnızca dizin türü tarafından başka bir özellikten farklı olan bir dizin oluşturucu özelliği çağırma bir ile sonuçlanır <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="8388c-103">Prior to the .NET Framework 4.6, calling <code>GetCustomAttribute(s)</code> on an indexer property which differed from another property only by the type of the index would result in an <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName>.</span></span> <span data-ttu-id="8388c-104">.NET Framework 4,6 ' den başlayarak özelliğin öznitelikleri doğru döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8388c-104">Beginning in the .NET Framework 4.6, the property's attributes will be correctly returned.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8388c-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="8388c-105">Suggestion</span></span>

<span data-ttu-id="8388c-106">GetCustomAttribute daha sık daha fazla çalışacağına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8388c-106">Be aware that GetCustomAttribute(s) will work more frequently now.</span></span> <span data-ttu-id="8388c-107">Bir uygulama daha önce üzerine bağlı ise, <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName> yansıma artık birden çok dizin oluşturucuyu açıkça aramak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8388c-107">If an app was previously relying on the <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName>, reflection should now be used to explicitly look for multiple indexers, instead.</span></span>

| <span data-ttu-id="8388c-108">Name</span><span class="sxs-lookup"><span data-stu-id="8388c-108">Name</span></span>    | <span data-ttu-id="8388c-109">Değer</span><span class="sxs-lookup"><span data-stu-id="8388c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8388c-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8388c-110">Scope</span></span>   |<span data-ttu-id="8388c-111">Edge</span><span class="sxs-lookup"><span data-stu-id="8388c-111">Edge</span></span>|
|<span data-ttu-id="8388c-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="8388c-112">Version</span></span>|<span data-ttu-id="8388c-113">4.6</span><span class="sxs-lookup"><span data-stu-id="8388c-113">4.6</span></span>|
|<span data-ttu-id="8388c-114">Tür</span><span class="sxs-lookup"><span data-stu-id="8388c-114">Type</span></span>|<span data-ttu-id="8388c-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="8388c-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="8388c-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="8388c-116">Affected APIs</span></span>

- <xref:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)`
- `M:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute``1(System.Reflection.MemberInfo)``
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute``1(System.Reflection.MemberInfo,System.Boolean)``
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes``1(System.Reflection.MemberInfo)``
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes``1(System.Reflection.MemberInfo,System.Boolean)``

-->
