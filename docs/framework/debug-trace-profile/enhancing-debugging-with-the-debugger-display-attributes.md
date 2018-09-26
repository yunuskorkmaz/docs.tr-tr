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
ms.openlocfilehash: 4150658f713e626c5578c21cfada0f6410cbd37b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208078"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme

Hata ayıklayıcı görüntü öznitelikleri izin Geliştirici belirtir ve çalışma zamanı davranışını en iyi şekilde anlayan, tür, ne de belirtmek için bu tür bir hata ayıklayıcıda zaman görüntülendiği gibi görünecektir. Ayrıca, hata ayıklayıcı görüntüleme sağlayan öznitelikler bir `Target` özelliği kaynak kod bilgisi olmadan kullanıcılar tarafından derleme düzeyinde uygulanabilir. <xref:System.Diagnostics.DebuggerDisplayAttribute> Özniteliği bir tür veya üye hata ayıklayıcı değişken pencerelerinde nasıl görüntüleneceğini denetler. <xref:System.Diagnostics.DebuggerBrowsableAttribute> Özelliği hata ayıklayıcı değişken pencerelerinde görüntülenen ya da öznitelik varsa ve bir alanın nasıl belirler. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Öznitelik türü hata ayıklayıcı pencerelerinde görüntülenen şekilde değiştirir ve bir yedek tür ya da bir tür için bir proxy belirtir. Bir proxy veya yedek tür sahip bir değişken görüntülediğinizde, proxy özgün türü hata ayıklayıcı görüntü penceresinde gösterir. Proxy türü yalnızca genel üyeleri hata ayıklayıcı değişken penceresinde görüntüler. Özel üyeler görüntülenmez.  
  
## <a name="using-the-debuggerdisplayattribute"></a>DebuggerDisplayAttribute kullanma  

<xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Oluşturucusu olan tek bir bağımsız değişken: değer sütununda görüntülenecek bir dize türü örnekleri. Bu dize, küme ayraçları içerebilir ({ve}). Bir çift küme ayraçlarının içindeki metni ifade olarak değerlendirilir. Örneğin, aşağıdaki C# kodu neden "sayısı = 4" örneği için hata ayıklayıcı görüntü genişletmek için artı işaretini (+) seçili olduğunda görüntülenecek `MyHashtable`.  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

Deyimde başvurulan özelliklerine uygulanan öznitelikleri işlenmez. C# derleyicisi, genel bir ifade yalnızca örtük erişim bu başvuru hedef türünün geçerli örneğe sahip izin verilir. İfade sınırlıdır; diğer adlar, Yereller ve işaretçileri için erişimi yoktur. C# kodunda, örtük erişimi olan ayraçlar arasındaki genel bir ifade kullanabilirsiniz `this` yalnızca hedef türü geçerli örneği için işaretçi.

Örneğin, bir C# nesnesi geçersiz kılınan bir varsa `ToString()`, hata ayıklayıcı geçersiz kılma işlemini çağırın ve standart yerine sonucu göster `{<typeName>}.` siz kıldıysanız Thus `ToString()`, kullanın gerekmez <xref:System.Diagnostics.DebuggerDisplayAttribute>. Her ikisi de kullanırsanız <xref:System.Diagnostics.DebuggerDisplayAttribute> özniteliği önceliklidir `ToString()` geçersiz kılar.

## <a name="using-the-debuggerbrowsableattribute"></a>DebuggerBrowsableAttribute kullanma
 Uygulama <xref:System.Diagnostics.DebuggerBrowsableAttribute> bir alan veya özellik hata ayıklayıcı penceresinde görüntülenecek alan veya özellik nasıl olduğunu belirtmek için. Bu öznitelik için oluşturucu birini alır <xref:System.Diagnostics.DebuggerBrowsableState> aşağıdaki durumlardan biriyle belirten numaralandırma değerlerinden:

-   <xref:System.Diagnostics.DebuggerBrowsableState.Never> Üye verileri penceresinde görüntülenmez gösterir.  Örneğin, bu değeri kullanarak <xref:System.Diagnostics.DebuggerBrowsableAttribute> üzerinde bir alan, alanın bu hiyerarşisinden kaldırır; türü örneği için (+) artı işaretine tıklayarak kapsayan türdeki genişlettiğinizde alan gösterilmez.

-   <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> üye görüntülenmez ancak varsayılan olarak genişletilmiş değil gösterir.  Bu varsayılan davranıştır.

-   <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> üye gösterilmez, ancak bir dizi veya koleksiyon olması durumunda, bağlı nesneler görüntülenir gösterir.

> [!NOTE]
>  <xref:System.Diagnostics.DebuggerBrowsableAttribute> Visual Basic'te .NET Framework sürüm 2.0 tarafından desteklenmez.

Aşağıdaki kod örneği, kullanımını gösterir <xref:System.Diagnostics.DebuggerBrowsableAttribute> sınıfı için hata ayıklama penceresinde görüntülenmesini aşağıdaki özellik önlemek için.

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a>DebuggerTypeProxy kullanma
 Kullanım <xref:System.Diagnostics.DebuggerTypeProxyAttribute> özniteliği önemli ölçüde ve temel bir tür hata ayıklama görünümünü değiştirebilirsiniz, ancak türü değiştirilmemesi gerektiğinde. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Öznitelik, bir türü için Görünüm türü için uygun hale getirmek bir geliştirici izin görünen proxy belirtmek için kullanılır.  Gibi bu öznitelik <xref:System.Diagnostics.DebuggerDisplayAttribute>, bu durumda derleme düzeyinde kullanılabilir <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> özelliği proxy kullanılacak türünü belirtir. Bu öznitelik türü özniteliği uygulandığı içinde oluşan özel bir iç içe türü belirttiğinden önerilen kullanımdır.  Bir tür görüntülendiğinde, bu öznitelik için bir ifade değerlendiricisi destekler görüntüleyiciler yazın denetler. Öznitelik bulunursa, ifade değerlendiricisi görünen proxy türü özniteliği uygulandığı türünün yerini alır.

 Zaman <xref:System.Diagnostics.DebuggerTypeProxyAttribute> varsa, proxy türü yalnızca genel üyeleri hata ayıklayıcı değişken penceresinde görüntüler. Özel üyeler görüntülenmez. Veri penceresi davranışını özniteliği Gelişmiş görünümler tarafından değiştirilmez.

 Ya da türü bir veri penceresinde yanındaki artı işaretini (+) tıklayarak kullanıcı veya uygulamanın nesne genişletilir kadar gereksiz performans cezalarını önlemek için görüntü proxy özniteliklerini işlenmez <xref:System.Diagnostics.DebuggerBrowsableAttribute> özniteliği. Bu nedenle, hiçbir öznitelik görüntü türünü uygulanması önerilir. Öznitelikleri olabilir ve görüntü türünü gövdesinden uygulanmalıdır.

 Aşağıdaki kod örneği, kullanımını gösterir <xref:System.Diagnostics.DebuggerTypeProxyAttribute> hata ayıklayıcı görüntü proxy olarak kullanılacak bir tür belirtmek için.

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

Aşağıdaki kod örneği uygulanması sonucu görmek için Visual Studio'da görüntülenebilir <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, ve <xref:System.Diagnostics.DebuggerTypeProxyAttribute> öznitelikleri.

### <a name="code"></a>Kod

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>