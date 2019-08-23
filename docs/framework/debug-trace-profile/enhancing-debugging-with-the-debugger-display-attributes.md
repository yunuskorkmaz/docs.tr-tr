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
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme

Hata ayıklayıcı görüntüleme öznitelikleri tür geliştiricisinin, bu türün çalışma zamanı davranışını belirten ve en iyi anladığı, bu türün bir hata ayıklayıcıda görüntülenmesiyle nasıl görüneceğine de olanak tanır. Ayrıca, bir `Target` özelliği sağlayan hata ayıklayıcı görüntüleme öznitelikleri, kaynak kodu bilgisine sahip olmayan kullanıcılar tarafından derleme düzeyinde uygulanabilir. <xref:System.Diagnostics.DebuggerDisplayAttribute> Özniteliği bir türün veya üyenin hata ayıklayıcı değişken penceresinde nasıl görüntülendiğini denetler. Özniteliği <xref:System.Diagnostics.DebuggerBrowsableAttribute> , bir alanın veya özelliğin hata ayıklayıcı değişkeni penceresinde görüntülenip görüntülenmeyeceğini ve nasıl görüntüleneceğini belirler. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Öznitelik, bir tür için alternatif bir tür veya ara sunucu belirtir ve tür hata ayıklayıcı penceresinde görüntülenme şeklini değiştirir. Proxy veya yedek türü olan bir değişkeni görüntülediğinizde, proxy, hata ayıklayıcı görüntü penceresinde özgün tür için temsil eder. Hata ayıklayıcı değişkeni penceresi yalnızca proxy türünün ortak üyelerini görüntüler. Özel Üyeler gösterilmez.  
  
## <a name="using-the-debuggerdisplayattribute"></a>DebuggerDisplayAttribute kullanma  

<xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Oluşturucunun tek bir bağımsız değişkeni vardır: tür örnekleri için değer sütununda görüntülenecek dize. Bu dize, küme ayracı ({ve}) içerebilir. Küme ayracı çiftindeki metin bir ifade olarak değerlendirilir. Örneğin, aşağıdaki C# kod, bir örneği için hata ayıklayıcı görüntüsünü genişletmek için artı işareti (+) seçildiğinde, "Count = 4" değerinin `MyHashtable`görüntülenmesine neden olur.  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

İfadede başvurulan özelliklere uygulanan öznitelikler işlenmedi. C# Derleyici için, hedef türün geçerli örneğine yönelik bu başvuruya yalnızca örtülü erişimi olan genel bir ifadeye izin verilir. İfade sınırlı; diğer adlar, Yereller veya işaretçiler için erişim yoktur. Kod C# içinde, yalnızca hedef türün geçerli örneğinin `this` işaretçisine örtük erişimi olan küme ayraçları arasında genel bir ifade kullanabilirsiniz.

C# Örneğin, bir nesne geçersiz kılınmışsa `ToString()`, hata ayıklayıcı geçersiz kılmayı çağırır ve standart `{<typeName>}.` yerine sonucunu gösterir. bu nedenle, geçersiz kılındıysanız `ToString()`, kullanmanız <xref:System.Diagnostics.DebuggerDisplayAttribute>gerekmez. Her ikisini de kullanırsanız, <xref:System.Diagnostics.DebuggerDisplayAttribute> öznitelik `ToString()` geçersiz kılmanın üzerine gelir.

## <a name="using-the-debuggerbrowsableattribute"></a>DebuggerBrowsableAttribute kullanma
 <xref:System.Diagnostics.DebuggerBrowsableAttribute> Alan veya özelliğin hata ayıklayıcı penceresinde nasıl görüntüleneceğini belirtmek için bir alan veya özelliğe uygulayın. Bu özniteliğin Oluşturucusu, aşağıdaki durumlardan birini belirten <xref:System.Diagnostics.DebuggerBrowsableState> sabit listesi değerlerinden birini alır:

- <xref:System.Diagnostics.DebuggerBrowsableState.Never>üyenin veri penceresinde görüntülenmediğini belirtir.  Örneğin, bir alan için <xref:System.Diagnostics.DebuggerBrowsableAttribute> bu değerin kullanılması alanı hiyerarşiden kaldırır; tür örneği için artı işaretine (+) tıklayarak kapsayan türü genişlettiğinizde alan görüntülenmez.

- <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed>üyenin varsayılan olarak görüntülendiğini ancak genişletilmediğini belirtir.  Bu varsayılan davranıştır.

- <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden>üyenin kendisinin gösterildiğini, ancak bir dizi veya koleksiyon ise, bileşen nesnelerinin görüntülendiğini belirtir.

> [!NOTE]
> Visual Basic <xref:System.Diagnostics.DebuggerBrowsableAttribute> , .NET Framework sürüm 2,0 ' de desteklenmez.

Aşağıdaki kod örneği, <xref:System.Diagnostics.DebuggerBrowsableAttribute> sınıfının hata ayıklama penceresinde sınıfın görüntülenmesini engellemek için öğesinin kullanımını gösterir.

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a>DebuggerTypeProxy kullanma
 Bir türün hata ayıklama görünümünü önemli ölçüde ve temel olarak değiştirmeniz gerektiğinde özniteliğikullanın,ancaktürünkendisinideğiştirmeyin.<xref:System.Diagnostics.DebuggerTypeProxyAttribute> <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Özniteliği, bir tür için bir görüntüleme proxy 'si belirtmek için kullanılır ve bu, geliştiricinin tür için görünümü uyarlayabilmesine izin verir.  Bu öznitelik, gibi <xref:System.Diagnostics.DebuggerDisplayAttribute>, derleme düzeyinde kullanılabilir, bu <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> durumda özellik proxy kullanılacak türü belirtir. Önerilen kullanım, bu özniteliğin özniteliğin uygulandığı tür içinde oluşan özel bir iç içe türü belirttiğinden emin olur.  Tür izleyicilerini destekleyen bir ifade değerlendirici, bir tür görüntülenirken bu özniteliği denetler. Öznitelik bulunursa, ifade değerlendirici özniteliğin uygulandığı tür için görüntüleme proxy türünü kullanır.

 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Varsa, hata ayıklayıcı değişkeni penceresi yalnızca proxy türünün genel üyelerini görüntüler. Özel Üyeler gösterilmez. Veri penceresinin davranışı öznitelik ile geliştirilmiş görünümler tarafından değiştirilmez.

 Gereksiz performans cezalarını önlemek için, nesne genişletilene kadar görüntüleme proxy 'si öznitelikleri, Kullanıcı aracılığıyla bir veri penceresinde <xref:System.Diagnostics.DebuggerBrowsableAttribute> türün yanındaki artı işaretine (+) tıklanana kadar işlenmeyecektir. özniteliğe. Bu nedenle, görüntüleme türüne hiçbir özniteliğin uygulanması önerilir. Öznitelikleri, görüntüleme türünün gövdesinde uygulanmalıdır.

 Aşağıdaki kod örneği, <xref:System.Diagnostics.DebuggerTypeProxyAttribute> hata ayıklayıcı görüntüleme proxy 'si olarak kullanılacak bir tür belirtmek için öğesinin kullanımını gösterir.

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

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki kod örneği <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, ve <xref:System.Diagnostics.DebuggerTypeProxyAttribute> özniteliklerini uygulamanın sonuçlarını görmek için Visual Studio 'da görüntülenebilir.

### <a name="code"></a>Kod

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
