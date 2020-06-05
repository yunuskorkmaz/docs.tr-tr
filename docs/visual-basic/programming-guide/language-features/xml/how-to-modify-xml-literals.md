---
title: 'Nasıl yapılır: XML Değişmez Değerlerini Değiştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: a2ac2e9802d4c8ab522bb430d15cce5616430437
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374907"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="46e38-102">Nasıl yapılır: XML Değişmez Değerlerini Değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46e38-102">How to: Modify XML Literals (Visual Basic)</span></span>

<span data-ttu-id="46e38-103">Visual Basic, XML değişmez değerlerini değiştirmek için kullanışlı yollar sağlar.</span><span class="sxs-lookup"><span data-stu-id="46e38-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="46e38-104">Öğeleri ve öznitelikleri ekleyebilir ya da silebilirsiniz ve ayrıca var olan bir öğeyi yeni bir XML öğesiyle değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="46e38-105">Bu konuda, var olan bir XML sabit değerinin nasıl değiştirileceği hakkında birkaç örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="46e38-105">This topic provides several examples of how to modify an existing XML literal.</span></span>

### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="46e38-106">Bir XML sabit değerinin değerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="46e38-106">To modify the value of an XML literal</span></span>

1. <span data-ttu-id="46e38-107">Bir XML sabit değerinin değerini değiştirmek için, XML değişmez değerine bir başvuru alın ve `Value` Özelliği istenen değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="46e38-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>

    <span data-ttu-id="46e38-108">Aşağıdaki kod örneği \<Price> BIR XML belgesindeki tüm öğelerin değerini günceller.</span><span class="sxs-lookup"><span data-stu-id="46e38-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    <span data-ttu-id="46e38-109">Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46e38-109">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="46e38-110">Kaynak XML:</span><span class="sxs-lookup"><span data-stu-id="46e38-110">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="46e38-111">Değiştirilen XML:</span><span class="sxs-lookup"><span data-stu-id="46e38-111">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>47.20</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>48.25</Price>
      </Book>
    </Catalog>
    ```

    > [!NOTE]
    > <span data-ttu-id="46e38-112">`Value`Özelliği, bir koleksiyondaki Ilk XML öğesine başvurur.</span><span class="sxs-lookup"><span data-stu-id="46e38-112">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="46e38-113">Koleksiyonda aynı ada sahip birden fazla öğe varsa, `Value` özelliğin ayarlanması yalnızca koleksiyondaki ilk öğeyi etkiler.</span><span class="sxs-lookup"><span data-stu-id="46e38-113">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>

### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="46e38-114">Bir XML sabit değerine öznitelik eklemek için</span><span class="sxs-lookup"><span data-stu-id="46e38-114">To add an attribute to an XML literal</span></span>

1. <span data-ttu-id="46e38-115">Bir XML sabit değerine bir öznitelik eklemek için, önce XML değişmez değerine bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="46e38-115">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="46e38-116">Daha sonra yeni bir XML özniteliği eksen özelliği ekleyerek bir öznitelik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-116">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="46e38-117">Ayrıca <xref:System.Xml.Linq.XAttribute> , yöntemini kullanarak XML sabit değerine yeni bir nesne ekleyebilirsiniz <xref:System.Xml.Linq.XContainer.Add%2A> .</span><span class="sxs-lookup"><span data-stu-id="46e38-117">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="46e38-118">Aşağıdaki örnekte her iki seçenek de gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46e38-118">The following example shows both options.</span></span>

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    <span data-ttu-id="46e38-119">Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46e38-119">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="46e38-120">Kaynak XML:</span><span class="sxs-lookup"><span data-stu-id="46e38-120">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="46e38-121">Değiştirilen XML:</span><span class="sxs-lookup"><span data-stu-id="46e38-121">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="46e38-122">XML özniteliği eksen özellikleri hakkında daha fazla bilgi için bkz. [XML özniteliği eksen özelliği](../../../language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="46e38-122">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>

### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="46e38-123">Bir XML sabit değerine öğe eklemek için</span><span class="sxs-lookup"><span data-stu-id="46e38-123">To add an element to an XML literal</span></span>

1. <span data-ttu-id="46e38-124">Bir XML sabit değerine öğe eklemek için, önce XML değişmez değerine bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="46e38-124">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="46e38-125">Daha sonra <xref:System.Xml.Linq.XElement> yöntemini kullanarak, öğesinin son alt öğesi olarak yeni bir nesne ekleyebilirsiniz <xref:System.Xml.Linq.XContainer.Add%2A> .</span><span class="sxs-lookup"><span data-stu-id="46e38-125">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="46e38-126"><xref:System.Xml.Linq.XElement>Yöntemini kullanarak ilk alt öğe olarak yeni bir nesne ekleyebilirsiniz <xref:System.Xml.Linq.XContainer.AddFirst%2A> .</span><span class="sxs-lookup"><span data-stu-id="46e38-126">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>

    <span data-ttu-id="46e38-127">Belirli bir konuma diğer alt öğelere göre yeni bir öğe eklemek için, önce bitişik bir alt öğeye bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="46e38-127">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="46e38-128">Sonra <xref:System.Xml.Linq.XElement> , yöntemini kullanarak komşu alt öğeden önce yeni nesneyi ekleyebilirsiniz <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> .</span><span class="sxs-lookup"><span data-stu-id="46e38-128">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="46e38-129">Ayrıca <xref:System.Xml.Linq.XElement> , yöntemini kullanarak komşu alt öğeden sonra yeni nesneyi ekleyebilirsiniz <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> .</span><span class="sxs-lookup"><span data-stu-id="46e38-129">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>

    <span data-ttu-id="46e38-130">Aşağıdaki örnek, bu tekniklerin her birinin örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="46e38-130">The following example shows examples of each of these techniques.</span></span>

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    <span data-ttu-id="46e38-131">Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46e38-131">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="46e38-132">Kaynak XML:</span><span class="sxs-lookup"><span data-stu-id="46e38-132">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="46e38-133">Değiştirilen XML:</span><span class="sxs-lookup"><span data-stu-id="46e38-133">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331">
        <Publisher>Microsoft Press</Publisher>
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <PublishDate>2005-2-14</PublishDate>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="46e38-134">Bir XML sabit değerinden öğe veya öznitelik kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="46e38-134">To remove an element or attribute from an XML literal</span></span>

1. <span data-ttu-id="46e38-135">Bir öğeyi veya özniteliği bir XML sabit değerinden kaldırmak için, aşağıdaki örnekte gösterildiği gibi, öğe veya özniteliğe bir başvuru alın ve `Remove` yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="46e38-135">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    <span data-ttu-id="46e38-136">Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46e38-136">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="46e38-137">Kaynak XML:</span><span class="sxs-lookup"><span data-stu-id="46e38-137">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

    <span data-ttu-id="46e38-138">Değiştirilen XML:</span><span class="sxs-lookup"><span data-stu-id="46e38-138">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book></Catalog>
    ```

    <span data-ttu-id="46e38-139">Tüm öğeleri veya öznitelikleri bir XML sabit değerinden kaldırmak için, XML değişmez değerine bir başvuru alın ve <xref:System.Xml.Linq.XElement.RemoveAll%2A> yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="46e38-139">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>

### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="46e38-140">Bir XML sabit değerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="46e38-140">To modify an XML literal</span></span>

1. <span data-ttu-id="46e38-141">Bir XML öğesinin adını değiştirmek için öncelikle öğesine bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="46e38-141">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="46e38-142">Daha sonra <xref:System.Xml.Linq.XElement> Yeni bir ada sahip yeni bir nesne oluşturabilir ve yeni <xref:System.Xml.Linq.XElement> nesneyi <xref:System.Xml.Linq.XNode.ReplaceWith%2A> var olan nesnenin yöntemine geçirebilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="46e38-142">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>

    <span data-ttu-id="46e38-143">Değiştirdiğiniz öğenin korunması gereken alt öğeleri varsa, yeni <xref:System.Xml.Linq.XElement> nesnenin değerini <xref:System.Xml.Linq.XContainer.Nodes%2A> varolan öğenin özelliğine ayarlayın...</span><span class="sxs-lookup"><span data-stu-id="46e38-143">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="46e38-144">Bu, yeni öğenin değerini varolan öğenin iç XML değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="46e38-144">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="46e38-145">Aksi takdirde, yeni öğenin değerini `Value` varolan öğenin özelliğine ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-145">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>

    <span data-ttu-id="46e38-146">Aşağıdaki kod örneği \<Description> bir öğesi olan tüm öğeleri değiştirir \<Abstract> .</span><span class="sxs-lookup"><span data-stu-id="46e38-146">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="46e38-147">Öğesinin içeriği, \<Description> \<Abstract> nesnesinin özelliği kullanılarak yeni öğesinde korunur <xref:System.Xml.Linq.XContainer.Nodes%2A> \<Description> <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="46e38-147">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    <span data-ttu-id="46e38-148">Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46e38-148">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="46e38-149">Kaynak XML:</span><span class="sxs-lookup"><span data-stu-id="46e38-149">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
        <Description>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Description>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <Description>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Description>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="46e38-150">Değiştirilen XML:</span><span class="sxs-lookup"><span data-stu-id="46e38-150">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <MSRP>44.95</MSRP>    <Abstract>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Abstract>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <MSRP>45.95</MSRP>    <Abstract>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Abstract>
      </Book>
    </Catalog>
    ```

## <a name="see-also"></a><span data-ttu-id="46e38-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46e38-151">See also</span></span>

- [<span data-ttu-id="46e38-152">Visual Basic'de XML'i Düzenleme</span><span class="sxs-lookup"><span data-stu-id="46e38-152">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
- [<span data-ttu-id="46e38-153">XML</span><span class="sxs-lookup"><span data-stu-id="46e38-153">XML</span></span>](index.md)
- [<span data-ttu-id="46e38-154">Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme</span><span class="sxs-lookup"><span data-stu-id="46e38-154">How to: Load XML from a File, String, or Stream</span></span>](how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="46e38-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="46e38-155">LINQ</span></span>](../linq/index.md)
- [<span data-ttu-id="46e38-156">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="46e38-156">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
