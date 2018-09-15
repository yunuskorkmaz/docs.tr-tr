---
title: 'Nasıl yapılır: bir nesneyi serileştirmek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: e4d6e3edb15dbf5ba4b7ec7f8658fec1a618d315
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45624911"
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="f12ce-102">Nasıl yapılır: bir nesneyi serileştirmek</span><span class="sxs-lookup"><span data-stu-id="f12ce-102">How to: Serialize an Object</span></span>
<span data-ttu-id="f12ce-103">Bir nesneyi serileştirmek için önce sıralanabilir ve ortak özelliklerini ve alanları ayarlamak için olan nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f12ce-103">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="f12ce-104">Bunu yapmak için XML akışı, bir akış olarak veya bir dosya olarak depolanır taşıma biçimi belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f12ce-104">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="f12ce-105">XML Akışı kalıcı bir biçimde kaydedilmesi gerekir, örneğin, oluşturun bir <xref:System.IO.FileStream> nesne.</span><span class="sxs-lookup"><span data-stu-id="f12ce-105">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f12ce-106">Daha fazla XML serileştirme örnekler için bkz. [XML serileştirme örnekler](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="f12ce-106">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="f12ce-107">Bir nesneyi serileştirmek için</span><span class="sxs-lookup"><span data-stu-id="f12ce-107">To serialize an object</span></span>  
  
1.  <span data-ttu-id="f12ce-108">Nesne oluşturun ve kendi ortak alanları ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f12ce-108">Create the object and set its public fields and properties.</span></span>  
  
2.  <span data-ttu-id="f12ce-109">Oluşturmak bir <xref:System.Xml.Serialization.XmlSerializer> kullanarak nesnenin türü.</span><span class="sxs-lookup"><span data-stu-id="f12ce-109">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="f12ce-110">Daha fazla bilgi için <xref:System.Xml.Serialization.XmlSerializer> sınıf oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="f12ce-110">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3.  <span data-ttu-id="f12ce-111">Çağrı <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> bir XML akışı veya nesnenin ortak özellikler ve alanları dosya gösterimini oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f12ce-111">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="f12ce-112">Aşağıdaki örnek, bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f12ce-112">The following example creates a file.</span></span>  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new   
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f12ce-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f12ce-113">See also</span></span>

- [<span data-ttu-id="f12ce-114">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="f12ce-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
- [<span data-ttu-id="f12ce-115">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="f12ce-115">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
