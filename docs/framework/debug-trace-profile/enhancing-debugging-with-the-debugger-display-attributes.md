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
ms.openlocfilehash: ca118bffb045a0e7e3a5084916a0ff8020ebda90
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216486"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme

Hata ayıklayıcı görüntüleme öznitelikleri tür geliştiricisinin, bu türün çalışma zamanı davranışını belirten ve en iyi anladığı, bu türün bir hata ayıklayıcıda görüntülenmesiyle nasıl görüneceğine de olanak tanır. Ayrıca, bir `Target` özelliği sağlayan hata ayıklayıcı görüntüleme öznitelikleri, kullanıcılar tarafından kaynak kodu bilgisi olmadan, derleme düzeyinde uygulanabilir. <xref:System.Diagnostics.DebuggerDisplayAttribute> özniteliği, bir tür veya üyenin hata ayıklayıcı değişken pencerelerinin nasıl görüntülendiğini denetler. <xref:System.Diagnostics.DebuggerBrowsableAttribute> özniteliği, bir alanın veya özelliğin hata ayıklayıcı değişkeni penceresinde görüntülenip görüntülenmeyeceğini ve nasıl görüntüleneceğini belirler. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> özniteliği, bir tür için alternatif bir tür veya proxy belirtir ve türün hata ayıklayıcı penceresinde görüntülenme şeklini değiştirir. Proxy veya yedek türü olan bir değişkeni görüntülediğinizde, proxy, hata ayıklayıcı görüntü penceresinde özgün tür için temsil eder. Hata ayıklayıcı değişkeni penceresi yalnızca proxy türünün ortak üyelerini görüntüler. Özel Üyeler gösterilmez.  
  
## <a name="using-the-debuggerdisplayattribute"></a>DebuggerDisplayAttribute kullanma  

<xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> oluşturucusunun tek bir bağımsız değişkeni vardır: tür örneklerine yönelik değer sütununda görüntülenecek dize. Bu dize, küme ayracı ({ve}) içerebilir. Küme ayracı çiftindeki metin bir ifade olarak değerlendirilir. Örneğin, aşağıdaki C# kod, bir `MyHashtable`örneği için hata ayıklayıcı görüntüsünü genişletmek üzere artı işareti (+) seçildiğinde, "Count = 4" değerinin görüntülenmesine neden olur.  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

İfadede başvurulan özelliklere uygulanan öznitelikler işlenmedi. C# Derleyici için, hedef türün geçerli örneğine yönelik bu başvuruya yalnızca örtülü erişimi olan genel bir ifadeye izin verilir. İfade sınırlı; diğer adlar, Yereller veya işaretçiler için erişim yoktur. Kod C# içinde, yalnızca hedef türün geçerli örneği için `this` işaretçisine örtük erişimi olan küme ayraçları arasında genel bir ifade kullanabilirsiniz.

Örneğin, bir C# nesnenin geçersiz kılındığı `ToString()`, hata ayıklayıcı geçersiz kılmayı çağırır ve standart `{<typeName>}.` yerine sonucunu gösterir, bu nedenle `ToString()`' i geçersiz kıldıysanız <xref:System.Diagnostics.DebuggerDisplayAttribute>kullanmanız gerekmez. Her ikisini de kullanıyorsanız, <xref:System.Diagnostics.DebuggerDisplayAttribute> özniteliği `ToString()` geçersiz kılma üzerinden önceliklidir.

## <a name="using-the-debuggerbrowsableattribute"></a>DebuggerBrowsableAttribute kullanma
 Alan veya özelliğin hata ayıklayıcı penceresinde nasıl görüntüleneceğini belirtmek için <xref:System.Diagnostics.DebuggerBrowsableAttribute> alana veya özelliğe uygulayın. Bu öznitelik için Oluşturucu, aşağıdaki durumlardan birini belirten <xref:System.Diagnostics.DebuggerBrowsableState> sabit listesi değerlerinden birini alır:

- <xref:System.Diagnostics.DebuggerBrowsableState.Never>, üyenin veri penceresinde görüntülenmediğini gösterir.  Örneğin, bir alanındaki <xref:System.Diagnostics.DebuggerBrowsableAttribute> için bu değerin kullanılması, alanı hiyerarşisinden kaldırır; tür örneği için artı işaretine (+) tıklayarak kapsayan türü genişlettiğinizde, alan görüntülenmez.

- <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed>, üyenin varsayılan olarak görüntülendiğini, ancak genişletilmediğini belirtir.  Bu varsayılan davranıştır.

- <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden>, üyenin kendisinin gösterilmediğini, ancak bir dizi veya koleksiyon ise bileşen nesnelerinin görüntülendiğini belirtir.

> [!NOTE]
> <xref:System.Diagnostics.DebuggerBrowsableAttribute>, .NET Framework 2,0 sürümünde Visual Basic desteklenmez.

Aşağıdaki kod örneği, sınıfın hata ayıklama penceresinde görünmesini izleyen özelliğin bu özelliğin kullanılmasını engellemek için <xref:System.Diagnostics.DebuggerBrowsableAttribute> kullanımını gösterir.

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a>DebuggerTypeProxy kullanma
 Bir türün hata ayıklama görünümünü önemli ölçüde ve temel olarak değiştirmeniz gerektiğinde <xref:System.Diagnostics.DebuggerTypeProxyAttribute> özniteliğini kullanın, ancak türün kendisini değiştirmeyin. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> özniteliği, bir geliştiricinin tür için görünümü uyarlayabilmesine izin veren bir türün görüntüleme proxy 'sini belirtmek için kullanılır.  <xref:System.Diagnostics.DebuggerDisplayAttribute>gibi bu öznitelik, derleme düzeyinde kullanılabilir, bu durumda <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> özelliği proxy 'nin kullanılacağı türü belirtir. Önerilen kullanım, bu özniteliğin özniteliğin uygulandığı tür içinde oluşan özel bir iç içe türü belirttiğinden emin olur.  Tür izleyicilerini destekleyen bir ifade değerlendirici, bir tür görüntülenirken bu özniteliği denetler. Öznitelik bulunursa, ifade değerlendirici özniteliğin uygulandığı tür için görüntüleme proxy türünü kullanır.

 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> mevcut olduğunda, hata ayıklayıcı değişkeni penceresi yalnızca proxy türünün genel üyelerini görüntüler. Özel Üyeler gösterilmez. Veri penceresinin davranışı öznitelik ile geliştirilmiş görünümler tarafından değiştirilmez.

 Gereksiz performans cezalarını önlemek için, Kullanıcı aracılığıyla bir veri penceresinde türün yanındaki artı işaretine (+) tıklamak veya <xref:System.Diagnostics.DebuggerBrowsableAttribute> özniteliği uygulaması aracılığıyla, görüntüleme proxy 'si öznitelikleri, nesne genişletilene kadar işlenmeyecektir. Bu nedenle, görüntüleme türüne hiçbir özniteliğin uygulanması önerilir. Öznitelikleri, görüntüleme türünün gövdesinde uygulanmalıdır.

 Aşağıdaki kod örneği, hata ayıklayıcı görüntüleme proxy 'si olarak kullanılacak bir tür belirtmek için <xref:System.Diagnostics.DebuggerTypeProxyAttribute> kullanımını gösterir.

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

Aşağıdaki kod örneği, <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>ve <xref:System.Diagnostics.DebuggerTypeProxyAttribute> özniteliklerini uygulamanın sonuçlarını görmek için Visual Studio 'da görüntülenebilir.

### <a name="code"></a>Kod

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
