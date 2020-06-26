---
title: Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme
description: Tür geliştiricisinin bir hata ayıklayıcıda gösterildiğinde ne gibi göründüğünü de belirtmesini sağlayan .NET 'teki hata ayıklayıcı görüntüleme özniteliklerini kullanmaya başlayın.
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
ms.openlocfilehash: f266bf7278f472c51dd355df5ba04a123cbd7df0
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415972"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="cd98a-103">Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme</span><span class="sxs-lookup"><span data-stu-id="cd98a-103">Enhancing Debugging with the Debugger Display Attributes</span></span>

<span data-ttu-id="cd98a-104">Hata ayıklayıcı görüntüleme öznitelikleri tür geliştiricisinin, bu türün çalışma zamanı davranışını belirten ve en iyi anladığı, bu türün bir hata ayıklayıcıda görüntülenmesiyle nasıl görüneceğine de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cd98a-104">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="cd98a-105">Ayrıca, bir özelliği sağlayan hata ayıklayıcı görüntüleme öznitelikleri, `Target` kaynak kodu bilgisine sahip olmayan kullanıcılar tarafından derleme düzeyinde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="cd98a-105">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="cd98a-106"><xref:System.Diagnostics.DebuggerDisplayAttribute>Özniteliği bir türün veya üyenin hata ayıklayıcı değişken penceresinde nasıl görüntülendiğini denetler.</span><span class="sxs-lookup"><span data-stu-id="cd98a-106">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="cd98a-107"><xref:System.Diagnostics.DebuggerBrowsableAttribute>Özniteliği, bir alanın veya özelliğin hata ayıklayıcı değişkeni penceresinde görüntülenip görüntülenmeyeceğini ve nasıl görüntüleneceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="cd98a-107">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="cd98a-108">Öznitelik, bir <xref:System.Diagnostics.DebuggerTypeProxyAttribute> tür için alternatif bir tür veya ara sunucu belirtir ve tür hata ayıklayıcı penceresinde görüntülenme şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="cd98a-108">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="cd98a-109">Proxy veya yedek türü olan bir değişkeni görüntülediğinizde, proxy, hata ayıklayıcı görüntü penceresinde özgün tür için temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cd98a-109">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window.</span></span> <span data-ttu-id="cd98a-110">Hata ayıklayıcı değişkeni penceresi yalnızca proxy türünün ortak üyelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cd98a-110">The debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="cd98a-111">Özel Üyeler gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="cd98a-111">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="cd98a-112">DebuggerDisplayAttribute kullanma</span><span class="sxs-lookup"><span data-stu-id="cd98a-112">Using the DebuggerDisplayAttribute</span></span>  

<span data-ttu-id="cd98a-113"><xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A>Oluşturucunun tek bir bağımsız değişkeni vardır: tür örnekleri için değer sütununda görüntülenecek dize.</span><span class="sxs-lookup"><span data-stu-id="cd98a-113">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="cd98a-114">Bu dize, küme ayracı ({ve}) içerebilir.</span><span class="sxs-lookup"><span data-stu-id="cd98a-114">This string can contain braces ({ and }).</span></span> <span data-ttu-id="cd98a-115">Küme ayracı çiftindeki metin bir ifade olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="cd98a-115">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="cd98a-116">Örneğin, aşağıdaki C# kodu, bir örneği için hata ayıklayıcı görüntüsünü genişletmek için artı işareti (+) seçildiğinde "Count = 4" görüntülenmesine neden olur `MyHashtable` .</span><span class="sxs-lookup"><span data-stu-id="cd98a-116">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

<span data-ttu-id="cd98a-117">İfadede başvurulan özelliklere uygulanan öznitelikler işlenmedi.</span><span class="sxs-lookup"><span data-stu-id="cd98a-117">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="cd98a-118">C# derleyicisi için, hedef türün geçerli örneğine yönelik bu başvuruya yalnızca örtülü erişimi olan genel bir ifadeye izin verilir.</span><span class="sxs-lookup"><span data-stu-id="cd98a-118">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="cd98a-119">İfade sınırlı; diğer adlar, Yereller veya işaretçiler için erişim yoktur.</span><span class="sxs-lookup"><span data-stu-id="cd98a-119">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="cd98a-120">C# kodunda, `this` yalnızca hedef türün geçerli örneğinin işaretçisine örtük erişimi olan küme ayraçları arasında genel bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd98a-120">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>

<span data-ttu-id="cd98a-121">Örneğin, bir C# nesnesi geçersiz kılınmışsa `ToString()` , hata ayıklayıcı geçersiz kılmayı çağırır ve standart yerine sonucunu gösterir, `{<typeName>}.` Aksi takdirde, ' yi geçersiz kılarsınız `ToString()` , kullanmanız gerekmez <xref:System.Diagnostics.DebuggerDisplayAttribute> .</span><span class="sxs-lookup"><span data-stu-id="cd98a-121">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="cd98a-122">Her ikisini de kullanırsanız, <xref:System.Diagnostics.DebuggerDisplayAttribute> öznitelik `ToString()` geçersiz kılmanın üzerine gelir.</span><span class="sxs-lookup"><span data-stu-id="cd98a-122">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>

## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="cd98a-123">DebuggerBrowsableAttribute kullanma</span><span class="sxs-lookup"><span data-stu-id="cd98a-123">Using the DebuggerBrowsableAttribute</span></span>
 <span data-ttu-id="cd98a-124"><xref:System.Diagnostics.DebuggerBrowsableAttribute>Alan veya özelliğin hata ayıklayıcı penceresinde nasıl görüntüleneceğini belirtmek için bir alan veya özelliğe uygulayın.</span><span class="sxs-lookup"><span data-stu-id="cd98a-124">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="cd98a-125">Bu özniteliğin Oluşturucusu, <xref:System.Diagnostics.DebuggerBrowsableState> aşağıdaki durumlardan birini belirten sabit listesi değerlerinden birini alır:</span><span class="sxs-lookup"><span data-stu-id="cd98a-125">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>

- <span data-ttu-id="cd98a-126"><xref:System.Diagnostics.DebuggerBrowsableState.Never>üyenin veri penceresinde görüntülenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd98a-126"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="cd98a-127">Örneğin, bir alan için bu değerin kullanılması <xref:System.Diagnostics.DebuggerBrowsableAttribute> alanı hiyerarşiden kaldırır; tür örneği için artı işaretine (+) tıklayarak kapsayan türü genişlettiğinizde alan görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="cd98a-127">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>

- <span data-ttu-id="cd98a-128"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed>üyenin varsayılan olarak görüntülendiğini ancak genişletilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd98a-128"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="cd98a-129">Bu, varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="cd98a-129">This is the default behavior.</span></span>

- <span data-ttu-id="cd98a-130"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden>üyenin kendisinin gösterildiğini, ancak bir dizi veya koleksiyon ise, bileşen nesnelerinin görüntülendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd98a-130"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>

> [!NOTE]
> <span data-ttu-id="cd98a-131"><xref:System.Diagnostics.DebuggerBrowsableAttribute>Visual Basic, .NET Framework sürüm 2,0 ' de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="cd98a-131">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>

<span data-ttu-id="cd98a-132">Aşağıdaki kod örneği, <xref:System.Diagnostics.DebuggerBrowsableAttribute> sınıfının hata ayıklama penceresinde sınıfın görüntülenmesini engellemek için öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd98a-132">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="cd98a-133">DebuggerTypeProxy kullanma</span><span class="sxs-lookup"><span data-stu-id="cd98a-133">Using the DebuggerTypeProxy</span></span>
 <span data-ttu-id="cd98a-134"><xref:System.Diagnostics.DebuggerTypeProxyAttribute>Bir türün hata ayıklama görünümünü önemli ölçüde ve temel olarak değiştirmeniz gerektiğinde özniteliği kullanın, ancak türün kendisini değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="cd98a-134">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="cd98a-135"><xref:System.Diagnostics.DebuggerTypeProxyAttribute>Özniteliği, bir tür için bir görüntüleme proxy 'si belirtmek için kullanılır ve bu, geliştiricinin tür için görünümü uyarlayabilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="cd98a-135">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="cd98a-136">Bu öznitelik, gibi, <xref:System.Diagnostics.DebuggerDisplayAttribute> derleme düzeyinde kullanılabilir, bu durumda <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> özellik proxy kullanılacak türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd98a-136">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="cd98a-137">Önerilen kullanım, bu özniteliğin özniteliğin uygulandığı tür içinde oluşan özel bir iç içe türü belirttiğinden emin olur.</span><span class="sxs-lookup"><span data-stu-id="cd98a-137">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="cd98a-138">Tür izleyicilerini destekleyen bir ifade değerlendirici, bir tür görüntülenirken bu özniteliği denetler.</span><span class="sxs-lookup"><span data-stu-id="cd98a-138">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="cd98a-139">Öznitelik bulunursa, ifade değerlendirici özniteliğin uygulandığı tür için görüntüleme proxy türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd98a-139">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>

 <span data-ttu-id="cd98a-140"><xref:System.Diagnostics.DebuggerTypeProxyAttribute>Varsa, hata ayıklayıcı değişkeni penceresi yalnızca proxy türünün genel üyelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cd98a-140">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="cd98a-141">Özel Üyeler gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="cd98a-141">Private members are not displayed.</span></span> <span data-ttu-id="cd98a-142">Veri penceresinin davranışı öznitelik ile geliştirilmiş görünümler tarafından değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="cd98a-142">The behavior of the data window is not changed by attribute-enhanced views.</span></span>

 <span data-ttu-id="cd98a-143">Gereksiz performans cezalarını önlemek için, Kullanıcı aracılığıyla bir veri penceresinde veya özniteliğin uygulaması aracılığıyla artı işaretine (+) tıklanana kadar, görüntüleme proxy 'si öznitelikleri, nesne genişletilene kadar işlenmeyecektir <xref:System.Diagnostics.DebuggerBrowsableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="cd98a-143">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="cd98a-144">Bu nedenle, görüntüleme türüne hiçbir özniteliğin uygulanması önerilir.</span><span class="sxs-lookup"><span data-stu-id="cd98a-144">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="cd98a-145">Öznitelikleri, görüntüleme türünün gövdesinde uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd98a-145">Attributes can and should be applied within the body of the display type.</span></span>

 <span data-ttu-id="cd98a-146">Aşağıdaki kod örneği, <xref:System.Diagnostics.DebuggerTypeProxyAttribute> hata ayıklayıcı görüntüleme proxy 'si olarak kullanılacak bir tür belirtmek için öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd98a-146">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>

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

## <a name="example"></a><span data-ttu-id="cd98a-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd98a-147">Example</span></span>

### <a name="description"></a><span data-ttu-id="cd98a-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd98a-148">Description</span></span>

<span data-ttu-id="cd98a-149">Aşağıdaki kod örneği,, ve özniteliklerini uygulamanın sonuçlarını görmek için Visual Studio 'da görüntülenebilir <xref:System.Diagnostics.DebuggerDisplayAttribute> <xref:System.Diagnostics.DebuggerBrowsableAttribute> <xref:System.Diagnostics.DebuggerTypeProxyAttribute> .</span><span class="sxs-lookup"><span data-stu-id="cd98a-149">The following code example can be viewed in Visual Studio to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>

### <a name="code"></a><span data-ttu-id="cd98a-150">Kod</span><span class="sxs-lookup"><span data-stu-id="cd98a-150">Code</span></span>

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="cd98a-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd98a-151">See also</span></span>

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
