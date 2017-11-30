---
title: Visual Basic'de Kapsam
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9bfda19b9f5ee96d45a0322541b35dfab7635d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="scope-in-visual-basic"></a>Visual Basic'de Kapsam
*Kapsam* bildirilen öğesinin adını niteleme veya yoluyla kullanılabilir hale getirme olmadan başvurduğu tüm kod kümesidir bir [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Bir öğe kapsamı aşağıdaki düzeyden birine sahip olabilir:  
  
|Düzey|Açıklama|  
|-----------|-----------------|  
|Blok kapsamı|Yalnızca kod içinde kullanılabilir engellemek, onu bildirildiği içinde|  
|Yordam kapsamı|İçinde bildirilmiş yordamı içindeki tüm kod için kullanılabilir|  
|Modül kapsamı|Modül, sınıf veya yapı içinde bildirilmiş içindeki tüm kod için kullanılabilir|  
|Namespace kapsamı|İçinde bildirilen ad alanındaki tüm kod için kullanılabilir|  
  
 Bu düzeyde dar (bloğun) kapsam ilerlemesini geniş (ad), burada *dar kapsamı* niteliğe olmadan öğesine başvurabilir kodu en küçük kümesini anlamına gelir. Daha fazla bilgi için bu sayfada "Kapsam düzeyleri" bakın.  
  
## <a name="specifying-scope-and-defining-variables"></a>Kapsam belirtme ve değişkenleri tanımlama  
 Bunu bildirirken bir öğe kapsamını belirtin. Kapsamı şu etkenlere bağlıdır:  
  
-   Öğe bildirme bölge (blok, yordam, modülü, sınıf veya yapı)  
  
-   Öğenin bildirimi içeren ad alanı  
  
-   Öğe için bildirme erişim düzeyi  
  
 Bunu yapmak için aynı adlı ancak farklı bir kapsam değişkenlerle tanımlarken kullanım dikkatli beklenmeyen sonuçlara yol açabilir. Daha fazla bilgi için bkz: [bildirilmiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="levels-of-scope"></a>Kapsam düzeyleri  
 Bir programlama öğesi içinde bildirirken bölge kullanılabilir. Aynı bölgede tüm kod adını niteleme olmadan öğesine başvurabilir.  
  
### <a name="block-scope"></a>Blok kapsamı  
 Bir blok başlatma ve sonlandırma aşağıdaki gibi bildirim deyimleri içine alınmış deyimleri kümesidir:  
  
-   `Do`ve`Loop`  
  
-   `For`[`Each`] ve`Next`  
  
-   `If`ve`End If`  
  
-   `Select`ve`End Select`  
  
-   `SyncLock`ve`End SyncLock`  
  
-   `Try`ve`End Try`  
  
-   `While`ve`End While`  
  
-   `With`ve`End With`  
  
 Bir bloğu içinde bir değişken bildirirseniz bu blokta yalnızca kullanabilirsiniz. Aşağıdaki örnekte, tamsayı değişkenin kapsamını `cube` arasında blok `If` ve `End If`, ve artık başvurabilirsiniz `cube` yürütme dışında blok zaman geçirir.  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  Bir değişkenin kapsamını bir bloğu ile sınırlı olsa bile, yaşam süresi hala tüm yordamın olmasıdır. Blok yordam sırasında birden çok kez girerseniz, her bir blok değişken önceki değerine korur. Böyle bir durumda beklenmeyen sonuçlardan kaçınmak için bloğun başlangıcında blok değişkenlerini başlatmak akıllıca olur.  
  
### <a name="procedure-scope"></a>Yordam kapsamı  
 Bir yordam içinde bildirilen bir öğe bu yordamın dışında kullanılamaz. Bildirim içeren yordamı da kullanabilirsiniz. Bu düzeyde değişkenlerdir olarak da bilinen *yerel değişkenler*. Bunlarla bildirme [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md), ile veya olmadan [statik](../../../../visual-basic/language-reference/modifiers/static.md) anahtar sözcüğü.  
  
 Yordam ve blok kapsamı yakından ilişkili. Yordam içindeki ancak bu yordam herhangi blokta dışında bir değişken bildirirseniz, değişken blok yordamın tamamını olduğu blok kapsamlı olarak düşünebilirsiniz.  
  
> [!NOTE]
>  Tüm yerel öğeler, bunlar olsa bile `Static` değişkenleri, göründükleri yordamı özel. Kullanan tüm öğesi bildiremezsiniz [ortak](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğü bir yordam içinde.  
  
### <a name="module-scope"></a>Modül kapsamı  
 Tek ifadeli kolaylık sağlamak için *modül düzeyi* modüller, sınıflar ve yapılar için eşit oranda geçerlidir. Herhangi bir yordamda veya blok dışında ancak modülü, sınıf veya yapı içinde bildirim deyiminin yerleştirerek bu düzeyde öğeleri bildirebilirsiniz.  
  
 Modül düzeyinde bir bildirimi yaptığınızda, seçtiğiniz erişim düzeyi kapsamı belirler. Modül, sınıf veya yapı içeren ad alanı kapsamı de etkiler.  
  
 Öğeleri bildirmek için [özel](../../../../visual-basic/language-reference/modifiers/private.md) erişim düzeyi, bu modüldeki her yordam için ancak farklı bir modüldeki herhangi bir kod için kullanılabilir. `Dim` Deyimi modülü düzeyinde varsayılanları `Private` hiçbir erişim düzeyi anahtar kullanmıyorsanız. Ancak, kapsam ve erişim düzeyi daha belirgin kullanarak yapabileceğiniz `Private` anahtar sözcük `Dim` deyimi.  
  
 Aşağıdaki örnekte, dize değişkenine modülde tanımlanmış tüm yordamları başvurabilir `strMsg`. İkinci yordam çağrıldığında, dize değişkenine içeriğini görüntüler `strMsg` iletişim kutusunda.  
  
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
 Modül kullanarak düzeyinde bir öğe bildirirseniz [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) veya [ortak](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğü, bu duruma tüm yordamlarda öğesi bildirilmiş ad alanı için kullanılabilir. Önceki örnekte, dize değişkenine için aşağıdaki değişiklikle birlikte `strMsg` için ad alanı bildiriminden başka bir yerindeki kodu tarafından başvurulabilir.  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 Namespace kapsam iç içe geçmiş ad alanları içerir. Bir ad alanında bulunan bir öğeyi de bu ad alanı içinde iç içe geçmiş herhangi bir ad alanı içinde kullanılabilir.  
  
 Projenizi herhangi içermiyorsa [Namespace deyimi](../../../../visual-basic/language-reference/statements/namespace-statement.md)projesinde her şeyi durumda aynı ad. Bu durumda, ad alanı kapsamı, proje kapsamı olarak düşünülebilir. `Public`bir modül, sınıf veya yapı öğeleri de kendi projeye başvuruda bulunan herhangi bir projesine kullanılabilir.  
  
## <a name="choice-of-scope"></a>Kapsam seçeneği  
 Bir değişken bildirin, aşağıdaki noktaları kapsamı seçerken göz önünde bulundurmalıdır.  
  
### <a name="advantages-of-local-variables"></a>Yerel değişkenler avantajları  
 Yerel değişkenler aşağıdaki nedenlerle geçici hesaplama, herhangi bir tür için iyi bir seçimdir şunlardır:  
  
-   **Ad çakışması kaçınma.** Yerel değişken adları, çakışma etkilenmez. Örneğin, adında bir değişkeni içeren birkaç farklı yordamlar oluşturabilirsiniz `intTemp`. Sürece her `intTemp` bildirilen yerel değişken olarak, her bir yordam yalnızca kendi sürümü tanır, `intTemp`. Herhangi bir yordam, yerel değerin değiştirebilir `intTemp` etkilemeden `intTemp` diğer yordamlar değişkenleri.  
  
-   **Bellek tüketimi.** Yalnızca kendi yordamı çalışırken yerel değişkenler bellek tüketir. Kendi bellek, yordamı çağıran kodu döndürdüğünde yayımlanır. Bunun aksine, [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) ve [statik](../../../../visual-basic/language-reference/modifiers/static.md) değişkenleri uygulamanızı çalışmadığında kadar bellek kaynaklarının kullanılmasına, bu nedenle bunları yalnızca gerekli olduğunda kullanın. *Örnek değişkenleri* bunları daha az verimlidir yerel değişkenler, ancak büyük olasılıkla daha verimlidir kılan kendi örneği mevcut devam ederken bellek tüketmesine `Shared` veya `Static` değişkenleri.  
  
### <a name="minimizing-scope"></a>Kapsam en aza indirme  
 Genel olarak, herhangi bir değişken veya sabit bildirme kapsamı olarak dar yapmak için uygulama programlama iyi olur (blok kapsamı olan dar). Bu bellek korunmasına yardımcı olur ve yanlışlıkla yanlış değişkenine başvurarak kodunuzu olasılığını en aza indirir. Benzer şekilde, olması için bir değişken bildirmelidir [statik](../../../../visual-basic/language-reference/modifiers/static.md) yalnızca bu yordam çağrıları arasında değeri korumak gerekli olduğunda.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bildirilen öğe özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Nasıl yapılır: bir değişkenin kapsamını denetleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [Visual Basic'de ömür](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Visual Basic'de erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Bildirilmiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Değişken bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
