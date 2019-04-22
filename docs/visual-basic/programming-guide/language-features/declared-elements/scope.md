---
title: Visual Basic'de Kapsam
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 6139af65958cefe43578f436204fa6836a71de0b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823551"
---
# <a name="scope-in-visual-basic"></a>Visual Basic'de Kapsam
*Kapsam* bildirilen bir öğenin adını nitelendirme veya aracılığıyla kullanılabilir hale getirme olmadan başvurduğu tüm kod kümesidir. bir [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Bir öğe kapsamı aşağıdaki düzeylerde birine sahip olabilir:  
  
|Düzey|Açıklama|  
|-----------|-----------------|  
|Blok kapsamı|Yalnızca kod içinde kullanılabilir block bildirildiği içinde|  
|Yordam kapsamı|Tüm kod içinde bildirildiği yordam içinde kullanılabilir|  
|Modül kapsamı|Modül, sınıf veya yapı içinde bildirildiği tüm kod için kullanılabilir|  
|Namespace kapsamı|İçinde bildirildiği ad alanındaki tüm kod için kullanılabilir|  
  
 Bu düzeyde dar (blok) kapsam ilerlemesini geniş (ad), burada *kapsamdan* nitelik olmadan öğesine başvurabilir kod en küçük kümesini anlamına gelir. Daha fazla bilgi için bu sayfada "Kapsam düzeyleri" konusuna bakın.  
  
## <a name="specifying-scope-and-defining-variables"></a>Kapsam belirleme ve değişkenleri tanımlama  
 Bildirdiğinizde, bir öğenin kapsamını belirtin. Kapsam aşağıdaki etkenlere bağlıdır:  
  
-   Öğe bildirdiğiniz bölge (blok, yordam, modül, sınıf veya yapının)  
  
-   Öğenin bildirimi içeren ad alanı  
  
-   Öğe için bildirmek erişim düzeyi  
  
 Aynı ada ancak farklı kapsam değişkenlerle belirlemekten tanımlarken kullanmak dikkat beklenmeyen sonuçlara neden olabilir. Daha fazla bilgi için [bildirilmiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="levels-of-scope"></a>Kapsam düzeyleri  
 Bir programlama öğesi bildirdiğiniz bölge kullanılabilir. Aynı bölgedeki tüm kod adıyla nitelemeden öğesine başvurabilir.  
  
### <a name="block-scope"></a>Blok kapsamı  
 Bir blok başlatma ve sonlandırma aşağıdaki gibi bildirim deyimleri içine alınmış deyimleri kümesidir:  
  
-   `Do` ve `Loop`  
  
-   `For` [`Each`] ve `Next`  
  
-   `If` ve `End If`  
  
-   `Select` ve `End Select`  
  
-   `SyncLock` ve `End SyncLock`  
  
-   `Try` ve `End Try`  
  
-   `While` ve `End While`  
  
-   `With` ve `End With`  
  
 Bir blok içinde bir değişken bildirirseniz, yalnızca bu blokta kullanabilirsiniz. Aşağıdaki örnekte, tam sayı değişkeni kapsamını `cube` arasında blok `If` ve `End If`, ve artık başvurabilirsiniz `cube` zaman Yürütme bloğunun dışına geçirir.  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  Bir değişkenin kapsamını bir blokla sınırlı olsa bile, yaşam süresi hala tüm yordamın olmasıdır. Blok yordam sırasında birden çok kez girerseniz, her bir blok değişken önceki değerini korur. Böyle bir durumda beklenmeyen sonuçlardan kaçınmak için bloğun başlangıcında blok değişkenlerini başlatmak üzere akıllıca olur.  
  
### <a name="procedure-scope"></a>Yordam kapsamı  
 Bir yordam içinde bildirilen bir öğenin dışında bu yordamın kullanılabilir değil. Yalnızca bildirimi içeren yordamı da kullanabilirsiniz. Bu düzeyde değişkenlerdir olarak da bilinen *yerel değişkenler*. Kendileriyle bildirin [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)veya bu profiller olmadan [statik](../../../../visual-basic/language-reference/modifiers/static.md) anahtar sözcüğü.  
  
 Yordam ve blok kapsamı yakından ilgili. Bir yordam içinde ancak bu yordam herhangi bir bloğu dışında bir değişken bildirirseniz, değişken blok yordamın tamamını olduğu blok kapsamlı olarak düşünebilirsiniz.  
  
> [!NOTE]
>  Tüm yerel öğeler, bunlar olsa bile `Static` göründükleri yordama özel değişkenler. Öğesini kullanarak bildiremezsiniz [genel](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğü bir yordam içinde.  
  
### <a name="module-scope"></a>Modül kapsamı  
 Kolaylık sağlamak adına, tek ifadeli *modül düzeyi* modülleri, sınıflar ve yapılar için eşit oranda geçerlidir. Bildirim deyiminin dışında herhangi bir yordam veya blok ancak modül, sınıf veya yapı içinde yerleştirerek bu düzeyde öğeleri bildirebilirsiniz.  
  
 Bir bildirimi Modül düzeyinde değişiklik yaptığınızda, kapsamı seçtiğiniz erişim düzeyini belirler. Modül, sınıf veya yapı içeren ad uzayı kapsam de etkiler.  
  
 Bildirmek için öğeleri [özel](../../../../visual-basic/language-reference/modifiers/private.md) erişim düzeyi bu modüldeki her yordam, ancak farklı bir modül herhangi bir kod için kullanılabilir. `Dim` Deyimi Modül düzeyinde varsayılan olarak `Private` erişim düzeyi anahtar sözcükleri kullanmazsanız. Bununla birlikte, kapsamı ve erişim düzeyi daha belirgin kullanarak yapabileceğiniz `Private` anahtar sözcüğünü `Dim` deyimi.  
  
 Aşağıdaki örnekte, tüm yordamları modülde tanımlanmış dize değişkenini ifade edebilir `strMsg`. İkinci yordam çağrıldığında, string değişkeni içeriğini görüntüler. `strMsg` iletişim kutusunda.  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### <a name="namespace-scope"></a>Namespace kapsamı  
 Modül kullanarak düzeyinde bir öğe bildirirseniz [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) veya [genel](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğü, bu duruma öğesi bildirilmiş ad alanı genelinde tüm yordamları için kullanılabilir. Önceki örnekte, dize değişkeni için aşağıdaki değişikliği ile `strMsg` kod bildiriminden ad alanındaki herhangi bir ifade.  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 Namespace kapsam iç içe ad alanlarını içerir. Ad alanı içinde bulunan bir öğe aynı zamanda bu ad alanı içinde iç içe geçmiş herhangi bir ad alanı içinde kullanılabilir.  
  
 Projenizi herhangi içermiyorsa [Namespace deyimi](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, projedeki her şeyi aynı ad alanında. Bu durumda, ad alanı kapsamında, proje kapsamı olarak düşünülebilir. `Public` bir modül, sınıf veya yapı öğeleri de kendi projesine başvuran projeler için kullanılabilir.  
  
## <a name="choice-of-scope"></a>Kapsam seçeneği  
 Bir değişken bildirdiğinizde, aşağıdaki noktaları kapsamı seçerken göz önünde tutmalısınız.  
  
### <a name="advantages-of-local-variables"></a>Yerel değişkenler avantajları  
 Yerel değişkenler, aşağıdaki nedenlerden dolayı herhangi bir türden geçici hesaplama için iyi bir seçim şunlardır:  
  
-   **Ad çakışması engelleme.** Yerel değişken adları çakışma açık değildir. Örneğin, adında bir değişkene içeren birkaç farklı yordamlar oluşturabilirsiniz `intTemp`. Olduğu sürece her `intTemp` bildirilen yerel değişken olarak, her yordam, yalnızca kendi sürüm tanır, `intTemp`. Herhangi bir yordam, yerel değeri değiştirebilir `intTemp` etkilemeden `intTemp` diğer yordamlar değişkenleri.  
  
-   **Bellek tüketimi.** Yalnızca kendi yordamı çalışırken yerel değişkenler bellek tüketir. Yordamı çağıran koda geri döndüğünde, kendi bellek serbest bırakılır. Bunun aksine, [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) ve [statik](../../../../visual-basic/language-reference/modifiers/static.md) değişkenleri uygulamanızın çalışmayı kadar bellek kaynaklarının kullanılmasına, bunları yalnızca gerekli olduğunda kullanın. *Örnek değişkenleri* bunları daha az yerel değişkenler verimlidir, ancak büyük olasılıkla daha verimli olmasını sağlayan kendi örneği var olmaya devam ederken bellek `Shared` veya `Static` değişkenleri.  
  
### <a name="minimizing-scope"></a>Kapsam en aza indirme  
 Genel olarak, herhangi bir değişken veya sabit bildirdiğinizde, kapsam olarak dar yapmak alışkanlıktır (blok kapsamı olan en düşük). Bu işlem, bellek korunmasına yardımcı olur ve kodunuzu deneyebileceğinizi hatalı değişkenine başvuran olasılığını en aza indirir. Benzer şekilde, olması için bir değişken bildirmelidir [statik](../../../../visual-basic/language-reference/modifiers/static.md) yalnızca zaman değerini yordam çağrıları arasında korumak gereklidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilen Öğe Özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Nasıl yapılır: Bir değişkenin kapsamını denetleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [Visual Basic'de ömür](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Visual Basic'de erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
