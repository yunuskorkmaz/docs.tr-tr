---
description: 'Hakkında daha fazla bilgi edinin: nesne hiyerarşisini XML verileriyle eşleme'
title: XML Verilerine Nesne Hiyerarşisi Eşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
ms.openlocfilehash: 1be34c43bc9656288e886c309e665b15cb332524
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732104"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="b0919-103">XML Verilerine Nesne Hiyerarşisi Eşleme</span><span class="sxs-lookup"><span data-stu-id="b0919-103">Mapping the Object Hierarchy to XML Data</span></span>

<span data-ttu-id="b0919-104">Bir XML belgesi bellekte olduğunda, kavramsal temsil bir ağaç olur.</span><span class="sxs-lookup"><span data-stu-id="b0919-104">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="b0919-105">Programlama için ağacın düğümlerine erişmek üzere bir nesne hiyerarşiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="b0919-105">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="b0919-106">Aşağıdaki örnek, XML içeriğinin düğüm haline geldiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0919-106">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="b0919-107">XML, XML Belge Nesne Modeli (DOM) olarak okunduğu için parçalar düğümlere çevrilir ve bu düğümler kendi düğüm türleri ve değerleri gibi, kendileri hakkındaki ek meta verileri korurlar.</span><span class="sxs-lookup"><span data-stu-id="b0919-107">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="b0919-108">Düğüm türü nesnesidir ve hangi eylemlerin gerçekleştirilebileceğini ve hangi özelliklerin ayarlanamayacağını veya alınamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="b0919-108">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="b0919-109">Aşağıdaki basit XML 'e sahipseniz:</span><span class="sxs-lookup"><span data-stu-id="b0919-109">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="b0919-110">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="b0919-110">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="b0919-111">Giriş, atanan düğüm türü özelliği ile aşağıdaki düğüm ağacı olarak bellekte temsil edilir:</span><span class="sxs-lookup"><span data-stu-id="b0919-111">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="b0919-112">![örnek düğüm ağacı](media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="b0919-112">![example node tree](media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="b0919-113">Kitap ve başlık düğümü ağaç gösterimi</span><span class="sxs-lookup"><span data-stu-id="b0919-113">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="b0919-114">Öğesi `book` bir **XmlElement** nesnesi olur, Next öğesi `title` de bir **XmlElement** olur, ancak öğe içeriği bir **XmlText** nesnesi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="b0919-114">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="b0919-115">**XmlElement** yöntemlerine ve özelliklerine bakarak, Yöntemler ve özellikler, **XmlText** nesnesinde bulunan yöntemlerden ve özelliklerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="b0919-115">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="b0919-116">Bu nedenle, XML biçimlendirmesinin hangi düğüm türünde olacağını bilmek, düğüm türü gerçekleştirilebilecek eylemleri belirlediği için çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b0919-116">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="b0919-117">Aşağıdaki örnek, XML verilerinde okur ve düğüm türüne bağlı olarak farklı metin yazar.</span><span class="sxs-lookup"><span data-stu-id="b0919-117">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="b0919-118">Aşağıdaki XML veri dosyasını girdi olarak kullanma, **items.xml**:</span><span class="sxs-lookup"><span data-stu-id="b0919-118">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="b0919-119">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="b0919-119">**Input**</span></span>  
  
```xml  
<?xml version="1.0"?>  
<!-- This is a sample XML document -->  
<!DOCTYPE Items [<!ENTITY number "123">]>  
<Items>  
  <Item>Test with an entity: &number;</Item>  
  <Item>test with a child element <more/> stuff</Item>  
  <Item>test with a CDATA section <![CDATA[<456>]]> def</Item>  
  <Item>Test with a char entity: A</Item>  
  <!-- Fourteen chars in this element.-->  
  <Item>1234567890ABCD</Item>  
</Items>  
```  
  
 <span data-ttu-id="b0919-120">Aşağıdaki kod örneği **items.xml** dosyayı okur ve her düğüm türü için bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b0919-120">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
    Private Const filename As String = "items.xml"  
  
    Public Shared Sub Main()  
  
        Dim reader As XmlTextReader = Nothing  
  
        Try  
            ' Load the reader with the data file and
            'ignore all white space nodes.
            reader = New XmlTextReader(filename)  
            reader.WhitespaceHandling = WhitespaceHandling.None  
  
            ' Parse the file and display each of the nodes.  
            While reader.Read()  
                Select Case reader.NodeType  
                    Case XmlNodeType.Element  
                        Console.Write("<{0}>", reader.Name)  
                    Case XmlNodeType.Text  
                        Console.Write(reader.Value)  
                    Case XmlNodeType.CDATA  
                        Console.Write("<![CDATA[{0}]]>", reader.Value)  
                    Case XmlNodeType.ProcessingInstruction  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value)  
                    Case XmlNodeType.Comment  
                        Console.Write("<!--{0}-->", reader.Value)  
                    Case XmlNodeType.XmlDeclaration  
                        Console.Write("<?xml version='1.0'?>")  
                    Case XmlNodeType.Document  
                    Case XmlNodeType.DocumentType  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value)  
                    Case XmlNodeType.EntityReference  
                        Console.Write(reader.Name)  
                    Case XmlNodeType.EndElement  
                        Console.Write("</{0}>", reader.Name)  
                End Select  
            End While  
  
        Finally  
            If Not (reader Is Nothing) Then  
                reader.Close()  
            End If  
        End Try  
    End Sub 'Main ' End class  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    private const String filename = "items.xml";  
  
    public static void Main()  
    {  
        XmlTextReader reader = null;  
  
        try  
        {  
            // Load the reader with the data file and ignore
            // all white space nodes.  
            reader = new XmlTextReader(filename);  
            reader.WhitespaceHandling = WhitespaceHandling.None;  
  
            // Parse the file and display each of the nodes.  
            while (reader.Read())  
            {  
                switch (reader.NodeType)  
                {  
                    case XmlNodeType.Element:  
                        Console.Write("<{0}>", reader.Name);  
                        break;  
                    case XmlNodeType.Text:  
                        Console.Write(reader.Value);  
                        break;  
                    case XmlNodeType.CDATA:  
                        Console.Write("<![CDATA[{0}]]>", reader.Value);  
                        break;  
                    case XmlNodeType.ProcessingInstruction:  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.Comment:  
                        Console.Write("<!--{0}-->", reader.Value);  
                        break;  
                    case XmlNodeType.XmlDeclaration:  
                        Console.Write("<?xml version='1.0'?>");  
                        break;  
                    case XmlNodeType.Document:  
                        break;  
                    case XmlNodeType.DocumentType:  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.EntityReference:  
                        Console.Write(reader.Name);  
                        break;  
                    case XmlNodeType.EndElement:  
                        Console.Write("</{0}>", reader.Name);  
                        break;  
                }  
            }  
        }  
  
        finally  
        {  
            if (reader != null)  
                reader.Close();  
        }  
    }  
} // End class  
```  
  
 <span data-ttu-id="b0919-121">Örneğin çıktısı, verilerin düğüm türlerine eşlenmesinin ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="b0919-121">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="b0919-122">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="b0919-122">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>
```  
  
 <span data-ttu-id="b0919-123">Girişi bir kerede tek bir satıra götürdüğünde ve koddan oluşturulan çıktıyı kullanarak, hangi düğüm testinin çıktı satırlarını üretdiğini analiz etmek için aşağıdaki tabloyu kullanabilirsiniz. böylece, hangi XML verilerinin ne tür düğüm türünde olduğunu anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0919-123">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="b0919-124">Girdi</span><span class="sxs-lookup"><span data-stu-id="b0919-124">Input</span></span>|<span data-ttu-id="b0919-125">Çıktı</span><span class="sxs-lookup"><span data-stu-id="b0919-125">Output</span></span>|<span data-ttu-id="b0919-126">Düğüm türü testi</span><span class="sxs-lookup"><span data-stu-id="b0919-126">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|\<?xml version="1.0"?>|\<?xml version='1.0'?>|<span data-ttu-id="b0919-127">XmlNodeType.Xmlbildirimi</span><span class="sxs-lookup"><span data-stu-id="b0919-127">XmlNodeType.XmlDeclaration</span></span>|  
|\<!-- This is a sample XML document -->|\<!--This is a sample XML document -->|<span data-ttu-id="b0919-128">XmlNodeType. Comment</span><span class="sxs-lookup"><span data-stu-id="b0919-128">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="b0919-129">\<!DOCTYPE Items [\<!ENTITY number "123">] ></span><span class="sxs-lookup"><span data-stu-id="b0919-129">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="b0919-130">\<!DOCTYPE Items [\<!ENTITY number "123">]</span><span class="sxs-lookup"><span data-stu-id="b0919-130">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="b0919-131">XmlNodeType.DocumentType</span><span class="sxs-lookup"><span data-stu-id="b0919-131">XmlNodeType.DocumentType</span></span>|  
|\<Items>|\<Items>|<span data-ttu-id="b0919-132">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="b0919-132">XmlNodeType.Element</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="b0919-133">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="b0919-133">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b0919-134">Bir varlıkla test edin: &number;</span><span class="sxs-lookup"><span data-stu-id="b0919-134">Test with an entity: &number;</span></span>|<span data-ttu-id="b0919-135">Bir varlıkla test: 123</span><span class="sxs-lookup"><span data-stu-id="b0919-135">Test with an entity: 123</span></span>|<span data-ttu-id="b0919-136">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="b0919-136">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="b0919-137">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="b0919-137">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="b0919-138">XmNodeType. element</span><span class="sxs-lookup"><span data-stu-id="b0919-138">XmNodeType.Element</span></span>|  
|<span data-ttu-id="b0919-139">alt öğe ile test etme</span><span class="sxs-lookup"><span data-stu-id="b0919-139">test with a child element</span></span>|<span data-ttu-id="b0919-140">alt öğe ile test etme</span><span class="sxs-lookup"><span data-stu-id="b0919-140">test with a child element</span></span>|<span data-ttu-id="b0919-141">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="b0919-141">XmlNodeType.Text</span></span>|  
|\<more>|\<more>|<span data-ttu-id="b0919-142">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="b0919-142">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b0919-143">Çocuk</span><span class="sxs-lookup"><span data-stu-id="b0919-143">stuff</span></span>|<span data-ttu-id="b0919-144">Çocuk</span><span class="sxs-lookup"><span data-stu-id="b0919-144">stuff</span></span>|<span data-ttu-id="b0919-145">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="b0919-145">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="b0919-146">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="b0919-146">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="b0919-147">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="b0919-147">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b0919-148">CDATA bölümüyle test etme</span><span class="sxs-lookup"><span data-stu-id="b0919-148">test with a CDATA section</span></span>|<span data-ttu-id="b0919-149">CDATA bölümüyle test etme</span><span class="sxs-lookup"><span data-stu-id="b0919-149">test with a CDATA section</span></span>|<span data-ttu-id="b0919-150">XmlTest. Text</span><span class="sxs-lookup"><span data-stu-id="b0919-150">XmlTest.Text</span></span>|  
|<span data-ttu-id="b0919-151"><! [CDATA [ \<456> ]]\></span><span class="sxs-lookup"><span data-stu-id="b0919-151"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="b0919-152"><! [CDATA [ \<456> ]]\></span><span class="sxs-lookup"><span data-stu-id="b0919-152"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="b0919-153">XmlTest. CDATA</span><span class="sxs-lookup"><span data-stu-id="b0919-153">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="b0919-154">def</span><span class="sxs-lookup"><span data-stu-id="b0919-154">def</span></span>|<span data-ttu-id="b0919-155">def</span><span class="sxs-lookup"><span data-stu-id="b0919-155">def</span></span>|<span data-ttu-id="b0919-156">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="b0919-156">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="b0919-157">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="b0919-157">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="b0919-158">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="b0919-158">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b0919-159">Bir Char varlığıyla test: &\# 65;</span><span class="sxs-lookup"><span data-stu-id="b0919-159">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="b0919-160">Bir Char varlığı ile test: A</span><span class="sxs-lookup"><span data-stu-id="b0919-160">Test with a char entity: A</span></span>|<span data-ttu-id="b0919-161">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="b0919-161">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="b0919-162">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="b0919-162">XmlNodeType.EndElement</span></span>|  
|\<!-- Fourteen chars in this element.-->|\<--Fourteen chars in this element.-->|<span data-ttu-id="b0919-163">XmlNodeType. Comment</span><span class="sxs-lookup"><span data-stu-id="b0919-163">XmlNodeType.Comment</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="b0919-164">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="b0919-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b0919-165">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="b0919-165">1234567890ABCD</span></span>|<span data-ttu-id="b0919-166">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="b0919-166">1234567890ABCD</span></span>|<span data-ttu-id="b0919-167">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="b0919-167">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="b0919-168">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="b0919-168">XmlNodeType.EndElement</span></span>|  
|\</Items>|\</Items>|<span data-ttu-id="b0919-169">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="b0919-169">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="b0919-170">Düğüm türü ne tür eylemlerin geçerli olduğunu ve ne tür özellikleri ayarlayabileceğinizi ve alabildiğinizi kontrol etmek için hangi düğüm türünün atandığını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0919-170">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="b0919-171">Veriler DOM 'a **PreserveWhitespace** bayrağıyla yüklendiğinde, boşluk için düğüm oluşturma denetlenir.</span><span class="sxs-lookup"><span data-stu-id="b0919-171">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="b0919-172">Daha fazla bilgi için bkz. [Dom yüklenirken beyaz boşluk ve önemli boşluk işleme](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="b0919-172">For more information, see [White Space and Significant White Space Handling when Loading the DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="b0919-173">DOM 'a yeni düğümler eklemek için bkz. [XML belgesine düğüm ekleme](inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b0919-173">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="b0919-174">DOM 'dan düğüm kaldırmak için bkz. [BIR XML belgesinden düğümleri, içeriği ve değerleri kaldırma](removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b0919-174">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="b0919-175">DOM 'daki düğümlerin içeriğini değiştirmek için bkz. [BIR XML belgesindeki düğümleri, içeriği ve değerleri değiştirme](modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b0919-175">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0919-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0919-176">See also</span></span>

- [<span data-ttu-id="b0919-177">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="b0919-177">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
