---
title: XML Verilerine Nesne Hiyerarşisi Eşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
ms.openlocfilehash: 4ad505749625e22a09406549329179990b81c140
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794396"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="eb4b6-102">XML Verilerine Nesne Hiyerarşisi Eşleme</span><span class="sxs-lookup"><span data-stu-id="eb4b6-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="eb4b6-103">Bir XML belgesi bellekte olduğunda, kavramsal temsil bir ağaç olur.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="eb4b6-104">Programlama için ağacın düğümlerine erişmek üzere bir nesne hiyerarşiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="eb4b6-105">Aşağıdaki örnek, XML içeriğinin düğüm haline geldiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="eb4b6-106">XML, XML Belge Nesne Modeli (DOM) olarak okunduğu için parçalar düğümlere çevrilir ve bu düğümler kendi düğüm türleri ve değerleri gibi, kendileri hakkındaki ek meta verileri korurlar.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="eb4b6-107">Düğüm türü nesnesidir ve hangi eylemlerin gerçekleştirilebileceğini ve hangi özelliklerin ayarlanamayacağını veya alınamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="eb4b6-108">Aşağıdaki basit XML 'e sahipseniz:</span><span class="sxs-lookup"><span data-stu-id="eb4b6-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="eb4b6-109">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="eb4b6-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="eb4b6-110">Giriş, atanan düğüm türü özelliği ile aşağıdaki düğüm ağacı olarak bellekte temsil edilir:</span><span class="sxs-lookup"><span data-stu-id="eb4b6-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="eb4b6-111">![örnek düğüm ağacı](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="eb4b6-111">![example node tree](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="eb4b6-112">Kitap ve başlık düğümü ağaç gösterimi</span><span class="sxs-lookup"><span data-stu-id="eb4b6-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="eb4b6-113">`book` Öğesi bir **XmlElement** nesnesi olur, Next öğesi `title`de bir **XmlElement**olur, ancak öğe içeriği bir **XmlText** nesnesi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="eb4b6-114">**XmlElement** yöntemlerine ve özelliklerine bakarak, Yöntemler ve özellikler, **XmlText** nesnesinde bulunan yöntemlerden ve özelliklerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="eb4b6-115">Bu nedenle, XML biçimlendirmesinin hangi düğüm türünde olacağını bilmek, düğüm türü gerçekleştirilebilecek eylemleri belirlediği için çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="eb4b6-116">Aşağıdaki örnek, XML verilerinde okur ve düğüm türüne bağlı olarak farklı metin yazar.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="eb4b6-117">Aşağıdaki XML veri dosyasını input, **Items. xml**olarak kullanma:</span><span class="sxs-lookup"><span data-stu-id="eb4b6-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="eb4b6-118">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="eb4b6-118">**Input**</span></span>  
  
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
  
 <span data-ttu-id="eb4b6-119">Aşağıdaki kod örneği **Items. xml** dosyasını okur ve her düğüm türü için bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
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
  
 <span data-ttu-id="eb4b6-120">Örneğin çıktısı, verilerin düğüm türlerine eşlenmesinin ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="eb4b6-121">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="eb4b6-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>
```  
  
 <span data-ttu-id="eb4b6-122">Girişi bir kerede tek bir satıra götürdüğünde ve koddan oluşturulan çıktıyı kullanarak, hangi düğüm testinin çıktı satırlarını üretdiğini analiz etmek için aşağıdaki tabloyu kullanabilirsiniz. böylece, hangi XML verilerinin ne tür düğüm türünde olduğunu anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="eb4b6-123">Girdi</span><span class="sxs-lookup"><span data-stu-id="eb4b6-123">Input</span></span>|<span data-ttu-id="eb4b6-124">Çıktı</span><span class="sxs-lookup"><span data-stu-id="eb4b6-124">Output</span></span>|<span data-ttu-id="eb4b6-125">Düğüm türü testi</span><span class="sxs-lookup"><span data-stu-id="eb4b6-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|<span data-ttu-id="eb4b6-126">\<? XML Version = "1.0"? ></span><span class="sxs-lookup"><span data-stu-id="eb4b6-126">\<?xml version="1.0"?></span></span>|<span data-ttu-id="eb4b6-127">\<? XML sürümü = ' 1.0 '? ></span><span class="sxs-lookup"><span data-stu-id="eb4b6-127">\<?xml version='1.0'?></span></span>|<span data-ttu-id="eb4b6-128">XmlNodeType. Xmlbildirimi</span><span class="sxs-lookup"><span data-stu-id="eb4b6-128">XmlNodeType.XmlDeclaration</span></span>|  
|<span data-ttu-id="eb4b6-129">\<Örnek bir XML belgesi olan!----></span><span class="sxs-lookup"><span data-stu-id="eb4b6-129">\<!-- This is a sample XML document --></span></span>|<span data-ttu-id="eb4b6-130">\<Örnek bir XML belgesi olan!----></span><span class="sxs-lookup"><span data-stu-id="eb4b6-130">\<!--This is a sample XML document --></span></span>|<span data-ttu-id="eb4b6-131">XmlNodeType. Comment</span><span class="sxs-lookup"><span data-stu-id="eb4b6-131">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="eb4b6-132">\<! DOCTYPE öğeleri [\<! VARLıK numarası "123" >] ></span><span class="sxs-lookup"><span data-stu-id="eb4b6-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="eb4b6-133">\<! DOCTYPE öğeleri [\<! "123" VARLıK numarası >]</span><span class="sxs-lookup"><span data-stu-id="eb4b6-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="eb4b6-134">XmlNodeType. DocumentType</span><span class="sxs-lookup"><span data-stu-id="eb4b6-134">XmlNodeType.DocumentType</span></span>|  
|<span data-ttu-id="eb4b6-135">\<Öğe></span><span class="sxs-lookup"><span data-stu-id="eb4b6-135">\<Items></span></span>|<span data-ttu-id="eb4b6-136">\<Öğe></span><span class="sxs-lookup"><span data-stu-id="eb4b6-136">\<Items></span></span>|<span data-ttu-id="eb4b6-137">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="eb4b6-137">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="eb4b6-138">\<Öğe></span><span class="sxs-lookup"><span data-stu-id="eb4b6-138">\<Item></span></span>|<span data-ttu-id="eb4b6-139">\<Öğe></span><span class="sxs-lookup"><span data-stu-id="eb4b6-139">\<Item></span></span>|<span data-ttu-id="eb4b6-140">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="eb4b6-140">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="eb4b6-141">Bir varlıkla test edin:&number;</span><span class="sxs-lookup"><span data-stu-id="eb4b6-141">Test with an entity: &number;</span></span>|<span data-ttu-id="eb4b6-142">Bir varlıkla test: 123</span><span class="sxs-lookup"><span data-stu-id="eb4b6-142">Test with an entity: 123</span></span>|<span data-ttu-id="eb4b6-143">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="eb4b6-143">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="eb4b6-144">\</İtem></span><span class="sxs-lookup"><span data-stu-id="eb4b6-144">\</Item></span></span>|<span data-ttu-id="eb4b6-145">\</İtem></span><span class="sxs-lookup"><span data-stu-id="eb4b6-145">\</Item></span></span>|<span data-ttu-id="eb4b6-146">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="eb4b6-146">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="eb4b6-147">\<Öğe></span><span class="sxs-lookup"><span data-stu-id="eb4b6-147">\<Item></span></span>|<span data-ttu-id="eb4b6-148">\<Öğe></span><span class="sxs-lookup"><span data-stu-id="eb4b6-148">\<Item></span></span>|<span data-ttu-id="eb4b6-149">XmNodeType. element</span><span class="sxs-lookup"><span data-stu-id="eb4b6-149">XmNodeType.Element</span></span>|  
|<span data-ttu-id="eb4b6-150">alt öğe ile test etme</span><span class="sxs-lookup"><span data-stu-id="eb4b6-150">test with a child element</span></span>|<span data-ttu-id="eb4b6-151">alt öğe ile test etme</span><span class="sxs-lookup"><span data-stu-id="eb4b6-151">test with a child element</span></span>|<span data-ttu-id="eb4b6-152">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="eb4b6-152">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="eb4b6-153">\<daha fazla></span><span class="sxs-lookup"><span data-stu-id="eb4b6-153">\<more></span></span>|<span data-ttu-id="eb4b6-154">\<daha fazla></span><span class="sxs-lookup"><span data-stu-id="eb4b6-154">\<more></span></span>|<span data-ttu-id="eb4b6-155">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="eb4b6-155">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="eb4b6-156">Çocuk</span><span class="sxs-lookup"><span data-stu-id="eb4b6-156">stuff</span></span>|<span data-ttu-id="eb4b6-157">Çocuk</span><span class="sxs-lookup"><span data-stu-id="eb4b6-157">stuff</span></span>|<span data-ttu-id="eb4b6-158">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="eb4b6-158">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="eb4b6-159">\</İtem></span><span class="sxs-lookup"><span data-stu-id="eb4b6-159">\</Item></span></span>|<span data-ttu-id="eb4b6-160">\</İtem></span><span class="sxs-lookup"><span data-stu-id="eb4b6-160">\</Item></span></span>|<span data-ttu-id="eb4b6-161">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="eb4b6-161">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="eb4b6-162">\<Öğe></span><span class="sxs-lookup"><span data-stu-id="eb4b6-162">\<Item></span></span>|<span data-ttu-id="eb4b6-163">\<Öğe></span><span class="sxs-lookup"><span data-stu-id="eb4b6-163">\<Item></span></span>|<span data-ttu-id="eb4b6-164">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="eb4b6-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="eb4b6-165">CDATA bölümüyle test etme</span><span class="sxs-lookup"><span data-stu-id="eb4b6-165">test with a CDATA section</span></span>|<span data-ttu-id="eb4b6-166">CDATA bölümüyle test etme</span><span class="sxs-lookup"><span data-stu-id="eb4b6-166">test with a CDATA section</span></span>|<span data-ttu-id="eb4b6-167">XmlTest. Text</span><span class="sxs-lookup"><span data-stu-id="eb4b6-167">XmlTest.Text</span></span>|  
|<span data-ttu-id="eb4b6-168"><! [CDATA [\<456>]]\></span><span class="sxs-lookup"><span data-stu-id="eb4b6-168"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="eb4b6-169"><! [CDATA [\<456>]]\></span><span class="sxs-lookup"><span data-stu-id="eb4b6-169"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="eb4b6-170">XmlTest. CDATA</span><span class="sxs-lookup"><span data-stu-id="eb4b6-170">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="eb4b6-171">def</span><span class="sxs-lookup"><span data-stu-id="eb4b6-171">def</span></span>|<span data-ttu-id="eb4b6-172">def</span><span class="sxs-lookup"><span data-stu-id="eb4b6-172">def</span></span>|<span data-ttu-id="eb4b6-173">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="eb4b6-173">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="eb4b6-174">\</İtem></span><span class="sxs-lookup"><span data-stu-id="eb4b6-174">\</Item></span></span>|<span data-ttu-id="eb4b6-175">\</İtem></span><span class="sxs-lookup"><span data-stu-id="eb4b6-175">\</Item></span></span>|<span data-ttu-id="eb4b6-176">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="eb4b6-176">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="eb4b6-177">\<Öğe></span><span class="sxs-lookup"><span data-stu-id="eb4b6-177">\<Item></span></span>|<span data-ttu-id="eb4b6-178">\<Öğe></span><span class="sxs-lookup"><span data-stu-id="eb4b6-178">\<Item></span></span>|<span data-ttu-id="eb4b6-179">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="eb4b6-179">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="eb4b6-180">Bir Char varlığıyla test: &\#65;</span><span class="sxs-lookup"><span data-stu-id="eb4b6-180">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="eb4b6-181">Bir Char varlığı ile test: A</span><span class="sxs-lookup"><span data-stu-id="eb4b6-181">Test with a char entity: A</span></span>|<span data-ttu-id="eb4b6-182">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="eb4b6-182">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="eb4b6-183">\</İtem></span><span class="sxs-lookup"><span data-stu-id="eb4b6-183">\</Item></span></span>|<span data-ttu-id="eb4b6-184">\</İtem></span><span class="sxs-lookup"><span data-stu-id="eb4b6-184">\</Item></span></span>|<span data-ttu-id="eb4b6-185">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="eb4b6-185">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="eb4b6-186">\<Bu öğede on dört karakter!--.--></span><span class="sxs-lookup"><span data-stu-id="eb4b6-186">\<!-- Fourteen chars in this element.--></span></span>|<span data-ttu-id="eb4b6-187">\<--Bu öğedeki on dört karakter.--></span><span class="sxs-lookup"><span data-stu-id="eb4b6-187">\<--Fourteen chars in this element.--></span></span>|<span data-ttu-id="eb4b6-188">XmlNodeType. Comment</span><span class="sxs-lookup"><span data-stu-id="eb4b6-188">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="eb4b6-189">\<Öğe></span><span class="sxs-lookup"><span data-stu-id="eb4b6-189">\<Item></span></span>|<span data-ttu-id="eb4b6-190">\<Öğe></span><span class="sxs-lookup"><span data-stu-id="eb4b6-190">\<Item></span></span>|<span data-ttu-id="eb4b6-191">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="eb4b6-191">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="eb4b6-192">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="eb4b6-192">1234567890ABCD</span></span>|<span data-ttu-id="eb4b6-193">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="eb4b6-193">1234567890ABCD</span></span>|<span data-ttu-id="eb4b6-194">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="eb4b6-194">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="eb4b6-195">\</İtem></span><span class="sxs-lookup"><span data-stu-id="eb4b6-195">\</Item></span></span>|<span data-ttu-id="eb4b6-196">\</İtem></span><span class="sxs-lookup"><span data-stu-id="eb4b6-196">\</Item></span></span>|<span data-ttu-id="eb4b6-197">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="eb4b6-197">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="eb4b6-198">\</Items></span><span class="sxs-lookup"><span data-stu-id="eb4b6-198">\</Items></span></span>|<span data-ttu-id="eb4b6-199">\</Items></span><span class="sxs-lookup"><span data-stu-id="eb4b6-199">\</Items></span></span>|<span data-ttu-id="eb4b6-200">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="eb4b6-200">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="eb4b6-201">Düğüm türü ne tür eylemlerin geçerli olduğunu ve ne tür özellikleri ayarlayabileceğinizi ve alabildiğinizi kontrol etmek için hangi düğüm türünün atandığını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-201">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="eb4b6-202">Veriler DOM 'a **PreserveWhitespace** bayrağıyla yüklendiğinde, boşluk için düğüm oluşturma denetlenir.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-202">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="eb4b6-203">Daha fazla bilgi için bkz. [Dom yüklenirken beyaz boşluk ve önemli boşluk işleme](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="eb4b6-203">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="eb4b6-204">DOM 'a yeni düğümler eklemek için bkz. [XML belgesine düğüm ekleme](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="eb4b6-204">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="eb4b6-205">DOM 'dan düğüm kaldırmak için bkz. [BIR XML belgesinden düğümleri, içeriği ve değerleri kaldırma](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="eb4b6-205">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="eb4b6-206">DOM 'daki düğümlerin içeriğini değiştirmek için bkz. [BIR XML belgesindeki düğümleri, içeriği ve değerleri değiştirme](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="eb4b6-206">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb4b6-207">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-207">See also</span></span>

- [<span data-ttu-id="eb4b6-208">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="eb4b6-208">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
