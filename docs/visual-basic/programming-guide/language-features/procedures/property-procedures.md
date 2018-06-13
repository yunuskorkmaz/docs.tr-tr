---
title: Özellik Yordamları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: a0a73494c3573973d88823a7b5a5a83d2672e7d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656093"
---
# <a name="property-procedures-visual-basic"></a>Özellik Yordamları (Visual Basic)
Bir özellik yordamı bir özel özellik modülü, sınıf veya yapı işlemek Visual Basic deyimleri dizisidir. Özellik yordamları olan olarak da bilinen *özellik erişimcisi*.  
  
 Visual Basic için aşağıdaki özellik yordamları sağlar:  
  
-   A `Get` yordamı bir özelliğin değerini döndürür. Bir ifade özelliğinde eriştiğinizde çağrılır.  
  
-   A `Set` yordamı bir nesne başvurusu dahil olmak üzere bir değer için bir özellik ayarlar. Özelliği için bir değer atadığınızda çağrılır.  
  
 Özellik yordamları kullanarak çiftler halinde genellikle tanımlamak `Get` ve `Set` deyimleri, ancak tanımlayabilirsiniz tek başına ya da yordamı özelliği salt okunur ise ([Get deyimi](../../../../visual-basic/language-reference/statements/get-statement.md)) veya salt yazılır ([ayarlayın Deyimi](../../../../visual-basic/language-reference/statements/set-statement.md)).  
  
 Atlayabilirsiniz `Get` ve `Set` otomatik uygulanan özelliğini kullanırken yordamı. Daha fazla bilgi için bkz: [Auto-Implemented özellikleri](./auto-implemented-properties.md).  
  
 Özellikler, sınıflar, yapılar ve modülleri tanımlayabilirsiniz. Özellikleri `Public` varsayılan olarak, yani çağırabilirsiniz bunları yerden uygulamanızda özelliğin kapsayıcı erişebilirsiniz.  
  
 Özellikler ve değişkenler karşılaştırması için bkz: [özellikleri arasındaki farklar ve Visual Basic değişken](./differences-between-properties-and-variables.md).  
  
## <a name="declaration-syntax"></a>Bildirim Sözdizimi  
 Bir özellik içine alınmış kod bloğunu tarafından tanımlanan [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md) ve `End Property` deyimi. Bu bloğunun içine bildirimi deyimi içinde çevrelenmiş bir iç bloğu olarak her bir özellik yordam görünür (`Get` veya `Set`) ve eşleşen `End` bildirimi.  
  
 Bir özellik ve onun yordamları bildirme söz dizimi aşağıdaki gibidir:  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 `Modifiers` Erişim düzeyini ve aşırı yüklemesi, geçersiz kılma, paylaşımı ve Gölgeleme, ilgili bilgileri yanı sıra özelliği salt okunur veya sadece yazılabilir olup belirtebilirsiniz. `AccessLevel` Üzerinde `Get` veya `Set` yordamı özelliği için belirtilen erişim düzeyini daha kısıtlayıcı olan herhangi bir düzeye olabilir. Daha fazla bilgi için bkz: [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md).  
  
### <a name="data-type"></a>Veri Türü  
 Bir özelliğin veri türüne ve asıl erişim düzeyi tanımlanır `Property` özelliği yordamlardaki deyimi. Bir özelliği yalnızca bir veri türüne sahip olabilir. Örneğin, depolamak için bir özellik tanımlanamaz bir `Decimal` değer ancak almak bir `Double` değeri.  
  
### <a name="access-level"></a>Erişim düzeyi  
 Ancak, bir özellik için bir asıl erişim düzeylerini tanımlayın ve daha fazla özellik yordamları birinde erişim düzeyi kısıtlayın. Örneğin, tanımlayabilirsiniz bir `Public` özelliği ve ardından tanımlayan bir `Private Set` yordamı. `Get` Yordamı kalır `Public`. Bir özelliğin yordamlar yalnızca birinde erişim düzeyini değiştirebilirsiniz ve yalnızca bunu asıl erişim düzeyini daha kısıtlayıcı bir duruma getirebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: bir özelliği karışık erişim düzeyleriyle bildirme](./how-to-declare-a-property-with-mixed-access-levels.md).  
  
## <a name="parameter-declaration"></a>Parametre bildirimi  
 Her bir parametreyi yapmak için aynı şekilde bildirme [alt yordamlar](./sub-procedures.md)geçirme mekanizması olmalı, dışında `ByVal`.  
  
 Parametre listesindeki her parametre için söz dizimi aşağıdaki gibidir:  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 Parametre isteğe bağlı ise, varsayılan değer bildiriminden bir parçası olarak sağlamanız gerekir. Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>Özellik Değeri  
 İçinde bir `Get` yordamı, dönüş değeri arama ifade özelliğinin değeri olarak sağlanan.  
  
 İçinde bir `Set` yordamı, yeni özellik değeri için parametresinin geçirilir `Set` deyimi. Bir parametre açıkça bildirirseniz özelliği olarak aynı veri türüne sahip bildirmeniz gerekir. Bir parametre bildirmeyin, derleyici örtük parametre kullanıyorsa `Value` özelliğine atanacak yeni değer temsil etmek için.  
  
## <a name="calling-syntax"></a>Arama sözdizimi  
 Bir özellik yordamı örtük olarak özellik referansı yaparak çağırır. Bağımsız değişken listesi parantez içine alın ve isteğe bağlı olmayan tüm bağımsız değişkenler için değer sağlamalısınız dışında bir değişken adını kullanacağınız aynı şekilde özelliğinin adını kullanın. Bağımsız değişkenler sağlandıysa, isteğe bağlı olarak parantez atlayabilirsiniz.  
  
 Örtük bir çağrı sözdizimi bir `Set` yordam aşağıdaki gibidir:  
  
 `propertyname[(argumentlist)] = expression`  
  
 Örtük bir çağrı sözdizimi bir `Get` yordam aşağıdaki gibidir:  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı çizimi  
 Aşağıdaki özellikler, iki bağlı adları, ad ve Soyadı bir tam ad depolar. Ne zaman çağıran kodu okur `fullName`, `Get` yordamı iki bağlı adları birleştirir ve tam adını döndürür. Çağrıyı yapan kod yeni bir tam ad atarken `Set` yordamı iki bağlı adlarına bölün dener. Bir alan bulamazsa, tüm ad depolar.  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 Aşağıdaki örnek özellik yordamları tipik çağrı gösterilir `fullName`.  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [İşlev Yordamları](./function-procedures.md)  
 [İşleç Yordamları](./operator-procedures.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Visual Basic'de özellikler ve değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)  
 [Nasıl yapılır: Özellik Oluşturma](./how-to-create-a-property.md)  
 [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)  
 [Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)  
 [Nasıl yapılır: Bir Özelliğe Değer Ekleme](./how-to-put-a-value-in-a-property.md)  
 [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)
