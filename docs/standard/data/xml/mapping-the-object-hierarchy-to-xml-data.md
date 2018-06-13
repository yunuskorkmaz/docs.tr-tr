---
title: XML verilerine nesne hiyerarşisi eşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45f39701d409ba76e3c3f428f484b6fd5e538fbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577208"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="fd5b5-102">XML verilerine nesne hiyerarşisi eşleme</span><span class="sxs-lookup"><span data-stu-id="fd5b5-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="fd5b5-103">Bir XML belgesi bellekte kavramsal temsili bir ağaç olur.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="fd5b5-104">Programlama için ağaç düğümleri erişmek için bir nesne hiyerarşisi vardır.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="fd5b5-105">Aşağıdaki örnekte nasıl XML içeriği düğümleri duruma gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="fd5b5-106">XML XML belge nesne modeli (DOM) içine okurken parçaları düğümlerin içine dönüştürülür ve bu düğümler, düğüm türü ve değerleri gibi kendileri hakkında ek meta veriler korumak.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="fd5b5-107">Düğüm türü, nesne ve hangi eylemleri gerçekleştirilebilir belirler ve hangi özelliklerin ayarlayın veya alınır.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="fd5b5-108">Aşağıdaki basit XML varsa:</span><span class="sxs-lookup"><span data-stu-id="fd5b5-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="fd5b5-109">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="fd5b5-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="fd5b5-110">Giriş bellekte atanan düğüm türü özelliği aşağıdaki düğüm ağacıyla olarak temsil edilir:</span><span class="sxs-lookup"><span data-stu-id="fd5b5-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="fd5b5-111">![örnek düğüm ağacı](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="fd5b5-111">![example node tree](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="fd5b5-112">Kitap ve başlık düğümü ağaç gösterimi</span><span class="sxs-lookup"><span data-stu-id="fd5b5-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="fd5b5-113">`book` Öğe haline gelir bir **XmlElement** nesnesi, sonraki öğeye `title`, haline bir **XmlElement**, öğe içeriği olurken bir **XmlText** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="fd5b5-114">Bakarak içinde **XmlElement** yöntemleri ve özellikleri, yöntemleri ve özellikleri yöntemleri ve özellikleri kullanılabilir farklı bir **XmlText** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="fd5b5-115">Bu nedenle gerçekleştirilecek eylemler düğüm türünü belirleyen XML Biçimlendirme hale hangi düğüm türü önemlidir bilerek.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="fd5b5-116">Aşağıdaki örnekte, XML verileri okur ve düğüm türüne bağlı olarak farklı bir metin çıkışı yazar.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="fd5b5-117">Girdi olarak şu XML veri dosyası kullanarak **items.xml**:</span><span class="sxs-lookup"><span data-stu-id="fd5b5-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="fd5b5-118">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="fd5b5-118">**Input**</span></span>  
  
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
  
 <span data-ttu-id="fd5b5-119">Aşağıdaki kod örneği okuma **items.xml** dosya ve her düğüm türünün bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
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
  
 <span data-ttu-id="fd5b5-120">Örneğin çıktısını düğüm türleri için verilerin eşleşmesini ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="fd5b5-121">**Output**</span><span class="sxs-lookup"><span data-stu-id="fd5b5-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 <span data-ttu-id="fd5b5-122">Aynı anda tek bir giriş çizgi alma ve koddan oluşturulan çıktı kullanarak, böylece XML verileri ne tür bir düğüm türü hale geldiğini anlamak hangi düğümü test çıkışı, hangi satırların üretilen çözümlemek için aşağıdaki tabloda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="fd5b5-123">Giriş</span><span class="sxs-lookup"><span data-stu-id="fd5b5-123">Input</span></span>|<span data-ttu-id="fd5b5-124">Çıkış</span><span class="sxs-lookup"><span data-stu-id="fd5b5-124">Output</span></span>|<span data-ttu-id="fd5b5-125">Düğüm türü sınaması</span><span class="sxs-lookup"><span data-stu-id="fd5b5-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|<span data-ttu-id="fd5b5-126">\<? xml version = "1.0"? ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-126">\<?xml version="1.0"?></span></span>|<span data-ttu-id="fd5b5-127">\<? xml sürümü ='1.0 '? ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-127">\<?xml version='1.0'?></span></span>|<span data-ttu-id="fd5b5-128">XmlNodeType.XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="fd5b5-128">XmlNodeType.XmlDeclaration</span></span>|  
|<span data-ttu-id="fd5b5-129">\<!--Örnek bir XML belgesi budur--></span><span class="sxs-lookup"><span data-stu-id="fd5b5-129">\<!-- This is a sample XML document --></span></span>|<span data-ttu-id="fd5b5-130">\<!--Örnek bir XML belgesi budur--></span><span class="sxs-lookup"><span data-stu-id="fd5b5-130">\<!--This is a sample XML document --></span></span>|<span data-ttu-id="fd5b5-131">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="fd5b5-131">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="fd5b5-132">\<! DOCTYPE öğeleri [\<! Varlık numarası "123" >] ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="fd5b5-133">\<! DOCTYPE öğeleri [\<! Varlık numarası "123" >]</span><span class="sxs-lookup"><span data-stu-id="fd5b5-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="fd5b5-134">XmlNodeType.DocumentType</span><span class="sxs-lookup"><span data-stu-id="fd5b5-134">XmlNodeType.DocumentType</span></span>|  
|<span data-ttu-id="fd5b5-135">\<Öğeleri ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-135">\<Items></span></span>|<span data-ttu-id="fd5b5-136">\<Öğeleri ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-136">\<Items></span></span>|<span data-ttu-id="fd5b5-137">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="fd5b5-137">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="fd5b5-138">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-138">\<Item></span></span>|<span data-ttu-id="fd5b5-139">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-139">\<Item></span></span>|<span data-ttu-id="fd5b5-140">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="fd5b5-140">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="fd5b5-141">Bir varlık ile test edin: &number;</span><span class="sxs-lookup"><span data-stu-id="fd5b5-141">Test with an entity: &number;</span></span>|<span data-ttu-id="fd5b5-142">Bir varlığı olan test: 123</span><span class="sxs-lookup"><span data-stu-id="fd5b5-142">Test with an entity: 123</span></span>|<span data-ttu-id="fd5b5-143">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="fd5b5-143">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="fd5b5-144">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-144">\</Item></span></span>|<span data-ttu-id="fd5b5-145">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-145">\</Item></span></span>|<span data-ttu-id="fd5b5-146">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="fd5b5-146">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="fd5b5-147">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-147">\<Item></span></span>|<span data-ttu-id="fd5b5-148">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-148">\<Item></span></span>|<span data-ttu-id="fd5b5-149">XmNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="fd5b5-149">XmNodeType.Element</span></span>|  
|<span data-ttu-id="fd5b5-150">bir alt öğesi ile test</span><span class="sxs-lookup"><span data-stu-id="fd5b5-150">test with a child element</span></span>|<span data-ttu-id="fd5b5-151">bir alt öğesi ile test</span><span class="sxs-lookup"><span data-stu-id="fd5b5-151">test with a child element</span></span>|<span data-ttu-id="fd5b5-152">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="fd5b5-152">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="fd5b5-153">\<Daha fazla ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-153">\<more></span></span>|<span data-ttu-id="fd5b5-154">\<Daha fazla ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-154">\<more></span></span>|<span data-ttu-id="fd5b5-155">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="fd5b5-155">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="fd5b5-156">Hizmetler</span><span class="sxs-lookup"><span data-stu-id="fd5b5-156">stuff</span></span>|<span data-ttu-id="fd5b5-157">Hizmetler</span><span class="sxs-lookup"><span data-stu-id="fd5b5-157">stuff</span></span>|<span data-ttu-id="fd5b5-158">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="fd5b5-158">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="fd5b5-159">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-159">\</Item></span></span>|<span data-ttu-id="fd5b5-160">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-160">\</Item></span></span>|<span data-ttu-id="fd5b5-161">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="fd5b5-161">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="fd5b5-162">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-162">\<Item></span></span>|<span data-ttu-id="fd5b5-163">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-163">\<Item></span></span>|<span data-ttu-id="fd5b5-164">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="fd5b5-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="fd5b5-165">CDATA bölümü ile test</span><span class="sxs-lookup"><span data-stu-id="fd5b5-165">test with a CDATA section</span></span>|<span data-ttu-id="fd5b5-166">CDATA bölümü ile test</span><span class="sxs-lookup"><span data-stu-id="fd5b5-166">test with a CDATA section</span></span>|<span data-ttu-id="fd5b5-167">XmlTest.Text</span><span class="sxs-lookup"><span data-stu-id="fd5b5-167">XmlTest.Text</span></span>|  
|<span data-ttu-id="fd5b5-168">&LT;! [CDATA [\<456 &GT;]]\></span><span class="sxs-lookup"><span data-stu-id="fd5b5-168"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="fd5b5-169">&LT;! [CDATA [\<456 &GT;]]\></span><span class="sxs-lookup"><span data-stu-id="fd5b5-169"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="fd5b5-170">XmlTest.CDATA</span><span class="sxs-lookup"><span data-stu-id="fd5b5-170">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="fd5b5-171">def</span><span class="sxs-lookup"><span data-stu-id="fd5b5-171">def</span></span>|<span data-ttu-id="fd5b5-172">def</span><span class="sxs-lookup"><span data-stu-id="fd5b5-172">def</span></span>|<span data-ttu-id="fd5b5-173">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="fd5b5-173">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="fd5b5-174">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-174">\</Item></span></span>|<span data-ttu-id="fd5b5-175">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-175">\</Item></span></span>|<span data-ttu-id="fd5b5-176">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="fd5b5-176">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="fd5b5-177">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-177">\<Item></span></span>|<span data-ttu-id="fd5b5-178">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-178">\<Item></span></span>|<span data-ttu-id="fd5b5-179">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="fd5b5-179">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="fd5b5-180">Char varlığı ile test: &\#65;</span><span class="sxs-lookup"><span data-stu-id="fd5b5-180">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="fd5b5-181">Char varlığı ile test: A</span><span class="sxs-lookup"><span data-stu-id="fd5b5-181">Test with a char entity: A</span></span>|<span data-ttu-id="fd5b5-182">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="fd5b5-182">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="fd5b5-183">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-183">\</Item></span></span>|<span data-ttu-id="fd5b5-184">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-184">\</Item></span></span>|<span data-ttu-id="fd5b5-185">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="fd5b5-185">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="fd5b5-186">\<!----> On dört karakter bu öğesi.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-186">\<!-- Fourteen chars in this element.--></span></span>|<span data-ttu-id="fd5b5-187">\<--Bu öğe. on dört karakter--></span><span class="sxs-lookup"><span data-stu-id="fd5b5-187">\<--Fourteen chars in this element.--></span></span>|<span data-ttu-id="fd5b5-188">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="fd5b5-188">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="fd5b5-189">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-189">\<Item></span></span>|<span data-ttu-id="fd5b5-190">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-190">\<Item></span></span>|<span data-ttu-id="fd5b5-191">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="fd5b5-191">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="fd5b5-192">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="fd5b5-192">1234567890ABCD</span></span>|<span data-ttu-id="fd5b5-193">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="fd5b5-193">1234567890ABCD</span></span>|<span data-ttu-id="fd5b5-194">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="fd5b5-194">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="fd5b5-195">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-195">\</Item></span></span>|<span data-ttu-id="fd5b5-196">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-196">\</Item></span></span>|<span data-ttu-id="fd5b5-197">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="fd5b5-197">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="fd5b5-198">\</ Öğeleri ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-198">\</Items></span></span>|<span data-ttu-id="fd5b5-199">\</ Öğeleri ></span><span class="sxs-lookup"><span data-stu-id="fd5b5-199">\</Items></span></span>|<span data-ttu-id="fd5b5-200">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="fd5b5-200">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="fd5b5-201">Düğüm türü atanmış bilmeniz gerekir, hangi tür Eylemler geçerli olduğunu ve ne tür bir ayarlamak ve almak özellikleri düğüm olarak türü denetler.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-201">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="fd5b5-202">Boşluk düğüm oluşturma, veri tarafından DOM içine yüklendiğinde denetlenir **PreserveWhitespace** bayrağı.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-202">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="fd5b5-203">Daha fazla bilgi için bkz: [boşluk ve önemli boşluk DOM yüklenirken işleme](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="fd5b5-203">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="fd5b5-204">DOM yeni düğümler eklemek için bkz: [ekleme düğümlerin bir XML belgesi içine](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="fd5b5-204">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="fd5b5-205">DOM düğümleri kaldırmak için bkz: [düğümleri kaldırma, içerik ve bir XML belgesi değerlerinden](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="fd5b5-205">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="fd5b5-206">DOM düğümler içeriğini değiştirmek için bkz: [değiştirme düğümleri, içerik ve bir XML belgesi değerleri](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="fd5b5-206">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd5b5-207">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd5b5-207">See Also</span></span>  
 [<span data-ttu-id="fd5b5-208">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="fd5b5-208">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
