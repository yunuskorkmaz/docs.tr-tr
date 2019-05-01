---
title: 'Nasıl yapılır: XML değişmez değerleri (Visual Basic) değiştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 003715b04f3a5c0fb41e846beb189f117378ea58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053034"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="220c1-102">Nasıl yapılır: XML değişmez değerleri (Visual Basic) değiştirme</span><span class="sxs-lookup"><span data-stu-id="220c1-102">How to: Modify XML Literals (Visual Basic)</span></span>

<span data-ttu-id="220c1-103">Visual Basic, XML değişmez değerlerini değiştirme için kullanışlı yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="220c1-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="220c1-104">Ekleyebilir veya öğeler ve öznitelikler silme ve var olan bir öğe olan yeni bir XML öğesi değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="220c1-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="220c1-105">Bu konu, varolan bir XML değişmez değer değiştirme çeşitli örneklerini sağlamaktadır.</span><span class="sxs-lookup"><span data-stu-id="220c1-105">This topic provides several examples of how to modify an existing XML literal.</span></span>

### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="220c1-106">Bir XML değişmez değeri değerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="220c1-106">To modify the value of an XML literal</span></span>

1. <span data-ttu-id="220c1-107">Bir XML değişmez değeri değerini değiştirmek için XML değişmez ve ayarlanmış bir başvuru elde `Value` özelliğini istediğiniz değer.</span><span class="sxs-lookup"><span data-stu-id="220c1-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>

    <span data-ttu-id="220c1-108">Aşağıdaki kod örneği, tüm değerini güncelleştirir \<fiyat > öğeleri bir XML belgesi.</span><span class="sxs-lookup"><span data-stu-id="220c1-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    <span data-ttu-id="220c1-109">Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="220c1-109">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="220c1-110">XML kaynağı:</span><span class="sxs-lookup"><span data-stu-id="220c1-110">Source XML:</span></span>

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

    <span data-ttu-id="220c1-111">Değiştirilmiş XML:</span><span class="sxs-lookup"><span data-stu-id="220c1-111">Modified XML:</span></span>

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
    > <span data-ttu-id="220c1-112">`Value` Bir koleksiyondaki ilk XML öğesi özelliği başvurur.</span><span class="sxs-lookup"><span data-stu-id="220c1-112">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="220c1-113">Bir koleksiyonda aynı ada sahip birden fazla öğe varsa, ayarı `Value` özelliği yalnızca koleksiyon içindeki ilk öğeyi etkiler.</span><span class="sxs-lookup"><span data-stu-id="220c1-113">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>

### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="220c1-114">Bir XML değişmez değeri için bir öznitelik eklemek için</span><span class="sxs-lookup"><span data-stu-id="220c1-114">To add an attribute to an XML literal</span></span>

1. <span data-ttu-id="220c1-115">XML değişmez değer için bir öznitelik eklemek için ilk XML değişmez değer için bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="220c1-115">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="220c1-116">Ardından, yeni bir XML özniteliği axis özelliği ekleyerek bir öznitelik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="220c1-116">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="220c1-117">Ayrıca, yeni bir ekleyebilirsiniz <xref:System.Xml.Linq.XAttribute> nesne değişmez değeri kullanarak XML <xref:System.Xml.Linq.XContainer.Add%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="220c1-117">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="220c1-118">Aşağıdaki örnek, her iki seçeneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="220c1-118">The following example shows both options.</span></span>

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    <span data-ttu-id="220c1-119">Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="220c1-119">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="220c1-120">XML kaynağı:</span><span class="sxs-lookup"><span data-stu-id="220c1-120">Source XML:</span></span>

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

    <span data-ttu-id="220c1-121">Değiştirilmiş XML:</span><span class="sxs-lookup"><span data-stu-id="220c1-121">Modified XML:</span></span>

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

    <span data-ttu-id="220c1-122">XML özniteliği eksen özellikleri hakkında daha fazla bilgi için bkz: [XML özniteliği Axis özelliği](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="220c1-122">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>

### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="220c1-123">Bir XML değişmez değeri için bir öğe eklemek için</span><span class="sxs-lookup"><span data-stu-id="220c1-123">To add an element to an XML literal</span></span>

1. <span data-ttu-id="220c1-124">XML değişmez değer için bir öğe eklemek için ilk XML değişmez değer için bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="220c1-124">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="220c1-125">Daha sonra yeni bir ekleyebilirsiniz <xref:System.Xml.Linq.XElement> nesnesi kullanarak öğesinin son alt öğesi olarak <xref:System.Xml.Linq.XContainer.Add%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="220c1-125">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="220c1-126">Yeni bir ekleyebilirsiniz <xref:System.Xml.Linq.XElement> nesnesi kullanarak ilk alt öğe olarak <xref:System.Xml.Linq.XContainer.AddFirst%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="220c1-126">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>

    <span data-ttu-id="220c1-127">Diğer alt öğelerine göre belirli bir konumda yeni bir öğe eklemek için öncelikle bitişik bir alt öğeye bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="220c1-127">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="220c1-128">Daha sonra yeni ekleyebilirsiniz <xref:System.Xml.Linq.XElement> kullanarak bitişik alt öğeden önce nesne <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="220c1-128">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="220c1-129">Ayrıca, yeni ekleyebilirsiniz <xref:System.Xml.Linq.XElement> kullanarak bitişik alt öğeden sonra nesne <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="220c1-129">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>

    <span data-ttu-id="220c1-130">Aşağıdaki örnek, her tekniğin örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="220c1-130">The following example shows examples of each of these techniques.</span></span>

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    <span data-ttu-id="220c1-131">Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="220c1-131">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="220c1-132">XML kaynağı:</span><span class="sxs-lookup"><span data-stu-id="220c1-132">Source XML:</span></span>

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

    <span data-ttu-id="220c1-133">Değiştirilmiş XML:</span><span class="sxs-lookup"><span data-stu-id="220c1-133">Modified XML:</span></span>

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

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="220c1-134">Bir öğe veya öznitelik, bir XML değişmez değeri kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="220c1-134">To remove an element or attribute from an XML literal</span></span>

1. <span data-ttu-id="220c1-135">Bir öğe veya öznitelik, bir XML değişmez değeri kaldırmak için öğe veya öznitelik ve çağrı başvuru elde `Remove` yöntemi, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="220c1-135">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    <span data-ttu-id="220c1-136">Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="220c1-136">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="220c1-137">XML kaynağı:</span><span class="sxs-lookup"><span data-stu-id="220c1-137">Source XML:</span></span>

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

    <span data-ttu-id="220c1-138">Değiştirilmiş XML:</span><span class="sxs-lookup"><span data-stu-id="220c1-138">Modified XML:</span></span>

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

    <span data-ttu-id="220c1-139">Tüm öğeler veya öznitelikleri bir XML değişmez değeri kaldırmak için XML değişmez değer için bir başvuru almak ve çağrı <xref:System.Xml.Linq.XElement.RemoveAll%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="220c1-139">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>

### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="220c1-140">Bir XML değişmez değeri değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="220c1-140">To modify an XML literal</span></span>

1. <span data-ttu-id="220c1-141">Bir XML öğesi adını değiştirmek için ilk öğeye bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="220c1-141">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="220c1-142">Daha sonra yeni bir oluşturabilirsiniz <xref:System.Xml.Linq.XElement> yeni bir ad ve yeni geçirin nesnesi <xref:System.Xml.Linq.XElement> nesnesini <xref:System.Xml.Linq.XNode.ReplaceWith%2A> varolan yöntemi <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="220c1-142">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>

    <span data-ttu-id="220c1-143">Değiştirdiğiniz öğe korunmalıdır alt öğeleri varsa, yeni değerini ayarlamak <xref:System.Xml.Linq.XElement> nesnesini <xref:System.Xml.Linq.XContainer.Nodes%2A> özelliği var olan öğe.</span><span class="sxs-lookup"><span data-stu-id="220c1-143">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="220c1-144">Bu yeni öğenin değeri var olan öğenin iç XML ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="220c1-144">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="220c1-145">Aksi takdirde, yeni bir öğe için değeri ayarlayabilirsiniz `Value` özelliği var olan öğe.</span><span class="sxs-lookup"><span data-stu-id="220c1-145">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>

    <span data-ttu-id="220c1-146">Aşağıdaki kod örneği, tüm değiştirir \<açıklaması > öğeleri ile bir \<soyut > öğesi.</span><span class="sxs-lookup"><span data-stu-id="220c1-146">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="220c1-147">İçeriği \<açıklaması > öğesi yeni korunur \<soyut > öğesi kullanarak <xref:System.Xml.Linq.XContainer.Nodes%2A> özelliği \<açıklaması > <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="220c1-147">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    <span data-ttu-id="220c1-148">Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="220c1-148">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="220c1-149">XML kaynağı:</span><span class="sxs-lookup"><span data-stu-id="220c1-149">Source XML:</span></span>

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

    <span data-ttu-id="220c1-150">Değiştirilmiş XML:</span><span class="sxs-lookup"><span data-stu-id="220c1-150">Modified XML:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="220c1-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="220c1-151">See also</span></span>

- [<span data-ttu-id="220c1-152">Visual Basic'de XML düzenleme</span><span class="sxs-lookup"><span data-stu-id="220c1-152">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [<span data-ttu-id="220c1-153">XML</span><span class="sxs-lookup"><span data-stu-id="220c1-153">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="220c1-154">Nasıl yapılır: Dosya, dize veya Stream XML yükleme</span><span class="sxs-lookup"><span data-stu-id="220c1-154">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="220c1-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="220c1-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="220c1-156">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="220c1-156">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
