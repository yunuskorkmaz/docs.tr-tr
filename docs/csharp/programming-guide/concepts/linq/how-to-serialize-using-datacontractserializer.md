---
title: DataContractSerializer (C#) kullanarak serileştirme
ms.date: 07/20/2015
ms.assetid: 3320ecbf-cdbe-480e-979c-2c14bbef9988
ms.openlocfilehash: 0b6d35a2f73ac512f05341f5aaffa61484657576
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168706"
---
# <a name="how-to-serialize-using-datacontractserializer-c"></a><span data-ttu-id="d4740-102">DataContractSerializer (C#) kullanarak serileştirme</span><span class="sxs-lookup"><span data-stu-id="d4740-102">How to serialize using DataContractSerializer (C#)</span></span>
<span data-ttu-id="d4740-103">Bu konu, 'yi kullanarak <xref:System.Runtime.Serialization.DataContractSerializer>serihale ve deserialize eden bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4740-103">This topic shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4740-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4740-104">Example</span></span>  
 <span data-ttu-id="d4740-105">Aşağıdaki örnek, nesneleri içeren <xref:System.Xml.Linq.XElement> bir dizi nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d4740-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d4740-106">Daha sonra onları metin dosyalarına serihale eder ve metin dosyalarından deserialize eder.</span><span class="sxs-lookup"><span data-stu-id="d4740-106">It then serializes them to text files, and then deserializes them from the text files.</span></span>  
  
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
  
 <span data-ttu-id="d4740-107">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d4740-107">This example produces the following output:</span></span>  
  
```output  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
