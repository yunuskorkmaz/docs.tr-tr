---
title: XmlSerializer (C#) kullanarak serileştirme
ms.date: 07/20/2015
ms.assetid: 2e0a0bbc-c548-4fe2-8741-be5a9ccd0cbb
ms.openlocfilehash: 0ec19e964471382c6f10f07d6d4bb25f88fd532f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347391"
---
# <a name="how-to-serialize-using-xmlserializer-c"></a><span data-ttu-id="d8413-102">XmlSerializer (C#) kullanarak serileştirme</span><span class="sxs-lookup"><span data-stu-id="d8413-102">How to serialize using XmlSerializer (C#)</span></span>
<span data-ttu-id="d8413-103">Bu konu, 'yi kullanarak <xref:System.Xml.Serialization.XmlSerializer>serihale ve deserialize eden bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8413-103">This topic shows an example that serializes and deserializes using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8413-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8413-104">Example</span></span>  
 <span data-ttu-id="d8413-105">Aşağıdaki örnek, nesneleri içeren <xref:System.Xml.Linq.XElement> bir dizi nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d8413-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d8413-106">Daha sonra onları bir bellek akışına serileştirir ve sonra bellek akışından deserialize eder.</span><span class="sxs-lookup"><span data-stu-id="d8413-106">It then serializes them to a memory stream, and then deserializes them from the memory stream.</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Linq;  
using System.Xml;  
using System.Xml.Serialization;  
using System.Xml.Linq;  
  
public class XElementContainer  
{  
    public XElement member;  
  
    public XElementContainer()  
    {  
        member = XLinqTest.CreateXElement();  
    }  
  
    public override string ToString()  
    {  
        return member.ToString();  
    }  
}  
  
public class XElementNullContainer  
{  
    public XElement member;  
  
    public XElementNullContainer()  
    {  
    }  
}  
  
class XLinqTest  
{  
    static void Main(string[] args)  
    {  
        Test<XElementNullContainer>(new XElementNullContainer());  
        Test<XElement>(CreateXElement());  
        Test<XElementContainer>(new XElementContainer());  
    }  
  
    public static XElement CreateXElement()  
    {  
        XNamespace ns = "http://www.adventure-works.com";  
        return new XElement(ns + "aw");  
    }  
  
    static void Test<T>(T obj)  
    {  
        using (MemoryStream stream = new MemoryStream())  
        {  
            XmlSerializer s = new XmlSerializer(typeof(T));  
            Console.WriteLine("Testing for type: {0}", typeof(T));  
            s.Serialize(XmlWriter.Create(stream), obj);  
            stream.Flush();  
            stream.Seek(0, SeekOrigin.Begin);  
            object o = s.Deserialize(XmlReader.Create(stream));  
            Console.WriteLine("  Deserialized type: {0}", o.GetType());  
        }  
    }  
}  
```  
  
 <span data-ttu-id="d8413-107">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d8413-107">This example produces the following output:</span></span>  
  
```output  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
```  
