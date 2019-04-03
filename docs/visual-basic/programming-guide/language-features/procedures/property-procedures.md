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
ms.openlocfilehash: 47e93ee17f160ce5cd701fd0a12ec16b3997ce9b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828358"
---
# <a name="property-procedures-visual-basic"></a>Özellik Yordamları (Visual Basic)
Bir özellik yordamı bir özel özellik bir modül, sınıf veya yapı işleyen Visual Basic deyimleri bir dizisidir. Özellik yordamları olan olarak da bilinen *özellik erişimcileri*.  
  
 Visual Basic için aşağıdaki özellik yordamları sağlar:  
  
-   A `Get` yordamı bir özelliğinin değerini döndürür. Bir ifade özelliğinde eriştiğinde çağrılır.  
  
-   A `Set` yordamı bir özellik içeren bir nesne başvurusu bir değere ayarlar. Özellik için bir değer atadığınızda çağrılır.  
  
 Özellik yordamları kullanarak çiftlerinde genellikle tanımlamak `Get` ve `Set` deyimleri, ancak tanımlayabilirsiniz tek başına ya da yordam özellik salt okunur ise ([alma deyimi](../../../../visual-basic/language-reference/statements/get-statement.md)) veya salt yazılır ([ayarlayın Deyimi](../../../../visual-basic/language-reference/statements/set-statement.md)).  
  
 Atlayabilirsiniz `Get` ve `Set` otomatik uygulanan bir özellik kullanıldığında yordamı. Daha fazla bilgi için [Implemented Properties](./auto-implemented-properties.md).  
  
 Özellikler, sınıflar, yapılar ve modülleri tanımlayabilirsiniz. Özellikleri `Public` varsayılan olarak, yani çağırabilirsiniz bunları yerden uygulamanızdaki özelliğin kapsayıcı erişebilirsiniz.  
  
 Özellikler ve değişkenlerin bir karşılaştırması için bkz. [arasındaki farklar özelliklerini ve Visual Basic'te değişkenler](./differences-between-properties-and-variables.md).  
  
## <a name="declaration-syntax"></a>Bildirim Sözdizimi  
 İçine alınmış bir kod bloğunu tarafından tanımlanan bir özellik [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md) ve `End Property` deyimi. Bir bildirim deyiminin alınmış bir dahili bloğu olarak her bir özellik yordamı bu blok içinde görünür (`Get` veya `Set`) ile eşleşen `End` bildirimi.  
  
 Bir özellik ve işlemleri bildirmek için sözdizimi aşağıdaki gibidir:  
  
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
  
 `Modifiers` Erişim düzeyi ve aşırı yüklemesi, geçersiz kılma, paylaşımı ve Gölgeleme, ilgili bilgileri yanı sıra özelliğin salt okunur veya sadece yazılabilir olup belirtebilirsiniz. `AccessLevel` Üzerinde `Get` veya `Set` yordamı özelliği için belirtilen erişim düzeyi daha kısıtlayıcı olan herhangi bir düzeyinde olabilir. Daha fazla bilgi için [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md).  
  
### <a name="data-type"></a>Veri Türü  
 Bir özelliğin veri türü ve asıl erişim düzeyi tanımlanan `Property` deyimi, özellik yordamları içinde değil. Bir özellik, yalnızca bir veri türü olabilir. Örneğin, depolamak için bir özellik tanımlanamaz bir `Decimal` değer ancak almak bir `Double` değeri.  
  
### <a name="access-level"></a>Erişim düzeyi  
 Ancak, bir özellik için bir asıl erişim düzeylerini tanımlayın ve kendi özellik yordamları biriyle erişim düzeyi kısıtlamanız. Örneğin, tanımlayabileceğiniz bir `Public` özelliği ve tanımlayabilirsiniz bir `Private Set` yordamı. `Get` Yordamı kalır `Public`. Bir özelliğin yordamlar yalnızca birinde erişim düzeyini değiştirebilir ve yalnızca bunu asıl erişim düzeyi daha kısıtlayıcı bir duruma getirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme](./how-to-declare-a-property-with-mixed-access-levels.md).  
  
## <a name="parameter-declaration"></a>Parametre bildirimi  
 Her parametre için yaptığınız gibi bildirdiğiniz [alt yordamlar](./sub-procedures.md)geçirme mekanizması olmalı, dışında `ByVal`.  
  
 Parametre listesindeki her parametre için sözdizimi aşağıdaki gibidir:  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 Parametre isteğe bağlıysa, varsayılan değer bildiriminin bir parçası olarak da belirtmeniz gerekir. Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>Özellik Değeri  
 İçinde bir `Get` yordamı, dönüş değeri, çağıran ifadeye özelliğinin değeri olarak sağlanır.  
  
 İçinde bir `Set` yordamı, yeni özellik değeri için parametresi geçirilir `Set` deyimi. Bir parametre açıkça bildirirseniz özelliği olarak aynı veri türünde bildirmeniz gerekir. Bir parametre bildirmeyin, derleyici örtük parametresini kullanır. `Value` özelliğe atanacak yeni değeri gösterecek.  
  
## <a name="calling-syntax"></a>Arama söz dizimi  
 Bir özellik yordamı örtük olarak özelliğine başvuru yaparak çağırın. İsteğe bağlı olmayan tüm bağımsız değişkenler için değer sağlamanız gereken dışında aynı şekilde, bir değişken adını kullanırsınız özelliğin adını kullanın ve bağımsız değişken listesi parantez içine almalısınız. Hiçbir bağımsız değişken sağlanmadıysa, parantezler isteğe bağlı olarak atlayabilirsiniz.  
  
 Örtük çağrıyla sözdizimi bir `Set` yordam şu şekildedir:  
  
 `propertyname[(argumentlist)] = expression`  
  
 Örtük çağrıyla sözdizimi bir `Get` yordam şu şekildedir:  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı gösterimi  
 Aşağıdaki özelliği tam adı, iki bağlı ad, ad ve Soyadı depolar. Çağıran kod zaman okur `fullName`, `Get` yordam iki bağlı adları birleştirir ve tam adını döndürür. Çağıran kod yeni bir tam ad atarken `Set` yordamı iki bağlı adlarına sonu dener. Bir alan bulamazsa, tüm ad depolar.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 Aşağıdaki örnek özellik yordamları tipik çağrıları gösterir `fullName`.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [İşlev Yordamları](./function-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Visual Basic'de özellikler ile değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir özellik yordamı çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir özelliğe değer ekleme](./how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir özellikten değer alma](./how-to-get-a-value-from-a-property.md)
