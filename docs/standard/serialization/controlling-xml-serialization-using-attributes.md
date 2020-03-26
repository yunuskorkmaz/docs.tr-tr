---
title: Öznitelikleri Kullanarak XML Serileştirmeyi Denetleme
ms.date: 03/30/2017
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
ms.openlocfilehash: e11152dc626b1e3619b9ecbc04d8a237ca9f13d3
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248049"
---
# <a name="controlling-xml-serialization-using-attributes"></a><span data-ttu-id="61638-102">Öznitelikleri Kullanarak XML Serileştirmeyi Denetleme</span><span class="sxs-lookup"><span data-stu-id="61638-102">Controlling XML Serialization Using Attributes</span></span>

<span data-ttu-id="61638-103">Öznitelikler, bir nesnenin XML serileştirmesini denetlemek veya aynı sınıf kümesinden alternatif bir XML akışı oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="61638-103">Attributes can be used to control the XML serialization of an object or to create an alternate XML stream from the same set of classes.</span></span> <span data-ttu-id="61638-104">Alternatif bir XML akışı oluşturma hakkında daha fazla bilgi için [bkz: XML Akışı için Alternatif Öğe Adı belirtin.](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)</span><span class="sxs-lookup"><span data-stu-id="61638-104">For more details about creating an alternate XML stream, see [How to: Specify an Alternate Element Name for an XML Stream](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span></span>

> [!NOTE]
> <span data-ttu-id="61638-105">Oluşturulan XML, World Wide Web Konsorsiyumu (W3C) basit [nesne erişim protokolü (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)başlıklı belgenin bölüm 5'e uygun olması gerekiyorsa, [Kodlanmış SOAP Serileştirmeyi Kontrol Eden Özniteliklerde](attributes-that-control-encoded-soap-serialization.md)listelenen öznitelikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="61638-105">If the XML generated must conform to section 5 of the World Wide Web Consortium (W3C) document titled [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), use the attributes listed in [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>

<span data-ttu-id="61638-106">Varsayılan olarak, bir XML öğesi adı, sınıf veya üye ada göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="61638-106">By default, an XML element name is determined by the class or member name.</span></span> <span data-ttu-id="61638-107">Adlı `Book`basit bir sınıfta , `ISBN` adlı bir alan \<aşağıdaki örnekte gösterildiği gibi, bir XML eleman etiketi ISBN> üretecektir.</span><span class="sxs-lookup"><span data-stu-id="61638-107">In a simple class named `Book`, a field named `ISBN` will produce an XML element tag \<ISBN>, as shown in the following example.</span></span>

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

<span data-ttu-id="61638-108">Öğe yeni bir ad verin istiyorsanız, bu varsayılan davranış değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="61638-108">This default behavior can be changed if you want to give the element a new name.</span></span> <span data-ttu-id="61638-109">Aşağıdaki kod, bir özniteliğin özelliğini <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> ayarlayarak <xref:System.Xml.Serialization.XmlElementAttribute>bunu nasıl etkinleştirdığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="61638-109">The following code shows how an attribute enables this by setting the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> property of a <xref:System.Xml.Serialization.XmlElementAttribute>.</span></span>

```vb
Public Class TaxRates
   < XmlElement(ElementName = "TaxRate")> _
    Public ReturnTaxRate As Decimal
End Class
```

```csharp
public class TaxRates {
    [XmlElement(ElementName = "TaxRate")]
    public decimal ReturnTaxRate;
}
```

<span data-ttu-id="61638-110">Öznitelikler hakkında daha fazla bilgi için [bkz.](../../../docs/standard/attributes/index.md)</span><span class="sxs-lookup"><span data-stu-id="61638-110">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span> <span data-ttu-id="61638-111">XML serileştirmeyi denetleyen özniteliklerin listesi için Bkz. [XML Serileştirmeyi Denetleyen Öznitelikler.](attributes-that-control-xml-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="61638-111">For a list of attributes that control XML serialization, see [Attributes That Control XML Serialization](attributes-that-control-xml-serialization.md).</span></span>

## <a name="controlling-array-serialization"></a><span data-ttu-id="61638-112">Dizi Serileştirmeyi Denetleme</span><span class="sxs-lookup"><span data-stu-id="61638-112">Controlling Array Serialization</span></span>

<span data-ttu-id="61638-113">Ve <xref:System.Xml.Serialization.XmlArrayAttribute> <xref:System.Xml.Serialization.XmlArrayItemAttribute> öznitelikleri dizilerin serileştirme denetlemek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="61638-113">The <xref:System.Xml.Serialization.XmlArrayAttribute> and the <xref:System.Xml.Serialization.XmlArrayItemAttribute> attributes are designed to control the serialization of arrays.</span></span> <span data-ttu-id="61638-114">Bu öznitelikleri kullanarak, öğe adı, ad alanı ve XML Şema (XSD) veri türünü (World Wide Web Konsorsiyumu [www.w3.org] belgede tanımlandığı gibi "XML Şema Bölüm 2: Veri Türleri" başlıklı denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61638-114">Using these attributes, you can control the element name, namespace, and XML Schema (XSD) data type (as defined in the World Wide Web Consortium [www.w3.org] document titled "XML Schema Part 2: Datatypes").</span></span> <span data-ttu-id="61638-115">Bir dizide dahil edilebilir türleri de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61638-115">You can also specify the types that can be included in an array.</span></span>

<span data-ttu-id="61638-116"><xref:System.Xml.Serialization.XmlArrayAttribute> Bir dizi serileştirilmiş olduğunda, kapsayan XML öğesi özelliklerini belirler.</span><span class="sxs-lookup"><span data-stu-id="61638-116">The <xref:System.Xml.Serialization.XmlArrayAttribute> will determine the properties of the enclosing XML element that results when an array is serialized.</span></span> <span data-ttu-id="61638-117">Örneğin, varsayılan olarak, aşağıdaki dizi serileştirmek adlı bir XML öğesi sonuçlanacak `Employees`.</span><span class="sxs-lookup"><span data-stu-id="61638-117">For example, by default, serializing the array below will result in an XML element named `Employees`.</span></span> <span data-ttu-id="61638-118">`Employees` Öğesi, bir dizi sonra dizi türü adlı öğeleri içerecek `Employee`.</span><span class="sxs-lookup"><span data-stu-id="61638-118">The `Employees` element will contain a series of elements named after the array type `Employee`.</span></span>

```vb
Public Class Group
    Public Employees() As Employee
End Class
Public Class Employee
    Public Name As String
End Class
```

```csharp
public class Group {
    public Employee[] Employees;
}
public class Employee {
    public string Name;
}
```

<span data-ttu-id="61638-119">Serileştirilmiş bir örnek şöyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="61638-119">A serialized instance might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</Employees>
</Group>
```

<span data-ttu-id="61638-120">Uygulayarak bir <xref:System.Xml.Serialization.XmlArrayAttribute>, XML öğesi adı aşağıdaki şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61638-120">By applying a <xref:System.Xml.Serialization.XmlArrayAttribute>, you can change the name of the XML element, as follows.</span></span>

```vb
Public Class Group
    <XmlArray("TeamMembers")> _
    Public Employees() As Employee
End Class
```

```csharp
public class Group {
    [XmlArray("TeamMembers")]
    public Employee[] Employees;
}
```

<span data-ttu-id="61638-121">Elde edilen XML aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="61638-121">The resulting XML might resemble the following.</span></span>

```xml
<Group>
<TeamMembers>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</TeamMembers>
</Group>
```

<span data-ttu-id="61638-122">Diğer <xref:System.Xml.Serialization.XmlArrayItemAttribute>taraftan, dizide bulunan öğelerin nasıl seri hale getirilmiş olduğunu denetler.</span><span class="sxs-lookup"><span data-stu-id="61638-122">The <xref:System.Xml.Serialization.XmlArrayItemAttribute>, on the other hand, controls how the items contained in the array are serialized.</span></span> <span data-ttu-id="61638-123">Özniteliğin diziyi döndüren alana uygulandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="61638-123">Note that the attribute is applied to the field returning the array.</span></span>

```vb
Public Class Group
    <XmlArrayItem("MemberName")> _
    Public Employee() As Employees
End Class
```

```csharp
public class Group {
    [XmlArrayItem("MemberName")]
    public Employee[] Employees;
}
```

<span data-ttu-id="61638-124">Elde edilen XML aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="61638-124">The resulting XML might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <MemberName>Haley</MemberName>
</Employees>
</Group>
```

## <a name="serializing-derived-classes"></a><span data-ttu-id="61638-125">Türetilen sınıfların seri hale getirilmedi</span><span class="sxs-lookup"><span data-stu-id="61638-125">Serializing Derived Classes</span></span>

<span data-ttu-id="61638-126">Başka bir kullanımını <xref:System.Xml.Serialization.XmlArrayItemAttribute> türetilen sınıfların serileştirmek izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="61638-126">Another use of the <xref:System.Xml.Serialization.XmlArrayItemAttribute> is to allow the serialization of derived classes.</span></span> <span data-ttu-id="61638-127">Örneğin, adlı başka bir sınıf `Manager` , türetilen `Employee` önceki örneği eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="61638-127">For example, another class named `Manager` that derives from `Employee` can be added to the previous example.</span></span> <span data-ttu-id="61638-128">Geçerli <xref:System.Xml.Serialization.XmlArrayItemAttribute>, türetilmiş sınıf türü tanınmıyor çünkü kod çalışma zamanında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="61638-128">If you do not apply the <xref:System.Xml.Serialization.XmlArrayItemAttribute>, the code will fail at run time because the derived class type will not be recognized.</span></span> <span data-ttu-id="61638-129">Bunu gidermek için, özniteliği her kabul <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> edilebilir tür (taban ve türetilmiş) için her zaman ayarlayarak iki kez uygulayın.</span><span class="sxs-lookup"><span data-stu-id="61638-129">To remedy this, apply the attribute twice, each time setting the <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> property for each acceptable type (base and derived).</span></span>

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
public class Group {
    [XmlArrayItem(Type = typeof(Employee)),
    XmlArrayItem(Type = typeof(Manager))]
    public Employee[] Employees;
}
public class Employee {
    public string Name;
}
public class Manager:Employee {
    public int Level;
}
```

<span data-ttu-id="61638-130">Serileştirilmiş bir örnek şöyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="61638-130">A serialized instance might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
    <Employee xsi:type = "Manager">
        <Name>Ann</Name>
        <Level>3</Level>
    </Employee>
</Employees>
</Group>
```

## <a name="serializing-an-array-as-a-sequence-of-elements"></a><span data-ttu-id="61638-131">Bir dizi öğeleri dizisi olarak seri hale getiriliyor.</span><span class="sxs-lookup"><span data-stu-id="61638-131">Serializing an Array as a Sequence of Elements</span></span>

<span data-ttu-id="61638-132">Uygulayarak düz dizisi XML öğesi olarak bir dizi serileştirebilen bir <xref:System.Xml.Serialization.XmlElementAttribute> alanına dizi gibi döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="61638-132">You can also serialize an array as a flat sequence of XML elements by applying a <xref:System.Xml.Serialization.XmlElementAttribute> to the field returning the array as follows.</span></span>

```vb
Public Class Group
    <XmlElement> _
    Public Employees() As Employee
End Class
```

```csharp
public class Group {
    [XmlElement]
    public Employee[] Employees;
}
```

<span data-ttu-id="61638-133">Serileştirilmiş bir örnek şöyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="61638-133">A serialized instance might resemble the following.</span></span>

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

<span data-ttu-id="61638-134">İki XML akışını ayırt etmenin başka bir yolu da, derlenen koddan XML Şema (XSD) belge dosyalarını oluşturmak için XML Şema Tanımı aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="61638-134">Another way to differentiate the two XML streams is to use the XML Schema Definition tool to generate the XML Schema (XSD) document files from the compiled code.</span></span> <span data-ttu-id="61638-135">(Aracı kullanma hakkında daha fazla bilgi için [XML Şema Tanım Aracı ve XML Serileştirme'ye](the-xml-schema-definition-tool-and-xml-serialization.md)bakın.) Alana öznitelik uygulanmadığında, şema öğeyi aşağıdaki şekilde açıklar.</span><span class="sxs-lookup"><span data-stu-id="61638-135">(For more details on using the tool, see [The XML Schema Definition Tool and XML Serialization](the-xml-schema-definition-tool-and-xml-serialization.md).) When no attribute is applied to the field, the schema describes the element in the following manner.</span></span>

```xml
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />
```

<span data-ttu-id="61638-136">Zaman <xref:System.Xml.Serialization.XmlElementAttribute> uygulandığı öğe elde edilen şema alanına, aşağıdaki şekilde açıklar.</span><span class="sxs-lookup"><span data-stu-id="61638-136">When the <xref:System.Xml.Serialization.XmlElementAttribute> is applied to the field, the resulting schema describes the element as follows.</span></span>

```xml
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" />
```

## <a name="serializing-an-arraylist"></a><span data-ttu-id="61638-137">ArrayList seri hale getirilmedi</span><span class="sxs-lookup"><span data-stu-id="61638-137">Serializing an ArrayList</span></span>

<span data-ttu-id="61638-138"><xref:System.Collections.ArrayList> Sınıfı, farklı nesnelerinin bir koleksiyonu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="61638-138">The <xref:System.Collections.ArrayList> class can contain a collection of diverse objects.</span></span> <span data-ttu-id="61638-139">Bu nedenle kullanabileceğiniz bir <xref:System.Collections.ArrayList> kadar bir dizi kullanın.</span><span class="sxs-lookup"><span data-stu-id="61638-139">You can therefore use a <xref:System.Collections.ArrayList> much as you use an array.</span></span> <span data-ttu-id="61638-140">Yazılan nesnelerin bir dizi döndürür bir alan oluşturmak yerine, ancak, tek bir döndüren bir alan oluşturabileceğiniz <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="61638-140">Instead of creating a field that returns an array of typed objects, however, you can create a field that returns a single <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="61638-141">Ancak, dizilerle gibi sizi bilgilendirmek gerekir <xref:System.Xml.Serialization.XmlSerializer> nesneleri türlerinin <xref:System.Collections.ArrayList> içerir.</span><span class="sxs-lookup"><span data-stu-id="61638-141">However, as with arrays, you must inform the <xref:System.Xml.Serialization.XmlSerializer> of the types of objects the <xref:System.Collections.ArrayList> contains.</span></span> <span data-ttu-id="61638-142">Bunu gerçekleştirmek için birden çok örneğinin atamak <xref:System.Xml.Serialization.XmlElementAttribute> alanına, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="61638-142">To accomplish this, assign multiple instances of the <xref:System.Xml.Serialization.XmlElementAttribute> to the field, as shown in the following example.</span></span>

```vb
Public Class Group
    <XmlElement(Type:=GetType(Employee)), _
    XmlElement(Type:=GetType(Manager))> _
    Public Info As ArrayList
End Class
```

```csharp
public class Group {
    [XmlElement(Type = typeof(Employee)),
    XmlElement(Type = typeof(Manager))]
    public ArrayList Info;
}
```

## <a name="controlling-serialization-of-classes-using-xmlrootattribute-and-xmltypeattribute"></a><span data-ttu-id="61638-143">XmlRootAttribute ve XmlTypeAttribute kullanarak Sınıfların Serileştirilmesi kontrol</span><span class="sxs-lookup"><span data-stu-id="61638-143">Controlling Serialization of Classes Using XmlRootAttribute and XmlTypeAttribute</span></span>

<span data-ttu-id="61638-144">Bir sınıfa (ve yalnızca bir sınıfa) uygulanabilecek iki öznitelik vardır: <xref:System.Xml.Serialization.XmlRootAttribute> ve. <xref:System.Xml.Serialization.XmlTypeAttribute></span><span class="sxs-lookup"><span data-stu-id="61638-144">There are two attributes that can be applied to a class (and only a class): <xref:System.Xml.Serialization.XmlRootAttribute> and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span> <span data-ttu-id="61638-145">Bu öznitelikler çok benzer.</span><span class="sxs-lookup"><span data-stu-id="61638-145">These attributes are very similar.</span></span> <span data-ttu-id="61638-146"><xref:System.Xml.Serialization.XmlRootAttribute> İçin yalnızca bir sınıf uygulanabilir: sınıf serileştirilmiş olduğunda, temsil eder XML belgesi açma kapatma ve, öğe — diğer bir deyişle, kök öğe.</span><span class="sxs-lookup"><span data-stu-id="61638-146">The <xref:System.Xml.Serialization.XmlRootAttribute> can be applied to only one class: the class that, when serialized, represents the XML document's opening and closing element—in other words, the root element.</span></span> <span data-ttu-id="61638-147"><xref:System.Xml.Serialization.XmlTypeAttribute>, Diğer el, kök sınıfı dahil olmak üzere herhangi bir sınıf uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="61638-147">The <xref:System.Xml.Serialization.XmlTypeAttribute>, on the other hand, can be applied to any class, including the root class.</span></span>

<span data-ttu-id="61638-148">Örneğin, önceki örneklerde, `Group` kök sınıfı ve tüm genel alanlar ve Özellikler XML belgesinde bulunan XML öğelerine haline gelir.</span><span class="sxs-lookup"><span data-stu-id="61638-148">For example, in the previous examples, the `Group` class is the root class, and all its public fields and properties become the XML elements found in the XML document.</span></span> <span data-ttu-id="61638-149">Bu nedenle, yalnızca bir kök sınıfı olabilir.</span><span class="sxs-lookup"><span data-stu-id="61638-149">Therefore, there can be only one root class.</span></span> <span data-ttu-id="61638-150"><xref:System.Xml.Serialization.XmlRootAttribute>, tarafından oluşturulan XML akışını kontrol <xref:System.Xml.Serialization.XmlSerializer>edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61638-150">By applying the <xref:System.Xml.Serialization.XmlRootAttribute>, you can control the XML stream generated by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="61638-151">Örneğin, ad alanı ve öğe adını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61638-151">For example, you can change the element name and namespace.</span></span>

<span data-ttu-id="61638-152">Oluşturulan <xref:System.Xml.Serialization.XmlTypeAttribute> XML şemasını kontrol etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="61638-152">The <xref:System.Xml.Serialization.XmlTypeAttribute> allows you to control the schema of the generated XML.</span></span> <span data-ttu-id="61638-153">Bu yetenek şeması XML Web hizmeti aracılığıyla yayımlamak gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="61638-153">This capability is useful when you need to publish the schema through an XML Web service.</span></span> <span data-ttu-id="61638-154">Aşağıdaki örnekte, her ikisi de uygulanır <xref:System.Xml.Serialization.XmlTypeAttribute> ve <xref:System.Xml.Serialization.XmlRootAttribute> aynı sınıfa.</span><span class="sxs-lookup"><span data-stu-id="61638-154">The following example applies both the <xref:System.Xml.Serialization.XmlTypeAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the same class.</span></span>

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
public class Group {
    public Employee[] Employees;
}
```

<span data-ttu-id="61638-155">Bu sınıf derlenmiş ve XML şema tanımı aracı şemasına üretmek için kullanılan, aşağıdaki açıklayan XML bulur `Group`.</span><span class="sxs-lookup"><span data-stu-id="61638-155">If this class is compiled, and the XML Schema Definition tool is used to generate its schema, you would find the following XML describing `Group`.</span></span>

```xml
<xs:element name="NewGroupName" type="NewTypeName" />
```

<span data-ttu-id="61638-156">Buna karşılık, sınıfın bir örneğini seri hale `NewGroupName` getirecekolsaydınız, yalnızca XML belgesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="61638-156">In contrast, if you were to serialize an instance of the class, only `NewGroupName` would be found in the XML document.</span></span>

```xml
<NewGroupName>
    . . .
</NewGroupName>
```

## <a name="preventing-serialization-with-the-xmlignoreattribute"></a><span data-ttu-id="61638-157">XmlIgnoreAttribute ile Serileştirme önleme</span><span class="sxs-lookup"><span data-stu-id="61638-157">Preventing Serialization with the XmlIgnoreAttribute</span></span>

<span data-ttu-id="61638-158">Ortak özelliği olduğunda durumlar olabilir veya alan seri hale gerekmez.</span><span class="sxs-lookup"><span data-stu-id="61638-158">There might be situations when a public property or field does not need to be serialized.</span></span> <span data-ttu-id="61638-159">Örneğin, bir alan veya özellik meta veriler içeren için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="61638-159">For example, a field or property could be used to contain metadata.</span></span> <span data-ttu-id="61638-160">Böyle durumlarda, uygulama <xref:System.Xml.Serialization.XmlIgnoreAttribute> alanı veya özelliği için ve <xref:System.Xml.Serialization.XmlSerializer> üzerine atlar.</span><span class="sxs-lookup"><span data-stu-id="61638-160">In such cases, apply the <xref:System.Xml.Serialization.XmlIgnoreAttribute> to the field or property and the <xref:System.Xml.Serialization.XmlSerializer> will skip over it.</span></span>

## <a name="see-also"></a><span data-ttu-id="61638-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61638-161">See also</span></span>

- [<span data-ttu-id="61638-162">XML Serileştirmeyi Denetleyen Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="61638-162">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="61638-163">Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="61638-163">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="61638-164">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="61638-164">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="61638-165">XML Serileştirme Örnekleri</span><span class="sxs-lookup"><span data-stu-id="61638-165">Examples of XML Serialization</span></span>](examples-of-xml-serialization.md)
- [<span data-ttu-id="61638-166">Nasıl yapılır: XML Akışı için Alternatif Öğe Adı Belirtme</span><span class="sxs-lookup"><span data-stu-id="61638-166">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="61638-167">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="61638-167">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="61638-168">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="61638-168">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
