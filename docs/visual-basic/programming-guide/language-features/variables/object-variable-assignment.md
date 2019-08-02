---
title: Nesne Değişkeni Ataması (Visual Basic)
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
ms.openlocfilehash: 59dea45511ba8d7d10c95cf17e47981124c532e4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631062"
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

`Nothing`Şu anda değişkene atanmış bir nesne olmadığı anlamına gelir.

## <a name="initialization"></a>Başlatma

Kodunuz çalışmaya başladığında, nesne değişkenleriniz olarak `Nothing`başlatılır. Bildirimleri başlatma dahil olanlar, bildirim deyimleri yürütüldüğünde belirttiğiniz değerlere yeniden başlatılır.

[Yeni](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğünü kullanarak bildirimindeki başlatmayı dahil edebilirsiniz. Aşağıdaki bildirim deyimleri, nesne değişkenlerini `testUri` `ver` bildirir ve bunlara belirli nesneler atar. Her biri, nesneyi başlatmak için uygun sınıfın aşırı yüklenmiş oluşturucularından birini kullanır.

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a>Disassociation tamamlayamadı

Bir nesne değişkenini, değişkenin `Nothing` ilişkilendirmesini belirli bir nesneyle devam ettirir şekilde ayarlama. Bu, değişkeni değiştirerek nesneyi yanlışlıkla değiştirmenizi önler. Ayrıca, aşağıdaki örnekte gösterildiği gibi, nesne değişkeninin geçerli bir nesneye işaret edilip edilmeyeceğini test etmenizi sağlar.

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

Değişkeninizin başvurduğu nesne başka bir uygulamada ise, bu test uygulamanın sonlandırılıp sonlandırılmadığını veya yalnızca geçersiz kılınmadığını belirleyemez.

Değerine `Nothing` sahip bir nesne değişkeni de *null başvuru*olarak adlandırılır.

## <a name="current-instance"></a>Geçerli örnek

Bir nesnenin *geçerli örneği* , kodun Şu anda yürütüldüğü bir nesnedir. Tüm kod bir yordam içinde yürütüldüğü için, geçerli örnek yordamın çağrıldığı bir nesnedir.

`Me` Anahtar sözcüğü, geçerli örneğe başvuran bir nesne değişkeni işlevi görür. Bir yordam paylaşılmışsa, [](../../../../visual-basic/language-reference/modifiers/shared.md)geçerli örneğe bir işaretçi almak için `Me` anahtar sözcüğünü kullanabilir. Paylaşılan yordamlar bir sınıfın belirli bir örneğiyle ilişkilendirilemez.

Kullanmak `Me` , özellikle geçerli örneği başka bir modüldeki yordama geçirmek için kullanışlıdır. Örneğin, bir dizi XML belgeniz olduğunu ve bunlara bazı standart metinler ekleneceğini varsayalım. Aşağıdaki örnek bunu yapmak için bir yordam tanımlar.

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
- [Nasıl yapılır: Bir nesne değişkeni bildirin ve Visual Basic bir nesne atayın](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Nasıl yapılır: Bir nesne değişkeninin herhangi bir örneğe başvurmadığından emin olun](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
