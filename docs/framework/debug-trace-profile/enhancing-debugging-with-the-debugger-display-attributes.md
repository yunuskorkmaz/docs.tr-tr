---
title: Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- debugger, display attributes
- DebuggerTypeProxyAttribute attribute
- debugging [.NET Framework], debugger display attributes
- DebuggerDisplayAttribute attribute
- display attributes for debugger
- DebuggerBrowsableAttribute attribute
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aff2dd26db4abb892b2fc775052b6e833aa25267
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754706"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="befb8-102">Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme</span><span class="sxs-lookup"><span data-stu-id="befb8-102">Enhancing Debugging with the Debugger Display Attributes</span></span>

<span data-ttu-id="befb8-103">Hata ayıklayıcı görüntü öznitelikleri izin Geliştirici belirtir ve çalışma zamanı davranışını en iyi şekilde anlayan, tür, ne de belirtmek için bu tür bir hata ayıklayıcıda zaman görüntülendiği gibi görünecektir.</span><span class="sxs-lookup"><span data-stu-id="befb8-103">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="befb8-104">Ayrıca, hata ayıklayıcı görüntüleme sağlayan öznitelikler bir `Target` özelliği kaynak kod bilgisi olmadan kullanıcılar tarafından derleme düzeyinde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="befb8-104">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="befb8-105"><xref:System.Diagnostics.DebuggerDisplayAttribute> Özniteliği bir tür veya üye hata ayıklayıcı değişken pencerelerinde nasıl görüntüleneceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="befb8-105">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="befb8-106"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Özelliği hata ayıklayıcı değişken pencerelerinde görüntülenen ya da öznitelik varsa ve bir alanın nasıl belirler.</span><span class="sxs-lookup"><span data-stu-id="befb8-106">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="befb8-107"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Öznitelik türü hata ayıklayıcı pencerelerinde görüntülenen şekilde değiştirir ve bir yedek tür ya da bir tür için bir proxy belirtir.</span><span class="sxs-lookup"><span data-stu-id="befb8-107">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="befb8-108">Bir proxy veya yedek tür sahip bir değişken görüntülediğinizde, proxy özgün türü hata ayıklayıcı görüntü penceresinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="befb8-108">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window.</span></span> <span data-ttu-id="befb8-109">Proxy türü yalnızca genel üyeleri hata ayıklayıcı değişken penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="befb8-109">The debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="befb8-110">Özel üyeler görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="befb8-110">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="befb8-111">DebuggerDisplayAttribute kullanma</span><span class="sxs-lookup"><span data-stu-id="befb8-111">Using the DebuggerDisplayAttribute</span></span>  

<span data-ttu-id="befb8-112"><xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Oluşturucusu olan tek bir bağımsız değişken: değer sütununda görüntülenecek bir dize türü örnekleri.</span><span class="sxs-lookup"><span data-stu-id="befb8-112">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="befb8-113">Bu dize, küme ayraçları içerebilir ({ve}).</span><span class="sxs-lookup"><span data-stu-id="befb8-113">This string can contain braces ({ and }).</span></span> <span data-ttu-id="befb8-114">Bir çift küme ayraçlarının içindeki metni ifade olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="befb8-114">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="befb8-115">Örneğin, aşağıdaki C# kodu neden "sayısı = 4" örneği için hata ayıklayıcı görüntü genişletmek için artı işaretini (+) seçili olduğunda görüntülenecek `MyHashtable`.</span><span class="sxs-lookup"><span data-stu-id="befb8-115">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

<span data-ttu-id="befb8-116">Deyimde başvurulan özelliklerine uygulanan öznitelikleri işlenmez.</span><span class="sxs-lookup"><span data-stu-id="befb8-116">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="befb8-117">C# derleyicisi, genel bir ifade yalnızca örtük erişim bu başvuru hedef türünün geçerli örneğe sahip izin verilir.</span><span class="sxs-lookup"><span data-stu-id="befb8-117">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="befb8-118">İfade sınırlıdır; diğer adlar, Yereller ve işaretçileri için erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="befb8-118">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="befb8-119">C# kodunda, örtük erişimi olan ayraçlar arasındaki genel bir ifade kullanabilirsiniz `this` yalnızca hedef türü geçerli örneği için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="befb8-119">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>

<span data-ttu-id="befb8-120">Örneğin, bir C# nesnesi geçersiz kılınan bir varsa `ToString()`, hata ayıklayıcı geçersiz kılma işlemini çağırın ve standart yerine sonucu göster `{<typeName>}.` siz kıldıysanız Thus `ToString()`, kullanın gerekmez <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="befb8-120">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="befb8-121">Her ikisi de kullanırsanız <xref:System.Diagnostics.DebuggerDisplayAttribute> özniteliği önceliklidir `ToString()` geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="befb8-121">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>

## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="befb8-122">DebuggerBrowsableAttribute kullanma</span><span class="sxs-lookup"><span data-stu-id="befb8-122">Using the DebuggerBrowsableAttribute</span></span>
 <span data-ttu-id="befb8-123">Uygulama <xref:System.Diagnostics.DebuggerBrowsableAttribute> bir alan veya özellik hata ayıklayıcı penceresinde görüntülenecek alan veya özellik nasıl olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="befb8-123">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="befb8-124">Bu öznitelik için oluşturucu birini alır <xref:System.Diagnostics.DebuggerBrowsableState> aşağıdaki durumlardan biriyle belirten numaralandırma değerlerinden:</span><span class="sxs-lookup"><span data-stu-id="befb8-124">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>

- <span data-ttu-id="befb8-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> Üye verileri penceresinde görüntülenmez gösterir.</span><span class="sxs-lookup"><span data-stu-id="befb8-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="befb8-126">Örneğin, bu değeri kullanarak <xref:System.Diagnostics.DebuggerBrowsableAttribute> üzerinde bir alan, alanın bu hiyerarşisinden kaldırır; türü örneği için (+) artı işaretine tıklayarak kapsayan türdeki genişlettiğinizde alan gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="befb8-126">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>

- <span data-ttu-id="befb8-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> üye görüntülenmez ancak varsayılan olarak genişletilmiş değil gösterir.</span><span class="sxs-lookup"><span data-stu-id="befb8-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="befb8-128">Bu varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="befb8-128">This is the default behavior.</span></span>

- <span data-ttu-id="befb8-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> üye gösterilmez, ancak bir dizi veya koleksiyon olması durumunda, bağlı nesneler görüntülenir gösterir.</span><span class="sxs-lookup"><span data-stu-id="befb8-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>

> [!NOTE]
>  <span data-ttu-id="befb8-130"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Visual Basic'te .NET Framework sürüm 2.0 tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="befb8-130">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>

<span data-ttu-id="befb8-131">Aşağıdaki kod örneği, kullanımını gösterir <xref:System.Diagnostics.DebuggerBrowsableAttribute> sınıfı için hata ayıklama penceresinde görüntülenmesini aşağıdaki özellik önlemek için.</span><span class="sxs-lookup"><span data-stu-id="befb8-131">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="befb8-132">DebuggerTypeProxy kullanma</span><span class="sxs-lookup"><span data-stu-id="befb8-132">Using the DebuggerTypeProxy</span></span>
 <span data-ttu-id="befb8-133">Kullanım <xref:System.Diagnostics.DebuggerTypeProxyAttribute> özniteliği önemli ölçüde ve temel bir tür hata ayıklama görünümünü değiştirebilirsiniz, ancak türü değiştirilmemesi gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="befb8-133">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="befb8-134"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Öznitelik, bir türü için Görünüm türü için uygun hale getirmek bir geliştirici izin görünen proxy belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="befb8-134">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="befb8-135">Gibi bu öznitelik <xref:System.Diagnostics.DebuggerDisplayAttribute>, bu durumda derleme düzeyinde kullanılabilir <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> özelliği proxy kullanılacak türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="befb8-135">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="befb8-136">Bu öznitelik türü özniteliği uygulandığı içinde oluşan özel bir iç içe türü belirttiğinden önerilen kullanımdır.</span><span class="sxs-lookup"><span data-stu-id="befb8-136">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="befb8-137">Bir tür görüntülendiğinde, bu öznitelik için bir ifade değerlendiricisi destekler görüntüleyiciler yazın denetler.</span><span class="sxs-lookup"><span data-stu-id="befb8-137">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="befb8-138">Öznitelik bulunursa, ifade değerlendiricisi görünen proxy türü özniteliği uygulandığı türünün yerini alır.</span><span class="sxs-lookup"><span data-stu-id="befb8-138">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>

 <span data-ttu-id="befb8-139">Zaman <xref:System.Diagnostics.DebuggerTypeProxyAttribute> varsa, proxy türü yalnızca genel üyeleri hata ayıklayıcı değişken penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="befb8-139">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="befb8-140">Özel üyeler görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="befb8-140">Private members are not displayed.</span></span> <span data-ttu-id="befb8-141">Veri penceresi davranışını özniteliği Gelişmiş görünümler tarafından değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="befb8-141">The behavior of the data window is not changed by attribute-enhanced views.</span></span>

 <span data-ttu-id="befb8-142">Ya da türü bir veri penceresinde yanındaki artı işaretini (+) tıklayarak kullanıcı veya uygulamanın nesne genişletilir kadar gereksiz performans cezalarını önlemek için görüntü proxy özniteliklerini işlenmez <xref:System.Diagnostics.DebuggerBrowsableAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="befb8-142">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="befb8-143">Bu nedenle, hiçbir öznitelik görüntü türünü uygulanması önerilir.</span><span class="sxs-lookup"><span data-stu-id="befb8-143">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="befb8-144">Öznitelikleri olabilir ve görüntü türünü gövdesinden uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="befb8-144">Attributes can and should be applied within the body of the display type.</span></span>

 <span data-ttu-id="befb8-145">Aşağıdaki kod örneği, kullanımını gösterir <xref:System.Diagnostics.DebuggerTypeProxyAttribute> hata ayıklayıcı görüntü proxy olarak kullanılacak bir tür belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="befb8-145">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>

```csharp
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable : Hashtable
{
    private const string TestString =
        "This should not appear in the debug window.";

    internal class HashtableDebugView
    {
        private Hashtable hashtable;
        public const string TestStringProxy =
            "This should appear in the debug window.";

        // The constructor for the type proxy class must have a
        // constructor that takes the target type as a parameter.
        public HashtableDebugView(Hashtable hashtable)
        {
            this.hashtable = hashtable;
        }
    }
}
```

## <a name="example"></a><span data-ttu-id="befb8-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="befb8-146">Example</span></span>

### <a name="description"></a><span data-ttu-id="befb8-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="befb8-147">Description</span></span>

<span data-ttu-id="befb8-148">Aşağıdaki kod örneği uygulanması sonucu görmek için Visual Studio'da görüntülenebilir <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, ve <xref:System.Diagnostics.DebuggerTypeProxyAttribute> öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="befb8-148">The following code example can be viewed in Visual Studio to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>

### <a name="code"></a><span data-ttu-id="befb8-149">Kod</span><span class="sxs-lookup"><span data-stu-id="befb8-149">Code</span></span>

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="befb8-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="befb8-150">See also</span></span>

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>