---
title: Nesne Değişkeni Ataması
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: 93de17490935d6d5cad01000e9ee3e2fe55bd16c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351826"
---
# <a name="object-variable-assignment-visual-basic"></a>Nesne Değişkeni Ataması (Visual Basic)

Bir nesne değişkenine bir nesne atamak için normal atama ifadesini kullanırsınız. Aşağıdaki örnekte gösterildiği gibi bir nesne ifadesi veya [Nothing](../../../../visual-basic/language-reference/nothing.md) anahtar sözcüğü atayabilirsiniz.

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

`Nothing`, şu anda değişkene atanmış bir nesne olmadığı anlamına gelir.

## <a name="initialization"></a>Başlatma

Kodunuz çalışmaya başladığında, nesne değişkenleriniz `Nothing`olarak başlatılır. Bildirimleri başlatma dahil olanlar, bildirim deyimleri yürütüldüğünde belirttiğiniz değerlere yeniden başlatılır.

[Yeni](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğünü kullanarak bildirimindeki başlatmayı dahil edebilirsiniz. Aşağıdaki bildirim deyimleri, nesne değişkenlerini `testUri` ve `ver` ve bunlara belirli nesneleri atar. Her biri, nesneyi başlatmak için uygun sınıfın aşırı yüklenmiş oluşturucularından birini kullanır.

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a>Disassociation tamamlayamadı

Bir nesne değişkeninin `Nothing` olarak ayarlanması, değişkenin ilişkilendirmesini belirli bir nesneyle devam ettirir. Bu, değişkeni değiştirerek nesneyi yanlışlıkla değiştirmenizi önler. Ayrıca, aşağıdaki örnekte gösterildiği gibi, nesne değişkeninin geçerli bir nesneye işaret edilip edilmeyeceğini test etmenizi sağlar.

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

Değişkeninizin başvurduğu nesne başka bir uygulamada ise, bu test uygulamanın sonlandırılıp sonlandırılmadığını veya yalnızca geçersiz kılınmadığını belirleyemez.

`Nothing` değerine sahip bir nesne değişkenine de *null başvuru*denir.

## <a name="current-instance"></a>Geçerli örnek

Bir nesnenin *geçerli örneği* , kodun Şu anda yürütüldüğü bir nesnedir. Tüm kod bir yordam içinde yürütüldüğü için, geçerli örnek yordamın çağrıldığı bir nesnedir.

`Me` anahtar sözcüğü, geçerli örneğe başvuran bir nesne değişkeni işlevi görür. Bir yordam [paylaşılmışsa](../../../../visual-basic/language-reference/modifiers/shared.md), geçerli örneğe bir işaretçi almak için `Me` anahtar sözcüğünü kullanabilir. Paylaşılan yordamlar bir sınıfın belirli bir örneğiyle ilişkilendirilemez.

`Me` kullanmak, geçerli örneği başka bir modüldeki bir yordama geçirmek için özellikle yararlıdır. Örneğin, bir dizi XML belgeniz olduğunu ve bunlara bazı standart metinler ekleneceğini varsayalım. Aşağıdaki örnek bunu yapmak için bir yordam tanımlar.

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

Her XML belge nesnesi, yordamı çağırabilir ve geçerli örneğini bir bağımsız değişken olarak geçirebilir. Aşağıdaki örnek bunu gösterir.

```vb
addStandardText(Me)
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Nasıl yapılır: Visual Basic içinde bir nesne değişkeni bildirme ve bir nesne atama](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Nasıl yapılır: Bir Nesne Değişkeninin Bir Örneğine Başvurmamasını Sağlama](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
