---
title: XmlSchemaCollection ile XML Şeması (XSD) Doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ad0b5717-3d32-41ad-a4d7-072c3e492b82
ms.openlocfilehash: 994153ba93848ebb120f23bdf6a979462a65142d
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159487"
---
# <a name="xml-schema-xsd-validation-with-xmlschemacollection"></a><span data-ttu-id="0d937-102">XmlSchemaCollection ile XML Şeması (XSD) Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="0d937-102">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>
<span data-ttu-id="0d937-103">XML şeması tanım dili <xref:System.Xml.Schema.XmlSchemaCollection> (xsd) şemalarında XML belgesini doğrulamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d937-103">You can use the <xref:System.Xml.Schema.XmlSchemaCollection> to validate an XML document against XML Schema definition language (XSD) schemas.</span></span> <span data-ttu-id="0d937-104">, <xref:System.Xml.Schema.XmlSchemaCollection> Şemaları, her doğrulama gerçekleştiğinde belleğe yüklenebilmeleri için, koleksiyonda depolayarak performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="0d937-104">The <xref:System.Xml.Schema.XmlSchemaCollection> improves performance by storing schemas in the collection so they are not loaded into memory each time validation occurs.</span></span> <span data-ttu-id="0d937-105">Şema, şema koleksiyonunda varsa, koleksiyonda şemayı aramak için `schemaLocation` özniteliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0d937-105">If the schema exists in the schema collection, the `schemaLocation` attribute is used to look up the schema in the collection.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0d937-106"><xref:System.Xml.Schema.XmlSchemaCollection> Sınıf artık kullanımdan kalkmıştır ve <xref:System.Xml.Schema.XmlSchemaSet> sınıfıyla değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0d937-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="0d937-107"><xref:System.Xml.Schema.XmlSchemaSet> Sınıf hakkında daha fazla bilgi için bkz. [şema derlemesi için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="0d937-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
 <span data-ttu-id="0d937-108">Aşağıdaki örnek, bir veri dosyasının kök öğesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d937-108">The following example shows the root element of a data file.</span></span>  
  
```xml  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"  
    xmlns="urn:bookstore-schema"  
    elementFormDefault="qualified"  
    targetNamespace="urn:bookstore-schema">  
```  
  
 <span data-ttu-id="0d937-109">Bu örnekte, `targetNamespace` özniteliğinin `urn:bookstore-schema`değeri, şemasına eklenirken kullanılan ad alanı olan. <xref:System.Xml.Schema.XmlSchemaCollection></span><span class="sxs-lookup"><span data-stu-id="0d937-109">For this example, the value of the `targetNamespace` attribute is `urn:bookstore-schema`, which is the same namespace that is used when adding the schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span>  
  
 <span data-ttu-id="0d937-110">Aşağıdaki kod örneği öğesine bir XML şeması ekler <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="0d937-110">The following code example adds an XML Schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span>  
  
```vb  
Dim xsc As New XmlSchemaCollection()  
' XML Schema.  
xsc.Add("urn:bookstore-schema", schema)
reader = New XmlTextReader(filename)  
vreader = New XmlValidatingReader(reader)  
vreader.Schemas.Add(xsc)  
```  
  
```csharp  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
// XML Schema.  
xsc.Add("urn:bookstore-schema", schema);  
reader = new XmlTextReader (filename);  
vreader = new XmlValidatingReader (reader);  
vreader.Schemas.Add(xsc);  
```  
  
 <span data-ttu-id="0d937-111">`targetNamespace` Özniteliği `namespaceURI` , <xref:System.Xml.Schema.XmlSchemaCollection>özelliği için <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemine eklediğinizde genellikle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0d937-111">The `targetNamespace` attribute is generally used when you add the `namespaceURI` property in the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method for the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span> <span data-ttu-id="0d937-112">Şemasını öğesine eklemeden önce bir null başvurusu belirtebilirsiniz <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="0d937-112">You can specify a null reference before adding the schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span> <span data-ttu-id="0d937-113">Boş bir dize ("") ad alanı olmayan şemalar için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d937-113">An empty string ("") should be used for schemas without a namespace.</span></span> <span data-ttu-id="0d937-114">, <xref:System.Xml.Schema.XmlSchemaCollection> Ad alanı olmayan yalnızca bir şemaya sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d937-114">The <xref:System.Xml.Schema.XmlSchemaCollection> can have only one schema without a namespace.</span></span>  
  
 <span data-ttu-id="0d937-115">Aşağıdaki kod örneği, bir XML şeması olan HeadCount. xsd öğesini öğesine ekler <xref:System.Xml.Schema.XmlSchemaCollection> ve Headcount. xml ' i doğrular.</span><span class="sxs-lookup"><span data-stu-id="0d937-115">The following code example adds an XML Schema, HeadCount.xsd, to the <xref:System.Xml.Schema.XmlSchemaCollection> and validates HeadCount.xml.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Schema  
  
Namespace ValidationSample  
  
   Class Sample  
  
      Public Shared Sub Main()  
         Dim tr As New XmlTextReader("HeadCount.xml")  
         Dim vr As New XmlValidatingReader(tr)  
  
         vr.Schemas.Add("xsdHeadCount", "HeadCount.xsd")  
         vr.ValidationType = ValidationType.Schema  
         AddHandler vr.ValidationEventHandler, AddressOf ValidationHandler  
  
         While vr.Read()  
         End While  
         Console.WriteLine("Validation finished")  
      End Sub  
      ' Main  
  
      Public Shared Sub ValidationHandler(sender As Object, args As ValidationEventArgs)  
         Console.WriteLine("***Validation error")  
         Console.WriteLine("Severity:{0}", args.Severity)  
         Console.WriteLine("Message:{0}", args.Message)  
      End Sub  
      ' ValidationHandler  
   End Class  
   ' Sample  
End Namespace  
' ValidationSample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Schema;  
  
namespace ValidationSample  
{  
   class Sample  
   {  
      public static void Main()  
      {  
         XmlTextReader tr = new XmlTextReader("HeadCount.xml");  
         XmlValidatingReader vr = new XmlValidatingReader(tr);  
  
         vr.Schemas.Add("xsdHeadCount", "HeadCount.xsd");  
         vr.ValidationType = ValidationType.Schema;  
         vr.ValidationEventHandler += new ValidationEventHandler (ValidationHandler);  
  
         while(vr.Read());  
         Console.WriteLine("Validation finished");  
      }  
  
      public static void ValidationHandler(object sender, ValidationEventArgs args)  
      {  
         Console.WriteLine("***Validation error");  
         Console.WriteLine("\tSeverity:{0}", args.Severity);  
         Console.WriteLine("\tMessage  :{0}", args.Message);  
      }  
   }  
}  
```  
  
 <span data-ttu-id="0d937-116">Aşağıda, doğrulama için HeadCount. xml giriş dosyasının içeriği özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0d937-116">The following outlines the contents of the input file, HeadCount.xml, to be validated.</span></span>  
  
```xml  
<!--Load HeadCount.xsd in SchemaCollection for Validation-->  
<hc:HeadCount xmlns:hc='xsdHeadCount'>  
   <Name>Waldo Pepper</Name>  
   <Name>Red Pepper</Name>  
</hc:HeadCount>  
```  
  
 <span data-ttu-id="0d937-117">Aşağıda, tarafından doğrulanacak olan HeadCount. xsd XML şema dosyasının içeriği özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0d937-117">The following outlines the contents of the XML Schema file, HeadCount.xsd, to be validated against.</span></span>  
  
```xml  
<xs:schema xmlns="xsdHeadCount" targetNamespace="xsdHeadCount" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name='HeadCount' type="HEADCOUNT"/>  
   <xs:complexType name="HEADCOUNT">  
      <xs:sequence>  
         <xs:element name='Name' type='xs:string' maxOccurs='unbounded'/>  
      </xs:sequence>  
      <xs:attribute name='division' type='xs:int' use='optional' default='8'/>  
   </xs:complexType>  
</xs:schema>  
```  
  
 <span data-ttu-id="0d937-118">Aşağıdaki kod örneği, alan oluşturur <xref:System.Xml.XmlValidatingReader> <xref:System.Xml.XmlTextReader>.</span><span class="sxs-lookup"><span data-stu-id="0d937-118">The following code example creates an <xref:System.Xml.XmlValidatingReader> that takes an <xref:System.Xml.XmlTextReader>.</span></span> <span data-ttu-id="0d937-119">Sample4. xml giriş dosyası, sample4. xsd XML şemasına göre onaylanır.</span><span class="sxs-lookup"><span data-stu-id="0d937-119">The input file, sample4.xml, is validated against the XML Schema, sample4.xsd.</span></span>  
  
```vb  
Dim tr As New XmlTextReader("sample4.xml")  
Dim vr As New XmlValidatingReader(tr)  
vr.ValidationType = ValidationType.Schema  
vr.Schemas.Add("datatypesTest", "sample4.xsd")  
AddHandler vr.ValidationEventHandler, AddressOf ValidationCallBack  
While vr.Read()  
   Console.WriteLine("NodeType: {0} NodeName: {1}", vr.NodeType, vr.Name)  
End While  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("sample4.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
vr.ValidationType = ValidationType.Schema;  
        vr.Schemas.Add("datatypesTest", "sample4.xsd");  
vr.ValidationEventHandler += new ValidationEventHandler(ValidationCallBack);  
while(vr.Read()) {  
    Console.WriteLine("NodeType: {0} NodeName: {1}", vr.NodeType, vr.Name);  
    }  
```  
  
 <span data-ttu-id="0d937-120">Aşağıda, doğrulanacak sample4. xml girdi dosyasının içeriği özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0d937-120">The following outlines the contents of the input file, sample4.xml, to be validated.</span></span>  
  
```xml  
<datatypes xmlns="datatypesTest">  
    <number>  
        <number_1>123</number_1>  
    </number>  
</datatypes>  
```  
  
 <span data-ttu-id="0d937-121">Aşağıda, sample4. xsd XML şema dosyasının içeriğine göre doğrulanacak olan içerikleri özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0d937-121">The following outlines the contents of the XML Schema file, sample4.xsd, to be validated against.</span></span>  
  
```xml  
<xs:schema
    xmlns:xs="http://www.w3.org/2001/XMLSchema"
    xmlns:tns="datatypesTest"
    targetNamespace="datatypesTest"  
    elementFormDefault="qualified">  
  
<xs:element name = "datatypes">  
  <xs:complexType>  
    <xs:all>  
        <xs:element name="number">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="number_1" type="xs:decimal" maxOccurs="unbounded"/>  
                </xs:sequence>  
            </xs:complexType>  
        </xs:element>  
    </xs:all>  
  </xs:complexType>  
</xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d937-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d937-122">See also</span></span>

- <xref:System.Xml.XmlParserContext>
- <xref:System.Xml.XmlValidatingReader.ValidationEventHandler?displayProperty=nameWithType>
- <xref:System.Xml.XmlValidatingReader.Schemas%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0d937-123">XmlSchemaCollection Şema Derlemesi</span><span class="sxs-lookup"><span data-stu-id="0d937-123">XmlSchemaCollection Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemacollection-schema-compilation.md)
