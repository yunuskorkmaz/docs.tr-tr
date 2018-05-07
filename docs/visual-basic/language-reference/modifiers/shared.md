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
ms.openlocfilehash: b15dd08d69f372317b9140001e8072eeb66d44ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
Bir veya daha fazla bildirilen programlama öğeleri ile bir sınıf veya yapı büyük ve değil sınıf veya yapı belirli bir örneği ile ilişkili olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="when-to-use-shared"></a>Ne zaman kullanılacağı paylaşılan  
 Bir sınıf veya yapı üyesi paylaşımı kullanılabilir hale getirir, her örneği için yerine *paylaşılmayan*, burada her örneğinin kendi kopyasını tutar. Bir değişkenin değeri uygulamanın tümünü uygulanıyorsa, örneğin, kullanışlıdır. Olması için bu değişkeni bildirirseniz `Shared`, ardından tüm örnekleri aynı depolama konumuna erişim ve bir örnek değişkenin değeri değişirse, tüm örnekler güncelleştirilmiş değeri erişim.  
  
 Paylaşım erişim düzeyi üyenin değiştirmez. Örneğin, bir sınıf üyesi paylaşılabilir ve özel (sınıf içinde erişilebilir yalnızca gelen), ya da paylaşılmayan hem de genel. Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Bildirim bağlamı.** Kullanabileceğiniz `Shared` yalnızca modülü düzeyinde. Bu bildirimi bağlamının anlamına gelir bir `Shared` öğesi bir sınıf veya yapı olması ve kaynak dosyasını, ad alanı veya yordam olamaz.  
  
-   **Birleşik değiştirici.** Belirtemeyeceğiniz `Shared` ile birlikte [geçersiz kılmaları](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), veya [ Statik](../../../visual-basic/language-reference/modifiers/static.md) aynı bildirimi.  
  
-   **Erişme.** Sınıf veya yapı adıyla birlikte, belirli bir sınıf ya da yapısı örneği değişken adını bilgisayardı niteleme tarafından paylaşılan bir öğenin erişin. Hatta sınıfı veya paylaşılan üyelerine erişmek için yapısının bir örneğini oluşturmanız gerekmez.  
  
     Aşağıdaki örnek paylaşılan yordam çağrıları <xref:System.Double.IsNaN%2A> tarafından sunulan <xref:System.Double> yapısı.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   **Örtük paylaşımı.** Kullanamazsınız `Shared` değiştiricisi bir [Const deyimi](../../../visual-basic/language-reference/statements/const-statement.md), ancak sabitleri örtük olarak paylaşılan. Benzer şekilde, olması için bir modül veya üyesi bir arabirim bildiremezsiniz `Shared`, ancak örtük olarak paylaşılır.  
  
## <a name="behavior"></a>Davranış  
  
-   **depolama alanı.** Yalnızca kaç veya birkaç örneği olsun, kendi sınıf veya yapı oluşturduktan sonra bir paylaşılan değişken veya olay bellekte depolanır. Benzer şekilde, bir paylaşılan bir yordam veya özellik, yerel değişkenleri yalnızca bir kümesi tutar.  
  
-   **Bir örnek değişkeni erişme.** Belirli bir sınıf ya da yapısı örneği içeren bir değişkeni adı ile niteleme tarafından paylaşılan bir öğesine erişmek mümkündür. Bu genellikle beklendiği gibi çalışır, ancak derleyici bir uyarı iletisi oluşturur ve sınıf veya yapı adı değişkeni yerine üzerinden erişim sağlar.  
  
-   **Bir örneği ifade yoluyla erişme.** Paylaşılan bir öğe, sınıf veya yapı örneğini döndüren bir ifadeye erişirseniz, derleyici ifade değerlendirme yerine sınıf veya yapı adı ile erişim sağlar. Diğer eylemlerin yanı sıra örneği döndüren gerçekleştirmek için ifade amaçlıyorsanız bu beklenmeyen sonuçlar üretir. Aşağıdaki örnek bunu göstermektedir.  
  
    ```  
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
  
     Önceki örnekte derleyici bir uyarı iletisi kodu paylaşılan değişken erişen her iki kez oluşturur `total` bir örnek üzerinden. Her durumda kolaylaştırır sınıfı aracılığıyla doğrudan erişim `shareTotal` ve kullanmayan herhangi bir örneğini kullanın. Yordam hedeflenen çağrısı durumunda `returnClass`, bu, hatta oluşturmaz yapılan bir çağrı anlamına gelir `returnClass`, "olarak adlandırılan işlevi returnClass()" görüntüleme başka bir işlem gerçekleştirilemiyor.  
  
 `Shared` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Static](../../../visual-basic/language-reference/modifiers/static.md)  
 [Visual Basic'de ömür](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
