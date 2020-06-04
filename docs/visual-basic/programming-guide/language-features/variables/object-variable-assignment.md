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
ms.openlocfilehash: 9ae1a307e8c886166d516140b7f100a411cedcfa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410380"
---
# <a name="object-variable-assignment-visual-basic"></a>Nesne Değişkeni Ataması (Visual Basic)

Bir nesne değişkenine bir nesne atamak için normal atama ifadesini kullanırsınız. Aşağıdaki örnekte gösterildiği gibi bir nesne ifadesi veya [Nothing](../../../language-reference/nothing.md) anahtar sözcüğü atayabilirsiniz.

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

`Nothing`Şu anda değişkene atanmış bir nesne olmadığı anlamına gelir.

## <a name="initialization"></a>Başlatma

Kodunuz çalışmaya başladığında, nesne değişkenleriniz olarak başlatılır `Nothing` . Bildirimleri başlatma dahil olanlar, bildirim deyimleri yürütüldüğünde belirttiğiniz değerlere yeniden başlatılır.

[Yeni](../../../language-reference/operators/new-operator.md) anahtar sözcüğünü kullanarak bildirimindeki başlatmayı dahil edebilirsiniz. Aşağıdaki bildirim deyimleri, nesne değişkenlerini bildirir `testUri` ve `ver` bunlara belirli nesneler atar. Her biri, nesneyi başlatmak için uygun sınıfın aşırı yüklenmiş oluşturucularından birini kullanır.

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a>Disassociation tamamlayamadı

Bir nesne değişkenini `Nothing` , değişkenin ilişkilendirmesini belirli bir nesneyle devam ettirir şekilde ayarlama. Bu, değişkeni değiştirerek nesneyi yanlışlıkla değiştirmenizi önler. Ayrıca, aşağıdaki örnekte gösterildiği gibi, nesne değişkeninin geçerli bir nesneye işaret edilip edilmeyeceğini test etmenizi sağlar.

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

Değişkeninizin başvurduğu nesne başka bir uygulamada ise, bu test uygulamanın sonlandırılıp sonlandırılmadığını veya yalnızca geçersiz kılınmadığını belirleyemez.

Değerine sahip bir nesne değişkeni `Nothing` de *null başvuru*olarak adlandırılır.

## <a name="current-instance"></a>Geçerli örnek

Bir nesnenin *geçerli örneği* , kodun Şu anda yürütüldüğü bir nesnedir. Tüm kod bir yordam içinde yürütüldüğü için, geçerli örnek yordamın çağrıldığı bir nesnedir.

`Me`Anahtar sözcüğü, geçerli örneğe başvuran bir nesne değişkeni işlevi görür. Bir yordam [paylaşılmışsa](../../../language-reference/modifiers/shared.md), `Me` geçerli örneğe bir işaretçi almak için anahtar sözcüğünü kullanabilir. Paylaşılan yordamlar bir sınıfın belirli bir örneğiyle ilişkilendirilemez.

Kullanmak, `Me` özellikle geçerli örneği başka bir modüldeki yordama geçirmek için kullanışlıdır. Örneğin, bir dizi XML belgeniz olduğunu ve bunlara bazı standart metinler ekleneceğini varsayalım. Aşağıdaki örnek bunu yapmak için bir yordam tanımlar.

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

- [Nesne Değişkenleri](object-variables.md)
- [Nesne Değişken Bildirimi](object-variable-declaration.md)
- [Nesne Değişkeni Değerleri](object-variable-values.md)
- [Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Nasıl yapılır: Bir Nesne Değişkeninin Bir Örneğine Başvurmamasını Sağlama](how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [Me, My, MyBase ve MyClass](../../program-structure/me-my-mybase-and-myclass.md)
