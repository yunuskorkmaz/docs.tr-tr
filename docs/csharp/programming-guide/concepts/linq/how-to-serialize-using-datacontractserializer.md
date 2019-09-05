---
title: 'Nasıl yapılır: DataContractSerializer (C#) kullanarak serileştirme'
ms.date: 07/20/2015
ms.assetid: 3320ecbf-cdbe-480e-979c-2c14bbef9988
ms.openlocfilehash: 2b4800e2c6d210d62ab3093b673898a147c1f92d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253336"
---
# <a name="how-to-serialize-using-datacontractserializer-c"></a><span data-ttu-id="ddcba-102">Nasıl yapılır: DataContractSerializer (C#) kullanarak serileştirme</span><span class="sxs-lookup"><span data-stu-id="ddcba-102">How to: Serialize Using DataContractSerializer (C#)</span></span>
<span data-ttu-id="ddcba-103">Bu konuda, kullanarak <xref:System.Runtime.Serialization.DataContractSerializer>seri hale getirilen ve seri hale getirilen bir örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ddcba-103">This topic shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddcba-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ddcba-104">Example</span></span>  
 <span data-ttu-id="ddcba-105">Aşağıdaki örnek, <xref:System.Xml.Linq.XElement> nesneleri içeren bir dizi nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ddcba-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="ddcba-106">Daha sonra bunları metin dosyalarına serileştirir ve metin dosyalarından serileştirir.</span><span class="sxs-lookup"><span data-stu-id="ddcba-106">It then serializes them to text files, and then deserializes them from the text files.</span></span>  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Linq;  
using System.IO;  
using System.Runtime.Serialization;  
  
public class XLinqTest  
{  
    public static void Main()  
    {  
        Test<XElement>(CreateXElement());  
        Test<XElementContainer>(new XElementContainer());  
        Test<XElementNullContainer>(new XElementNullContainer());  
    }  
  
    public static void Test<T>(T obj)  
    {  
        DataContractSerializer s = new DataContractSerializer(typeof(T));  
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Create))  
        {  
            Console.WriteLine("Testing for type: {0}", typeof(T));   
            s.WriteObject(fs, obj);  
        }  
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Open))  
        {  
            object s2 = s.ReadObject(fs);  
            if (s2 == null)  
                Console.WriteLine("  Deserialized object is null (Nothing in VB)");  
            else  
                Console.WriteLine("  Deserialized type: {0}", s2.GetType());  
        }  
    }  
  
    public static XElement CreateXElement()  
    {  
        return new XElement(XName.Get("NameInNamespace", "http://www.adventure-works.org"));  
    }  
}  
  
[DataContract]  
public class XElementContainer  
{  
    [DataMember]  
    public XElement member;  
  
    public XElementContainer()  
    {  
        member = XLinqTest.CreateXElement();  
    }  
}  
  
[DataContract]  
public class XElementNullContainer  
{  
    [DataMember]  
    public XElement member;  
  
    public XElementNullContainer()  
    {  
        member = null;  
    }  
}  
```  
  
 <span data-ttu-id="ddcba-107">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ddcba-107">This example produces the following output:</span></span>  
  
```output  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
