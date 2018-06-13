---
title: 'Nasıl yapılır: XML Değişmez Değerlerini Değiştirme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 17da86d6d10fb1602c16fc2a8c4d6f9f8acf8ff7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656051"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="daaf9-102">Nasıl yapılır: XML Değişmez Değerlerini Değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="daaf9-102">How to: Modify XML Literals (Visual Basic)</span></span>
<span data-ttu-id="daaf9-103">Visual Basic XML değişmez değerleri değiştirmek için kullanışlı yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="daaf9-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="daaf9-104">Ekleme veya öğeleri ve özniteliklerinin silme ve varolan öğeyi yeni bir XML öğesi ile değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="daaf9-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="daaf9-105">Bu konu, mevcut XML değişmez değer değiştirmek çeşitli örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="daaf9-105">This topic provides several examples of how to modify an existing XML literal.</span></span>  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="daaf9-106">XML değişmez değeri değerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="daaf9-106">To modify the value of an XML literal</span></span>  
  
1.  <span data-ttu-id="daaf9-107">XML değişmez değeri değerini değiştirmek için XML değişmez değer ve ayarlanan bir başvuru elde `Value` istenen değeri özelliğine.</span><span class="sxs-lookup"><span data-stu-id="daaf9-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>  
  
     <span data-ttu-id="daaf9-108">Aşağıdaki kod örneğinde tüm değerini güncelleştirmeleri \<fiyat > öğelerini bir XML belgesi.</span><span class="sxs-lookup"><span data-stu-id="daaf9-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     <span data-ttu-id="daaf9-109">Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="daaf9-109">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
    >  <span data-ttu-id="daaf9-110">`Value` Özelliği bir koleksiyon ilk XML öğe anlamına gelmektedir.</span><span class="sxs-lookup"><span data-stu-id="daaf9-110">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="daaf9-111">Bir koleksiyondaki aynı ada sahip birden fazla öğe varsa, ayarı `Value` özelliği yalnızca ilk öğe koleksiyonda etkiler.</span><span class="sxs-lookup"><span data-stu-id="daaf9-111">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="daaf9-112">Öznitelik bir XML değişmez değeri eklemek için</span><span class="sxs-lookup"><span data-stu-id="daaf9-112">To add an attribute to an XML literal</span></span>  
  
1.  <span data-ttu-id="daaf9-113">Öznitelik bir XML değişmez değer eklemek için önce değişmez değer XML başvurusu edinin.</span><span class="sxs-lookup"><span data-stu-id="daaf9-113">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="daaf9-114">Ardından, yeni bir XML özniteliği axis özelliği ekleyerek bir öznitelik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="daaf9-114">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="daaf9-115">Ayrıca, yeni bir ekleyebilirsiniz <xref:System.Xml.Linq.XAttribute> kullanarak değişmez değer XML nesnesine <xref:System.Xml.Linq.XContainer.Add%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="daaf9-115">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="daaf9-116">Aşağıdaki örnek, her iki seçenek gösterir.</span><span class="sxs-lookup"><span data-stu-id="daaf9-116">The following example shows both options.</span></span>  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     <span data-ttu-id="daaf9-117">Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="daaf9-117">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
     <span data-ttu-id="daaf9-118">XML özniteliği axis özellikleri hakkında daha fazla bilgi için bkz: [XML özniteliği Axis özelliği](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="daaf9-118">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>  
  
### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="daaf9-119">Bir XML değişmez değeri için bir öğe eklemek için</span><span class="sxs-lookup"><span data-stu-id="daaf9-119">To add an element to an XML literal</span></span>  
  
1.  <span data-ttu-id="daaf9-120">XML değişmez değer için bir öğe eklemek için önce değişmez değer XML başvurusu edinin.</span><span class="sxs-lookup"><span data-stu-id="daaf9-120">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="daaf9-121">Daha sonra yeni bir ekleyebilirsiniz <xref:System.Xml.Linq.XElement> nesnesi kullanarak öğesinin son alt öğesi olarak <xref:System.Xml.Linq.XContainer.Add%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="daaf9-121">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="daaf9-122">Yeni bir ekleyebilirsiniz <xref:System.Xml.Linq.XElement> nesnesi kullanarak ilk alt öğesi olarak <xref:System.Xml.Linq.XContainer.AddFirst%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="daaf9-122">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>  
  
     <span data-ttu-id="daaf9-123">Diğer alt öğeleri göre belirli bir konumda yeni bir öğe eklemek için öncelikle bitişik bir alt öğe başvurusu edinin.</span><span class="sxs-lookup"><span data-stu-id="daaf9-123">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="daaf9-124">Daha sonra yeni ekleyebilirsiniz <xref:System.Xml.Linq.XElement> nesnesi kullanarak bitişik alt öğe önce <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="daaf9-124">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="daaf9-125">Ayrıca, yeni ekleyebilirsiniz <xref:System.Xml.Linq.XElement> nesnesi kullanarak bitişik alt öğe sonra <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="daaf9-125">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>  
  
     <span data-ttu-id="daaf9-126">Aşağıdaki örnekte, her tekniğin örnekler gösterir.</span><span class="sxs-lookup"><span data-stu-id="daaf9-126">The following example shows examples of each of these techniques.</span></span>  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     <span data-ttu-id="daaf9-127">Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="daaf9-127">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="daaf9-128">Öğe veya öznitelik bir XML değişmez değeri kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="daaf9-128">To remove an element or attribute from an XML literal</span></span>  
  
1.  <span data-ttu-id="daaf9-129">Bir öğe veya öznitelik bir XML değişmez değeri kaldırmak için öğe veya öznitelik ve çağrı başvuru elde `Remove` aşağıdaki örnekte gösterildiği gibi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="daaf9-129">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     <span data-ttu-id="daaf9-130">Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="daaf9-130">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
     <span data-ttu-id="daaf9-131">Tüm öğeleri ve öznitelikleri bir XML değişmez değeri kaldırmak için değişmez değer XML başvurusu edinin ve çağrı <xref:System.Xml.Linq.XElement.RemoveAll%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="daaf9-131">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>  
  
### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="daaf9-132">XML değişmez değeri değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="daaf9-132">To modify an XML literal</span></span>  
  
1.  <span data-ttu-id="daaf9-133">Bir XML öğesi adını değiştirmek için ilk öğe başvurusu edinin.</span><span class="sxs-lookup"><span data-stu-id="daaf9-133">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="daaf9-134">Daha sonra yeni bir oluşturabilirsiniz <xref:System.Xml.Linq.XElement> , yeni bir ad ve yeni geçirin sahip bir nesne <xref:System.Xml.Linq.XElement> nesnesini <xref:System.Xml.Linq.XNode.ReplaceWith%2A> var olan yöntemi <xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="daaf9-134">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     <span data-ttu-id="daaf9-135">Değiştirdiğiniz öğenin korunmalıdır alt öğeleri varsa, yeni değerini <xref:System.Xml.Linq.XElement> nesnesine <xref:System.Xml.Linq.XContainer.Nodes%2A> varolan öğesi özelliği.</span><span class="sxs-lookup"><span data-stu-id="daaf9-135">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="daaf9-136">Bu yeni öğenin değerini var olan öğenin iç XML'e ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="daaf9-136">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="daaf9-137">Aksi takdirde, yeni öğe değerini ayarlayabilir `Value` varolan öğesi özelliği.</span><span class="sxs-lookup"><span data-stu-id="daaf9-137">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>  
  
     <span data-ttu-id="daaf9-138">Aşağıdaki kod örneğinde tüm değiştirir \<açıklama > öğelerle bir \<soyut > öğesi.</span><span class="sxs-lookup"><span data-stu-id="daaf9-138">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="daaf9-139">İçeriği \<açıklama > öğesi yeni korunur \<soyut > öğesi kullanarak <xref:System.Xml.Linq.XContainer.Nodes%2A> özelliği \<açıklama > <xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="daaf9-139">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     <span data-ttu-id="daaf9-140">Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="daaf9-140">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
## <a name="see-also"></a><span data-ttu-id="daaf9-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="daaf9-141">See Also</span></span>  
 [<span data-ttu-id="daaf9-142">Visual Basic'te XML düzenleme</span><span class="sxs-lookup"><span data-stu-id="daaf9-142">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 [<span data-ttu-id="daaf9-143">XML</span><span class="sxs-lookup"><span data-stu-id="daaf9-143">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="daaf9-144">Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme</span><span class="sxs-lookup"><span data-stu-id="daaf9-144">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 [<span data-ttu-id="daaf9-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="daaf9-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="daaf9-146">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="daaf9-146">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
