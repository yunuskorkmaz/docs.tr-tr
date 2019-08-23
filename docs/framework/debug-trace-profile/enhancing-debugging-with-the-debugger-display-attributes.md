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
ms.openlocfilehash: c27732de448e19c4227062706c7a7d73c98e5f19
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966870"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="a66f8-102">Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme</span><span class="sxs-lookup"><span data-stu-id="a66f8-102">Enhancing Debugging with the Debugger Display Attributes</span></span>

<span data-ttu-id="a66f8-103">Hata ayıklayıcı görüntüleme öznitelikleri tür geliştiricisinin, bu türün çalışma zamanı davranışını belirten ve en iyi anladığı, bu türün bir hata ayıklayıcıda görüntülenmesiyle nasıl görüneceğine de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a66f8-103">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="a66f8-104">Ayrıca, bir `Target` özelliği sağlayan hata ayıklayıcı görüntüleme öznitelikleri, kaynak kodu bilgisine sahip olmayan kullanıcılar tarafından derleme düzeyinde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-104">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="a66f8-105"><xref:System.Diagnostics.DebuggerDisplayAttribute> Özniteliği bir türün veya üyenin hata ayıklayıcı değişken penceresinde nasıl görüntülendiğini denetler.</span><span class="sxs-lookup"><span data-stu-id="a66f8-105">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="a66f8-106">Özniteliği <xref:System.Diagnostics.DebuggerBrowsableAttribute> , bir alanın veya özelliğin hata ayıklayıcı değişkeni penceresinde görüntülenip görüntülenmeyeceğini ve nasıl görüntüleneceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="a66f8-106">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="a66f8-107"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Öznitelik, bir tür için alternatif bir tür veya ara sunucu belirtir ve tür hata ayıklayıcı penceresinde görüntülenme şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-107">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="a66f8-108">Proxy veya yedek türü olan bir değişkeni görüntülediğinizde, proxy, hata ayıklayıcı görüntü penceresinde özgün tür için temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a66f8-108">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window.</span></span> <span data-ttu-id="a66f8-109">Hata ayıklayıcı değişkeni penceresi yalnızca proxy türünün ortak üyelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a66f8-109">The debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="a66f8-110">Özel Üyeler gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="a66f8-110">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="a66f8-111">DebuggerDisplayAttribute kullanma</span><span class="sxs-lookup"><span data-stu-id="a66f8-111">Using the DebuggerDisplayAttribute</span></span>  

<span data-ttu-id="a66f8-112"><xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Oluşturucunun tek bir bağımsız değişkeni vardır: tür örnekleri için değer sütununda görüntülenecek dize.</span><span class="sxs-lookup"><span data-stu-id="a66f8-112">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="a66f8-113">Bu dize, küme ayracı ({ve}) içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-113">This string can contain braces ({ and }).</span></span> <span data-ttu-id="a66f8-114">Küme ayracı çiftindeki metin bir ifade olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-114">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="a66f8-115">Örneğin, aşağıdaki C# kod, bir örneği için hata ayıklayıcı görüntüsünü genişletmek için artı işareti (+) seçildiğinde, "Count = 4" değerinin `MyHashtable`görüntülenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="a66f8-115">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

<span data-ttu-id="a66f8-116">İfadede başvurulan özelliklere uygulanan öznitelikler işlenmedi.</span><span class="sxs-lookup"><span data-stu-id="a66f8-116">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="a66f8-117">C# Derleyici için, hedef türün geçerli örneğine yönelik bu başvuruya yalnızca örtülü erişimi olan genel bir ifadeye izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-117">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="a66f8-118">İfade sınırlı; diğer adlar, Yereller veya işaretçiler için erişim yoktur.</span><span class="sxs-lookup"><span data-stu-id="a66f8-118">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="a66f8-119">Kod C# içinde, yalnızca hedef türün geçerli örneğinin `this` işaretçisine örtük erişimi olan küme ayraçları arasında genel bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a66f8-119">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>

<span data-ttu-id="a66f8-120">C# Örneğin, bir nesne geçersiz kılınmışsa `ToString()`, hata ayıklayıcı geçersiz kılmayı çağırır ve standart `{<typeName>}.` yerine sonucunu gösterir. bu nedenle, geçersiz kılındıysanız `ToString()`, kullanmanız <xref:System.Diagnostics.DebuggerDisplayAttribute>gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a66f8-120">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="a66f8-121">Her ikisini de kullanırsanız, <xref:System.Diagnostics.DebuggerDisplayAttribute> öznitelik `ToString()` geçersiz kılmanın üzerine gelir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-121">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>

## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="a66f8-122">DebuggerBrowsableAttribute kullanma</span><span class="sxs-lookup"><span data-stu-id="a66f8-122">Using the DebuggerBrowsableAttribute</span></span>
 <span data-ttu-id="a66f8-123"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Alan veya özelliğin hata ayıklayıcı penceresinde nasıl görüntüleneceğini belirtmek için bir alan veya özelliğe uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a66f8-123">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="a66f8-124">Bu özniteliğin Oluşturucusu, aşağıdaki durumlardan birini belirten <xref:System.Diagnostics.DebuggerBrowsableState> sabit listesi değerlerinden birini alır:</span><span class="sxs-lookup"><span data-stu-id="a66f8-124">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>

- <span data-ttu-id="a66f8-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never>üyenin veri penceresinde görüntülenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="a66f8-126">Örneğin, bir alan için <xref:System.Diagnostics.DebuggerBrowsableAttribute> bu değerin kullanılması alanı hiyerarşiden kaldırır; tür örneği için artı işaretine (+) tıklayarak kapsayan türü genişlettiğinizde alan görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="a66f8-126">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>

- <span data-ttu-id="a66f8-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed>üyenin varsayılan olarak görüntülendiğini ancak genişletilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="a66f8-128">Bu varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="a66f8-128">This is the default behavior.</span></span>

- <span data-ttu-id="a66f8-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden>üyenin kendisinin gösterildiğini, ancak bir dizi veya koleksiyon ise, bileşen nesnelerinin görüntülendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>

> [!NOTE]
> <span data-ttu-id="a66f8-130">Visual Basic <xref:System.Diagnostics.DebuggerBrowsableAttribute> , .NET Framework sürüm 2,0 ' de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a66f8-130">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>

<span data-ttu-id="a66f8-131">Aşağıdaki kod örneği, <xref:System.Diagnostics.DebuggerBrowsableAttribute> sınıfının hata ayıklama penceresinde sınıfın görüntülenmesini engellemek için öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-131">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="a66f8-132">DebuggerTypeProxy kullanma</span><span class="sxs-lookup"><span data-stu-id="a66f8-132">Using the DebuggerTypeProxy</span></span>
 <span data-ttu-id="a66f8-133">Bir türün hata ayıklama görünümünü önemli ölçüde ve temel olarak değiştirmeniz gerektiğinde özniteliğikullanın,ancaktürünkendisinideğiştirmeyin.<xref:System.Diagnostics.DebuggerTypeProxyAttribute></span><span class="sxs-lookup"><span data-stu-id="a66f8-133">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="a66f8-134"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Özniteliği, bir tür için bir görüntüleme proxy 'si belirtmek için kullanılır ve bu, geliştiricinin tür için görünümü uyarlayabilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-134">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="a66f8-135">Bu öznitelik, gibi <xref:System.Diagnostics.DebuggerDisplayAttribute>, derleme düzeyinde kullanılabilir, bu <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> durumda özellik proxy kullanılacak türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-135">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="a66f8-136">Önerilen kullanım, bu özniteliğin özniteliğin uygulandığı tür içinde oluşan özel bir iç içe türü belirttiğinden emin olur.</span><span class="sxs-lookup"><span data-stu-id="a66f8-136">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="a66f8-137">Tür izleyicilerini destekleyen bir ifade değerlendirici, bir tür görüntülenirken bu özniteliği denetler.</span><span class="sxs-lookup"><span data-stu-id="a66f8-137">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="a66f8-138">Öznitelik bulunursa, ifade değerlendirici özniteliğin uygulandığı tür için görüntüleme proxy türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="a66f8-138">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>

 <span data-ttu-id="a66f8-139"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Varsa, hata ayıklayıcı değişkeni penceresi yalnızca proxy türünün genel üyelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a66f8-139">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="a66f8-140">Özel Üyeler gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="a66f8-140">Private members are not displayed.</span></span> <span data-ttu-id="a66f8-141">Veri penceresinin davranışı öznitelik ile geliştirilmiş görünümler tarafından değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="a66f8-141">The behavior of the data window is not changed by attribute-enhanced views.</span></span>

 <span data-ttu-id="a66f8-142">Gereksiz performans cezalarını önlemek için, nesne genişletilene kadar görüntüleme proxy 'si öznitelikleri, Kullanıcı aracılığıyla bir veri penceresinde <xref:System.Diagnostics.DebuggerBrowsableAttribute> türün yanındaki artı işaretine (+) tıklanana kadar işlenmeyecektir. özniteliğe.</span><span class="sxs-lookup"><span data-stu-id="a66f8-142">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="a66f8-143">Bu nedenle, görüntüleme türüne hiçbir özniteliğin uygulanması önerilir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-143">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="a66f8-144">Öznitelikleri, görüntüleme türünün gövdesinde uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a66f8-144">Attributes can and should be applied within the body of the display type.</span></span>

 <span data-ttu-id="a66f8-145">Aşağıdaki kod örneği, <xref:System.Diagnostics.DebuggerTypeProxyAttribute> hata ayıklayıcı görüntüleme proxy 'si olarak kullanılacak bir tür belirtmek için öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-145">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>

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

## <a name="example"></a><span data-ttu-id="a66f8-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="a66f8-146">Example</span></span>

### <a name="description"></a><span data-ttu-id="a66f8-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a66f8-147">Description</span></span>

<span data-ttu-id="a66f8-148">Aşağıdaki kod örneği <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, ve <xref:System.Diagnostics.DebuggerTypeProxyAttribute> özniteliklerini uygulamanın sonuçlarını görmek için Visual Studio 'da görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="a66f8-148">The following code example can be viewed in Visual Studio to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>

### <a name="code"></a><span data-ttu-id="a66f8-149">Kod</span><span class="sxs-lookup"><span data-stu-id="a66f8-149">Code</span></span>

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="a66f8-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a66f8-150">See also</span></span>

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
