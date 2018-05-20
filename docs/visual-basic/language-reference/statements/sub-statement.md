---
title: Sub Deyimi (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: 08be38cdbec82914b567ab5b86eed71181efcf57
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="sub-statement-visual-basic"></a>Sub Deyimi (Visual Basic)
Ad, parametreleri ve tanımlama kodu bildiren bir `Sub` yordamı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Bölümler  
  
-   `attributelist`  
  
     İsteğe bağlı. Bkz: [öznitelik listesi](attribute-list.md).  
  
-   `Partial`  
  
     İsteğe bağlı. Kısmi bir yöntem tanımını gösterir. Bkz: [kısmi yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).  
  
-   `accessmodifier`  
  
     İsteğe bağlı. Aşağıdakilerden biri olabilir:  
  
    -   [Public](../modifiers/public.md)  
  
    -   [Protected](../modifiers/protected.md)  
  
    -   [Friend](../modifiers/friend.md)  
  
    -   [Private](../modifiers/private.md)  
  
    - [Korumalı Friend](../../language-reference/modifiers/protected-friend.md)

    - [Özel korumalı](../../language-reference/modifiers/private-protected.md)
  
     Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     İsteğe bağlı. Aşağıdakilerden biri olabilir:  
  
    -   [Overloads](../modifiers/overloads.md)  
  
    -   [Overrides](../modifiers/overrides.md)  
  
    -   [Overridable](../modifiers/overridable.md)  
  
    -   [NotOverridable](../modifiers/notoverridable.md)  
  
    -   [MustOverride](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     İsteğe bağlı. Bkz: [paylaşılan](../modifiers/shared.md).  
  
-   `Shadows`  
  
     İsteğe bağlı. Bkz: [gölgeleri](../modifiers/shadows.md).  
  
-   `Async`  
  
     İsteğe bağlı. Bkz: [zaman uyumsuz](../modifiers/async.md).  
  
-   `name`  
  
     Gerekli. Yordamın adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Bir sınıf için bir oluşturucu yordam oluşturmak için adını ayarlayın bir `Sub` yordamına `New` anahtar sözcüğü. Daha fazla bilgi için bkz: [nesne ömrü: nesneleri oluşturma ve Destroyed şeklini](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
-   `typeparamlist`  
  
     İsteğe bağlı. Tür parametreleri genel bir yordam listesi. Bkz: [yazın listesi](type-list.md).  
  
-   `parameterlist`  
  
     İsteğe bağlı. Bu yordam parametreleri temsil eden yerel değişken adları listesi. Bkz: [parametre listesi](parameter-list.md).  
  
-   `Implements`  
  
     İsteğe bağlı. Bu yordam bir veya daha fazla uyguladığını gösteren `Sub` yordamlar, bu yordamın içeren sınıf veya yapı tarafından uygulanan bir arabirim tanımlanan her biri. Bkz: [uygulayan deyimi](implements-statement.md).  
  
-   `implementslist`  
  
     Gerekli olursa `Implements` sağlanır. Listesi `Sub` uygulanan yordamlar.  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     Her `implementedprocedure` aşağıdaki söz dizimini ve bölümleri vardır:  
  
     `interface.definedname`  
  
    |Bölümü|Açıklama|  
    |---|---|  
    |`interface`|Gerekli. Bu yordam tarafından uygulanan bir arabirim adını sınıf veya yapı içeren.|  
    |`definedname`|Gerekli. Adı olarak yordamı tanımlanmış `interface`.|  
  
-   `Handles`  
  
     İsteğe bağlı. Bu yordam bir veya daha fazla belirli olayları işleyebilirsiniz gösterir. Bkz: [işleme](handles-clause.md).  
  
-   `eventlist`  
  
     Gerekli olursa `Handles` sağlanır. Bu yordamı işleme olayların listesi.  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     Her `eventspecifier` aşağıdaki söz dizimini ve bölümleri vardır:  
  
     `eventvariable.event`  
  
    |Bölümü|Açıklama|  
    |---|---|  
    |`eventvariable`|Gerekli. Nesne değişkeni sınıf veya olayı oluşturan yapı, veri türü ile bildirilmedi.|  
    |`event`|Gerekli. Bu yordamı işleme olayın adı.|  
  
-   `statements`  
  
     İsteğe bağlı. Bu yordam içinde çalıştırmak için deyimleri bloğu.  
  
-   `End Sub`  
  
     Bu yordamı tanımı sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm yürütülebilir kod yordam içinde olmalıdır. Kullanım bir `Sub` çağıran kodu için bir değer döndürmesi istemediğinizde yordamı. Kullanım bir `Function` bir değer döndürmek istediğinizde yordamı.  
  
## <a name="defining-a-sub-procedure"></a>Bir alt yordam tanımlama  
 Tanımlayabileceğiniz bir `Sub` yordamı yalnızca modülü düzeyinde. Bildirimi bağlam alt yordamı için bu nedenle, bir sınıf, bir yapı, bir modül veya bir arabirim olmalıdır ve kaynak dosyası, bir ad alanı, bir yordam veya bir blok olamaz. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).  
  
 `Sub` Genel erişim varsayılan yordamlar. Erişim değiştiricileri kullanarak bunların erişim düzeyleri ayarlayabilirsiniz.  
  
 Yordam kullanıyorsa `Implements` anahtar sözcüğü, içeren sınıf veya yapı olmalıdır bir `Implements` hemen izleyen deyimi kendi `Class` veya `Structure` deyimi. `Implements` Deyim, belirtilen her bir arabirime içermelidir `implementslist`. Ancak, bir arabirim tarafından tanımlayan ad `Sub` (içinde `definedname`) bu yordamı adıyla eşleşmesi gerekmez (içinde `name`).  
  
## <a name="returning-from-a-sub-procedure"></a>Bir alt yordam döndürme  
 Zaman bir `Sub` yordamı çağıran kodu döndürür, yürütme adlı deyiminden sonraki ile devam eder.  
  
 Aşağıdaki örnek, bir dönüş gösterir bir `Sub` yordamı.  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 `Exit Sub` Ve `Return` deyimleri neden bir hemen çıkın bir `Sub` yordamı. Herhangi bir sayıda `Exit Sub` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Sub` ve `Return` deyimleri.  
  
## <a name="calling-a-sub-procedure"></a>Alt yordamı çağırma  
 Çağırmanız bir `Sub` bir deyimde yordam adı kullanarak ve bu adı taşıyan kendi bağımsız değişken listesi parantez içinde aşağıdaki yordamı. Yalnızca herhangi bir bağımsız değişken belirlemezseniz parantez atlayabilirsiniz. Ancak, kodunuzun her zaman parantez eklerseniz, daha okunabilir durumdadır.  
  
 A `Sub` yordam ve `Function` yordamı parametrelere sahip ve bir dizi deyimi gerçekleştirin. Ancak, bir `Function` yordamı döndürür bir değer ve bir `Sub` yordam değil. Bu nedenle, kullanamazsınız bir `Sub` yordamda bir ifade.  
  
 Kullanabileceğiniz `Call` çağırdığınızda anahtar sözcüğü bir `Sub` yordamı, ancak bu anahtar sözcük birçok kullanım için önerilmez. Daha fazla bilgi için bkz: [Call deyimi](call-statement.md).  
  
 Visual Basic bazen iç verimliliğini artırmak için aritmetik ifadeler yeniden düzenler. Bağımsız değişken listesi diğer yordamlar çağrı ifadeler içeriyorsa, bu nedenle, belirli bir sırada bu ifadeler adlı olduğunu varsayalım döndürmemelidir.  
  
## <a name="async-sub-procedures"></a>Zaman uyumsuz alt yordamlar  
 Async özelliği kullanarak, açık geri aramalar kullanarak veya birden çok işlevleri veya lambda ifadeleri kodunuzu el ile bölme olmadan zaman uyumsuz işlevleri çağırabilir.  
  
 Bir yordam ile işaretlerseniz [zaman uyumsuz](../modifiers/async.md) kullanabileceğiniz değiştiricisi, [bekleme](../../../visual-basic/language-reference/operators/await-operator.md) yordamda işleci. Ulaştığında denetlemek bir `Await` ifadesinde `Async` yordam, Denetim çağırana döndürür ve awaited görevi tamamlanana kadar yordamı ediyor askıya alındı. Görev tamamlandığında yürütme yordamda devam edebilirsiniz.  
  
> [!NOTE]
>  Bir `Async` yordamı döndürür henüz tamamlanmadı ya da ilk awaited nesne karşılaşıldığında çağıran ya da sonunda `Async` yordamı ulaşıldığında, hangisi daha önce gerçekleşir.  
  
 Ayrıca işaretleyebilirsiniz bir [Function deyimi](function-statement.md) ile `Async` değiştiricisi. Bir `Async` işlevi dönüş türüne sahip <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task>. Bu konuda gösterilmektedir örnek daha sonra da bir `Async` dönüş türüne sahip işlevi <xref:System.Threading.Tasks.Task%601>.  
  
 `Async` `Sub` yordamlar, burada bir değer döndürülemiyor olay işleyicileri için öncelikle kullanılır. Bir `Async``Sub` yordamı beklemenin olamaz ve çağıran bir `Async``Sub` yordamı catch özel durumları olamaz, `Sub` yordamı atar.  
  
 Bir `Async` yordam herhangi bildiremez [ByRef](../modifiers/byref.md) parametreleri.  
  
 Hakkında daha fazla bilgi için `Async` yordamlar, bkz: [uyumsuz ve bekleme ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md), [akış denetimi zaman uyumsuz programlarda](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), ve [zaman uyumsuz dönüş türleri](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Sub` ad, parametreleri ve gövdesini kodu tanımlamak için deyimi bir `Sub` yordamı.  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `DelayAsync` olan bir `Async``Function` dönüş türüne sahip <xref:System.Threading.Tasks.Task%601>. `DelayAsync` sahip bir `Return` deyimi bir tamsayı döndürür. Bu nedenle, işlevi bildirimi `DelayAsync` dönüş türüne sahip olmalıdır `Task(Of Integer)`. Dönüş türü olduğundan `Task(Of Integer)`, değerlendirmesi `Await` ifadesinde `DoSomethingAsync` aşağıdaki deyimi gösterildiği gibi bir tamsayı üretir: `Dim result As Integer = Await delayTask`.  
  
 `startButton_Click` Yordamdır örneği bir `Async Sub` yordamı. Çünkü `DoSomethingAsync` olan bir `Async` işlevi, görev çağrısı için `DoSomethingAsync` , aşağıdaki deyimi gösterildiği beklemenin gerekir: `Await DoSomethingAsync()`. `startButton_Click``Sub` Yordamı tanımlı, ile `Async` değiştiricisi içerdiğinden bir `Await` ifade.  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Implements Deyimi](implements-statement.md)  
 [Function Deyimi](function-statement.md)  
 [Parametre Listesi](parameter-list.md)  
 [Dim Deyimi](dim-statement.md)  
 [Call Deyimi](call-statement.md)  
 [,](of-clause.md)  
 [Parametre Dizileri](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Yordam Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [Kısmi Yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
