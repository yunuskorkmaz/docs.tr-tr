---
title: Property deyimi (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 4c92e7b3892fa35035935d5db317c72d74814ab8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512989"
---
# <a name="property-statement"></a>Property Deyimi
Adı bir özelliği ve depolamak ve özelliğin değerini almak için kullanılan özellik yordamlarını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]  
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
    [ <attributelist> ] [ accessmodifier ] Get  
        [ statements ]  
    End Get  
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )  
        [ statements ]  
    End Set  
End Property  
- or -  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]   
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
```  
  
## <a name="parts"></a>Bölümler  
  
-   `attributelist`  
  
     İsteğe bağlı. Bu özellik için geçerli olan özniteliklerin listesi veya `Get` veya `Set` yordamı. Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
-   `Default`  
  
     İsteğe bağlı. Bu özellik bir sınıf ya da yapı üzerinde tanımlandığı için varsayılan özelliği olduğunu belirtir. Varsayılan özellikleri parametreleri kabul etmeniz gerekir ve ayarlanabilir ve özellik adı belirtmeden alınır. Özellik olarak bildirirseniz `Default`, kullanamazsınız `Private` özelliği veya ya da kendi özellik yordamları.  
  
-   `accessmodifier`  
  
     İsteğe bağlı `Property` deyimi ve en fazla bir `Get` ve `Set` deyimleri. Aşağıdakilerden biri olabilir:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Protected Friend](../../language-reference/modifiers/protected-friend.md) 

    - [Private Protected](../../language-reference/modifiers/private-protected.md)
  
     Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `propertymodifiers`  
  
     İsteğe bağlı. Aşağıdakilerden biri olabilir:  
  
    -   [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     İsteğe bağlı. Bkz: [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     İsteğe bağlı. Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `ReadOnly`  
  
     İsteğe bağlı. Bkz: [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
-   `WriteOnly`  
  
     İsteğe bağlı. Bkz: [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   `Iterator`  
  
     İsteğe bağlı. Bkz: [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Gerekli. Özelliğin adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `parameterlist`  
  
     İsteğe bağlı. Bu özelliğin parametreleri ve olası ek parametrelerini temsil eden yerel değişken adlarının listesini `Set` yordamı. Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).  
  
-   `returntype`  
  
     Gerekli if `Option Strict` olduğu `On`. Bu özellik tarafından döndürülen değerin veri türü.  
  
-   `Implements`  
  
     İsteğe bağlı. Bu özellik bir veya daha fazla özellik, her biri bu özelliğin içeren sınıf veya yapı tarafından uygulanan bir arabirim içinde tanımlanmış uygulayan gösterir. Bkz: [uygulayan deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).  
  
-   `implementslist`  
  
     Gerekli if `Implements` sağlanır. Uygulanan özelliklerin listesi.  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     Her `implementedproperty` aşağıdaki söz dizimini ve bölümleri vardır:  
  
     `interface.definedname`  
  
    |Bölümü|Açıklama|  
    |---|---|  
    |`interface`|Gerekli. Bu özellik tarafından uygulanan arabirimin adını sınıf veya yapı içeren.|  
    |`definedname`|Gerekli. Ad tarafından özelliği tanımlanan `interface`.|  
  
-   `Get`  
  
     İsteğe bağlı. Özellik işaretlenmişse gerekli `WriteOnly`. Başlatan bir `Get` özelliğinin değeri döndürmek için kullanılan bir özellik yordamı.  
  
-   `statements`  
  
     İsteğe bağlı. İçinde çalıştırılacak deyimler bloğunu `Get` veya `Set` yordamı.  
  
-   `End Get`  
  
     Sonlandırır `Get` özellik yordamı.  
  
-   `Set`  
  
     İsteğe bağlı. Özellik işaretlenmişse gerekli `ReadOnly`. Başlatan bir `Set` özellik değerini depolamak için kullanılan bir özellik yordamı.  
  
-   `End Set`  
  
     Sonlandırır `Set` özellik yordamı.  
  
-   `End Property`  
  
     Bu özelliğin tanımını sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 `Property` Deyimi, özelliğin bildirimini sunar. Bir özelliğin sahip olabileceği bir `Get` yordamı (salt okunur), bir `Set` yordamı (salt okunur) veya her iki (okuma ve yazma). Atlayabilirsiniz `Get` ve `Set` otomatik uygulanan bir özellik kullanıldığında yordamı. Daha fazla bilgi için [Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
 Kullanabileceğiniz `Property` yalnızca sınıf düzeyinde. Başka bir deyişle *bildirim içeriğinin* bir özellik bir sınıf, yapı, modül veya arabirimi olması gerekir ve bir kaynak dosyası, ad alanı, yordam veya blok olamayacağı için. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Varsayılan olarak, genel erişim özelliklerini kullanın. Bir özelliğin erişim düzeyiyle bir erişim değiştiricisidir düzenleyebilirsiniz `Property` deyimi ve isteğe bağlı olarak ayarlayabilir, özellik yordamları daha kısıtlayıcı bir erişim düzeyi.  
  
 Visual Basic için bir parametre geçirir `Set` yordam sırasında özelliği atamaları. İçin bir parametre belirtmezseniz `Set`, tümleşik geliştirme ortamı (IDE) adlı bir örtük parametresini kullanan `value`. Bu parametre, özelliğe atanacak değer tutar. Genellikle bu değer özel bir yerel değişkene depolayın ve döndürün. her `Get` yordamı çağrılır.  
  
## <a name="rules"></a>Kurallar  
  
-   **Karışık erişim düzeyleri.** Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak farklı erişim düzeyi için belirtebilirsiniz `Get` veya `Set` yordamı, ancak ikisine birden değil. Bunu yaparsanız, yordam erişim düzeyi özellik erişim düzeyinden daha kısıtlayıcı olmalıdır. Örneğin, özellik bildirilirse `Friend`, bildirebilirsiniz `Set` yordamı `Private`, ama `Public`.  
  
     Tanımlıyorsanız, bir `ReadOnly` veya `WriteOnly` özelliği, tek bir özellik yordamı (`Get` veya `Set`sırasıyla) tüm özelliği temsil eder. İki erişim düzeyi özelliği ayarlamanız gerekir çünkü bu tür bir yordam için bir farklı erişim düzeyi bildiremezsiniz.  
  
-   **Dönüş türü.** `Property` Deyimi döndürdüğü değerin veri türü bildirebilirsiniz. Herhangi bir veri türü veya bir sabit listesi, yapısı, sınıf veya arabirim adını belirtebilirsiniz.  
  
     Siz belirtmezseniz `returntype`, özellik döndürür `Object`.  
  
-   **Uygulama.** Bu özellik kullanıyorsa `Implements` anahtar sözcüğü, kapsayan sınıf veya yapı olmalıdır bir `Implements` hemen deyimi, `Class` veya `Structure` deyimi. `Implements` Deyimi belirttiğiniz her arabirim içermelidir `implementslist`. Ancak, bir arabirim tarafından tanımlayan adı `Property` (içinde `definedname`) bu özelliğin adı ile aynı olması gerekmez (içinde `name`).  
  
## <a name="behavior"></a>Davranış  
  
-   **Bir özellik yordamı döndürüyor.** Zaman `Get` veya `Set` yordamı çağıran koda döndürür, kendisini çağıran deyiminin sonrasındaki deyime ile yürütme devam eder.  
  
     `Exit Property` Ve `Return` deyimleri neden hemen bir çıkış bir özellik yordamı. Herhangi bir sayıda `Exit Property` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Property` ve `Return` deyimleri.  
  
-   **Dönüş değeri.** Bir değer döndürmek için bir `Get` yordam, özellik adı için değer atamak veya olmasını bir `Return` deyimi. Aşağıdaki örnek, özellik adı için dönüş değeri atar `quoteForTheDay` ve ardından `Exit Property` döndürülecek deyimi.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     Kullanırsanız `Exit Property` değerine atama olmadan `name`, `Get` yordamı özelliğin veri türü için varsayılan değeri döndürür.  
  
     `Return` Deyimi aynı anda atar `Get` yordamı dönüş değeri ve yordamdan çıkar. Aşağıdaki örnekte bu gösterir.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sınıftaki bir özelliği bildirir.  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Otomatik Uygulanan Özellikler](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Get Deyimi](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set Deyimi](../../../visual-basic/language-reference/statements/set-statement.md)
- [Parametre Listesi](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Default](../../../visual-basic/language-reference/modifiers/default.md)
