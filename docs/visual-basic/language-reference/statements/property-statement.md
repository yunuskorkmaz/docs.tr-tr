---
title: Property Deyimi
ms.date: 07/20/2015
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
ms.openlocfilehash: 70738ecf739b8e50078903dc108fdc8f97d29636
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="property-statement"></a>Property Deyimi
Bir özellik ve depolamak ve özellik değerini almak için kullanılan özellik yordamları adını bildirir.  
  
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
  
     İsteğe bağlı. Bu özellik için geçerli öznitelikler listesi veya `Get` veya `Set` yordamı. Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
-   `Default`  
  
     İsteğe bağlı. Bu özellik varsayılan özelliği sınıf veya yapı tanımlı için olduğunu belirtir. Varsayılan Özellikler parametreleri kabul etmeniz gerekir ve ayarlanabilir ve özellik adı belirtmeden alınır. Özelliği olarak bildirirseniz `Default`, kullanamazsınız `Private` özelliği veya onun özellik yordamlardan birini.  
  
-   `accessmodifier`  
  
     İsteğe bağlı `Property` deyimi ve en fazla birinde `Get` ve `Set` deyimleri. Aşağıdakilerden biri olabilir:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
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
  
     İsteğe bağlı. Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `ReadOnly`  
  
     İsteğe bağlı. Bkz: [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
-   `WriteOnly`  
  
     İsteğe bağlı. Bkz: [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   `Iterator`  
  
     İsteğe bağlı. Bkz: [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Gerekli. Özelliğin adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `parameterlist`  
  
     İsteğe bağlı. Bu özellik parametrelerinin ve olası ek parametreleri temsil eden yerel değişken adları listesi `Set` yordamı. Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).  
  
-   `returntype`  
  
     Gerekli olursa `Option``Strict` olan `On`. Bu özellik tarafından döndürülen değerin veri türü.  
  
-   `Implements`  
  
     İsteğe bağlı. Bu özellik bir veya daha fazla özellikler, bu özelliğin içeren sınıf veya yapı tarafından uygulanan bir arabirim tanımlanan her biri uygulayan gösterir. Bkz: [uygulayan deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).  
  
-   `implementslist`  
  
     Gerekli olursa `Implements` sağlanır. Uygulanan özelliklerin listesi.  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     Her `implementedproperty` aşağıdaki söz dizimini ve bölümleri vardır:  
  
     `interface.definedname`  
  
    |Bölümü|Açıklama|  
    |---|---|  
    |`interface`|Gerekli. Bu özellik tarafından uygulanan bir arabirim adını sınıf veya yapı içeren.|  
    |`definedname`|Gerekli. Adı olarak özelliği tanımlanmış `interface`.|  
  
-   `Get`  
  
     İsteğe bağlı. Özellik işaretlenmişse gerekli `WriteOnly`. Başlayan bir `Get` özelliğinin değeri döndürmek için kullanılan özellik yordamı.  
  
-   `statements`  
  
     İsteğe bağlı. İçinde çalıştırmak için deyimleri bloğunu `Get` veya `Set` yordamı.  
  
-   `End Get`  
  
     Sonlandırır `Get` özellik yordamı.  
  
-   `Set`  
  
     İsteğe bağlı. Özellik işaretlenmişse gerekli `ReadOnly`. Başlayan bir `Set` özelliğinin değeri depolamak için kullanılan özellik yordamı.  
  
-   `End Set`  
  
     Sonlandırır `Set` özellik yordamı.  
  
-   `End Property`  
  
     Bu özellik tanımını sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 `Property` Deyimi bir özellik bildirimi tanıtır. Bir özelliğin sahip olabileceği bir `Get` (salt okunur), yordam bir `Set` yordamı (yalnızca yazma) veya her iki (okuma-yazma). Atlayabilirsiniz `Get` ve `Set` otomatik uygulanan özelliğini kullanırken yordamı. Daha fazla bilgi için bkz: [Auto-Implemented özellikleri](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
 Kullanabileceğiniz `Property` yalnızca sınıf düzeyinde. Yani *bildirimi bağlam* bir özelliği bir sınıf, yapısı, modül veya arabirim olmalı ve kaynak dosyasını, ad alanı, yordam veya blok olamaz. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Varsayılan olarak, genel erişim özelliklerini kullanın. Bir özelliğin erişim düzeyi bir erişim değiştiricisi ile ayarlayabilirsiniz `Property` deyimi ve isteğe bağlı olarak ayarlayabilir, özellik yordamları daha kısıtlayıcı bir erişim düzeyi için.  
  
 Visual Basic geçirir parametresi `Set` yordam sırasında özelliği atamaları. İçin bir parametre belirtmezseniz `Set`, tümleşik geliştirme ortamı (IDE) adlı bir örtük parametresini kullanır `value`. Bu parametre özelliğine atanan değer tutar. Genellikle bu değer bir özel yerel değişkende depolayın ve döndürün her `Get` yordamı çağrılır.  
  
## <a name="rules"></a>Kurallar  
  
-   **Karışık erişim düzeyleri.** Bir okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak farklı erişim düzeyi için ya da belirtebilirsiniz `Get` veya `Set` yordamı, ancak ikisini birden değil. Bunu yaparsanız, yordam erişim düzeyi özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir. Örneğin, özellik bildirilirse `Friend`, bildirebilirsiniz `Set` yordam `Private`, ama `Public`.  
  
     Tanımlıyorsanız, bir `ReadOnly` veya `WriteOnly` özelliği, tek bir özellik yordamı (`Get` veya `Set`sırasıyla) tüm özelliğinin temsil eder. Özelliği için iki erişim düzeyleri ayarlamanız gerekir çünkü bu tür bir yordam için farklı erişim düzeyi bildiremezsiniz.  
  
-   **Dönüş türü.** `Property` Deyimi döndürdüğü değerin veri türü bildirebilirsiniz. Herhangi bir veri türü veya bir numaralandırma, yapısı, sınıf veya arabirim adını belirtebilirsiniz.  
  
     Belirtmezseniz, `returntype`, özellik döndürür `Object`.  
  
-   **Uygulaması.** Bu özellik kullanıyorsa `Implements` anahtar sözcüğü, içeren sınıf veya yapı olmalıdır bir `Implements` hemen ardından deyimi kendi `Class` veya `Structure` deyimi. `Implements` Deyim, belirtilen her bir arabirime içermelidir `implementslist`. Ancak, bir arabirim tarafından tanımlayan ad `Property` (içinde `definedname`) bu özelliğin adı ile aynı olması gerekmez (içinde `name`).  
  
## <a name="behavior"></a>Davranış  
  
-   **Bir özellik yordamından döndürülüyor.** Zaman `Get` veya `Set` yordamı çağıran kodu döndürür, yürütme çağrılması deyiminden deyim ile devam eder.  
  
     `Exit Property` Ve `Return` deyimleri neden hemen bir çıkış bir özellik yordam. Herhangi bir sayıda `Exit Property` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Property` ve `Return` deyimleri.  
  
-   **Dönüş değeri.** Bir değer almak için bir `Get` yordamı, özellik adı değerini atayın veya olmasını bir `Return` deyimi. Aşağıdaki örnek, özellik adı dönüş değeri atar `quoteForTheDay` ve ardından `Exit Property` dönmek için deyimi.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     Kullanırsanız `Exit Property` değerine atama olmadan `name`, `Get` yordamı özelliğin veri türü için varsayılan değeri döndürür.  
  
     `Return` Deyimi aynı anda atar `Get` yordamı dönüş değeri ve yordamdan çıkar. Aşağıdaki örnekte bu gösterir.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir sınıftaki bir özelliği bildirir.  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Otomatik Uygulanan Özellikler](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Get Deyimi](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set Deyimi](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Parametre Listesi](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [Default](../../../visual-basic/language-reference/modifiers/default.md)
