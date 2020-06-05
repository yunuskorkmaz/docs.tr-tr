---
title: Özellik Yordamları
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
ms.openlocfilehash: cb5b0e12512e476b7c96bbfb19f8e4f470f6b498
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363739"
---
# <a name="property-procedures-visual-basic"></a>Özellik Yordamları (Visual Basic)

Özellik yordamı bir modül, sınıf veya yapıda özel bir özelliği düzenleyen Visual Basic deyimlerinin bir dizisidir. Özellik yordamları, *özellik erişimcileri*olarak da bilinir.

Visual Basic aşağıdaki özellik yordamları için sağlar:

- Bir `Get` yordam bir özelliğin değerini döndürür. Bir ifadede özelliğe eriştiğinizde çağrılır.
- Bir `Set` yordam, bir özelliği bir nesne başvurusu dahil olmak üzere bir değere ayarlar. Özelliğe bir değer atadığınızda çağrılır.

Genellikle özellik yordamlarını ve deyimlerini kullanarak çiftler halinde tanımlarsınız `Get` `Set` , ancak özellik salt okunurdur ([Get deyimi](../../../language-reference/statements/get-statement.md)) ya da salt yazılır ([küme deyimi](../../../language-reference/statements/set-statement.md)) ise tek başına yordamı tanımlayabilirsiniz.

`Get` `Set` Otomatik uygulanan bir özellik kullanırken ve yordamını atlayabilirsiniz. Daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](./auto-implemented-properties.md).

Sınıflar, yapılar ve modüllerde özellikler tanımlayabilirsiniz. Özellikler `Public` Varsayılan olarak, uygulamanın, özelliğin kapsayıcısına erişebilen uygulamanızdaki herhangi bir yerden çağırabileceği anlamına gelir.

Özelliklerin ve değişkenlerin karşılaştırması için [Visual Basic Özellikler ve değişkenler arasındaki farklılıklar](differences-between-properties-and-variables.md)bölümüne bakın.

## <a name="declaration-syntax"></a>Bildirim söz dizimi

Özelliğin kendisi, [özellik bildiriminde](../../../language-reference/statements/property-statement.md) ve ifadesiyle alınmış bir kod bloğu tarafından tanımlanır `End Property` . Bu bloğun içinde her özellik yordamı, bir bildirim bildirimi ( `Get` veya `Set` ) ve eşleşen bildirim içinde iç bir blok olarak görünür `End` .

Bir özelliği ve yordamlarını bildirmek için sözdizimi aşağıdaki gibidir:

```vb
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
' - or -
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]
```

, `Modifiers` Aşırı yükleme, geçersiz kılma, paylaşma ve gölgeleme ile ilgili erişim düzeyini ve bilgileri, özelliğin salt okunurdur mi yoksa salt yazılır mi olduğunu belirtebilir. `AccessLevel` `Get` Veya `Set` yordamı, özelliğin kendisi için belirtilen erişim düzeyinden daha kısıtlayıcı olan herhangi bir düzey olabilir. Daha fazla bilgi için bkz. [özellik açıklaması](../../../language-reference/statements/property-statement.md).

### <a name="data-type"></a>Veri Türü

Özelliğin veri türü ve asıl erişim düzeyi, `Property` özellik yordamlarında değil, bildiriminde tanımlanmıştır. Bir özellik yalnızca bir veri türüne sahip olabilir. Örneğin, bir değeri depolamak için bir özellik tanımlayamazsınız `Decimal` ancak bir `Double` değer alabilirsiniz.

### <a name="access-level"></a>Erişim düzeyi

Ancak, bir özellik için bir asıl erişim düzeyi tanımlayabilir ve özellik yordamlarından birinde erişim düzeyini daha da kısıtlayabilirsiniz. Örneğin, bir `Public` özellik tanımlayabilir ve ardından bir `Private Set` yordam tanımlayabilirsiniz. `Get`Yordam kalır `Public` . Erişim düzeyini bir özelliğin yordamlarından yalnızca birinde değiştirebilirsiniz ve yalnızca asıl erişim düzeyinden daha kısıtlayıcı hale getirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: karışık erişim düzeylerine sahip bir özellik bildirme](how-to-declare-a-property-with-mixed-access-levels.md).

## <a name="parameter-declaration"></a>Parametre bildirimi

Geçirilen mekanizmanın olması dışında, her parametreyi [alt yordamlar](sub-procedures.md)için yaptığınız gibi bildirirsiniz `ByVal` .

Parametre listesindeki her bir parametre için sözdizimi aşağıdaki gibidir:

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

Parametre isteğe bağlı ise, bildiriminin bir parçası olarak bir varsayılan değer de belirtmeniz gerekir. Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a>Özellik değeri

Bir `Get` yordamda, dönüş değeri, özelliğin değeri olarak çağırma ifadesine sağlanır.

Bir `Set` yordamda, yeni özellik değeri deyimin parametresine geçirilir `Set` . Açıkça bir parametre bildirirseniz, özelliği ile aynı veri türüyle bildirmeniz gerekir. Bir parametre bildirmezsiniz derleyici, `Value` özelliğe atanacak yeni değeri temsil etmek için örtük parametresini kullanır.

## <a name="calling-syntax"></a>Çağırma sözdizimi

Özelliğe başvuru yaparak bir özellik yordamını örtük olarak çağırılır. Özelliği, isteğe bağlı olmayan tüm bağımsız değişkenlerin değerlerini sağlamanız ve bağımsız değişken listesini parantez içine almanız gerekir, ancak, özelliğin adını bir değişkenin adını kullandığınız şekilde kullanırsınız. Herhangi bir bağımsız değişken sağlanmazsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.

Bir yordama örtük çağrının sözdizimi `Set` aşağıdaki gibidir:

```vb
propertyname[(argumentlist)] = expression
```

Bir yordama örtük çağrının sözdizimi `Get` aşağıdaki gibidir:

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı gösterimi

Aşağıdaki özellik, tam adı iki anayent adı, ad ve soyadı olarak depolar. Çağıran kod okuduğunda `fullName` , `Get` yordam iki anayent adı birleştirir ve tam adı döndürür. Çağıran kod yeni bir tam ad atarken, `Set` yordam onu iki anayada bölmek için çalışır. Bir boşluk bulamazsa, ilk ad olarak tümünü depolar.

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

Aşağıdaki örnek, öğesinin özellik yordamlarına yapılan tipik çağrıları gösterir `fullName` :

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](index.md)
- [İşlev Yordamları](function-procedures.md)
- [İşleç Yordamları](operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](procedure-parameters-and-arguments.md)
- [Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar](differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik Oluşturma](how-to-create-a-property.md)
- [Nasıl yapılır: Bir Özellik Yordamı Çağırma](how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma](how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özelliğe Değer Ekleme](how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir Özellikten Değer Alma](how-to-get-a-value-from-a-property.md)
