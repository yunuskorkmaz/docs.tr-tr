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
ms.openlocfilehash: 2efa8cfb2b196d6f5a26354161e42c1f376e43b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389548"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme
Hata ayıklayıcı görüntü öznitelikleri izin Geliştirici belirtir ve bu tür çalışma zamanı davranışını anlayabilmesi gerekir, tür, ne de belirtmek için bu tür bir hata ayıklayıcıda zaman görüntülendiği gibi görünür. Ayrıca, hata ayıklayıcı görüntüleme sağlamak öznitelikleri bir `Target` özelliği kaynak kodunun bilgisi olmadan kullanıcılar tarafından derleme düzeyinde uygulanabilir. <xref:System.Diagnostics.DebuggerDisplayAttribute> Özniteliği denetleyen bir tür veya üye hata ayıklayıcı değişken pencerelerini de nasıl görüntülenir. <xref:System.Diagnostics.DebuggerBrowsableAttribute> Özniteliği varsa ve bir alanın nasıl belirler veya özelliği hata ayıklayıcı değişken pencerelerini de görüntülenir. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Öznitelik türü hata ayıklayıcı Windows'da görüntülenme şeklini değiştirir ve bir yedek türü ya da bir tür için bir proxy belirtir. Bir proxy veya yedek türüne sahip bir değişken görüntülediğinizde, proxy hata ayıklayıcı görüntü penceresinde özgün türünün anlamına gelir **.** Hata ayıklayıcı değişken windowdisplays yalnızca Genel üyeler proxy'sinin yazın. Özel üyelerin görüntülenmez.  
  
## <a name="using-the-debuggerdisplayattribute"></a>DebuggerDisplayAttribute kullanma  
 <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Bir oluşturucuya sahip tek bir bağımsız değişken: için değer sütununda görüntülenecek bir dize türü örnekleri. Bu dize köşeli parantez içerebilir ({ve}). Bir çift köşeli parantez içindeki metni bir ifade olarak değerlendirilir. Örneğin, aşağıdaki C# kod neden "Count = 4" örneği için hata ayıklayıcı görüntü genişletmek için artı (+) seçildiğinde görüntülenecek `MyHashtable`.  
  
```csharp
[DebuggerDisplay("Count = {count}")]  
class MyHashtable  
{  
    public int count = 4;  
}  
```
  
 Deyimde başvurulan özelliklerine uygulanan öznitelikleri işlenmez. C# derleyici için yalnızca örtük bu başvuru için geçerli örneği erişim hedef türü olan bir genel ifadesine izin verilir. İfade sınırlıdır; diğer adlar, yerel veya işaretçileri için erişimi yoktur. C# kodunda, genel bir ifade örtük erişimi ayraçlar arasında kullanabilirsiniz `this` hedef türü yalnızca geçerli örneği için bir işaretçi.  
  
 Örneğin, C# nesnesi geçersiz kılınan bir varsa `ToString()`, hata ayıklayıcı geçersiz kılma işlemini çağırın ve standart yerine sonucu göster `{<typeName>}.` siz kıldıysanız nedenle `ToString()`, kullanmak gerekmez <xref:System.Diagnostics.DebuggerDisplayAttribute>. Her ikisini de kullanırsanız, <xref:System.Diagnostics.DebuggerDisplayAttribute> özniteliği önceliklidir `ToString()` geçersiz kılar.  
  
## <a name="using-the-debuggerbrowsableattribute"></a>DebuggerBrowsableAttribute kullanma  
 Uygulama <xref:System.Diagnostics.DebuggerBrowsableAttribute> bir alan veya nasıl alanı veya özelliği hata ayıklayıcı penceresinde görüntülenecek belirtmek için özellik. Bu öznitelik Oluşturucusu birini alır <xref:System.Diagnostics.DebuggerBrowsableState> şu durumlardan birini belirten numaralandırma değerlerinin:  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState.Never> Üye verileri penceresinde görüntülenmez gösterir.  Örneğin, bu değer için kullanarak <xref:System.Diagnostics.DebuggerBrowsableAttribute> üzerinde bir alan alan hiyerarşiden kaldırır; türü örneği için artı işareti (+) tıklatarak kendilerini kapsayan türle genişlettiğinizde alanı görüntülenmez.  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> üye görüntülenen ancak varsayılan olarak genişletilmiş değil belirtir.  Bu varsayılan davranıştır.  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> üye gösterilmez, ancak bir dizi veya koleksiyon ise, bağlı olan nesneler görüntülenir gösterir.  
  
> [!NOTE]
>  <xref:System.Diagnostics.DebuggerBrowsableAttribute> Visual Basic'te .NET Framework sürüm 2.0 tarafından desteklenmez.  
  
 Aşağıdaki kod örneğinde kullanımı gösterilmiştir <xref:System.Diagnostics.DebuggerBrowsableAttribute> sınıfı için hata ayıklama penceresinde görüntülenmesini aşağıdaki özellik önlemek için.  
  
```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]  
public static string y = "Test String";  
```  
  
## <a name="using-the-debuggertypeproxy"></a>DebuggerTypeProxy kullanma  
 Kullanım <xref:System.Diagnostics.DebuggerTypeProxyAttribute> özniteliği önemli ölçüde ve temelde bir tür hata ayıklama görünümünü değiştirme, ancak türü değiştirmemek gerektiğinde. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Öznitelik türü için Görünüm uyarlamak geliştiricinin vererek bir görüntü proxy bir tür için belirtmek için kullanılır.  Gibi bu öznitelik <xref:System.Diagnostics.DebuggerDisplayAttribute>, derleme düzeyinde; bu durumda kullanılabilir <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> özelliği, proxy kullanılacak türünü belirtir. Bu öznitelik, öznitelik uygulandığı türü içinde gerçekleşir özel bir iç içe geçmiş tür belirtir önerilen kullanımdır.  Bir tür görüntülendiğinde bu öznitelik için bir ifade değerlendiricisi destekler görüntüleyiciler yazın denetler. İfade değerlendirici öznitelik bulunursa, öznitelik uygulandığı türü için görüntü proxy türü ile değiştirir.  
  
 Zaman <xref:System.Diagnostics.DebuggerTypeProxyAttribute> var, yalnızca Genel üyeler proxy türü hata ayıklayıcı değişken penceresinde görüntüler. Özel üyelerin görüntülenmez. Veri penceresi davranışını özniteliği Gelişmiş görünümler tarafından değiştirilmez.  
  
 Bir veri penceresinde türü yanındaki artı (+) tıklatarak kullanıcı, veya aracılığıyla uygulamayı nesne genişletilir kadar gereksiz performans cezalarını önlemek için görüntü proxy özniteliklerini işlenmez <xref:System.Diagnostics.DebuggerBrowsableAttribute> özniteliği. Bu nedenle, hiçbir öznitelik görüntü türünü uygulanması önerilir. Öznitelikleri olabilir ve görüntü türü gövdesi içinde uygulanmalıdır.  
  
 Aşağıdaki kod örneğinde kullanımı gösterilmiştir <xref:System.Diagnostics.DebuggerTypeProxyAttribute> bir hata ayıklayıcı görüntü proxy olarak kullanılacak bir türünü belirtin.  
  
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
 Aşağıdaki kod örneğinde görüntülenebilir [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] uygulama sonuçlarını görmek için <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, ve <xref:System.Diagnostics.DebuggerTypeProxyAttribute> öznitelikleri.  
  
### <a name="code"></a>Kod  
 [!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
 [!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
 [!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.DebuggerDisplayAttribute>  
 <xref:System.Diagnostics.DebuggerBrowsableAttribute>  
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
