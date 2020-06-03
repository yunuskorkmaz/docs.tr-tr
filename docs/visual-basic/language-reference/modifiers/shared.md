---
title: Shared
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
ms.openlocfilehash: 000cc13bc6e80914e9a21b6ee60e91127809ee08
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84307091"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)

Bir veya daha fazla bildirilmemiş programlama öğesinin, bir sınıf veya yapı ile ilişkili olduğunu ve sınıf veya yapının belirli bir örneğiyle ilişkilendirildiğini belirtir.

## <a name="when-to-use-shared"></a>Paylaşılan ne zaman kullanılır

Bir sınıfın veya yapının bir üyesinin paylaşılması, her örneğin kendi kopyasını sakladığı, *paylaşılmayan*değil, her örnek için kullanılabilir hale getirir. Örneğin, bir değişkenin değeri uygulamanın tamamına geçerliyse, bu yararlıdır. Bu değişkenin olduğunu bildirirseniz `Shared` , tüm örnekler aynı depolama konumuna erişir ve bir örnek değişkenin değerini değiştirirse, tüm örnekler güncelleştirilmiş değere erişir.

Paylaşım, üyenin erişim düzeyini değiştirmez. Örneğin, bir sınıf üyesi paylaşılabilir ve özel (yalnızca sınıftan erişilebilir) veya paylaşılmayan ve genel olabilir. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** `Shared`Yalnızca modül düzeyinde kullanabilirsiniz. Diğer bir deyişle, bir öğe için bildirim bağlamı `Shared` bir sınıf veya yapı olmalıdır ve kaynak dosya, ad alanı veya yordam olamaz.

- **Birleşik değiştiriciler.** `Shared`Aynı bildirimde [geçersiz kılmalar](../../../visual-basic/language-reference/modifiers/overrides.md), geçersiz [kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)veya [static](../../../visual-basic/language-reference/modifiers/static.md) ile birlikte belirtemezsiniz.

- **Erişme.** Bir paylaşılan öğeye, sınıfının veya yapısının belirli bir örneğinin değişken adıyla değil, sınıf veya yapı adıyla niteleyerek erişebilirsiniz. Paylaşılan üyelerine erişmek için bir sınıf veya yapının örneğini oluşturmanız da gerekmez.

     Aşağıdaki örnek, <xref:System.Double.IsNaN%2A> Yapı tarafından sunulan paylaşılan yordamı çağırır <xref:System.Double> .

     ```vb
     If Double.IsNaN(result) Then Console.WriteLine("Result is mathematically undefined.")
     ```

- **Örtük paylaşım.** `Shared`Bir [const ifadesinde](../../../visual-basic/language-reference/statements/const-statement.md)değiştirici kullanamazsınız, ancak sabitler örtülü olarak paylaşılır. Benzer şekilde, bir modülün veya arabirimin bir üyesini `Shared` değil, örtülü olarak paylaşılırlar.

## <a name="behavior"></a>Davranış

- **Depo.** Paylaşılan bir değişken veya olay, sınıfı veya yapısını kaç tane veya birkaç örnek oluşturduğunuz ve bu durumda yalnızca bir kez bellekte depolanır. Benzer şekilde, paylaşılan bir yordam veya özellik yalnızca bir yerel değişken kümesi tutar.

- **Örnek değişkenine erişme.** Kendi sınıfının veya yapısının belirli bir örneğini içeren bir değişkenin adı ile niteleyerek paylaşılan bir öğeye erişmek mümkündür. Bu, genellikle beklenen şekilde çalışsa da, derleyici bir uyarı mesajı oluşturur ve değişken yerine sınıf veya yapı adıyla erişimi yapar.

- **Örnek Ifadesiyle erişme.** Sınıfının veya yapısının bir örneğini döndüren bir ifade aracılığıyla paylaşılan bir öğeye eriştiğinizde, derleyici, ifadeyi değerlendirmek yerine sınıf veya yapı adı üzerinden erişim sağlar. Bu, ifadenin diğer eylemleri gerçekleştirmesini ve örneği döndürmesini amaçlıyorsanız beklenmedik sonuçlar üretir. Aşağıdaki örnek bunu göstermektedir.
  
    ```vb
    Sub Main()
        ' The following line is the preferred way to access Total.
        ShareTotal.Total = 10

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of through
        ' the variable instanceVar. This works as expected and adds
        ' 100 to Total.
        Dim instanceVar As New ShareTotal
        instanceVar.Total += 100

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of calling
        ' ReturnClass(). This adds 1000 to total but does not work as
        ' expected, because the WriteLine in ReturnClass() does not run.
        Console.WriteLine("Value of total is " & CStr(ShareTotal.Total))
        ReturnClass().Total += 1000
    End Sub

    Public Function ReturnClass() As ShareTotal
        Console.WriteLine("Function ReturnClass() called")
        Return New ShareTotal
    End Function

    Public Class ShareTotal
        Public Shared Property Total As Integer
    End Class
    ```

     Önceki örnekte, derleyici her iki durumda da kodun paylaşılan özelliğe bir örnek aracılığıyla eriştiği bir uyarı mesajı oluşturur `Total` . Her durumda, erişimi doğrudan sınıf üzerinden yapar `ShareTotal` ve herhangi bir örneği kullanmaz. Yordama yönelik amaçlanan çağrı durumunda `ReturnClass` Bu, bir çağrı üretmediği anlamına gelir; bu `ReturnClass` nedenle "Function returnClass ()" adlı "işlev" olarak adlandırılan ek eylem gerçekleştirilmez.

`Shared`Değiştirici şu bağlamlarda kullanılabilir:

- [Dim Deyimi](../statements/dim-statement.md)
- [Event Deyimi](../statements/event-statement.md)
- [Function Deyimi](../statements/function-statement.md)
- [Operator Deyimi](../statements/operator-statement.md)
- [Property Deyimi](../statements/property-statement.md)
- [Sub Deyimi](../statements/sub-statement.md)
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shadows](shadows.md)
- [Se](static.md)
- [Visual Basic'de Ömür](../../programming-guide/language-features/declared-elements/lifetime.md)
- [Yordamlar](../../programming-guide/language-features/procedures/index.md)
- [Yapılar](../../programming-guide/language-features/data-types/structures.md)
- [Nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md)
