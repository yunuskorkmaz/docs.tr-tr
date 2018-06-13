---
title: 'Nasıl yapılır: DataContractSerializer (C#) kullanarak serileştirme'
ms.date: 07/20/2015
ms.assetid: 3320ecbf-cdbe-480e-979c-2c14bbef9988
ms.openlocfilehash: 1b2ec431698f23ea0c3e690cd57261bad8b1e4a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329290"
---
# <a name="how-to-serialize-using-datacontractserializer-c"></a><span data-ttu-id="09697-102">Nasıl yapılır: DataContractSerializer (C#) kullanarak serileştirme</span><span class="sxs-lookup"><span data-stu-id="09697-102">How to: Serialize Using DataContractSerializer (C#)</span></span>
<span data-ttu-id="09697-103">Bu konuda, serileştirir ve kullanılarak seri durumdan çıkarır bir örnek gösterilmektedir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="09697-103">This topic shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09697-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="09697-104">Example</span></span>  
 <span data-ttu-id="09697-105">Aşağıdaki örnek, bir dizi içeren nesneleri oluşturur <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="09697-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="09697-106">Bunları metin dosyalarına serileştirir ve bunları metin dosyalarından çıkarır.</span><span class="sxs-lookup"><span data-stu-id="09697-106">It then serializes them to text files, and then deserializes them from the text files.</span></span>  
  
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
  
 <span data-ttu-id="09697-107">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="09697-107">This example produces the following output:</span></span>  
  
```  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
  
## <a name="see-also"></a><span data-ttu-id="09697-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09697-108">See Also</span></span>  
 [<span data-ttu-id="09697-109">XElement nesneler (C#) içeren nesne grafiklerinin seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="09697-109">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-object-graphs-that-contain-xelement-objects.md)
