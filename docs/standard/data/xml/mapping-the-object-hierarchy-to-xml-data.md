---
title: XML Verilerine Nesne Hiyerarşisi Eşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
ms.openlocfilehash: 97cc7558f51b7bcbdb5201ef0f0c463da8f2c070
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822613"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="16304-102">XML Verilerine Nesne Hiyerarşisi Eşleme</span><span class="sxs-lookup"><span data-stu-id="16304-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="16304-103">Bir XML belgesi bellekte olduğunda, kavramsal temsil bir ağaç olur.</span><span class="sxs-lookup"><span data-stu-id="16304-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="16304-104">Programlama için ağacın düğümlerine erişmek üzere bir nesne hiyerarşiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="16304-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="16304-105">Aşağıdaki örnek, XML içeriğinin düğüm haline geldiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="16304-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="16304-106">XML, XML Belge Nesne Modeli (DOM) olarak okunduğu için parçalar düğümlere çevrilir ve bu düğümler kendi düğüm türleri ve değerleri gibi, kendileri hakkındaki ek meta verileri korurlar.</span><span class="sxs-lookup"><span data-stu-id="16304-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="16304-107">Düğüm türü nesnesidir ve hangi eylemlerin gerçekleştirilebileceğini ve hangi özelliklerin ayarlanamayacağını veya alınamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="16304-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="16304-108">Aşağıdaki basit XML 'e sahipseniz:</span><span class="sxs-lookup"><span data-stu-id="16304-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="16304-109">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="16304-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="16304-110">Giriş, atanan düğüm türü özelliği ile aşağıdaki düğüm ağacı olarak bellekte temsil edilir:</span><span class="sxs-lookup"><span data-stu-id="16304-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="16304-111">![örnek düğüm ağacı](media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="16304-111">![example node tree](media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="16304-112">Kitap ve başlık düğümü ağaç gösterimi</span><span class="sxs-lookup"><span data-stu-id="16304-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="16304-113">Öğesi `book` bir **XmlElement** nesnesi olur, Next öğesi `title` de bir **XmlElement** olur, ancak öğe içeriği bir **XmlText** nesnesi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="16304-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="16304-114">**XmlElement** yöntemlerine ve özelliklerine bakarak, Yöntemler ve özellikler, **XmlText** nesnesinde bulunan yöntemlerden ve özelliklerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="16304-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="16304-115">Bu nedenle, XML biçimlendirmesinin hangi düğüm türünde olacağını bilmek, düğüm türü gerçekleştirilebilecek eylemleri belirlediği için çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="16304-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="16304-116">Aşağıdaki örnek, XML verilerinde okur ve düğüm türüne bağlı olarak farklı metin yazar.</span><span class="sxs-lookup"><span data-stu-id="16304-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="16304-117">Aşağıdaki XML veri dosyasını girdi olarak kullanma, **items.xml**:</span><span class="sxs-lookup"><span data-stu-id="16304-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="16304-118">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="16304-118">**Input**</span></span>  
  
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
  
 <span data-ttu-id="16304-119">Aşağıdaki kod örneği **items.xml** dosyayı okur ve her düğüm türü için bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="16304-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
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
  
 <span data-ttu-id="16304-120">Örneğin çıktısı, verilerin düğüm türlerine eşlenmesinin ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="16304-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="16304-121">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="16304-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>
```  
  
 <span data-ttu-id="16304-122">Girişi bir kerede tek bir satıra götürdüğünde ve koddan oluşturulan çıktıyı kullanarak, hangi düğüm testinin çıktı satırlarını üretdiğini analiz etmek için aşağıdaki tabloyu kullanabilirsiniz. böylece, hangi XML verilerinin ne tür düğüm türünde olduğunu anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16304-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="16304-123">Girdi</span><span class="sxs-lookup"><span data-stu-id="16304-123">Input</span></span>|<span data-ttu-id="16304-124">Çıktı</span><span class="sxs-lookup"><span data-stu-id="16304-124">Output</span></span>|<span data-ttu-id="16304-125">Düğüm türü testi</span><span class="sxs-lookup"><span data-stu-id="16304-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|\<?xml version="1.0"?>|\<?xml version='1.0'?>|<span data-ttu-id="16304-126">XmlNodeType.Xmlbildirimi</span><span class="sxs-lookup"><span data-stu-id="16304-126">XmlNodeType.XmlDeclaration</span></span>|  
|\<!-- This is a sample XML document -->|\<!--This is a sample XML document -->|<span data-ttu-id="16304-127">XmlNodeType. Comment</span><span class="sxs-lookup"><span data-stu-id="16304-127">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="16304-128">\<!DOCTYPE Items [\<!ENTITY number "123">] ></span><span class="sxs-lookup"><span data-stu-id="16304-128">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="16304-129">\<!DOCTYPE Items [\<!ENTITY number "123">]</span><span class="sxs-lookup"><span data-stu-id="16304-129">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="16304-130">XmlNodeType.DocumentType</span><span class="sxs-lookup"><span data-stu-id="16304-130">XmlNodeType.DocumentType</span></span>|  
|\<Items>|\<Items>|<span data-ttu-id="16304-131">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="16304-131">XmlNodeType.Element</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="16304-132">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="16304-132">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="16304-133">Bir varlıkla test edin: &number;</span><span class="sxs-lookup"><span data-stu-id="16304-133">Test with an entity: &number;</span></span>|<span data-ttu-id="16304-134">Bir varlıkla test: 123</span><span class="sxs-lookup"><span data-stu-id="16304-134">Test with an entity: 123</span></span>|<span data-ttu-id="16304-135">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="16304-135">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="16304-136">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="16304-136">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="16304-137">XmNodeType. element</span><span class="sxs-lookup"><span data-stu-id="16304-137">XmNodeType.Element</span></span>|  
|<span data-ttu-id="16304-138">alt öğe ile test etme</span><span class="sxs-lookup"><span data-stu-id="16304-138">test with a child element</span></span>|<span data-ttu-id="16304-139">alt öğe ile test etme</span><span class="sxs-lookup"><span data-stu-id="16304-139">test with a child element</span></span>|<span data-ttu-id="16304-140">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="16304-140">XmlNodeType.Text</span></span>|  
|\<more>|\<more>|<span data-ttu-id="16304-141">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="16304-141">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="16304-142">Çocuk</span><span class="sxs-lookup"><span data-stu-id="16304-142">stuff</span></span>|<span data-ttu-id="16304-143">Çocuk</span><span class="sxs-lookup"><span data-stu-id="16304-143">stuff</span></span>|<span data-ttu-id="16304-144">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="16304-144">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="16304-145">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="16304-145">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="16304-146">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="16304-146">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="16304-147">CDATA bölümüyle test etme</span><span class="sxs-lookup"><span data-stu-id="16304-147">test with a CDATA section</span></span>|<span data-ttu-id="16304-148">CDATA bölümüyle test etme</span><span class="sxs-lookup"><span data-stu-id="16304-148">test with a CDATA section</span></span>|<span data-ttu-id="16304-149">XmlTest. Text</span><span class="sxs-lookup"><span data-stu-id="16304-149">XmlTest.Text</span></span>|  
|<span data-ttu-id="16304-150"><! [CDATA [ \<456> ]]\></span><span class="sxs-lookup"><span data-stu-id="16304-150"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="16304-151"><! [CDATA [ \<456> ]]\></span><span class="sxs-lookup"><span data-stu-id="16304-151"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="16304-152">XmlTest. CDATA</span><span class="sxs-lookup"><span data-stu-id="16304-152">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="16304-153">def</span><span class="sxs-lookup"><span data-stu-id="16304-153">def</span></span>|<span data-ttu-id="16304-154">def</span><span class="sxs-lookup"><span data-stu-id="16304-154">def</span></span>|<span data-ttu-id="16304-155">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="16304-155">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="16304-156">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="16304-156">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="16304-157">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="16304-157">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="16304-158">Bir Char varlığıyla test: &\# 65;</span><span class="sxs-lookup"><span data-stu-id="16304-158">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="16304-159">Bir Char varlığı ile test: A</span><span class="sxs-lookup"><span data-stu-id="16304-159">Test with a char entity: A</span></span>|<span data-ttu-id="16304-160">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="16304-160">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="16304-161">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="16304-161">XmlNodeType.EndElement</span></span>|  
|\<!-- Fourteen chars in this element.-->|\<--Fourteen chars in this element.-->|<span data-ttu-id="16304-162">XmlNodeType. Comment</span><span class="sxs-lookup"><span data-stu-id="16304-162">XmlNodeType.Comment</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="16304-163">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="16304-163">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="16304-164">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="16304-164">1234567890ABCD</span></span>|<span data-ttu-id="16304-165">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="16304-165">1234567890ABCD</span></span>|<span data-ttu-id="16304-166">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="16304-166">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="16304-167">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="16304-167">XmlNodeType.EndElement</span></span>|  
|\</Items>|\</Items>|<span data-ttu-id="16304-168">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="16304-168">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="16304-169">Düğüm türü ne tür eylemlerin geçerli olduğunu ve ne tür özellikleri ayarlayabileceğinizi ve alabildiğinizi kontrol etmek için hangi düğüm türünün atandığını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="16304-169">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="16304-170">Veriler DOM 'a **PreserveWhitespace** bayrağıyla yüklendiğinde, boşluk için düğüm oluşturma denetlenir.</span><span class="sxs-lookup"><span data-stu-id="16304-170">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="16304-171">Daha fazla bilgi için bkz. [Dom yüklenirken beyaz boşluk ve önemli boşluk işleme](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="16304-171">For more information, see [White Space and Significant White Space Handling when Loading the DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="16304-172">DOM 'a yeni düğümler eklemek için bkz. [XML belgesine düğüm ekleme](inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="16304-172">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="16304-173">DOM 'dan düğüm kaldırmak için bkz. [BIR XML belgesinden düğümleri, içeriği ve değerleri kaldırma](removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="16304-173">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="16304-174">DOM 'daki düğümlerin içeriğini değiştirmek için bkz. [BIR XML belgesindeki düğümleri, içeriği ve değerleri değiştirme](modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="16304-174">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16304-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16304-175">See also</span></span>

- [<span data-ttu-id="16304-176">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="16304-176">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
