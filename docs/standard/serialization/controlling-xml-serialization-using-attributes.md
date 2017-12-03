---
title: "XML serileştirme özniteliklerini kullanarak denetleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, serializing
- XML serialization, examples
- derived classes, serializing
- arrays, serializing
- XML serialization, attributes
- preventing serialization
- attributes [.NET Framework], XML serialization
- serialization, examples
- serialization, attributes
ms.assetid: 47d4c39d-30e1-4c7b-8a2e-301325390647
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f90cf4e481d8ce8f5f34c3aaab3e544e37e1481
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="controlling-xml-serialization-using-attributes"></a><span data-ttu-id="1be24-102">XML serileştirme özniteliklerini kullanarak denetleme</span><span class="sxs-lookup"><span data-stu-id="1be24-102">Controlling XML Serialization Using Attributes</span></span>
<span data-ttu-id="1be24-103">Öznitelikler, nesnenin XML serileştirme kontrol etmek veya alternatif bir XML akışı sınıfları aynı kümesinden oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1be24-103">Attributes can be used to control the XML serialization of an object or to create an alternate XML stream from the same set of classes.</span></span> <span data-ttu-id="1be24-104">Alternatif bir XML akışı oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir diğer öğe adı için bir XML akışı belirtin](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span><span class="sxs-lookup"><span data-stu-id="1be24-104">For more details about creating an alternate XML stream, see [How to: Specify an Alternate Element Name for an XML Stream](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1be24-105">Oluşturulan XML "Basit Nesne Erişim Protokolü (SOAP) 1.1" başlıklı bölüme World Wide Web Konsorsiyumu (www.w3.org) belgenin 5 uymalıdır, listelenen öznitelikleri kullanın. [öznitelikleri, Denetim kodlanmış SOAP seri hale getirme](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="1be24-105">If the XML generated must conform to section 5 of the World Wide Web Consortium (www.w3.org) document titled "Simple Object Access Protocol (SOAP) 1.1," use the attributes listed in [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="1be24-106">Varsayılan olarak, bir XML öğesi adı, sınıf veya üye ada göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="1be24-106">By default, an XML element name is determined by the class or member name.</span></span> <span data-ttu-id="1be24-107">Adlı basit bir sınıf içinde `Book`, adında bir alan `ISBN` bir XML öğesi etiketi üretecektir \<ISBN >, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1be24-107">In a simple class named `Book`, a field named `ISBN` will produce an XML element tag \<ISBN>, as shown in the following example.</span></span>  
  
```vb  
Public Class Book  
    Public ISBN As String  
End Class  
' When an instance of the Book class is serialized, it might   
' produce this XML:  
' <ISBN>1234567890</ISBN>.  
```  
  
```csharp  
public class Book  
{  
    public string ISBN;  
}  
// When an instance of the Book class is serialized, it might   
// produce this XML:  
// <ISBN>1234567890</ISBN>.  
```  
  
 <span data-ttu-id="1be24-108">Öğe yeni bir ad verin istiyorsanız, bu varsayılan davranış değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1be24-108">This default behavior can be changed if you want to give the element a new name.</span></span> <span data-ttu-id="1be24-109">Aşağıdaki kod nasıl bir öznitelik bu ayarlayarak sağlar gösterir <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> özelliği bir <xref:System.Xml.Serialization.XmlElementAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1be24-109">The following code shows how an attribute enables this by setting the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> property of a <xref:System.Xml.Serialization.XmlElementAttribute>.</span></span>  
  
```vb  
Public Class TaxRates  
   < XmlElement(ElementName = "TaxRate")> _  
    Public ReturnTaxRate As Decimal  
End Class  
```  
  
```csharp  
public class TaxRates{  
    [XmlElement(ElementName = "TaxRate")]  
    public decimal ReturnTaxRate;  
}  
```  
  
 <span data-ttu-id="1be24-110">Öznitelikler hakkında daha fazla bilgi için bkz: [öznitelikleri](../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="1be24-110">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span> <span data-ttu-id="1be24-111">XML serileştirme denetim öznitelikleri listesi için bkz: [öznitelikleri, Denetim XML serileştirme](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="1be24-111">For a list of attributes that control XML serialization, see [Attributes That Control XML Serialization](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md).</span></span>  
  
## <a name="controlling-array-serialization"></a><span data-ttu-id="1be24-112">Dizi serileştirme denetleme</span><span class="sxs-lookup"><span data-stu-id="1be24-112">Controlling Array Serialization</span></span>  
 <span data-ttu-id="1be24-113"><xref:System.Xml.Serialization.XmlArrayAttribute> Ve <xref:System.Xml.Serialization.XmlArrayItemAttribute> öznitelikleri diziler serileştirmek denetlemek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1be24-113">The <xref:System.Xml.Serialization.XmlArrayAttribute> and the <xref:System.Xml.Serialization.XmlArrayItemAttribute> attributes are designed to control the serialization of arrays.</span></span> <span data-ttu-id="1be24-114">Bu öznitelikler kullanarak, ("XML Şeması bölümü 2: veri türleri" başlıklı World Wide Web Konsorsiyumu [www.w3.org] belgede tanımlanan) öğesi adını, ad alanı ve XML Şeması (XSD) veri türü denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1be24-114">Using these attributes, you can control the element name, namespace, and XML Schema (XSD) data type (as defined in the World Wide Web Consortium [www.w3.org] document titled "XML Schema Part 2: Datatypes").</span></span> <span data-ttu-id="1be24-115">Bir dizide dahil edilebilir türleri de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1be24-115">You can also specify the types that can be included in an array.</span></span>  
  
 <span data-ttu-id="1be24-116"><xref:System.Xml.Serialization.XmlArrayAttribute> Bir dizi serileştirilmiş olduğunda, kapsayan XML öğesi özelliklerini belirler.</span><span class="sxs-lookup"><span data-stu-id="1be24-116">The <xref:System.Xml.Serialization.XmlArrayAttribute> will determine the properties of the enclosing XML element that results when an array is serialized.</span></span> <span data-ttu-id="1be24-117">Örneğin, varsayılan olarak, aşağıdaki dizi serileştirmek adlı bir XML öğesi sonuçlanacak `Employees`.</span><span class="sxs-lookup"><span data-stu-id="1be24-117">For example, by default, serializing the array below will result in an XML element named `Employees`.</span></span> <span data-ttu-id="1be24-118">`Employees` Öğesi, bir dizi sonra dizi türü adlı öğeleri içerecek `Employee`.</span><span class="sxs-lookup"><span data-stu-id="1be24-118">The `Employees` element will contain a series of elements named after the array type `Employee`.</span></span>  
  
```vb  
Public Class Group  
    Public Employees() As Employee  
End Class  
Public Class Employee  
    Public Name As String  
End Class  
```  
  
```csharp  
public class Group{  
    public Employee[] Employees;  
}  
public class Employee{  
    public string Name;  
}  
```  
  
 <span data-ttu-id="1be24-119">Serileştirilmiş bir örnek şöyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="1be24-119">A serialized instance might resemble the following.</span></span>  
  
```xml  
<Group>  
<Employees>  
    <Employee>  
        <Name>Haley</Name>  
    </Employee>  
</Employees >  
</Group>  
```  
  
 <span data-ttu-id="1be24-120">Uygulayarak bir <xref:System.Xml.Serialization.XmlArrayAttribute>, XML öğesi adı aşağıdaki şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1be24-120">By applying a <xref:System.Xml.Serialization.XmlArrayAttribute>, you can change the name of the XML element, as follows.</span></span>  
  
```vb  
Public Class Group  
    <XmlArray("TeamMembers")> _  
    Public Employees() As Employee  
End Class  
```  
  
```csharp  
public class Group{  
    [XmlArray("TeamMembers")]  
    public Employee[] Employees;  
}  
```  
  
 <span data-ttu-id="1be24-121">Elde edilen XML aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="1be24-121">The resulting XML might resemble the following.</span></span>  
  
```xml  
<Group>  
<TeamMembers>  
    <Employee>  
        <Name>Haley</Name>  
    </Employee>  
</TeamMembers>  
```  
  
 <span data-ttu-id="1be24-122"><xref:System.Xml.Serialization.XmlArrayItemAttribute>, Diğer yandan dizisinde bulunan öğeleri nasıl serileştirilmiş denetler.</span><span class="sxs-lookup"><span data-stu-id="1be24-122">The <xref:System.Xml.Serialization.XmlArrayItemAttribute>, on the other hand, controls how the items contained in the array are serialized.</span></span> <span data-ttu-id="1be24-123">Öznitelik dizi dönerek alanın uygulandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1be24-123">Note that the attribute is applied to the field returning the array.</span></span>  
  
```vb  
Public Class Group  
    <XmlArrayItem("MemberName")> _  
    Public Employee() As Employees  
End Class  
```  
  
```csharp  
public class Group{  
    [XmlArrayItem("MemberName")]  
    public Employee[] Employees;  
}  
```  
  
 <span data-ttu-id="1be24-124">Elde edilen XML aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="1be24-124">The resulting XML might resemble the following.</span></span>  
  
```xml  
<Group>  
<Employees>  
    <MemberName>Haley</MemberName>  
</Employees>  
</Group>  
```  
  
## <a name="serializing-derived-classes"></a><span data-ttu-id="1be24-125">Türetilen sınıfların seri hale getirilmedi</span><span class="sxs-lookup"><span data-stu-id="1be24-125">Serializing Derived Classes</span></span>  
 <span data-ttu-id="1be24-126">Başka bir kullanımını <xref:System.Xml.Serialization.XmlArrayItemAttribute> türetilen sınıfların serileştirmek izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="1be24-126">Another use of the <xref:System.Xml.Serialization.XmlArrayItemAttribute> is to allow the serialization of derived classes.</span></span> <span data-ttu-id="1be24-127">Örneğin, adlı başka bir sınıf `Manager` , türetilen `Employee` önceki örneği eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1be24-127">For example, another class named `Manager` that derives from `Employee` can be added to the previous example.</span></span> <span data-ttu-id="1be24-128">Geçerli <xref:System.Xml.Serialization.XmlArrayItemAttribute>, türetilmiş sınıf türü tanınmıyor çünkü kod çalışma zamanında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="1be24-128">If you do not apply the <xref:System.Xml.Serialization.XmlArrayItemAttribute>, the code will fail at run time because the derived class type will not be recognized.</span></span> <span data-ttu-id="1be24-129">Bu sorunu gidermek için özniteliğini uygulayın iki kez, her zaman ayarı <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> her kabul edilebilir bir türü (temel ve türetilen) özelliği.</span><span class="sxs-lookup"><span data-stu-id="1be24-129">To remedy this, apply the attribute twice, each time setting the <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> property for each acceptable type (base and derived).</span></span>  
  
```vb  
Public Class Group  
    <XmlArrayItem(Type:=GetType(Employee)), _  
    XmlArrayItem(Type:=GetType(Manager))> _  
    Public Employees() As Employee  
End Class  
Public Class Employee  
    Public Name As String  
End Class  
Public Class Manager  
Inherits Employee  
    Public Level As Integer  
End Class  
```  
  
```csharp  
public class Group{  
    [XmlArrayItem(Type = typeof(Employee)),  
    XmlArrayItem(Type = typeof(Manager))]  
    public Employee[] Employees;  
}  
public class Employee{  
    public string Name;  
}  
public class Manager:Employee{  
    public int Level;  
}  
```  
  
 <span data-ttu-id="1be24-130">Serileştirilmiş bir örnek şöyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="1be24-130">A serialized instance might resemble the following.</span></span>  
  
```xml  
<Group>  
<Employees>  
    <Employee>  
        <Name>Haley</Name>  
    </Employee>  
    <Employee xsi:type = "Manager">  
        <Name>Ann</Name>  
        <Level>3</Level>  
    <Employee>  
</Employees >  
</Group>  
```  
  
## <a name="serializing-an-array-as-a-sequence-of-elements"></a><span data-ttu-id="1be24-131">Bir dizi öğeleri dizisi olarak seri hale getiriliyor.</span><span class="sxs-lookup"><span data-stu-id="1be24-131">Serializing an Array as a Sequence of Elements</span></span>  
 <span data-ttu-id="1be24-132">Uygulayarak düz dizisi XML öğesi olarak bir dizi serileştirebilen bir <xref:System.Xml.Serialization.XmlElementAttribute> alanına dizi gibi döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="1be24-132">You can also serialize an array as a flat sequence of XML elements by applying a <xref:System.Xml.Serialization.XmlElementAttribute> to the field returning the array as follows.</span></span>  
  
```vb  
Public Class Group  
    <XmlElement> _  
    Public Employees() As Employee  
End Class  
```  
  
```csharp  
public class Group{  
    [XmlElement]  
    public Employee[] Employees;  
}  
```  
  
 <span data-ttu-id="1be24-133">Serileştirilmiş bir örnek şöyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="1be24-133">A serialized instance might resemble the following.</span></span>  
  
```xml  
<Group>  
<Employees>  
    <Name>Haley</Name>  
</Employees>  
<Employees>  
    <Name>Noriko</Name>  
</Employees>  
<Employees>  
    <Name>Marco</Name>  
</Employees>  
</Group>  
```  
  
 <span data-ttu-id="1be24-134">İki XML akışlar ayırt etmek için başka bir yolu derlenmiş kodundan XML Şeması (XSD) belge dosyaları oluşturmak için XML şema tanımı aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="1be24-134">Another way to differentiate the two XML streams is to use the XML Schema Definition tool to generate the XML Schema (XSD) document files from the compiled code.</span></span> <span data-ttu-id="1be24-135">(Aracı'nı kullanma hakkında daha fazla ayrıntı için bkz: [XML şema tanımı aracı ve XML serileştirme](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md).) Hiçbir öznitelik alana uygulandığında, şema öğesi aşağıdaki şekilde açıklar.</span><span class="sxs-lookup"><span data-stu-id="1be24-135">(For more details on using the tool, see [The XML Schema Definition Tool and XML Serialization](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md).) When no attribute is applied to the field, the schema describes the element in the following manner.</span></span>  
  
```xml  
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />  
```  
  
 <span data-ttu-id="1be24-136">Zaman <xref:System.Xml.Serialization.XmlElementAttribute> uygulandığı öğe elde edilen şema alanına, aşağıdaki şekilde açıklar.</span><span class="sxs-lookup"><span data-stu-id="1be24-136">When the <xref:System.Xml.Serialization.XmlElementAttribute> is applied to the field, the resulting schema describes the element as follows.</span></span>  
  
```xml  
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" />   
```  
  
## <a name="serializing-an-arraylist"></a><span data-ttu-id="1be24-137">ArrayList seri hale getirilmedi</span><span class="sxs-lookup"><span data-stu-id="1be24-137">Serializing an ArrayList</span></span>  
 <span data-ttu-id="1be24-138"><xref:System.Collections.ArrayList> Sınıfı, farklı nesnelerinin bir koleksiyonu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1be24-138">The <xref:System.Collections.ArrayList> class can contain a collection of diverse objects.</span></span> <span data-ttu-id="1be24-139">Bu nedenle kullanabileceğiniz bir <xref:System.Collections.ArrayList> kadar bir dizi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1be24-139">You can therefore use a <xref:System.Collections.ArrayList> much as you use an array.</span></span> <span data-ttu-id="1be24-140">Yazılan nesnelerin bir dizi döndürür bir alan oluşturmak yerine, ancak, tek bir döndüren bir alan oluşturabileceğiniz <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="1be24-140">Instead of creating a field that returns an array of typed objects, however, you can create a field that returns a single <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="1be24-141">Ancak, dizilerle gibi sizi bilgilendirmek gerekir <xref:System.Xml.Serialization.XmlSerializer> nesneleri türlerinin <xref:System.Collections.ArrayList> içerir.</span><span class="sxs-lookup"><span data-stu-id="1be24-141">However, as with arrays, you must inform the <xref:System.Xml.Serialization.XmlSerializer> of the types of objects the <xref:System.Collections.ArrayList> contains.</span></span> <span data-ttu-id="1be24-142">Bunu gerçekleştirmek için birden çok örneğinin atamak <xref:System.Xml.Serialization.XmlElementAttribute> alanına, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1be24-142">To accomplish this, assign multiple instances of the <xref:System.Xml.Serialization.XmlElementAttribute> to the field, as shown in the following example.</span></span>  
  
```vb  
Public Class Group  
    <XmlElement(Type:=GetType(Employee)), _  
    XmlElement(Type:=GetType(Manager))> _  
    Public Info As ArrayList  
End Class  
```  
  
```csharp  
public class Group{  
    [XmlElement(Type = typeof(Employee)),   
    XmlElement(Type = typeof(Manager))]  
    public ArrayList Info;  
}  
```  
  
## <a name="controlling-serialization-of-classes-using-xmlrootattribute-and-xmltypeattribute"></a><span data-ttu-id="1be24-143">Seri hale getirme XmlRootAttribute ve XmlTypeAttribute kullanarak sınıfların denetleme</span><span class="sxs-lookup"><span data-stu-id="1be24-143">Controlling Serialization of Classes Using XmlRootAttribute and XmlTypeAttribute</span></span>  
 <span data-ttu-id="1be24-144">Bir sınıf (ve yalnızca bir sınıf) uygulanabilir iki öznitelik: <xref:System.Xml.Serialization.XmlRootAttribute> ve <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1be24-144">There are two attributes that can be applied to a class (and only a class): <xref:System.Xml.Serialization.XmlRootAttribute> and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span> <span data-ttu-id="1be24-145">Bu öznitelikler çok benzer.</span><span class="sxs-lookup"><span data-stu-id="1be24-145">These attributes are very similar.</span></span> <span data-ttu-id="1be24-146"><xref:System.Xml.Serialization.XmlRootAttribute> İçin yalnızca bir sınıf uygulanabilir: sınıf serileştirilmiş olduğunda, temsil eder XML belgesi açma kapatma ve, öğe — diğer bir deyişle, kök öğe.</span><span class="sxs-lookup"><span data-stu-id="1be24-146">The <xref:System.Xml.Serialization.XmlRootAttribute> can be applied to only one class: the class that, when serialized, represents the XML document's opening and closing element—in other words, the root element.</span></span> <span data-ttu-id="1be24-147"><xref:System.Xml.Serialization.XmlTypeAttribute>, Diğer el, kök sınıfı dahil olmak üzere herhangi bir sınıf uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1be24-147">The <xref:System.Xml.Serialization.XmlTypeAttribute>, on the other hand, can be applied to any class, including the root class.</span></span>  
  
 <span data-ttu-id="1be24-148">Örneğin, önceki örneklerde, `Group` kök sınıfı ve tüm genel alanlar ve Özellikler XML belgesinde bulunan XML öğelerine haline gelir.</span><span class="sxs-lookup"><span data-stu-id="1be24-148">For example, in the previous examples, the `Group` class is the root class, and all its public fields and properties become the XML elements found in the XML document.</span></span> <span data-ttu-id="1be24-149">Bu nedenle, yalnızca bir kök sınıfı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1be24-149">Therefore, there can be only one root class.</span></span> <span data-ttu-id="1be24-150">Uygulayarak <xref:System.Xml.Serialization.XmlRootAttribute>, tarafından oluşturulan XML akışı denetleyebilirsiniz <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1be24-150">By applying the <xref:System.Xml.Serialization.XmlRootAttribute>, you can control the XML stream generated by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="1be24-151">Örneğin, ad alanı ve öğe adını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1be24-151">For example, you can change the element name and namespace.</span></span>  
  
 <span data-ttu-id="1be24-152"><xref:System.Xml.Serialization.XmlTypeAttribute> Oluşturulan XML Şeması denetlemenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="1be24-152">The <xref:System.Xml.Serialization.XmlTypeAttribute> allows you to control the schema of the generated XML.</span></span> <span data-ttu-id="1be24-153">Bu yetenek şeması XML Web hizmeti aracılığıyla yayımlamak gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="1be24-153">This capability is useful when you need to publish the schema through an XML Web service.</span></span> <span data-ttu-id="1be24-154">Aşağıdaki örnekte, her ikisi de uygulanır <xref:System.Xml.Serialization.XmlTypeAttribute> ve <xref:System.Xml.Serialization.XmlRootAttribute> aynı sınıfa.</span><span class="sxs-lookup"><span data-stu-id="1be24-154">The following example applies both the <xref:System.Xml.Serialization.XmlTypeAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the same class.</span></span>  
  
```vb  
<XmlRoot("NewGroupName"), _  
XmlType("NewTypeName")> _  
Public Class Group  
    Public Employees() As Employee  
End Class  
```  
  
```csharp  
[XmlRoot("NewGroupName")]  
[XmlType("NewTypeName")]  
public class Group{  
    public Employee[] Employees;  
}  
```  
  
 <span data-ttu-id="1be24-155">Bu sınıf derlenmiş ve XML şema tanımı aracı şemasına üretmek için kullanılan, aşağıdaki açıklayan XML bulur `Group`.</span><span class="sxs-lookup"><span data-stu-id="1be24-155">If this class is compiled, and the XML Schema Definition tool is used to generate its schema, you would find the following XML describing `Group`.</span></span>  
  
```xml  
<xs:element name="NewGroupName" type="NewTypeName">  
```  
  
 <span data-ttu-id="1be24-156">Buna karşılık, sınıfının bir örneği, yalnızca serileştirme olsaydı `NewGroupName` XML belgesinde bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="1be24-156">In contrast, if you were to serialize an instance of the class, only `NewGroupName` would be found in the XML document.</span></span>  
  
```xml  
<NewGroupName>  
    . . .  
</NewGroupName>  
```  
  
## <a name="preventing-serialization-with-the-xmlignoreattribute"></a><span data-ttu-id="1be24-157">Seri hale getirme XmlIgnoreAttribute ile önleme</span><span class="sxs-lookup"><span data-stu-id="1be24-157">Preventing Serialization with the XmlIgnoreAttribute</span></span>  
 <span data-ttu-id="1be24-158">Ortak özelliği olduğunda durumlar olabilir veya alan seri hale gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1be24-158">There might be situations when a public property or field does not need to be serialized.</span></span> <span data-ttu-id="1be24-159">Örneğin, bir alan veya özellik meta veriler içeren için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1be24-159">For example, a field or property could be used to contain metadata.</span></span> <span data-ttu-id="1be24-160">Böyle durumlarda, uygulama <xref:System.Xml.Serialization.XmlIgnoreAttribute> alanı veya özelliği için ve <xref:System.Xml.Serialization.XmlSerializer> üzerine atlar.</span><span class="sxs-lookup"><span data-stu-id="1be24-160">In such cases, apply the <xref:System.Xml.Serialization.XmlIgnoreAttribute> to the field or property and the <xref:System.Xml.Serialization.XmlSerializer> will skip over it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1be24-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1be24-161">See Also</span></span>  
 [<span data-ttu-id="1be24-162">XML serileştirme denetim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="1be24-162">Attributes That Control XML Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 [<span data-ttu-id="1be24-163">Kodlanmış SOAP serileştirme denetim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="1be24-163">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 [<span data-ttu-id="1be24-164">Giriş XML serileştirme</span><span class="sxs-lookup"><span data-stu-id="1be24-164">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="1be24-165">XML serileştirme örnekleri</span><span class="sxs-lookup"><span data-stu-id="1be24-165">Examples of XML Serialization</span></span>](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 [<span data-ttu-id="1be24-166">Nasıl yapılır: bir XML akışı için bir diğer öğe adı belirtin</span><span class="sxs-lookup"><span data-stu-id="1be24-166">How to: Specify an Alternate Element Name for an XML Stream</span></span>](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 [<span data-ttu-id="1be24-167">Nasıl yapılır: bir nesneyi serileştirme</span><span class="sxs-lookup"><span data-stu-id="1be24-167">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="1be24-168">Nasıl yapılır: bir nesne seri durumdan</span><span class="sxs-lookup"><span data-stu-id="1be24-168">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
