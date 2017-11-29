---
title: "Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c396a794cd3afa394cbb6b2393257a3103c6239d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="4d402-102">Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme</span><span class="sxs-lookup"><span data-stu-id="4d402-102">Enhancing Debugging with the Debugger Display Attributes</span></span>
<span data-ttu-id="4d402-103">Hata ayıklayıcı görüntü öznitelikleri izin Geliştirici belirtir ve bu tür çalışma zamanı davranışını anlayabilmesi gerekir, tür, ne de belirtmek için bu tür bir hata ayıklayıcıda zaman görüntülendiği gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="4d402-103">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="4d402-104">Ayrıca, hata ayıklayıcı görüntüleme sağlamak öznitelikleri bir `Target` özelliği kaynak kodunun bilgisi olmadan kullanıcılar tarafından derleme düzeyinde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="4d402-104">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="4d402-105"><xref:System.Diagnostics.DebuggerDisplayAttribute> Özniteliği denetleyen bir tür veya üye hata ayıklayıcı değişken pencerelerini de nasıl görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4d402-105">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="4d402-106"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Özniteliği varsa ve bir alanın nasıl belirler veya özelliği hata ayıklayıcı değişken pencerelerini de görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4d402-106">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="4d402-107"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Öznitelik türü hata ayıklayıcı Windows'da görüntülenme şeklini değiştirir ve bir yedek türü ya da bir tür için bir proxy belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d402-107">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="4d402-108">Bir proxy veya yedek türüne sahip bir değişken görüntülediğinizde, proxy hata ayıklayıcı görüntü penceresinde özgün türünün anlamına gelir**.**</span><span class="sxs-lookup"><span data-stu-id="4d402-108">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window**.**</span></span> <span data-ttu-id="4d402-109">Hata ayıklayıcı değişken windowdisplays yalnızca Genel üyeler proxy'sinin yazın.</span><span class="sxs-lookup"><span data-stu-id="4d402-109">The debugger variable windowdisplays only the public members of the proxy type.</span></span> <span data-ttu-id="4d402-110">Özel üyelerin görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="4d402-110">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="4d402-111">DebuggerDisplayAttribute kullanma</span><span class="sxs-lookup"><span data-stu-id="4d402-111">Using the DebuggerDisplayAttribute</span></span>  
 <span data-ttu-id="4d402-112"><xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Bir oluşturucuya sahip tek bir bağımsız değişken: için değer sütununda görüntülenecek bir dize türü örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4d402-112">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="4d402-113">Bu dize köşeli parantez içerebilir ({ve}).</span><span class="sxs-lookup"><span data-stu-id="4d402-113">This string can contain braces ({ and }).</span></span> <span data-ttu-id="4d402-114">Bir çift köşeli parantez içindeki metni bir ifade olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4d402-114">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="4d402-115">Örneğin, aşağıdaki C# kod neden "Count = 4" örneği için hata ayıklayıcı görüntü genişletmek için artı (+) seçildiğinde görüntülenecek `MyHashtable`.</span><span class="sxs-lookup"><span data-stu-id="4d402-115">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  
  
```csharp
[DebuggerDisplay("Count = {count}")]  
class MyHashtable  
{  
    public int count = 4;  
}  
```
  
 <span data-ttu-id="4d402-116">Deyimde başvurulan özelliklerine uygulanan öznitelikleri işlenmez.</span><span class="sxs-lookup"><span data-stu-id="4d402-116">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="4d402-117">C# derleyici için yalnızca örtük bu başvuru için geçerli örneği erişim hedef türü olan bir genel ifadesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="4d402-117">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="4d402-118">İfade sınırlıdır; diğer adlar, yerel veya işaretçileri için erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4d402-118">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="4d402-119">C# kodunda, genel bir ifade örtük erişimi ayraçlar arasında kullanabilirsiniz `this` hedef türü yalnızca geçerli örneği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4d402-119">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>  
  
 <span data-ttu-id="4d402-120">Örneğin, C# nesnesi geçersiz kılınan bir varsa `ToString()`, hata ayıklayıcı geçersiz kılma işlemini çağırın ve standart yerine sonucu göster `{<typeName>}.` siz kıldıysanız nedenle `ToString()`, kullanmak gerekmez <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4d402-120">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="4d402-121">Her ikisini de kullanırsanız, <xref:System.Diagnostics.DebuggerDisplayAttribute> özniteliği önceliklidir `ToString()` geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="4d402-121">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>  
  
## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="4d402-122">DebuggerBrowsableAttribute kullanma</span><span class="sxs-lookup"><span data-stu-id="4d402-122">Using the DebuggerBrowsableAttribute</span></span>  
 <span data-ttu-id="4d402-123">Uygulama <xref:System.Diagnostics.DebuggerBrowsableAttribute> bir alan veya nasıl alanı veya özelliği hata ayıklayıcı penceresinde görüntülenecek belirtmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="4d402-123">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="4d402-124">Bu öznitelik Oluşturucusu birini alır <xref:System.Diagnostics.DebuggerBrowsableState> şu durumlardan birini belirten numaralandırma değerlerinin:</span><span class="sxs-lookup"><span data-stu-id="4d402-124">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>  
  
-   <span data-ttu-id="4d402-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never>Üye verileri penceresinde görüntülenmez gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d402-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="4d402-126">Örneğin, bu değer için kullanarak <xref:System.Diagnostics.DebuggerBrowsableAttribute> üzerinde bir alan alan hiyerarşiden kaldırır; türü örneği için artı işareti (+) tıklatarak kendilerini kapsayan türle genişlettiğinizde alanı görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="4d402-126">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>  
  
-   <span data-ttu-id="4d402-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed>üye görüntülenen ancak varsayılan olarak genişletilmiş değil belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d402-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="4d402-128">Bu varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="4d402-128">This is the default behavior.</span></span>  
  
-   <span data-ttu-id="4d402-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden>üye gösterilmez, ancak bir dizi veya koleksiyon ise, bağlı olan nesneler görüntülenir gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d402-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d402-130"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Visual Basic'te .NET Framework sürüm 2.0 tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4d402-130">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="4d402-131">Aşağıdaki kod örneğinde kullanımı gösterilmiştir <xref:System.Diagnostics.DebuggerBrowsableAttribute> sınıfı için hata ayıklama penceresinde görüntülenmesini aşağıdaki özellik önlemek için.</span><span class="sxs-lookup"><span data-stu-id="4d402-131">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>  
  
```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]  
public static string y = "Test String";  
```  
  
## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="4d402-132">DebuggerTypeProxy kullanma</span><span class="sxs-lookup"><span data-stu-id="4d402-132">Using the DebuggerTypeProxy</span></span>  
 <span data-ttu-id="4d402-133">Kullanım <xref:System.Diagnostics.DebuggerTypeProxyAttribute> özniteliği önemli ölçüde ve temelde bir tür hata ayıklama görünümünü değiştirme, ancak türü değiştirmemek gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="4d402-133">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="4d402-134"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Öznitelik türü için Görünüm uyarlamak geliştiricinin vererek bir görüntü proxy bir tür için belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d402-134">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="4d402-135">Gibi bu öznitelik <xref:System.Diagnostics.DebuggerDisplayAttribute>, derleme düzeyinde; bu durumda kullanılabilir <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> özelliği, proxy kullanılacak türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d402-135">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="4d402-136">Bu öznitelik, öznitelik uygulandığı türü içinde gerçekleşir özel bir iç içe geçmiş tür belirtir önerilen kullanımdır.</span><span class="sxs-lookup"><span data-stu-id="4d402-136">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="4d402-137">Bir tür görüntülendiğinde bu öznitelik için bir ifade değerlendiricisi destekler görüntüleyiciler yazın denetler.</span><span class="sxs-lookup"><span data-stu-id="4d402-137">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="4d402-138">İfade değerlendirici öznitelik bulunursa, öznitelik uygulandığı türü için görüntü proxy türü ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="4d402-138">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>  
  
 <span data-ttu-id="4d402-139">Zaman <xref:System.Diagnostics.DebuggerTypeProxyAttribute> var, yalnızca Genel üyeler proxy türü hata ayıklayıcı değişken penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4d402-139">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="4d402-140">Özel üyelerin görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="4d402-140">Private members are not displayed.</span></span> <span data-ttu-id="4d402-141">Veri penceresi davranışını özniteliği Gelişmiş görünümler tarafından değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="4d402-141">The behavior of the data window is not changed by attribute-enhanced views.</span></span>  
  
 <span data-ttu-id="4d402-142">Bir veri penceresinde türü yanındaki artı (+) tıklatarak kullanıcı, veya aracılığıyla uygulamayı nesne genişletilir kadar gereksiz performans cezalarını önlemek için görüntü proxy özniteliklerini işlenmez <xref:System.Diagnostics.DebuggerBrowsableAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4d402-142">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="4d402-143">Bu nedenle, hiçbir öznitelik görüntü türünü uygulanması önerilir.</span><span class="sxs-lookup"><span data-stu-id="4d402-143">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="4d402-144">Öznitelikleri olabilir ve görüntü türü gövdesi içinde uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4d402-144">Attributes can and should be applied within the body of the display type.</span></span>  
  
 <span data-ttu-id="4d402-145">Aşağıdaki kod örneğinde kullanımı gösterilmiştir <xref:System.Diagnostics.DebuggerTypeProxyAttribute> bir hata ayıklayıcı görüntü proxy olarak kullanılacak bir türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="4d402-145">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="4d402-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d402-146">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4d402-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d402-147">Description</span></span>  
 <span data-ttu-id="4d402-148">Aşağıdaki kod örneğinde görüntülenebilir [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] uygulama sonuçlarını görmek için <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, ve <xref:System.Diagnostics.DebuggerTypeProxyAttribute> öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="4d402-148">The following code example can be viewed in [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4d402-149">Kod</span><span class="sxs-lookup"><span data-stu-id="4d402-149">Code</span></span>  
 [!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
 [!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
 [!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4d402-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d402-150">See Also</span></span>  
 <xref:System.Diagnostics.DebuggerDisplayAttribute>  
 <xref:System.Diagnostics.DebuggerBrowsableAttribute>  
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
