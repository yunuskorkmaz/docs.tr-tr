---
title: XML serileştirme özniteliklerini kullanarak denetleme
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
ms.openlocfilehash: 84e1734a18a464ab28a75176a507168a7ba029d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592008"
---
# <a name="controlling-xml-serialization-using-attributes"></a>XML serileştirme özniteliklerini kullanarak denetleme
Öznitelikler, nesnenin XML serileştirme kontrol etmek veya alternatif bir XML akışı sınıfları aynı kümesinden oluşturmak için kullanılabilir. Alternatif bir XML akışı oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir diğer öğe adı için bir XML akışı belirtin](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md).  
  
> [!NOTE]
>  Oluşturulan XML "Basit Nesne Erişim Protokolü (SOAP) 1.1" başlıklı bölüme World Wide Web Konsorsiyumu (www.w3.org) belgenin 5 uymalıdır, listelenen öznitelikleri kullanın. [öznitelikleri, Denetim kodlanmış SOAP seri hale getirme](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
 Varsayılan olarak, bir XML öğesi adı, sınıf veya üye ada göre belirlenir. Adlı basit bir sınıf içinde `Book`, adında bir alan `ISBN` bir XML öğesi etiketi üretecektir \<ISBN >, aşağıdaki örnekte gösterildiği gibi.  
  
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
  
 Öğe yeni bir ad verin istiyorsanız, bu varsayılan davranış değiştirilebilir. Aşağıdaki kod nasıl bir öznitelik bu ayarlayarak sağlar gösterir <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> özelliği bir <xref:System.Xml.Serialization.XmlElementAttribute>.  
  
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
  
 Öznitelikler hakkında daha fazla bilgi için bkz: [öznitelikleri](../../../docs/standard/attributes/index.md). XML serileştirme denetim öznitelikleri listesi için bkz: [öznitelikleri, Denetim XML serileştirme](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md).  
  
## <a name="controlling-array-serialization"></a>Dizi serileştirme denetleme  
 <xref:System.Xml.Serialization.XmlArrayAttribute> Ve <xref:System.Xml.Serialization.XmlArrayItemAttribute> öznitelikleri diziler serileştirmek denetlemek için tasarlanmıştır. Bu öznitelikler kullanarak, ("XML Şeması bölümü 2: veri türleri" başlıklı World Wide Web Konsorsiyumu [www.w3.org] belgede tanımlanan) öğesi adını, ad alanı ve XML Şeması (XSD) veri türü denetleyebilirsiniz. Bir dizide dahil edilebilir türleri de belirtebilirsiniz.  
  
 <xref:System.Xml.Serialization.XmlArrayAttribute> Bir dizi serileştirilmiş olduğunda, kapsayan XML öğesi özelliklerini belirler. Örneğin, varsayılan olarak, aşağıdaki dizi serileştirmek adlı bir XML öğesi sonuçlanacak `Employees`. `Employees` Öğesi, bir dizi sonra dizi türü adlı öğeleri içerecek `Employee`.  
  
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
  
 Serileştirilmiş bir örnek şöyle olabilir.  
  
```xml  
<Group>  
<Employees>  
    <Employee>  
        <Name>Haley</Name>  
    </Employee>  
</Employees >  
</Group>  
```  
  
 Uygulayarak bir <xref:System.Xml.Serialization.XmlArrayAttribute>, XML öğesi adı aşağıdaki şekilde değiştirebilirsiniz.  
  
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
  
 Elde edilen XML aşağıdakine benzer.  
  
```xml  
<Group>  
<TeamMembers>  
    <Employee>  
        <Name>Haley</Name>  
    </Employee>  
</TeamMembers>  
```  
  
 <xref:System.Xml.Serialization.XmlArrayItemAttribute>, Diğer yandan dizisinde bulunan öğeleri nasıl serileştirilmiş denetler. Öznitelik dizi dönerek alanın uygulandığını unutmayın.  
  
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
  
 Elde edilen XML aşağıdakine benzer.  
  
```xml  
<Group>  
<Employees>  
    <MemberName>Haley</MemberName>  
</Employees>  
</Group>  
```  
  
## <a name="serializing-derived-classes"></a>Türetilen sınıfların seri hale getirilmedi  
 Başka bir kullanımını <xref:System.Xml.Serialization.XmlArrayItemAttribute> türetilen sınıfların serileştirmek izin vermektir. Örneğin, adlı başka bir sınıf `Manager` , türetilen `Employee` önceki örneği eklenebilir. Geçerli <xref:System.Xml.Serialization.XmlArrayItemAttribute>, türetilmiş sınıf türü tanınmıyor çünkü kod çalışma zamanında başarısız olur. Bu sorunu gidermek için özniteliğini uygulayın iki kez, her zaman ayarı <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> her kabul edilebilir bir türü (temel ve türetilen) özelliği.  
  
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
  
 Serileştirilmiş bir örnek şöyle olabilir.  
  
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
  
## <a name="serializing-an-array-as-a-sequence-of-elements"></a>Bir dizi öğeleri dizisi olarak seri hale getiriliyor.  
 Uygulayarak düz dizisi XML öğesi olarak bir dizi serileştirebilen bir <xref:System.Xml.Serialization.XmlElementAttribute> alanına dizi gibi döndürüyor.  
  
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
  
 Serileştirilmiş bir örnek şöyle olabilir.  
  
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
  
 İki XML akışlar ayırt etmek için başka bir yolu derlenmiş kodundan XML Şeması (XSD) belge dosyaları oluşturmak için XML şema tanımı aracını kullanmaktır. (Aracı'nı kullanma hakkında daha fazla ayrıntı için bkz: [XML şema tanımı aracı ve XML serileştirme](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md).) Hiçbir öznitelik alana uygulandığında, şema öğesi aşağıdaki şekilde açıklar.  
  
```xml  
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />  
```  
  
 Zaman <xref:System.Xml.Serialization.XmlElementAttribute> uygulandığı öğe elde edilen şema alanına, aşağıdaki şekilde açıklar.  
  
```xml  
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" />   
```  
  
## <a name="serializing-an-arraylist"></a>ArrayList seri hale getirilmedi  
 <xref:System.Collections.ArrayList> Sınıfı, farklı nesnelerinin bir koleksiyonu içerebilir. Bu nedenle kullanabileceğiniz bir <xref:System.Collections.ArrayList> kadar bir dizi kullanın. Yazılan nesnelerin bir dizi döndürür bir alan oluşturmak yerine, ancak, tek bir döndüren bir alan oluşturabileceğiniz <xref:System.Collections.ArrayList>. Ancak, dizilerle gibi sizi bilgilendirmek gerekir <xref:System.Xml.Serialization.XmlSerializer> nesneleri türlerinin <xref:System.Collections.ArrayList> içerir. Bunu gerçekleştirmek için birden çok örneğinin atamak <xref:System.Xml.Serialization.XmlElementAttribute> alanına, aşağıdaki örnekte gösterildiği gibi.  
  
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
  
## <a name="controlling-serialization-of-classes-using-xmlrootattribute-and-xmltypeattribute"></a>Seri hale getirme XmlRootAttribute ve XmlTypeAttribute kullanarak sınıfların denetleme  
 Bir sınıf (ve yalnızca bir sınıf) uygulanabilir iki öznitelik: <xref:System.Xml.Serialization.XmlRootAttribute> ve <xref:System.Xml.Serialization.XmlTypeAttribute>. Bu öznitelikler çok benzer. <xref:System.Xml.Serialization.XmlRootAttribute> İçin yalnızca bir sınıf uygulanabilir: sınıf serileştirilmiş olduğunda, temsil eder XML belgesi açma kapatma ve, öğe — diğer bir deyişle, kök öğe. <xref:System.Xml.Serialization.XmlTypeAttribute>, Diğer el, kök sınıfı dahil olmak üzere herhangi bir sınıf uygulanabilir.  
  
 Örneğin, önceki örneklerde, `Group` kök sınıfı ve tüm genel alanlar ve Özellikler XML belgesinde bulunan XML öğelerine haline gelir. Bu nedenle, yalnızca bir kök sınıfı olabilir. Uygulayarak <xref:System.Xml.Serialization.XmlRootAttribute>, tarafından oluşturulan XML akışı denetleyebilirsiniz <xref:System.Xml.Serialization.XmlSerializer>. Örneğin, ad alanı ve öğe adını değiştirebilirsiniz.  
  
 <xref:System.Xml.Serialization.XmlTypeAttribute> Oluşturulan XML Şeması denetlemenize olanak verir. Bu yetenek şeması XML Web hizmeti aracılığıyla yayımlamak gerektiğinde faydalıdır. Aşağıdaki örnekte, her ikisi de uygulanır <xref:System.Xml.Serialization.XmlTypeAttribute> ve <xref:System.Xml.Serialization.XmlRootAttribute> aynı sınıfa.  
  
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
  
 Bu sınıf derlenmiş ve XML şema tanımı aracı şemasına üretmek için kullanılan, aşağıdaki açıklayan XML bulur `Group`.  
  
```xml  
<xs:element name="NewGroupName" type="NewTypeName">  
```  
  
 Buna karşılık, sınıfının bir örneği, yalnızca serileştirme olsaydı `NewGroupName` XML belgesinde bulunamadı.  
  
```xml  
<NewGroupName>  
    . . .  
</NewGroupName>  
```  
  
## <a name="preventing-serialization-with-the-xmlignoreattribute"></a>Seri hale getirme XmlIgnoreAttribute ile önleme  
 Ortak özelliği olduğunda durumlar olabilir veya alan seri hale gerekmez. Örneğin, bir alan veya özellik meta veriler içeren için kullanılabilir. Böyle durumlarda, uygulama <xref:System.Xml.Serialization.XmlIgnoreAttribute> alanı veya özelliği için ve <xref:System.Xml.Serialization.XmlSerializer> üzerine atlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Serileştirmeyi Denetleyen Öznitelikler](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 [Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 [XML Serileştirmeye Giriş](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [XML Serileştirme Örnekleri](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 [Nasıl yapılır: XML Akışı için Alternatif Öğe Adı Belirtme](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 [Nasıl yapılır: Nesne Serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
