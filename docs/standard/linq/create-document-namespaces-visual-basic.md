---
title: Visual Basic LINQ to XML ad alanları içeren bir belge oluşturma
description: Ön ek içeren varsayılan ad alanları veya ad alanları içeren belgeler oluşturmak için Visual Basic XML sabit değerlerini kullanın.
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 48e2a1abf8f7a82df3db5cb2f580804d67776b15
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553509"
---
# <a name="how-to-create-a-document-with-namespaces-in-visual-basic-linq-to-xml"></a>Visual Basic ad alanları içeren bir belge oluşturma (LINQ to XML)

Bu makalede, Visual Basic ad alanları içeren bir belge oluşturma gösterilmektedir.

Visual Basic XML değişmez değerleri kullanılırken, kullanıcılar bir genel varsayılan XML ad alanı tanımlayabilir. Bu ad alanı, XML değişmez değerleri ve XML özellikleri için varsayılan ad alanıdır. Varsayılan XML ad alanı, proje düzeyinde ya da dosya düzeyinde tanımlanabilir. Dosya düzeyinde tanımlıysa, proje düzeyinde varsayılan ad alanını geçersiz kılar.

Diğer ad alanlarını da tanımlayabilir ve bu ad alanları için ad alanı öneklerini belirtebilirsiniz. `Imports`Her iki ad alanı türünü tanımlamak için anahtar sözcüğünü kullanırsınız.

Daha fazla bilgi için bkz. [Visual Basic xml sabit değerleri](xml-literals.md).

Varsayılan XML ad alanının yalnızca öğeler için geçerli olduğunu ve öznitelikler için geçerli olduğunu unutmayın. Varsayılan ad alanındaki öznitelikler varsayılan olarak ayarlanır. Ancak, bir ad alanına bir özniteliği yerleştirmek için bir ad alanı öneki kullanabilirsiniz.

## <a name="example-create-a-document-that-has-a-namespace"></a>Örnek: ad alanı bulunan bir belge oluşturma

Bu örnek, bir ad alanı içeren bir belge oluşturur.

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child aw:Att="attvalue"/>
            </aw:Root>
        Console.WriteLine(root)
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child aw:Att="attvalue" />
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a>Örnek: biri öneki olan iki ad alanı olan bir belge oluşturun

Bu örnekte iki ad alanı içeren bir belge oluşturulur. Biri varsayılan ad alanıdır, diğeri bir ön eke sahiptir.

```vb
Imports <xmlns="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child Att="attvalue"/>
                <fc:Child2>child2 content</fc:Child2>
            </Root>
        Console.WriteLine(root)
    End Sub

End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">
  <Child Att="attvalue" />
  <fc:Child2>child2 content</fc:Child2>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a>Örnek: iki ad alanı olan, her ikisi de önekle bir belge oluşturun

Aşağıdaki örnek, ad alanı önekleri olan iki ad alanını içeren bir belge oluşturur.

Bir XML ağacını serileştirilirken, LINQ to XML her bir öğenin belirlenen ad alanında olması için ad alanı bildirimleri gerektiği gibi yayar.

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <fc:Child>
                    <aw:DifferentChild>other content</aw:DifferentChild>
                </fc:Child>
                <aw:Child2>c2 content</aw:Child2>
                <fc:Child3>c3 content</fc:Child3>
            </aw:Root>
        Console.WriteLine(root)
    End Sub

End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ad alanlarına genel bakış](namespaces-overview.md)
