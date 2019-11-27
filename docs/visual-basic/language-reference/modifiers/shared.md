---
title: '{1&gt;Paylaşılan&lt;1}'
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: 98fa25d2283408dfb80e82fbc620a1b284e5c530
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349125"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
Bir veya daha fazla bildirilmemiş programlama öğesinin, bir sınıf veya yapı ile ilişkili olduğunu ve sınıf veya yapının belirli bir örneğiyle ilişkilendirildiğini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="when-to-use-shared"></a>Paylaşılan ne zaman kullanılır  
 Bir sınıfın veya yapının bir üyesinin paylaşılması, *paylaşılan*değil, her örneğin kendi kopyasını tutan her örnek için kullanılabilir hale getirir. Örneğin, bir değişkenin değeri uygulamanın tamamına geçerliyse, bu yararlıdır. Bu değişkenin `Shared`olduğunu bildirirseniz, tüm örnekler aynı depolama konumuna erişir ve bir örnek değişkenin değerini değiştirirse, tüm örnekler güncelleştirilmiş değere erişir.  
  
 Paylaşım, üyenin erişim düzeyini değiştirmez. Örneğin, bir sınıf üyesi paylaşılabilir ve özel (yalnızca sınıfın içinden erişilebilir) veya paylaşılmayan ve genel olabilir. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** Yalnızca modül düzeyinde `Shared` kullanabilirsiniz. Bu, bir `Shared` öğesi için bildirim bağlamının bir sınıf veya yapı olması ve kaynak dosya, ad alanı veya yordam olması anlamına gelir.  
  
- **Birleşik değiştiriciler.** Aynı bildirimde [geçersiz kılmalar](../../../visual-basic/language-reference/modifiers/overrides.md), geçersiz [kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)veya [static](../../../visual-basic/language-reference/modifiers/static.md) ile birlikte `Shared` belirtemezsiniz.  
  
- **Erişme.** Bir paylaşılan öğeye, sınıfının veya yapısının belirli bir örneğinin değişken adıyla değil, sınıf veya yapı adıyla niteleyerek erişebilirsiniz. Paylaşılan üyelerine erişmek için bir sınıf veya yapının örneğini oluşturmanız da gerekmez.  
  
     Aşağıdaki örnek, <xref:System.Double> yapısı tarafından sunulan <xref:System.Double.IsNaN%2A> paylaşılan yordamı çağırır.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- **Örtük paylaşım.** `Shared` değiştiricisini [const ifadesinde](../../../visual-basic/language-reference/statements/const-statement.md)kullanamazsınız, ancak sabitler örtülü olarak paylaşılır. Benzer şekilde, bir modülün veya arabirimin üyesini `Shared`olarak bildiremezsiniz, ancak örtülü olarak paylaşılır.  
  
## <a name="behavior"></a>Davranış  
  
- **Depo.** Paylaşılan bir değişken veya olay, sınıfı veya yapısını kaç tane veya birkaç örnek oluşturduğunuz ve bu durumda yalnızca bir kez bellekte depolanır. Benzer şekilde, paylaşılan bir yordam veya özellik yalnızca bir yerel değişken kümesi tutar.  
  
- **Örnek değişkenine erişme.** Kendi sınıfının veya yapısının belirli bir örneğini içeren bir değişkenin adı ile niteleyerek paylaşılan bir öğeye erişmek mümkündür. Bu, genellikle beklenen şekilde çalışsa da, derleyici bir uyarı mesajı oluşturur ve değişken yerine sınıf veya yapı adıyla erişimi yapar.  
  
- **Örnek Ifadesiyle erişme.** Sınıfının veya yapısının bir örneğini döndüren bir ifade aracılığıyla paylaşılan bir öğeye eriştiğinizde, derleyici, ifadeyi değerlendirmek yerine sınıf veya yapı adı üzerinden erişim sağlar. Bu, ifadenin diğer eylemleri gerçekleştirmesini ve örneği döndürmesini amaçlıyorsanız beklenmedik sonuçlar üretir. Aşağıdaki örnek bunu göstermektedir.  
  
    ```vb
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     Önceki örnekte, derleyici her iki durumda da kodun paylaşılan değişkenine `total` bir örnek üzerinden eriştiği bir uyarı mesajı oluşturur. Her durumda, erişimi doğrudan sınıf `shareTotal` aracılığıyla yapar ve herhangi bir örneği kullanmaz. `returnClass`yordam çağrısı olması durumunda bu, `returnClass`bir çağrı üretmediği anlamına gelir; bu nedenle "Function returnClass ()" adlı Işlev "olarak adlandırılan ek eylem gerçekleştirilmez.  
  
 `Shared` değiştiricisi şu bağlamlarda kullanılabilir:  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Visual Basic ömrü](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
