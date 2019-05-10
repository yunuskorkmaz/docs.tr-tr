---
title: Shared (Visual Basic)
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
ms.openlocfilehash: fd43ef7cb5c16995fff87a65fc0f0974d8f4a47d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647699"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
Bir veya daha fazla bildirilmiş programlama öğesine bir sınıf veya yapı büyük ile değil, belirli bir sınıfın veya yapının örneği ile ilişkili olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="when-to-use-shared"></a>Paylaşılan ne zaman kullanılır?  
 Bir sınıf veya yapı üyesi paylaşımı kullanılabilir hale getirir, her örnek için yerine *paylaşılmayan*, burada her örnek kendi kopyasını tutar. Bir değişkenin değeri uygulamanın tamamı için geçerliyse bu örneğin, kullanışlıdır. Olması için bu değişken bildirirseniz `Shared`, ardından tüm örnekleri aynı depolama konumu erişmek ve bir örnek, değişkenin değeri değişirse, güncelleştirilmiş değeri tüm örneklere erişmek.  
  
 Paylaşımı bir üye erişim düzeyini değiştirmez. Örneğin, bir sınıf üyesinin paylaşılabilir ve özel (sınıf içinde erişilebilir yalnızca), veya paylaşılmayan hem de ortak. Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** Kullanabileceğiniz `Shared` yalnızca Modül düzeyinde. Bildirim bağlamı başka bir deyişle bir `Shared` öğesi bir sınıf veya yapı olmalıdır ve bir kaynak dosyası, ad alanı ya da yordamın olamaz.  
  
- **Birleşik değiştiriciler.** Belirtemezsiniz `Shared` ile birlikte [geçersiz kılmalar](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), veya [ Statik](../../../visual-basic/language-reference/modifiers/static.md) aynı bildirimde.  
  
- **Erişme.** Sınıf veya yapı adı ile belirli bir örneği, sınıfın veya yapının değişken adı ile değil niteleme tarafından paylaşılan bir öğe erişin. Bile bir sınıf veya yapı paylaşılan üyelerine erişmek için bir örneğini oluşturmak gerekmez.  
  
     Aşağıdaki örnek, paylaşılan bir yordam çağrıları <xref:System.Double.IsNaN%2A> tarafından kullanıma sunulan <xref:System.Double> yapısı.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- **Örtük paylaşma.** Kullanamazsınız `Shared` değiştiricisini bir [Const deyimi](../../../visual-basic/language-reference/statements/const-statement.md), ancak sabitleri örtük olarak paylaşılır. Benzer şekilde, bir üyesinin bir modül veya bir arabirim bildiremezsiniz `Shared`, ancak örtük olarak paylaşılır.  
  
## <a name="behavior"></a>Davranış  
  
- **Depolama alanı.** Yalnızca ne kadar ya da birkaç örnek ne olursa olsun, kendi sınıf veya yapı oluşturduktan sonra paylaşılan bir değişken veya olay bellekte depolanır. Benzer şekilde, paylaşılan bir yordam veya özellik yerel değişkenler yalnızca bir kümesini içerir.  
  
- **Bir örnek değişkeni erişme.** Belirli bir alt sınıf veya yapının örneğini içeren bir değişken adını nitelendirme tarafından paylaşılan bir öğeye erişmeyi mümkündür. Bu genellikle beklendiği gibi çalışır, ancak derleyici bir uyarı iletisi oluşturuyor ve sınıf veya yapı adı yerine değişken üzerinden erişim sağlar.  
  
- **Bir örnek ifade yoluyla erişme.** Paylaşılan öğe, bir sınıfın veya yapının örneğini döndüren bir ifade erişirseniz, derleyici ifadenin değerlendirilmesi yerine sınıf veya yapı adı aracılığıyla erişim sağlar. Bu, diğer eylemlerin yanı sıra örneği döndüren gerçekleştirmek için ifade hedeflediyseniz beklenmeyen sonuçlar üretir. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
     Önceki örnekte, derleyici bir uyarı iletisi kod erişen paylaşılan değişkeni iki kez oluşturur `total` bir örnek üzerinden. Her durumda, sınıf üzerinden doğrudan erişim sağlar `shareTotal` ve kullanmayan herhangi bir örneğini kullanın. Hedeflenen çağrı yordam söz konusu olduğunda `returnClass`, bu, hatta oluşturmaz çağrısı anlamına gelir `returnClass`, "adlı işlevi returnClass()" görüntülemenin başka bir işlem gerçekleştirilemiyor.  
  
 `Shared` Bu bağlamda değiştirici kullanılabilir:  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Visual Basic'de ömür](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
