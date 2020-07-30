---
title: DataContractSerializer kullanarak serileştirme (C#)
description: DataContractSerializer kullanarak nesneleri seri hale getirme hakkında bilgi edinin. Nesneleri oluşturan, bunları metin dosyalarına diztiren ve sonra da onları seri hale getirilen bir örneğe bakın.
ms.date: 07/20/2015
ms.assetid: 3320ecbf-cdbe-480e-979c-2c14bbef9988
ms.openlocfilehash: b713f36cde594f7cd7011073345d33c6f46585e0
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301534"
---
# <a name="how-to-serialize-using-datacontractserializer-c"></a><span data-ttu-id="bbbf0-104">DataContractSerializer kullanarak serileştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="bbbf0-104">How to serialize using DataContractSerializer (C#)</span></span>
<span data-ttu-id="bbbf0-105">Bu konuda, kullanarak seri hale getirilen ve seri hale getirilen bir örnek gösterilmektedir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="bbbf0-105">This topic shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbbf0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbbf0-106">Example</span></span>  
 <span data-ttu-id="bbbf0-107">Aşağıdaki örnek, nesneleri içeren bir dizi nesne oluşturur <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="bbbf0-107">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="bbbf0-108">Daha sonra bunları metin dosyalarına serileştirir ve metin dosyalarından serileştirir.</span><span class="sxs-lookup"><span data-stu-id="bbbf0-108">It then serializes them to text files, and then deserializes them from the text files.</span></span>  
  
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
  
 <span data-ttu-id="bbbf0-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bbbf0-109">This example produces the following output:</span></span>  
  
```output  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
