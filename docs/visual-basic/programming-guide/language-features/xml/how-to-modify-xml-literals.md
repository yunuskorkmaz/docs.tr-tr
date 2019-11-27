---
title: 'Nasıl yapılır: XML Değişmez Değerlerini Değiştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 99ec35addcb9fc8d886c9151cde87227b5113eb9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330854"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="177b9-102">Nasıl yapılır: XML Değişmez Değerlerini Değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="177b9-102">How to: Modify XML Literals (Visual Basic)</span></span>

<span data-ttu-id="177b9-103">Visual Basic, XML değişmez değerlerini değiştirmek için kullanışlı yollar sağlar.</span><span class="sxs-lookup"><span data-stu-id="177b9-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="177b9-104">Öğeleri ve öznitelikleri ekleyebilir ya da silebilirsiniz ve ayrıca var olan bir öğeyi yeni bir XML öğesiyle değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="177b9-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="177b9-105">Bu konuda, var olan bir XML sabit değerinin nasıl değiştirileceği hakkında birkaç örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="177b9-105">This topic provides several examples of how to modify an existing XML literal.</span></span>

### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="177b9-106">Bir XML sabit değerinin değerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="177b9-106">To modify the value of an XML literal</span></span>

1. <span data-ttu-id="177b9-107">Bir XML sabit değerinin değerini değiştirmek için, XML değişmez değerine bir başvuru alın ve `Value` özelliğini istenen değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="177b9-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>

    <span data-ttu-id="177b9-108">Aşağıdaki kod örneği bir XML belgesindeki tüm \<Price > öğelerinin değerini günceller.</span><span class="sxs-lookup"><span data-stu-id="177b9-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    <span data-ttu-id="177b9-109">Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="177b9-109">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="177b9-110">Kaynak XML:</span><span class="sxs-lookup"><span data-stu-id="177b9-110">Source XML:</span></span>

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

    <span data-ttu-id="177b9-111">Değiştirilen XML:</span><span class="sxs-lookup"><span data-stu-id="177b9-111">Modified XML:</span></span>

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
    > <span data-ttu-id="177b9-112">`Value` özelliği, bir koleksiyondaki ilk XML öğesine başvurur.</span><span class="sxs-lookup"><span data-stu-id="177b9-112">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="177b9-113">Koleksiyonda aynı ada sahip birden fazla öğe varsa, `Value` özelliğinin ayarlanması yalnızca koleksiyondaki ilk öğeyi etkiler.</span><span class="sxs-lookup"><span data-stu-id="177b9-113">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>

### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="177b9-114">Bir XML sabit değerine öznitelik eklemek için</span><span class="sxs-lookup"><span data-stu-id="177b9-114">To add an attribute to an XML literal</span></span>

1. <span data-ttu-id="177b9-115">Bir XML sabit değerine bir öznitelik eklemek için, önce XML değişmez değerine bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="177b9-115">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="177b9-116">Daha sonra yeni bir XML özniteliği eksen özelliği ekleyerek bir öznitelik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="177b9-116">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="177b9-117">Ayrıca, <xref:System.Xml.Linq.XContainer.Add%2A> metodunu kullanarak XML sabit değerine yeni bir <xref:System.Xml.Linq.XAttribute> nesnesi de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="177b9-117">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="177b9-118">Aşağıdaki örnekte her iki seçenek de gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="177b9-118">The following example shows both options.</span></span>

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    <span data-ttu-id="177b9-119">Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="177b9-119">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="177b9-120">Kaynak XML:</span><span class="sxs-lookup"><span data-stu-id="177b9-120">Source XML:</span></span>

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

    <span data-ttu-id="177b9-121">Değiştirilen XML:</span><span class="sxs-lookup"><span data-stu-id="177b9-121">Modified XML:</span></span>

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

    <span data-ttu-id="177b9-122">XML özniteliği eksen özellikleri hakkında daha fazla bilgi için bkz. [XML özniteliği eksen özelliği](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="177b9-122">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>

### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="177b9-123">Bir XML sabit değerine öğe eklemek için</span><span class="sxs-lookup"><span data-stu-id="177b9-123">To add an element to an XML literal</span></span>

1. <span data-ttu-id="177b9-124">Bir XML sabit değerine öğe eklemek için, önce XML değişmez değerine bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="177b9-124">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="177b9-125">Daha sonra, <xref:System.Xml.Linq.XContainer.Add%2A> yöntemini kullanarak, öğenin son alt öğesi olarak yeni bir <xref:System.Xml.Linq.XElement> nesnesi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="177b9-125">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="177b9-126"><xref:System.Xml.Linq.XContainer.AddFirst%2A> yöntemini kullanarak yeni bir <xref:System.Xml.Linq.XElement> nesnesini ilk alt öğe olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="177b9-126">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>

    <span data-ttu-id="177b9-127">Belirli bir konuma diğer alt öğelere göre yeni bir öğe eklemek için, önce bitişik bir alt öğeye bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="177b9-127">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="177b9-128">Sonra, <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> metodunu kullanarak komşu alt öğeden önce yeni <xref:System.Xml.Linq.XElement> nesnesini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="177b9-128">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="177b9-129">Ayrıca, <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> yöntemini kullanarak komşu alt öğeden sonra yeni <xref:System.Xml.Linq.XElement> nesnesini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="177b9-129">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>

    <span data-ttu-id="177b9-130">Aşağıdaki örnek, bu tekniklerin her birinin örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="177b9-130">The following example shows examples of each of these techniques.</span></span>

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    <span data-ttu-id="177b9-131">Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="177b9-131">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="177b9-132">Kaynak XML:</span><span class="sxs-lookup"><span data-stu-id="177b9-132">Source XML:</span></span>

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

    <span data-ttu-id="177b9-133">Değiştirilen XML:</span><span class="sxs-lookup"><span data-stu-id="177b9-133">Modified XML:</span></span>

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

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="177b9-134">Bir XML sabit değerinden öğe veya öznitelik kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="177b9-134">To remove an element or attribute from an XML literal</span></span>

1. <span data-ttu-id="177b9-135">Bir öğeyi veya özniteliği bir XML sabit değerinden kaldırmak için, aşağıdaki örnekte gösterildiği gibi, öğe veya özniteliğe bir başvuru alın ve `Remove` yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="177b9-135">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    <span data-ttu-id="177b9-136">Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="177b9-136">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="177b9-137">Kaynak XML:</span><span class="sxs-lookup"><span data-stu-id="177b9-137">Source XML:</span></span>

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

    <span data-ttu-id="177b9-138">Değiştirilen XML:</span><span class="sxs-lookup"><span data-stu-id="177b9-138">Modified XML:</span></span>

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

    <span data-ttu-id="177b9-139">Bir XML sabit değerinden tüm öğeleri veya öznitelikleri kaldırmak için, XML değişmez değerine bir başvuru alın ve <xref:System.Xml.Linq.XElement.RemoveAll%2A> yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="177b9-139">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>

### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="177b9-140">Bir XML sabit değerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="177b9-140">To modify an XML literal</span></span>

1. <span data-ttu-id="177b9-141">Bir XML öğesinin adını değiştirmek için öncelikle öğesine bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="177b9-141">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="177b9-142">Daha sonra yeni bir ada sahip yeni bir <xref:System.Xml.Linq.XElement> nesnesi oluşturabilir ve yeni <xref:System.Xml.Linq.XElement> nesnesini varolan <xref:System.Xml.Linq.XElement> nesnesinin <xref:System.Xml.Linq.XNode.ReplaceWith%2A> yöntemine geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="177b9-142">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>

    <span data-ttu-id="177b9-143">Değiştirdiğiniz öğenin korunması gereken alt öğeleri varsa, yeni <xref:System.Xml.Linq.XElement> nesnesinin değerini varolan öğenin <xref:System.Xml.Linq.XContainer.Nodes%2A> özelliğine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="177b9-143">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="177b9-144">Bu, yeni öğenin değerini varolan öğenin iç XML değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="177b9-144">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="177b9-145">Aksi takdirde, yeni öğenin değerini varolan öğesinin `Value` özelliğine ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="177b9-145">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>

    <span data-ttu-id="177b9-146">Aşağıdaki kod örneği, tüm \<Description > öğelerini \<soyut > öğesi ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="177b9-146">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="177b9-147">\<Description > öğesinin içeriği, yeni \<soyut > öğesinde <xref:System.Xml.Linq.XContainer.Nodes%2A> Description \<> nesnesinin <xref:System.Xml.Linq.XElement> özelliği kullanılarak korunur.</span><span class="sxs-lookup"><span data-stu-id="177b9-147">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    <span data-ttu-id="177b9-148">Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="177b9-148">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="177b9-149">Kaynak XML:</span><span class="sxs-lookup"><span data-stu-id="177b9-149">Source XML:</span></span>

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

    <span data-ttu-id="177b9-150">Değiştirilen XML:</span><span class="sxs-lookup"><span data-stu-id="177b9-150">Modified XML:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="177b9-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="177b9-151">See also</span></span>

- [<span data-ttu-id="177b9-152">Visual Basic XML 'yi düzenleme</span><span class="sxs-lookup"><span data-stu-id="177b9-152">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [<span data-ttu-id="177b9-153">XML</span><span class="sxs-lookup"><span data-stu-id="177b9-153">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="177b9-154">Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme</span><span class="sxs-lookup"><span data-stu-id="177b9-154">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="177b9-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="177b9-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="177b9-156">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="177b9-156">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
